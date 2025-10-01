---
component: 'selection-modal'
description: 'Design guidelines, API documentation, and usage instructions for the selection-modal component extracted from SKY UX documentation.'
---

# Selection Modal Component Guidelines

## Component Overview
Selection modals let users select from a list of options. The lookup component is preferable for most selection tasks, but selection modals are useful when users need to take immediate action on selections.

## Usage

### ✅ Use when

Use selection modals when users need to select options from a long or unpredictable list and then immediately interact with the selections. If users only need to select options, use the lookup component instead.

Use buttons to open selection modals. After users select options, display selections in a format or pattern that supports the next interaction.

### ❌ Don't use when

Don't use selection modals when users only need to select options. Instead, use lookup fields.

Don't use selection modals for five or fewer options. Instead, use checkboxes or radio buttons.

Don't use selection modals when a list of options requires a format other than a simple selectable repeater. If a list requires a different format, such as a custom repeater template or a tree view, or if users require filters to find and select options, create a custom modal with the appropriate features.

## Anatomy

- Modal
- Search
- Multiselect toolbar (multiselect only)
- Unselected option
- Selected option
- New button

## Options

### Single-select and multiselect

Use single-select mode to limit users to a single option, and use multiselect mode to let them select multiple options.

### Button to create options

If users may need to add options to the list, include a button to start the workflow to create options. After users create options, they are selected in the selection modal.

## Behavior and states

### List scrolling

Long lists inside selection modals use infinite scroll.

### Presentation of selected options

Selection modals don't provide a default presentation of selected options. When users close selection modals, present the selected options in a format that matches the needs of the scenario.

## Content

### Modal title text

Use the following format for selection modal titles, and use plural objects when using multiselect:

Select <direct object>

### Modal footer buttons

Use Select as the standard label for the primary button. Use Cancel as the standard label for the link button.

## Related information

### Components

- Checkbox
- Lookup
- Radio button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

#### SkySelectionModalModule

**Package:** `@skyux/lookup`

⚠️ **This component is deprecated.**

#### SkySelectionModalService

Displays a modal for selecting one or more values.

**Package:** `@skyux/lookup`

#### SkySelectionModalAddCallbackArgs

Specifies the information for the callback used when adding a new item to a selection modal instance.

**Package:** `@skyux/lookup`

#### SkySelectionModalAddClickEventArgs

Specifies a callback function for the consumer to use to notify the selection modal that a new item has been added.

**Package:** `@skyux/lookup`

#### SkySelectionModalCloseArgs

The result from the selection modal.

**Package:** `@skyux/lookup`

#### SkySelectionModalInstance

Represents an instance of a selection modal.

**Package:** `@skyux/lookup`

#### SkySelectionModalOpenArgs

Parameters for the selection modal.

**Package:** `@skyux/lookup`

#### SkySelectionModalResult

The result from the selection modal.

**Package:** `@skyux/lookup`

#### SkySelectionModalSearchArgs

Arguments passed when an asynchronous search is executed from the
selection modal service.

**Package:** `@skyux/lookup`

#### SkySelectionModalSearchResult

The result of searching for items to display in a selection modal.

**Package:** `@skyux/lookup`

#### SkySelectionModalHarness

Harness for interacting with a selection modal in tests.

**Package:** `@skyux/lookup/testing`

#### SkySelectionModalSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionModalSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkySelectionModalSearchResultHarness

Harness for interacting with a selection modal's search results in tests.

**Package:** `@skyux/lookup/testing`

### Code Examples

#### Selection modal with add item functionality

**Selector:** `app-lookup-selection-modal-add-item-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import {
  SkySelectionModalAddClickEventArgs,
  SkySelectionModalCloseArgs,
  SkySelectionModalSearchResult,
  SkySelectionModalService,
} from '@skyux/lookup';
import { SkyModalService } from '@skyux/modals';

import { Subscription } from 'rxjs';
import { map } from 'rxjs/operators';

import { AddItemModalComponent } from './add-item-modal.component';
import { ExampleService } from './example.service';
import { Person } from './person';

/**
 * @title Selection modal with add item functionality
 */
@Component({
  standalone: true,
  selector: 'app-lookup-selection-modal-add-item-example',
  templateUrl: './example.component.html',
})
export class LookupSelectionModalAddItemExampleComponent implements OnDestroy {
  protected selectedPeople: Person[] | undefined;

  #subscriptions = new Subscription();

  readonly #modalSvc = inject(SkyModalService);
  readonly #searchSvc = inject(ExampleService);
  readonly #selectionModalSvc = inject(SkySelectionModalService);

  public ngOnDestroy(): void {
    this.#subscriptions.unsubscribe();
  }

  protected showSelectionModal(): void {
    const instance = this.#selectionModalSvc.open({
      descriptorProperty: 'name',
      idProperty: 'id',
      selectionDescriptor: 'person',
      searchAsync: (args) =>
        this.#searchSvc.search(args.searchText).pipe(
          map(
            (results): SkySelectionModalSearchResult => ({
              hasMore: results.hasMore,
              items: results.people,
              totalCount: results.totalCount,
            }),
          ),
        ),
      selectMode: 'single',
      showAddButton: true,
      addClick: (args: SkySelectionModalAddClickEventArgs) => {
        const modal = this.#modalSvc.open(AddItemModalComponent);

        this.#subscriptions.add(
          modal.closed.subscribe((close) => {
            if (close.reason === 'save') {
              const person = close.data as Person;
              this.#searchSvc.addItem(person);
              args.itemAdded({ item: person });
            }
          }),
        );
      },
    });

    this.#subscriptions.add(
      instance.closed.subscribe((args: SkySelectionModalCloseArgs) => {
        if (args.reason === 'save') {
          this.selectedPeople = args.selectedItems as Person[];
        }
      }),
    );
  }
}

```

**Template:**

```html
<form novalidate [formGroup]="formGroup" (ngSubmit)="save()">
  <sky-modal headingText="Add Item">
    <sky-modal-content>
      <sky-input-box labelText="Name">
        <input
          type="text"
          autocapitalize="words"
          autocomplete="off"
          formControlName="name"
          class="sky-form-control"
        />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Add</button>
      <button class="sky-btn sky-btn-link" type="button" (click)="close()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

#### Selection modal with basic setup

**Selector:** `app-lookup-selection-modal-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  SkySelectionModalSearchResult,
  SkySelectionModalService,
} from '@skyux/lookup';

import { map } from 'rxjs/operators';

import { ExampleService } from './example.service';
import { Person } from './person';

/**
 * @title Selection modal with basic setup
 */
@Component({
  standalone: true,
  selector: 'app-lookup-selection-modal-basic-example',
  templateUrl: './example.component.html',
})
export class LookupSelectionModalBasicExampleComponent {
  protected selectedPeople: Person[] | undefined;

  readonly #searchSvc = inject(ExampleService);
  readonly #selectionModalSvc = inject(SkySelectionModalService);

  protected showSelectionModal(): void {
    const instance = this.#selectionModalSvc.open({
      descriptorProperty: 'name',
      idProperty: 'id',
      selectionDescriptor: 'person',
      searchAsync: (args) =>
        this.#searchSvc.search(args.searchText).pipe(
          map(
            (results): SkySelectionModalSearchResult => ({
              hasMore: results.hasMore,
              items: results.people,
              totalCount: results.totalCount,
            }),
          ),
        ),
      selectMode: 'single',
    });

    instance.closed.subscribe((args) => {
      if (args.reason === 'save') {
        this.selectedPeople = args.selectedItems as Person[];
      }
    });
  }
}

```

**Template:**

```html
<div class="sky-margin-stacked-xl">
  <button
    type="button"
    class="sky-btn sky-btn-default selection-modal-example-show-btn"
    (click)="showSelectionModal()"
  >
    Select a value
  </button>
</div>

@if (selectedPeople?.length) {
  <div>
    Selected people:
    <ul class="selection-modal-example-selected">
      @for (selectedPerson of selectedPeople; track selectedPerson) {
        <li>
          {{ selectedPerson.name }}
        </li>
      }
    </ul>
  </div>
}

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
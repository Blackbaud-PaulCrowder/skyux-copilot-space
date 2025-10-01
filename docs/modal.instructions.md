---
component: 'modal'
description: 'Design guidelines, API documentation, and usage instructions for the modal component extracted from SKY UX documentation.'
---

# Modal Component Guidelines

## Component Overview
The modal component and service launch modals in a consistent way in SKY UX applications.

## Usage

### ✅ Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

**✅ Do use modals when users must complete tasks before they proceed.**

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

**✅ Do use modals when displaying long forms.**

Use modals when users need to add records from paginated lists or infinite scroll lists.

**✅ Do use modals to add records from paginated lists or infinite scroll lists.**

Use large modals when housing a large component that best utilizes the horizontal space, such as sectioned forms or wizards.

**✅ Do use large modals with sectioned forms and wizards.**

### ✅ Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

## Anatomy

- Heading
- Content
- Footer
- Buttons
- Help inline button

## Options

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a help inline button beside the header to invoke contextual user assistance.

## Behavior and states

### Unsaved data

If users close a modal before saving their changes, use SkyModalIsDirtyDirective to warn them about losing the unsaved data with a confirmation dialog.

## Content

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

### Buttons in the modal action bar

## Related information

### Components

- Buttons
- Confirmation dialog
- Input box

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandModalExampleComponent

**Selector:** `app-layout-text-expand-modal-example`

**Package:** `@skyux/code-examples`

#### ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

#### ModalsConfirmBasicWithControllerExampleComponent

**Selector:** `app-modals-confirm-basic-with-controller-example`

**Package:** `@skyux/code-examples`

#### ModalsConfirmBasicWithHarnessExampleComponent

**Selector:** `app-modals-confirm-basic-with-harness-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithControllerExampleComponent

**Selector:** `app-modals-modal-basic-with-controller-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithHarnessHelpKeyExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-help-key-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithHarnessExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-example`

**Package:** `@skyux/code-examples`

#### ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Package:** `@skyux/code-examples`

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### SkyDataManagerFilterModalContext

Sets the state of the filters.

**Package:** `@skyux/data-manager`

#### SkyTextEditorUrlModalComponent

**Selector:** `sky-text-editor-url-modal`

**Package:** `@skyux/text-editor`

#### SkyFilterItemModalComponent

A filter bar item that opens a modal for complex filter configuration.
Use this component when your filter requires a rich UI with multiple inputs,
date pickers, or other complex controls that don't fit in an inline filter.

**Selector:** `sky-filter-item-modal`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `filterId`: `InputSignal<string>` - A unique identifier for the filter item. **[Required]**
- `labelText`: `InputSignal<string>` - The label to display for the filter item. **[Required]**
- `modalComponent`: `InputSignal<Type<SkyFilterItemModal<TData>>>` - The modal component to display when the user selects the filter.
The component needs to inject a `SkyFilterItemModalInstance` object on instantiation to receive the modal instance and context from the modal service.
The return value of the modal save action needs to be a `SkyFilterBarFilterValue`. **[Required]**
- `modalSize`: `InputSignal<SkyFilterItemModalSizeType>` - The size of the modal to display. The valid options are `"small"`, `"medium"`, `"large"`, and `"fullScreen"`.

**Outputs:**

- `modalOpened`: `EventEmitter<SkyFilterItemModalOpenedArgs<TData>>` - Fires when the user clicks the filter item. To pass additional context data to a filter modal, consumers
must subscribe to this event and return the context using the observable property on the event args.

#### SkyFilterItemModalContext

The context object that is provided to a filter modal.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalInstance

A specialized `SkyModalInstance` wrapper.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalOpenedArgs

Arguments passed to a filter modal when it opens.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalSavedArgs

Arguments passed back from a filter modal when the user has saved.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalSizeType

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModal

A type marker for passing context object data types into the filter modal component.

**Package:** `@skyux/filter-bar`

#### ErrorModalConfig

**Package:** `@skyux/errors`

⚠️ **This component is deprecated.**

#### SkyErrorModalService

Opens a modal to display a SKY UX-themed error message.

**Package:** `@skyux/errors`

⚠️ **This component is deprecated.**

#### SkyErrorModalHarness

Harness for interacting with an error modal component in tests.

**Package:** `@skyux/errors/testing`

#### SkyTextExpandModalHarness

Harness for interacting with a text expand modal component in tests.

**Package:** `@skyux/layout/testing`

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

#### SkyModalBeforeCloseHandler

Properties about the modal close action and a method to close the modal.

**Package:** `@skyux/modals`

#### SkyModalCloseArgs

Contains an object with the data passed from users when
a modal is closed and the reason that the modal was closed.

**Package:** `@skyux/modals`

#### SkyModalConfiguration

**Package:** `@skyux/modals`

#### SkyModalContentComponent

Specifies content to display in the modal's body.

**Selector:** `sky-modal-content`

**Package:** `@skyux/modals`

#### SkyModalError

Contains an object with properties for displaying form-level errors in the modal.

**Package:** `@skyux/modals`

#### SkyModalErrorsService

**Package:** `@skyux/modals`

#### SkyModalFooterComponent

Specifies content to display in the modal's footer.

**Selector:** `sky-modal-footer`

**Package:** `@skyux/modals`

#### SkyModalHeaderComponent

Specifies a header for the modal.

**Selector:** `sky-modal-header`

**Package:** `@skyux/modals`

#### SkyModalHostService

**Package:** `@skyux/modals`

#### SkyModalInstance

**Package:** `@skyux/modals`

#### SkyModalIsDirtyDirective

Provides a way to mark a modal as "dirty" and displays a confirmation
message when a user closes the modal without saving.

**Selector:** `sky-modal[isDirty]`

**Package:** `@skyux/modals`

**Inputs:**

- `isDirty`: `boolean` - Whether the user edited an input on the modal. (default: false) **[Required]**

#### SkyModalServiceInterface

**Package:** `@skyux/modals`

#### SkyModalComponent

Provides a common look-and-feel for modal content with options to display
a common modal header, specify body content, and display a common modal footer
and buttons.

**Selector:** `sky-modal`

**Package:** `@skyux/modals`

**Inputs:**

- `headingText`: `string | undefined` - The text to display as the modal's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the modal header. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `layout`: `InputSignal<"none" | "fit">`
- `tiledBody`: `boolean | undefined`
- `ariaDescribedBy`: `string | undefined` - Used by the confirm component to set descriptive text without using a
modal header.
- `ariaLabelledBy`: `string | undefined` - Used by the confirm component to set descriptive text without using a
modal header.
- `ariaRole`: `string | undefined` - Used by the confirm component to set a different role for the modal.
- `formErrors`: `SkyModalError[] | undefined` - A list of form-level errors to display to the user.

#### SkyModalConfigurationInterface

Specifies configuration options for creating a modal.

**Package:** `@skyux/modals`

#### SkyModalModule

**Package:** `@skyux/modals`

#### SkyModalLegacyService

A service that launches modals.

**Package:** `@skyux/modals`

⚠️ **This component is deprecated.**

#### SkyModalService

A service that launches modals.

**Package:** `@skyux/modals`

#### SkyModalFixture

Allows interaction with a SKY UX modal component.

**Package:** `@skyux/modals/testing`

⚠️ **This component is deprecated.**

#### SkyModalTestingController

A controller to be injected into tests, which mocks the modal service
and handles interactions with modal instances. For testing interactions
with the modal component itself, use the `SkyModalHarness`.

**Package:** `@skyux/modals/testing`

#### SkyModalTestingModule

Configures the `SkyModalTestingController` as the implementation for the `SkyModalService`.

**Package:** `@skyux/modals/testing`

#### SkyModalHarnessFilters

A set of criteria that can be used to filter a list of SkyModalHarness instances.

**Package:** `@skyux/modals/testing`

#### SkyModalHarness

Harness for interacting with a modal component in tests.

**Package:** `@skyux/modals/testing`

#### SkyPageModalLink

Displays links to related information or recently accessed items.

**Package:** `@skyux/pages`

#### SkyPageModalLinksInput

**Package:** `@skyux/pages`

#### SkyModalLinkListComponent

A component that displays a list of links such as within a `<sky-page-links>` component.

**Selector:** `sky-modal-link-list`

**Package:** `@skyux/pages`

**Inputs:**

- `headingText`: `InputSignal<undefined | string>` - The text to display as the list's heading.
- `links`: `InputSignal<SkyPageModalLinksInput>` - Option to pass links as an array of `SkyPageModalLink` objects or `'loading'` to display a loading indicator.

#### SkyModalLinkListModule

**Package:** `@skyux/pages`

### Code Examples

#### Modal with summary action bar

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Modal with summary action bar
 */
@Component({
  standalone: true,
  selector: 'app-action-bars-summary-action-bar-modal-example',
  templateUrl: './example.component.html',
})
export class ActionBarsSummaryActionBarModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  protected openModal(): void {
    this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });
  }
}

```

**Template:**

```html
<button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
  Open modal
</button>

```

#### Show an error inside a modal

**Selector:** `app-errors-error-modal-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyErrorModalService } from '@skyux/errors';

/**
 * @title Show an error inside a modal
 */
@Component({
  standalone: true,
  selector: 'app-errors-error-modal-example',
  templateUrl: './example.component.html',
})
export class ErrorsErrorModalExampleComponent {
  readonly #errorSvc = inject(SkyErrorModalService);

  public openErrorModal(): void {
    this.#errorSvc.open({
      errorTitle: 'Something went wrong.',
      errorDescription: 'Close the modal, and come back later.',
      errorCloseText: 'Close',
    });
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="openErrorModal()"
>
  Open error modal
</button>

```

#### Text expand with a modal

**Selector:** `app-layout-text-expand-modal-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandModule } from '@skyux/layout';

/**
 * @title Text expand with a modal
 */
@Component({
  selector: 'app-layout-text-expand-modal-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandModule],
})
export class LayoutTextExpandModalExampleComponent {
  protected longText =
    'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.';
}

```

**Template:**

```html
<sky-text-expand [text]="longText" [maxExpandedLength]="100" />

```

#### Modal filter

**Selector:** `app-lists-filter-modal-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';
import { FilterModalComponent } from './filter-modal.component';
import { Fruit } from './fruit';

/**
 * @title Modal filter
 */
@Component({
  selector: 'app-lists-filter-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyFilterModule, SkyRepeaterModule, SkyToolbarModule],
})
export class ListsFilterModalExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected onDismiss(index: number): void {
    this.appliedFilters.splice(index, 1);
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  protected onInlineFilterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected onModalFilterButtonClick(): void {
    const modalInstance = this.#modalSvc.open(FilterModalComponent, [
      {
        provide: FilterModalContext,
        useValue: {
          appliedFilters: this.appliedFilters,
        },
      },
    ]);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'save') {
        this.appliedFilters = (result.data as Filter[]).slice();
        this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
        this.#changeDetectorRef.markForCheck();
      }
    });
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }
}

```

**Template:**

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [showButtonText]="true"
        (filterButtonClick)="onModalFilterButtonClick()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
  @if (appliedFilters && appliedFilters.length > 0) {
    <sky-toolbar-section>
      <sky-filter-summary data-sky-id="filter-summary">
        @for (item of appliedFilters; track item; let i = $index) {
          <sky-filter-summary-item (dismiss)="onDismiss(i)">
            {{ item.label }}
          </sky-filter-summary-item>
        }
      </sky-filter-summary>
    </sky-toolbar-section>
  }
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

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

#### Confirm, tested with controller

**Selector:** `app-modals-confirm-basic-with-controller-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyConfirmService } from '@skyux/modals';

/**
 * @title Confirm, tested with controller
 */
@Component({
  selector: 'app-modals-confirm-basic-with-controller-example',
  standalone: true,
  template: `<button
    aria-haspopup="dialog"
    class="sky-btn sky-btn-default"
    type="button"
    (click)="launchConfirm()"
  >
    Open confirm
  </button>`,
})
export class ModalsConfirmBasicWithControllerExampleComponent {
  public selectedAction: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  public launchConfirm(): void {
    const dialog = this.#confirmSvc.open({
      message: 'Are you sure?',
    });

    dialog.closed.subscribe((args) => {
      this.selectedAction = args.action;
    });
  }
}

```

#### Confirm, tested with harness

**Selector:** `app-modals-confirm-basic-with-harness-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  SkyConfirmButtonConfig,
  SkyConfirmInstance,
  SkyConfirmService,
  SkyConfirmType,
} from '@skyux/modals';

/**
 * @title Confirm, tested with harness
 */
@Component({
  selector: 'app-modals-confirm-basic-with-harness-example',
  standalone: true,
  templateUrl: './example.component.html',
})
export class ModalsConfirmBasicWithHarnessExampleComponent {
  protected selectedAction: string | undefined;
  protected selectedText: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  protected openOKConfirm(): void {
    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message:
        'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
    });

    dialog.closed.subscribe((result) => {
      this.selectedText = undefined;
      this.selectedAction = result.action;
    });
  }

  protected openTwoActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Finalize', action: 'save', styleType: 'primary' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message: 'Finalize report cards?',
      body: 'Grades cannot be changed once the report cards are finalized.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openThreeActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Save', action: 'save', styleType: 'primary' },
      { text: 'Delete', action: 'delete' },
      { text: 'Keep working', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Save your changes before leaving?',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openDeleteConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Delete', action: 'delete', styleType: 'danger' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Delete this account?',
      body: 'Deleting this account may affect processes that are currently running.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }
}

```

**Template:**

```html
<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm ok-confirm-btn"
  type="button"
  (click)="openOKConfirm()"
>
  OK confirm
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm two-action-confirm-btn"
  type="button"
  (click)="openTwoActionConfirm()"
>
  Confirm with two actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openThreeActionConfirm()"
>
  Confirm with three actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openDeleteConfirm()"
>
  Confirm with delete button
</button>

@if (selectedAction) {
  @if (selectedText) {
    <p class="displayed-text">
      You selected the "{{ selectedText }}" button, which has an action of "{{
        selectedAction
      }}."
    </p>
  } @else {
    <p class="displayed-text">
      You selected the "{{ selectedAction }}" action.
    </p>
  }
}

```

#### Modal with basic setup, tested with controller

**Selector:** `app-modals-modal-basic-with-controller-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyHelpService } from '@skyux/core';
import {
  SkyModalError,
  SkyModalInstance,
  SkyModalService,
} from '@skyux/modals';

import { MyHelpService } from './help.service';
import { ModalContext } from './modal-context';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with basic setup, tested with controller
 */
@Component({
  selector: 'app-modals-modal-basic-with-controller-example',
  standalone: true,
  template: `<button
    class="sky-btn sky-btn-default"
    type="button"
    (click)="openModal()"
  >
    Open modal
  </button>`,
})
export class ModalsModalBasicWithControllerExampleComponent
  implements OnDestroy
{
  public hasErrors = false;

  protected errors: SkyModalError[] = [];

  readonly #instances: SkyModalInstance[] = [];
  readonly #modalSvc = inject(SkyModalService);

  public ngOnDestroy(): void {
    this.#instances.forEach((i) => {
      i.close();
    });
  }

  public openModal(): void {
    const instance = this.#modalSvc.open(ModalComponent, {
      providers: [
        {
          provide: ModalContext,
          useValue: { value1: 'Hello!' },
        },
        // NOTE: The help service is normally provided at the application root, but
        // it is added here purely for demonstration purposes.
        // See: https://developer.blackbaud.com/skyux/learn/develop/global-help
        {
          provide: SkyHelpService,
          useExisting: MyHelpService,
        },
      ],
    });

    instance.beforeClose.subscribe((handler) => {
      if (this.hasErrors && handler.closeArgs.reason !== 'cancel') {
        this.errors = [
          {
            message: 'Something bad happened.',
          },
        ];
      } else {
        handler.closeModal();
      }
    });

    this.#instances.push(instance);
  }
}

```

#### Modal with a help key

**Selector:** `app-modals-modal-basic-with-harness-help-key-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with a help key
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-basic-with-harness-help-key-example',
  templateUrl: './example.component.html',
})
export class ModalsModalBasicWithHarnessHelpKeyExampleComponent
  implements OnDestroy
{
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### Modal with basic setup, tested with harness

**Selector:** `app-modals-modal-basic-with-harness-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with basic setup, tested with harness
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-basic-with-harness-example',
  templateUrl: './example.component.html',
})
export class ModalsModalBasicWithHarnessExampleComponent implements OnDestroy {
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### Modal with form errors

**Selector:** `app-modals-modal-with-error-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with form errors
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-with-error-example',
  templateUrl: './example.component.html',
})
export class ModalsModalWithErrorExampleComponent implements OnDestroy {
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### Sectioned form inside modal

**Selector:** `app-tabs-sectioned-form-modal-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Sectioned form inside modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-sectioned-form-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class TabsSectionedFormModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  public openModal(): void {
    const modalInstance = this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel') {
        console.log(`Modal cancelled`);
      } else if (result.reason === 'save') {
        console.log(`Modal saved`);
      }
    });
  }
}

```

**Template:**

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
  Open sectioned form
</button>

```

#### Wizard in a modal

**Selector:** `app-tabs-wizard-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard in a modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-wizard-basic-example',
  templateUrl: './example.component.html',
})
export class TabsWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  #modalSize = 'large';

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent, { size: this.#modalSize });
  }
}

```

**Template:**

```html
<button type="button" class="sky-btn sky-btn-default" (click)="openWizard()">
  Open Wizard
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
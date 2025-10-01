---
component: 'summary-action-bar'
description: 'Design guidelines, API documentation, and usage instructions for the summary-action-bar component extracted from SKY UX documentation.'
---

# Summary Action Bar Component Guidelines

## Component Overview
The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.

## Usage

### ✅ Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

**✅ Do use summary action bars for actions on a list of items.**

Use summary action bars for actions that are taken on the selected record in split views.

**✅ Do use summary action bars for actions in split views.**

Use summary action bars when you need to show summary information related to the forms in modals.

**✅ Do use summary action bars for summary information in modals.**

### ❌ Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

**❌ Don't use summary action bars for large amounts of content.**

## Anatomy

- Actions
- Summary information

## Behavior and states

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

## Options

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

## Related information

### Components

- Data entry grid
- Data grid
- Modal
- Repeater

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ActionBarsSummaryActionBarBasicExampleComponent

**Selector:** `app-action-bars-summary-action-bar-basic-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarErrorExampleComponent

**Selector:** `app-action-bars-summary-action-bar-error-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarTabExampleComponent

**Selector:** `app-action-bars-summary-action-bar-tab-example`

**Package:** `@skyux/code-examples`

#### SkySummaryActionBarActionsComponent

Contains actions for the `sky-summary-action-bar` component.

**Selector:** `sky-summary-action-bar-actions`

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarCancelComponent

Displays a cancel action.

**Selector:** `sky-summary-action-bar-cancel`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable the cancel action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select the cancel action.

#### SkySummaryActionBarPrimaryActionComponent

Displays a primary button.

**Selector:** `sky-summary-action-bar-primary-action`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable the primary action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select the primary action.

#### SkySummaryActionBarSecondaryActionComponent

Specifies secondary actions.

**Selector:** `sky-summary-action-bar-secondary-action`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable a secondary action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select a secondary action.

#### SkySummaryActionBarSecondaryActionsComponent

Contains secondary actions specified with `sky-summary-action-bar-secondary-action`
components.

**Selector:** `sky-summary-action-bar-secondary-actions`

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarComponent

Contains the `sky-summary-action-bar-actions` and
`sky-summary-action-bar-summary` components.

**Selector:** `sky-summary-action-bar`

**Package:** `@skyux/action-bars`

**Inputs:**

- `formErrors`: `SkySummaryActionBarError[] | undefined`

#### SkySummaryActionBarModule

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarSummaryComponent

Specifies the summary information to display.

**Selector:** `sky-summary-action-bar-summary`

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarError

Contains an object with properties for displaying form-level errors in a summary action bar.

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarCancelHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarCancelHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarCancelHarness

Harness for interacting with a summary action bar cancel component in tests.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarHarness

Harness for interacting with a summary action bar component in tests.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarPrimaryActionHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarPrimaryActionHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarPrimaryActionHarness

Harness for interacting with a summary action bar primary action component in tests.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSecondaryActionHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionHarness

Harness for interacting with a summary action bar secondary action component in tests.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionsHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSecondaryActionsHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionsHarness

Harness for interacting with a summary action bar secondary actions component in tests.
Use this harness to query harnesses for an individual action's SkySummaryActionBarSecondaryActionHarness.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSummaryHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSummaryHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSummaryHarness

Harness for interacting with a summary action bar summary component in tests.
Use this harness to query components inside the `sky-summary-action-bar-summary` component.

**Package:** `@skyux/action-bars/testing`

### Code Examples

#### Basic summary action bar

**Selector:** `app-action-bars-summary-action-bar-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Basic summary action bar
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule],
})
export class ActionBarsSummaryActionBarBasicExampleComponent {
  public onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }
}

```

**Template:**

```html
<sky-summary-action-bar data-sky-id="donation-summary">
  <sky-summary-action-bar-actions>
    <sky-summary-action-bar-primary-action
      (actionClick)="onPrimaryActionClick()"
    >
      Primary action
    </sky-summary-action-bar-primary-action>
    <sky-summary-action-bar-secondary-actions>
      <sky-summary-action-bar-secondary-action
        data-sky-id="secondary-action"
        (actionClick)="onSecondaryActionClick()"
      >
        Secondary action
      </sky-summary-action-bar-secondary-action>
      <sky-summary-action-bar-secondary-action
        data-sky-id="secondary-action-2"
        (actionClick)="onSecondaryAction2Click()"
      >
        Secondary action 2
      </sky-summary-action-bar-secondary-action>
    </sky-summary-action-bar-secondary-actions>
  </sky-summary-action-bar-actions>
  <sky-summary-action-bar-summary>
    <sky-key-info>
      <sky-key-info-value>$250</sky-key-info-value>
      <sky-key-info-label>Given this month</sky-key-info-label>
    </sky-key-info>
    <sky-key-info>
      <sky-key-info-value>$1,000</sky-key-info-value>
      <sky-key-info-label>Given this year</sky-key-info-label>
    </sky-key-info>
    <sky-key-info>
      <sky-key-info-value>$1,300</sky-key-info-value>
      <sky-key-info-label>Given all time</sky-key-info-label>
    </sky-key-info>
  </sky-summary-action-bar-summary>
</sky-summary-action-bar>

```

#### Summary action bar with errors

**Selector:** `app-action-bars-summary-action-bar-error-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { FormBuilder, FormControl, ReactiveFormsModule } from '@angular/forms';
import {
  SkySummaryActionBarError,
  SkySummaryActionBarModule,
} from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { of, switchMap } from 'rxjs';

interface donationSummary {
  value: number;
  label: string;
}

/**
 * @title Summary action bar with errors
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-error-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule, ReactiveFormsModule],
})
export class ActionBarsSummaryActionBarErrorExampleComponent {
  protected donationSummary = new FormControl<donationSummary[] | null>([
    {
      value: 250,
      label: 'Given this month',
    },
    {
      value: 1000,
      label: 'Given this year',
    },
    {
      value: 1300,
      label: 'Given all time',
    },
  ]);
  protected exampleForm = inject(FormBuilder).group({
    donationSummary: this.donationSummary,
  });

  protected formErrors = toSignal<SkySummaryActionBarError[] | undefined>(
    this.donationSummary.statusChanges.pipe(
      switchMap(() => {
        const errors = this.donationSummary.errors;

        return of(
          errors
            ? Object.values(errors).map((error) => ({
                message: error as string,
              }))
            : undefined,
        );
      }),
    ),
  );

  protected onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  protected singleError(): void {
    this.donationSummary.setErrors({
      singleError: 'Monthly donation is missing.',
    });
  }

  protected multipleErrors(): void {
    this.donationSummary.setErrors({
      firstError: 'Monthly donation is missing.',
      secondError: 'Yearly donation is missing.',
    });
  }
}

```

**Template:**

```html
<form [formGroup]="exampleForm">
  <sky-summary-action-bar
    data-sky-id="donation-summary"
    [formErrors]="formErrors()"
  >
    <sky-summary-action-bar-actions>
      <sky-summary-action-bar-primary-action
        (actionClick)="onPrimaryActionClick()"
      >
        Primary action
      </sky-summary-action-bar-primary-action>
      <sky-summary-action-bar-secondary-actions>
        <sky-summary-action-bar-secondary-action
          data-sky-id="single-error-action"
          (actionClick)="singleError()"
        >
          Single error action
        </sky-summary-action-bar-secondary-action>
        <sky-summary-action-bar-secondary-action
          data-sky-id="multiple-error-action"
          (actionClick)="multipleErrors()"
        >
          Multiple errors action
        </sky-summary-action-bar-secondary-action>
      </sky-summary-action-bar-secondary-actions>
    </sky-summary-action-bar-actions>
    <sky-summary-action-bar-summary>
      @for (info of donationSummary.value; track info) {
        <sky-key-info>
          <sky-key-info-value>${{ info.value }}</sky-key-info-value>
          <sky-key-info-label>{{ info.label }}</sky-key-info-label>
        </sky-key-info>
      }
    </sky-summary-action-bar-summary>
  </sky-summary-action-bar>
</form>

```

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

#### Tab with summary action bar

**Selector:** `app-action-bars-summary-action-bar-tab-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tab with summary action bar
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-tab-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule, SkyTabsModule],
})
export class ActionBarsSummaryActionBarTabExampleComponent {
  public onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }
}

```

**Template:**

```html
<sky-tabset [active]="0">
  <sky-tab tabHeading="Tab 1"> Tab without summary action bar. </sky-tab>
  <sky-tab tabHeading="Tab 2">
    Tab with summary action bar.
    <sky-summary-action-bar data-sky-id="donation-summary">
      <sky-summary-action-bar-actions>
        <sky-summary-action-bar-primary-action
          (actionClick)="onPrimaryActionClick()"
        >
          Primary action
        </sky-summary-action-bar-primary-action>
        <sky-summary-action-bar-secondary-actions>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action"
            (actionClick)="onSecondaryActionClick()"
          >
            Secondary action
          </sky-summary-action-bar-secondary-action>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action-2"
            (actionClick)="onSecondaryAction2Click()"
          >
            Secondary action 2
          </sky-summary-action-bar-secondary-action>
        </sky-summary-action-bar-secondary-actions>
      </sky-summary-action-bar-actions>
      <sky-summary-action-bar-summary>
        <sky-key-info>
          <sky-key-info-value>$250</sky-key-info-value>
          <sky-key-info-label>Given this month</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,000</sky-key-info-value>
          <sky-key-info-label>Given this year</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,300</sky-key-info-value>
          <sky-key-info-label>Given all time</sky-key-info-label>
        </sky-key-info>
      </sky-summary-action-bar-summary>
    </sky-summary-action-bar>
  </sky-tab>
</sky-tabset>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
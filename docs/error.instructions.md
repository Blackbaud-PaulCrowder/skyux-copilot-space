---
component: 'error'
description: 'Design guidelines, API documentation, and usage instructions for the error component extracted from SKY UX documentation.'
---

# Error Component Guidelines

## Component Overview
The error component displays a SKY UX-themed error message.

## Usage

### ✅ Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

Use error messages when the content inside modals fails to load.

### ❌ Don't use when

Don't use error messages to display information about background processes. Use toasts instead.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use alerts instead.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

## Anatomy

- Title
- Image
- Description
- Action

## Options

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

Use the under construction error type when pages are under maintenance or experience known outages.

Use the not found error type when pages fail to load because of 404 errors.

Use the security error type when users don't have access to view content.

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

## Content

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

## Layout

## Related Information

### Components

- Alert
- Toast

### Guidelines

- Error handling
- Form design
- User assistance

## API Documentation

### Components and Directives

#### ActionBarsSummaryActionBarErrorExampleComponent

**Selector:** `app-action-bars-summary-action-bar-error-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorEmbeddedExampleComponent

**Selector:** `app-errors-error-embedded-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Package:** `@skyux/code-examples`

#### SkySummaryActionBarError

Contains an object with properties for displaying form-level errors in a summary action bar.

**Package:** `@skyux/action-bars`

#### SkyErrorActionComponent

Specifies an interactive element to include with the error message.
For example, you can include a button to reload the page or to refresh data.

**Selector:** `sky-error-action`

**Package:** `@skyux/errors`

#### SkyErrorDescriptionComponent

Specifies a description to provide additional details about the error.

**Selector:** `sky-error-description`

**Package:** `@skyux/errors`

**Inputs:**

- `replaceDefaultDescription`: `boolean | undefined` - Whether to replace the default description. If `false`, the content
from this component is added after the default description. (default: false)

#### SkyErrorImageComponent

Specifies an image to display with the error message.

**Selector:** `sky-error-image`

**Package:** `@skyux/errors`

#### ErrorModalConfig

**Package:** `@skyux/errors`

⚠️ **This component is deprecated.**

#### SkyErrorModalService

Opens a modal to display a SKY UX-themed error message.

**Package:** `@skyux/errors`

⚠️ **This component is deprecated.**

#### SkyErrorTitleComponent

Specifies a title to display with the error message.

**Selector:** `sky-error-title`

**Package:** `@skyux/errors`

**Inputs:**

- `replaceDefaultTitle`: `boolean | undefined` - Whether to replace the default title. If `false`, the content
from this component is added after the default title. (default: false)

#### SkyErrorType

The type of error to display.

**Package:** `@skyux/errors`

#### SkyErrorComponent

Displays a SKY UX-themed error message.

**Selector:** `sky-error`

**Package:** `@skyux/errors`

**Inputs:**

- `showImage`: `boolean | undefined` - Whether to display the error image. (default: true)
- `errorType`: `SkyErrorType | undefined` - The set of pre-defined values for the image,
title, and description.

#### SkyErrorModule

**Package:** `@skyux/errors`

#### SkyErrorFixture

Allows interaction with a SKY UX error component.

**Package:** `@skyux/errors/testing`

⚠️ **This component is deprecated.**

#### SkyErrorActionHarness

Harness for interacting with an error action component in tests.

**Package:** `@skyux/errors/testing`

#### SkyErrorHarnessFilters

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

**Package:** `@skyux/errors/testing`

#### SkyErrorHarness

Harness for interacting with an error component in tests.

**Package:** `@skyux/errors/testing`

#### SkyErrorImageHarness

Harness for interacting with an error image component in tests.

**Package:** `@skyux/errors/testing`

#### SkyErrorModalHarness

Harness for interacting with an error modal component in tests.

**Package:** `@skyux/errors/testing`

#### SkyModalError

Contains an object with properties for displaying form-level errors in the modal.

**Package:** `@skyux/modals`

#### SkyModalErrorsService

**Package:** `@skyux/modals`

#### SkyFileItemErrorType

The type of error that was thrown.

**Package:** `@skyux/forms`

#### SkyFormErrorComponent

Displays default and custom form field error messages for form field components.
Set `labelText` on the form field component to automatically display required,
maximum length, minimum length, date, email, phone number, time, and URL errors.
To display custom errors, include sky-form-error elements in the form field component.

**Selector:** `sky-form-error`

**Package:** `@skyux/forms`

**Inputs:**

- `errorName`: `string` - The name of the error. **[Required]**
- `errorText`: `string` - The error message to display. **[Required]**

#### SkyFormErrorModule

**Package:** `@skyux/forms`

#### SKY_FORM_ERRORS_ENABLED

**Package:** `@skyux/forms`

#### SkyFormErrorsComponent

**Selector:** `sky-form-errors`

**Package:** `@skyux/forms`

**Inputs:**

- `dirty`: `boolean` - Indicates whether the parent component's control is dirty (default: false)
- `errors`: `null | ValidationErrors | undefined` - The validation errors from the form control.
- `labelText`: `string | undefined` - Input label text to display in the error messages.
- `touched`: `boolean` - Indicates whether the parent component's control is touched (default: false)

#### SkyFormErrorsModule

**Package:** `@skyux/forms`

#### SkyFormErrorHarnessFilters

A set of criteria that can be used to filter a list of `SkyFormErrorHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFormErrorHarness

**Package:** `@skyux/forms/testing`

#### SkyFormErrorsHarnessFilters

A set of criteria that can be used to filter a list of `SkyFormErrorHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFormErrorsHarness

**Package:** `@skyux/forms/testing`

### Code Examples

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

#### Embed error within the page markup

**Selector:** `app-errors-error-embedded-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyErrorModule } from '@skyux/errors';

/**
 * @title Embed error within the page markup
 */
@Component({
  selector: 'app-errors-error-embedded-example',
  templateUrl: './example.component.html',
  imports: [SkyErrorModule],
})
export class ErrorsErrorEmbeddedExampleComponent {
  protected customAction(): void {
    alert('action clicked!');
  }
}

```

**Template:**

```html
<sky-error errorType="broken">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Try again
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="notfound">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="construction">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="security">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error>
  <sky-error-image>
    <img
      alt=""
      role="presentation"
      src="data:image/png;base64,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"
    />
  </sky-error-image>
  <sky-error-title> Custom error with a custom image. </sky-error-title>
  <sky-error-description> Custom description. </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="broken">
  <sky-error-title [replaceDefaultTitle]="true">
    Custom error with a default image.
  </sky-error-title>
  <sky-error-description [replaceDefaultDescription]="true">
    Custom description.
  </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

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

#### Input box with custom errors

**Selector:** `app-forms-input-box-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box with custom errors
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class FormsInputBoxWithCustomFormErrorsExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    favoriteColor: this.favoriteColor,
  });
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-input-box
    data-sky-id="input-box-favorite-color"
    labelText="Favorite color"
  >
    <select formControlName="favoriteColor">
      <option value="none">None</option>
      <option value="red">Red</option>
      <option value="orange">Orange</option>
      <option value="yellow">Yellow</option>
      <option value="green">Green</option>
      <option value="blue">Blue</option>
      <option value="purple">Purple</option>
      <option value="invalid">Invalid Color</option>
    </select>
    @if (favoriteColor.errors?.['invalid']) {
      <sky-form-error
        errorName="invalid"
        errorText="The color Invalid Color is not a color"
      />
    }
  </sky-input-box>
</form>

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
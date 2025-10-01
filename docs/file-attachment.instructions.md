---
component: 'file-attachment'
description: 'Design guidelines, API documentation, and usage instructions for the file-attachment component extracted from SKY UX documentation.'
---

# File Attachment Component Guidelines

## Component Overview
The file attachment element lets users attach a single local file.

## Usage

### ✅ Use when

Use the file attachment input when users need to upload a single local file.

### ❌ Don't use when

Don't use the file attachment input when users need to link to a URL to attach an external file. Use the file drop component instead.

Don't use the file attachment input to upload multiple local files. Use the file drop component instead.

## Anatomy

### Before file is attached

### After file is attached

- Label
- File attachment button
- Required field marker
- Help inline button
- Hint text

## Options

### Required field marker

When a file attachment input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a file attachment label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file attachment input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file attachment input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the file attachment:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Image preview

When users attach images, a small preview appears below the replace file button.

### File link

When users attach a file, the file name displays as a link beside the replace file button. You must bind an action to the click event to prevent a dead link and to allow users to download the file.

## Related information

### Components

- Field group
- File drop

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsFileAttachmentBasicExampleComponent

**Selector:** `app-forms-file-attachment-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFileAttachmentHelpKeyExampleComponent

**Selector:** `app-forms-file-attachment-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyFileAttachmentChange

**Package:** `@skyux/forms`

#### SkyFileAttachmentClick

**Package:** `@skyux/forms`

#### SkyFileAttachmentLabelComponent

Displays a label above the file attachment element. To display a help button
beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-file-attachment-label` element and a `sky-control-help` CSS class
on that help button element.

**Selector:** `sky-file-attachment-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyFileAttachmentComponent

Provides an element to attach a single local file.

**Selector:** `sky-file-attachment`

**Package:** `@skyux/forms`

**Inputs:**

- `acceptedTypes`: `string | undefined` - The comma-delimited string literal of MIME types that users can attach.
By default, all file types are allowed.
- `acceptedTypesErrorMessage`: `string | undefined` - A custom error message to display when a file doesn't match the accepted types.
This replaces a default error message that lists all accepted types.
- `disabled`: `boolean` - Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the single file attachment label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the single file attachment label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `labelHidden`: `boolean` - Whether to hide `labelText` from view. (default: false)
- `labelText`: `string | undefined` - The text to display as the file attachment's label.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete.
For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required). (default: false)
- `stacked`: `boolean` - Whether the single file attachment is stacked on another form component. When specified,
the appropriate vertical spacing is automatically added to the single file attachment. (default: false)
- `validateFn`: `SkyFileValidateFn | undefined` - The custom validation function. This validation runs alongside the internal
file validation. This function takes a `SkyFileItem` object as a parameter.
- `maxFileSize`: `number` - The maximum size in bytes for valid files. (default: 500000)
- `minFileSize`: `number` - The minimum size in bytes for valid files. (default: 0)

**Outputs:**

- `fileChange`: `EventEmitter<SkyFileAttachmentChange>` - Fires when users add or remove files.
- `fileClick`: `EventEmitter<SkyFileAttachmentClick>` - Fires when users select the file name link. Make sure to bind the event.
If you do not, the file name link will be a dead link.

#### SkyFileAttachmentModule

**Package:** `@skyux/forms`

#### SkyFileAttachmentsModule

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyFileAttachmentHarnessFilters

A set of criteria that can be used to filter a list of `SkyFileAttachmentHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFileAttachmentHarness

Harness for interacting with a file attachment component in tests.

**Package:** `@skyux/forms/testing`

#### provideSkyFileAttachmentTesting

Provides mocks for file attachment testing.

**Package:** `@skyux/forms/testing`

### Code Examples

#### File attachment with basic setup

**Selector:** `app-forms-file-attachment-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import {
  SkyFileAttachmentClick,
  SkyFileAttachmentModule,
  SkyFileItem,
} from '@skyux/forms';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<SkyFileItem | null | undefined>,
): ValidationErrors | null {
  const fileItem = control.value;

  return fileItem?.file?.name.startsWith('a')
    ? { invalidStartingLetter: true }
    : null;
}

/**
 * @title File attachment with basic setup
 */
@Component({
  selector: 'app-forms-file-attachment-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyFileAttachmentModule],
})
export class FormsFileAttachmentBasicExampleComponent {
  protected attachment: FormControl<SkyFileItem | null | undefined>;

  protected formGroup: FormGroup<{
    attachment: FormControl<SkyFileItem | null | undefined>;
  }>;

  protected maxFileSize = 4000000;

  constructor() {
    this.attachment = new FormControl(undefined, {
      validators: [Validators.required, customValidator],
    });

    this.formGroup = inject(FormBuilder).group({
      attachment: this.attachment,
    });
  }

  protected onFileClick($event: SkyFileAttachmentClick): void {
    // Ensure we are only attempting to navigate to locally updated data for download.
    if ($event.file.url.startsWith('data:')) {
      const link = document.createElement('a');
      link.download = $event.file.file.name;
      link.href = $event.file.url;
      link.click();
    }
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-file-attachment
    acceptedTypes="application/pdf,image/jpeg,image/png,image/gif"
    data-sky-id="birth-certificate"
    formControlName="attachment"
    helpPopoverTitle="Requirements"
    hintText="Attach a .pdf, .gif, .png, or .jpeg file."
    labelText="Birth certificate"
    [helpPopoverContent]="helpInlinePopoverRef"
    [maxFileSize]="maxFileSize"
    (fileClick)="onFileClick($event)"
  >
    @if (attachment.errors?.['invalidStartingLetter']) {
      <sky-form-error
        errorName="invalidStartingLetter"
        errorText="You may not upload a file that begins with the letter 'a'."
      />
    }
  </sky-file-attachment>
</form>

<ng-template #helpInlinePopoverRef>
  Make sure the birth certificate includes:
  <ul>
    <li>Full name of child</li>
    <li>Birth date</li>
    <li>Place of birth</li>
    <li>Name and signature of the physician or midwife</li>
    <li>Registration or certificate number</li>
  </ul>
</ng-template>

```

#### File attachment with help key

**Selector:** `app-forms-file-attachment-help-key-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import {
  SkyFileAttachmentClick,
  SkyFileAttachmentModule,
  SkyFileItem,
} from '@skyux/forms';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<SkyFileItem | null | undefined>,
): ValidationErrors | null {
  const fileItem = control.value;

  return fileItem?.file?.name.startsWith('a')
    ? { invalidStartingLetter: true }
    : null;
}

/**
 * @title File attachment with help key
 */
@Component({
  selector: 'app-forms-file-attachment-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyFileAttachmentModule],
})
export class FormsFileAttachmentHelpKeyExampleComponent {
  protected attachment: FormControl<SkyFileItem | null | undefined>;

  protected formGroup: FormGroup<{
    attachment: FormControl<SkyFileItem | null | undefined>;
  }>;

  protected maxFileSize = 4000000;

  constructor() {
    this.attachment = new FormControl(undefined, {
      validators: [Validators.required, customValidator],
    });

    this.formGroup = inject(FormBuilder).group({
      attachment: this.attachment,
    });
  }

  protected onFileClick($event: SkyFileAttachmentClick): void {
    // Ensure we are only attempting to navigate to locally updated data for download.
    if ($event.file.url.startsWith('data:')) {
      const link = document.createElement('a');
      link.download = $event.file.file.name;
      link.href = $event.file.url;
      link.click();
    }
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-file-attachment
    acceptedTypes="application/pdf,image/jpeg,image/png,image/gif"
    formControlName="attachment"
    helpKey="file-help"
    hintText="Attach a .pdf, .gif, .png, or .jpeg file."
    labelText="Birth certificate"
    [maxFileSize]="maxFileSize"
    (fileClick)="onFileClick($event)"
  >
    @if (attachment.errors?.['invalidStartingLetter']) {
      <sky-form-error
        errorName="invalidStartingLetter"
        errorText="You may not upload a file that begins with the letter 'a'."
      />
    }
  </sky-file-attachment>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
---
component: 'file-drop'
description: 'Design guidelines, API documentation, and usage instructions for the file-drop component extracted from SKY UX documentation.'
---

# File Drop Component Guidelines

## Component Overview
The file drop element lets users attach multiple local files or link to external files, and it displays summary information about the attachments.

## Usage

### ✅ Use when

Use the file drop element when users need to upload multiple files or attach files from URLs rather than from local devices.

**✅ Do use a file drop element to upload more than one file.**

Use the file drop element when users need to add metadata about uploaded files.

**✅ Do use a file drop element to add metadata about uploaded files.**

### ❌ Don't use when

Don't use the file drop element when users only need to upload a single local file. Use the file attachment component instead.

## Anatomy

- Label
- Option to upload local files
- File name
- File size
- File preview
- Delete button
- Required field marker
- Help inline button
- Option to link to external files
- Hint text
- User-entered metadata

## Options

### Required field marker

When a file drop input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a file drop label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Link to external files

You can indicate whether to include the option to attach external files using their URLs.

### Hint text

To highlight important considerations about a file drop input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file drop input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file drop input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the file drop:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Metadata

You can include inputs for users to add metadata about file attachments.

### Validation

You can specify parameters for valid files, including file types, minimum and maximum sizes, and custom validation.

## Behavior and states

### File information

After users attach files, summary information appears below the file drop options. For local files, the default summary includes the file name, file size, file preview, and a delete button. For external files, the default summary includes the URL and a delete button. You can include additional inputs to display user-entered metadata.

### Responsiveness

The file drop element switches to a vertical layout in smaller viewports.

### States

## Related information

### Components

- Field group
- Help inline button
- File attachment

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsFileDropBasicExampleComponent

**Selector:** `app-forms-file-drop-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFileDropHelpKeyExampleComponent

**Selector:** `app-forms-file-drop-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyFileDropChange

**Package:** `@skyux/forms`

#### SkyFileDropComponent

Provides an element to attach multiple files where users can browse or drag and drop local files
or provide hyperlinks to external files. You can leave the contents of the component
blank to display the drop zone's default UI, or you can specify custom content to
display instead. When the module initializes, it disables the ability to drag and
drop files for the entire window to prevent the browser from opening files that are
accidentally dropped outside the target zone. If you implement your own file drop functionality
outside of the file drop component, you can place the `sky-file-drop-target` CSS class
on the element that receives drop events to exempt it from the drop exclusion rule.

**Selector:** `sky-file-drop`

**Package:** `@skyux/forms`

**Inputs:**

- `acceptedTypes`: `string | undefined` - The comma-delimited string literal of MIME types that users can attach.
By default, all file types are allowed. **[Required]**
- `acceptedTypesErrorMessage`: `string | undefined` - A custom error message to display when a file doesn't match the accepted types.
This replaces a default error message that lists all accepted types.
- `allowLinks`: `boolean | undefined` - Whether to display the option to attach files from URLs rather than from local devices. (default: false)
- `fileUploadAriaLabel`: `string | undefined` - The ARIA label for the file upload button. This provides a text equivalent for
screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label). (default: "Drag a file here or click to browse")
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the file attachment label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the file attachment label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `labelHidden`: `boolean` - Whether to hide `labelText` from view. (default: false)
- `labelText`: `string | undefined` - The text to display as the file attachment's label.
- `linkUploadAriaLabel`: `string | undefined` - The ARIA label for the link upload input. This sets the button's `aria-label` attribute to provide a text equivalent for
screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label). (default: "Link to a file")
- `linkUploadHintText`: `string | undefined` - The hint text for the link upload input.
- `multiple`: `boolean | undefined` - Whether users can drag and drop multiple files at the same time. (default: true)
- `noClick`: `boolean | undefined` - Whether to disable the option to browse for files to attach. (default: false)
- `required`: `boolean` - Whether uploading a file or link is required.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input elements so that screen readers announce an invalid state until the input element
is complete.
For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required). (default: false)
- `stacked`: `boolean` - Whether the file attachment is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the file attachment. (default: false)
- `validateFn`: `SkyFileValidateFn | undefined` - The custom validation function. This validation runs alongside the internal
file validation. This function takes a `SkyFileItem` object as a parameter.
The string returned is used as the error message in multi-file attachment.
- `maxFileSize`: `number` - The maximum size in bytes for valid files. (default: 500000)
- `minFileSize`: `number` - The minimum size in bytes for valid files. (default: 0)

**Outputs:**

- `filesChanged`: `EventEmitter<SkyFileDropChange>` - Fires when users add or remove files.
- `linkChanged`: `EventEmitter<SkyFileLink>` - Fires when users add or remove links.
- `linkInputBlur`: `EventEmitter<void>` - Fires when the link input box triggers a blur event.

#### SkyFileDropModule

**Package:** `@skyux/forms`

#### SkyFileDropHarnessFilters

A set of criteria that can be used to filter a list of `SkyFileDropHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFileDropHarness

Harness for interacting with a file drop component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### File drop with basic setup

**Selector:** `app-forms-file-drop-basic-example`

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
import { SkyFileDropModule, SkyFileItem, SkyFileLink } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<(SkyFileItem | SkyFileLink)[] | null | undefined>,
): ValidationErrors | null {
  if (control.value !== undefined && control.value !== null) {
    if (control.value.length > 3) {
      return { maxNumberOfFilesReached: true };
    }
  }
  return null;
}

/**
 * @title File drop with basic setup
 */
@Component({
  selector: 'app-forms-file-drop-basic-example',
  templateUrl: './example.component.html',
  imports: [
    SkyFileDropModule,
    SkyStatusIndicatorModule,
    FormsModule,
    ReactiveFormsModule,
  ],
})
export class FormsFileDropBasicExampleComponent {
  protected acceptedTypes = 'image/png,image/jpeg';
  protected hintText = 'Upload up to 3 files under 50MB.';
  protected inlineHelpContent =
    'Your logo appears in places such as authentication pages, student and parent portals, and extracurricular home pages.';
  protected labelText = 'Logo image';
  protected maxFileSize = 5242880;
  protected stacked = 'true';

  public fileDrop = new FormControl<
    (SkyFileItem | SkyFileLink)[] | null | undefined
  >(undefined, [Validators.required, customValidator]);
  public formGroup: FormGroup = inject(FormBuilder).group({
    fileDrop: this.fileDrop,
  });

  protected deleteFile(file: SkyFileItem | SkyFileLink): void {
    const index = this.fileDrop.value?.indexOf(file);

    if (index !== undefined && index !== -1) {
      this.fileDrop.value?.splice(index, 1);
      /*
        If you are adding custom validation through the form control,
        be sure to include this line after deleting a file from the form.
      */
      this.fileDrop.updateValueAndValidity();
    }
    // To ensure that empty arrays throw required errors, include this check.
    if (this.fileDrop.value?.length === 0) {
      this.fileDrop.setValue(null);
    }
  }

  protected validateFile(file: SkyFileItem): string | undefined {
    return file.file.name.startsWith('a')
      ? 'Upload a file that does not begin with the letter "a"'
      : undefined;
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-file-drop
    data-sky-id="logo-upload"
    linkUploadHintText="Start with http:// or https://"
    formControlName="fileDrop"
    [acceptedTypes]="acceptedTypes"
    [allowLinks]="true"
    [helpPopoverContent]="inlineHelpContent"
    [hintText]="hintText"
    [labelText]="labelText"
    [maxFileSize]="maxFileSize"
    [stacked]="stacked"
    [validateFn]="validateFile"
  >
    @if (fileDrop.errors?.['maxNumberOfFilesReached']) {
      <sky-form-error
        errorName="maxNumberOfFilesReached"
        errorText="Do not upload more than 3 files."
      />
    }
  </sky-file-drop>
</form>

@for (file of fileDrop.value; track file) {
  <sky-file-item [fileItem]="file" (deleteFile)="deleteFile($event)" />
}

```

#### File drop with help key

**Selector:** `app-forms-file-drop-help-key-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import {
  SkyFileDropChange,
  SkyFileDropModule,
  SkyFileItem,
  SkyFileLink,
} from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title File drop with help key
 */
@Component({
  selector: 'app-forms-file-drop-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyFileDropModule, SkyStatusIndicatorModule],
})
export class FormsFileDropHelpKeyExampleComponent {
  protected acceptedTypes = 'image/png,image/jpeg';
  protected allItems: (SkyFileItem | SkyFileLink)[] = [];
  protected hintText = '5 MB maximum';
  protected labelText = 'Logo image';
  protected maxFileSize = 5242880;
  protected rejectedFiles: SkyFileItem[] = [];
  protected required = true;
  protected stacked = 'true';

  #filesToUpload: SkyFileItem[] = [];
  #linksToUpload: SkyFileLink[] = [];

  protected deleteFile(file: SkyFileItem | SkyFileLink): void {
    this.#removeFromArray(this.allItems, file);
    this.#removeFromArray(this.#filesToUpload, file);
    this.#removeFromArray(this.#linksToUpload, file);
  }

  protected onFilesChanged(change: SkyFileDropChange): void {
    this.#filesToUpload = this.#filesToUpload.concat(change.files);
    this.rejectedFiles = change.rejectedFiles;
    this.allItems = this.allItems.concat(change.files);
  }

  protected onLinkChanged(change: SkyFileLink): void {
    this.#linksToUpload = this.#linksToUpload.concat(change);
    this.allItems = this.allItems.concat(change);
  }

  protected validateFile(file: SkyFileItem): string | undefined {
    return file.file.name.startsWith('a')
      ? 'Upload a file that does not begin with the letter "a"'
      : undefined;
  }

  #removeFromArray(
    items: (SkyFileItem | SkyFileLink)[],
    obj: SkyFileItem | SkyFileLink,
  ): void {
    if (items) {
      const index = items.indexOf(obj);

      if (index !== -1) {
        items.splice(index, 1);
      }
    }
  }
}

```

**Template:**

```html
<sky-file-drop
  helpKey="file-help"
  linkUploadHintText="Start with http:// or https://"
  [acceptedTypes]="acceptedTypes"
  [allowLinks]="true"
  [hintText]="hintText"
  [labelText]="labelText"
  [maxFileSize]="maxFileSize"
  [required]="required"
  [stacked]="stacked"
  [validateFn]="validateFile"
  (filesChanged)="onFilesChanged($event)"
  (linkChanged)="onLinkChanged($event)"
/>
@for (file of allItems; track file) {
  <div>
    <sky-file-item [fileItem]="file" (deleteFile)="deleteFile($event)" />
  </div>
}

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
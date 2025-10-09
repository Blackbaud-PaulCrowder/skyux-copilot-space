                  

 File drop
=========

The file drop element lets users attach multiple local files or link to external files, and it displays summary information about the attachments.

 Usage
------

### Use when

Use the file drop element when users need to upload multiple files or attach files from URLs rather than from local devices.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/use-multi.c01a33e902554ca64b00866d1d7e0b26.png)

Do use a file drop element to upload more than one file.

Use the file drop element when users need to add metadata about uploaded files.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/use-metadata.4be46c9f5ba23d84f61c37d44b30550b.png)

Do use a file drop element to add metadata about uploaded files.

### Don't use when

Don't use the file drop element when users only need to upload a single local file. Use the [file attachment component](/skyux/components/file-attachment.md) instead.

 Anatomy
--------

1

Label

2

Option to upload local files

3

File name

4

File size

5

File preview

6

Delete button

7

Required field marker (optional)

8

Help inline button (optional)

9

Option to link to external files (optional)

10

Hint text (optional)

11

User-entered metadata (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/anatomy.a3a96f9179ea916d3c36c5a02cf63757.png)

 Options
--------

### Required field marker

When a file drop input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

### Help inline button

When you need to supplement a file drop label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Link to external files

You can indicate whether to include the option to attach external files using their URLs.

### Hint text

To highlight important considerations about a file drop input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file drop input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the file drop input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the file drop:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/options-stacked.024ad5be28990b2b46d8d328f6ddda3d.png)

### Metadata

You can include inputs for users to add metadata about file attachments.

### Validation

You can specify parameters for valid files, including file types, minimum and maximum sizes, and custom validation.

 Behavior and states
--------------------

### File information

After users attach files, summary information appears below the file drop options. For local files, the default summary includes the file name, file size, file preview, and a delete button. For external files, the default summary includes the URL and a delete button. You can include additional inputs to display user-entered metadata.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/behavior-preview.857c6273dd7e820eec8fca5a981a9bcd.png)

### Responsiveness

The file drop element switches to a vertical layout in smaller viewports.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/behavior-responsive.26059504579953417c202b84ac811b35.png)

### States

Base

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/state-base.fcd75b8945a83901245ba59a26e14ed9.png)

Attached image

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/state-attached-image.816f6fd3e9d64b26dc97098400dcf934.png)

Attached non-image

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/state-attached-other.8e6f54cebde79a437351b60ccba2cfc4.png)

Attached link

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/file-attach/state-file-link.0eec0582fde6371b6b11c4050d58bfe1.png)

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [File attachment](/skyux/components/file-attachment.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/file-attachment/file-drop/file-drop.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFileDropModule
------------------

Type: Module

`import { SkyFileDropModule } from '@skyux/forms';`

 SkyFileDropComponent
---------------------

Type: Component

Selector: `sky-file-drop`

Provides an element to attach multiple files where users can browse or drag and drop local files or provide hyperlinks to external files. You can leave the contents of the component blank to display the drop zone's default UI, or you can specify custom content to display instead. When the module initializes, it disables the ability to drag and drop files for the entire window to prevent the browser from opening files that are accidentally dropped outside the target zone. If you implement your own file drop functionality outside of the file drop component, you can place the `sky-file-drop-target` CSS class on the element that receives drop events to exempt it from the drop exclusion rule.

### Inputs

#### `acceptedTypes: string | undefined`

Required

The comma-delimited string literal of MIME types that users can attach. By default, all file types are allowed.

#### `acceptedTypesErrorMessage: string | undefined`

A custom error message to display when a file doesn't match the accepted types. This replaces a default error message that lists all accepted types.

#### `allowLinks: boolean | undefined`

Whether to display the option to attach files from URLs rather than from local devices.

Default: `false`

#### `fileUploadAriaLabel: string | undefined`

The ARIA label for the file upload button. This provides a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"Drag a file here or click to browse"`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the file attachment label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the file attachment label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelHidden: boolean`

Whether to hide `labelText` from view.

Default: `false`

#### `labelText: string | undefined`

The text to display as the file attachment's label.

#### `linkUploadAriaLabel: string | undefined`

The ARIA label for the link upload input. This sets the button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"Link to a file"`

#### `linkUploadHintText: string | undefined`

The hint text for the link upload input.

#### `maxFileSize: number`

The maximum size in bytes for valid files.

Default: `500000`

#### `minFileSize: number`

The minimum size in bytes for valid files.

Default: `0`

#### `multiple: boolean | undefined`

Whether users can drag and drop multiple files at the same time.

Default: `true`

#### `noClick: boolean | undefined`

Whether to disable the option to browse for files to attach.

Default: `false`

#### `required: boolean`

Whether uploading a file or link is required. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input elements so that screen readers announce an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the file attachment is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the file attachment.

Default: `false`

#### `validateFn: SkyFileValidateFn | undefined`

The custom validation function. This validation runs alongside the internal file validation. This function takes a `SkyFileItem` object as a parameter. The string returned is used as the error message in multi-file attachment.

### Outputs

#### `filesChanged: EventEmitter<SkyFileDropChange>`

Fires when users add or remove files.

#### `linkChanged: EventEmitter<SkyFileLink>`

Fires when users add or remove links.

#### `linkInputBlur: EventEmitter<void>`

Fires when the link input box triggers a blur event.

 SkyFileItemComponent
---------------------

Type: Component

Selector: `sky-file-item`

### Inputs

#### `fileItem: SkyFileItem | SkyFileLink | undefined`

Required

The summary information to display about file attachments. For local files, the default summary includes the file name, file size, file preview, and a delete button. For external files, the default summary includes the URL and a delete button. You can include additional inputs to display user-entered metadata.

### Outputs

#### `deleteFile: EventEmitter<SkyFileItem | SkyFileLink>`

Fires when users select the delete button for an item. The deleted item is passed to the function.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyFileDropChange
------------------

Type: Interface

    interface SkyFileDropChange {
      files: SkyFileItem[];
      rejectedFiles: SkyFileItem[];
    }

### Properties

#### `files: SkyFileItem[]`

The array of files that were added or removed.

#### `rejectedFiles: SkyFileItem[]`

The array of files that were rejected.

 SkyFileLink
------------

Type: Interface

    interface SkyFileLink {
      url: string;
    }

### Properties

#### `url: string`

The URL for the linked file.

 SkyFileItem
------------

Type: Interface

    interface SkyFileItem {
      errorParam?: string;
      errorType?: SkyFileItemErrorType;
      file: File;
      url: string;
    }

### Properties

#### `errorParam?: string`

Additional parameters about the error that caused the file to be rejected.

#### `errorType?: SkyFileItemErrorType`

The type of error that caused the file to be rejected.

#### `file: File`

The object that was added or removed.

#### `url: string`

The [data URL](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs) for the file that was added or removed.

 SkyFileItemErrorType
---------------------

Type: Type alias

The type of error that was thrown.

    type SkyFileItemErrorType = "fileType" | "minFileSize" | "maxFileSize" | "validate"

 SkyFileValidateFn
------------------

Type: Type alias

Custom validation run on each file uploaded. The string returned is used as the error message in multi-file attachment.

    type SkyFileValidateFn = (file: SkyFileItem) => string | undefined

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFileDropHarness
-------------------

Type: Class

`import { SkyFileDropHarness } from '@skyux/forms/testing';`

Harness for interacting with a file drop component in tests.

### Methods

#### `clickFileDropTarget(): Promise<void>`

Clicks the file drop target.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `clickLinkUploadDoneButton(): Promise<void>`

Clicks the link upload `Done` button'.

#### Returns

`Promise<void>`

#### `enterLinkUploadText(link: string): Promise<void>`

Enters text into the link upload input.

#### Parameters

##### `link: string`

#### Returns

`Promise<void>`

#### `getAcceptedTypes(): Promise<null | string>`

Gets the accepted file types.

#### Returns

`Promise<null | string>`

#### `getFileUploadAriaLabel(): Promise<null | string>`

Gets the aria-label for the file upload button.

#### Returns

`Promise<null | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help inline popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help inline popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the label text.

#### Returns

`Promise<string>`

#### `getLinkUploadAriaLabel(): Promise<null | string>`

Gets the link upload aria-label.

#### Returns

`Promise<null | string>`

#### `getLinkUploadHintText(): Promise<undefined | string>`

Gets the link upload hint text.

#### Returns

`Promise<undefined | string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether a custom form error has fired.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasFileTypeError(): Promise<boolean>`

Whether the file type error has fired.

#### Returns

`Promise<boolean>`

#### `hasMaxFileSizeError(): Promise<boolean>`

Whether the max file size error has fired.

#### Returns

`Promise<boolean>`

#### `hasMinFileSizeError(): Promise<boolean>`

Whether the min file size error has fired.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required error has fired.

#### Returns

`Promise<boolean>`

#### `hasValidateFnError(): Promise<boolean>`

Whether the validate error from the customer validation has fired.

#### Returns

`Promise<boolean>`

#### `isLabelHidden(): Promise<boolean>`

Whether label text is hidden.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether file drop is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether file drop has stacked enabled.

#### Returns

`Promise<boolean>`

#### `loadFile(file: File): Promise<void>`

Loads a single file. Be sure to include `provideSkyFileReaderTesting` as a provider when calling this function in tests.

#### Parameters

##### `file: File`

#### Returns

`Promise<void>`

#### `loadFiles(files: null | File[]): Promise<void>`

Loads multiple files. Be sure to include `provideSkyFileReaderTesting` as a provider when calling this function in tests.

#### Parameters

##### `files: null | File[]`

#### Returns

`Promise<void>`

#### `SkyFileDropHarness.with(filters: SkyFileDropHarnessFilters): HarnessPredicate<SkyFileDropHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFileDropHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFileDropHarnessFilters`

#### Returns

`HarnessPredicate<SkyFileDropHarness>`

 SkyFileDropHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFileDropHarness` instances.

    interface SkyFileDropHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFileItemHarness
-------------------

Type: Class

`import { SkyFileItemHarness } from '@skyux/forms/testing';`

Harness for interacting with a file item component in tests.

### Methods

#### `clickDeleteButton(): Promise<void>`

Clicks the delete button.

#### Returns

`Promise<void>`

#### `getFileName(): Promise<string>`

Gets the file name.

#### Returns

`Promise<string>`

#### `getFileSize(): Promise<string>`

Gets the file size.

#### Returns

`Promise<string>`

#### `SkyFileItemHarness.with(filters: SkyFileItemHarnessFilters): HarnessPredicate<SkyFileItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFileItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFileItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFileItemHarness>`

 SkyFileItemHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFileItemHarness` instances.

    interface SkyFileItemHarnessFilters {
      dataSkyId?: string | RegExp;
      fileName: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `fileName: string`

Finds files whose file name matches this value.

 provideSkyFileAttachmentTesting
--------------------------------

Type: Function

Provides mocks for file attachment testing.

### Example

    TestBed.configureTestingModule({

    function provideSkyFileAttachmentTesting(): Provider[]
                  

 File attachment
===============

The file attachment element lets users attach a single local file.

 Usage
------

### Use when

Use the file attachment input when users need to upload a single local file.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/use.866f878b055dccf47d296843fc5ea3c5.png)

Do use the file attachment input to upload one file.

### Don't use when

Don't use the file attachment input when users need to link to a URL to attach an external file. Use [the file drop component](/skyux/components/file-drop.md) instead.

Don't use the file attachment input to upload multiple local files. Use [the file drop component](/skyux/components/file-drop.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/dont-use-multi.8d94e340d046159a066151cc61748664.png)

Don't use file attachment inputs to upload more than one local file.

 Anatomy
--------

### Before file is attached

1

Label

2

File attachment button

3

Required field marker  (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/anatomy-no-file.b9affec567368b11feca6d1a3a7204d7.png)

### After file is attached

1

Preview image

2

File name

3

Delete button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/anatomy-file.d0663c6f7601320208cdb052e10a26a1.png)

 Options
--------

### Required field marker

When a file attachment input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a file attachment label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file attachment input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the file attachment input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the file attachment:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/options-stacked.3a5b567f8348f79be437e3406b134abc.png)

 Behavior and states
--------------------

### Image preview

When users attach images, a small preview appears below the replace file button.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/behavior-preview.62f187ec2f665ed9a682622fa67e52cd.png)

### File link

When users attach a file, the file name displays as a link beside the replace file button. You must bind an action to the click event to prevent a dead link and to allow users to download the file.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/single-file-attach/behavior-file-link.5edddced7061fa48f874cd442c2bb5b3.png)

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [File drop](/skyux/components/file-drop.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/file-attachment/file-attachment/file-attachment.module.ts#L16) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFileAttachmentModule
------------------------

Type: Module

`import { SkyFileAttachmentModule } from '@skyux/forms';`

 SkyFileAttachmentComponent
---------------------------

Type: Component

Selector: `sky-file-attachment`

Provides an element to attach a single local file.

### Inputs

#### `acceptedTypes: string | undefined`

The comma-delimited string literal of MIME types that users can attach. By default, all file types are allowed.

#### `acceptedTypesErrorMessage: string | undefined`

A custom error message to display when a file doesn't match the accepted types. This replaces a default error message that lists all accepted types.

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the single file attachment label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the single file attachment label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelHidden: boolean`

Whether to hide `labelText` from view.

Default: `false`

#### `labelText: string | undefined`

The text to display as the file attachment's label.

#### `maxFileSize: number`

The maximum size in bytes for valid files.

Default: `500000`

#### `minFileSize: number`

The minimum size in bytes for valid files.

Default: `0`

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the single file attachment is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the single file attachment.

Default: `false`

#### `validateFn: SkyFileValidateFn | undefined`

Warning: **Deprecated.** Add a custom Angular `Validator` function to the `FormControl` instead.

The custom validation function. This validation runs alongside the internal file validation. This function takes a `SkyFileItem` object as a parameter.

### Outputs

#### `fileChange: EventEmitter<SkyFileAttachmentChange>`

Warning: **Deprecated.** Subscribe to the form control's `valueChanges` event instead.

Fires when users add or remove files.

#### `fileClick: EventEmitter<SkyFileAttachmentClick>`

Fires when users select the file name link. Make sure to bind the event. If you do not, the file name link will be a dead link.

 SkyFileAttachmentLabelComponent
--------------------------------

Type: Component

Selector: `sky-file-attachment-label`

Warning: **Deprecated.** Use the `labelText` input on the single file attachment component instead.

Displays a label above the file attachment element. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-file-attachment-label` element and a `sky-control-help` CSS class on that help button element.

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

 SkyFileAttachmentChange
------------------------

Type: Interface

    interface SkyFileAttachmentChange {
      file?: SkyFileItem;
    }

### Properties

#### `file?: SkyFileItem`

The file that was added, or undefined if the file was removed.

 SkyFileAttachmentClick
-----------------------

Type: Interface

    interface SkyFileAttachmentClick {
      file: SkyFileItem;
    }

### Properties

#### `file: SkyFileItem`

The file that was clicked.

 SkyFileItemErrorType
---------------------

Type: Type alias

The type of error that was thrown.

    type SkyFileItemErrorType = "fileType" | "minFileSize" | "maxFileSize" | "validate"

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

 SkyFileValidateFn
------------------

Type: Type alias

Custom validation run on each file uploaded. The string returned is used as the error message in multi-file attachment.

    type SkyFileValidateFn = (file: SkyFileItem) => string | undefined

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFileAttachmentHarness
-------------------------

Type: Class

`import { SkyFileAttachmentHarness } from '@skyux/forms/testing';`

Harness for interacting with a file attachment component in tests.

### Methods

#### `attachFile(file: File): Promise<void>`

Attaches a file. Be sure to include `provideSkyFileReaderTesting` as a provider when calling this function in tests.

#### Parameters

##### `file: File`

#### Returns

`Promise<void>`

#### `clickAttachedFile(): Promise<void>`

Clicks the attached file to download it.

#### Returns

`Promise<void>`

#### `clickAttachedFileDeleteButton(): Promise<void>`

Clicks the attached file's delete button.

#### Returns

`Promise<void>`

#### `clickAttachFileButton(): Promise<void>`

Clicks the attach file button if it is visible.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `clickReplaceFileButton(): Promise<void>`

Clicks the replace file button in default theme.

#### Returns

`Promise<void>`

#### `getAcceptedTypes(): Promise<null | string>`

Gets the accepted file types.

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

Gets the file attachment label.

#### Returns

`Promise<string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether a custom error has fired.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasFileTypeError(): Promise<boolean>`

Whether the wrong file type error has fired.

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

#### `isDisabled(): Promise<boolean>`

Whether file attachment is disabled.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether file attachment is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether file attachment has stacked enabled.

#### Returns

`Promise<boolean>`

#### `SkyFileAttachmentHarness.with(filters: SkyFileAttachmentHarnessFilters): HarnessPredicate<SkyFileAttachmentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFileAttachmentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFileAttachmentHarnessFilters`

#### Returns

`HarnessPredicate<SkyFileAttachmentHarness>`

 SkyFileAttachmentHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFileAttachmentHarness` instances.

    interface SkyFileAttachmentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 provideSkyFileAttachmentTesting
--------------------------------

Type: Function

Provides mocks for file attachment testing.

### Example

    TestBed.configureTestingModule({

    function provideSkyFileAttachmentTesting(): Provider[]
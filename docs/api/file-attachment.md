---
component: 'file-attachment'
type: 'api-documentation'
description: 'API documentation for the file-attachment component including components, interfaces, and types.'
---

# File Attachment API Documentation

## Components and Directives

#### FormsFileAttachmentBasicExampleComponent

**Selector:** `app-forms-file-attachment-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFileAttachmentHelpKeyExampleComponent

**Selector:** `app-forms-file-attachment-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyFileAttachmentLabelComponent

Displays a label above the file attachment element. To display a help button
beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-file-attachment-label` element and a `sky-control-help` CSS class
on that help button element.

**Selector:** `sky-file-attachment-label`

**Package:** `@skyux/forms`

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
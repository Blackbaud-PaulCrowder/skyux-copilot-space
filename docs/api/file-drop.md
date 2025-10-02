---
component: 'file-drop'
type: 'api-documentation'
description: 'API documentation for the file-drop component including components, interfaces, and types.'
---

# File Drop API Documentation

## Components and Directives

#### FormsFileDropBasicExampleComponent

**Selector:** `app-forms-file-drop-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFileDropHelpKeyExampleComponent

**Selector:** `app-forms-file-drop-help-key-example`

**Package:** `@skyux/code-examples`

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
By default, all file types are allowed.
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
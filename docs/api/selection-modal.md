---
component: 'selection-modal'
type: 'api-documentation'
description: 'API documentation for the selection-modal component including components, interfaces, and types.'
---

# Selection Modal API Documentation

## Components and Directives

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

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
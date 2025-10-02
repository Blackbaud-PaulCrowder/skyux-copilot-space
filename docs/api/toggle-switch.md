---
component: 'toggle-switch'
type: 'api-documentation'
description: 'API documentation for the toggle-switch component including components, interfaces, and types.'
---

# Toggle Switch API Documentation

## Components and Directives

#### FormsToggleSwitchBasicExampleComponent

**Selector:** `app-forms-toggle-switch-basic-example`

**Package:** `@skyux/code-examples`

#### FormsToggleSwitchHelpKeyExampleComponent

**Selector:** `app-forms-toggle-switch-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyToggleSwitchLabelComponent

Specifies the label to display beside the toggle switch. To display a help button beside the label, include a help
button element, such as `sky-help-inline`, in the `sky-toggle-switch` element and a `sky-control-help` CSS class on
that help button element.

**Selector:** `sky-toggle-switch-label`

**Package:** `@skyux/forms`

#### SkyToggleSwitchComponent

**Selector:** `sky-toggle-switch`

**Package:** `@skyux/forms`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to disable the toggle switch on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the toggle switch label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the toggle switch. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `labelHidden`: `boolean` - Whether to hide `labelText` from view. (default: false)
- `labelText`: `string | undefined` - The text to display as the toggle switch's label.
- `tabIndex`: `number | undefined` - The tab index for the toggle switch. If not defined, the index is set to the position
of the toggle switch on load. (default: 0)
- `ariaLabel`: `string | undefined` - The ARIA label for the toggle switch. This sets the `aria-label`
attribute to provide a text equivalent for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Activate annual fundraiser" for a toggle switch that activates and deactivates an annual fundraiser. Context is especially important if multiple toggle switches are in close proximity.
When the `sky-toggle-switch-label` component displays a visible label, this property is only necessary if that label requires extra context.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `checked`: `boolean` - Whether the toggle switch is selected. (default: false)

**Outputs:**

- `toggleChange`: `EventEmitter<SkyToggleSwitchChange>` - Fires when the checked state of a toggle switch changes.
---
component: 'help-inline'
type: 'api-documentation'
description: 'API documentation for the help-inline component including components, interfaces, and types.'
---

# Help Inline API Documentation

## Components and Directives

#### HelpInlineActionClickExampleComponent

**Selector:** `app-help-inline-action-click-example`

**Package:** `@skyux/code-examples`

#### HelpInlineHelpKeyExampleComponent

**Selector:** `app-help-inline-help-key-example`

**Package:** `@skyux/code-examples`

#### HelpInlinePopoverExampleComponent

**Selector:** `app-help-inline-popover-example`

**Package:** `@skyux/code-examples`

#### SkyHelpInlineComponent

Inserts a help button beside an element, such as a field, to display contextual information about the element.

**Selector:** `sky-help-inline`

**Package:** `@skyux/help-inline`

**Inputs:**

- `ariaControls`: `string | undefined` - The ID of the element that the help inline button controls.
This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure).
For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).
- `ariaExpanded`: `boolean | undefined` - Whether an element or popover controlled by the help inline button is expanded. If popoverContent is specified,
this value is overridden with popover expanded status.
- `ariaLabel`: `string | undefined` - The ARIA label for the help inline button. This sets the button's `aria-label` to provide a text equivalent for screen readers.
Will be overridden if label text is set. (default: "Show help content")
- `helpKey`: `string | undefined` - A unique key that identifies the [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help) content to display when the button is clicked.
- `labelledBy`: `string | undefined` - The ID of the element associated with the help inline button. This is used to set the button's `aria-labelledby`
to provides a text equivalent for screen readers. Takes precedence over `ariaLabel` and `labelText` inputs.
- `popoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, clicking the help inline button opens a popover with this content and optional title.
- `popoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `popoverContent` is
also specified.
- `labelText`: `string | undefined` - The label of the component the help inline button is attached to.

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when the user clicks the help inline button.
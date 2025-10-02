---
component: 'dropdown'
type: 'api-documentation'
description: 'API documentation for the dropdown component including components, interfaces, and types.'
---

# Dropdown API Documentation

## Components and Directives

#### PopoversDropdownBasicExampleComponent

**Selector:** `app-popovers-dropdown-basic-example`

**Package:** `@skyux/code-examples`

#### SkyDropdownButtonComponent

Specifies the button for the dropdown menu.

**Selector:** `sky-dropdown-button`

**Package:** `@skyux/popovers`

#### SkyDropdownItemComponent

Specifies the items to display on the dropdown menu.

**Selector:** `sky-dropdown-item`

**Package:** `@skyux/popovers`

**Inputs:**

- `ariaRole`: `string` - The ARIA role for the dropdown menu item
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating how the item functions and what it controls. For information about
how an ARIA role indicates what an item represents on a web page, see the
[WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles). (default: "menuitem")

#### SkyDropdownMenuComponent

Creates a menu that contains dropdown menu items.

**Selector:** `sky-dropdown-menu`

**Package:** `@skyux/popovers`

**Inputs:**

- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the dropdown menu. This sets the dropdown menu's `aria-labelledby` attribute to provide a text equivalent for
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `ariaRole`: `string` - The ARIA role for the dropdown menu
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating how the dropdown menu functions and what it controls. The dropdown button
inherits this value to set its `aria-haspopup` property. For information
about how an ARIA role indicates what an item represents on a web page, see the
[WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles). (default: "menu")
- `useNativeFocus`: `boolean` - Whether to use the browser's native focus function when users navigate through menu
items with the keyboard. To disable the native focus function, set this property to `false`.
For example, to let users interact with the dropdown menu but keep the keyboard focus on a
different element, set this property to `false`. (default: true)

**Outputs:**

- `menuChanges`: `EventEmitter<SkyDropdownMenuChange>` - Fires when the dropdown menu's active index or selected item changes. This event provides an
observable to emit changes, and the response is of
the SkyDropdownMenuChange type.

#### SkyDropdownTriggerDirective

**Selector:** `[skyDropdownTrigger]`

**Package:** `@skyux/popovers`

#### SkyDropdownComponent

Creates a dropdown menu that displays menu items that users may select.

**Selector:** `sky-dropdown`

**Package:** `@skyux/popovers`

**Inputs:**

- `messageStream`: `Subject<SkyDropdownMessage> | undefined` - The observable that sends commands to the dropdown. The commands should respect
the [[SkyDropdownMessage]] type.
- `buttonStyle`: `string` - The background color for the dropdown button. Available values are `default`,
`primary`, and `link`. These values set the background color and hover behavior from the
[secondary and primary button classes](https://developer.blackbaud.com/skyux/components/button) respectively. (default: "default")
- `buttonType`: `SkyDropdownButtonType` - The type of button to render as the dropdown's trigger element. To display a button
with a caret, specify `'select'` and render the button text or icon in a
`sky-dropdown-button` element. To display a round button with an ellipsis, specify
`'context-menu'`. (default: "select")
- `disabled`: `boolean | undefined` - Whether to disable the dropdown button. (default: false)
- `horizontalAlignment`: `SkyDropdownHorizontalAlignment` - The horizontal alignment of the dropdown menu in relation to the dropdown button. (default: "left")
- `label`: `string | undefined` - The ARIA label for the dropdown. This sets the dropdown's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility). If multiple dropdowns with no label or the same label appear on the same page,
they must have unique ARIA labels that provide context, such as "Context menu for Robert Hernandez" or "Edit Robert Hernandez."
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `title`: `string | undefined` - The title to display in a tooltip when users hover the mouse over the dropdown button.
- `trigger`: `SkyDropdownTriggerType` - How users interact with the dropdown button to expose the dropdown menu.
We recommend the default `click` value because the `hover` value can pose
[accessibility](https://developer.blackbaud.com/skyux/learn/accessibility) issues
for users on touch devices such as phones and tablets. (default: "click")
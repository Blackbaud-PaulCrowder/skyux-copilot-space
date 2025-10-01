---
component: 'dropdown'
description: 'Design guidelines, API documentation, and usage instructions for the dropdown component extracted from SKY UX documentation.'
---

# Dropdown Component Guidelines

## Component Overview
Dropdown buttons display menus that group sets of actions or functions.

## Usage

### ✅ Use when

Use dropdowns when users require access to multiple, related actions or when users require access to multiple, unrelated actions and you do not have room for multiple buttons.

**✅ Do use dropdowns to let users access multiple actions.**

Use context-menu dropdowns when actions affect individual items in a list.

For details on when to include a delete action in a context-menu dropdown, see the manage data guidelines.

**✅ Do use context-menu dropdowns with items in a list.**

Use icon-only dropdowns when you do not have room for text labels. For example, use icon-only dropdowns in list toolbars when screen widths are narrow.

**✅ Do use icon-only dropdowns when you do not have space for labels.**

### ❌ Don't use when

Don't use dropdowns as form inputs. Use HTML <select> fields instead.

**❌ Don't use dropdowns as form inputs.**

## Anatomy

- Dropdown button
- Dropdown menu
- Action

## Options

### Button types

### Button styles

Dropdown buttons can use the default or primary styles inherited from SKY UX buttons. For details about when to use the primary style, see the primary action guidelines.

## Behavior and states

### Behavior

The popover component defines the behavior of dropdown menus.

### States

Dropdown buttons inherit the styling for states such as hover and disabled from SKY UX buttons.

## Content

### Dropdown menu action text

For actions that clearly apply to the object associated with the context menu, use the following format for the action wording:

<Verb>

For dropdown buttons with one type of action, use the following format:

Button text: <Verb>

Menu item: <Direct object>

For dropdown buttons with more than one type of action, use the following format:

Button icon: fa-ellipsis-hsky-i-ellipsis

Button text: More

Menu item: <Verb> <direct object>

## Layout

### Placement

Place context-menu dropdowns to the left of all row-specific content but to the right of all list controls, such as expand-collapse actions in tree views and checkboxes in grids or repeaters.

Default dropdowns are positioned with the same alignment and margins as SKY UX buttons.

**✅ Do put context-menu dropdowns to the left of all row-specific content in lists.**

### Menu items

Organize menu items to place the most important or frequently used options at the top of the list and the least important or least frequently used items at the bottom.

## Related information

### Components

- Buttons
- Popovers

### Guidelines

- Buttons and links

## API Documentation

### Components and Directives

#### PopoversDropdownBasicExampleComponent

**Selector:** `app-popovers-dropdown-basic-example`

**Package:** `@skyux/code-examples`

#### SkyColorpickerDropdownHarnessFilters

A set of criteria that can be used to filter a list of `SkyColorpickerDropdownHarness` instances.

**Package:** `@skyux/colorpicker/testing`

#### SkyColorpickerDropdownHarness

Harness for interacting with colorpicker dropdown in tests.

**Package:** `@skyux/colorpicker/testing`

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

#### SkyDropdownModule

**Package:** `@skyux/popovers`

#### SkyDropdownButtonType

**Package:** `@skyux/popovers`

#### SkyDropdownHorizontalAlignment

The horizontal alignment for the dropdown.

**Package:** `@skyux/popovers`

#### SkyDropdownMenuChange

Specifies menu items, including the selected one.

**Package:** `@skyux/popovers`

#### SkyDropdownMessageType

The type of message to send.

**Package:** `@skyux/popovers`

#### SkyDropdownMessage

Specifies the type of message to send to the dropdown component.

**Package:** `@skyux/popovers`

#### SkyDropdownTriggerType

How users interact with the dropdown button to expose the dropdown menu.

**Package:** `@skyux/popovers`

#### SkyDropdownFixture

Provides information for and interaction with a SKY UX dropdown component.
By using the fixture API, a test insulates itself against updates to the internals
of a component, such as changing its DOM structure.

**Package:** `@skyux/popovers/testing`

⚠️ **This component is deprecated.**

#### SkyDropdownTestingModule

**Package:** `@skyux/popovers/testing`

#### SkyPopoversFixtureDropdownItem

**Package:** `@skyux/popovers/testing`

#### SkyPopoversFixtureDropdownMenu

**Package:** `@skyux/popovers/testing`

#### SkyPopoversFixtureDropdown

**Package:** `@skyux/popovers/testing`

#### SkyDropdownHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownHarness

Harness for interacting with a dropdown component in tests.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownItemHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownItemHarness

Harness for interacting with a dropdown item component in tests.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownMenuHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownMenuHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownMenuHarness

Harness for interacting with a dropdown menu component in tests.

**Package:** `@skyux/popovers/testing`

### Code Examples

#### Dropdown with basic setup

**Selector:** `app-popovers-dropdown-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

interface DropdownItem {
  name: string;
  disabled: boolean;
}

/**
 * @title Dropdown with basic setup
 */
@Component({
  selector: 'app-popovers-dropdown-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDropdownModule],
})
export class PopoversDropdownBasicExampleComponent {
  protected items: DropdownItem[] = [
    { name: 'Option 1', disabled: false },
    { name: 'Disabled option', disabled: true },
    { name: 'Option 3', disabled: false },
    { name: 'Option 4', disabled: false },
    { name: 'Option 5', disabled: false },
  ];

  public actionClicked(action: string): void {
    alert(`You selected ${action}.`);
  }
}

```

**Template:**

```html
<sky-dropdown data-sky-id="dropdown-example" label="Test dropdown">
  <sky-dropdown-button> Show dropdown </sky-dropdown-button>
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>
<br />
<sky-dropdown buttonType="context-menu" label="Code example context menu">
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
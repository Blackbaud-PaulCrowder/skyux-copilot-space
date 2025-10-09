                    

 Dropdown
========

Dropdown buttons display menus that group sets of actions or functions.

 Usage
------

### Use when

Use dropdowns when users require access to multiple, related actions or when users require access to multiple, unrelated actions and you do not have room for multiple buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/usage-actions.56f53001c5cd0e4d16185bcb24c73fc0.png)

Do use dropdowns to let users access multiple actions.

Use context-menu dropdowns when actions affect individual items in a list.

For details on when to include a delete action in a context-menu dropdown, see the [manage data guidelines](/skyux/design/guidelines/managing-records.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/usage-context-menu.91a631070ee2694534359e47cce965dd.png)

Do use context-menu dropdowns with items in a list.

Use icon-only dropdowns when you do not have room for text labels. For example, use icon-only dropdowns in list toolbars when screen widths are narrow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/usage-icon-only-1.9ef33c2449a20807f180ea65f17fe68c.png)

Do use icon-only dropdowns when you do not have space for labels.

### Don't use when

Don't use dropdowns as form inputs. Use HTML `<select>` fields instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/usage-dont-input.6f166a247c0e3b1dc2d96375fc6252c9.png)

Don't use dropdowns as form inputs.

 Anatomy
--------

1

Dropdown button

2

Dropdown menu

3

Action

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/anatomy.c5cd72fff92e6f9eef4c76ec196cf6cc.png)

 Options
--------

### Button types

Default

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/option-type-text.aba1e718e05ebbc4b9ae050ced037e54.png)

Icon and text

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/option-type-text-icon.2604697ca1d6b2e5ed64a7ce6734b296.png)

Context menu

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/option-type-context.fe08d7bd6625d4295fab6883cfd4bd1f.png)

Icon only

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/option-type-icon-only.7677618454ea859aa5f85d966c7bcfa1.png)

### Button styles

Dropdown buttons can use the default or primary styles inherited from [SKY UX buttons](/skyux/components/button.md). For details about when to use the primary style, see the [primary action guidelines](/skyux/design/guidelines/page-layouts.md).

 Behavior and states
--------------------

### Behavior

The [popover](/skyux/components/popover.md) component defines the behavior of dropdown menus.

### States

Dropdown buttons inherit the styling for states such as hover and disabled from [SKY UX buttons](/skyux/components/button.md).

 Content
--------

### Dropdown menu action text

For actions that clearly apply to the object associated with the context menu, use the following format for the action wording:

<Verb>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/dropdown-content-1.392cfff3677a7a49aee4af8a0bec26be.png)

For dropdown buttons with one type of action, use the following format:

Button text: <Verb>

Menu item: <Direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/dropdown-content-2.06f447f77141ae0290bb28b148000e20.png)

For dropdown buttons with more than one type of action, use the following format:

Button icon: sky-i-ellipsis

Button text: More

Menu item: <Verb> <direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/dropdown-content-3.9c19df7ab01f66ea295e4209931cd560.png)

In addition, follow these guidelines for button text:

*   Use sentence-style capitalization.
*   Use singular direct objects for actions that apply to one item and plural direct objects for actions that apply to multiple items.
*   Don't append extra words such as “details.” For example, use “Edit constituent” rather than “Edit constituent details.”

 Layout
-------

### Placement

Place context-menu dropdowns to the left of all row-specific content but to the right of all list controls, such as expand-collapse actions in [tree views](/skyux/components/angular-tree.md) and checkboxes in [grids](/skyux/components/grid.md) or [repeaters](/skyux/components/repeater.md).

Default dropdowns are positioned with the same alignment and margins as [SKY UX buttons](/skyux/components/button.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/dropdown/dropdown-layout.eeaaa066752bf9ad4e0fed4ec2797fcc.png)

Do put context-menu dropdowns to the left of all row-specific content in lists.

### Menu items

Organize menu items to place the most important or frequently used options at the top of the list and the least important or least frequently used items at the bottom.

 Related information
--------------------

### Components

*   [Buttons](/skyux/components/button.md)
*   [Popovers](/skyux/components/popover.md)

### Guidelines

*   [Buttons and links](/skyux/design/guidelines/buttons-links.md)

 Installation
-------------

NPM package

`@skyux/popovers`[View in NPM](https://www.npmjs.com/package/@skyux/popovers) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/popovers/src/lib/modules/dropdown/dropdown.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/popovers`Copy None found.

 SkyDropdownModule
------------------

Type: Module

`import { SkyDropdownModule } from '@skyux/popovers';`

 SkyDropdownComponent
---------------------

Type: Component

Selector: `sky-dropdown`

Creates a dropdown menu that displays menu items that users may select.

### Inputs

#### `buttonStyle: string`

The background color for the dropdown button. Available values are `default`, `primary`, and `link`. These values set the background color and hover behavior from the [secondary and primary button classes](/skyux/components/button.md) respectively.

Default: `"default"`

#### `buttonType: SkyDropdownButtonType`

The type of button to render as the dropdown's trigger element. To display a button with a caret, specify `'select'` and render the button text or icon in a `sky-dropdown-button` element. To display a round button with an ellipsis, specify `'context-menu'`.

Default: `"select"`

#### `disabled: boolean | undefined`

Whether to disable the dropdown button.

Default: `false`

#### `horizontalAlignment: SkyDropdownHorizontalAlignment`

The horizontal alignment of the dropdown menu in relation to the dropdown button.

Default: `"left"`

#### `label: string | undefined`

The ARIA label for the dropdown. This sets the dropdown's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If multiple dropdowns with no label or the same label appear on the same page, they must have unique ARIA labels that provide context, such as "Context menu for Robert Hernandez" or "Edit Robert Hernandez." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `title: string | undefined`

The title to display in a tooltip when users hover the mouse over the dropdown button.

#### `trigger: SkyDropdownTriggerType`

Warning: **Deprecated.** We recommend against using this property. If you choose to use the deprecated `hover` value anyway, we recommend that you not use it in combination with the `title` property.

How users interact with the dropdown button to expose the dropdown menu. We recommend the default `click` value because the `hover` value can pose [accessibility](/skyux/learn/accessibility.md) issues for users on touch devices such as phones and tablets.

Default: `"click"`

 SkyDropdownButtonComponent
---------------------------

Type: Component

Selector: `sky-dropdown-button`

Specifies the button for the dropdown menu.

 SkyDropdownMenuComponent
-------------------------

Type: Component

Selector: `sky-dropdown-menu`

Creates a menu that contains dropdown menu items.

### Inputs

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the dropdown menu. This sets the dropdown menu's `aria-labelledby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string`

The ARIA role for the dropdown menu [to support accessibility](/skyux/learn/accessibility.md) by indicating how the dropdown menu functions and what it controls. The dropdown button inherits this value to set its `aria-haspopup` property. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"menu"`

 SkyDropdownItemComponent
-------------------------

Type: Component

Selector: `sky-dropdown-item`

Specifies the items to display on the dropdown menu.

### Inputs

#### `ariaRole: string`

The ARIA role for the dropdown menu item [to support accessibility](/skyux/learn/accessibility.md) by indicating how the item functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"menuitem"`

 SkyDropdownButtonType
----------------------

Type: Type alias

    type SkyDropdownButtonType = "select" | "context-menu" | "tab"

 SkyDropdownHorizontalAlignment
-------------------------------

Type: Type alias

The horizontal alignment for the dropdown.

    type SkyDropdownHorizontalAlignment = "left" | "center" | "right"

 SkyDropdownTriggerType
-----------------------

Type: Type alias

How users interact with the dropdown button to expose the dropdown menu.

    type SkyDropdownTriggerType = "click" | "hover"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDropdownHarness
-------------------

Type: Class

`import { SkyDropdownHarness } from '@skyux/popovers/testing';`

Harness for interacting with a dropdown component in tests.

### Methods

#### `clickDropdownButton(): Promise<void>`

Clicks the dropdown button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label value.

#### Returns

`Promise<null | string>`

#### `getButtonStyle(): Promise<string>`

Gets the dropdown button style.

#### Returns

`Promise<string>`

#### `getButtonType(): Promise<string>`

Gets the dropdown button type.

#### Returns

`Promise<string>`

#### `getDropdownMenu(): Promise<SkyDropdownMenuHarness>`

Gets the dropdown menu component.

#### Returns

`Promise<SkyDropdownMenuHarness>`

#### `getTitle(): Promise<null | string>`

Gets the hover tooltip text.

#### Returns

`Promise<null | string>`

#### `isDisabled(): Promise<boolean>`

Gets whether the dropdown is disabled.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Gets whether the dropdown menu is open.

#### Returns

`Promise<boolean>`

#### `SkyDropdownHarness.with(filters: SkyDropdownHarnessFilters): HarnessPredicate<SkyDropdownHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDropdownHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDropdownHarnessFilters`

#### Returns

`HarnessPredicate<SkyDropdownHarness>`

 SkyDropdownHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDropdownHarness` instances.

    interface SkyDropdownHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDropdownItemHarness
-----------------------

Type: Class

`import { SkyDropdownItemHarness } from '@skyux/popovers/testing';`

Harness for interacting with a dropdown item component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the dropdown item.

#### Returns

`Promise<void>`

#### `getAriaRole(): Promise<null | string>`

Gets the dropdown item role.

#### Returns

`Promise<null | string>`

#### `getText(): Promise<null | string>`

Gets the menu item text.

#### Returns

`Promise<null | string>`

#### `SkyDropdownItemHarness.with(filters: SkyDropdownItemHarnessFilters): HarnessPredicate<SkyDropdownItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDropdownItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDropdownItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyDropdownItemHarness>`

 SkyDropdownItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDropdownItemHarness` instances.

    interface SkyDropdownItemHarnessFilters {
      ariaRole?: string;
      dataSkyId?: string | RegExp;
      text?: string;
    }

### Properties

#### `ariaRole?: string`

Only find instances whose role matches the given value.

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `text?: string`

Only find instances whose text content matches the given value.

 SkyDropdownMenuHarness
-----------------------

Type: Class

`import { SkyDropdownMenuHarness } from '@skyux/popovers/testing';`

Harness for interacting with a dropdown menu component in tests.

### Methods

#### `clickOut(): Promise<void>`

Clicks out of the dropdown menu.

#### Returns

`Promise<void>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the `aria-labelledby` value.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the dropdown menu role.

#### Returns

`Promise<null | string>`

#### `getItem(filter: SkyDropdownItemHarnessFilters): Promise<SkyDropdownItemHarness>`

Gets a specific dropdown menu item based on the filter criteria.

#### Parameters

##### `filter: SkyDropdownItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDropdownItemHarness>`

#### `getItems(filters?: SkyDropdownItemHarnessFilters): Promise<SkyDropdownItemHarness[]>`

Gets an array of dropdown menu items based on the filter criteria. If no filter is provided, returns all dropdown menu items.

#### Parameters

##### `filters?: SkyDropdownItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDropdownItemHarness[]>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyDropdownMenuHarness.with(filters: SkyDropdownMenuHarnessFilters): HarnessPredicate<SkyDropdownMenuHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDropdownMenuHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDropdownMenuHarnessFilters`

#### Returns

`HarnessPredicate<SkyDropdownMenuHarness>`

 SkyDropdownMenuHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDropdownMenuHarness` instances.

    interface SkyDropdownMenuHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
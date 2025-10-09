                  

 Toggle switch
=============

The toggle switch lets users turn a SKY UX-themed switch "on" or "off." The change takes effect immediately.

 Usage
------

### Use when

Use toggles when users can toggle between two states or options, and the changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toggle/toggle-usage-1.61d2cb7bd1e92a9dc4c356b4a7320f07.png)

Do use toggles to alternate between two states when changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toggle/toggle-usage-2.4c44440b2409c060d19959053bfe28be.png)

Do use toggles to set binary states on multiple items.

### Don't use when

Don't use toggles when the options have significant consequences that the users need to confirm before changes take effect. Use a workflow where users must confirm the changes instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toggle/toggle-usage-3.4c1495e3a7be8e239eb463cb050b2208.png)

Don't use toggles for states with significant consequences.

Don't use toggles when the input is presented in a modal. Use [checkboxes](/skyux/components/checkbox.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toggle/toggle-usage-4.15fa24e5454816606631f55b6fa5dd4d.png)

Don't use toggles inside modals where they won't take effect immediately.

 Anatomy
--------

1

Toggle switch

2

Label (optional)

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toggle/toggle-anatomy.65702983ae748f080b38f002c75578e9.png)

 Options
--------

### Label

Text labels describe the properties that toggles control, and you can provide labels for both the selected and unselected states. Always include text labels unless other text clearly indicates the purpose of toggles. For example, when toggles are in grids, you can rely on column headings instead of text labels.

In scenarios where toggles may become disabled, always include labels for both the selected and unselected states to make those states clear to users.

### Help inline button

When you need to supplement a toggle switch label with additional information, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/toggle-switch/toggle-switch.module.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyToggleSwitchModule
----------------------

Type: Module

`import { SkyToggleSwitchModule } from '@skyux/forms';`

 SkyToggleSwitchComponent
-------------------------

Type: Component

Selector: `sky-toggle-switch`

### Inputs

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use the `labelText` input instead.

The ARIA label for the toggle switch. This sets the `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Activate annual fundraiser" for a toggle switch that activates and deactivates an annual fundraiser. Context is especially important if multiple toggle switches are in close proximity. When the `sky-toggle-switch-label` component displays a visible label, this property is only necessary if that label requires extra context. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `checked: boolean`

Whether the toggle switch is selected.

Default: `false`

#### `disabled: boolean | undefined`

Whether to disable the toggle switch on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the toggle switch label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the toggle switch. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `labelHidden: boolean`

Whether to hide `labelText` from view.

Default: `false`

#### `labelText: string | undefined`

The text to display as the toggle switch's label.

#### `tabIndex: number | undefined`

The tab index for the toggle switch. If not defined, the index is set to the position of the toggle switch on load.

Default: `0`

### Outputs

#### `toggleChange: EventEmitter<SkyToggleSwitchChange>`

Fires when the checked state of a toggle switch changes.

 SkyToggleSwitchLabelComponent
------------------------------

Type: Component

Selector: `sky-toggle-switch-label`

Warning: **Deprecated.** Use the `labelText` input on the toggle switch component instead.

Specifies the label to display beside the toggle switch. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-toggle-switch` element and a `sky-control-help` CSS class on that help button element.

 SkyToggleSwitchChange
----------------------

Type: Interface

Indicates whether the toggle switch is selected.

    interface SkyToggleSwitchChange {
      checked: boolean;
    }

### Properties

#### `checked: boolean`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyToggleSwitchHarness
-----------------------

Type: Class

`import { SkyToggleSwitchHarness } from '@skyux/forms/testing';`

Harness for interacting with a toggle switch component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the toggle switch.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the toggle switch in a checked state.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the toggle switch.

#### Returns

`Promise<void>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the toggle switch's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `isChecked(): Promise<boolean>`

Whether the toggle switch is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the toggle switch is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the toggle switch is focused.

#### Returns

`Promise<boolean>`

#### `uncheck(): Promise<void>`

Puts the toggle switch in an unchecked state.

#### Returns

`Promise<void>`

#### `SkyToggleSwitchHarness.with(filters: SkyToggleSwitchHarnessFilters): HarnessPredicate<SkyToggleSwitchHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyToggleSwitchHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyToggleSwitchHarnessFilters`

#### Returns

`HarnessPredicate<SkyToggleSwitchHarness>`

 SkyToggleSwitchHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyToggleSwitchHarness` instances.

    interface SkyToggleSwitchHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
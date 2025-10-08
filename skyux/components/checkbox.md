# Design

                  Skip to Main Content

 Checkbox
========

Checkboxes let users select multiple items from a short list of items.

 Usage
------

### Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-1.2ccbee78ed1195de5654aa725908d635.png)

Do use a checkbox when users must make a single yes/no decision.

Use checkbox groups when users must make multiple, related yes/no decisions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-3.772c7f4cf4b38525a592f3af8b484e3a.png)

Do use a checkbox group for multiple, related checkboxes.

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-2.b5beeddabfe59b96f97ed5ddf12a68f7.png)

Do use icon checkboxes when icons clearly communicate the options.

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-4.3435d079788bf4bbf82e8b02c3418b5a.png)

Do use checkboxes to enable conditional inputs as part of a task.

### Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different [selection input](/skyux/design/guidelines/form-design.md), such as a [lookup field](/skyux/components/lookup.md), instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.5.76e1e8659bc01c83e3988a8735b340f1.png)

Don't use a checkbox group for a homogenous list of more than 5 items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.75.b28d82a07fd6f474db0c993e31936af7.png)

Do use a lookup field to let users select items from a long, homogenous list.

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.6.01dca0c929ecf82b5b8a0f683ac1f9bf.png)

Do use checkbox groups for more than 5 checkboxes when the choices represent distinct decisions.

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use [toggle switch](/skyux/components/toggle-switch.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.1.f043c6cc4a485287b9d9b24beb14b8a5.png)

Don't use checkboxes to alternate between two states when changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.2.f31c8d06ba6d9a953e27fa9eaa29ba0b.png)

Do use toggle switches when changes take effect immediately.

Don't use a checkbox group for a lone checkbox in a form or [field group](/skyux/components/field-group.md).

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-5.b06b9ee82f9d92319efa6e7bba4d35ac.png)

Don't use a checkbox group for a lone checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-6.e7dc9ca88c4c9ddc46fc808d373234f2.png)

Do use an ungrouped checkbox within a form or field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-7.006dcb79da3b7168d9955fa05666c435.png)

Don't use an ungrouped checkbox next to a checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.24ec6cf356c263ec1e8a5cbb1bac97e5.png)

Do use a checkbox group for a lone checkbox next to a checkbox group.

 Anatomy
--------

### Individual checkbox

1

Checkbox

2

Label

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-anatomy.07fe9a203319f8db2cdedaf4bb35177e.png)

### Checkbox group

1

Label

2

Checkboxes

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-group-anatomy.7366139e6d55d56171fc04927f455984.png)

### Icon checkbox

1

Icon checkbox

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-icon-anatomy.e8cf1789a28ac8e1edfa2a35b4744c2e.png)

 Options
--------

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a checkbox group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-heading.639f4268dc24869dcb3ceeba34c03f48.png)

Checkbox group labels can be turned into HTML headings.

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

*   Constraints or requirements on a checkbox group
*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the checkbox group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

Also use `stacked` when an individual checkbox is immediately followed by another form input. However, don't use `stacked` when the checkbox is followed by one or more conditional fields. Use `sky-margin-stacked-sm` instead for closely related fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-1.8589348a67334a785313ffff87a36842.png)

If a checkbox group uses `headingLevel`, use `stacked` when the checkbox group is followed by a [field group](/skyux/components/field-group.md) or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-2.8232d9a4871fd76f1e2f3d1a2d4e029d.png)

 Content
--------

Make checkbox group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, checkbox group labels can use short sentences or sentence fragments.

For details about styling checkbox group labels as headings, see the "Headings" section above.

Similarly, make checkbox labels succinct and descriptive. When necessary, checkbox labels can use short sentences or sentence fragments.

 Layout
-------

Don't wrap a checkbox group inside a [field group](/skyux/component/field-group.md) component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.853c1e673416762512b56d55cb925f36.png)

Don't use a field group with a lone checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-10.389b289ade7642e0e90cb5bd28b2d460.png)

Do adjust the heading level and heading style of a checkbox group to match the hierarcy of field groups.

 Accessibility
--------------

Checkbox groups automatically create `<fieldset>`and `<legend>` elements based on their contents and label text.

In most cases, checkbox group labels aren't treated as HTML headings, but when necessary, you can specify a heading level and heading style. For example, when a lone checkbox group appears on a form with [field groups](/skyux/components/field-group.md), set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style that matches the semantic and visual hierarchy of the field group headings.

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/checkbox/checkbox.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCheckboxModule
------------------

Type: Module

`import { SkyCheckboxModule } from '@skyux/forms';`

 SkyCheckboxComponent
---------------------

Type: Component

Selector: `sky-checkbox`

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

### Inputs

#### `checkboxType: string`

Warning: **Deprecated.** The `checkboxType` input is no longer supported.

The background color type after users select a checkbox where the `icon` property displays an icon in place of the checkbox. The valid options correspond to [the label component's](/skyux/components/label.md) label types. `"info"` creates a blue background, `"success"` creates a green background, `"warning"` creates an orange background, and `"danger"` creates a red background.

Default: `"info"`

#### `checked: boolean`

Whether the checkbox is selected.

#### `disabled: boolean`

Whether the checkbox is disabled.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the checkbox. To group icon checkboxes like in the demo, place the checkboxes within a `sky-checkbox-group`.

#### `id: string | undefined`

The ID for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md) when the checkbox does not include a visible label. You must set this property for icon checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only. Specifying `labelText` also enables automatic error message handling for checkbox.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the checkbox. This sets the checkbox's `aria-labelledby` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md). If the checkbox does not include a visible label, use `label` instead.

#### `name: string`

The name for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete.

Default: `false`

#### `stacked: boolean`

Whether the checkbox is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group, set `stacked` on the checkbox group component instead.

Default: `false`

#### `tabindex: number | undefined`

The index for the checkbox. If not defined, the index is set to the position of the checkbox on load.

Default: `0`

### Outputs

#### `change: EventEmitter<SkyCheckboxChange>`

Fires when the selected value changes.

#### `checkedChange: Observable<boolean>`

Fires when users select or deselect the checkbox.

#### `disabledChange: Observable<boolean>`

Fires when the selected value changes.

 SkyCheckboxGroupComponent
--------------------------

Type: Component

Selector: `sky-checkbox-group`

Organizes checkboxes into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyCheckboxGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyCheckboxGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string`

The text to display as the checkbox group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox group fieldset legend. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the checkbox group is required.

Default: `false`

#### `stacked: boolean`

Whether the checkbox group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox group.

 SkyCheckboxLabelComponent
--------------------------

Type: Component

Selector: `sky-checkbox-label`

Warning: **Deprecated.** Use `labelText` input on `sky-checkbox-component` instead.

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button element.

 SkyCheckboxChange
------------------

Type: Interface

Fires when users select or deselect the checkbox.

    interface SkyCheckboxChange {
      checked?: boolean;
    }

### Properties

#### `checked?: boolean`

The value from the checkbox component.

 SkyCheckboxGroupHeadingLevel
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingLevel = 3 | 4 | 5

 SkyCheckboxGroupHeadingStyle
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingStyle = 3 | 4 | 5

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCheckboxHarness
-------------------

Type: Class

`import { SkyCheckboxHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the checkbox.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the checkbox in a checked state by toggling it if it is currently unchecked, or doing nothing if it is already checked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the checkbox.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the checkbox's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the checkbox's aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the checkbox's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the checkbox's name.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<null | string>`

Gets the checkbox's value.

#### Returns

`Promise<null | string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether the checkbox displays custom error.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the checkbox displays an error that it is required.

#### Returns

`Promise<boolean>`

#### `isChecked(): Promise<boolean>`

Whether the checkbox is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the checkbox is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the checkbox is focused.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether the checkbox is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the checkbox is stacked.

#### Returns

`Promise<boolean>`

#### `uncheck(): Promise<void>`

Puts the checkbox in an unchecked state by toggling it if it is currently checked, or doing nothing if it is already unchecked.

#### Returns

`Promise<void>`

#### `SkyCheckboxHarness.with(filters: SkyCheckboxHarnessFilters): HarnessPredicate<SkyCheckboxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxHarness>`

 SkyCheckboxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

    interface SkyCheckboxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyCheckboxGroupHarness
------------------------

Type: Class

`import { SkyCheckboxGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCheckbox(filter: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness>`

Gets a specific checkbox based on the filter criteria.

#### Parameters

##### `filter: SkyCheckboxHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyCheckboxHarness>`

#### `getCheckboxes(filters?: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness[]>`

Gets an array of checkboxes based on the filter criteria. If no filter is provided, returns all checkboxes.

#### Parameters

##### `filters?: SkyCheckboxHarnessFilters`

#### Returns

`Promise<SkyCheckboxHarness[]>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyCheckboxGroupHeadingLevel>`

The semantic heading level used for the checkbox group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyCheckboxGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyCheckboxGroupHeadingStyle>`

The heading style used for the checkbox group.

#### Returns

`Promise<SkyCheckboxGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the checkbox group's heading text. If `headingHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox group's hint text.

#### Returns

`Promise<string>`

#### `getRequired(): Promise<boolean>`

Whether the checkbox group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the checkbox group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the checkbox group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether all the checkboxes in a required group are unchecked.

#### Returns

`Promise<boolean>`

#### `SkyCheckboxGroupHarness.with(filters: SkyCheckboxGroupHarnessFilters): HarnessPredicate<SkyCheckboxGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxGroupHarness>`

 SkyCheckboxGroupHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

    interface SkyCheckboxGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Checkbox
========

Checkboxes let users select multiple items from a short list of items.

 Usage
------

### Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-1.2ccbee78ed1195de5654aa725908d635.png)

Do use a checkbox when users must make a single yes/no decision.

Use checkbox groups when users must make multiple, related yes/no decisions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-3.772c7f4cf4b38525a592f3af8b484e3a.png)

Do use a checkbox group for multiple, related checkboxes.

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-2.b5beeddabfe59b96f97ed5ddf12a68f7.png)

Do use icon checkboxes when icons clearly communicate the options.

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-4.3435d079788bf4bbf82e8b02c3418b5a.png)

Do use checkboxes to enable conditional inputs as part of a task.

### Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different [selection input](/skyux/design/guidelines/form-design.md), such as a [lookup field](/skyux/components/lookup.md), instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.5.76e1e8659bc01c83e3988a8735b340f1.png)

Don't use a checkbox group for a homogenous list of more than 5 items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.75.b28d82a07fd6f474db0c993e31936af7.png)

Do use a lookup field to let users select items from a long, homogenous list.

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.6.01dca0c929ecf82b5b8a0f683ac1f9bf.png)

Do use checkbox groups for more than 5 checkboxes when the choices represent distinct decisions.

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use [toggle switch](/skyux/components/toggle-switch.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.1.f043c6cc4a485287b9d9b24beb14b8a5.png)

Don't use checkboxes to alternate between two states when changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.2.f31c8d06ba6d9a953e27fa9eaa29ba0b.png)

Do use toggle switches when changes take effect immediately.

Don't use a checkbox group for a lone checkbox in a form or [field group](/skyux/components/field-group.md).

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-5.b06b9ee82f9d92319efa6e7bba4d35ac.png)

Don't use a checkbox group for a lone checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-6.e7dc9ca88c4c9ddc46fc808d373234f2.png)

Do use an ungrouped checkbox within a form or field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-7.006dcb79da3b7168d9955fa05666c435.png)

Don't use an ungrouped checkbox next to a checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.24ec6cf356c263ec1e8a5cbb1bac97e5.png)

Do use a checkbox group for a lone checkbox next to a checkbox group.

 Anatomy
--------

### Individual checkbox

1

Checkbox

2

Label

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-anatomy.07fe9a203319f8db2cdedaf4bb35177e.png)

### Checkbox group

1

Label

2

Checkboxes

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-group-anatomy.7366139e6d55d56171fc04927f455984.png)

### Icon checkbox

1

Icon checkbox

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-icon-anatomy.e8cf1789a28ac8e1edfa2a35b4744c2e.png)

 Options
--------

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a checkbox group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-heading.639f4268dc24869dcb3ceeba34c03f48.png)

Checkbox group labels can be turned into HTML headings.

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

*   Constraints or requirements on a checkbox group
*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the checkbox group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

Also use `stacked` when an individual checkbox is immediately followed by another form input. However, don't use `stacked` when the checkbox is followed by one or more conditional fields. Use `sky-margin-stacked-sm` instead for closely related fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-1.8589348a67334a785313ffff87a36842.png)

If a checkbox group uses `headingLevel`, use `stacked` when the checkbox group is followed by a [field group](/skyux/components/field-group.md) or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-2.8232d9a4871fd76f1e2f3d1a2d4e029d.png)

 Content
--------

Make checkbox group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, checkbox group labels can use short sentences or sentence fragments.

For details about styling checkbox group labels as headings, see the "Headings" section above.

Similarly, make checkbox labels succinct and descriptive. When necessary, checkbox labels can use short sentences or sentence fragments.

 Layout
-------

Don't wrap a checkbox group inside a [field group](/skyux/component/field-group.md) component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.853c1e673416762512b56d55cb925f36.png)

Don't use a field group with a lone checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-10.389b289ade7642e0e90cb5bd28b2d460.png)

Do adjust the heading level and heading style of a checkbox group to match the hierarcy of field groups.

 Accessibility
--------------

Checkbox groups automatically create `<fieldset>`and `<legend>` elements based on their contents and label text.

In most cases, checkbox group labels aren't treated as HTML headings, but when necessary, you can specify a heading level and heading style. For example, when a lone checkbox group appears on a form with [field groups](/skyux/components/field-group.md), set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style that matches the semantic and visual hierarchy of the field group headings.

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/checkbox/checkbox.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCheckboxModule
------------------

Type: Module

`import { SkyCheckboxModule } from '@skyux/forms';`

 SkyCheckboxComponent
---------------------

Type: Component

Selector: `sky-checkbox`

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

### Inputs

#### `checkboxType: string`

Warning: **Deprecated.** The `checkboxType` input is no longer supported.

The background color type after users select a checkbox where the `icon` property displays an icon in place of the checkbox. The valid options correspond to [the label component's](/skyux/components/label.md) label types. `"info"` creates a blue background, `"success"` creates a green background, `"warning"` creates an orange background, and `"danger"` creates a red background.

Default: `"info"`

#### `checked: boolean`

Whether the checkbox is selected.

#### `disabled: boolean`

Whether the checkbox is disabled.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the checkbox. To group icon checkboxes like in the demo, place the checkboxes within a `sky-checkbox-group`.

#### `id: string | undefined`

The ID for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md) when the checkbox does not include a visible label. You must set this property for icon checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only. Specifying `labelText` also enables automatic error message handling for checkbox.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the checkbox. This sets the checkbox's `aria-labelledby` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md). If the checkbox does not include a visible label, use `label` instead.

#### `name: string`

The name for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete.

Default: `false`

#### `stacked: boolean`

Whether the checkbox is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group, set `stacked` on the checkbox group component instead.

Default: `false`

#### `tabindex: number | undefined`

The index for the checkbox. If not defined, the index is set to the position of the checkbox on load.

Default: `0`

### Outputs

#### `change: EventEmitter<SkyCheckboxChange>`

Fires when the selected value changes.

#### `checkedChange: Observable<boolean>`

Fires when users select or deselect the checkbox.

#### `disabledChange: Observable<boolean>`

Fires when the selected value changes.

 SkyCheckboxGroupComponent
--------------------------

Type: Component

Selector: `sky-checkbox-group`

Organizes checkboxes into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyCheckboxGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyCheckboxGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string`

The text to display as the checkbox group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox group fieldset legend. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the checkbox group is required.

Default: `false`

#### `stacked: boolean`

Whether the checkbox group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox group.

 SkyCheckboxLabelComponent
--------------------------

Type: Component

Selector: `sky-checkbox-label`

Warning: **Deprecated.** Use `labelText` input on `sky-checkbox-component` instead.

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button element.

 SkyCheckboxChange
------------------

Type: Interface

Fires when users select or deselect the checkbox.

    interface SkyCheckboxChange {
      checked?: boolean;
    }

### Properties

#### `checked?: boolean`

The value from the checkbox component.

 SkyCheckboxGroupHeadingLevel
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingLevel = 3 | 4 | 5

 SkyCheckboxGroupHeadingStyle
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingStyle = 3 | 4 | 5

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCheckboxHarness
-------------------

Type: Class

`import { SkyCheckboxHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the checkbox.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the checkbox in a checked state by toggling it if it is currently unchecked, or doing nothing if it is already checked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the checkbox.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the checkbox's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the checkbox's aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the checkbox's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the checkbox's name.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<null | string>`

Gets the checkbox's value.

#### Returns

`Promise<null | string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether the checkbox displays custom error.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the checkbox displays an error that it is required.

#### Returns

`Promise<boolean>`

#### `isChecked(): Promise<boolean>`

Whether the checkbox is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the checkbox is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the checkbox is focused.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether the checkbox is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the checkbox is stacked.

#### Returns

`Promise<boolean>`

#### `uncheck(): Promise<void>`

Puts the checkbox in an unchecked state by toggling it if it is currently checked, or doing nothing if it is already unchecked.

#### Returns

`Promise<void>`

#### `SkyCheckboxHarness.with(filters: SkyCheckboxHarnessFilters): HarnessPredicate<SkyCheckboxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxHarness>`

 SkyCheckboxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

    interface SkyCheckboxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyCheckboxGroupHarness
------------------------

Type: Class

`import { SkyCheckboxGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCheckbox(filter: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness>`

Gets a specific checkbox based on the filter criteria.

#### Parameters

##### `filter: SkyCheckboxHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyCheckboxHarness>`

#### `getCheckboxes(filters?: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness[]>`

Gets an array of checkboxes based on the filter criteria. If no filter is provided, returns all checkboxes.

#### Parameters

##### `filters?: SkyCheckboxHarnessFilters`

#### Returns

`Promise<SkyCheckboxHarness[]>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyCheckboxGroupHeadingLevel>`

The semantic heading level used for the checkbox group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyCheckboxGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyCheckboxGroupHeadingStyle>`

The heading style used for the checkbox group.

#### Returns

`Promise<SkyCheckboxGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the checkbox group's heading text. If `headingHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox group's hint text.

#### Returns

`Promise<string>`

#### `getRequired(): Promise<boolean>`

Whether the checkbox group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the checkbox group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the checkbox group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether all the checkboxes in a required group are unchecked.

#### Returns

`Promise<boolean>`

#### `SkyCheckboxGroupHarness.with(filters: SkyCheckboxGroupHarnessFilters): HarnessPredicate<SkyCheckboxGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxGroupHarness>`

 SkyCheckboxGroupHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

    interface SkyCheckboxGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Checkbox
========

Checkboxes let users select multiple items from a short list of items.Usage
------

### Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-1.2ccbee78ed1195de5654aa725908d635.png)

Do use a checkbox when users must make a single yes/no decision.

Use checkbox groups when users must make multiple, related yes/no decisions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-3.772c7f4cf4b38525a592f3af8b484e3a.png)

Do use a checkbox group for multiple, related checkboxes.

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-2.b5beeddabfe59b96f97ed5ddf12a68f7.png)

Do use icon checkboxes when icons clearly communicate the options.

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-4.3435d079788bf4bbf82e8b02c3418b5a.png)

Do use checkboxes to enable conditional inputs as part of a task.

### Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different [selection input](/skyux/design/guidelines/form-design.md), such as a [lookup field](/skyux/components/lookup.md), instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.5.76e1e8659bc01c83e3988a8735b340f1.png)

Don't use a checkbox group for a homogenous list of more than 5 items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.75.b28d82a07fd6f474db0c993e31936af7.png)

Do use a lookup field to let users select items from a long, homogenous list.

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.6.01dca0c929ecf82b5b8a0f683ac1f9bf.png)

Do use checkbox groups for more than 5 checkboxes when the choices represent distinct decisions.

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use [toggle switch](/skyux/components/toggle-switch.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.1.f043c6cc4a485287b9d9b24beb14b8a5.png)

Don't use checkboxes to alternate between two states when changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.2.f31c8d06ba6d9a953e27fa9eaa29ba0b.png)

Do use toggle switches when changes take effect immediately.

Don't use a checkbox group for a lone checkbox in a form or [field group](/skyux/components/field-group.md).

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-5.b06b9ee82f9d92319efa6e7bba4d35ac.png)

Don't use a checkbox group for a lone checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-6.e7dc9ca88c4c9ddc46fc808d373234f2.png)

Do use an ungrouped checkbox within a form or field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-7.006dcb79da3b7168d9955fa05666c435.png)

Don't use an ungrouped checkbox next to a checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.24ec6cf356c263ec1e8a5cbb1bac97e5.png)

Do use a checkbox group for a lone checkbox next to a checkbox group.

 Anatomy
--------

### Individual checkbox

1

Checkbox

2

Label

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-anatomy.07fe9a203319f8db2cdedaf4bb35177e.png)

### Checkbox group

1

Label

2

Checkboxes

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-group-anatomy.7366139e6d55d56171fc04927f455984.png)

### Icon checkbox

1

Icon checkbox

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-icon-anatomy.e8cf1789a28ac8e1edfa2a35b4744c2e.png)

 Options
--------

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a checkbox group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-heading.639f4268dc24869dcb3ceeba34c03f48.png)

Checkbox group labels can be turned into HTML headings.

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

*   Constraints or requirements on a checkbox group
*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the checkbox group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

Also use `stacked` when an individual checkbox is immediately followed by another form input. However, don't use `stacked` when the checkbox is followed by one or more conditional fields. Use `sky-margin-stacked-sm` instead for closely related fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-1.8589348a67334a785313ffff87a36842.png)

If a checkbox group uses `headingLevel`, use `stacked` when the checkbox group is followed by a [field group](/skyux/components/field-group.md) or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-2.8232d9a4871fd76f1e2f3d1a2d4e029d.png)

 Content
--------

Make checkbox group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, checkbox group labels can use short sentences or sentence fragments.

For details about styling checkbox group labels as headings, see the "Headings" section above.

Similarly, make checkbox labels succinct and descriptive. When necessary, checkbox labels can use short sentences or sentence fragments.

 Layout
-------

Don't wrap a checkbox group inside a [field group](/skyux/component/field-group.md) component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.853c1e673416762512b56d55cb925f36.png)

Don't use a field group with a lone checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-10.389b289ade7642e0e90cb5bd28b2d460.png)

Do adjust the heading level and heading style of a checkbox group to match the hierarcy of field groups.

 Accessibility
--------------

Checkbox groups automatically create `<fieldset>`and `<legend>` elements based on their contents and label text.

In most cases, checkbox group labels aren't treated as HTML headings, but when necessary, you can specify a heading level and heading style. For example, when a lone checkbox group appears on a form with [field groups](/skyux/components/field-group.md), set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style that matches the semantic and visual hierarchy of the field group headings.

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/checkbox/checkbox.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCheckboxModule
------------------

Type: Module

`import { SkyCheckboxModule } from '@skyux/forms';`

 SkyCheckboxComponent
---------------------

Type: Component

Selector: `sky-checkbox`

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

### Inputs

#### `checkboxType: string`

Warning: **Deprecated.** The `checkboxType` input is no longer supported.

The background color type after users select a checkbox where the `icon` property displays an icon in place of the checkbox. The valid options correspond to [the label component's](/skyux/components/label.md) label types. `"info"` creates a blue background, `"success"` creates a green background, `"warning"` creates an orange background, and `"danger"` creates a red background.

Default: `"info"`

#### `checked: boolean`

Whether the checkbox is selected.

#### `disabled: boolean`

Whether the checkbox is disabled.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the checkbox. To group icon checkboxes like in the demo, place the checkboxes within a `sky-checkbox-group`.

#### `id: string | undefined`

The ID for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md) when the checkbox does not include a visible label. You must set this property for icon checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only. Specifying `labelText` also enables automatic error message handling for checkbox.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the checkbox. This sets the checkbox's `aria-labelledby` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md). If the checkbox does not include a visible label, use `label` instead.

#### `name: string`

The name for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete.

Default: `false`

#### `stacked: boolean`

Whether the checkbox is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group, set `stacked` on the checkbox group component instead.

Default: `false`

#### `tabindex: number | undefined`

The index for the checkbox. If not defined, the index is set to the position of the checkbox on load.

Default: `0`

### Outputs

#### `change: EventEmitter<SkyCheckboxChange>`

Fires when the selected value changes.

#### `checkedChange: Observable<boolean>`

Fires when users select or deselect the checkbox.

#### `disabledChange: Observable<boolean>`

Fires when the selected value changes.

 SkyCheckboxGroupComponent
--------------------------

Type: Component

Selector: `sky-checkbox-group`

Organizes checkboxes into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyCheckboxGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyCheckboxGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string`

The text to display as the checkbox group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox group fieldset legend. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the checkbox group is required.

Default: `false`

#### `stacked: boolean`

Whether the checkbox group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox group.

 SkyCheckboxLabelComponent
--------------------------

Type: Component

Selector: `sky-checkbox-label`

Warning: **Deprecated.** Use `labelText` input on `sky-checkbox-component` instead.

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button element.

 SkyCheckboxChange
------------------

Type: Interface

Fires when users select or deselect the checkbox.

    interface SkyCheckboxChange {
      checked?: boolean;
    }

### Properties

#### `checked?: boolean`

The value from the checkbox component.

 SkyCheckboxGroupHeadingLevel
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingLevel = 3 | 4 | 5

 SkyCheckboxGroupHeadingStyle
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingStyle = 3 | 4 | 5

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCheckboxHarness
-------------------

Type: Class

`import { SkyCheckboxHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the checkbox.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the checkbox in a checked state by toggling it if it is currently unchecked, or doing nothing if it is already checked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the checkbox.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the checkbox's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the checkbox's aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the checkbox's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the checkbox's name.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<null | string>`

Gets the checkbox's value.

#### Returns

`Promise<null | string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether the checkbox displays custom error.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the checkbox displays an error that it is required.

#### Returns

`Promise<boolean>`

#### `isChecked(): Promise<boolean>`

Whether the checkbox is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the checkbox is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the checkbox is focused.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether the checkbox is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the checkbox is stacked.

#### Returns

`Promise<boolean>`

#### `uncheck(): Promise<void>`

Puts the checkbox in an unchecked state by toggling it if it is currently checked, or doing nothing if it is already unchecked.

#### Returns

`Promise<void>`

#### `SkyCheckboxHarness.with(filters: SkyCheckboxHarnessFilters): HarnessPredicate<SkyCheckboxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxHarness>`

 SkyCheckboxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

    interface SkyCheckboxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyCheckboxGroupHarness
------------------------

Type: Class

`import { SkyCheckboxGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCheckbox(filter: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness>`

Gets a specific checkbox based on the filter criteria.

#### Parameters

##### `filter: SkyCheckboxHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyCheckboxHarness>`

#### `getCheckboxes(filters?: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness[]>`

Gets an array of checkboxes based on the filter criteria. If no filter is provided, returns all checkboxes.

#### Parameters

##### `filters?: SkyCheckboxHarnessFilters`

#### Returns

`Promise<SkyCheckboxHarness[]>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyCheckboxGroupHeadingLevel>`

The semantic heading level used for the checkbox group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyCheckboxGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyCheckboxGroupHeadingStyle>`

The heading style used for the checkbox group.

#### Returns

`Promise<SkyCheckboxGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the checkbox group's heading text. If `headingHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox group's hint text.

#### Returns

`Promise<string>`

#### `getRequired(): Promise<boolean>`

Whether the checkbox group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the checkbox group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the checkbox group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether all the checkboxes in a required group are unchecked.

#### Returns

`Promise<boolean>`

#### `SkyCheckboxGroupHarness.with(filters: SkyCheckboxGroupHarnessFilters): HarnessPredicate<SkyCheckboxGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxGroupHarness>`

 SkyCheckboxGroupHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

    interface SkyCheckboxGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Standard checkboxes

Edit in StackBlitz

Contact methodRequiredShow help content for

Please select at least one phone-based method.

EmailPhoneText

I agree to the terms and conditionsSubmit

Show code

Copy

    <form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
      <sky-checkbox-group
        data-sky-id="checkbox-group"
        headingText="Contact method"
        headingStyle="5"
        helpPopoverContent="We use your contact info to keep you informed on current events. We will not sell your information."
        hintText="Please select at least one phone-based method."
        [formGroup]="contactMethod"
        [required]="true"
        [stacked]="true"
      >
        <sky-checkbox formControlName="email" labelText="Email" />
        <sky-checkbox formControlName="phone" labelText="Phone" />
        <sky-checkbox formControlName="text" labelText="Text" />
        @if (contactMethod.errors?.['emailOnly']) {
          <sky-form-error
            errorName="emailOnly"
            errorText="Email cannot be the only contact method."
          />
        }
      </sky-checkbox-group>
      <sky-checkbox
        data-sky-id="single-checkbox"
        formControlName="terms"
        labelText="I agree to the terms and conditions"
        [required]="true"
        [stacked]="true"
      />
      <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyCheckboxGroupHarness,
      SkyCheckboxHarness,
    } from '@skyux/forms/testing';
    
    import { FormsCheckboxBasicExampleComponent } from './example.component';
    
    describe('Basic checkbox group example', () => {
      async function setupCheckboxGroupTest(options: {
        dataSkyId: string;
      }): Promise<SkyCheckboxGroupHarness> {
        const fixture = TestBed.createComponent(FormsCheckboxBasicExampleComponent);
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyCheckboxGroupHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return harness;
      }
    
      async function setupCheckboxTest(options: {
        dataSkyId: string;
      }): Promise<SkyCheckboxHarness> {
        const fixture = TestBed.createComponent(FormsCheckboxBasicExampleComponent);
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyCheckboxHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return harness;
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [NoopAnimationsModule, FormsCheckboxBasicExampleComponent],
        });
      });
    
      it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
        const harness = await setupCheckboxGroupTest({
          dataSkyId: 'checkbox-group',
        });
    
        const checkboxButtons = await harness.getCheckboxes();
    
        await expectAsync(harness.getHeadingText()).toBeResolvedTo(
          'Contact method',
        );
        await expectAsync(harness.getHeadingLevel()).toBeResolvedTo(undefined);
        await expectAsync(harness.getHeadingStyle()).toBeResolvedTo(5);
        await expectAsync(harness.getHintText()).toBeResolvedTo(
          'Please select at least one phone-based method.',
        );
    
        await expectAsync(checkboxButtons[0].getLabelText()).toBeResolvedTo(
          'Email',
        );
        await expectAsync(checkboxButtons[0].getHintText()).toBeResolvedTo('');
    
        await expectAsync(checkboxButtons[1].getLabelText()).toBeResolvedTo(
          'Phone',
        );
        await expectAsync(checkboxButtons[1].getHintText()).toBeResolvedTo('');
    
        await expectAsync(checkboxButtons[2].getLabelText()).toBeResolvedTo('Text');
        await expectAsync(checkboxButtons[2].getHintText()).toBeResolvedTo('');
      });
    
      it('should display an error message when there is a custom validation error', async () => {
        const harness = await setupCheckboxGroupTest({
          dataSkyId: 'checkbox-group',
        });
    
        const checkboxHarness = (await harness.getCheckboxes())[0];
    
        await checkboxHarness.check();
    
        await expectAsync(harness.hasError('emailOnly')).toBeResolvedTo(true);
      });
    
      it('should show a help popover with the expected text', async () => {
        const harness = await setupCheckboxGroupTest({
          dataSkyId: 'checkbox-group',
        });
    
        await harness.clickHelpInline();
    
        const helpPopoverContent = await harness.getHelpPopoverContent();
        expect(helpPopoverContent).toBe(
          `We use your contact info to keep you informed on current events. We will not sell your information.`,
        );
      });
    
      it('should check and uncheck checkboxes in display errors if they are required', async () => {
        const harness = await setupCheckboxTest({ dataSkyId: 'single-checkbox' });
    
        await expectAsync(harness.isStacked()).toBeResolvedTo(true);
    
        await expectAsync(harness.isChecked()).toBeResolvedTo(false);
        await harness.check();
        await expectAsync(harness.isChecked()).toBeResolvedTo(true);
        await harness.uncheck();
        await harness.blur();
        await expectAsync(harness.hasRequiredError()).toBeResolvedTo(true);
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
    } from '@angular/forms';
    import { SkyCheckboxModule } from '@skyux/forms';
    
    /**
     * @title Standard checkboxes
     */
    @Component({
      selector: 'app-forms-checkbox-basic-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
    })
    export class FormsCheckboxBasicExampleComponent {
      #formBuilder: FormBuilder = inject(FormBuilder);
    
      protected formGroup: FormGroup;
      protected contactMethod: FormGroup;
    
      constructor() {
        this.contactMethod = this.#formBuilder.group({
          email: new FormControl(false),
          phone: new FormControl(false),
          text: new FormControl(false),
        });
    
        this.formGroup = this.#formBuilder.group({
          contactMethod: this.contactMethod,
          terms: new FormControl(false),
        });
    
        this.contactMethod.setValidators(
          (control: AbstractControl): ValidationErrors | null => {
            const group = control as FormGroup;
            const email = group.controls['email'];
            const phone = group.controls['phone'];
            const text = group.controls['text'];
    
            if (email.value && !phone.value && !text.value) {
              return { emailOnly: true };
            } else {
              return null;
            }
          },
        );
      }
    
      protected onSubmit(): void {
        this.formGroup.markAllAsTouched();
    
        console.log(this.formGroup.value);
      }
    }
### Checkboxes with help key

Edit in StackBlitz

Contact methodRequiredShow help content for

Please select at least one phone-based method.

EmailPhoneText

I agree to the terms and conditionsShow help content for Submit

Show code

Copy

    <form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
      <sky-checkbox-group
        data-sky-id="checkbox-group"
        headingText="Contact method"
        headingStyle="5"
        helpKey="contact-help"
        hintText="Please select at least one phone-based method."
        [formGroup]="contactMethod"
        [required]="true"
        [stacked]="true"
      >
        <sky-checkbox formControlName="email" labelText="Email" />
        <sky-checkbox formControlName="phone" labelText="Phone" />
        <sky-checkbox formControlName="text" labelText="Text" />
        @if (contactMethod.errors?.['emailOnly']) {
          <sky-form-error
            errorName="emailOnly"
            errorText="Email cannot be the only contact method."
          />
        }
      </sky-checkbox-group>
      <sky-checkbox
        data-sky-id="single-checkbox"
        formControlName="terms"
        helpKey="terms-help"
        labelText="I agree to the terms and conditions"
        [required]="true"
        [stacked]="true"
      />
      <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import {
      SkyCheckboxGroupHarness,
      SkyCheckboxHarness,
    } from '@skyux/forms/testing';
    
    import { FormsCheckboxHelpKeyExampleComponent } from './example.component';
    
    describe('Basic checkbox group example', () => {
      async function setupCheckboxGroupTest(options: {
        dataSkyId: string;
      }): Promise<{
        checkboxGroupHarness: SkyCheckboxGroupHarness;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          FormsCheckboxHelpKeyExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const checkboxGroupHarness = await loader.getHarness(
          SkyCheckboxGroupHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { checkboxGroupHarness, helpController };
      }
    
      async function setupCheckboxTest(options: { dataSkyId: string }): Promise<{
        checkboxHarness: SkyCheckboxHarness;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          FormsCheckboxHelpKeyExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const checkboxHarness = await loader.getHarness(
          SkyCheckboxHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { checkboxHarness, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            NoopAnimationsModule,
            FormsCheckboxHelpKeyExampleComponent,
            SkyHelpTestingModule,
          ],
        });
      });
    
      it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
        const { checkboxGroupHarness } = await setupCheckboxGroupTest({
          dataSkyId: 'checkbox-group',
        });
    
        const checkboxButtons = await checkboxGroupHarness.getCheckboxes();
    
        await expectAsync(checkboxGroupHarness.getHeadingText()).toBeResolvedTo(
          'Contact method',
        );
        await expectAsync(checkboxGroupHarness.getHeadingLevel()).toBeResolvedTo(
          undefined,
        );
        await expectAsync(checkboxGroupHarness.getHeadingStyle()).toBeResolvedTo(5);
        await expectAsync(checkboxGroupHarness.getHintText()).toBeResolvedTo(
          'Please select at least one phone-based method.',
        );
    
        await expectAsync(checkboxButtons[0].getLabelText()).toBeResolvedTo(
          'Email',
        );
        await expectAsync(checkboxButtons[0].getHintText()).toBeResolvedTo('');
    
        await expectAsync(checkboxButtons[1].getLabelText()).toBeResolvedTo(
          'Phone',
        );
        await expectAsync(checkboxButtons[1].getHintText()).toBeResolvedTo('');
    
        await expectAsync(checkboxButtons[2].getLabelText()).toBeResolvedTo('Text');
        await expectAsync(checkboxButtons[2].getHintText()).toBeResolvedTo('');
      });
    
      it('should display an error message when there is a custom validation error', async () => {
        const { checkboxGroupHarness } = await setupCheckboxGroupTest({
          dataSkyId: 'checkbox-group',
        });
    
        const checkboxHarness = (await checkboxGroupHarness.getCheckboxes())[0];
    
        await checkboxHarness.check();
    
        await expectAsync(
          checkboxGroupHarness.hasError('emailOnly'),
        ).toBeResolvedTo(true);
      });
    
      it('should have the correct help key for checkbox groups', async () => {
        const { checkboxGroupHarness, helpController } =
          await setupCheckboxGroupTest({
            dataSkyId: 'checkbox-group',
          });
    
        await checkboxGroupHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('contact-help');
      });
    
      it('should check and uncheck checkboxes in display errors if they are required', async () => {
        const { checkboxHarness } = await setupCheckboxTest({
          dataSkyId: 'single-checkbox',
        });
    
        await expectAsync(checkboxHarness.isStacked()).toBeResolvedTo(true);
    
        await expectAsync(checkboxHarness.isChecked()).toBeResolvedTo(false);
        await checkboxHarness.check();
        await expectAsync(checkboxHarness.isChecked()).toBeResolvedTo(true);
        await checkboxHarness.uncheck();
        await checkboxHarness.blur();
        await expectAsync(checkboxHarness.hasRequiredError()).toBeResolvedTo(true);
      });
    
      it('should have the correct help key for checkboxes', async () => {
        const { checkboxHarness, helpController } = await setupCheckboxTest({
          dataSkyId: 'single-checkbox',
        });
    
        await checkboxHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('terms-help');
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
    } from '@angular/forms';
    import { SkyCheckboxModule } from '@skyux/forms';
    
    /**
     * @title Checkboxes with help key
     */
    @Component({
      selector: 'app-forms-checkbox-help-key-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
    })
    export class FormsCheckboxHelpKeyExampleComponent {
      #formBuilder: FormBuilder = inject(FormBuilder);
    
      protected formGroup: FormGroup;
      protected contactMethod: FormGroup;
    
      constructor() {
        this.contactMethod = this.#formBuilder.group({
          email: new FormControl(false),
          phone: new FormControl(false),
          text: new FormControl(false),
        });
    
        this.formGroup = this.#formBuilder.group({
          contactMethod: this.contactMethod,
          terms: new FormControl(false),
        });
    
        this.contactMethod.setValidators(
          (control: AbstractControl): ValidationErrors | null => {
            const group = control as FormGroup;
            const email = group.controls['email'];
            const phone = group.controls['phone'];
            const text = group.controls['text'];
    
            if (email.value && !phone.value && !text.value) {
              return { emailOnly: true };
            } else {
              return null;
            }
          },
        );
      }
    
      protected onSubmit(): void {
        this.formGroup.markAllAsTouched();
    
        console.log(this.formGroup.value);
      }
    }
### Icon checkbox group

Edit in StackBlitz

Text formatting

Submit

Show code

Copy

    <form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
      <sky-checkbox-group
        headingText="Text formatting"
        [formGroup]="formGroup"
        [headingHidden]="true"
        [stacked]="true"
      >
        <sky-checkbox
          formControlName="bold"
          iconName="text-bold"
          labelHidden="true"
          labelText="Bold"
        />
        <sky-checkbox
          formControlName="italic"
          iconName="text-italic"
          labelHidden="true"
          labelText="Italic"
        />
        <sky-checkbox
          formControlName="underline"
          iconName="text-underline"
          labelHidden="true"
          labelText="Underline"
        />
      </sky-checkbox-group>
      <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
    </form>

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyCheckboxModule } from '@skyux/forms';
    
    /**
     * @title Icon checkbox group
     */
    @Component({
      selector: 'app-forms-checkbox-icon-group-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
    })
    export class FormsCheckboxIconGroupExampleComponent {
      protected formGroup: FormGroup;
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          bold: new FormControl(false),
          italic: new FormControl(false),
          underline: new FormControl(false),
        });
      }
    
      public onSubmit(): void {
        console.log(this.formGroup.value);
      }
    }

# Testing

                  Skip to Main Content

 Checkbox
========

Checkboxes let users select multiple items from a short list of items.

 Usage
------

### Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-1.2ccbee78ed1195de5654aa725908d635.png)

Do use a checkbox when users must make a single yes/no decision.

Use checkbox groups when users must make multiple, related yes/no decisions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-3.772c7f4cf4b38525a592f3af8b484e3a.png)

Do use a checkbox group for multiple, related checkboxes.

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-2.b5beeddabfe59b96f97ed5ddf12a68f7.png)

Do use icon checkboxes when icons clearly communicate the options.

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-4.3435d079788bf4bbf82e8b02c3418b5a.png)

Do use checkboxes to enable conditional inputs as part of a task.

### Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different [selection input](/skyux/design/guidelines/form-design.md), such as a [lookup field](/skyux/components/lookup.md), instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.5.76e1e8659bc01c83e3988a8735b340f1.png)

Don't use a checkbox group for a homogenous list of more than 5 items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.75.b28d82a07fd6f474db0c993e31936af7.png)

Do use a lookup field to let users select items from a long, homogenous list.

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.6.01dca0c929ecf82b5b8a0f683ac1f9bf.png)

Do use checkbox groups for more than 5 checkboxes when the choices represent distinct decisions.

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use [toggle switch](/skyux/components/toggle-switch.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.1.f043c6cc4a485287b9d9b24beb14b8a5.png)

Don't use checkboxes to alternate between two states when changes take effect immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.2.f31c8d06ba6d9a953e27fa9eaa29ba0b.png)

Do use toggle switches when changes take effect immediately.

Don't use a checkbox group for a lone checkbox in a form or [field group](/skyux/components/field-group.md).

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-5.b06b9ee82f9d92319efa6e7bba4d35ac.png)

Don't use a checkbox group for a lone checkbox.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-6.e7dc9ca88c4c9ddc46fc808d373234f2.png)

Do use an ungrouped checkbox within a form or field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-7.006dcb79da3b7168d9955fa05666c435.png)

Don't use an ungrouped checkbox next to a checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-8.24ec6cf356c263ec1e8a5cbb1bac97e5.png)

Do use a checkbox group for a lone checkbox next to a checkbox group.

 Anatomy
--------

### Individual checkbox

1

Checkbox

2

Label

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-anatomy.07fe9a203319f8db2cdedaf4bb35177e.png)

### Checkbox group

1

Label

2

Checkboxes

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-group-anatomy.7366139e6d55d56171fc04927f455984.png)

### Icon checkbox

1

Icon checkbox

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-icon-anatomy.e8cf1789a28ac8e1edfa2a35b4744c2e.png)

 Options
--------

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a checkbox group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-heading.639f4268dc24869dcb3ceeba34c03f48.png)

Checkbox group labels can be turned into HTML headings.

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

*   Constraints or requirements on a checkbox group
*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the checkbox group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

Also use `stacked` when an individual checkbox is immediately followed by another form input. However, don't use `stacked` when the checkbox is followed by one or more conditional fields. Use `sky-margin-stacked-sm` instead for closely related fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-1.8589348a67334a785313ffff87a36842.png)

If a checkbox group uses `headingLevel`, use `stacked` when the checkbox group is followed by a [field group](/skyux/components/field-group.md) or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-options-stacked-2.8232d9a4871fd76f1e2f3d1a2d4e029d.png)

 Content
--------

Make checkbox group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, checkbox group labels can use short sentences or sentence fragments.

For details about styling checkbox group labels as headings, see the "Headings" section above.

Similarly, make checkbox labels succinct and descriptive. When necessary, checkbox labels can use short sentences or sentence fragments.

 Layout
-------

Don't wrap a checkbox group inside a [field group](/skyux/component/field-group.md) component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-9.853c1e673416762512b56d55cb925f36.png)

Don't use a field group with a lone checkbox group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/checkbox/checkbox-usage-10.389b289ade7642e0e90cb5bd28b2d460.png)

Do adjust the heading level and heading style of a checkbox group to match the hierarcy of field groups.

 Accessibility
--------------

Checkbox groups automatically create `<fieldset>`and `<legend>` elements based on their contents and label text.

In most cases, checkbox group labels aren't treated as HTML headings, but when necessary, you can specify a heading level and heading style. For example, when a lone checkbox group appears on a form with [field groups](/skyux/components/field-group.md), set the checkbox group's `headingLevel` and `headingStyle` to `3` to use the label as an `h3` heading with a `sky-font-heading-3` visual style that matches the semantic and visual hierarchy of the field group headings.

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/checkbox/checkbox.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCheckboxModule
------------------

Type: Module

`import { SkyCheckboxModule } from '@skyux/forms';`

 SkyCheckboxComponent
---------------------

Type: Component

Selector: `sky-checkbox`

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

### Inputs

#### `checkboxType: string`

Warning: **Deprecated.** The `checkboxType` input is no longer supported.

The background color type after users select a checkbox where the `icon` property displays an icon in place of the checkbox. The valid options correspond to [the label component's](/skyux/components/label.md) label types. `"info"` creates a blue background, `"success"` creates a green background, `"warning"` creates an orange background, and `"danger"` creates a red background.

Default: `"info"`

#### `checked: boolean`

Whether the checkbox is selected.

#### `disabled: boolean`

Whether the checkbox is disabled.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the checkbox. To group icon checkboxes like in the demo, place the checkboxes within a `sky-checkbox-group`.

#### `id: string | undefined`

The ID for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md) when the checkbox does not include a visible label. You must set this property for icon checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only. Specifying `labelText` also enables automatic error message handling for checkbox.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the checkbox. This sets the checkbox's `aria-labelledby` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md). If the checkbox does not include a visible label, use `label` instead.

#### `name: string`

The name for the checkbox. If a value is not provided, an autogenerated ID is used.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete.

Default: `false`

#### `stacked: boolean`

Whether the checkbox is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group, set `stacked` on the checkbox group component instead.

Default: `false`

#### `tabindex: number | undefined`

The index for the checkbox. If not defined, the index is set to the position of the checkbox on load.

Default: `0`

### Outputs

#### `change: EventEmitter<SkyCheckboxChange>`

Fires when the selected value changes.

#### `checkedChange: Observable<boolean>`

Fires when users select or deselect the checkbox.

#### `disabledChange: Observable<boolean>`

Fires when the selected value changes.

 SkyCheckboxGroupComponent
--------------------------

Type: Component

Selector: `sky-checkbox-group`

Organizes checkboxes into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyCheckboxGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyCheckboxGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string`

The text to display as the checkbox group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the checkbox group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the checkbox group fieldset legend. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the checkbox group is required.

Default: `false`

#### `stacked: boolean`

Whether the checkbox group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the checkbox group.

 SkyCheckboxLabelComponent
--------------------------

Type: Component

Selector: `sky-checkbox-label`

Warning: **Deprecated.** Use `labelText` input on `sky-checkbox-component` instead.

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button element.

 SkyCheckboxChange
------------------

Type: Interface

Fires when users select or deselect the checkbox.

    interface SkyCheckboxChange {
      checked?: boolean;
    }

### Properties

#### `checked?: boolean`

The value from the checkbox component.

 SkyCheckboxGroupHeadingLevel
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingLevel = 3 | 4 | 5

 SkyCheckboxGroupHeadingStyle
-----------------------------

Type: Type alias

    type SkyCheckboxGroupHeadingStyle = 3 | 4 | 5

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCheckboxHarness
-------------------

Type: Class

`import { SkyCheckboxHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the checkbox.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the checkbox in a checked state by toggling it if it is currently unchecked, or doing nothing if it is already checked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the checkbox.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the checkbox's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the checkbox's aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the checkbox's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the checkbox's name.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<null | string>`

Gets the checkbox's value.

#### Returns

`Promise<null | string>`

#### `hasCustomError(errorName: string): Promise<boolean>`

Whether the checkbox displays custom error.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the checkbox displays an error that it is required.

#### Returns

`Promise<boolean>`

#### `isChecked(): Promise<boolean>`

Whether the checkbox is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the checkbox is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the checkbox is focused.

#### Returns

`Promise<boolean>`

#### `isRequired(): Promise<boolean>`

Whether the checkbox is required.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the checkbox is stacked.

#### Returns

`Promise<boolean>`

#### `uncheck(): Promise<void>`

Puts the checkbox in an unchecked state by toggling it if it is currently checked, or doing nothing if it is already unchecked.

#### Returns

`Promise<void>`

#### `SkyCheckboxHarness.with(filters: SkyCheckboxHarnessFilters): HarnessPredicate<SkyCheckboxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxHarness>`

 SkyCheckboxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

    interface SkyCheckboxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyCheckboxGroupHarness
------------------------

Type: Class

`import { SkyCheckboxGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a checkbox group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCheckbox(filter: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness>`

Gets a specific checkbox based on the filter criteria.

#### Parameters

##### `filter: SkyCheckboxHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyCheckboxHarness>`

#### `getCheckboxes(filters?: SkyCheckboxHarnessFilters): Promise<SkyCheckboxHarness[]>`

Gets an array of checkboxes based on the filter criteria. If no filter is provided, returns all checkboxes.

#### Parameters

##### `filters?: SkyCheckboxHarnessFilters`

#### Returns

`Promise<SkyCheckboxHarness[]>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyCheckboxGroupHeadingLevel>`

The semantic heading level used for the checkbox group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyCheckboxGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyCheckboxGroupHeadingStyle>`

The heading style used for the checkbox group.

#### Returns

`Promise<SkyCheckboxGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the checkbox group's heading text. If `headingHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the checkbox group's hint text.

#### Returns

`Promise<string>`

#### `getRequired(): Promise<boolean>`

Whether the checkbox group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the checkbox group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the checkbox group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether all the checkboxes in a required group are unchecked.

#### Returns

`Promise<boolean>`

#### `SkyCheckboxGroupHarness.with(filters: SkyCheckboxGroupHarnessFilters): HarnessPredicate<SkyCheckboxGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCheckboxGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCheckboxGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyCheckboxGroupHarness>`

 SkyCheckboxGroupHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

    interface SkyCheckboxGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
# Design

                  Skip to Main Content

 Radio button
============

Radio buttons let users select one item from a short list of items.

 Usage
------

### Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-1.0faf1ea491585986a7755c2ae094d652.png)

Do use radio button groups when users select a single item from a short list of options in a modal.

Use icon radio button groups when icons clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-4.253385ed82a0e6333979ce9bcf086f30.png)

Do use icon radio button groups when icons clearly illustrate the options.

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using [action buttons](/skyux/components/action-button.md) instead. See the [form layout](/skyux/design/guidelines/form-design#form-layout.md) guidelines for more information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-5.6377ae12e3f2b2e54402a3cf867bd5f1.png)

Do use radio buttons to enable conditional inputs as part of a task.

### Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-6.b5d15ab9095bf93f6a38244162ff6a7b.png)

Don't use radio buttons for a long list of options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-7.6918953b44ee81a622c16c675a76c1f8.png)

Do use different selection controls for more than five choices.

Don't use radio buttons for two options that are exact opposites. Use a [checkbox](/skyux/components/checkbox.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-8.bb1dced3921747be3200eb3fc0964cb4.png)

Don't use radio buttons to represent exact opposites.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-9.01937762fa8b73247dabd00f0b1631be.png)

Do use a checkbox to represent exact opposites.

Don't use radio buttons when user selections significantly alter the workflow. Use [action buttons](/skyux/components/action-button.md) instead, and place them at the beginning of the task.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-10.b03b6b3095bcaab8a3d5229d84942088.png)

Don't use radio buttons for options that significantly alter the workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-11.16da7d131835d6e108ef4399b49773e4.png)

Do use action buttons for decisions that branch users into significantly different workflows.

 Anatomy
--------

### Individual radio button

1

Radio button

2

Label

3

Help inline button (optional)

4

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-anatomy.21f90955fe130bf661114e96db2f3beb.png)

### Radio button group

1

Label

2

Radio buttons

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-group-anatomy.7c8861e2e913d0b8b543c025fcd3f082.png)

### Icon radio button group

1

Icon radio button

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-icon-radio-button-group-anatomy.d02cffe93d8037fcb903aad8ea8d9785.png)

 Options
--------

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a radio button group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-heading-option.e8a1d1a3b06eb0c9ae2f35202bf68d1c.png)

Radio button group labels can be turned into HTML headings.

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the radio button group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-1.26cce06c1b3a5b98e02f4ffccb3be907.png)

If a radio button group uses `headingLevel`, use `stacked` when the radio button group is followed by a [field group](/skyux/components/field-group.md) or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-2.f42e7d466f28c5f366bc2051b5c7ec12.png)

 Content
--------

Make radio button group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, radio button group labels can use short sentences or sentence fragments.

For details about styling radio button group labels as headings, see the "Headings" section above.

Similarly, make radio button labels succinct and descriptive. But when necessary, radio button labels can use short sentences or sentence fragments.

Icon radio buttons use the [icon](/skyux/components/icon.md) component. For a list of common icons, see the [SKY UX icon inventory](/skyux/components/icon#section-inventory.md). Don't display heading text or label text on icon radio button groups.

 Layout
-------

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with `headingLevel` and `headingStyle` set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-1.23106409ac2d82070d48813123d08928.png)

Don't use a field group with a lone radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-2.dc2ff66f192a36b10dc8bc64e4a8d23b.png)

Do adjust the heading level and heading style of a radio button group to match the hierarchy of field groups.

 Accessibility
--------------

Radio button groups will automatically create `<fieldset>`and `<legend>` elements from their contents and heading text.

In most cases, radio button group labels are not treated as semantic `h` elements, but when necessary, you can specify a heading level and heading style. For example, when a lone radio button group appears on a form field with [field groups](/skyux/components/field-group.md), set the radio button group's `headingLevel` to `3` and `headingStyle` to `sky-font-heading-3` to match the semantic and visual hierarchy of field group headings.

 Related information
--------------------

### Components

*   [Action buttons](/skyux/components/action-button.md)
*   [Checkbox](/skyux/components/checkbox.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Modal](/skyux/components/modal.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/radio/radio.module.ts#L42) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyRadioModule
---------------

Type: Module

`import { SkyRadioModule } from '@skyux/forms';`

 SkyRadioGroupComponent
-----------------------

Type: Component

Selector: `sky-radio-group`

Organizes radio buttons into a group. It is required for radio buttons on Angular reactive forms, and we recommend using it with all radio buttons. On Angular forms, the component manages the selected values and keeps the forms up-to-date. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

### Inputs

#### `name: string`

Required

The name for the collection of radio buttons that the component groups together. This property overwrites the deprecated `name` property on individual `sky-radio` elements, and it is required unless the `name` property is set on individual `sky-radio` elements.

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The ARIA label for the radio button group. This sets the radio button group's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The HTML element ID of the element that labels the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyRadioGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyRadioGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string | undefined`

The text to display as the radio group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to radio group. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the radio button group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the radio button group.

#### `tabIndex: number | undefined`

The index for all the radio buttons in the group. If the index is not defined, the indices for individual radio buttons are set to their positions on load. This property supports accessibility by placing focus on the currently selected radio button. If no radio button is selected, it places focus on the first or last button depending on how users navigate to the radio button group.

#### `value: any`

The value of the radio button to select by default when the group loads. The value corresponds to the `value` property of an individual `sky-radio` element within the group.

 SkyRadioComponent
------------------

Type: Component

Selector: `sky-radio`

Renders a SKY UX-themed replacement for an HTML `input` element with `type="radio"`. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

### Inputs

#### `value: any`

Required

The value bound to the radio button's `value` property. The value usually corresponds to the radio button's label, which you specify with the `sky-radio-label` component.

#### `checked: boolean`

Whether the radio button is selected.

Default: `false`

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio button label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to radio button. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the radio button. To group radio buttons like in the demo above, place the `sky-switch-icon-group` class on the direct parent element of the radio buttons.

#### `id: string | undefined`

The ID for the radio button. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the radio button. This sets the radio button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md) when the radio button does not include a visible label. You must set this property for icon radio buttons. If the radio button includes a visible label, use `labelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button does not include a visible label, use `label` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `name: string | undefined`

This property is deprecated in favor of the `name` property on the `sky-radio-group element`. We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to, then this property specifies a name for a group of radio buttons.

#### `radioType: SkyRadioType`

Warning: **Deprecated.** radioType is no longer supported

The background color type after users select an icon radio button. The valid options correspond [the label component's](/skyux/components/label.md) label types. `danger` creates a red background, `info` creates a blue background, `success` creates a green background, and `warning` creates an orange background.

Default: `"info"`

#### `tabindex: number`

This property is deprecated in favor of the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio button. If the index is not defined, it is set to the position of the radio button on load.

### Outputs

#### `change: EventEmitter<SkyRadioChange>`

Fires when users select a radio button.

#### `checkedChange: EventEmitter<boolean>`

Fires when the selected value changes.

#### `disabledChange: EventEmitter<boolean>`

Fires when the selected value changes.

 SkyRadioLabelComponent
-----------------------

Type: Component

Selector: `sky-radio-label`

Warning: **Deprecated.** Use `labelText` input on `sky-radio-component` instead.

Specifies a label for the radio button. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button element.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyRadioGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingLevel = 3 | 4 | 5

 SkyRadioGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingStyle = 3 | 4 | 5

 SkyRadioType
-------------

Type: Type alias

Warning: **Deprecated.** radioType is no longer supported

    type SkyRadioType = "danger" | "info" | "success" | "warning"

 SkyRadioChange
---------------

Type: Interface

Fires when users select a radio button.

    interface SkyRadioChange {
      value: any;
    }

### Properties

#### `value: any`

The value from the radio component.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyRadioGroupHarness
---------------------

Type: Class

`import { SkyRadioGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyRadioGroupHeadingLevel>`

The semantic heading level used for the radio group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyRadioGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyRadioGroupHeadingStyle>`

The heading style used for the radio group.

#### Returns

`Promise<SkyRadioGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the radio group's heading text. If `headingHidden` is true, the text will still be returned.

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

Gets the radio group's hint text.

#### Returns

`Promise<string>`

#### `getRadioButton(filter: SkyRadioHarnessFilters): Promise<SkyRadioHarness>`

Gets a specific radio button based on the filter criteria.

#### Parameters

##### `filter: SkyRadioHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyRadioHarness>`

#### `getRadioButtons(filters?: SkyRadioHarnessFilters): Promise<SkyRadioHarness[]>`

Gets an array of radio buttons based on the filter criteria. If no filter is provided, returns all radio buttons.

#### Parameters

##### `filters?: SkyRadioHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyRadioHarness[]>`

#### `getRequired(): Promise<boolean>`

Whether the radio group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the radio group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the radio group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `SkyRadioGroupHarness.with(filters: SkyRadioGroupHarnessFilters): HarnessPredicate<SkyRadioGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioGroupHarness>`

 SkyRadioGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

    interface SkyRadioGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRadioHarness
----------------

Type: Class

`import { SkyRadioHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio button component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the radio button.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the radio button in a checked state if it is currently unchecked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the radio button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the radio button's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the radio button's aria-labelledby.

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

Gets the radio button's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the radio button's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the radio button's name.

#### Returns

`Promise<null | string>`

#### `isChecked(): Promise<boolean>`

Whether the radio button is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the radio button is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the radio button is focused.

#### Returns

`Promise<boolean>`

#### `SkyRadioHarness.with(filters: SkyRadioHarnessFilters): HarnessPredicate<SkyRadioHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioHarness>`

 SkyRadioHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

    interface SkyRadioHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Radio button
============

Radio buttons let users select one item from a short list of items.

 Usage
------

### Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-1.0faf1ea491585986a7755c2ae094d652.png)

Do use radio button groups when users select a single item from a short list of options in a modal.

Use icon radio button groups when icons clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-4.253385ed82a0e6333979ce9bcf086f30.png)

Do use icon radio button groups when icons clearly illustrate the options.

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using [action buttons](/skyux/components/action-button.md) instead. See the [form layout](/skyux/design/guidelines/form-design#form-layout.md) guidelines for more information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-5.6377ae12e3f2b2e54402a3cf867bd5f1.png)

Do use radio buttons to enable conditional inputs as part of a task.

### Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-6.b5d15ab9095bf93f6a38244162ff6a7b.png)

Don't use radio buttons for a long list of options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-7.6918953b44ee81a622c16c675a76c1f8.png)

Do use different selection controls for more than five choices.

Don't use radio buttons for two options that are exact opposites. Use a [checkbox](/skyux/components/checkbox.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-8.bb1dced3921747be3200eb3fc0964cb4.png)

Don't use radio buttons to represent exact opposites.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-9.01937762fa8b73247dabd00f0b1631be.png)

Do use a checkbox to represent exact opposites.

Don't use radio buttons when user selections significantly alter the workflow. Use [action buttons](/skyux/components/action-button.md) instead, and place them at the beginning of the task.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-10.b03b6b3095bcaab8a3d5229d84942088.png)

Don't use radio buttons for options that significantly alter the workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-11.16da7d131835d6e108ef4399b49773e4.png)

Do use action buttons for decisions that branch users into significantly different workflows.

 Anatomy
--------

### Individual radio button

1

Radio button

2

Label

3

Help inline button (optional)

4

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-anatomy.21f90955fe130bf661114e96db2f3beb.png)

### Radio button group

1

Label

2

Radio buttons

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-group-anatomy.7c8861e2e913d0b8b543c025fcd3f082.png)

### Icon radio button group

1

Icon radio button

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-icon-radio-button-group-anatomy.d02cffe93d8037fcb903aad8ea8d9785.png)

 Options
--------

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a radio button group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-heading-option.e8a1d1a3b06eb0c9ae2f35202bf68d1c.png)

Radio button group labels can be turned into HTML headings.

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the radio button group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-1.26cce06c1b3a5b98e02f4ffccb3be907.png)

If a radio button group uses `headingLevel`, use `stacked` when the radio button group is followed by a [field group](/skyux/components/field-group.md) or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-2.f42e7d466f28c5f366bc2051b5c7ec12.png)

 Content
--------

Make radio button group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, radio button group labels can use short sentences or sentence fragments.

For details about styling radio button group labels as headings, see the "Headings" section above.

Similarly, make radio button labels succinct and descriptive. But when necessary, radio button labels can use short sentences or sentence fragments.

Icon radio buttons use the [icon](/skyux/components/icon.md) component. For a list of common icons, see the [SKY UX icon inventory](/skyux/components/icon#section-inventory.md). Don't display heading text or label text on icon radio button groups.

 Layout
-------

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with `headingLevel` and `headingStyle` set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-1.23106409ac2d82070d48813123d08928.png)

Don't use a field group with a lone radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-2.dc2ff66f192a36b10dc8bc64e4a8d23b.png)

Do adjust the heading level and heading style of a radio button group to match the hierarchy of field groups.

 Accessibility
--------------

Radio button groups will automatically create `<fieldset>`and `<legend>` elements from their contents and heading text.

In most cases, radio button group labels are not treated as semantic `h` elements, but when necessary, you can specify a heading level and heading style. For example, when a lone radio button group appears on a form field with [field groups](/skyux/components/field-group.md), set the radio button group's `headingLevel` to `3` and `headingStyle` to `sky-font-heading-3` to match the semantic and visual hierarchy of field group headings.

 Related information
--------------------

### Components

*   [Action buttons](/skyux/components/action-button.md)
*   [Checkbox](/skyux/components/checkbox.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Modal](/skyux/components/modal.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/radio/radio.module.ts#L42) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyRadioModule
---------------

Type: Module

`import { SkyRadioModule } from '@skyux/forms';`

 SkyRadioGroupComponent
-----------------------

Type: Component

Selector: `sky-radio-group`

Organizes radio buttons into a group. It is required for radio buttons on Angular reactive forms, and we recommend using it with all radio buttons. On Angular forms, the component manages the selected values and keeps the forms up-to-date. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

### Inputs

#### `name: string`

Required

The name for the collection of radio buttons that the component groups together. This property overwrites the deprecated `name` property on individual `sky-radio` elements, and it is required unless the `name` property is set on individual `sky-radio` elements.

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The ARIA label for the radio button group. This sets the radio button group's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The HTML element ID of the element that labels the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyRadioGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyRadioGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string | undefined`

The text to display as the radio group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to radio group. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the radio button group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the radio button group.

#### `tabIndex: number | undefined`

The index for all the radio buttons in the group. If the index is not defined, the indices for individual radio buttons are set to their positions on load. This property supports accessibility by placing focus on the currently selected radio button. If no radio button is selected, it places focus on the first or last button depending on how users navigate to the radio button group.

#### `value: any`

The value of the radio button to select by default when the group loads. The value corresponds to the `value` property of an individual `sky-radio` element within the group.

 SkyRadioComponent
------------------

Type: Component

Selector: `sky-radio`

Renders a SKY UX-themed replacement for an HTML `input` element with `type="radio"`. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

### Inputs

#### `value: any`

Required

The value bound to the radio button's `value` property. The value usually corresponds to the radio button's label, which you specify with the `sky-radio-label` component.

#### `checked: boolean`

Whether the radio button is selected.

Default: `false`

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio button label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to radio button. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the radio button. To group radio buttons like in the demo above, place the `sky-switch-icon-group` class on the direct parent element of the radio buttons.

#### `id: string | undefined`

The ID for the radio button. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the radio button. This sets the radio button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md) when the radio button does not include a visible label. You must set this property for icon radio buttons. If the radio button includes a visible label, use `labelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button does not include a visible label, use `label` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `name: string | undefined`

This property is deprecated in favor of the `name` property on the `sky-radio-group element`. We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to, then this property specifies a name for a group of radio buttons.

#### `radioType: SkyRadioType`

Warning: **Deprecated.** radioType is no longer supported

The background color type after users select an icon radio button. The valid options correspond [the label component's](/skyux/components/label.md) label types. `danger` creates a red background, `info` creates a blue background, `success` creates a green background, and `warning` creates an orange background.

Default: `"info"`

#### `tabindex: number`

This property is deprecated in favor of the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio button. If the index is not defined, it is set to the position of the radio button on load.

### Outputs

#### `change: EventEmitter<SkyRadioChange>`

Fires when users select a radio button.

#### `checkedChange: EventEmitter<boolean>`

Fires when the selected value changes.

#### `disabledChange: EventEmitter<boolean>`

Fires when the selected value changes.

 SkyRadioLabelComponent
-----------------------

Type: Component

Selector: `sky-radio-label`

Warning: **Deprecated.** Use `labelText` input on `sky-radio-component` instead.

Specifies a label for the radio button. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button element.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyRadioGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingLevel = 3 | 4 | 5

 SkyRadioGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingStyle = 3 | 4 | 5

 SkyRadioType
-------------

Type: Type alias

Warning: **Deprecated.** radioType is no longer supported

    type SkyRadioType = "danger" | "info" | "success" | "warning"

 SkyRadioChange
---------------

Type: Interface

Fires when users select a radio button.

    interface SkyRadioChange {
      value: any;
    }

### Properties

#### `value: any`

The value from the radio component.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyRadioGroupHarness
---------------------

Type: Class

`import { SkyRadioGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyRadioGroupHeadingLevel>`

The semantic heading level used for the radio group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyRadioGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyRadioGroupHeadingStyle>`

The heading style used for the radio group.

#### Returns

`Promise<SkyRadioGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the radio group's heading text. If `headingHidden` is true, the text will still be returned.

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

Gets the radio group's hint text.

#### Returns

`Promise<string>`

#### `getRadioButton(filter: SkyRadioHarnessFilters): Promise<SkyRadioHarness>`

Gets a specific radio button based on the filter criteria.

#### Parameters

##### `filter: SkyRadioHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyRadioHarness>`

#### `getRadioButtons(filters?: SkyRadioHarnessFilters): Promise<SkyRadioHarness[]>`

Gets an array of radio buttons based on the filter criteria. If no filter is provided, returns all radio buttons.

#### Parameters

##### `filters?: SkyRadioHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyRadioHarness[]>`

#### `getRequired(): Promise<boolean>`

Whether the radio group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the radio group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the radio group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `SkyRadioGroupHarness.with(filters: SkyRadioGroupHarnessFilters): HarnessPredicate<SkyRadioGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioGroupHarness>`

 SkyRadioGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

    interface SkyRadioGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRadioHarness
----------------

Type: Class

`import { SkyRadioHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio button component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the radio button.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the radio button in a checked state if it is currently unchecked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the radio button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the radio button's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the radio button's aria-labelledby.

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

Gets the radio button's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the radio button's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the radio button's name.

#### Returns

`Promise<null | string>`

#### `isChecked(): Promise<boolean>`

Whether the radio button is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the radio button is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the radio button is focused.

#### Returns

`Promise<boolean>`

#### `SkyRadioHarness.with(filters: SkyRadioHarnessFilters): HarnessPredicate<SkyRadioHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioHarness>`

 SkyRadioHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

    interface SkyRadioHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Radio button
============

Radio buttons let users select one item from a short list of items.Usage
------

### Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-1.0faf1ea491585986a7755c2ae094d652.png)

Do use radio button groups when users select a single item from a short list of options in a modal.

Use icon radio button groups when icons clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-4.253385ed82a0e6333979ce9bcf086f30.png)

Do use icon radio button groups when icons clearly illustrate the options.

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using [action buttons](/skyux/components/action-button.md) instead. See the [form layout](/skyux/design/guidelines/form-design#form-layout.md) guidelines for more information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-5.6377ae12e3f2b2e54402a3cf867bd5f1.png)

Do use radio buttons to enable conditional inputs as part of a task.

### Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-6.b5d15ab9095bf93f6a38244162ff6a7b.png)

Don't use radio buttons for a long list of options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-7.6918953b44ee81a622c16c675a76c1f8.png)

Do use different selection controls for more than five choices.

Don't use radio buttons for two options that are exact opposites. Use a [checkbox](/skyux/components/checkbox.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-8.bb1dced3921747be3200eb3fc0964cb4.png)

Don't use radio buttons to represent exact opposites.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-9.01937762fa8b73247dabd00f0b1631be.png)

Do use a checkbox to represent exact opposites.

Don't use radio buttons when user selections significantly alter the workflow. Use [action buttons](/skyux/components/action-button.md) instead, and place them at the beginning of the task.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-10.b03b6b3095bcaab8a3d5229d84942088.png)

Don't use radio buttons for options that significantly alter the workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-11.16da7d131835d6e108ef4399b49773e4.png)

Do use action buttons for decisions that branch users into significantly different workflows.

 Anatomy
--------

### Individual radio button

1

Radio button

2

Label

3

Help inline button (optional)

4

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-anatomy.21f90955fe130bf661114e96db2f3beb.png)

### Radio button group

1

Label

2

Radio buttons

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-group-anatomy.7c8861e2e913d0b8b543c025fcd3f082.png)

### Icon radio button group

1

Icon radio button

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-icon-radio-button-group-anatomy.d02cffe93d8037fcb903aad8ea8d9785.png)

 Options
--------

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a radio button group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-heading-option.e8a1d1a3b06eb0c9ae2f35202bf68d1c.png)

Radio button group labels can be turned into HTML headings.

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the radio button group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-1.26cce06c1b3a5b98e02f4ffccb3be907.png)

If a radio button group uses `headingLevel`, use `stacked` when the radio button group is followed by a [field group](/skyux/components/field-group.md) or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-2.f42e7d466f28c5f366bc2051b5c7ec12.png)

 Content
--------

Make radio button group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, radio button group labels can use short sentences or sentence fragments.

For details about styling radio button group labels as headings, see the "Headings" section above.

Similarly, make radio button labels succinct and descriptive. But when necessary, radio button labels can use short sentences or sentence fragments.

Icon radio buttons use the [icon](/skyux/components/icon.md) component. For a list of common icons, see the [SKY UX icon inventory](/skyux/components/icon#section-inventory.md). Don't display heading text or label text on icon radio button groups.

 Layout
-------

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with `headingLevel` and `headingStyle` set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-1.23106409ac2d82070d48813123d08928.png)

Don't use a field group with a lone radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-2.dc2ff66f192a36b10dc8bc64e4a8d23b.png)

Do adjust the heading level and heading style of a radio button group to match the hierarchy of field groups.

 Accessibility
--------------

Radio button groups will automatically create `<fieldset>`and `<legend>` elements from their contents and heading text.

In most cases, radio button group labels are not treated as semantic `h` elements, but when necessary, you can specify a heading level and heading style. For example, when a lone radio button group appears on a form field with [field groups](/skyux/components/field-group.md), set the radio button group's `headingLevel` to `3` and `headingStyle` to `sky-font-heading-3` to match the semantic and visual hierarchy of field group headings.

 Related information
--------------------

### Components

*   [Action buttons](/skyux/components/action-button.md)
*   [Checkbox](/skyux/components/checkbox.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Modal](/skyux/components/modal.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/radio/radio.module.ts#L42) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyRadioModule
---------------

Type: Module

`import { SkyRadioModule } from '@skyux/forms';`

 SkyRadioGroupComponent
-----------------------

Type: Component

Selector: `sky-radio-group`

Organizes radio buttons into a group. It is required for radio buttons on Angular reactive forms, and we recommend using it with all radio buttons. On Angular forms, the component manages the selected values and keeps the forms up-to-date. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

### Inputs

#### `name: string`

Required

The name for the collection of radio buttons that the component groups together. This property overwrites the deprecated `name` property on individual `sky-radio` elements, and it is required unless the `name` property is set on individual `sky-radio` elements.

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The ARIA label for the radio button group. This sets the radio button group's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The HTML element ID of the element that labels the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyRadioGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyRadioGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string | undefined`

The text to display as the radio group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to radio group. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the radio button group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the radio button group.

#### `tabIndex: number | undefined`

The index for all the radio buttons in the group. If the index is not defined, the indices for individual radio buttons are set to their positions on load. This property supports accessibility by placing focus on the currently selected radio button. If no radio button is selected, it places focus on the first or last button depending on how users navigate to the radio button group.

#### `value: any`

The value of the radio button to select by default when the group loads. The value corresponds to the `value` property of an individual `sky-radio` element within the group.

 SkyRadioComponent
------------------

Type: Component

Selector: `sky-radio`

Renders a SKY UX-themed replacement for an HTML `input` element with `type="radio"`. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

### Inputs

#### `value: any`

Required

The value bound to the radio button's `value` property. The value usually corresponds to the radio button's label, which you specify with the `sky-radio-label` component.

#### `checked: boolean`

Whether the radio button is selected.

Default: `false`

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio button label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to radio button. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the radio button. To group radio buttons like in the demo above, place the `sky-switch-icon-group` class on the direct parent element of the radio buttons.

#### `id: string | undefined`

The ID for the radio button. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the radio button. This sets the radio button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md) when the radio button does not include a visible label. You must set this property for icon radio buttons. If the radio button includes a visible label, use `labelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button does not include a visible label, use `label` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `name: string | undefined`

This property is deprecated in favor of the `name` property on the `sky-radio-group element`. We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to, then this property specifies a name for a group of radio buttons.

#### `radioType: SkyRadioType`

Warning: **Deprecated.** radioType is no longer supported

The background color type after users select an icon radio button. The valid options correspond [the label component's](/skyux/components/label.md) label types. `danger` creates a red background, `info` creates a blue background, `success` creates a green background, and `warning` creates an orange background.

Default: `"info"`

#### `tabindex: number`

This property is deprecated in favor of the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio button. If the index is not defined, it is set to the position of the radio button on load.

### Outputs

#### `change: EventEmitter<SkyRadioChange>`

Fires when users select a radio button.

#### `checkedChange: EventEmitter<boolean>`

Fires when the selected value changes.

#### `disabledChange: EventEmitter<boolean>`

Fires when the selected value changes.

 SkyRadioLabelComponent
-----------------------

Type: Component

Selector: `sky-radio-label`

Warning: **Deprecated.** Use `labelText` input on `sky-radio-component` instead.

Specifies a label for the radio button. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button element.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyRadioGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingLevel = 3 | 4 | 5

 SkyRadioGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingStyle = 3 | 4 | 5

 SkyRadioType
-------------

Type: Type alias

Warning: **Deprecated.** radioType is no longer supported

    type SkyRadioType = "danger" | "info" | "success" | "warning"

 SkyRadioChange
---------------

Type: Interface

Fires when users select a radio button.

    interface SkyRadioChange {
      value: any;
    }

### Properties

#### `value: any`

The value from the radio component.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyRadioGroupHarness
---------------------

Type: Class

`import { SkyRadioGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyRadioGroupHeadingLevel>`

The semantic heading level used for the radio group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyRadioGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyRadioGroupHeadingStyle>`

The heading style used for the radio group.

#### Returns

`Promise<SkyRadioGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the radio group's heading text. If `headingHidden` is true, the text will still be returned.

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

Gets the radio group's hint text.

#### Returns

`Promise<string>`

#### `getRadioButton(filter: SkyRadioHarnessFilters): Promise<SkyRadioHarness>`

Gets a specific radio button based on the filter criteria.

#### Parameters

##### `filter: SkyRadioHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyRadioHarness>`

#### `getRadioButtons(filters?: SkyRadioHarnessFilters): Promise<SkyRadioHarness[]>`

Gets an array of radio buttons based on the filter criteria. If no filter is provided, returns all radio buttons.

#### Parameters

##### `filters?: SkyRadioHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyRadioHarness[]>`

#### `getRequired(): Promise<boolean>`

Whether the radio group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the radio group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the radio group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `SkyRadioGroupHarness.with(filters: SkyRadioGroupHarnessFilters): HarnessPredicate<SkyRadioGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioGroupHarness>`

 SkyRadioGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

    interface SkyRadioGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRadioHarness
----------------

Type: Class

`import { SkyRadioHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio button component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the radio button.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the radio button in a checked state if it is currently unchecked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the radio button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the radio button's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the radio button's aria-labelledby.

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

Gets the radio button's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the radio button's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the radio button's name.

#### Returns

`Promise<null | string>`

#### `isChecked(): Promise<boolean>`

Whether the radio button is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the radio button is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the radio button is focused.

#### Returns

`Promise<boolean>`

#### `SkyRadioHarness.with(filters: SkyRadioHarnessFilters): HarnessPredicate<SkyRadioHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioHarness>`

 SkyRadioHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

    interface SkyRadioHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Radio group with standard setup

Edit in StackBlitz

#### Payment method

Show help content for

Card methods require proof of identification.

CashShow help content for

Check

Apple pay

Credit

A 2% late fee is applied to payments made after the due date.

Debit

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-radio-group
        data-sky-id="radio-group"
        formControlName="paymentMethod"
        headingLevel="4"
        headingText="Payment method"
        [helpPopoverContent]="helpPopoverContent"
        [helpPopoverTitle]="helpPopoverTitle"
        [hintText]="hintText"
      >
        @for (option of paymentOptions; track option) {
          <sky-radio
            [disabled]="option.disabled"
            [value]="option.value"
            [labelText]="option.name"
            [helpPopoverContent]="option.helpContent"
            [hintText]="option.hintText"
          />
        }
        @if (paymentMethod.errors?.['processingIssue']) {
          <sky-form-error
            errorName="processingIssue"
            errorText="An error occurred with this payment method. Please contact us to resolve."
          />
        }
      </sky-radio-group>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyRadioGroupHarness } from '@skyux/forms/testing';
    
    import { FormsRadioStandardExampleComponent } from './example.component';
    
    describe('Basic radio group example', () => {
      async function setupTest(options: {
        dataSkyId: string;
      }): Promise<SkyRadioGroupHarness> {
        const fixture = TestBed.createComponent(FormsRadioStandardExampleComponent);
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyRadioGroupHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return harness;
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [NoopAnimationsModule, FormsRadioStandardExampleComponent],
        });
      });
    
      it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
        const harness = await setupTest({ dataSkyId: 'radio-group' });
    
        const radioButtons = await harness.getRadioButtons();
    
        await expectAsync(harness.getHeadingText()).toBeResolvedTo(
          'Payment method',
        );
        await expectAsync(harness.getHeadingLevel()).toBeResolvedTo(4);
        await expectAsync(harness.getHeadingStyle()).toBeResolvedTo(4);
        await expectAsync(harness.getHintText()).toBeResolvedTo(
          'Card methods require proof of identification.',
        );
    
        await expectAsync(radioButtons[0].getLabelText()).toBeResolvedTo('Cash');
        await expectAsync(radioButtons[0].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[1].getLabelText()).toBeResolvedTo('Check');
        await expectAsync(radioButtons[1].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[2].getLabelText()).toBeResolvedTo(
          'Apple pay',
        );
        await expectAsync(radioButtons[2].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[3].getLabelText()).toBeResolvedTo('Credit');
        await expectAsync(radioButtons[3].getHintText()).toBeResolvedTo(
          'A 2% late fee is applied to payments made after the due date.',
        );
    
        await expectAsync(radioButtons[4].getLabelText()).toBeResolvedTo('Debit');
        await expectAsync(radioButtons[4].getHintText()).toBeResolvedTo('');
      });
    
      it('should display an error message when there is a custom validation error', async () => {
        const harness = await setupTest({ dataSkyId: 'radio-group' });
    
        const radioHarness = (await harness.getRadioButtons())[1];
    
        await radioHarness.check();
    
        await expectAsync(harness.hasError('processingIssue')).toBeResolvedTo(true);
      });
    
      it('should show a help popover with the expected text', async () => {
        const harness = await setupTest({
          dataSkyId: 'radio-group',
        });
    
        await harness.clickHelpInline();
    
        const helpPopoverTitle = await harness.getHelpPopoverTitle();
        expect(helpPopoverTitle).toBe('Are there fees?');
    
        const helpPopoverContent = await harness.getHelpPopoverContent();
        expect(helpPopoverContent).toBe(
          `We don't charge fees for any payment method. The only exception is when credit card payments are late, which incurs a 2% fee.`,
        );
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
    import { SkyRadioModule } from '@skyux/forms';
    
    interface DemoForm {
      paymentMethod: FormControl<string | null>;
    }
    
    interface Item {
      name: string;
      value: string;
      disabled?: boolean;
      hintText?: string;
      helpContent?: string;
    }
    
    function validatePaymentMethod(
      control: AbstractControl,
    ): ValidationErrors | null {
      return control.value === 'check' ? { processingIssue: true } : null;
    }
    
    /**
     * @title Radio group with standard setup
     */
    @Component({
      selector: 'app-forms-radio-standard-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
    })
    export class FormsRadioStandardExampleComponent {
      protected formGroup: FormGroup<DemoForm>;
      protected helpPopoverContent =
        "We don't charge fees for any payment method. The only exception is when credit card payments are late, which incurs a 2% fee.";
      protected helpPopoverTitle = 'Are there fees?';
      protected hintText = 'Card methods require proof of identification.';
      protected paymentMethod: FormControl<string | null>;
    
      protected paymentOptions: Item[] = [
        {
          name: 'Cash',
          value: 'cash',
          helpContent:
            'We accept cash at any of our locations and affiliated partners.',
        },
        { name: 'Check', value: 'check' },
        { name: 'Apple pay', value: 'apple', disabled: true },
        {
          name: 'Credit',
          value: 'credit',
          hintText: 'A 2% late fee is applied to payments made after the due date.',
        },
        { name: 'Debit', value: 'debit' },
      ];
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.paymentMethod = this.#formBuilder.control(
          this.paymentOptions[0].name,
          {
            validators: [validatePaymentMethod],
          },
        );
    
        this.formGroup = this.#formBuilder.group({
          paymentMethod: this.paymentMethod,
        });
      }
    }
### Radio group with help key

Edit in StackBlitz

#### Payment method

Show help content for

Card methods require proof of identification.

CashShow help content for

Check

Apple pay

Credit

A 2% late fee is applied to payments made after the due date.

Debit

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-radio-group
        data-sky-id="radio-group"
        formControlName="paymentMethod"
        headingLevel="4"
        headingText="Payment method"
        helpKey="payment-help"
        [hintText]="hintText"
      >
        @for (option of paymentOptions; track option) {
          <sky-radio
            [disabled]="option.disabled"
            [value]="option.value"
            [labelText]="option.name"
            [helpKey]="option.helpKey"
            [hintText]="option.hintText"
          />
        }
        @if (paymentMethod.errors?.['processingIssue']) {
          <sky-form-error
            errorName="processingIssue"
            errorText="An error occurred with this payment method. Please contact us to resolve."
          />
        }
      </sky-radio-group>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyRadioGroupHarness } from '@skyux/forms/testing';
    
    import { FormsRadioHelpKeyExampleComponent } from './example.component';
    
    describe('Basic radio group example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        radioGroupHarness: SkyRadioGroupHarness;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(FormsRadioHelpKeyExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        const radioGroupHarness = await loader.getHarness(
          SkyRadioGroupHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { radioGroupHarness, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            NoopAnimationsModule,
            FormsRadioHelpKeyExampleComponent,
            SkyHelpTestingModule,
          ],
        });
      });
    
      it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
        const { radioGroupHarness } = await setupTest({ dataSkyId: 'radio-group' });
    
        const radioButtons = await radioGroupHarness.getRadioButtons();
    
        await expectAsync(radioGroupHarness.getHeadingText()).toBeResolvedTo(
          'Payment method',
        );
        await expectAsync(radioGroupHarness.getHeadingLevel()).toBeResolvedTo(4);
        await expectAsync(radioGroupHarness.getHeadingStyle()).toBeResolvedTo(4);
        await expectAsync(radioGroupHarness.getHintText()).toBeResolvedTo(
          'Card methods require proof of identification.',
        );
    
        await expectAsync(radioButtons[0].getLabelText()).toBeResolvedTo('Cash');
        await expectAsync(radioButtons[0].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[1].getLabelText()).toBeResolvedTo('Check');
        await expectAsync(radioButtons[1].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[2].getLabelText()).toBeResolvedTo(
          'Apple pay',
        );
        await expectAsync(radioButtons[2].getHintText()).toBeResolvedTo('');
    
        await expectAsync(radioButtons[3].getLabelText()).toBeResolvedTo('Credit');
        await expectAsync(radioButtons[3].getHintText()).toBeResolvedTo(
          'A 2% late fee is applied to payments made after the due date.',
        );
    
        await expectAsync(radioButtons[4].getLabelText()).toBeResolvedTo('Debit');
        await expectAsync(radioButtons[4].getHintText()).toBeResolvedTo('');
      });
    
      it('should display an error message when there is a custom validation error', async () => {
        const { radioGroupHarness } = await setupTest({ dataSkyId: 'radio-group' });
    
        const radioHarness = (await radioGroupHarness.getRadioButtons())[1];
    
        await radioHarness.check();
    
        await expectAsync(
          radioGroupHarness.hasError('processingIssue'),
        ).toBeResolvedTo(true);
      });
    
      it('should have the correct help key for radio group', async () => {
        const { radioGroupHarness, helpController } = await setupTest({
          dataSkyId: 'radio-group',
        });
    
        await radioGroupHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('payment-help');
      });
    
      it('should have the correct help key for radio', async () => {
        const { radioGroupHarness, helpController } = await setupTest({
          dataSkyId: 'radio-group',
        });
        const radioHarness = (await radioGroupHarness.getRadioButtons())[0];
    
        await radioHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('cash-help');
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
    import { SkyRadioModule } from '@skyux/forms';
    
    interface DemoForm {
      paymentMethod: FormControl<string | null>;
    }
    
    interface Item {
      name: string;
      value: string;
      disabled?: boolean;
      hintText?: string;
      helpKey?: string;
    }
    
    function validatePaymentMethod(
      control: AbstractControl,
    ): ValidationErrors | null {
      return control.value === 'check' ? { processingIssue: true } : null;
    }
    
    /**
     * @title Radio group with help key
     */
    @Component({
      selector: 'app-forms-radio-help-key-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
    })
    export class FormsRadioHelpKeyExampleComponent {
      protected formGroup: FormGroup<DemoForm>;
      protected hintText = 'Card methods require proof of identification.';
      protected paymentMethod: FormControl<string | null>;
    
      protected paymentOptions: Item[] = [
        {
          name: 'Cash',
          value: 'cash',
          helpKey: 'cash-help',
        },
        { name: 'Check', value: 'check' },
        { name: 'Apple pay', value: 'apple', disabled: true },
        {
          name: 'Credit',
          value: 'credit',
          hintText: 'A 2% late fee is applied to payments made after the due date.',
        },
        { name: 'Debit', value: 'debit' },
      ];
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.paymentMethod = this.#formBuilder.control(
          this.paymentOptions[0].name,
          {
            validators: [validatePaymentMethod],
          },
        );
    
        this.formGroup = this.#formBuilder.group({
          paymentMethod: this.paymentMethod,
        });
      }
    }
### Radio group with icons

Edit in StackBlitz

View

Table

List

Map

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-radio-group
        class="sky-switch-icon-group"
        formControlName="myView"
        headingHidden="true"
        headingText="View"
      >
        @for (view of views; track view) {
          <sky-radio
            [labelHidden]="true"
            [iconName]="view.iconName"
            [labelText]="view.label"
            [value]="view.name"
          />
        }
      </sky-radio-group>
    </form>

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyRadioModule } from '@skyux/forms';
    
    interface Item {
      iconName: string;
      label: string;
      name: string;
    }
    
    /**
     * @title Radio group with icons
     */
    @Component({
      selector: 'app-forms-radio-icon-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
    })
    export class FormsRadioIconExampleComponent {
      protected formGroup: FormGroup;
    
      protected views: Item[] = [
        { iconName: 'table', label: 'Table', name: 'table' },
        { iconName: 'text-number-list-ltr', label: 'List', name: 'list' },
        { iconName: 'location', label: 'Map', name: 'map' },
      ];
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          myView: this.views[0].name,
        });
      }
    }

# Testing

                  Skip to Main Content

 Radio button
============

Radio buttons let users select one item from a short list of items.

 Usage
------

### Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-1.0faf1ea491585986a7755c2ae094d652.png)

Do use radio button groups when users select a single item from a short list of options in a modal.

Use icon radio button groups when icons clearly communicate the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-4.253385ed82a0e6333979ce9bcf086f30.png)

Do use icon radio button groups when icons clearly illustrate the options.

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using [action buttons](/skyux/components/action-button.md) instead. See the [form layout](/skyux/design/guidelines/form-design#form-layout.md) guidelines for more information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-5.6377ae12e3f2b2e54402a3cf867bd5f1.png)

Do use radio buttons to enable conditional inputs as part of a task.

### Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-6.b5d15ab9095bf93f6a38244162ff6a7b.png)

Don't use radio buttons for a long list of options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-7.6918953b44ee81a622c16c675a76c1f8.png)

Do use different selection controls for more than five choices.

Don't use radio buttons for two options that are exact opposites. Use a [checkbox](/skyux/components/checkbox.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-8.bb1dced3921747be3200eb3fc0964cb4.png)

Don't use radio buttons to represent exact opposites.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-9.01937762fa8b73247dabd00f0b1631be.png)

Do use a checkbox to represent exact opposites.

Don't use radio buttons when user selections significantly alter the workflow. Use [action buttons](/skyux/components/action-button.md) instead, and place them at the beginning of the task.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-10.b03b6b3095bcaab8a3d5229d84942088.png)

Don't use radio buttons for options that significantly alter the workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-11.16da7d131835d6e108ef4399b49773e4.png)

Do use action buttons for decisions that branch users into significantly different workflows.

 Anatomy
--------

### Individual radio button

1

Radio button

2

Label

3

Help inline button (optional)

4

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-anatomy.21f90955fe130bf661114e96db2f3beb.png)

### Radio button group

1

Label

2

Radio buttons

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-group-anatomy.7c8861e2e913d0b8b543c025fcd3f082.png)

### Icon radio button group

1

Icon radio button

2

Icon

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-icon-radio-button-group-anatomy.d02cffe93d8037fcb903aad8ea8d9785.png)

 Options
--------

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use `headingLevel` to specify a semantic heading level in the document structure and `headingStyle` to set the heading [font style](/skyux/design/styles/typography.md). For example, use a label as a heading to indicate that a radio button group is a form section just like other [field groups](/skyux/components/field-group.md). Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-heading-option.e8a1d1a3b06eb0c9ae2f35202bf68d1c.png)

Radio button group labels can be turned into HTML headings.

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the radio button group:

*   Is the last input inside a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-1.26cce06c1b3a5b98e02f4ffccb3be907.png)

If a radio button group uses `headingLevel`, use `stacked` when the radio button group is followed by a [field group](/skyux/components/field-group.md) or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-stacked-option-2.f42e7d466f28c5f366bc2051b5c7ec12.png)

 Content
--------

Make radio button group labels succinct and descriptive. In most cases, use nouns or noun phrases. When necessary, radio button group labels can use short sentences or sentence fragments.

For details about styling radio button group labels as headings, see the "Headings" section above.

Similarly, make radio button labels succinct and descriptive. But when necessary, radio button labels can use short sentences or sentence fragments.

Icon radio buttons use the [icon](/skyux/components/icon.md) component. For a list of common icons, see the [SKY UX icon inventory](/skyux/components/icon#section-inventory.md). Don't display heading text or label text on icon radio button groups.

 Layout
-------

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with `headingLevel` and `headingStyle` set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-1.23106409ac2d82070d48813123d08928.png)

Don't use a field group with a lone radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-layout-2.dc2ff66f192a36b10dc8bc64e4a8d23b.png)

Do adjust the heading level and heading style of a radio button group to match the hierarchy of field groups.

 Accessibility
--------------

Radio button groups will automatically create `<fieldset>`and `<legend>` elements from their contents and heading text.

In most cases, radio button group labels are not treated as semantic `h` elements, but when necessary, you can specify a heading level and heading style. For example, when a lone radio button group appears on a form field with [field groups](/skyux/components/field-group.md), set the radio button group's `headingLevel` to `3` and `headingStyle` to `sky-font-heading-3` to match the semantic and visual hierarchy of field group headings.

 Related information
--------------------

### Components

*   [Action buttons](/skyux/components/action-button.md)
*   [Checkbox](/skyux/components/checkbox.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Modal](/skyux/components/modal.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/radio/radio.module.ts#L42) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyRadioModule
---------------

Type: Module

`import { SkyRadioModule } from '@skyux/forms';`

 SkyRadioGroupComponent
-----------------------

Type: Component

Selector: `sky-radio-group`

Organizes radio buttons into a group. It is required for radio buttons on Angular reactive forms, and we recommend using it with all radio buttons. On Angular forms, the component manages the selected values and keeps the forms up-to-date. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

### Inputs

#### `name: string`

Required

The name for the collection of radio buttons that the component groups together. This property overwrites the deprecated `name` property on individual `sky-radio` elements, and it is required unless the `name` property is set on individual `sky-radio` elements.

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The ARIA label for the radio button group. This sets the radio button group's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The HTML element ID of the element that labels the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button group does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyRadioGroupHeadingLevel | undefined`

The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.

#### `headingStyle: SkyRadioGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `4`

#### `headingText: string | undefined`

The text to display as the radio group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to radio group. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `required: boolean`

Whether the input is required for form validation. When you set this property to `true`, the component adds `aria-required` and `required` attributes to the input element so that forms display an invalid state until the input element is complete. For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required).

Default: `false`

#### `stacked: boolean`

Whether the radio button group is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the radio button group.

#### `tabIndex: number | undefined`

The index for all the radio buttons in the group. If the index is not defined, the indices for individual radio buttons are set to their positions on load. This property supports accessibility by placing focus on the currently selected radio button. If no radio button is selected, it places focus on the first or last button depending on how users navigate to the radio button group.

#### `value: any`

The value of the radio button to select by default when the group loads. The value corresponds to the `value` property of an individual `sky-radio` element within the group.

 SkyRadioComponent
------------------

Type: Component

Selector: `sky-radio`

Renders a SKY UX-themed replacement for an HTML `input` element with `type="radio"`. When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

### Inputs

#### `value: any`

Required

The value bound to the radio button's `value` property. The value usually corresponds to the radio button's label, which you specify with the `sky-radio-label` component.

#### `checked: boolean`

Whether the radio button is selected.

Default: `false`

#### `disabled: boolean`

Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the radio button label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to radio button. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `iconName: string | undefined`

The SVG icon to display in place of the radio button. To group radio buttons like in the demo above, place the `sky-switch-icon-group` class on the direct parent element of the radio buttons.

#### `id: string | undefined`

The ID for the radio button. If a value is not provided, an autogenerated ID is used.

#### `label: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The ARIA label for the radio button. This sets the radio button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md) when the radio button does not include a visible label. You must set this property for icon radio buttons. If the radio button includes a visible label, use `labelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `labelHidden: boolean`

Indicates whether to hide the `labelText`.

Default: `false`

#### `labelText: string | undefined`

The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.

#### `labelledBy: string | undefined`

Warning: **Deprecated.** Use `labelText` instead.

The HTML element ID of the element that labels the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the radio button does not include a visible label, use `label` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `name: string | undefined`

This property is deprecated in favor of the `name` property on the `sky-radio-group element`. We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to, then this property specifies a name for a group of radio buttons.

#### `radioType: SkyRadioType`

Warning: **Deprecated.** radioType is no longer supported

The background color type after users select an icon radio button. The valid options correspond [the label component's](/skyux/components/label.md) label types. `danger` creates a red background, `info` creates a blue background, `success` creates a green background, and `warning` creates an orange background.

Default: `"info"`

#### `tabindex: number`

This property is deprecated in favor of the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio button. If the index is not defined, it is set to the position of the radio button on load.

### Outputs

#### `change: EventEmitter<SkyRadioChange>`

Fires when users select a radio button.

#### `checkedChange: EventEmitter<boolean>`

Fires when the selected value changes.

#### `disabledChange: EventEmitter<boolean>`

Fires when the selected value changes.

 SkyRadioLabelComponent
-----------------------

Type: Component

Selector: `sky-radio-label`

Warning: **Deprecated.** Use `labelText` input on `sky-radio-component` instead.

Specifies a label for the radio button. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button element.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyRadioGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingLevel = 3 | 4 | 5

 SkyRadioGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyRadioGroupHeadingStyle = 3 | 4 | 5

 SkyRadioType
-------------

Type: Type alias

Warning: **Deprecated.** radioType is no longer supported

    type SkyRadioType = "danger" | "info" | "success" | "warning"

 SkyRadioChange
---------------

Type: Interface

Fires when users select a radio button.

    interface SkyRadioChange {
      value: any;
    }

### Properties

#### `value: any`

The value from the radio component.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyRadioGroupHarness
---------------------

Type: Class

`import { SkyRadioGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyRadioGroupHeadingLevel>`

The semantic heading level used for the radio group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyRadioGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyRadioGroupHeadingStyle>`

The heading style used for the radio group.

#### Returns

`Promise<SkyRadioGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the radio group's heading text. If `headingHidden` is true, the text will still be returned.

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

Gets the radio group's hint text.

#### Returns

`Promise<string>`

#### `getRadioButton(filter: SkyRadioHarnessFilters): Promise<SkyRadioHarness>`

Gets a specific radio button based on the filter criteria.

#### Parameters

##### `filter: SkyRadioHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyRadioHarness>`

#### `getRadioButtons(filters?: SkyRadioHarnessFilters): Promise<SkyRadioHarness[]>`

Gets an array of radio buttons based on the filter criteria. If no filter is provided, returns all radio buttons.

#### Parameters

##### `filters?: SkyRadioHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyRadioHarness[]>`

#### `getRequired(): Promise<boolean>`

Whether the radio group is required.

#### Returns

`Promise<boolean>`

#### `getStacked(): Promise<boolean>`

Whether the radio group is stacked.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the radio group has errors.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `SkyRadioGroupHarness.with(filters: SkyRadioGroupHarnessFilters): HarnessPredicate<SkyRadioGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioGroupHarness>`

 SkyRadioGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

    interface SkyRadioGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRadioHarness
----------------

Type: Class

`import { SkyRadioHarness } from '@skyux/forms/testing';`

Harness for interacting with a radio button component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the radio button.

#### Returns

`Promise<void>`

#### `check(): Promise<void>`

Puts the radio button in a checked state if it is currently unchecked.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the radio button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the radio button's aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the radio button's aria-labelledby.

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

Gets the radio button's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the label is hidden. Only supported when using the `labelText` input to set the label.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<undefined | string>`

Gets the radio button's label text. If the label is set via `labelText` and `labelHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getName(): Promise<null | string>`

Gets the radio button's name.

#### Returns

`Promise<null | string>`

#### `isChecked(): Promise<boolean>`

Whether the radio button is checked.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the radio button is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the radio button is focused.

#### Returns

`Promise<boolean>`

#### `SkyRadioHarness.with(filters: SkyRadioHarnessFilters): HarnessPredicate<SkyRadioHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRadioHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRadioHarnessFilters`

#### Returns

`HarnessPredicate<SkyRadioHarness>`

 SkyRadioHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

    interface SkyRadioHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
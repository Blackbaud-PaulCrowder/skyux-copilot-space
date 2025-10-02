---
component: 'radio'
type: 'api-documentation'
description: 'API documentation for the radio component including components, interfaces, and types.'
---

# Radio API Documentation

## Components and Directives

#### FormsRadioHelpKeyExampleComponent

**Selector:** `app-forms-radio-help-key-example`

**Package:** `@skyux/code-examples`

#### FormsRadioIconExampleComponent

**Selector:** `app-forms-radio-icon-example`

**Package:** `@skyux/code-examples`

#### FormsRadioStandardExampleComponent

**Selector:** `app-forms-radio-standard-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Package:** `@skyux/code-examples`

#### SkyRadioGroupComponent

Organizes radio buttons into a group. It is required for radio
buttons on Angular reactive forms, and we recommend using it with all radio buttons.
On Angular forms, the component manages the selected values and keeps the forms up-to-date.
When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

**Selector:** `sky-radio-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingText`: `string | undefined` - The text to display as the radio group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the radio group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to radio group. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete.
For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required). (default: false)
- `ariaLabel`: `string | undefined` - The ARIA label for the radio button group. This sets the
radio button group's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button group includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button group does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `disabled`: `boolean` - Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `headingLevel`: `SkyRadioGroupHeadingLevel | undefined` - The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.
- `headingStyle`: `SkyRadioGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 4)
- `name`: `string` - The name for the collection of radio buttons that the component groups together.
This property overwrites the deprecated `name` property on individual `sky-radio` elements,
and it is required unless the `name` property is set on individual `sky-radio` elements.
- `stacked`: `boolean` - Whether the radio button group is stacked on another form component. When specified,
the appropriate vertical spacing is automatically added to the radio button group.
- `tabIndex`: `number | undefined` - The index for all the radio buttons in the group. If the index is not defined,
the indices for individual radio buttons are set to their positions on load.
This property supports accessibility by placing focus on the currently selected radio
button. If no radio button is selected, it places focus on the first or last button
depending on how users navigate to the radio button group.
- `value`: `any` - The value of the radio button to select by default when the group loads.
The value corresponds to the `value` property of an individual `sky-radio` element within the
group.

#### SkyRadioLabelComponent

Specifies a label for the radio button. To display a help button beside the label, include a help button element,
such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-radio-label`

**Package:** `@skyux/forms`

#### SkyRadioComponent

Renders a SKY UX-themed replacement for an HTML `input` element
with `type="radio"`. When users select a radio button, its value is driven through an
`ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

**Selector:** `sky-radio`

**Package:** `@skyux/forms`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the radio button label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to radio button. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `iconName`: `string | undefined` - The SVG icon to display in place of the radio button. To group radio buttons like in
the demo above, place the `sky-switch-icon-group` class on the direct parent element of the
radio buttons.
- `labelHidden`: `boolean` - Indicates whether to hide the `labelText`. (default: false)
- `labelText`: `string | undefined` - The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.
- `checked`: `boolean` - Whether the radio button is selected. (default: false)
- `disabled`: `boolean` - Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `id`: `string | undefined` - The ID for the radio button.
If a value is not provided, an autogenerated ID is used.
- `label`: `string | undefined` - The ARIA label for the radio button. This sets the radio button's `aria-label`
attribute to provide a text equivalent for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
when the radio button does not include a visible label. You must set this property for icon
radio buttons. If the radio button includes a visible label, use `labelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels
the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button does not include a visible label, use `label` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `name`: `string | undefined` - This property is deprecated in favor of the `name` property on the `sky-radio-group element`.
We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to,
then this property specifies a name for a group of radio buttons.
- `radioType`: `SkyRadioType` - The background color type after users select an icon radio button.
The valid options correspond
[the label component's](https://developer.blackbaud.com/skyux/components/label)
label types. `danger` creates a red background, `info` creates a blue background,
`success` creates a green background, and `warning` creates an orange background. (default: "info")
- `tabindex`: `number` - This property is deprecated in favor of
the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio
button. If the index is not defined, it is set to the position of the radio button on load.
- `value`: `any` - The value bound to the radio button's `value` property. The value usually
corresponds to the radio button's label, which you specify with the `sky-radio-label`
component.

**Outputs:**

- `change`: `EventEmitter<SkyRadioChange>` - Fires when users select a radio button.
- `checkedChange`: `EventEmitter<boolean>` - Fires when the selected value changes.
- `disabledChange`: `EventEmitter<boolean>` - Fires when the selected value changes.
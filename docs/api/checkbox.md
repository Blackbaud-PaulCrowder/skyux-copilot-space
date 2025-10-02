---
component: 'checkbox'
type: 'api-documentation'
description: 'API documentation for the checkbox component including components, interfaces, and types.'
---

# Checkbox API Documentation

## Components and Directives

#### FormsCheckboxBasicExampleComponent

**Selector:** `app-forms-checkbox-basic-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxHelpKeyExampleComponent

**Selector:** `app-forms-checkbox-help-key-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### SkyBoxComponent

Provides a common look-and-feel for box content with options to display a common box header, specify body content, and display common box controls.

**Selector:** `sky-box`

**Package:** `@skyux/layout`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the box. This sets the box's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the box includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the box. This sets the box's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the box does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `ariaRole`: `string | undefined` - The ARIA role for the box
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating what the box contains. For information about
how an ARIA role indicates what an item represents on a web page,
see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).
- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingLevel`: `SkyBoxHeadingLevel` - The semantic heading level in the document structure. The default is 2. (default: 2)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the box heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the box heading. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `headingStyle`: `SkyBoxHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 2)
- `headingText`: `string | undefined` - The text to display as the box's heading.

#### SkyCheckboxGroupComponent

Organizes checkboxes into a group.

**Selector:** `sky-checkbox-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingText`: `string` - The text to display as the checkbox group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox group fieldset legend. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `required`: `boolean` - Whether the checkbox group is required. (default: false)
- `headingLevel`: `SkyCheckboxGroupHeadingLevel | undefined` - The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.
- `headingStyle`: `SkyCheckboxGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 4)
- `stacked`: `boolean` - Whether the checkbox group is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox group.

#### SkyCheckboxLabelComponent

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-checkbox-label`

**Package:** `@skyux/forms`

#### SkyCheckboxComponent

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value
is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

**Selector:** `sky-checkbox`

**Package:** `@skyux/forms`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `iconName`: `string | undefined` - The SVG icon to display in place of the checkbox. To group icon checkboxes
like in the demo, place the checkboxes within a `sky-checkbox-group`.
- `labelHidden`: `boolean` - Indicates whether to hide the `labelText`. (default: false)
- `labelText`: `string | undefined` - The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only.
Specifying `labelText` also enables automatic error message handling for checkbox.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete. (default: false)
- `stacked`: `boolean` - Whether the checkbox is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group,
set `stacked` on the checkbox group component instead. (default: false)
- `tabindex`: `number | undefined` - The index for the checkbox. If not defined, the index is set to the position of the
checkbox on load. (default: 0)
- `checkboxType`: `string` - The background color type after users select a checkbox where the
`icon` property displays an icon in place of the checkbox. The valid options correspond to
[the label component's](https://developer.blackbaud.com/skyux/components/label)
label types. `"info"` creates a blue background, `"success"` creates a green
background, `"warning"` creates an orange background, and `"danger"` creates a red background. (default: "info")
- `checked`: `boolean` - Whether the checkbox is selected.
- `disabled`: `boolean` - Whether the checkbox is disabled.
- `id`: `string | undefined` - The ID for the checkbox.
If a value is not provided, an autogenerated ID is used.
- `indeterminate`: `boolean` - Whether the checkbox is in the indeterminate state. This has no visual effect for icon checkboxes.
- `label`: `string | undefined` - The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility)
when the checkbox does not include a visible label. You must set this property for icon
checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels the
checkbox. This sets the checkbox's `aria-labelledby` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
If the checkbox does not include a visible label, use `label` instead.
- `name`: `string` - The name for the checkbox.
If a value is not provided, an autogenerated ID is used.

**Outputs:**

- `change`: `EventEmitter<SkyCheckboxChange>` - Fires when the selected value changes.
- `checkedChange`: `Observable<boolean>` - Fires when users select or deselect the checkbox.
- `disabledChange`: `Observable<boolean>` - Fires when the selected value changes.
- `indeterminateChange`: `Observable<boolean>` - Fires when the indeterminate state changes.
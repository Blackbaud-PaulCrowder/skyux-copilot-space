---
component: 'box'
type: 'api-documentation'
description: 'API documentation for the box component including components, interfaces, and types.'
---

# Box API Documentation

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

#### FormsInputBoxBasicExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Package:** `@skyux/code-examples`

#### LayoutBoxBasicExampleComponent

**Selector:** `app-layout-box-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutBoxHelpKeyExampleComponent

**Selector:** `app-layout-box-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyBoxContentComponent

Specifies the body content to display inside the box and provides padding around that content.

**Selector:** `sky-box-content`

**Package:** `@skyux/layout`

#### SkyBoxControlsComponent

Specifies the controls to display in upper right corner of the box. These buttons typically let users edit the box content.

**Selector:** `sky-box-controls`

**Package:** `@skyux/layout`

#### SkyBoxHeaderComponent

Specifies a header for the box.

**Selector:** `sky-box-header`

**Package:** `@skyux/layout`

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

#### SkyInputBoxControlDirective

**Selector:** `input:not([skyId]):not(.sky-form-control),select:not([skyId]):not(.sky-form-control),textarea:not([skyId]):not(.sky-form-control)`

**Package:** `@skyux/forms`

**Inputs:**

- `autocomplete`: `string | undefined`

#### SkyInputBoxComponent

A wrapper component that provides styling and accessibility to form elements.

**Selector:** `sky-input-box`

**Package:** `@skyux/forms`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to visually highlight the input box as disabled. To disable the input box's
input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled`
property. If the input element is mapped to an Angular form control
(e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically;
if the input element is not associated with an Angular form control, the `disabled`
property on the input box must be set to `true` to visually indicate
the disabled state on the input box. (default: false)
- `hasErrors`: `boolean | undefined` - Whether to visually highlight the input box in an error state. If not specified, the input box
displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error. (default: undefined)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the input box label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the input box label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `labelText`: `string | undefined` - The text to display as the input's label and in known validation error messages. The label
will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX
component included in the input box.
- `characterLimit`: `number | undefined` - The maximum number of characters allowed in the input. A [SKY UX character count](https://developer.blackbaud.com/skyux/components/character-count)
will be placed on the input element with the appropriate validator.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `BooleanInput` - Whether the input box is stacked on another input box. When specified, the appropriate
vertical spacing is automatically added to the input box.

#### SkySelectionBoxDescriptionComponent

Specifies the description to display in a selection box.

**Selector:** `sky-selection-box-description`

**Package:** `@skyux/forms`

#### SkySelectionBoxGridComponent

Creates a grid layout for an array of selection boxes.

**Selector:** `sky-selection-box-grid`

**Package:** `@skyux/forms`

**Inputs:**

- `alignItems`: `SkySelectionBoxGridAlignItemsType` - How to display the selection boxes in the grid. (default: 'center')

#### SkySelectionBoxHeaderComponent

Specifies the header to display in a selection box.

**Selector:** `sky-selection-box-header`

**Package:** `@skyux/forms`

#### SkySelectionBoxComponent

Creates a button to present users with a choice or question before proceeding with a one-time process.

**Selector:** `sky-selection-box`

**Package:** `@skyux/forms`

**Inputs:**

- `control`: `SkyCheckboxComponent | SkyRadioComponent | undefined` - The radio button or checkbox to display in the selection box.
---
component: 'label'
type: 'api-documentation'
description: 'API documentation for the label component including components, interfaces, and types.'
---

# Label API Documentation

## Components and Directives

#### IndicatorsLabelBasicExampleComponent

**Selector:** `app-indicators-label-basic-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `daysUntilDue`: `number`
- `submitted`: `boolean`

#### SkyKeyInfoLabelComponent

Specifies a label to display in smaller text under or beside the value.
To display a help button beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-key-info` element and a `sky-control-help` CSS class on that help button element.

**Selector:** `sky-key-info-label`

**Package:** `@skyux/indicators`

#### SkyLabelComponent

**Selector:** `sky-label`

**Package:** `@skyux/indicators`

**Inputs:**

- `customDescription`: `string | undefined` - The text to be read by screen readers for users who cannot see
the indicator icon when `descriptionType` is `custom`.
- `descriptionType`: `SkyIndicatorDescriptionType | undefined` - The predefined text to be read by screen readers for users who cannot see the indicator icon.
This property is optional but will be required in future versions of SKY UX.
- `labelType`: `SkyLabelType | undefined` - The type of label to display. (default: 'info')

#### SkyDefinitionListLabelComponent

Specifies the label in a label-value pair.

**Selector:** `sky-definition-list-label`

**Package:** `@skyux/layout`

#### SkyCheckboxLabelComponent

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-checkbox-label`

**Package:** `@skyux/forms`

#### SkyFileAttachmentLabelComponent

Displays a label above the file attachment element. To display a help button
beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-file-attachment-label` element and a `sky-control-help` CSS class
on that help button element.

**Selector:** `sky-file-attachment-label`

**Package:** `@skyux/forms`

#### SkyRadioLabelComponent

Specifies a label for the radio button. To display a help button beside the label, include a help button element,
such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-radio-label`

**Package:** `@skyux/forms`

#### SkyToggleSwitchLabelComponent

Specifies the label to display beside the toggle switch. To display a help button beside the label, include a help
button element, such as `sky-help-inline`, in the `sky-toggle-switch` element and a `sky-control-help` CSS class on
that help button element.

**Selector:** `sky-toggle-switch-label`

**Package:** `@skyux/forms`

#### SkyScreenReaderLabelDirective

Adds the element to a screen reader only section of the body.
This prevents components' DOM from including text only intended for screen readers.

**Selector:** `[skyScreenReaderLabel]`

**Package:** `@skyux/core`

**Inputs:**

- `createLabel`: `boolean` - Indicates if the label should be created in the DOM. (default: false)
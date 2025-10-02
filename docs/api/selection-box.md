---
component: 'selection-box'
type: 'api-documentation'
description: 'API documentation for the selection-box component including components, interfaces, and types.'
---

# Selection Box API Documentation

## Components and Directives

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

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
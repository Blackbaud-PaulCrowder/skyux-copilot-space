---
component: 'input-box'
type: 'api-documentation'
description: 'API documentation for the input-box component including components, interfaces, and types.'
---

# Input Box API Documentation

## Components and Directives

#### FormsInputBoxBasicExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

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
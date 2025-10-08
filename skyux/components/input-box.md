# Design

                   Skip to Main Content

 Input box
=========

Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-1.9ca7d4e41274caab88eb7dc65dc77191.png)

Do use input boxes to style data entry elements.

Use input boxes when forms include native HTML elements for text and selection, such as `<input>`, `<select>`, and `<textarea>`. To determine whether to use the HTML `<select>` element or a SKY UX component, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-2.e36a2aa5fa708257b8f148f4a0f24924.png)

Do use input boxes to style HTML elements.

Use input boxes when forms include SKY UX components, such as [country fields](/skyux/components/country-field.md), [datepickers](/skyux/components/datepicker.md), [lookup fields](/skyux/components/lookup.md), [phone fields](/skyux/components/phone-field.md), and [timepickers](/skyux/components/timepicker.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-3.09f692aebca6c7bbd71fa82f334eed3a.png)

Do use input boxes to style SKY UX components.

 Anatomy
--------

1

Label

2

Input field

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-anatomy.54376094501941eac71074c7adc57b24.png)

 Options
--------

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-required.a56e43319fbbde7a3858c20d556886e0.png)

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-help-button.361ba22cebcd930dd1d8baebdeb4bada.png)

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-hint-text.236b96597d3f69586ab8c35caf98734e.png)

Do use hint text to explain how to enter data.

### Character count

When users are likely to exceed a character limit, use a [character count](/skyux/components/character-count.md) indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-count.6742159929f2689848d03872f8016c22.png)

Do use character count indicators on input fields when users may realistically exceed character limits.

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the form input:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-stacked.170f20ef8ed9b3d088316694a870cda1.png)

### Suggested text

To provide suggested text that helps users with data entry on common fields, you can use the HTML `autocomplete` attribute. Place this attribute on `input`, `textarea`, and `select` elements instead of using the [SKY UX autocomplete component](/skyux/components/autocomplete.md).

Browsers provide suggested text based on previous entries, so `autocomplete` is most helpful for personal information, such as names and addresses, that users enter in multiple places. Don't use `autocomplete` when browsers are unlikely to provide useful suggested text, such as for fields that request information about other users.

 Behavior and states
--------------------

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the [error-handling guidelines](/skyux/design/guidelines/error-handling.md).

 Content
--------

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-1.ca49c946672ebf8f31aac988903a2f2b.png)

Don't use full sentences or questions for input labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-2.483192c1386905976861756a7e4923d3.png)

Do use succinct input labels.

 Layout
-------

Input boxes are most common inside [modals](/skyux/components/modal.md) and follow [form design guidelines](/skyux/design/guidelines/form-design.md). For two-column or three-column layouts, use fluid grid's small gutters [spacing option](/skyux/design/styles/spacing.md) to apply vertical and horizontal padding evenly.

 Related information
--------------------

### Components

*   [Character count](/skyux/components/character-count.md)
*   [Country field](/skyux/components/country-field.md)
*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Phone field](/skyux/components/phone-field.md)
*   [Timepicker](/skyux/components/timepicker.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Spacing](/skyux/design/styles/spacing.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/input-box/input-box.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 Basic usage
------------

Input boxes usually consist of a text label and a form element, such as `input`, `select`, or `textarea`. The input box component handles the majority of use cases by detecting the form element inside it and rendering the the rest of the component based on its inputs. For instance, specifying `labelText` renders a `label` element and associates it with the form element by assigning a unique ID to the form element's `id` attribute and the `label` element's `for` attribute.

Other features of input box include:

*   Adding a [SKY UX character count](/skyux/components/character-count.md) component with the appropriate validator.
*   Adding a [SKY UX help inline](/skyux/components/help-inline.md) button that opens a [SKY UX popover](/skyux/components/popover.md) when clicked.
*   Displaying a red asterisk (\*) next to the label of required fields based on the input's `ngModel`   `required` property or `FormControl`   [Required](https://angular.io/api/forms/RequiredValidator) validator.
*   Displaying errors for well-known validators, including the built-in Angular [Max length](https://angular.io/api/forms/MaxLengthValidator), [Min length](https://angular.io/api/forms/MinLengthValidator), and [Required](https://angular.io/api/forms/RequiredValidator) validators; built-in SKY UX [Email](/skyux/components/email-validation.md) and [URL](/skyux/components/email-validation.md) validators; and the validators added by the [Datepicker](/skyux/components/datepicker.md) , [Phone field](/skyux/components/phone-field.md), and [Timepicker](/skyux/components/timepicker.md) components and directives. These errors render inside an [ARIA live](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) region and are associated with the input element using `aria-errormessage` for accessibility.
*   Adding the appropriate [vertical spacing CSS class](/skyux/design/styles/spacing%23vertical-spacing.md) for displaying an input box above another input box.

 Advanced usage
---------------

For more complex scenarios, each component can be specified individually inside the `sky-input-box` element, and the input box component will place it in the correct location.

*   To use a form element other than an `input`, `select`, or `textarea` element, or to have full control over the input element, include the `sky-form-control` class on the element. You will be responsible for displaying error messages, adding a `label` element and associating it to the input, etc.
*   To specify your own `label` element, or to use an element other than `label`, include the `sky-control-label` class on the element.
*   To display a `sky-help-inline` component with your own click handler, or to use another component to display inline help, include the `sky-control-help` class on the element.
*   To display custom validation error messages under the input, include a `sky-form-error` element. Use `@if` to determine whether to display the validation message based on the input value. These error messages render in the ARIA live region after any errors are detected by input box.

 SkyInputBoxModule
------------------

Type: Module

`import { SkyInputBoxModule } from '@skyux/forms';`

 SkyInputBoxComponent
---------------------

Type: Component

Selector: `sky-input-box`

A wrapper component that provides styling and accessibility to form elements.

### Inputs

#### `characterLimit: number | undefined`

The maximum number of characters allowed in the input. A [SKY UX character count](/skyux/components/character-count.md) will be placed on the input element with the appropriate validator.

#### `disabled: boolean | undefined`

Whether to visually highlight the input box as disabled. To disable the input box's input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled` property. If the input element is mapped to an Angular form control (e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically; if the input element is not associated with an Angular form control, the `disabled` property on the input box must be set to `true` to visually indicate the disabled state on the input box.

Default: `false`

#### `hasErrors: boolean | undefined`

Whether to visually highlight the input box in an error state. If not specified, the input box displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error.

Default: `undefined`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the input box label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the input box label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelText: string | undefined`

The text to display as the input's label and in known validation error messages. The label will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX component included in the input box.

#### `stacked: BooleanInput`

Whether the input box is stacked on another input box. When specified, the appropriate vertical spacing is automatically added to the input box.

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

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

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

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

 SkyInputBoxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyInputBoxHarness](/skyux/components/input-box?docs-active-tab=design#class_sky-input-box-harness.md) instances.

    interface SkyInputBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                   Skip to Main Content

 Input box
=========

Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-1.9ca7d4e41274caab88eb7dc65dc77191.png)

Do use input boxes to style data entry elements.

Use input boxes when forms include native HTML elements for text and selection, such as `<input>`, `<select>`, and `<textarea>`. To determine whether to use the HTML `<select>` element or a SKY UX component, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-2.e36a2aa5fa708257b8f148f4a0f24924.png)

Do use input boxes to style HTML elements.

Use input boxes when forms include SKY UX components, such as [country fields](/skyux/components/country-field.md), [datepickers](/skyux/components/datepicker.md), [lookup fields](/skyux/components/lookup.md), [phone fields](/skyux/components/phone-field.md), and [timepickers](/skyux/components/timepicker.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-3.09f692aebca6c7bbd71fa82f334eed3a.png)

Do use input boxes to style SKY UX components.

 Anatomy
--------

1

Label

2

Input field

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-anatomy.54376094501941eac71074c7adc57b24.png)

 Options
--------

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-required.a56e43319fbbde7a3858c20d556886e0.png)

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-help-button.361ba22cebcd930dd1d8baebdeb4bada.png)

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-hint-text.236b96597d3f69586ab8c35caf98734e.png)

Do use hint text to explain how to enter data.

### Character count

When users are likely to exceed a character limit, use a [character count](/skyux/components/character-count.md) indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-count.6742159929f2689848d03872f8016c22.png)

Do use character count indicators on input fields when users may realistically exceed character limits.

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the form input:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-stacked.170f20ef8ed9b3d088316694a870cda1.png)

### Suggested text

To provide suggested text that helps users with data entry on common fields, you can use the HTML `autocomplete` attribute. Place this attribute on `input`, `textarea`, and `select` elements instead of using the [SKY UX autocomplete component](/skyux/components/autocomplete.md).

Browsers provide suggested text based on previous entries, so `autocomplete` is most helpful for personal information, such as names and addresses, that users enter in multiple places. Don't use `autocomplete` when browsers are unlikely to provide useful suggested text, such as for fields that request information about other users.

 Behavior and states
--------------------

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the [error-handling guidelines](/skyux/design/guidelines/error-handling.md).

 Content
--------

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-1.ca49c946672ebf8f31aac988903a2f2b.png)

Don't use full sentences or questions for input labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-2.483192c1386905976861756a7e4923d3.png)

Do use succinct input labels.

 Layout
-------

Input boxes are most common inside [modals](/skyux/components/modal.md) and follow [form design guidelines](/skyux/design/guidelines/form-design.md). For two-column or three-column layouts, use fluid grid's small gutters [spacing option](/skyux/design/styles/spacing.md) to apply vertical and horizontal padding evenly.

 Related information
--------------------

### Components

*   [Character count](/skyux/components/character-count.md)
*   [Country field](/skyux/components/country-field.md)
*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Phone field](/skyux/components/phone-field.md)
*   [Timepicker](/skyux/components/timepicker.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Spacing](/skyux/design/styles/spacing.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/input-box/input-box.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 Basic usage
------------

Input boxes usually consist of a text label and a form element, such as `input`, `select`, or `textarea`. The input box component handles the majority of use cases by detecting the form element inside it and rendering the the rest of the component based on its inputs. For instance, specifying `labelText` renders a `label` element and associates it with the form element by assigning a unique ID to the form element's `id` attribute and the `label` element's `for` attribute.

Other features of input box include:

*   Adding a [SKY UX character count](/skyux/components/character-count.md) component with the appropriate validator.
*   Adding a [SKY UX help inline](/skyux/components/help-inline.md) button that opens a [SKY UX popover](/skyux/components/popover.md) when clicked.
*   Displaying a red asterisk (\*) next to the label of required fields based on the input's `ngModel`   `required` property or `FormControl`   [Required](https://angular.io/api/forms/RequiredValidator) validator.
*   Displaying errors for well-known validators, including the built-in Angular [Max length](https://angular.io/api/forms/MaxLengthValidator), [Min length](https://angular.io/api/forms/MinLengthValidator), and [Required](https://angular.io/api/forms/RequiredValidator) validators; built-in SKY UX [Email](/skyux/components/email-validation.md) and [URL](/skyux/components/email-validation.md) validators; and the validators added by the [Datepicker](/skyux/components/datepicker.md) , [Phone field](/skyux/components/phone-field.md), and [Timepicker](/skyux/components/timepicker.md) components and directives. These errors render inside an [ARIA live](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) region and are associated with the input element using `aria-errormessage` for accessibility.
*   Adding the appropriate [vertical spacing CSS class](/skyux/design/styles/spacing%23vertical-spacing.md) for displaying an input box above another input box.

 Advanced usage
---------------

For more complex scenarios, each component can be specified individually inside the `sky-input-box` element, and the input box component will place it in the correct location.

*   To use a form element other than an `input`, `select`, or `textarea` element, or to have full control over the input element, include the `sky-form-control` class on the element. You will be responsible for displaying error messages, adding a `label` element and associating it to the input, etc.
*   To specify your own `label` element, or to use an element other than `label`, include the `sky-control-label` class on the element.
*   To display a `sky-help-inline` component with your own click handler, or to use another component to display inline help, include the `sky-control-help` class on the element.
*   To display custom validation error messages under the input, include a `sky-form-error` element. Use `@if` to determine whether to display the validation message based on the input value. These error messages render in the ARIA live region after any errors are detected by input box.

 SkyInputBoxModule
------------------

Type: Module

`import { SkyInputBoxModule } from '@skyux/forms';`

 SkyInputBoxComponent
---------------------

Type: Component

Selector: `sky-input-box`

A wrapper component that provides styling and accessibility to form elements.

### Inputs

#### `characterLimit: number | undefined`

The maximum number of characters allowed in the input. A [SKY UX character count](/skyux/components/character-count.md) will be placed on the input element with the appropriate validator.

#### `disabled: boolean | undefined`

Whether to visually highlight the input box as disabled. To disable the input box's input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled` property. If the input element is mapped to an Angular form control (e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically; if the input element is not associated with an Angular form control, the `disabled` property on the input box must be set to `true` to visually indicate the disabled state on the input box.

Default: `false`

#### `hasErrors: boolean | undefined`

Whether to visually highlight the input box in an error state. If not specified, the input box displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error.

Default: `undefined`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the input box label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the input box label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelText: string | undefined`

The text to display as the input's label and in known validation error messages. The label will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX component included in the input box.

#### `stacked: BooleanInput`

Whether the input box is stacked on another input box. When specified, the appropriate vertical spacing is automatically added to the input box.

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

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

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

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

 SkyInputBoxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyInputBoxHarness](/skyux/components/input-box?docs-active-tab=development#class_sky-input-box-harness.md) instances.

    interface SkyInputBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                        Skip to Main Content

 Input box
=========

Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.Usage
------

### Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-1.9ca7d4e41274caab88eb7dc65dc77191.png)

Do use input boxes to style data entry elements.

Use input boxes when forms include native HTML elements for text and selection, such as `<input>`, `<select>`, and `<textarea>`. To determine whether to use the HTML `<select>` element or a SKY UX component, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-2.e36a2aa5fa708257b8f148f4a0f24924.png)

Do use input boxes to style HTML elements.

Use input boxes when forms include SKY UX components, such as [country fields](/skyux/components/country-field.md), [datepickers](/skyux/components/datepicker.md), [lookup fields](/skyux/components/lookup.md), [phone fields](/skyux/components/phone-field.md), and [timepickers](/skyux/components/timepicker.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-3.09f692aebca6c7bbd71fa82f334eed3a.png)

Do use input boxes to style SKY UX components.

 Anatomy
--------

1

Label

2

Input field

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-anatomy.54376094501941eac71074c7adc57b24.png)

 Options
--------

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-required.a56e43319fbbde7a3858c20d556886e0.png)

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-help-button.361ba22cebcd930dd1d8baebdeb4bada.png)

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-hint-text.236b96597d3f69586ab8c35caf98734e.png)

Do use hint text to explain how to enter data.

### Character count

When users are likely to exceed a character limit, use a [character count](/skyux/components/character-count.md) indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-count.6742159929f2689848d03872f8016c22.png)

Do use character count indicators on input fields when users may realistically exceed character limits.

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the form input:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-stacked.170f20ef8ed9b3d088316694a870cda1.png)

### Suggested text

To provide suggested text that helps users with data entry on common fields, you can use the HTML `autocomplete` attribute. Place this attribute on `input`, `textarea`, and `select` elements instead of using the [SKY UX autocomplete component](/skyux/components/autocomplete.md).

Browsers provide suggested text based on previous entries, so `autocomplete` is most helpful for personal information, such as names and addresses, that users enter in multiple places. Don't use `autocomplete` when browsers are unlikely to provide useful suggested text, such as for fields that request information about other users.

 Behavior and states
--------------------

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the [error-handling guidelines](/skyux/design/guidelines/error-handling.md).

 Content
--------

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-1.ca49c946672ebf8f31aac988903a2f2b.png)

Don't use full sentences or questions for input labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-2.483192c1386905976861756a7e4923d3.png)

Do use succinct input labels.

 Layout
-------

Input boxes are most common inside [modals](/skyux/components/modal.md) and follow [form design guidelines](/skyux/design/guidelines/form-design.md). For two-column or three-column layouts, use fluid grid's small gutters [spacing option](/skyux/design/styles/spacing.md) to apply vertical and horizontal padding evenly.

 Related information
--------------------

### Components

*   [Character count](/skyux/components/character-count.md)
*   [Country field](/skyux/components/country-field.md)
*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Phone field](/skyux/components/phone-field.md)
*   [Timepicker](/skyux/components/timepicker.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Spacing](/skyux/design/styles/spacing.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/input-box/input-box.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 Basic usage
------------

Input boxes usually consist of a text label and a form element, such as `input`, `select`, or `textarea`. The input box component handles the majority of use cases by detecting the form element inside it and rendering the the rest of the component based on its inputs. For instance, specifying `labelText` renders a `label` element and associates it with the form element by assigning a unique ID to the form element's `id` attribute and the `label` element's `for` attribute.

Other features of input box include:

*   Adding a [SKY UX character count](/skyux/components/character-count.md) component with the appropriate validator.
*   Adding a [SKY UX help inline](/skyux/components/help-inline.md) button that opens a [SKY UX popover](/skyux/components/popover.md) when clicked.
*   Displaying a red asterisk (\*) next to the label of required fields based on the input's `ngModel`   `required` property or `FormControl`   [Required](https://angular.io/api/forms/RequiredValidator) validator.
*   Displaying errors for well-known validators, including the built-in Angular [Max length](https://angular.io/api/forms/MaxLengthValidator), [Min length](https://angular.io/api/forms/MinLengthValidator), and [Required](https://angular.io/api/forms/RequiredValidator) validators; built-in SKY UX [Email](/skyux/components/email-validation.md) and [URL](/skyux/components/email-validation.md) validators; and the validators added by the [Datepicker](/skyux/components/datepicker.md) , [Phone field](/skyux/components/phone-field.md), and [Timepicker](/skyux/components/timepicker.md) components and directives. These errors render inside an [ARIA live](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) region and are associated with the input element using `aria-errormessage` for accessibility.
*   Adding the appropriate [vertical spacing CSS class](/skyux/design/styles/spacing%23vertical-spacing.md) for displaying an input box above another input box.

 Advanced usage
---------------

For more complex scenarios, each component can be specified individually inside the `sky-input-box` element, and the input box component will place it in the correct location.

*   To use a form element other than an `input`, `select`, or `textarea` element, or to have full control over the input element, include the `sky-form-control` class on the element. You will be responsible for displaying error messages, adding a `label` element and associating it to the input, etc.
*   To specify your own `label` element, or to use an element other than `label`, include the `sky-control-label` class on the element.
*   To display a `sky-help-inline` component with your own click handler, or to use another component to display inline help, include the `sky-control-help` class on the element.
*   To display custom validation error messages under the input, include a `sky-form-error` element. Use `@if` to determine whether to display the validation message based on the input value. These error messages render in the ARIA live region after any errors are detected by input box.

 SkyInputBoxModule
------------------

Type: Module

`import { SkyInputBoxModule } from '@skyux/forms';`

 SkyInputBoxComponent
---------------------

Type: Component

Selector: `sky-input-box`

A wrapper component that provides styling and accessibility to form elements.

### Inputs

#### `characterLimit: number | undefined`

The maximum number of characters allowed in the input. A [SKY UX character count](/skyux/components/character-count.md) will be placed on the input element with the appropriate validator.

#### `disabled: boolean | undefined`

Whether to visually highlight the input box as disabled. To disable the input box's input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled` property. If the input element is mapped to an Angular form control (e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically; if the input element is not associated with an Angular form control, the `disabled` property on the input box must be set to `true` to visually indicate the disabled state on the input box.

Default: `false`

#### `hasErrors: boolean | undefined`

Whether to visually highlight the input box in an error state. If not specified, the input box displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error.

Default: `undefined`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the input box label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the input box label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelText: string | undefined`

The text to display as the input's label and in known validation error messages. The label will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX component included in the input box.

#### `stacked: BooleanInput`

Whether the input box is stacked on another input box. When specified, the appropriate vertical spacing is automatically added to the input box.

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

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

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

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

 SkyInputBoxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyInputBoxHarness](/skyux/components/input-box?docs-active-tab=examples#class_sky-input-box-harness.md) instances.

    interface SkyInputBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Input box

Edit in StackBlitz

New member form
---------------

First nameShow help content for

Last name

Bio 0/250 0 characters out of 250

A brief description of the member's background, such as hometown, school, hobbies, etc.

Email addressShow help content for

Date of birth

Use the format MM/DD/YYYY.

Favorite color

NoneRedOrangeYellowGreenBluePurpleInvalid Color

Show code

Copy

    <div class="sky-padding-even-lg">
      <form [formGroup]="formGroup">
        <sky-fluid-grid gutterSize="small" [disableMargin]="false">
          <sky-row>
            <sky-column [screenSmall]="12">
              <h2>New member form</h2>
            </sky-column>
          </sky-row>
          <sky-row>
            <sky-column [screenSmall]="12" [screenMedium]="6">
              <sky-input-box
                data-sky-id="input-box-first-name"
                helpKey="first-name-help"
                labelText="First name"
                stacked="true"
              >
                <input formControlName="firstName" spellcheck="false" type="text" />
              </sky-input-box>
            </sky-column>
            <sky-column [screenSmall]="12" [screenMedium]="6">
              <sky-input-box
                data-sky-id="input-box-last-name"
                labelText="Last name"
                stacked="true"
              >
                <input
                  class="last-name-input-box"
                  formControlName="lastName"
                  spellcheck="false"
                  type="text"
                />
              </sky-input-box>
            </sky-column>
          </sky-row>
          <sky-row>
            <sky-column [screenSmall]="12">
              <sky-input-box
                characterLimit="250"
                data-sky-id="input-box-bio"
                hintText="A brief description of the member's background, such as hometown, school, hobbies, etc."
                labelText="Bio"
                stacked="true"
              >
                <textarea formControlName="bio"></textarea>
              </sky-input-box>
            </sky-column>
          </sky-row>
          <sky-row>
            <sky-column [screenSmall]="12" [screenMedium]="6">
              <sky-input-box
                data-sky-id="input-box-email"
                labelText="Email address"
                stacked="true"
                helpPopoverContent="We do not share this information with any third parties."
                helpPopoverTitle="Privacy notice"
              >
                <input formControlName="email" type="text" />
              </sky-input-box>
            </sky-column>
            <sky-column [screenSmall]="12" [screenMedium]="6">
              <sky-input-box labelText="Date of birth" stacked="true">
                <sky-datepicker>
                  <input formControlName="dob" skyDatepickerInput />
                </sky-datepicker>
              </sky-input-box>
            </sky-column>
          </sky-row>
          <sky-row>
            <sky-column [screenSmall]="12">
              <sky-input-box
                data-sky-id="input-box-favorite-color"
                labelText="Favorite color"
              >
                <select
                  class="input-box-favorite-color-select"
                  formControlName="favoriteColor"
                >
                  <option value="none">None</option>
                  <option value="red">Red</option>
                  <option value="orange">Orange</option>
                  <option value="yellow">Yellow</option>
                  <option value="green">Green</option>
                  <option value="blue">Blue</option>
                  <option value="purple">Purple</option>
                  <option value="invalid">Invalid Color</option>
                </select>
                <!-- Custom form error not handled by input box. -->
                @if (favoriteColor.errors?.['invalid']) {
                  <sky-form-error
                    errorName="invalid"
                    errorText="Invalid Color is not a color"
                  />
                }
              </sky-input-box>
            </sky-column>
          </sky-row>
        </sky-fluid-grid>
      </form>
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    
    import { FormsInputBoxBasicExampleComponent } from './example.component';
    
    describe('Basic input box example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        fixture: ComponentFixture<FormsInputBoxBasicExampleComponent>;
        inputBoxHarness: SkyInputBoxHarness;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(FormsInputBoxBasicExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        const inputBoxHarness = await loader.getHarness(
          SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        return { fixture, inputBoxHarness, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            NoopAnimationsModule,
            FormsInputBoxBasicExampleComponent,
            SkyHelpTestingModule,
          ],
        });
      });
    
      describe('first name field', () => {
        it('should have the expected label text and stacked values', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-first-name',
          });
    
          fixture.detectChanges();
    
          await expectAsync(inputBoxHarness.getLabelText()).toBeResolvedTo(
            'First name',
          );
    
          await expectAsync(inputBoxHarness.getStacked()).toBeResolvedTo(true);
        });
    
        it('should have the correct help key', async () => {
          const { fixture, inputBoxHarness, helpController } = await setupTest({
            dataSkyId: 'input-box-first-name',
          });
    
          fixture.detectChanges();
    
          await inputBoxHarness.clickHelpInline();
    
          helpController.expectCurrentHelpKey('first-name-help');
        });
      });
    
      describe('last name field', () => {
        it('should have last name required', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-last-name',
          });
    
          fixture.detectChanges();
    
          const inputEl = await inputBoxHarness.querySelector(
            '.last-name-input-box',
          );
    
          await inputEl.setInputValue('');
          await inputEl.blur();
    
          await expectAsync(inputBoxHarness.hasRequiredError()).toBeResolvedTo(
            true,
          );
        });
      });
    
      describe('bio field', () => {
        it('should have a character limit of 250', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-bio',
          });
    
          fixture.detectChanges();
    
          const characterCounter = await inputBoxHarness.getCharacterCounter();
    
          await expectAsync(characterCounter.getCharacterCount()).toBeResolvedTo(0);
          await expectAsync(
            characterCounter.getCharacterCountLimit(),
          ).toBeResolvedTo(250);
        });
    
        it('should show hint text', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-bio',
          });
    
          fixture.detectChanges();
    
          await expectAsync(inputBoxHarness.getHintText()).toBeResolvedTo(
            `A brief description of the member's background, such as hometown, school, hobbies, etc.`,
          );
        });
      });
    
      describe('email field', () => {
        it('should show a help popover with the expected text', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-email',
          });
    
          fixture.detectChanges();
    
          await inputBoxHarness.clickHelpInline();
    
          await expectAsync(inputBoxHarness.getHelpPopoverTitle()).toBeResolvedTo(
            'Privacy notice',
          );
    
          await expectAsync(inputBoxHarness.getHelpPopoverContent()).toBeResolvedTo(
            `We do not share this information with any third parties.`,
          );
        });
      });
    
      describe('favorite color field', () => {
        it('should not allow invalid color to be selected', async () => {
          const { fixture, inputBoxHarness } = await setupTest({
            dataSkyId: 'input-box-favorite-color',
          });
    
          fixture.detectChanges();
    
          const selectEl = await inputBoxHarness.querySelector('select');
    
          // Select the "invalid" option.
          await selectEl.selectOptions(7);
    
          await expectAsync(
            inputBoxHarness.hasCustomFormError('invalid'),
          ).toBeResolvedTo(true);
        });
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
      Validators,
    } from '@angular/forms';
    import { SkyDatepickerModule } from '@skyux/datetime';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyStatusIndicatorModule } from '@skyux/indicators';
    import { SkyFluidGridModule } from '@skyux/layout';
    import { SkyValidators } from '@skyux/validation';
    
    function validateColor(control: AbstractControl): ValidationErrors | null {
      if (control.value === 'invalid') {
        return { invalid: true };
      }
    
      return null;
    }
    
    /**
     * @title Input box
     */
    @Component({
      selector: 'app-forms-input-box-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyDatepickerModule,
        SkyFluidGridModule,
        SkyInputBoxModule,
        SkyStatusIndicatorModule,
      ],
    })
    export class FormsInputBoxBasicExampleComponent {
      protected favoriteColor = new FormControl('none', {
        validators: [validateColor],
      });
    
      protected formGroup = inject(FormBuilder).group({
        firstName: new FormControl(''),
        lastName: new FormControl('', Validators.required),
        bio: new FormControl(''),
        email: new FormControl('', [Validators.required, SkyValidators.email]),
        dob: new FormControl('', Validators.required),
        favoriteColor: this.favoriteColor,
      });
    }
### Input box with custom errors

Edit in StackBlitz

Favorite color

NoneRedOrangeYellowGreenBluePurpleInvalid Color

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-input-box
        data-sky-id="input-box-favorite-color"
        labelText="Favorite color"
      >
        <select formControlName="favoriteColor">
          <option value="none">None</option>
          <option value="red">Red</option>
          <option value="orange">Orange</option>
          <option value="yellow">Yellow</option>
          <option value="green">Green</option>
          <option value="blue">Blue</option>
          <option value="purple">Purple</option>
          <option value="invalid">Invalid Color</option>
        </select>
        @if (favoriteColor.errors?.['invalid']) {
          <sky-form-error
            errorName="invalid"
            errorText="The color Invalid Color is not a color"
          />
        }
      </sky-input-box>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    
    import { FormsInputBoxWithCustomFormErrorsExampleComponent } from './example.component';
    
    describe('Input box with custom form errors example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        fixture: ComponentFixture<FormsInputBoxWithCustomFormErrorsExampleComponent>;
        inputBoxHarness: SkyInputBoxHarness;
      }> {
        const fixture = TestBed.createComponent(
          FormsInputBoxWithCustomFormErrorsExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const inputBoxHarness = await loader.getHarness(
          SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        return { fixture, inputBoxHarness };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [FormsInputBoxWithCustomFormErrorsExampleComponent],
        });
      });
    
      it('should not allow invalid color to be selected', async () => {
        const { fixture, inputBoxHarness } = await setupTest({
          dataSkyId: 'input-box-favorite-color',
        });
    
        fixture.detectChanges();
    
        const selectEl = await inputBoxHarness.querySelector('select');
    
        // Select the "invalid" option.
        await selectEl.selectOptions(7);
    
        await expectAsync(
          inputBoxHarness.hasCustomFormError('invalid'),
        ).toBeResolvedTo(true);
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    
    function validateColor(control: AbstractControl): ValidationErrors | null {
      if (control.value === 'invalid') {
        return { invalid: true };
      }
    
      return null;
    }
    
    /**
     * @title Input box with custom errors
     */
    @Component({
      selector: 'app-forms-input-box-basic-example',
      templateUrl: './example.component.html',
      imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
    })
    export class FormsInputBoxWithCustomFormErrorsExampleComponent {
      protected favoriteColor = new FormControl('none', {
        validators: [validateColor],
      });
    
      protected formGroup = inject(FormBuilder).group({
        favoriteColor: this.favoriteColor,
      });
    }
### Country field with basic setup

Edit in StackBlitz

CountryShow help content for

If you have multiple countries, choose your primary country.

Show code

Copy

    <form [formGroup]="countryForm">
      <sky-input-box
        data-sky-id="country-field"
        hintText="If you have multiple countries, choose your primary country."
        labelText="Country"
        [helpPopoverContent]="helpPopoverContent"
      >
        <sky-country-field formControlName="country" />
        @if (countryControl.errors?.['invalidCountry']) {
          <sky-form-error
            errorName="invalidCountry"
            errorText="This country is no longer available for the date you selected."
          />
        }
      </sky-input-box>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    import { SkyCountryFieldHarness } from '@skyux/lookup/testing';
    
    import { LookupCountryFieldBasicExampleComponent } from './example.component';
    
    describe('Basic country field example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        harness: SkyCountryFieldHarness;
        fixture: ComponentFixture<LookupCountryFieldBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          LookupCountryFieldBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await (
          await loader.getHarness(
            SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
          )
        ).queryHarness(SkyCountryFieldHarness);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [LookupCountryFieldBasicExampleComponent],
        });
      });
    
      it('should set up country field input', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: 'country-field',
        });
    
        await harness.focus();
        await harness.enterText('ger');
    
        const searchResultsText = await harness.getSearchResultsText();
    
        expect(searchResultsText.length).toBe(4);
    
        await harness.clear();
        await harness.enterText('can');
    
        const searchResults = await harness.getSearchResults();
        await expectAsync(searchResults[1].getText()).toBeResolvedTo('Canada');
    
        await searchResults[1].select();
        const value = fixture.componentInstance.countryForm.get('country')?.value;
        expect(value?.name).toBe('Canada');
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
      Validators,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyCountryFieldCountry, SkyCountryFieldModule } from '@skyux/lookup';
    
    interface DemoForm {
      country: FormControl<SkyCountryFieldCountry | undefined>;
    }
    
    function validateCountry(
      control: AbstractControl<SkyCountryFieldCountry | undefined>,
    ): ValidationErrors | null {
      return control.value?.name === 'Mexico' ? { invalidCountry: true } : null;
    }
    
    /**
     * @title Country field with basic setup
     */
    @Component({
      selector: 'app-lookup-country-field-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyCountryFieldModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupCountryFieldBasicExampleComponent {
      protected countryControl: FormControl<SkyCountryFieldCountry | undefined>;
      public countryForm: FormGroup<DemoForm>;
    
      protected helpPopoverContent =
        'We use the country to validate your passport within 10 business days. You can update it at any time.';
    
      #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.countryControl = new FormControl(
          {
            name: 'Australia',
            iso2: 'au',
          },
          {
            nonNullable: true,
            validators: [validateCountry, Validators.required],
          },
        );
    
        this.countryForm = this.#formBuilder.group({
          country: this.countryControl,
        });
      }
    }
### Datepicker with basic setup

Edit in StackBlitz

Start dateShow help content for

Must be before your 1 year anniversary. Use the format MM/DD/YYYY.

Selected date: `"2001-10-12T04:00:00.000Z"`

Show code

Copy

    <div class="sky-padding-even-lg">
      <form [formGroup]="formGroup">
        <sky-input-box
          data-sky-id="datepicker-example"
          labelText="Start date"
          [helpPopoverContent]="helpPopoverContent"
          [hintText]="hintText"
        >
          <sky-datepicker>
            <input formControlName="startDate" skyDatepickerInput type="text" />
          </sky-datepicker>
          @if (startDate.errors?.['invalidWeekend']) {
            <sky-form-error
              errorName="invalidWeekend"
              errorText="Start date must not be on a weekend."
            />
          }
        </sky-input-box>
      </form>
    
      <p>
        Selected date: <code>{{ startDate.value | json }}</code>
      </p>
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyDatepickerHarness } from '@skyux/datetime/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    
    import { DatetimeDatepickerBasicExampleComponent } from './example.component';
    
    describe('Basic datepicker example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        inputHarness: SkyInputBoxHarness;
        datepickerHarness: SkyDatepickerHarness;
        fixture: ComponentFixture<DatetimeDatepickerBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          DatetimeDatepickerBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const inputHarness = await loader.getHarness(
          SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
        );
        const datepickerHarness =
          await inputHarness.queryHarness(SkyDatepickerHarness);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { inputHarness, datepickerHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [DatetimeDatepickerBasicExampleComponent, NoopAnimationsModule],
        });
      });
    
      it('should have initial setup values', async () => {
        const { inputHarness, datepickerHarness, fixture } = await setupTest({
          dataSkyId: 'datepicker-example',
        });
    
        await expectAsync(inputHarness.getHintText()).toBeResolvedTo(
          'Must be before your 1 year anniversary. Use the format MM/DD/YYYY.',
        );
    
        await datepickerHarness.clickCalendarButton();
    
        await inputHarness.clickHelpInline();
        await expectAsync(inputHarness.getHelpPopoverContent()).toBeResolvedTo(
          fixture.componentInstance.helpPopoverContent,
        );
    
        await datepickerHarness.clickCalendarButton();
        const calendarHarness = await datepickerHarness.getDatepickerCalendar();
        await expectAsync(calendarHarness.getSelectedValue()).toBeResolvedTo(
          'Friday, October 12th 2001',
        );
      });
    
      it('should throw an error if selecting a weekend', async () => {
        const { inputHarness, datepickerHarness } = await setupTest({
          dataSkyId: 'datepicker-example',
        });
    
        await datepickerHarness.clickCalendarButton();
        const calendarHarness = await datepickerHarness.getDatepickerCalendar();
    
        await calendarHarness.clickDate('Saturday, October 13th 2001');
        await expectAsync(
          inputHarness.hasCustomFormError('invalidWeekend'),
        ).toBeResolvedTo(true);
      });
    });

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
      Validators,
    } from '@angular/forms';
    import { SkyDatepickerModule } from '@skyux/datetime';
    import { SkyInputBoxModule } from '@skyux/forms';
    
    interface DemoForm {
      startDate: FormControl<Date | string | null>;
    }
    
    function validateDate(
      control: AbstractControl<Date | string | null>,
    ): ValidationErrors | null {
      const date = control.value;
      if (date instanceof Date) {
        const day = date?.getDay();
    
        return day !== undefined && (day === 0 || day === 6)
          ? {
              invalidWeekend: true,
            }
          : null;
      }
      return null;
    }
    
    /**
     * @title Datepicker with basic setup
     */
    @Component({
      selector: 'app-datetime-datepicker-basic-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyDatepickerModule,
        SkyInputBoxModule,
      ],
    })
    export class DatetimeDatepickerBasicExampleComponent {
      protected formGroup: FormGroup<DemoForm>;
      protected startDate: FormControl<Date | string | null>;
      protected hintText = 'Must be before your 1 year anniversary.';
    
      public helpPopoverContent =
        'If you need help with registration, choose a date at least 8 business days after you arrive. The process takes up to 7 business days from the start date.';
    
      constructor() {
        this.startDate = new FormControl<Date | string | null>(
          new Date('10/12/2001'),
          {
            validators: [Validators.required, validateDate],
          },
        );
    
        this.formGroup = inject(FormBuilder).group<DemoForm>({
          startDate: this.startDate,
        });
      }
    }
### Lookup in single select mode

Edit in StackBlitz

Favorite nameShow help content for

Choose a name from the list or add a new name.

**Form model:**

{
  "favoriteName": \[
    {
      "name": "Shirley"
    }
  \]
}

Submit

Show code

Copy

    <form
      class="sky-padding-even-md"
      novalidate
      [formGroup]="favoritesForm"
      (ngSubmit)="onSubmit()"
    >
      <sky-input-box
        data-sky-id="favorite-names-field"
        helpPopoverContent="A name can be selected from the list or added as a new name."
        hintText="Choose a name from the list or add a new name."
        labelText="Favorite name"
        stacked
      >
        <sky-lookup
          formControlName="favoriteName"
          idProperty="name"
          [enableShowMore]="true"
          [selectMode]="'single'"
          [showAddButton]="true"
          [showMoreConfig]="showMoreConfig"
          (searchAsync)="searchAsync($event)"
          (addClick)="addClick($event)"
        />
        @if (favoritesForm.controls.favoriteName.errors?.['letterE']) {
          <sky-form-error
            errorName="letterE"
            errorText="Please only choose a name that contain the letter E"
          />
        }
      </sky-input-box>
      <div
        class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
      >
        <strong>Form model:</strong>
        <pre>{{ favoritesForm.value | json }}</pre>
      </div>
      <button class="sky-btn sky-btn-default" type="submit">Submit</button>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    import { SkyLookupHarness } from '@skyux/lookup/testing';
    
    import { of } from 'rxjs';
    
    import { LookupSingleSelectExampleComponent } from './example.component';
    import { DemoService } from './example.service';
    
    describe('Lookup single-select example', () => {
      let mockSvc!: jasmine.SpyObj<DemoService>;
    
      async function setupTest(): Promise<{
        lookupHarness: SkyLookupHarness;
        fixture: ComponentFixture<LookupSingleSelectExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(LookupSingleSelectExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const lookupHarness = await (
          await loader.getHarness(
            SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
          )
        ).queryHarness(SkyLookupHarness);
    
        return { lookupHarness, fixture };
      }
    
      beforeEach(() => {
        // Create a mock search service. In a real-world application, the search
        // service would make a web request which should be avoided in unit tests.
        mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);
    
        TestBed.configureTestingModule({
          imports: [LookupSingleSelectExampleComponent, NoopAnimationsModule],
          providers: [
            {
              provide: DemoService,
              useValue: mockSvc,
            },
          ],
        });
      });
    
      it('should set the expected initial value', async () => {
        const { lookupHarness } = await setupTest();
    
        await expectAsync(lookupHarness.getValue()).toBeResolvedTo('Shirley');
      });
    
      it('should update the form control when a favorite name is selected', async () => {
        const { lookupHarness, fixture } = await setupTest();
    
        mockSvc.search.and.callFake((searchText) =>
          of({
            hasMore: false,
            people:
              searchText === 'b'
                ? [
                    {
                      name: 'Bernard',
                    },
                  ]
                : [],
            totalCount: 1,
          }),
        );
    
        await lookupHarness.enterText('b');
        await lookupHarness.selectSearchResult({
          text: 'Bernard',
        });
    
        expect(fixture.componentInstance.favoritesForm.value.favoriteName).toEqual([
          { name: 'Bernard' },
        ]);
      });
    
      it('should respect the selection descriptor', async () => {
        const { lookupHarness } = await setupTest();
    
        mockSvc.search.and.callFake(() =>
          of({
            hasMore: false,
            people: [
              {
                id: '21',
                name: 'Bernard',
              },
            ],
            totalCount: 1,
          }),
        );
    
        await lookupHarness.clickShowMoreButton();
    
        const picker = await lookupHarness.getShowMorePicker();
    
        await expectAsync(picker.getSearchAriaLabel()).toBeResolvedTo(
          'Search names',
        );
        await expectAsync(picker.getSaveButtonAriaLabel()).toBeResolvedTo(
          'Select names',
        );
      });
    });
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, of } from 'rxjs';
    import { delay } from 'rxjs/operators';
    
    import { Person } from './person';
    import { LookupAsyncDemoSearchResults } from './search-results';
    
    const people: Person[] = [
      { name: 'Abed' },
      { name: 'Alex' },
      { name: 'Ben' },
      { name: 'Britta' },
      { name: 'Buzz' },
      { name: 'Craig' },
      { name: 'Elroy' },
      { name: 'Garrett' },
      { name: 'Ian' },
      { name: 'Jeff' },
      { name: 'Leonard' },
      { name: 'Neil' },
      { name: 'Pierce' },
      { name: 'Preston' },
      { name: 'Rachel' },
      { name: 'Shirley' },
      { name: 'Todd' },
      { name: 'Troy' },
      { name: 'Vaughn' },
      { name: 'Vicki' },
    ];
    
    @Injectable({
      providedIn: 'root',
    })
    export class DemoService {
      public search(searchText: string): Observable<LookupAsyncDemoSearchResults> {
        // Simulate a network call with latency. A real-world application might
        // use Angular's HttpClient to create an Observable from a call to a
        // web service.
        searchText = searchText.toUpperCase();
    
        const matchingPeople = people.filter((person) =>
          person.name.toUpperCase().includes(searchText),
        );
    
        return of({
          hasMore: false,
          people: matchingPeople,
          totalCount: matchingPeople.length,
        }).pipe(delay(800));
      }
    
      public addPerson(person: Person): Observable<number> {
        // Simulate adding a person with a network call.
        if (!people.some((item) => item.name === person.name)) {
          people.unshift(person);
        }
    
        return of(1).pipe(delay(800));
      }
    }
Copy

    export interface Person {
      name: string;
    }
Copy

    import { Person } from './person';
    
    export interface LookupAsyncDemoSearchResults {
      hasMore: boolean;
      people: Person[];
      totalCount: number;
    }

Copy

    import { CommonModule } from '@angular/common';
    import { Component, OnInit, inject } from '@angular/core';
    import {
      AbstractControl,
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
      ValidationErrors,
    } from '@angular/forms';
    import { SkyFormErrorModule, SkyInputBoxModule } from '@skyux/forms';
    import { SkyWaitService } from '@skyux/indicators';
    import {
      SkyAutocompleteSearchAsyncArgs,
      SkyLookupAddClickEventArgs,
      SkyLookupModule,
      SkyLookupShowMoreConfig,
    } from '@skyux/lookup';
    
    import { map } from 'rxjs/operators';
    
    import { DemoService } from './example.service';
    import { Person } from './person';
    
    /**
     * @title Lookup in single select mode
     */
    @Component({
      selector: 'app-lookup-single-select-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyFormErrorModule,
        SkyInputBoxModule,
        SkyLookupModule,
      ],
    })
    export class LookupSingleSelectExampleComponent implements OnInit {
      public favoritesForm: FormGroup<{
        favoriteName: FormControl<Person[] | null>;
      }>;
    
      public showMoreConfig: SkyLookupShowMoreConfig = {
        nativePickerConfig: {
          selectionDescriptor: 'names',
        },
      };
    
      readonly #svc = inject(DemoService);
      readonly #waitSvc = inject(SkyWaitService);
    
      constructor() {
        const name = new FormControl<Person[]>([{ name: 'Shirley' }], {
          validators: [
            (control: AbstractControl<Person[] | null>): ValidationErrors => {
              if (
                control.value?.some((person) => /e/i.exec(person.name) === null)
              ) {
                return { letterE: true };
              }
    
              return {};
            },
          ],
        });
    
        this.favoritesForm = inject(FormBuilder).group({
          favoriteName: name,
        });
      }
    
      public ngOnInit(): void {
        // If you need to execute some logic after the lookup values change,
        // subscribe to Angular's built-in value changes observable.
        this.favoritesForm.valueChanges.subscribe((changes) => {
          console.log('Lookup value changes:', changes);
        });
      }
    
      protected onSubmit(): void {
        alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
      }
    
      protected searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
        // In a real-world application the search service might return an Observable
        // created by calling HttpClient.get(). Assigning that Observable to the result
        // allows the lookup component to cancel the web request if it does not complete
        // before the user searches again.
        args.result = this.#svc.search(args.searchText).pipe(
          map((result) => ({
            hasMore: result.hasMore,
            items: result.people,
            totalCount: result.totalCount,
          })),
        );
      }
    
      protected addClick(args: SkyLookupAddClickEventArgs): void {
        const person: Person = {
          name: 'Newman',
        };
    
        this.#waitSvc.blockingWrap(this.#svc.addPerson(person)).subscribe(() => {
          args.itemAdded({
            item: person,
          });
        });
      }
    }
### Phone field with basic setup

Edit in StackBlitz

Phone numberShow help content for

Enter the phone number where you can be reached before 5 p.m., Monday through Friday. Example: (201) 555-0123.

Show code

Copy

    <div class="sky-padding-even-lg">
      <form class="phone-field-example" [formGroup]="phoneForm">
        <sky-input-box
          data-sky-id="my-phone-field"
          helpPopoverTitle="How we use your phone number"
          hintText="Enter the phone number where you can be reached before 5 p.m., Monday through Friday."
          labelText="Phone number"
          [helpPopoverContent]="inlineHelpPopover"
        >
          <sky-phone-field [defaultCountry]="'us'">
            <input formControlName="phoneControl" skyPhoneFieldInput />
          </sky-phone-field>
        </sky-input-box>
      </form>
    </div>
    
    <ng-template #inlineHelpPopover>
      We use this number for calls and text about your student. We won't use it for
      other purposes.
      <br />
      <br />
      For more information, see our <a>privacy policy</a>.
    </ng-template>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    import { SkyPhoneFieldCountry } from '@skyux/phone-field';
    import { SkyPhoneFieldHarness } from '@skyux/phone-field/testing';
    
    import { PhoneFieldBasicExampleComponent } from './example.component';
    
    const COUNTRY_AU: SkyPhoneFieldCountry = {
      name: 'Australia',
      iso2: 'au',
      dialCode: '+61',
    };
    
    const DATA_SKY_ID = 'my-phone-field';
    const VALID_AU_NUMBER = '0212345678';
    const VALID_US_NUMBER = '8675555309';
    
    describe('Basic phone field example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        harness: SkyPhoneFieldHarness;
        fixture: ComponentFixture<PhoneFieldBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(PhoneFieldBasicExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await (
          await loader.getHarness(
            SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
          )
        ).queryHarness(SkyPhoneFieldHarness);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [PhoneFieldBasicExampleComponent, NoopAnimationsModule],
        });
      });
    
      it('should set up phone field input and clear value', async () => {
        const { harness } = await setupTest({
          dataSkyId: DATA_SKY_ID,
        });
    
        // First, set a value on the phoneField.
        const inputHarness = await harness.getControl();
        await inputHarness.focus();
        await inputHarness.setValue(VALID_US_NUMBER);
    
        await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_US_NUMBER);
    
        // Now, clear the value.
        await inputHarness.clear();
        await expectAsync(inputHarness.getValue()).toBeResolvedTo('');
      });
    
      it('should use selected country', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: DATA_SKY_ID,
        });
    
        const inputHarness = await harness.getControl();
        await inputHarness.focus();
        // enter a valid phone number for the default country
        await inputHarness.setValue(VALID_US_NUMBER);
    
        // expect the model to use the proper dial code and format
        await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_US_NUMBER);
        expect(fixture.componentInstance.phoneControl.value).toEqual(
          '(867) 555-5309',
        );
    
        if (COUNTRY_AU.name) {
          // change the country
          await harness.selectCountry(COUNTRY_AU.name);
        }
    
        const countryName: string | null = await harness.getSelectedCountryName();
    
        const countryIos2: string | null = await harness.getSelectedCountryIso2();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        if (COUNTRY_AU.name && countryName) {
          expect(countryName).toBe(COUNTRY_AU.name);
        }
        if (COUNTRY_AU.iso2 && countryIos2) {
          expect(countryIos2).toBe(COUNTRY_AU.iso2);
        }
    
        // enter a valid phone number for the new country
        await inputHarness.setValue(VALID_AU_NUMBER);
    
        // expect the model to use the proper dial code and format
        await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_AU_NUMBER);
        expect(fixture.componentInstance.phoneControl.value).toEqual(
          '+61 2 1234 5678',
        );
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
      Validators,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyPhoneFieldModule } from '@skyux/phone-field';
    
    /**
     * @title Phone field with basic setup
     */
    @Component({
      selector: 'app-phone-field-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyInputBoxModule,
        SkyPhoneFieldModule,
      ],
    })
    export class PhoneFieldBasicExampleComponent {
      public phoneForm: FormGroup;
      public phoneControl: FormControl;
    
      #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.phoneControl = this.#formBuilder.control(undefined, {
          validators: Validators.required,
        });
        this.phoneForm = this.#formBuilder.group({
          phoneControl: this.phoneControl,
        });
      }
    }
### Timepicker with basic setup

Edit in StackBlitz

Start timeShow help content for

Choose a time that allows for late arrivals.

Show code

Copy

    <div class="sky-padding-even-lg">
      <form [formGroup]="formGroup">
        <sky-input-box
          data-sky-id="timepicker-example"
          labelText="Start time"
          [helpPopoverContent]="helpPopoverContent"
          [hintText]="hintText"
        >
          <sky-timepicker #timepicker>
            <input
              formControlName="time"
              timeFormat="hh"
              [skyTimepickerInput]="timepicker"
            />
          </sky-timepicker>
          @if (time.errors?.['invalidMinute']) {
            <sky-form-error
              errorName="invalidMinute"
              errorText="Start time must be a 15-minute increment."
            />
          }
        </sky-input-box>
      </form>
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyTimepickerHarness } from '@skyux/datetime/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    
    import { DatetimeTimepickerBasicExampleComponent } from './example.component';
    
    describe('Basic timepicker example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        inputHarness: SkyInputBoxHarness;
        timepickerHarness: SkyTimepickerHarness;
        fixture: ComponentFixture<DatetimeTimepickerBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          DatetimeTimepickerBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const inputHarness = await loader.getHarness(
          SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
        );
        const timepickerHarness =
          await inputHarness.queryHarness(SkyTimepickerHarness);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { inputHarness, timepickerHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [DatetimeTimepickerBasicExampleComponent, NoopAnimationsModule],
        });
      });
    
      it('should have initial setup values', async () => {
        const { inputHarness, timepickerHarness, fixture } = await setupTest({
          dataSkyId: 'timepicker-example',
        });
    
        await expectAsync(inputHarness.getHintText()).toBeResolvedTo(
          'Choose a time that allows for late arrivals.',
        );
    
        await timepickerHarness.clickSelectorButton();
    
        await inputHarness.clickHelpInline();
        await expectAsync(inputHarness.getHelpPopoverContent()).toBeResolvedTo(
          fixture.componentInstance.helpPopoverContent,
        );
    
        await timepickerHarness.clickSelectorButton();
        const selectorHarness = await timepickerHarness.getTimepickerSelector();
        await expectAsync(selectorHarness.getSelectedValue()).toBeResolvedTo(
          '2:45 AM',
        );
        await expectAsync(
          (await timepickerHarness.getControl()).isDisabled(),
        ).toBeResolvedTo(false);
      });
    
      it('should throw an error if selecting an invalid time', async () => {
        const { inputHarness, timepickerHarness } = await setupTest({
          dataSkyId: 'timepicker-example',
        });
    
        await timepickerHarness.clickSelectorButton();
        const selectorHarness = await timepickerHarness.getTimepickerSelector();
    
        await selectorHarness.clickMinute('40');
        await expectAsync(
          inputHarness.hasCustomFormError('invalidMinute'),
        ).toBeResolvedTo(true);
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
      Validators,
    } from '@angular/forms';
    import { SkyTimepickerModule, SkyTimepickerTimeOutput } from '@skyux/datetime';
    import { SkyInputBoxModule } from '@skyux/forms';
    
    interface DemoForm {
      time: FormControl<SkyTimepickerTimeOutput | string>;
    }
    
    function isTimepickerOutput(value: unknown): value is SkyTimepickerTimeOutput {
      return !!(value && typeof value === 'object' && 'minute' in value);
    }
    
    function validateTime(
      control: AbstractControl<SkyTimepickerTimeOutput | string>,
    ): ValidationErrors | null {
      const minute = isTimepickerOutput(control.value)
        ? control.value.minute
        : undefined;
    
      return minute && minute % 15 !== 0 ? { invalidMinute: true } : null;
    }
    
    /**
     * @title Timepicker with basic setup
     */
    @Component({
      selector: 'app-datetime-timepicker-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyInputBoxModule,
        SkyTimepickerModule,
      ],
    })
    export class DatetimeTimepickerBasicExampleComponent {
      protected formGroup: FormGroup<DemoForm>;
      protected time: FormControl<SkyTimepickerTimeOutput | string>;
    
      protected hintText = 'Choose a time that allows for late arrivals.';
    
      public helpPopoverContent =
        'Allow time to complete all activities that your team signed up for. All activities take about 30 minutes, except the ropes course, which takes 60 minutes.';
    
      constructor() {
        this.time = new FormControl('2:45', {
          nonNullable: true,
          validators: [Validators.required, validateTime],
        });
    
        this.formGroup = inject(FormBuilder).group<DemoForm>({ time: this.time });
      }
    }

# Testing

                   Skip to Main Content

 Input box
=========

Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-1.9ca7d4e41274caab88eb7dc65dc77191.png)

Do use input boxes to style data entry elements.

Use input boxes when forms include native HTML elements for text and selection, such as `<input>`, `<select>`, and `<textarea>`. To determine whether to use the HTML `<select>` element or a SKY UX component, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-2.e36a2aa5fa708257b8f148f4a0f24924.png)

Do use input boxes to style HTML elements.

Use input boxes when forms include SKY UX components, such as [country fields](/skyux/components/country-field.md), [datepickers](/skyux/components/datepicker.md), [lookup fields](/skyux/components/lookup.md), [phone fields](/skyux/components/phone-field.md), and [timepickers](/skyux/components/timepicker.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-usage-3.09f692aebca6c7bbd71fa82f334eed3a.png)

Do use input boxes to style SKY UX components.

 Anatomy
--------

1

Label

2

Input field

3

Required field marker (optional)

4

Help inline button (optional)

5

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-anatomy.54376094501941eac71074c7adc57b24.png)

 Options
--------

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-required.a56e43319fbbde7a3858c20d556886e0.png)

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-help-button.361ba22cebcd930dd1d8baebdeb4bada.png)

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-hint-text.236b96597d3f69586ab8c35caf98734e.png)

Do use hint text to explain how to enter data.

### Character count

When users are likely to exceed a character limit, use a [character count](/skyux/components/character-count.md) indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-count.6742159929f2689848d03872f8016c22.png)

Do use character count indicators on input fields when users may realistically exceed character limits.

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the form input:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-options-stacked.170f20ef8ed9b3d088316694a870cda1.png)

### Suggested text

To provide suggested text that helps users with data entry on common fields, you can use the HTML `autocomplete` attribute. Place this attribute on `input`, `textarea`, and `select` elements instead of using the [SKY UX autocomplete component](/skyux/components/autocomplete.md).

Browsers provide suggested text based on previous entries, so `autocomplete` is most helpful for personal information, such as names and addresses, that users enter in multiple places. Don't use `autocomplete` when browsers are unlikely to provide useful suggested text, such as for fields that request information about other users.

 Behavior and states
--------------------

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the [error-handling guidelines](/skyux/design/guidelines/error-handling.md).

 Content
--------

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-1.ca49c946672ebf8f31aac988903a2f2b.png)

Don't use full sentences or questions for input labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/input-box/input-box-content-2.483192c1386905976861756a7e4923d3.png)

Do use succinct input labels.

 Layout
-------

Input boxes are most common inside [modals](/skyux/components/modal.md) and follow [form design guidelines](/skyux/design/guidelines/form-design.md). For two-column or three-column layouts, use fluid grid's small gutters [spacing option](/skyux/design/styles/spacing.md) to apply vertical and horizontal padding evenly.

 Related information
--------------------

### Components

*   [Character count](/skyux/components/character-count.md)
*   [Country field](/skyux/components/country-field.md)
*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Modal](/skyux/components/modal.md)
*   [Phone field](/skyux/components/phone-field.md)
*   [Timepicker](/skyux/components/timepicker.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Spacing](/skyux/design/styles/spacing.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/input-box/input-box.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 Basic usage
------------

Input boxes usually consist of a text label and a form element, such as `input`, `select`, or `textarea`. The input box component handles the majority of use cases by detecting the form element inside it and rendering the the rest of the component based on its inputs. For instance, specifying `labelText` renders a `label` element and associates it with the form element by assigning a unique ID to the form element's `id` attribute and the `label` element's `for` attribute.

Other features of input box include:

*   Adding a [SKY UX character count](/skyux/components/character-count.md) component with the appropriate validator.
*   Adding a [SKY UX help inline](/skyux/components/help-inline.md) button that opens a [SKY UX popover](/skyux/components/popover.md) when clicked.
*   Displaying a red asterisk (\*) next to the label of required fields based on the input's `ngModel`   `required` property or `FormControl`   [Required](https://angular.io/api/forms/RequiredValidator) validator.
*   Displaying errors for well-known validators, including the built-in Angular [Max length](https://angular.io/api/forms/MaxLengthValidator), [Min length](https://angular.io/api/forms/MinLengthValidator), and [Required](https://angular.io/api/forms/RequiredValidator) validators; built-in SKY UX [Email](/skyux/components/email-validation.md) and [URL](/skyux/components/email-validation.md) validators; and the validators added by the [Datepicker](/skyux/components/datepicker.md) , [Phone field](/skyux/components/phone-field.md), and [Timepicker](/skyux/components/timepicker.md) components and directives. These errors render inside an [ARIA live](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) region and are associated with the input element using `aria-errormessage` for accessibility.
*   Adding the appropriate [vertical spacing CSS class](/skyux/design/styles/spacing%23vertical-spacing.md) for displaying an input box above another input box.

 Advanced usage
---------------

For more complex scenarios, each component can be specified individually inside the `sky-input-box` element, and the input box component will place it in the correct location.

*   To use a form element other than an `input`, `select`, or `textarea` element, or to have full control over the input element, include the `sky-form-control` class on the element. You will be responsible for displaying error messages, adding a `label` element and associating it to the input, etc.
*   To specify your own `label` element, or to use an element other than `label`, include the `sky-control-label` class on the element.
*   To display a `sky-help-inline` component with your own click handler, or to use another component to display inline help, include the `sky-control-help` class on the element.
*   To display custom validation error messages under the input, include a `sky-form-error` element. Use `@if` to determine whether to display the validation message based on the input value. These error messages render in the ARIA live region after any errors are detected by input box.

 SkyInputBoxModule
------------------

Type: Module

`import { SkyInputBoxModule } from '@skyux/forms';`

 SkyInputBoxComponent
---------------------

Type: Component

Selector: `sky-input-box`

A wrapper component that provides styling and accessibility to form elements.

### Inputs

#### `characterLimit: number | undefined`

The maximum number of characters allowed in the input. A [SKY UX character count](/skyux/components/character-count.md) will be placed on the input element with the appropriate validator.

#### `disabled: boolean | undefined`

Whether to visually highlight the input box as disabled. To disable the input box's input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled` property. If the input element is mapped to an Angular form control (e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically; if the input element is not associated with an Angular form control, the `disabled` property on the input box must be set to `true` to visually indicate the disabled state on the input box.

Default: `false`

#### `hasErrors: boolean | undefined`

Whether to visually highlight the input box in an error state. If not specified, the input box displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error.

Default: `undefined`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the input box label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the input box label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `labelText: string | undefined`

The text to display as the input's label and in known validation error messages. The label will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX component included in the input box.

#### `stacked: BooleanInput`

Whether the input box is stacked on another input box. When specified, the appropriate vertical spacing is automatically added to the input box.

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

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

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

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

 SkyInputBoxHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyInputBoxHarness](/skyux/components/input-box?docs-active-tab=testing#class_sky-input-box-harness.md) instances.

    interface SkyInputBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
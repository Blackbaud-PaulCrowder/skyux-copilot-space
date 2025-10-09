                    

 Country field
=============

The country field lets users enter search criteria and then select a country from search results. Country fields must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use country fields when users need to select countries.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/country-field/country-field-usage-form.71fd04415ddb7476b49042bbe7097722.png)

Use country fields when users need to select countries.

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

Selected country flag (optional)

6

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/country-field/country-field-anatomy.69739cfba2944db9c0508d5159482eab.png)

### Search results

1

Search results

2

Focused country

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/country-field/country-field-anatomy-results.bbc19513d7716fac7bf19211399e22b2.png)

 Options
--------

### Required field marker

When a country field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

### Help inline button

When you need to supplement a country field with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a country field, use hint text. This persistent inline help can explain details such as:

*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a country field is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the country field from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the country field:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/country-field/country-field-options-stacked.875de1fb6bf9c6735cf36fa3bb481d88.png)

 Related information
--------------------

### Components

*   [Autocomplete](/skyux/components/autocomplete.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Phone field](/skyux/components/phone-field.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/country-field/country-field.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 Setup
------

To enable standard form features, you must wrap the country field in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyCountryFieldModule
----------------------

Type: Module

`import { SkyCountryFieldModule } from '@skyux/lookup';`

 SkyCountryFieldComponent
-------------------------

Type: Component

Selector: `sky-country-field`

### Inputs

#### `autocompleteAttribute: string | undefined`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value for the HTML `autocomplete` attribute on the form input.

Default: `'off'`

#### `defaultCountry: string | undefined`

The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country code for the default country. When search results include the default country, it appears at the top of the list.

Default: `"us"`

#### `disabled: boolean`

Whether to disable the country field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `supportedCountryISOs: string[]`

The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country codes for the countries that users can select. By default, all countries are available.

### Outputs

#### `selectedCountryChange: EventEmitter<SkyCountryFieldCountry>`

Fires when the selected country changes.

 SkyCountryFieldCountry
-----------------------

Type: Interface

Represents the data for a given country.

    interface SkyCountryFieldCountry {
      iso2: string;
      name?: string;
    }

### Properties

#### `iso2: string`

The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country code for the country.

#### `name?: string`

The name of the country.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCountryFieldHarness
-----------------------

Type: Class

`import { SkyCountryFieldHarness } from '@skyux/lookup/testing';`

Harness for interacting with a country field component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).blur()` instead.

Blurs the country field input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).clear()` instead.

Clears the country field input value.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).setValue()` instead.

Enters text into the country field input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).focus()` instead.

Focuses the country field input.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyAutocompleteInputHarness>`

Gets the autocomplete input harness.

#### Returns

`Promise<SkyAutocompleteInputHarness>`

#### `getSearchResult(filter: SkyCountryFieldSearchResultHarnessFilters): Promise<SkyCountryFieldSearchResultHarness>`

Gets a specific country field search result based on the filter criteria.

#### Parameters

##### `filter: SkyCountryFieldSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyCountryFieldSearchResultHarness>`

#### `getSearchResults(filters?: SkyCountryFieldSearchResultHarnessFilters): Promise<SkyCountryFieldSearchResultHarness[]>`

Gets an array of country field search results based on the filter criteria. If no filter is provided, returns all country field search results.

#### Parameters

##### `filters?: SkyCountryFieldSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyCountryFieldSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyCountryFieldSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each country field search result.

#### Parameters

##### `filters?: SkyCountryFieldSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).getValue()` instead.

Gets the value of the country field input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).isDisabled()` instead.

Whether the country field input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await countryField.getControl()).isFocused()` instead.

Whether the country field input is focused.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the country field is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyCountryFieldSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyCountryFieldSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyCountryFieldHarness.with(filters: SkyCountryFieldHarnessFilters): HarnessPredicate<SkyCountryFieldHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCountryFieldHarness` that meets certain criteria. These filters only work for standalone country fields. For country fields wrapped inside `sky-input-box`, place filters on the input box instead, and query the country field using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyCountryFieldHarnessFilters`

#### Returns

`HarnessPredicate<SkyCountryFieldHarness>`

 SkyCountryFieldHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCountryFieldHarness` instances.

    interface SkyCountryFieldHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyCountryFieldSearchResultHarness
-----------------------------------

Type: Class

`import { SkyCountryFieldSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getText(): Promise<string>`

Returns the text of the search result.

#### Returns

`Promise<string>`

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

#### `select(): Promise<void>`

Selects the search result.

#### Returns

`Promise<void>`

#### `SkyCountryFieldSearchResultHarness.with(filters: SkyCountryFieldSearchResultHarnessFilters): HarnessPredicate<SkyCountryFieldSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCountryFieldSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCountryFieldSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyCountryFieldSearchResultHarness>`

 SkyCountryFieldSearchResultHarnessFilters
------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyCountryFieldSearchResultHarness` instances.

    interface SkyCountryFieldSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyAutocompleteInputHarness
----------------------------

Type: Class

`import { SkyAutocompleteInputHarness } from '@skyux/lookup/testing';`

Harness to interact with the autocomplete input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Returns the value of the input's `aria-controls` attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input. The value will be set by simulating key presses that correspond to the given value.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

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

A set of criteria that can be used to filter a list of [SkyInputBoxHarness](/skyux/components/country-field?docs-active-tab=design#class_sky-input-box-harness.md) instances.

    interface SkyInputBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
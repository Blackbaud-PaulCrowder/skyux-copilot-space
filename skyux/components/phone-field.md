                    

 Phone field
===========

The phone field module creates a button, search input, and text input for entering and validating international phone numbers. Phone fields must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use phone fields to validate phone numbers against the correct format for the selected country.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-usage.5de7ebbc7d6b95874466ae54580d8b01.png)

Do use phone fields to validate phone numbers.

 Anatomy
--------

### Phone field

1

Country selector button

2

Label

3

Input field

4

Default hint text

5

Required field marker (optional)

6

Help inline button (optional)

7

Additional hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-anatomy.e357178a9d225fced616ee795ba6e838.png)

### Country selector

1

Country search input

2

Country search close button

3

Search results

4

Focused country

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-results-anatomy.2f2325f1b4bfa46340d74dcc23a3eb34.png)

 Options
--------

### Default country

By default, the country selector is set to the United States, but you can specify a different default value. You can also set the default dynamically. For example, you can set the default value using location detection.

### Required field marker

When a phone field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a phone field label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a phone field, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the phone field
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a phone field is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the phone field from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the phone field:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-options-stacked.8ea8739ffb15ebac1fcc7b930653df30.png)

 Behavior and states
--------------------

### Country selection

The selected country determines the format to use to validate phone numbers. If users enter phone numbers from a different country, they must also select that country to validate phone numbers based on the correct format.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-country-picker.5bda8df90bb62f2864d7bf7018518a2b.png)

### Phone format validation

The phone field input directive validates phone numbers based on the format for the selected country. You must specify an error message. In most cases, the error message should be "Enter a phone number matching the format for the selected country."

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/phone-field/phone-field-error.f5ad123c2f62a6da21136c589fec5089.png)

 Related content
----------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Help inpline button](/skyux/components/help-inlin.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/phone-field`[View in NPM](https://www.npmjs.com/package/@skyux/phone-field) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/phone-field/src/lib/modules/phone-field/phone-field.module.ts#L10) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/phone-field`Copy None found.

 Setup
------

To enable standard form features, you must wrap the phone field in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyPhoneFieldModule
--------------------

Type: Module

`import { SkyPhoneFieldModule } from '@skyux/phone-field';`

 SkyPhoneFieldComponent
-----------------------

Type: Component

Selector: `sky-phone-field`

### Inputs

#### `allowExtensions: boolean`

Whether phone number extensions are allowed.

Default: `true`

#### `defaultCountry: string`

The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country code for the default country. The country selector button displays a flag icon for this default country until users select a different country.

Default: `"us"`

#### `returnFormat: SkyPhoneFieldNumberReturnFormat`

The format for validated phone numbers. Options include: `"default"`, `"international"`, and `"national"`.

Default: `"default"`

#### `selectedCountry: SkyPhoneFieldCountry | undefined`

The currently selected country to validate against.

#### `supportedCountryISOs: string[] | undefined`

The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country codes for the countries that users can select. By default, all countries are available.

### Outputs

#### `selectedCountryChange: EventEmitter<SkyPhoneFieldCountry>`

Emits a `SkyPhoneFieldCountry` object when the selected country in the country search input changes.

 SkyPhoneFieldInputDirective
----------------------------

Type: Directive

Selector: `[skyPhoneFieldInput]`

Creates a button, search input, and text input for entering and validating international phone numbers. Place this attribute on an `input` element, and wrap that element in a `sky-phone-field` component. By default, the country selector button displays a flag icon for the default country, and the phone number input displays a sample of the correct phone number format. When users select the country selector button, they expose the country search input, which is [an autocomplete input](/skyux/components/autocomplete.md) that allows them to select different countries. When users enter `+` followed by an international dial code in the phone number input, the country automatically switches to the country associated with the dial code.

### Inputs

#### `disabled: boolean`

Whether to disable the phone field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `skyPhoneFieldNoValidate: boolean`

Whether to prevent validation on the phone number input. For validation, phone numbers are driven through the `ngModel` attribute that you specify on an `input` element or on a `FormControl` in a reactive form. To prevent validation, set this property to `true`.

Default: `false`

 SkyPhoneFieldCountry
---------------------

Type: Interface

    interface SkyPhoneFieldCountry {
      dialCode?: string;
      exampleNumber?: string;
      iso2: string;
      name?: string;
    }

### Properties

#### `dialCode?: string`

The country's international dial code.

#### `exampleNumber?: string`

The placeholder value that demonstrates the country's number format. This value is `undefined` until a country is selected to validate against.

#### `iso2: string`

The country's [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm) country code.

#### `name?: string`

The name of the country.

 SkyPhoneFieldNumberReturnFormat
--------------------------------

Type: Type alias

Represents the format for validated phone numbers. `default` returns the national format for the default country, `national` returns the national format for all countries, and `international` returns the international format for all countries.

    type SkyPhoneFieldNumberReturnFormat = "default" | "international" | "national"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPhoneFieldHarness
---------------------

Type: Class

`import { SkyPhoneFieldHarness } from '@skyux/phone-field/testing';`

Harness for interacting with a phone field component in tests.

### Methods

#### `getControl(): Promise<SkyPhoneFieldInputHarness>`

Gets the phone field input harness.

#### Returns

`Promise<SkyPhoneFieldInputHarness>`

#### `getSelectedCountryIso2(): Promise<null | string>`

Returns the selected country iso2 code.

#### Returns

`Promise<null | string>`

#### `getSelectedCountryName(): Promise<null | string>`

Returns the selected country name.

#### Returns

`Promise<null | string>`

#### `searchCountry(searchText: string): Promise<string[]>`

Opens the country selector, performs a search, but makes no selection.

#### Parameters

##### `searchText: string`

The name of the country to select.

#### Returns

`Promise<string[]>`

#### `selectCountry(searchText: string): Promise<void>`

Opens the country selector, performs a search, and selects the first result (if any).

#### Parameters

##### `searchText: string`

The name of the country to select.

#### Returns

`Promise<void>`

#### `SkyPhoneFieldHarness.with(filters: SkyPhoneFieldHarnessFilters): HarnessPredicate<SkyPhoneFieldHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPhoneFieldHarness` that meets certain criteria.

These filters only work for standalone phone fields. For phone fields wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyPhoneFieldHarnessFilters`

#### Returns

`HarnessPredicate<SkyPhoneFieldHarness>`

 SkyPhoneFieldHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPhoneFieldHarness](/skyux/components/phone-field?docs-active-tab=design#class_sky-phone-field-harness.md) instances.

    interface SkyPhoneFieldHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPhoneFieldInputHarness
--------------------------

Type: Class

`import { SkyPhoneFieldInputHarness } from '@skyux/phone-field/testing';`

Harness to interact with the phone field input harness.

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
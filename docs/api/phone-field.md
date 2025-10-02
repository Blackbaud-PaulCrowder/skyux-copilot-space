---
component: 'phone-field'
type: 'api-documentation'
description: 'API documentation for the phone-field component including components, interfaces, and types.'
---

# Phone Field API Documentation

## Components and Directives

#### PhoneFieldBasicExampleComponent

**Selector:** `app-phone-field-basic-example`

**Package:** `@skyux/code-examples`

#### SkyPhoneFieldInputDirective

Creates a button, search input, and text input for entering and validating
international phone numbers. Place this attribute on an `input` element, and wrap
that element in a `sky-phone-field` component. By default, the country selector
button displays a flag icon for the default country, and the phone number input
displays a sample of the correct phone number format. When users select the country
selector button, they expose the country search input, which is
[an autocomplete input](https://developer.blackbaud.com/skyux/components/autocomplete)
that allows them to select different countries. When users enter `+` followed by an
international dial code in the phone number input, the country automatically switches
to the country associated with the dial code.

**Selector:** `[skyPhoneFieldInput]`

**Package:** `@skyux/phone-field`

**Inputs:**

- `skyPhoneFieldNoValidate`: `boolean` - Whether to prevent validation on the phone number input. For validation,
phone numbers are driven through the `ngModel` attribute that you specify on an
`input` element or on a `FormControl` in a reactive form. To prevent validation,
set this property to `true`. (default: false)
- `disabled`: `boolean` - Whether to disable the phone field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)

#### SkyPhoneFieldComponent

**Selector:** `sky-phone-field`

**Package:** `@skyux/phone-field`

**Inputs:**

- `supportedCountryISOs`: `string[] | undefined` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country codes for the countries that users can select. By default, all countries are available.
- `allowExtensions`: `boolean` - Whether phone number extensions are allowed. (default: true)
- `defaultCountry`: `string` - The
[International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country code for the default country. The country selector button displays a flag
icon for this default country until users select a different country. (default: "us")
- `returnFormat`: `SkyPhoneFieldNumberReturnFormat` - The format for validated phone numbers.
Options include: `"default"`, `"international"`, and `"national"`. (default: "default")
- `selectedCountry`: `SkyPhoneFieldCountry | undefined` - The currently selected country to validate against.

**Outputs:**

- `selectedCountryChange`: `EventEmitter<SkyPhoneFieldCountry>` - Emits a `SkyPhoneFieldCountry` object when the selected country in the country search
input changes.
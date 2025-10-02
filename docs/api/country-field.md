---
component: 'country-field'
type: 'api-documentation'
description: 'API documentation for the country-field component including components, interfaces, and types.'
---

# Country Field API Documentation

## Components and Directives

#### LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Package:** `@skyux/code-examples`

#### SkyCountryFieldComponent

**Selector:** `sky-country-field`

**Package:** `@skyux/lookup`

**Inputs:**

- `autocompleteAttribute`: `string | undefined` - The value for the HTML `autocomplete` attribute on the form input. (default: 'off')
- `defaultCountry`: `string | undefined` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country code for the default country.
When search results include the default country, it appears at the top of the list. (default: "us")
- `disabled`: `boolean` - Whether to disable the country field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `supportedCountryISOs`: `string[]` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country codes for the countries that users can select. By default, all countries are available.

**Outputs:**

- `countryFieldFocusout`: `EventEmitter<FocusEvent>` - Fires when the country field is focused out.
- `selectedCountryChange`: `EventEmitter<SkyCountryFieldCountry>` - Fires when the selected country changes.
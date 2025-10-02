---
component: 'numeric'
type: 'api-documentation'
description: 'API documentation for the numeric component including components, interfaces, and types.'
---

# Numeric API Documentation

## Components and Directives

#### AutonumericCurrencyExampleComponent

**Selector:** `app-autonumeric-currency-example`

**Package:** `@skyux/code-examples`

#### AutonumericInternationalFormattingExampleComponent

**Selector:** `app-autonumeric-international-formatting-example`

**Package:** `@skyux/code-examples`

#### AutonumericOptionsProviderExampleComponent

**Selector:** `app-autonumeric-options-provider-example`

**Package:** `@skyux/code-examples`

#### AutonumericPresetExampleComponent

**Selector:** `app-autonumeric-preset-example`

**Package:** `@skyux/code-examples`

#### CoreNumericBasicExampleComponent

**Selector:** `app-core-numeric-basic-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `configuredValue`: `number` (default: 1234567)
- `defaultValue`: `number` (default: 1000000)
- `numericOptions`: `SkyNumericOptions`

#### SkyAutonumericDirective

Wraps the [autoNumeric utility](https://github.com/autoNumeric/autoNumeric) to format
any type of number, including currency.

**Selector:** `input[skyAutonumeric]`

**Package:** `@skyux/autonumeric`

**Inputs:**

- `skyAutonumericFormChangesUnformatted`: `boolean | undefined` (default: false)
- `skyAutonumeric`: `SkyAutonumericOptions | undefined` - Assigns the name of a property from `SkyAutonumericOptionsProvider`.
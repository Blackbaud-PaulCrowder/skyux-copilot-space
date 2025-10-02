---
component: 'autonumeric'
type: 'api-documentation'
description: 'API documentation for the autonumeric component including components, interfaces, and types.'
---

# Autonumeric API Documentation

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

#### SkyAutonumericDirective

Wraps the [autoNumeric utility](https://github.com/autoNumeric/autoNumeric) to format
any type of number, including currency.

**Selector:** `input[skyAutonumeric]`

**Package:** `@skyux/autonumeric`

**Inputs:**

- `skyAutonumericFormChangesUnformatted`: `boolean | undefined` (default: false)
- `skyAutonumeric`: `SkyAutonumericOptions | undefined` - Assigns the name of a property from `SkyAutonumericOptionsProvider`.
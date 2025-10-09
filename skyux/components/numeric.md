                 

 Numeric
=======

The numeric pipe and numeric service format numbers with proper localization and currency symbol placement.

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/numeric/numeric.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyNumericModule
-----------------

Type: Module

`import { SkyNumericModule } from '@skyux/core';`

 SkyNumericPipe
---------------

Type: Pipe

Pipe name: `skyNumeric`

Shortens numbers to rounded numbers and abbreviation characters such as K for thousands, M for millions, B for billions, and T for trillions. The pipe also formats for currency. Be sure you have a space after the two curly brackets opening the pipe and a space before the two curly brackets closing the pipe or it will not work.

### Methods

#### `transform(value: null | number | undefined, config?: SkyNumericOptions): string`

Formats a number based on the provided options.

#### Parameters

##### `value: null | number | undefined`

##### `config?: SkyNumericOptions`

#### Returns

`string`

 SkyNumericService
------------------

Type: Service

### Methods

#### `formatNumber(value: null | number | undefined, options: SkyNumericOptions): string`

Formats a number based on the provided options.

#### Parameters

##### `value: null | number | undefined`

The number to format.

##### `options: SkyNumericOptions`

Format options.

#### Returns

`string`

 SkyNumericOptions
------------------

Type: Interface

Provides arguments for the number to format.

    interface SkyNumericOptions {
      currencyDisplay?: "symbol" | "code" | "narrowSymbol" | "name";
      currencySign?: "standard" | "accounting";
      digits?: number;
      format?: string;
      iso?: string;
      locale?: string;
      minDigits?: number;
      truncate?: boolean;
      truncateAfter?: number;
    }

### Properties

#### `currencyDisplay?: "symbol" | "code" | "narrowSymbol" | "name"`

Specifies the display of the currency. Defaults to 'symbol'.

#### `currencySign?: "standard" | "accounting"`

Specifies the format of the currency.

#### `digits?: number`

Specifies the maximum number of digits after the decimal separator.

#### `format?: string`

Specifies how to format the number. Options are `currency` or `number`.

#### `iso?: string`

Specifies the ISO4217 currency code to use for currency formatting.

#### `locale?: string`

Specifies the locale code to use when formatting.

#### `minDigits?: number`

Specifies the minimum number of digits after the decimal separator. This property only applies when the `truncate` property is set to `false`. If `digits` specifies a maximum number of digits, then `minDigits` must be less than that value.

#### `truncate?: boolean`

Indicates whether to shorten numbers to rounded numbers and abbreviation characters such as K for thousands, M for millions, B for billions, and T for trillions.

#### `truncateAfter?: number`

Specifies the minimum value at which numbers are shortened to rounded numbers and abbreviation characters. Values less than `1000` are not truncated.
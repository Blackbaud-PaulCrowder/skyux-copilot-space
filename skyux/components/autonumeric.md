                 

 Autonumeric
===========

The autonumeric directive automatically formats currency and other numbers that users enter in form inputs. This directive wraps the third-party autoNumeric library. For in-depth information about autoNumeric and its capabilities, see [the autoNumeric documentation.](https://github.com/autoNumeric/autoNumeric/blob/next/README.md)

 Installation
-------------

NPM package

`@skyux/autonumeric`[View in NPM](https://www.npmjs.com/package/@skyux/autonumeric) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/autonumeric/src/lib/modules/autonumeric/autonumeric.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/autonumeric`Copy None found.

 SkyAutonumericModule
---------------------

Type: Module

`import { SkyAutonumericModule } from '@skyux/autonumeric';`

 SkyAutonumericDirective
------------------------

Type: Directive

Selector: `input[skyAutonumeric]`

Wraps the [autoNumeric utility](https://github.com/autoNumeric/autoNumeric) to format any type of number, including currency.

### Inputs

#### `skyAutonumeric: SkyAutonumericOptions | undefined`

Assigns the name of a property from `SkyAutonumericOptionsProvider`.

 SkyAutonumericOptions
----------------------

Type: Type alias

Custom options to provide to the underlying [AutoNumeric library](https://github.com/autoNumeric/autoNumeric). The value can be set to `string`, which is an alias that represents a [set of predefined set of options](https://github.com/autoNumeric/autoNumeric#predefined-options) for a currency or language, or `Options`, which is a [custom set of options](https://github.com/autoNumeric/autoNumeric#options) that override any default options that the `skyAutonumeric` attribute specifies.

    type SkyAutonumericOptions = string | keyof AutoNumeric.PredefinedOptions | AutoNumeric.Options

 SkyAutonumericOptionsProvider
------------------------------

Type: Service

Provides options to the underlying [AutoNumeric library](https://github.com/autoNumeric/autoNumeric). This can set global options on multiple input fields.

### Methods

#### `getConfig(): SkyAutonumericOptions`

The value for a settings object to pass to the AutoNumeric library. This overrides any default options specified by the `skyAutonumeric` attribute.

#### Returns

`SkyAutonumericOptions`
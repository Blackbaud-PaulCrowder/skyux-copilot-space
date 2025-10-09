               

 Format
======

The format module provides a component that allows you to place formatted text inside a tokenized string template. This avoids the need to build HTML manually on the server or in a custom directive where HTML injection bugs are common.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/format/format.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyFormatModule
----------------

Type: Module

`import { SkyFormatModule } from '@skyux/layout';`

 SkyFormatComponent
-------------------

Type: Component

Selector: `sky-format`

### Inputs

#### `args: TemplateRef<any>[] | undefined`

An array of `TemplateRef` objects to be placed in the template, where the `nth` item is placed at the `{n}` location in the template.

#### `text: string | undefined`

The tokenized string that represents the template. Tokens use the `{n}` notation where `n` is the ordinal of the item to replace the token.

 SkyAppFormat
-------------

Type: Service

### Methods

#### `formatText(format: string, args: any[]): string`

#### Parameters

##### `format: string`

##### `args: any[]`

#### Returns

`string`
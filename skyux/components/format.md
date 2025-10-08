# Development

               Skip to Main Content

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

# Examples

                   Skip to Main Content

 Format
======

The format module provides a component that allows you to place formatted text inside a tokenized string template. This avoids the need to build HTML manually on the server or in a custom directive where HTML injection bugs are common.Installation
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

### Format service basic usage

Edit in StackBlitz

**39,210** is an important number. **78** is important, too, but not as important as **39,210**.

Show code

Copy

    <sky-format
      text="{0} is an important number. {1} is important, too, but not as important as {0}."
      [args]="[value1, value2]"
    />
    
    <ng-template #value1>
      <strong class="number-large">39,210</strong>
    </ng-template>
    
    <ng-template #value2>
      <strong class="number-medium">78</strong>
    </ng-template>
Copy

    .number-large {
      font-size: 18px;
    }
    
    .number-medium {
      font-size: 16px;
    }

Copy

    import { Component } from '@angular/core';
    import { SkyFormatModule } from '@skyux/layout';
    
    /**
     * @title Format service basic usage
     */
    @Component({
      selector: 'app-layout-format-example',
      templateUrl: './example.component.html',
      styleUrls: ['./example.component.scss'],
      imports: [SkyFormatModule],
    })
    export class LayoutFormatExampleComponent {}
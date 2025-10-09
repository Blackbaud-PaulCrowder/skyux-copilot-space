                  

 Text highlight
==============

The text highlight directive highlights text all matching text within DOM elements.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/text-highlight/text-highlight.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTextHighlightModule
-----------------------

Type: Module

`import { SkyTextHighlightModule } from '@skyux/indicators';`

 SkyTextHighlightDirective
--------------------------

Type: Directive

Selector: `[skyHighlight]`

Highlights all matching text within the current DOM element.

### Inputs

#### `skyHighlight: string | string[] | undefined`

The text to highlight.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextHighlightHarness
------------------------

Type: Class

`import { SkyTextHighlightHarness } from '@skyux/indicators/testing';`

Harness to interact with a text highlight directive in tests.

### Methods

#### `getHighlights(): Promise<TestElement[]>`

Gets an array of all instances of highlighted text.

#### Returns

`Promise<TestElement[]>`

#### `SkyTextHighlightHarness.with(filters: SkyTextHighlightHarnessFilters): HarnessPredicate<SkyTextHighlightHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextHighlightHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextHighlightHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextHighlightHarness>`

 SkyTextHighlightHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyTextHighlightHarness](/skyux/components/text-highlight?docs-active-tab=development#class_sky-text-highlight-harness.md) instances.

    interface SkyTextHighlightHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
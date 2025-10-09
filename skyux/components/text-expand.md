                 

 Text expand
===========

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand/text-expand.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandModule
--------------------

Type: Module

`import { SkyTextExpandModule } from '@skyux/layout';`

 SkyTextExpandComponent
-----------------------

Type: Component

Selector: `sky-text-expand`

### Inputs

#### `expandModalTitle: string | undefined`

The title to display when the component expands the full text in a modal.

Default: `"Expanded view"`

#### `maxExpandedLength: number`

The maximum number of text characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal instead.

Default: `600`

#### `maxExpandedNewlines: number`

The maximum number of newline characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal view instead.

Default: `2`

#### `maxLength: number`

The number of text characters to display before truncating the text. To avoid truncating text in the middle of a word, the component looks for a space in the 10 characters before the last character.

Default: `200`

#### `text: string`

The text to truncate.

#### `truncateNewlines: boolean`

Whether to replace newline characters in truncated text with spaces.

Default: `true`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandHarness
---------------------

Type: Class

`import { SkyTextExpandHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getExpandedViewModal(): Promise<SkyTextExpandModalHarness>`

Gets the harness to interact with the modal expanded view.

#### Returns

`Promise<SkyTextExpandModalHarness>`

#### `getText(): Promise<string>`

Gets the text content of the text expand.

#### Returns

`Promise<string>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `textExpandsToModal(): Promise<boolean>`

Whether the text will expand to a modal.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandHarness.with(filters: SkyTextExpandHarnessFilters): HarnessPredicate<SkyTextExpandHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandHarness>`

 SkyTextExpandHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandHarness` instances.

    interface SkyTextExpandHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandModalHarness
--------------------------

Type: Class

`import { SkyTextExpandModalHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand modal component in tests.

### Methods

#### `clickCloseButton(): Promise<void>`

Clicks the modal close button.

#### Returns

`Promise<void>`

#### `getExpandModalTitle(): Promise<string>`

Gets the modal title.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Gets the expanded text in the modal.

#### Returns

`Promise<string>`
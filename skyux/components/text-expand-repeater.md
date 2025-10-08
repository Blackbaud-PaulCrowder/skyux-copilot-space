# Development

                 Skip to Main Content

 Text expand repeater
====================

The text expand repeater component truncates a list and displays a limited number of items until users select a link to expand the list.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand-repeater/text-expand-repeater.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandRepeaterModule
----------------------------

Type: Module

`import { SkyTextExpandRepeaterModule } from '@skyux/layout';`

 SkyTextExpandRepeaterComponent
-------------------------------

Type: Component

Selector: `sky-text-expand-repeater`

### Inputs

#### `data: InputSignal<undefined | TData[]>`

The data to truncate.

#### `itemTemplate: InputSignal<undefined | TemplateRef<unknown>>`

The template for items in the list.

#### `listStyle: InputSignal<undefined | SkyTextExpandRepeaterListStyleType>`

The style of bullet to use

Default: `"unordered"`

#### `maxItems: InputSignalWithTransform<number, unknown>`

The number of items to display before truncating the list. If not supplied, all items are shown.

 SkyTextExpandRepeaterListStyleType
-----------------------------------

Type: Type alias

    type SkyTextExpandRepeaterListStyleType = "unordered" | "ordered" | "unstyled"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandRepeaterHarness
-----------------------------

Type: Class

`import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getItems(): Promise<SkyTextExpandRepeaterItemHarness[]>`

Gets an array of container harnesses for the repeater items.

#### Returns

`Promise<SkyTextExpandRepeaterItemHarness[]>`

#### `getListStyle(): Promise<SkyTextExpandRepeaterListStyleType>`

Gets the list style.

#### Returns

`Promise<SkyTextExpandRepeaterListStyleType>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandRepeaterHarness.with(filters: SkyTextExpandRepeaterHarnessFilters): HarnessPredicate<SkyTextExpandRepeaterHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandRepeaterHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandRepeaterHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandRepeaterHarness>`

 SkyTextExpandRepeaterHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandRepeaterHarness` instances.

    interface SkyTextExpandRepeaterHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandRepeaterItemHarness
---------------------------------

Type: Class

`import { SkyTextExpandRepeaterItemHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater items in tests.

### Methods

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

# Examples

                   Skip to Main Content

 Text expand repeater
====================

The text expand repeater component truncates a list and displays a limited number of items until users select a link to expand the list.Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand-repeater/text-expand-repeater.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandRepeaterModule
----------------------------

Type: Module

`import { SkyTextExpandRepeaterModule } from '@skyux/layout';`

 SkyTextExpandRepeaterComponent
-------------------------------

Type: Component

Selector: `sky-text-expand-repeater`

### Inputs

#### `data: InputSignal<undefined | TData[]>`

The data to truncate.

#### `itemTemplate: InputSignal<undefined | TemplateRef<unknown>>`

The template for items in the list.

#### `listStyle: InputSignal<undefined | SkyTextExpandRepeaterListStyleType>`

The style of bullet to use

Default: `"unordered"`

#### `maxItems: InputSignalWithTransform<number, unknown>`

The number of items to display before truncating the list. If not supplied, all items are shown.

 SkyTextExpandRepeaterListStyleType
-----------------------------------

Type: Type alias

    type SkyTextExpandRepeaterListStyleType = "unordered" | "ordered" | "unstyled"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandRepeaterHarness
-----------------------------

Type: Class

`import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getItems(): Promise<SkyTextExpandRepeaterItemHarness[]>`

Gets an array of container harnesses for the repeater items.

#### Returns

`Promise<SkyTextExpandRepeaterItemHarness[]>`

#### `getListStyle(): Promise<SkyTextExpandRepeaterListStyleType>`

Gets the list style.

#### Returns

`Promise<SkyTextExpandRepeaterListStyleType>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandRepeaterHarness.with(filters: SkyTextExpandRepeaterHarnessFilters): HarnessPredicate<SkyTextExpandRepeaterHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandRepeaterHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandRepeaterHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandRepeaterHarness>`

 SkyTextExpandRepeaterHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandRepeaterHarness` instances.

    interface SkyTextExpandRepeaterHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandRepeaterItemHarness
---------------------------------

Type: Class

`import { SkyTextExpandRepeaterItemHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater items in tests.

### Methods

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

### Text expand repeater with basic setup

Edit in StackBlitz

*   Repeater item 1
*   Repeater item 2
*   Repeater item 3
*   Repeater item 4
*   Repeater item 5

See more

Show code

Copy

    <sky-text-expand-repeater [data]="repeaterData" [maxItems]="2" />
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';
    
    import { LayoutTextExpandRepeaterExampleComponent } from './example.component';
    
    describe('Text expand inline example', () => {
      async function setupTest(
        options: {
          dataSkyId?: string;
        } = {},
      ): Promise<{
        textExpandRepeaterHarness: SkyTextExpandRepeaterHarness;
      }> {
        await TestBed.configureTestingModule({
          imports: [LayoutTextExpandRepeaterExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutTextExpandRepeaterExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const textExpandRepeaterHarness: SkyTextExpandRepeaterHarness =
          options.dataSkyId
            ? await loader.getHarness(
                SkyTextExpandRepeaterHarness.with({
                  dataSkyId: options.dataSkyId,
                }),
              )
            : await loader.getHarness(SkyTextExpandRepeaterHarness);
    
        return { textExpandRepeaterHarness };
      }
    
      it('should set up the text expand repeater', async () => {
        const { textExpandRepeaterHarness } = await setupTest();
    
        await textExpandRepeaterHarness.clickExpandCollapseButton();
    
        await expectAsync(textExpandRepeaterHarness.isExpanded()).toBeResolvedTo(
          true,
        );
    
        const items = await textExpandRepeaterHarness.getItems();
    
        await expectAsync((await items[2].host()).text()).toBeResolvedTo(
          'Repeater item 3',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyTextExpandRepeaterModule } from '@skyux/layout';
    
    /**
     * @title Text expand repeater with basic setup
     */
    @Component({
      selector: 'app-layout-text-expand-repeater-example',
      templateUrl: './example.component.html',
      imports: [SkyTextExpandRepeaterModule],
    })
    export class LayoutTextExpandRepeaterExampleComponent {
      protected repeaterData: string[] = [
        'Repeater item 1',
        'Repeater item 2',
        'Repeater item 3',
        'Repeater item 4',
        'Repeater item 5',
      ];
    }

# Testing

                 Skip to Main Content

 Text expand repeater
====================

The text expand repeater component truncates a list and displays a limited number of items until users select a link to expand the list.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand-repeater/text-expand-repeater.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandRepeaterModule
----------------------------

Type: Module

`import { SkyTextExpandRepeaterModule } from '@skyux/layout';`

 SkyTextExpandRepeaterComponent
-------------------------------

Type: Component

Selector: `sky-text-expand-repeater`

### Inputs

#### `data: InputSignal<undefined | TData[]>`

The data to truncate.

#### `itemTemplate: InputSignal<undefined | TemplateRef<unknown>>`

The template for items in the list.

#### `listStyle: InputSignal<undefined | SkyTextExpandRepeaterListStyleType>`

The style of bullet to use

Default: `"unordered"`

#### `maxItems: InputSignalWithTransform<number, unknown>`

The number of items to display before truncating the list. If not supplied, all items are shown.

 SkyTextExpandRepeaterListStyleType
-----------------------------------

Type: Type alias

    type SkyTextExpandRepeaterListStyleType = "unordered" | "ordered" | "unstyled"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandRepeaterHarness
-----------------------------

Type: Class

`import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getItems(): Promise<SkyTextExpandRepeaterItemHarness[]>`

Gets an array of container harnesses for the repeater items.

#### Returns

`Promise<SkyTextExpandRepeaterItemHarness[]>`

#### `getListStyle(): Promise<SkyTextExpandRepeaterListStyleType>`

Gets the list style.

#### Returns

`Promise<SkyTextExpandRepeaterListStyleType>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandRepeaterHarness.with(filters: SkyTextExpandRepeaterHarnessFilters): HarnessPredicate<SkyTextExpandRepeaterHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandRepeaterHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandRepeaterHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandRepeaterHarness>`

 SkyTextExpandRepeaterHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandRepeaterHarness` instances.

    interface SkyTextExpandRepeaterHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandRepeaterItemHarness
---------------------------------

Type: Class

`import { SkyTextExpandRepeaterItemHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand repeater items in tests.

### Methods

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`
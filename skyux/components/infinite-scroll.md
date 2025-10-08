# Development

                 Skip to Main Content

 Infinite scroll
===============

The infinite scroll component dynamically loads data as users scroll.

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/infinite-scroll/infinite-scroll.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyInfiniteScrollModule
------------------------

Type: Module

`import { SkyInfiniteScrollModule } from '@skyux/lists';`

 SkyInfiniteScrollComponent
---------------------------

Type: Component

Selector: `sky-infinite-scroll`

### Inputs

#### `loading: boolean | undefined`

Required

Whether data is loading because of a `scrollEnd` event. Setting the property to `true` disables new `scrollEnd` events from firing until it changes to `false`. If this property is not specified, the infinite scroll component watches the DOM for changes and fires `scrollEnd` events when changes occur on its parent DOM element. Relying on this default behavior could fire an excessive number of `scrollEnd` events if the DOM changes are not related to loading data, so we strongly recommend using this property to explicitly set the infinite scroll's loading state.

#### `enabled: boolean | undefined`

Whether to make the infinite scroll component active when more data is available to load. By default, infinite scroll is inactive and does not call the load function.

Default: `false`

### Outputs

#### `scrollEnd: EventEmitter<void>`

Fires when scrolling triggers the need to load more data or when users select the button to load more data. This event only fires when the `enabled` property is set to `true` and data is not already loading.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInfiniteScrollHarness
-------------------------

Type: Class

`import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';`

Harness for interacting with an infinite scroll component in tests.

### Methods

#### `isEnabled(): Promise<boolean>`

Whether the infinite scroll is enabled.

#### Returns

`Promise<boolean>`

#### `isLoading(): Promise<boolean>`

Whether the infinite scroll is loading.

#### Returns

`Promise<boolean>`

#### `loadMore(): Promise<void>`

Clicks the "Load more" button.

#### Returns

`Promise<void>`

#### `SkyInfiniteScrollHarness.with(filters: SkyInfiniteScrollHarnessFilters): HarnessPredicate<SkyInfiniteScrollHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInfiniteScrollHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInfiniteScrollHarnessFilters`

#### Returns

`HarnessPredicate<SkyInfiniteScrollHarness>`

 SkyInfiniteScrollHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInfiniteScrollHarness` instances.

    interface SkyInfiniteScrollHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                   Skip to Main Content

 Infinite scroll
===============

The infinite scroll component dynamically loads data as users scroll.Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/infinite-scroll/infinite-scroll.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyInfiniteScrollModule
------------------------

Type: Module

`import { SkyInfiniteScrollModule } from '@skyux/lists';`

 SkyInfiniteScrollComponent
---------------------------

Type: Component

Selector: `sky-infinite-scroll`

### Inputs

#### `loading: boolean | undefined`

Required

Whether data is loading because of a `scrollEnd` event. Setting the property to `true` disables new `scrollEnd` events from firing until it changes to `false`. If this property is not specified, the infinite scroll component watches the DOM for changes and fires `scrollEnd` events when changes occur on its parent DOM element. Relying on this default behavior could fire an excessive number of `scrollEnd` events if the DOM changes are not related to loading data, so we strongly recommend using this property to explicitly set the infinite scroll's loading state.

#### `enabled: boolean | undefined`

Whether to make the infinite scroll component active when more data is available to load. By default, infinite scroll is inactive and does not call the load function.

Default: `false`

### Outputs

#### `scrollEnd: EventEmitter<void>`

Fires when scrolling triggers the need to load more data or when users select the button to load more data. This event only fires when the `enabled` property is set to `true` and data is not already loading.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInfiniteScrollHarness
-------------------------

Type: Class

`import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';`

Harness for interacting with an infinite scroll component in tests.

### Methods

#### `isEnabled(): Promise<boolean>`

Whether the infinite scroll is enabled.

#### Returns

`Promise<boolean>`

#### `isLoading(): Promise<boolean>`

Whether the infinite scroll is loading.

#### Returns

`Promise<boolean>`

#### `loadMore(): Promise<void>`

Clicks the "Load more" button.

#### Returns

`Promise<void>`

#### `SkyInfiniteScrollHarness.with(filters: SkyInfiniteScrollHarnessFilters): HarnessPredicate<SkyInfiniteScrollHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInfiniteScrollHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInfiniteScrollHarnessFilters`

#### Returns

`HarnessPredicate<SkyInfiniteScrollHarness>`

 SkyInfiniteScrollHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInfiniteScrollHarness` instances.

    interface SkyInfiniteScrollHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Infinite scroll with repeater

Edit in StackBlitz

Load more

Show code

Copy

    <div class="wrapper">
      <sky-repeater>
        @for (item of items; track item) {
          <sky-repeater-item>
            <sky-repeater-item-title>
              {{ item.name }}
            </sky-repeater-item-title>
          </sky-repeater-item>
        }
      </sky-repeater>
      <sky-infinite-scroll [enabled]="itemsHaveMore" (scrollEnd)="onScrollEnd()" />
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';
    
    import { ListsInfiniteScrollRepeaterExampleComponent } from './example.component';
    
    describe('Infinite scroll example', () => {
      async function setupTest(): Promise<{
        infiniteScrollHarness: SkyInfiniteScrollHarness;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            ListsInfiniteScrollRepeaterExampleComponent,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          ListsInfiniteScrollRepeaterExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const infiniteScrollHarness: SkyInfiniteScrollHarness =
          await loader.getHarness(SkyInfiniteScrollHarness);
    
        return { infiniteScrollHarness };
      }
    
      it('should set up the component', async () => {
        const { infiniteScrollHarness } = await setupTest();
    
        await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);
    
        await infiniteScrollHarness.loadMore();
    
        await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);
    
        await infiniteScrollHarness.loadMore();
    
        await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(false);
    
        await expectAsync(infiniteScrollHarness.loadMore()).toBeRejectedWithError(
          'Unable to click the "Load more" button because the infinite scroll is not enabled.',
        );
      });
    });
Copy

    export interface InfiniteScrollDemoItem {
      name: string;
    }

Copy

    import { Component, OnInit } from '@angular/core';
    import { SkyInfiniteScrollModule, SkyRepeaterModule } from '@skyux/lists';
    
    import { InfiniteScrollDemoItem } from './item';
    
    let nextId = 0;
    
    /**
     * @title Infinite scroll with repeater
     */
    @Component({
      selector: 'app-lists-infinite-scroll-repeater-example',
      styles: `
        .wrapper {
          overflow-y: auto;
          max-height: 500px;
          position: relative;
        }
      `,
      templateUrl: './example.component.html',
      imports: [SkyInfiniteScrollModule, SkyRepeaterModule],
    })
    export class ListsInfiniteScrollRepeaterExampleComponent implements OnInit {
      protected items: InfiniteScrollDemoItem[] = [];
      protected itemsHaveMore = true;
    
      public ngOnInit(): void {
        void this.#addData();
      }
    
      protected onScrollEnd(): void {
        if (this.itemsHaveMore) {
          void this.#addData();
        }
      }
    
      async #addData(): Promise<void> {
        const result = await this.#mockRemote();
        this.items = this.items.concat(result.data);
        this.itemsHaveMore = result.hasMore;
      }
    
      #mockRemote(): Promise<{
        data: InfiniteScrollDemoItem[];
        hasMore: boolean;
      }> {
        const data: InfiniteScrollDemoItem[] = [];
    
        for (let i = 0; i < 20; i++) {
          data.push({
            name: `Item #${++nextId}`,
          });
        }
    
        // Simulate async request.
        return new Promise((resolve) => {
          setTimeout(() => {
            resolve({
              data,
              hasMore: nextId < 50,
            });
          }, 1000);
        });
      }
    }

# Testing

                 Skip to Main Content

 Infinite scroll
===============

The infinite scroll component dynamically loads data as users scroll.

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/infinite-scroll/infinite-scroll.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyInfiniteScrollModule
------------------------

Type: Module

`import { SkyInfiniteScrollModule } from '@skyux/lists';`

 SkyInfiniteScrollComponent
---------------------------

Type: Component

Selector: `sky-infinite-scroll`

### Inputs

#### `loading: boolean | undefined`

Required

Whether data is loading because of a `scrollEnd` event. Setting the property to `true` disables new `scrollEnd` events from firing until it changes to `false`. If this property is not specified, the infinite scroll component watches the DOM for changes and fires `scrollEnd` events when changes occur on its parent DOM element. Relying on this default behavior could fire an excessive number of `scrollEnd` events if the DOM changes are not related to loading data, so we strongly recommend using this property to explicitly set the infinite scroll's loading state.

#### `enabled: boolean | undefined`

Whether to make the infinite scroll component active when more data is available to load. By default, infinite scroll is inactive and does not call the load function.

Default: `false`

### Outputs

#### `scrollEnd: EventEmitter<void>`

Fires when scrolling triggers the need to load more data or when users select the button to load more data. This event only fires when the `enabled` property is set to `true` and data is not already loading.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInfiniteScrollHarness
-------------------------

Type: Class

`import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';`

Harness for interacting with an infinite scroll component in tests.

### Methods

#### `isEnabled(): Promise<boolean>`

Whether the infinite scroll is enabled.

#### Returns

`Promise<boolean>`

#### `isLoading(): Promise<boolean>`

Whether the infinite scroll is loading.

#### Returns

`Promise<boolean>`

#### `loadMore(): Promise<void>`

Clicks the "Load more" button.

#### Returns

`Promise<void>`

#### `SkyInfiniteScrollHarness.with(filters: SkyInfiniteScrollHarnessFilters): HarnessPredicate<SkyInfiniteScrollHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInfiniteScrollHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInfiniteScrollHarnessFilters`

#### Returns

`HarnessPredicate<SkyInfiniteScrollHarness>`

 SkyInfiniteScrollHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInfiniteScrollHarness` instances.

    interface SkyInfiniteScrollHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
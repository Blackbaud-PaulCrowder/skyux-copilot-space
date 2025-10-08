# Design

                  Skip to Main Content

 Paging
======

The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.

 Usage
------

### Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

*   Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
    
*   Avoiding wait times of more than a couple seconds while items load.
    
*   Using less space so that the page composition better communicates the relationship between the list and other elements on the page.
    

### Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use the paging component when a list is presented in a [split view](/skyux/components/split-view.md).

 Anatomy
--------

1

Paging content

2

Previous button

3

Current page

4

Pages

5

Next button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/anatomy-paging.f9c4f00494abd78c1da30d4ceda1cdc6.png)

 Options
--------

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/option-num-pages.e53fa5d3ba28ef91eabe38beb4bf2c46.png)

The number of pages to display can be adjusted.

### Number of items per page

To determine how many items to display per page:

*   Optimize for performance to load items within 2 seconds.
    
*   Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
    
*   Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.
    

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

 Behavior and states
--------------------

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

First page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-first.1ccf8f81a34f02d1fca86b9bdd53084a.png)

The previous button is disabled.

Last page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-last.757a28099837a45311a5f11fd6a6a7b7.png)

The next button is disabled.

Page beyond midpoint

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-midpoint.7b56780bf61dc6ae41c9adc1d83f183e.png)

The selected page maintains a centered position within the pages.

### Loading new items

When users navigate to a new set of items, the list is disabled and a [wait indicator](/skyux/components/wait.md) appears in the paging content area until the new items finish loading.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-waiting.5648a36de13aa33137dc79bed85c23cb.png)

A wait indicator appears while new items load.

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Split view](/skyux/components/split-view.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Filtering lists](/skyux/design/guidelines/filtering-lists.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/paging/paging.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyPagingModule
----------------

Type: Module

`import { SkyPagingModule } from '@skyux/lists';`

 SkyPagingComponent
-------------------

Type: Component

Selector: `sky-paging`

### Inputs

#### `currentPage: number`

The page number of the current page. Page numbers start at 1 and increment.

Default: `1`

#### `itemCount: number`

The total number of items across all pages.

Default: `0`

#### `maxPages: number`

The maximum number of pages to display in the pagination control.

Default: `5`

#### `pageSize: number`

The number of items to display per page.

Default: `10`

#### `pagingLabel: string | undefined`

The label for the pagination control when an application includes multiple paging components on the same page. The label should be unique and descriptive to help users of assistive technology differentiate pagination controls and understand what each one does.

Default: `"Pagination"`

### Outputs

#### `contentChange: EventEmitter<SkyPagingContentChangeArgs>`

Fires when the current page changes and emits the new current page with a function to call when loading the new page completes. Handling this event will display the wait component until the callback function is called, and focus will move to the top of the list for keyboard navigation if the list contents are placed inside the sky-paging-content element.

#### `currentPageChange: EventEmitter<number>`

Fires when the current page changes and emits the new current page.

 SkyPagingContentComponent
--------------------------

Type: Component

Selector: `sky-paging-content`

 SkyPagingContentChangeArgs
---------------------------

Type: Interface

Information about the paged content to load.

    interface SkyPagingContentChangeArgs {
      currentPage: number;
      loadingComplete: () => void;
    }

### Properties

#### `currentPage: number`

The current page number.

#### `loadingComplete: () => void`

A function to call when loading the paged content completes.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPagingHarness
-----------------

Type: Class

`import { SkyPagingHarness } from '@skyux/lists/testing';`

Harness for interacting with a paging component in tests.

### Methods

#### `clickNextButton(): Promise<void>`

Clicks the next button.

#### Returns

`Promise<void>`

#### `clickPageButton(pageNumber: number): Promise<void>`

Clicks the page button with the requested number. Throws an error if that button is not present.

#### Parameters

##### `pageNumber: number`

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the previous button.

#### Returns

`Promise<void>`

#### `getCurrentPage(): Promise<number>`

Gets the current page number.

#### Returns

`Promise<number>`

#### `getPagingContent(): Promise<SkyPagingContentHarness>`

Gets the paging content.

#### Returns

`Promise<SkyPagingContentHarness>`

#### `getPagingLabel(): Promise<string>`

#### Returns

`Promise<string>`

#### `SkyPagingHarness.with(filters: SkyPagingHarnessFilters): HarnessPredicate<SkyPagingHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPagingHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPagingHarnessFilters`

#### Returns

`HarnessPredicate<SkyPagingHarness>`

 SkyPagingHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

    interface SkyPagingHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPagingContentHarness
------------------------

Type: Class

`import { SkyPagingContentHarness } from '@skyux/lists/testing';`

Harness to interact with a paging content component in tests.

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

Loading page 1

# Development

                  Skip to Main Content

 Paging
======

The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.

 Usage
------

### Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

*   Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
    
*   Avoiding wait times of more than a couple seconds while items load.
    
*   Using less space so that the page composition better communicates the relationship between the list and other elements on the page.
    

### Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use the paging component when a list is presented in a [split view](/skyux/components/split-view.md).

 Anatomy
--------

1

Paging content

2

Previous button

3

Current page

4

Pages

5

Next button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/anatomy-paging.f9c4f00494abd78c1da30d4ceda1cdc6.png)

 Options
--------

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/option-num-pages.e53fa5d3ba28ef91eabe38beb4bf2c46.png)

The number of pages to display can be adjusted.

### Number of items per page

To determine how many items to display per page:

*   Optimize for performance to load items within 2 seconds.
    
*   Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
    
*   Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.
    

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

 Behavior and states
--------------------

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

First page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-first.1ccf8f81a34f02d1fca86b9bdd53084a.png)

The previous button is disabled.

Last page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-last.757a28099837a45311a5f11fd6a6a7b7.png)

The next button is disabled.

Page beyond midpoint

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-midpoint.7b56780bf61dc6ae41c9adc1d83f183e.png)

The selected page maintains a centered position within the pages.

### Loading new items

When users navigate to a new set of items, the list is disabled and a [wait indicator](/skyux/components/wait.md) appears in the paging content area until the new items finish loading.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-waiting.5648a36de13aa33137dc79bed85c23cb.png)

A wait indicator appears while new items load.

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Split view](/skyux/components/split-view.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Filtering lists](/skyux/design/guidelines/filtering-lists.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/paging/paging.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyPagingModule
----------------

Type: Module

`import { SkyPagingModule } from '@skyux/lists';`

 SkyPagingComponent
-------------------

Type: Component

Selector: `sky-paging`

### Inputs

#### `currentPage: number`

The page number of the current page. Page numbers start at 1 and increment.

Default: `1`

#### `itemCount: number`

The total number of items across all pages.

Default: `0`

#### `maxPages: number`

The maximum number of pages to display in the pagination control.

Default: `5`

#### `pageSize: number`

The number of items to display per page.

Default: `10`

#### `pagingLabel: string | undefined`

The label for the pagination control when an application includes multiple paging components on the same page. The label should be unique and descriptive to help users of assistive technology differentiate pagination controls and understand what each one does.

Default: `"Pagination"`

### Outputs

#### `contentChange: EventEmitter<SkyPagingContentChangeArgs>`

Fires when the current page changes and emits the new current page with a function to call when loading the new page completes. Handling this event will display the wait component until the callback function is called, and focus will move to the top of the list for keyboard navigation if the list contents are placed inside the sky-paging-content element.

#### `currentPageChange: EventEmitter<number>`

Fires when the current page changes and emits the new current page.

 SkyPagingContentComponent
--------------------------

Type: Component

Selector: `sky-paging-content`

 SkyPagingContentChangeArgs
---------------------------

Type: Interface

Information about the paged content to load.

    interface SkyPagingContentChangeArgs {
      currentPage: number;
      loadingComplete: () => void;
    }

### Properties

#### `currentPage: number`

The current page number.

#### `loadingComplete: () => void`

A function to call when loading the paged content completes.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPagingHarness
-----------------

Type: Class

`import { SkyPagingHarness } from '@skyux/lists/testing';`

Harness for interacting with a paging component in tests.

### Methods

#### `clickNextButton(): Promise<void>`

Clicks the next button.

#### Returns

`Promise<void>`

#### `clickPageButton(pageNumber: number): Promise<void>`

Clicks the page button with the requested number. Throws an error if that button is not present.

#### Parameters

##### `pageNumber: number`

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the previous button.

#### Returns

`Promise<void>`

#### `getCurrentPage(): Promise<number>`

Gets the current page number.

#### Returns

`Promise<number>`

#### `getPagingContent(): Promise<SkyPagingContentHarness>`

Gets the paging content.

#### Returns

`Promise<SkyPagingContentHarness>`

#### `getPagingLabel(): Promise<string>`

#### Returns

`Promise<string>`

#### `SkyPagingHarness.with(filters: SkyPagingHarnessFilters): HarnessPredicate<SkyPagingHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPagingHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPagingHarnessFilters`

#### Returns

`HarnessPredicate<SkyPagingHarness>`

 SkyPagingHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

    interface SkyPagingHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPagingContentHarness
------------------------

Type: Class

`import { SkyPagingContentHarness } from '@skyux/lists/testing';`

Harness to interact with a paging content component in tests.

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

Loading page 1

# Examples

                    Skip to Main Content

 Paging
======

The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.Usage
------

### Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

*   Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
    
*   Avoiding wait times of more than a couple seconds while items load.
    
*   Using less space so that the page composition better communicates the relationship between the list and other elements on the page.
    

### Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use the paging component when a list is presented in a [split view](/skyux/components/split-view.md).

 Anatomy
--------

1

Paging content

2

Previous button

3

Current page

4

Pages

5

Next button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/anatomy-paging.f9c4f00494abd78c1da30d4ceda1cdc6.png)

 Options
--------

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/option-num-pages.e53fa5d3ba28ef91eabe38beb4bf2c46.png)

The number of pages to display can be adjusted.

### Number of items per page

To determine how many items to display per page:

*   Optimize for performance to load items within 2 seconds.
    
*   Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
    
*   Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.
    

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

 Behavior and states
--------------------

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

First page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-first.1ccf8f81a34f02d1fca86b9bdd53084a.png)

The previous button is disabled.

Last page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-last.757a28099837a45311a5f11fd6a6a7b7.png)

The next button is disabled.

Page beyond midpoint

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-midpoint.7b56780bf61dc6ae41c9adc1d83f183e.png)

The selected page maintains a centered position within the pages.

### Loading new items

When users navigate to a new set of items, the list is disabled and a [wait indicator](/skyux/components/wait.md) appears in the paging content area until the new items finish loading.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-waiting.5648a36de13aa33137dc79bed85c23cb.png)

A wait indicator appears while new items load.

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Split view](/skyux/components/split-view.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Filtering lists](/skyux/design/guidelines/filtering-lists.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/paging/paging.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyPagingModule
----------------

Type: Module

`import { SkyPagingModule } from '@skyux/lists';`

 SkyPagingComponent
-------------------

Type: Component

Selector: `sky-paging`

### Inputs

#### `currentPage: number`

The page number of the current page. Page numbers start at 1 and increment.

Default: `1`

#### `itemCount: number`

The total number of items across all pages.

Default: `0`

#### `maxPages: number`

The maximum number of pages to display in the pagination control.

Default: `5`

#### `pageSize: number`

The number of items to display per page.

Default: `10`

#### `pagingLabel: string | undefined`

The label for the pagination control when an application includes multiple paging components on the same page. The label should be unique and descriptive to help users of assistive technology differentiate pagination controls and understand what each one does.

Default: `"Pagination"`

### Outputs

#### `contentChange: EventEmitter<SkyPagingContentChangeArgs>`

Fires when the current page changes and emits the new current page with a function to call when loading the new page completes. Handling this event will display the wait component until the callback function is called, and focus will move to the top of the list for keyboard navigation if the list contents are placed inside the sky-paging-content element.

#### `currentPageChange: EventEmitter<number>`

Fires when the current page changes and emits the new current page.

 SkyPagingContentComponent
--------------------------

Type: Component

Selector: `sky-paging-content`

 SkyPagingContentChangeArgs
---------------------------

Type: Interface

Information about the paged content to load.

    interface SkyPagingContentChangeArgs {
      currentPage: number;
      loadingComplete: () => void;
    }

### Properties

#### `currentPage: number`

The current page number.

#### `loadingComplete: () => void`

A function to call when loading the paged content completes.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPagingHarness
-----------------

Type: Class

`import { SkyPagingHarness } from '@skyux/lists/testing';`

Harness for interacting with a paging component in tests.

### Methods

#### `clickNextButton(): Promise<void>`

Clicks the next button.

#### Returns

`Promise<void>`

#### `clickPageButton(pageNumber: number): Promise<void>`

Clicks the page button with the requested number. Throws an error if that button is not present.

#### Parameters

##### `pageNumber: number`

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the previous button.

#### Returns

`Promise<void>`

#### `getCurrentPage(): Promise<number>`

Gets the current page number.

#### Returns

`Promise<number>`

#### `getPagingContent(): Promise<SkyPagingContentHarness>`

Gets the paging content.

#### Returns

`Promise<SkyPagingContentHarness>`

#### `getPagingLabel(): Promise<string>`

#### Returns

`Promise<string>`

#### `SkyPagingHarness.with(filters: SkyPagingHarnessFilters): HarnessPredicate<SkyPagingHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPagingHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPagingHarnessFilters`

#### Returns

`HarnessPredicate<SkyPagingHarness>`

 SkyPagingHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

    interface SkyPagingHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPagingContentHarness
------------------------

Type: Class

`import { SkyPagingContentHarness } from '@skyux/lists/testing';`

Harness to interact with a paging content component in tests.

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

### Paging with basic setup

Edit in StackBlitz

*   1
*   2
*   3

The current page is 1.

Show code

Copy

    <sky-paging
      [itemCount]="8"
      [maxPages]="3"
      [pageSize]="2"
      [(currentPage)]="currentPage"
    />
    
    <p>The current page is {{ currentPage }}.</p>

Copy

    import { Component } from '@angular/core';
    import { SkyPagingModule } from '@skyux/lists';
    
    /**
     * @title Paging with basic setup
     */
    @Component({
      selector: 'app-lists-paging-basic-example',
      templateUrl: './example.component.html',
      imports: [SkyPagingModule],
    })
    export class ListsPagingBasicExampleComponent {
      protected currentPage = 1;
    }
### Paging with content wrapper

Edit in StackBlitz

Show code

Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, delay, of } from 'rxjs';
    
    import { DemoData } from './demo-data';
    
    const people = [
      {
        name: 'Abed',
        formal: 'Mr. Nadir',
      },
      {
        name: 'Alex',
        formal: 'Mr. Osbourne',
      },
      {
        name: 'Ben',
        formal: 'Mr. Chang',
      },
      {
        name: 'Britta',
        formal: 'Ms. Perry',
      },
      {
        name: 'Buzz',
        formal: 'Mr. Hickey',
      },
      {
        name: 'Craig',
        formal: 'Mr. Pelton',
      },
      {
        name: 'Elroy',
        formal: 'Mr. Patashnik',
      },
      {
        name: 'Garrett',
        formal: 'Mr. Lambert',
      },
      {
        name: 'Ian',
        formal: 'Mr. Duncan',
      },
      {
        name: 'Jeff',
        formal: 'Mr. Winger',
      },
      {
        name: 'Leonard',
        formal: 'Mr. Rodriguez',
      },
      {
        name: 'Neil',
        formal: 'Mr. Neil',
      },
      {
        name: 'Pierce',
        formal: 'Mr. Hawthorne',
      },
      {
        name: 'Preston',
        formal: 'Mr. Koogler',
      },
      {
        name: 'Rachel',
        formal: 'Ms. Rachel',
      },
      {
        name: 'Shirley',
        formal: 'Ms. Bennett',
      },
      {
        name: 'Todd',
        formal: 'Mr. Jacobson',
      },
      {
        name: 'Troy',
        formal: 'Mr. Barnes',
      },
      {
        name: 'Vaughn',
        formal: 'Mr. Miller',
      },
      {
        name: 'Vicki',
        formal: 'Ms. Jenkins',
      },
    ];
    
    @Injectable({
      providedIn: 'root',
    })
    export class DemoDataService {
      public getPagedData(
        pageNumber: number,
        itemCount: number,
      ): Observable<DemoData> {
        const startIndex = (pageNumber - 1) * itemCount;
    
        return of({
          people: people.slice(startIndex, startIndex + itemCount),
          totalCount: people.length,
        }).pipe(
          // Simulate network latency.
          delay(1000),
        );
      }
    }
Copy

    import { Person } from './person';
    
    export interface DemoData {
      people: Person[];
      totalCount: number;
    }
Copy

    <sky-paging
      data-sky-id="my-paging-content"
      [itemCount]="(pagedData | async)?.totalCount ?? 0"
      [maxPages]="3"
      [pageSize]="pageSize"
      [(currentPage)]="currentPage"
      (contentChange)="contentChange.next($event)"
    >
      <sky-paging-content>
        <sky-repeater>
          @for (person of (pagedData | async)?.people; track person) {
            <sky-repeater-item>
              <sky-repeater-item-title>
                {{ person.name }}
              </sky-repeater-item-title>
              <sky-repeater-item-content>
                <sky-description-list>
                  <sky-description-list-content>
                    <sky-description-list-term>
                      Formal name
                    </sky-description-list-term>
                    <sky-description-list-description>
                      {{ person.formal }}
                    </sky-description-list-description>
                  </sky-description-list-content>
                </sky-description-list>
              </sky-repeater-item-content>
            </sky-repeater-item>
          }
        </sky-repeater>
      </sky-paging-content>
    </sky-paging>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyPagingHarness, SkyRepeaterHarness } from '@skyux/lists/testing';
    
    import { ListsPagingWithContentExampleComponent } from './example.component';
    
    describe('Paging example', () => {
      async function setupTest(
        options: {
          dataSkyId?: string;
        } = {},
      ): Promise<{
        pagingHarness: SkyPagingHarness;
        fixture: ComponentFixture<ListsPagingWithContentExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [ListsPagingWithContentExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          ListsPagingWithContentExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const pagingHarness: SkyPagingHarness = options.dataSkyId
          ? await loader.getHarness(
              SkyPagingHarness.with({
                dataSkyId: options.dataSkyId,
              }),
            )
          : await loader.getHarness(SkyPagingHarness);
    
        return { pagingHarness, fixture };
      }
    
      it('should set up the paging content', async () => {
        const { pagingHarness, fixture } = await setupTest({
          dataSkyId: 'my-paging-content',
        });
    
        await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(1);
    
        const contentHarness = await (
          await pagingHarness.getPagingContent()
        ).queryHarness(SkyRepeaterHarness);
    
        let items = await contentHarness.getRepeaterItems();
    
        await expectAsync(items[0].getTitleText()).toBeResolvedTo('Abed');
    
        await pagingHarness.clickPageButton(3);
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(3);
    
        items = await contentHarness.getRepeaterItems();
    
        await expectAsync(items[0].getTitleText()).toBeResolvedTo('Leonard');
    
        await pagingHarness.clickNextButton();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(4);
    
        items = await contentHarness.getRepeaterItems();
    
        await expectAsync(items[0].getTitleText()).toBeResolvedTo('Shirley');
    
        await expectAsync(pagingHarness.clickNextButton()).toBeRejectedWithError(
          'Could not click the next button because it is disabled.',
        );
    
        await expectAsync(pagingHarness.clickPageButton(1)).toBeRejectedWithError(
          'Could not find page button 1.',
        );
      });
    });
Copy

    export interface Person {
      name: string;
      formal: string;
    }

Copy

    import { CommonModule } from '@angular/common';
    import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
    import { SkyDescriptionListModule } from '@skyux/layout';
    import {
      SkyPagingContentChangeArgs,
      SkyPagingModule,
      SkyRepeaterModule,
    } from '@skyux/lists';
    
    import { Subject, shareReplay, switchMap, tap } from 'rxjs';
    
    import { DemoDataService } from './demo-data.service';
    
    /**
     * @title Paging with content wrapper
     */
    @Component({
      selector: 'app-lists-paging-with-content-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        SkyDescriptionListModule,
        SkyPagingModule,
        SkyRepeaterModule,
      ],
      changeDetection: ChangeDetectionStrategy.OnPush,
    })
    export class ListsPagingWithContentExampleComponent {
      #demoDataSvc = inject(DemoDataService);
    
      protected currentPage = 1;
      protected pageSize = 5;
      protected contentChange = new Subject<SkyPagingContentChangeArgs>();
    
      protected pagedData = this.contentChange.pipe(
        switchMap((args) =>
          this.#demoDataSvc.getPagedData(args.currentPage, this.pageSize).pipe(
            tap(() => {
              args.loadingComplete();
            }),
          ),
        ),
        shareReplay(1),
      );
    }
 

Loading page 1

# Testing

                  Skip to Main Content

 Paging
======

The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.

 Usage
------

### Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

*   Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
    
*   Avoiding wait times of more than a couple seconds while items load.
    
*   Using less space so that the page composition better communicates the relationship between the list and other elements on the page.
    

### Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use the paging component when a list is presented in a [split view](/skyux/components/split-view.md).

 Anatomy
--------

1

Paging content

2

Previous button

3

Current page

4

Pages

5

Next button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/anatomy-paging.f9c4f00494abd78c1da30d4ceda1cdc6.png)

 Options
--------

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/option-num-pages.e53fa5d3ba28ef91eabe38beb4bf2c46.png)

The number of pages to display can be adjusted.

### Number of items per page

To determine how many items to display per page:

*   Optimize for performance to load items within 2 seconds.
    
*   Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
    
*   Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.
    

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

 Behavior and states
--------------------

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

First page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-first.1ccf8f81a34f02d1fca86b9bdd53084a.png)

The previous button is disabled.

Last page

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-last.757a28099837a45311a5f11fd6a6a7b7.png)

The next button is disabled.

Page beyond midpoint

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-midpoint.7b56780bf61dc6ae41c9adc1d83f183e.png)

The selected page maintains a centered position within the pages.

### Loading new items

When users navigate to a new set of items, the list is disabled and a [wait indicator](/skyux/components/wait.md) appears in the paging content area until the new items finish loading.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/paging/behavior-waiting.5648a36de13aa33137dc79bed85c23cb.png)

A wait indicator appears while new items load.

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Split view](/skyux/components/split-view.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Filtering lists](/skyux/design/guidelines/filtering-lists.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/paging/paging.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyPagingModule
----------------

Type: Module

`import { SkyPagingModule } from '@skyux/lists';`

 SkyPagingComponent
-------------------

Type: Component

Selector: `sky-paging`

### Inputs

#### `currentPage: number`

The page number of the current page. Page numbers start at 1 and increment.

Default: `1`

#### `itemCount: number`

The total number of items across all pages.

Default: `0`

#### `maxPages: number`

The maximum number of pages to display in the pagination control.

Default: `5`

#### `pageSize: number`

The number of items to display per page.

Default: `10`

#### `pagingLabel: string | undefined`

The label for the pagination control when an application includes multiple paging components on the same page. The label should be unique and descriptive to help users of assistive technology differentiate pagination controls and understand what each one does.

Default: `"Pagination"`

### Outputs

#### `contentChange: EventEmitter<SkyPagingContentChangeArgs>`

Fires when the current page changes and emits the new current page with a function to call when loading the new page completes. Handling this event will display the wait component until the callback function is called, and focus will move to the top of the list for keyboard navigation if the list contents are placed inside the sky-paging-content element.

#### `currentPageChange: EventEmitter<number>`

Fires when the current page changes and emits the new current page.

 SkyPagingContentComponent
--------------------------

Type: Component

Selector: `sky-paging-content`

 SkyPagingContentChangeArgs
---------------------------

Type: Interface

Information about the paged content to load.

    interface SkyPagingContentChangeArgs {
      currentPage: number;
      loadingComplete: () => void;
    }

### Properties

#### `currentPage: number`

The current page number.

#### `loadingComplete: () => void`

A function to call when loading the paged content completes.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPagingHarness
-----------------

Type: Class

`import { SkyPagingHarness } from '@skyux/lists/testing';`

Harness for interacting with a paging component in tests.

### Methods

#### `clickNextButton(): Promise<void>`

Clicks the next button.

#### Returns

`Promise<void>`

#### `clickPageButton(pageNumber: number): Promise<void>`

Clicks the page button with the requested number. Throws an error if that button is not present.

#### Parameters

##### `pageNumber: number`

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the previous button.

#### Returns

`Promise<void>`

#### `getCurrentPage(): Promise<number>`

Gets the current page number.

#### Returns

`Promise<number>`

#### `getPagingContent(): Promise<SkyPagingContentHarness>`

Gets the paging content.

#### Returns

`Promise<SkyPagingContentHarness>`

#### `getPagingLabel(): Promise<string>`

#### Returns

`Promise<string>`

#### `SkyPagingHarness.with(filters: SkyPagingHarnessFilters): HarnessPredicate<SkyPagingHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPagingHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPagingHarnessFilters`

#### Returns

`HarnessPredicate<SkyPagingHarness>`

 SkyPagingHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

    interface SkyPagingHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPagingContentHarness
------------------------

Type: Class

`import { SkyPagingContentHarness } from '@skyux/lists/testing';`

Harness to interact with a paging content component in tests.

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

Loading page 1
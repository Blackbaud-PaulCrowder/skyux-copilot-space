# Design

                   Skip to Main Content

 Filter
======

Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

 Usage
------

### Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a **Filter** button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the [filtering lists guidelines](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/expandable-filters.8996914281905539abec0afe9f30b26d.png)

Do use expandable inline filters in containers for simple filter controls that won't be used frequently.

### Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use [persistent inline filters](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md) instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/dont-use-for-frequent.753f576bc5784a577f1eaa5a8eec6c39.png)

Don't use expandable inline filters for one or two simple filter controls that users need frequently.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/persistent-inline-filter.7402dc41d714d1b25e8bfeaeed58b6fe.png)

Do use persistent inline filters for one or two simple filter controls that users need frequently.

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a [filter bar](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md) instead to make filters always available and directly selectable.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-expandable.c66b32c2b1ee9de459a449d71c2877ca.png)

Don't use expandable inline filters for full-page lists. Use filter bars instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-filter-bar.dd98f064a90df703d7a34f12a02a38d9.png)

For full-page lists, use a filter bar for filtering.

 Anatomy
--------

1

[Toolbar](/skyux/components/toolbar.md) (transparent)

2

Filter button

3

Expandable filter section (transparent)

4

Simple filters

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/anatomy-expandable-filter.0f18054fa66c30283ccbdb1e427735cb.png)

 Behaviors and states
---------------------

Collapsed

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-collapsed.92f1dbc9ea6c6210a0b5b7eeeae94ea2.png)

Expanded

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded.dee1aec86894529082b3dbfc2fe359f6.png)

Filter on (expanded)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded-on.8079c6f0912cefd63ea5f91264912c8d.png)

 Layout
-------

Filter buttons appear in the toolbar above lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/layout-expandable-filter.12f4dc40fab3160576246cc8549dce2c.png)

 Related information
--------------------

### Components

*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Filter lists](/skyux/design/guidelines/filtering-lists.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/filter/filter.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyFilterModule
----------------

Type: Module

`import { SkyFilterModule } from '@skyux/lists';`

 SkyFilterInlineComponent
-------------------------

Type: Component

Selector: `sky-filter-inline`

Specifies a wrapper for the inline filters.

 SkyFilterInlineItemComponent
-----------------------------

Type: Component

Selector: `sky-filter-inline-item`

Specifies an inline filter.

 SkyFilterSummaryComponent
--------------------------

Type: Component

Selector: `sky-filter-summary`

Specifies a wrapper for the filters that were applied.

 SkyFilterSummaryItemComponent
------------------------------

Type: Component

Selector: `sky-filter-summary-item`

Specifies a filter that was applied.

### Inputs

#### `dismissible: boolean`

Whether the filter summary item has a close button.

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when the summary item close button is selected.

#### `itemClick: EventEmitter<void>`

Fires when the summary item is selected.

 SkyFilterButtonComponent
-------------------------

Type: Component

Selector: `sky-filter-button`

### Inputs

#### `active: boolean | undefined`

Whether to highlight the filter button to indicate that filters were applied. We recommend setting this property to `true` when no indication of filtering is visible to users. For example, set it to `true` if you do not display the filter summary.

Default: `false`

#### `ariaControls: string | undefined`

The ID to identify the element that contains the filtering options that the filter button exposes. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-controls` attribute when using inline filters. For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaExpanded: boolean | undefined`

Whether the filtering options are exposed. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-expanded` attribute when using inline filters. For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded).

Default: `false`

#### `ariaLabel: string | undefined`

The ARIA label for the filter button. This sets the filter button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity. In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `disabled: boolean | undefined`

Whether to disable the filter button.

Default: `false`

#### `filterButtonId: string`

The ID for the filter button.

#### `showButtonText: boolean | undefined`

Whether to display a "Filter" label beside the icon on the filter button.

Default: `false`

### Outputs

#### `filterButtonClick: EventEmitter<void>`

Fires when the filter button is selected.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFilterButtonHarness
-----------------------

Type: Class

`import { SkyFilterButtonHarness } from '@skyux/lists/testing';`

Harness for interacting with a filter button component in tests.

### Methods

#### `clickFilterButton(): Promise<void>`

Clicks the filter button.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Gets the filter button's aria-controls attribute.

#### Returns

`Promise<null | string>`

#### `getAriaExpanded(): Promise<boolean>`

Gets the filter button's aria-expanded attribute.

#### Returns

`Promise<boolean>`

#### `getAriaLabel(): Promise<null | string>`

Gets the filter button's aria-label.

#### Returns

`Promise<null | string>`

#### `getButtonId(): Promise<null | string>`

Gets the filter button's id.

#### Returns

`Promise<null | string>`

#### `getButtonText(): Promise<string>`

Gets the text that appears on the filter button.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the filter button is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the filter button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyFilterButtonHarness.with(filters: SkyFilterButtonHarnessFilters): HarnessPredicate<SkyFilterButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterButtonHarness>`

 SkyFilterButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterButtonHarness` instances.

    interface SkyFilterButtonHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineHarness
-----------------------

Type: Class

`import { SkyFilterInlineHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline component in tests.

### Methods

#### `getItem(filter: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness>`

Gets a specific filter inline item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterInlineItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness>`

#### `getItems(filters?: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness[]>`

Gets an array of filter inline items based on the filter criteria. If no filter is provided, returns all filter inline items.

#### Parameters

##### `filters?: SkyFilterInlineItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness[]>`

#### `SkyFilterInlineHarness.with(filters: SkyFilterInlineHarnessFilters): HarnessPredicate<SkyFilterInlineHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineHarness>`

 SkyFilterInlineHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineHarness` instances.

    interface SkyFilterInlineHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineItemHarness
---------------------------

Type: Class

`import { SkyFilterInlineItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline item component in tests.

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

#### `SkyFilterInlineItemHarness.with(filters: SkyFilterInlineItemHarnessFilters): HarnessPredicate<SkyFilterInlineItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineItemHarness>`

 SkyFilterInlineItemHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineItemHarness` instances.

    interface SkyFilterInlineItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryHarness
------------------------

Type: Class

`import { SkyFilterSummaryHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary component in tests.

### Methods

#### `getItem(filter: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness>`

Gets a specific filter summary item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterSummaryItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness>`

#### `getItems(filters?: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness[]>`

Gets an array of filter summary items based on the filter criteria. If no filter is provided, returns all filter summary items.

#### Parameters

##### `filters?: SkyFilterSummaryItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness[]>`

#### `SkyFilterSummaryHarness.with(filters: SkyFilterSummaryHarnessFilters): HarnessPredicate<SkyFilterSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryHarness>`

 SkyFilterSummaryHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryHarness` instances.

    interface SkyFilterSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryItemHarness
----------------------------

Type: Class

`import { SkyFilterSummaryItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary item component in tests.

### Methods

#### `clickItem(): Promise<void>`

Clicks the filter summary item.

#### Returns

`Promise<void>`

#### `dismiss(): Promise<void>`

Dismisses the filter summary item.

#### Returns

`Promise<void>`

#### `isDismissible(): Promise<boolean>`

Whether the filter summary item is dismissible.

#### Returns

`Promise<boolean>`

#### `SkyFilterSummaryItemHarness.with(filters: SkyFilterSummaryItemHarnessFilters): HarnessPredicate<SkyFilterSummaryItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryItemHarness>`

 SkyFilterSummaryItemHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryItemHarness` instances.

    interface SkyFilterSummaryItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                   Skip to Main Content

 Filter
======

Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

 Usage
------

### Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a **Filter** button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the [filtering lists guidelines](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/expandable-filters.8996914281905539abec0afe9f30b26d.png)

Do use expandable inline filters in containers for simple filter controls that won't be used frequently.

### Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use [persistent inline filters](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md) instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/dont-use-for-frequent.753f576bc5784a577f1eaa5a8eec6c39.png)

Don't use expandable inline filters for one or two simple filter controls that users need frequently.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/persistent-inline-filter.7402dc41d714d1b25e8bfeaeed58b6fe.png)

Do use persistent inline filters for one or two simple filter controls that users need frequently.

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a [filter bar](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md) instead to make filters always available and directly selectable.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-expandable.c66b32c2b1ee9de459a449d71c2877ca.png)

Don't use expandable inline filters for full-page lists. Use filter bars instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-filter-bar.dd98f064a90df703d7a34f12a02a38d9.png)

For full-page lists, use a filter bar for filtering.

 Anatomy
--------

1

[Toolbar](/skyux/components/toolbar.md) (transparent)

2

Filter button

3

Expandable filter section (transparent)

4

Simple filters

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/anatomy-expandable-filter.0f18054fa66c30283ccbdb1e427735cb.png)

 Behaviors and states
---------------------

Collapsed

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-collapsed.92f1dbc9ea6c6210a0b5b7eeeae94ea2.png)

Expanded

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded.dee1aec86894529082b3dbfc2fe359f6.png)

Filter on (expanded)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded-on.8079c6f0912cefd63ea5f91264912c8d.png)

 Layout
-------

Filter buttons appear in the toolbar above lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/layout-expandable-filter.12f4dc40fab3160576246cc8549dce2c.png)

 Related information
--------------------

### Components

*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Filter lists](/skyux/design/guidelines/filtering-lists.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/filter/filter.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyFilterModule
----------------

Type: Module

`import { SkyFilterModule } from '@skyux/lists';`

 SkyFilterInlineComponent
-------------------------

Type: Component

Selector: `sky-filter-inline`

Specifies a wrapper for the inline filters.

 SkyFilterInlineItemComponent
-----------------------------

Type: Component

Selector: `sky-filter-inline-item`

Specifies an inline filter.

 SkyFilterSummaryComponent
--------------------------

Type: Component

Selector: `sky-filter-summary`

Specifies a wrapper for the filters that were applied.

 SkyFilterSummaryItemComponent
------------------------------

Type: Component

Selector: `sky-filter-summary-item`

Specifies a filter that was applied.

### Inputs

#### `dismissible: boolean`

Whether the filter summary item has a close button.

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when the summary item close button is selected.

#### `itemClick: EventEmitter<void>`

Fires when the summary item is selected.

 SkyFilterButtonComponent
-------------------------

Type: Component

Selector: `sky-filter-button`

### Inputs

#### `active: boolean | undefined`

Whether to highlight the filter button to indicate that filters were applied. We recommend setting this property to `true` when no indication of filtering is visible to users. For example, set it to `true` if you do not display the filter summary.

Default: `false`

#### `ariaControls: string | undefined`

The ID to identify the element that contains the filtering options that the filter button exposes. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-controls` attribute when using inline filters. For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaExpanded: boolean | undefined`

Whether the filtering options are exposed. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-expanded` attribute when using inline filters. For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded).

Default: `false`

#### `ariaLabel: string | undefined`

The ARIA label for the filter button. This sets the filter button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity. In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `disabled: boolean | undefined`

Whether to disable the filter button.

Default: `false`

#### `filterButtonId: string`

The ID for the filter button.

#### `showButtonText: boolean | undefined`

Whether to display a "Filter" label beside the icon on the filter button.

Default: `false`

### Outputs

#### `filterButtonClick: EventEmitter<void>`

Fires when the filter button is selected.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFilterButtonHarness
-----------------------

Type: Class

`import { SkyFilterButtonHarness } from '@skyux/lists/testing';`

Harness for interacting with a filter button component in tests.

### Methods

#### `clickFilterButton(): Promise<void>`

Clicks the filter button.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Gets the filter button's aria-controls attribute.

#### Returns

`Promise<null | string>`

#### `getAriaExpanded(): Promise<boolean>`

Gets the filter button's aria-expanded attribute.

#### Returns

`Promise<boolean>`

#### `getAriaLabel(): Promise<null | string>`

Gets the filter button's aria-label.

#### Returns

`Promise<null | string>`

#### `getButtonId(): Promise<null | string>`

Gets the filter button's id.

#### Returns

`Promise<null | string>`

#### `getButtonText(): Promise<string>`

Gets the text that appears on the filter button.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the filter button is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the filter button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyFilterButtonHarness.with(filters: SkyFilterButtonHarnessFilters): HarnessPredicate<SkyFilterButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterButtonHarness>`

 SkyFilterButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterButtonHarness` instances.

    interface SkyFilterButtonHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineHarness
-----------------------

Type: Class

`import { SkyFilterInlineHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline component in tests.

### Methods

#### `getItem(filter: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness>`

Gets a specific filter inline item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterInlineItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness>`

#### `getItems(filters?: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness[]>`

Gets an array of filter inline items based on the filter criteria. If no filter is provided, returns all filter inline items.

#### Parameters

##### `filters?: SkyFilterInlineItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness[]>`

#### `SkyFilterInlineHarness.with(filters: SkyFilterInlineHarnessFilters): HarnessPredicate<SkyFilterInlineHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineHarness>`

 SkyFilterInlineHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineHarness` instances.

    interface SkyFilterInlineHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineItemHarness
---------------------------

Type: Class

`import { SkyFilterInlineItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline item component in tests.

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

#### `SkyFilterInlineItemHarness.with(filters: SkyFilterInlineItemHarnessFilters): HarnessPredicate<SkyFilterInlineItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineItemHarness>`

 SkyFilterInlineItemHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineItemHarness` instances.

    interface SkyFilterInlineItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryHarness
------------------------

Type: Class

`import { SkyFilterSummaryHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary component in tests.

### Methods

#### `getItem(filter: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness>`

Gets a specific filter summary item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterSummaryItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness>`

#### `getItems(filters?: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness[]>`

Gets an array of filter summary items based on the filter criteria. If no filter is provided, returns all filter summary items.

#### Parameters

##### `filters?: SkyFilterSummaryItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness[]>`

#### `SkyFilterSummaryHarness.with(filters: SkyFilterSummaryHarnessFilters): HarnessPredicate<SkyFilterSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryHarness>`

 SkyFilterSummaryHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryHarness` instances.

    interface SkyFilterSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryItemHarness
----------------------------

Type: Class

`import { SkyFilterSummaryItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary item component in tests.

### Methods

#### `clickItem(): Promise<void>`

Clicks the filter summary item.

#### Returns

`Promise<void>`

#### `dismiss(): Promise<void>`

Dismisses the filter summary item.

#### Returns

`Promise<void>`

#### `isDismissible(): Promise<boolean>`

Whether the filter summary item is dismissible.

#### Returns

`Promise<boolean>`

#### `SkyFilterSummaryItemHarness.with(filters: SkyFilterSummaryItemHarnessFilters): HarnessPredicate<SkyFilterSummaryItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryItemHarness>`

 SkyFilterSummaryItemHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryItemHarness` instances.

    interface SkyFilterSummaryItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                   Skip to Main Content

 Filter
======

Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

 Usage
------

### Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a **Filter** button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the [filtering lists guidelines](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/expandable-filters.8996914281905539abec0afe9f30b26d.png)

Do use expandable inline filters in containers for simple filter controls that won't be used frequently.

### Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use [persistent inline filters](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md) instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/dont-use-for-frequent.753f576bc5784a577f1eaa5a8eec6c39.png)

Don't use expandable inline filters for one or two simple filter controls that users need frequently.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/persistent-inline-filter.7402dc41d714d1b25e8bfeaeed58b6fe.png)

Do use persistent inline filters for one or two simple filter controls that users need frequently.

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a [filter bar](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md) instead to make filters always available and directly selectable.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-expandable.c66b32c2b1ee9de459a449d71c2877ca.png)

Don't use expandable inline filters for full-page lists. Use filter bars instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-filter-bar.dd98f064a90df703d7a34f12a02a38d9.png)

For full-page lists, use a filter bar for filtering.

 Anatomy
--------

1

[Toolbar](/skyux/components/toolbar.md) (transparent)

2

Filter button

3

Expandable filter section (transparent)

4

Simple filters

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/anatomy-expandable-filter.0f18054fa66c30283ccbdb1e427735cb.png)

 Behaviors and states
---------------------

Collapsed

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-collapsed.92f1dbc9ea6c6210a0b5b7eeeae94ea2.png)

Expanded

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded.dee1aec86894529082b3dbfc2fe359f6.png)

Filter on (expanded)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded-on.8079c6f0912cefd63ea5f91264912c8d.png)

 Layout
-------

Filter buttons appear in the toolbar above lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/layout-expandable-filter.12f4dc40fab3160576246cc8549dce2c.png)

 Related information
--------------------

### Components

*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Filter lists](/skyux/design/guidelines/filtering-lists.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/filter/filter.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyFilterModule
----------------

Type: Module

`import { SkyFilterModule } from '@skyux/lists';`

 SkyFilterInlineComponent
-------------------------

Type: Component

Selector: `sky-filter-inline`

Specifies a wrapper for the inline filters.

 SkyFilterInlineItemComponent
-----------------------------

Type: Component

Selector: `sky-filter-inline-item`

Specifies an inline filter.

 SkyFilterSummaryComponent
--------------------------

Type: Component

Selector: `sky-filter-summary`

Specifies a wrapper for the filters that were applied.

 SkyFilterSummaryItemComponent
------------------------------

Type: Component

Selector: `sky-filter-summary-item`

Specifies a filter that was applied.

### Inputs

#### `dismissible: boolean`

Whether the filter summary item has a close button.

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when the summary item close button is selected.

#### `itemClick: EventEmitter<void>`

Fires when the summary item is selected.

 SkyFilterButtonComponent
-------------------------

Type: Component

Selector: `sky-filter-button`

### Inputs

#### `active: boolean | undefined`

Whether to highlight the filter button to indicate that filters were applied. We recommend setting this property to `true` when no indication of filtering is visible to users. For example, set it to `true` if you do not display the filter summary.

Default: `false`

#### `ariaControls: string | undefined`

The ID to identify the element that contains the filtering options that the filter button exposes. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-controls` attribute when using inline filters. For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaExpanded: boolean | undefined`

Whether the filtering options are exposed. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-expanded` attribute when using inline filters. For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded).

Default: `false`

#### `ariaLabel: string | undefined`

The ARIA label for the filter button. This sets the filter button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity. In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `disabled: boolean | undefined`

Whether to disable the filter button.

Default: `false`

#### `filterButtonId: string`

The ID for the filter button.

#### `showButtonText: boolean | undefined`

Whether to display a "Filter" label beside the icon on the filter button.

Default: `false`

### Outputs

#### `filterButtonClick: EventEmitter<void>`

Fires when the filter button is selected.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFilterButtonHarness
-----------------------

Type: Class

`import { SkyFilterButtonHarness } from '@skyux/lists/testing';`

Harness for interacting with a filter button component in tests.

### Methods

#### `clickFilterButton(): Promise<void>`

Clicks the filter button.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Gets the filter button's aria-controls attribute.

#### Returns

`Promise<null | string>`

#### `getAriaExpanded(): Promise<boolean>`

Gets the filter button's aria-expanded attribute.

#### Returns

`Promise<boolean>`

#### `getAriaLabel(): Promise<null | string>`

Gets the filter button's aria-label.

#### Returns

`Promise<null | string>`

#### `getButtonId(): Promise<null | string>`

Gets the filter button's id.

#### Returns

`Promise<null | string>`

#### `getButtonText(): Promise<string>`

Gets the text that appears on the filter button.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the filter button is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the filter button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyFilterButtonHarness.with(filters: SkyFilterButtonHarnessFilters): HarnessPredicate<SkyFilterButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterButtonHarness>`

 SkyFilterButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterButtonHarness` instances.

    interface SkyFilterButtonHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineHarness
-----------------------

Type: Class

`import { SkyFilterInlineHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline component in tests.

### Methods

#### `getItem(filter: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness>`

Gets a specific filter inline item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterInlineItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness>`

#### `getItems(filters?: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness[]>`

Gets an array of filter inline items based on the filter criteria. If no filter is provided, returns all filter inline items.

#### Parameters

##### `filters?: SkyFilterInlineItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness[]>`

#### `SkyFilterInlineHarness.with(filters: SkyFilterInlineHarnessFilters): HarnessPredicate<SkyFilterInlineHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineHarness>`

 SkyFilterInlineHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineHarness` instances.

    interface SkyFilterInlineHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineItemHarness
---------------------------

Type: Class

`import { SkyFilterInlineItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline item component in tests.

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

#### `SkyFilterInlineItemHarness.with(filters: SkyFilterInlineItemHarnessFilters): HarnessPredicate<SkyFilterInlineItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineItemHarness>`

 SkyFilterInlineItemHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineItemHarness` instances.

    interface SkyFilterInlineItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryHarness
------------------------

Type: Class

`import { SkyFilterSummaryHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary component in tests.

### Methods

#### `getItem(filter: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness>`

Gets a specific filter summary item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterSummaryItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness>`

#### `getItems(filters?: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness[]>`

Gets an array of filter summary items based on the filter criteria. If no filter is provided, returns all filter summary items.

#### Parameters

##### `filters?: SkyFilterSummaryItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness[]>`

#### `SkyFilterSummaryHarness.with(filters: SkyFilterSummaryHarnessFilters): HarnessPredicate<SkyFilterSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryHarness>`

 SkyFilterSummaryHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryHarness` instances.

    interface SkyFilterSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryItemHarness
----------------------------

Type: Class

`import { SkyFilterSummaryItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary item component in tests.

### Methods

#### `clickItem(): Promise<void>`

Clicks the filter summary item.

#### Returns

`Promise<void>`

#### `dismiss(): Promise<void>`

Dismisses the filter summary item.

#### Returns

`Promise<void>`

#### `isDismissible(): Promise<boolean>`

Whether the filter summary item is dismissible.

#### Returns

`Promise<boolean>`

#### `SkyFilterSummaryItemHarness.with(filters: SkyFilterSummaryItemHarnessFilters): HarnessPredicate<SkyFilterSummaryItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryItemHarness>`

 SkyFilterSummaryItemHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryItemHarness` instances.

    interface SkyFilterSummaryItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Testing

                   Skip to Main Content

 Filter
======

Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

 Usage
------

### Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a **Filter** button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the [filtering lists guidelines](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/expandable-filters.8996914281905539abec0afe9f30b26d.png)

Do use expandable inline filters in containers for simple filter controls that won't be used frequently.

### Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use [persistent inline filters](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md) instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/dont-use-for-frequent.753f576bc5784a577f1eaa5a8eec6c39.png)

Don't use expandable inline filters for one or two simple filter controls that users need frequently.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/persistent-inline-filter.7402dc41d714d1b25e8bfeaeed58b6fe.png)

Do use persistent inline filters for one or two simple filter controls that users need frequently.

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a [filter bar](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md) instead to make filters always available and directly selectable.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-expandable.c66b32c2b1ee9de459a449d71c2877ca.png)

Don't use expandable inline filters for full-page lists. Use filter bars instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/full-page-filter-bar.dd98f064a90df703d7a34f12a02a38d9.png)

For full-page lists, use a filter bar for filtering.

 Anatomy
--------

1

[Toolbar](/skyux/components/toolbar.md) (transparent)

2

Filter button

3

Expandable filter section (transparent)

4

Simple filters

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/anatomy-expandable-filter.0f18054fa66c30283ccbdb1e427735cb.png)

 Behaviors and states
---------------------

Collapsed

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-collapsed.92f1dbc9ea6c6210a0b5b7eeeae94ea2.png)

Expanded

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded.dee1aec86894529082b3dbfc2fe359f6.png)

Filter on (expanded)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/state-expanded-on.8079c6f0912cefd63ea5f91264912c8d.png)

 Layout
-------

Filter buttons appear in the toolbar above lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter/layout-expandable-filter.12f4dc40fab3160576246cc8549dce2c.png)

 Related information
--------------------

### Components

*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Filter lists](/skyux/design/guidelines/filtering-lists.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/filter/filter.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyFilterModule
----------------

Type: Module

`import { SkyFilterModule } from '@skyux/lists';`

 SkyFilterInlineComponent
-------------------------

Type: Component

Selector: `sky-filter-inline`

Specifies a wrapper for the inline filters.

 SkyFilterInlineItemComponent
-----------------------------

Type: Component

Selector: `sky-filter-inline-item`

Specifies an inline filter.

 SkyFilterSummaryComponent
--------------------------

Type: Component

Selector: `sky-filter-summary`

Specifies a wrapper for the filters that were applied.

 SkyFilterSummaryItemComponent
------------------------------

Type: Component

Selector: `sky-filter-summary-item`

Specifies a filter that was applied.

### Inputs

#### `dismissible: boolean`

Whether the filter summary item has a close button.

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when the summary item close button is selected.

#### `itemClick: EventEmitter<void>`

Fires when the summary item is selected.

 SkyFilterButtonComponent
-------------------------

Type: Component

Selector: `sky-filter-button`

### Inputs

#### `active: boolean | undefined`

Whether to highlight the filter button to indicate that filters were applied. We recommend setting this property to `true` when no indication of filtering is visible to users. For example, set it to `true` if you do not display the filter summary.

Default: `false`

#### `ariaControls: string | undefined`

The ID to identify the element that contains the filtering options that the filter button exposes. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-controls` attribute when using inline filters. For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaExpanded: boolean | undefined`

Whether the filtering options are exposed. To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure), this property is necessary to set the `aria-expanded` attribute when using inline filters. For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded).

Default: `false`

#### `ariaLabel: string | undefined`

The ARIA label for the filter button. This sets the filter button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity. In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `disabled: boolean | undefined`

Whether to disable the filter button.

Default: `false`

#### `filterButtonId: string`

The ID for the filter button.

#### `showButtonText: boolean | undefined`

Whether to display a "Filter" label beside the icon on the filter button.

Default: `false`

### Outputs

#### `filterButtonClick: EventEmitter<void>`

Fires when the filter button is selected.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFilterButtonHarness
-----------------------

Type: Class

`import { SkyFilterButtonHarness } from '@skyux/lists/testing';`

Harness for interacting with a filter button component in tests.

### Methods

#### `clickFilterButton(): Promise<void>`

Clicks the filter button.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Gets the filter button's aria-controls attribute.

#### Returns

`Promise<null | string>`

#### `getAriaExpanded(): Promise<boolean>`

Gets the filter button's aria-expanded attribute.

#### Returns

`Promise<boolean>`

#### `getAriaLabel(): Promise<null | string>`

Gets the filter button's aria-label.

#### Returns

`Promise<null | string>`

#### `getButtonId(): Promise<null | string>`

Gets the filter button's id.

#### Returns

`Promise<null | string>`

#### `getButtonText(): Promise<string>`

Gets the text that appears on the filter button.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the filter button is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the filter button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyFilterButtonHarness.with(filters: SkyFilterButtonHarnessFilters): HarnessPredicate<SkyFilterButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterButtonHarness>`

 SkyFilterButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterButtonHarness` instances.

    interface SkyFilterButtonHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineHarness
-----------------------

Type: Class

`import { SkyFilterInlineHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline component in tests.

### Methods

#### `getItem(filter: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness>`

Gets a specific filter inline item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterInlineItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness>`

#### `getItems(filters?: SkyFilterInlineItemHarnessFilters): Promise<SkyFilterInlineItemHarness[]>`

Gets an array of filter inline items based on the filter criteria. If no filter is provided, returns all filter inline items.

#### Parameters

##### `filters?: SkyFilterInlineItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterInlineItemHarness[]>`

#### `SkyFilterInlineHarness.with(filters: SkyFilterInlineHarnessFilters): HarnessPredicate<SkyFilterInlineHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineHarness>`

 SkyFilterInlineHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineHarness` instances.

    interface SkyFilterInlineHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterInlineItemHarness
---------------------------

Type: Class

`import { SkyFilterInlineItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter inline item component in tests.

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

#### `SkyFilterInlineItemHarness.with(filters: SkyFilterInlineItemHarnessFilters): HarnessPredicate<SkyFilterInlineItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterInlineItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterInlineItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterInlineItemHarness>`

 SkyFilterInlineItemHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterInlineItemHarness` instances.

    interface SkyFilterInlineItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryHarness
------------------------

Type: Class

`import { SkyFilterSummaryHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary component in tests.

### Methods

#### `getItem(filter: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness>`

Gets a specific filter summary item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterSummaryItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness>`

#### `getItems(filters?: SkyFilterSummaryItemHarnessFilters): Promise<SkyFilterSummaryItemHarness[]>`

Gets an array of filter summary items based on the filter criteria. If no filter is provided, returns all filter summary items.

#### Parameters

##### `filters?: SkyFilterSummaryItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterSummaryItemHarness[]>`

#### `SkyFilterSummaryHarness.with(filters: SkyFilterSummaryHarnessFilters): HarnessPredicate<SkyFilterSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryHarness>`

 SkyFilterSummaryHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryHarness` instances.

    interface SkyFilterSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterSummaryItemHarness
----------------------------

Type: Class

`import { SkyFilterSummaryItemHarness } from '@skyux/lists/testing';`

Harness to interact with a filter summary item component in tests.

### Methods

#### `clickItem(): Promise<void>`

Clicks the filter summary item.

#### Returns

`Promise<void>`

#### `dismiss(): Promise<void>`

Dismisses the filter summary item.

#### Returns

`Promise<void>`

#### `isDismissible(): Promise<boolean>`

Whether the filter summary item is dismissible.

#### Returns

`Promise<boolean>`

#### `SkyFilterSummaryItemHarness.with(filters: SkyFilterSummaryItemHarnessFilters): HarnessPredicate<SkyFilterSummaryItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterSummaryItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterSummaryItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterSummaryItemHarness>`

 SkyFilterSummaryItemHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterSummaryItemHarness` instances.

    interface SkyFilterSummaryItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
                   

 Filter bar
==========

The filter bar presents users with inline filter options to narrow lists. It allows for a large number of filter options.

The filter bar component does not currently integrate the [data manager](/skyux/components/data-manager.md) component, but integration is coming soon.

 Usage
------

### Use when

Use the filter bar when the main or only task on a page is to narrow a collection of items or manipulate a pre-filtered collection. Use a filter bar or tabs to support the [filtering tasks](/skyux/design/guidelines/filtering-lists.md) on dedicated full-page lists, such as [list pages](/skyux/design/guidelines/page-layouts/list-page.md) or in tabs on [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/full-page-context.9eb411599b85fa6f4db8d7bd047c56ca.png)

Do use the filter bar with full-page lists on list pages.

Use the filter bar with pre-filtered lists where filters are already active when:

*   Users need to adjust preset filter values or add additional filters to refine lists.
*   Users access lists through calls to action and need to further narrow the lists before taking action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/pre-filtered-bar.f07731a9eaf12f820440ca81321a7e81.png)

Do use the filter bar with pre-filtered lists to make workflows more efficient. Users can narrow lists further as necessary.

### Don't use when

Don't use the filter bar when:

*   Users need regular access to a small number of lists.
*   One list in a small group of lists needs priority or will be used most frequently.
*   A small number of lists have different tasks for users to complete.

Use pre-filtered lists in [tabs](/skyux/components/tabs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/tab-filters-do.a85b9657b36b424fb17d4181a0055b86.png)

Do use tabs to support easy access to a few pre-filtered lists.

 Anatomy
--------

1

Toolbar divider

2

Filter bar label

3

Filter button (filter not set)

4

Filter button (filter set)

5

Clear filters button

6

Filter chooser button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filter-bar/filter-bar-anatomy.2e8c9fa059ba767aa86d25f5ebbcfc97.png)

 Options
--------

### Filter chooser

When a list requires many filters to give users multiple ways to narrow the collection of items, include a filter chooser to let users select the filters to include in the filter bar.

Within filter choosers, organize filters alphabetically. If some filters will be used most of the time, include them directly in the filter bar by default.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/option-filter-chooser.791b82ee4c3464915407872ef65f3dda.png)

The filter chooser button opens a modal to select the filters to enable in the filter bar.

 Behavior and states
--------------------

### Filter types

The filter bar can support multiple types of selection methods for filtering. Use the following filter types for selection and display of filters in the filter bar.

Lookup or categorical

Lookup or categorical filters support the selection of one or multiple values.

Include operators in the initial Filter by input. The pattern supports operators such as:

*   Any of these values
*   None of these values
*   No value
*   Any value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-lookup.1a9278da381d0c49f15a48539b935409.png)

Lookup button filter values

Any of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-any.27889be69557881bcaf2dde261d1502a.png)

None of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-none.7837b1a2f0caba449b606e9846eae91b.png)

No value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-no-value.ff7b280c08299aebf380887ab2f4023b.png)

Any value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-any-value.87cf1e67e34f745832cbe97743dae792.png)

Numeric

Numeric filters allow users to narrow down numeric or currency amounts.

Include operators in the initial Filter to input. The pattern supports various operators that you should customize for your scenario:

*   Equal to
*   Does not equal
*   Greater than or equal to
*   Greater than
*   Less than or equal to
*   Less than
*   Between

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-num.dcc604a92042e9436060156379343c59.png)

Numeric button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-num-one.56174979ae5a8e859852d6afafc8cb12.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-num-two.00834ba12aa1d50f641d0d6599f65ec2.png)

Boolean

For boolean filters, determine the appropriate default state based on the workflows that lists support. For example, decide whether to display all contacts in a list by default or only the active contacts that users are most likely to work with. This determines the available filter options.

### Display all items

When a list displays all items by default, users can filter the list to display only one boolean value. For example, they can filter to only display active or inactive list items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-bool-all.0be4e38192ef008af9e7217ba6caaed8.png)

Boolean button filter values

Default (All items displayed)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-all.e07d07d7949531e2323e4444206986ba.png)

Filter set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-all-set.8773c24fa6dc980fca321aca42bced3c.png)

### Display items with boolean value

When a list only displays items with a boolean value by default, users can filter to display the other boolean value. For example, they can switch from active list items to inactive items.

Use this filter when the majority of workflows for lists apply to the subset of items with a boolean value.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-bool-value.25bfdc5a633bed8d7f51f4b38c7ec01c.png)

Boolean button filter values

Default (One boolean displayed)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-value-default.e07d07d7949531e2323e4444206986ba.png)

Filter set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-value-set.75c1862f7548492862fa09be8b6878f4.png)

Date

Date filters allow users to filter based on a specific date.

Include operators in the initial Filter to input. This pattern supports various operators that you should customize for your scenario.

*   After
*   Before
*   Specific range
*   Yesterday
*   Today
*   Tomorrow
*   Last week
*   This week
*   Next week
*   Last month
*   This month
*   Next month
*   Last quarter
*   This quarter
*   Next quarter
*   Last calendar year
*   This calendar year
*   Next calendar year
*   Last fiscal year
*   This fiscal year
*   Next fiscal year
*   Last N days
*   Next N days
*   Any value
*   No value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-date.7f7378c82bafbcdb382ef9cf6833772c.png)

Date button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-one.71cf68e602ef48b18cd428e76c60f2aa.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-two.b31bd21669ab738fdbd5f10f05ad2aa7.png)

Fuzzy dates

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-fuzzy.3dfac838e827e668a0ebe339db4d3688.png)

Month-day

Month-day filters allow users to set a filter based on dates without specifying a year.

Include operators in the initial Filter to input similar to a date filter.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-month-day.727c3f5289daccbf47ff2deb38a90935.png)

Month-day button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-month-one.64fe292aa0f18d737ceb1f060e33a181.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-month-two.092f567788ce8766e36fe1675455d5e9.png)

Text

Text filters allow users to filter based on a string of text.

Include operators in the initial Filter to input. This pattern supports various operators that you should customize for your scenario.

*   Equal to
*   Does not equal
*   Blank
*   Not blank
*   Starts with
*   Does not start with
*   Any of these values
*   None of these values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-text.3d91e960b61c0845ecb1741effcf513a.png)

Text button filter values

Operators

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-ops.894a2dd01512ae669aa8020fb9bc2236.png)

Blank or Not blank

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-blank.5ea1e0424335281fd3e7859f2141acee.png)

Any of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-any.d025bc6a3124283b4e5a14644f645303.png)

None of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-none.bab1c93366afaff5a77805e0126c400f.png)

### Clear all values

When users select **Clear all values**, confirm their intention with a [confirmation modal](/skyux/components/confirm.md) before removing the filter values to avoid losing their work by mistake.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/clearing-filters.89fc5ebcfc1f3a20bb14005cc221ae51.png)

### Updates to summary details

When filters or search criteria are applied to a list, update the list count and summary details to reflect the filtered list. Add "match" to the list count label to reflect the list is in a filtered state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filtered-list-count.769d0cd8c574c061bb42292676159f41.png)

Do update summary details when filters or search criteria are applied to a list. To provide context, update the list count label to include 'match.'

 Content
--------

When displaying filters in the filter bar by default, organize them in descending order of importance based on the tasks that users will perform. Place the most important or most frequently used filters first.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/filter-bar`[View in NPM](https://www.npmjs.com/package/@skyux/filter-bar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/filter-bar/src/lib/modules/filter-bar/filter-bar.module.ts#L19) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/filter-bar`Copy None found.

 SkyFilterBarModule
-------------------

Type: Module

`import { SkyFilterBarModule } from '@skyux/filter-bar';`

 SkyFilterBarComponent
----------------------

Type: Component

Selector: `sky-filter-bar`

The top-level filter bar component.

### Inputs

#### `appliedFilters: ModelSignal<undefined | SkyFilterBarFilterItem[]>`

An array of filter items containing the IDs and values of the filters that have been set.

#### `selectedFilterIds: ModelSignal<undefined | string[]>`

An array of filter IDs that the user has selected using the built-in selection modal. Setting this input to undefined results in all filters being displayed.

 SkyFilterBarFilterItem
-----------------------

Type: Interface

Represents a specific filter item and its selected value, if any.

    interface SkyFilterBarFilterItem {
      filterId: string;
      filterValue?: SkyFilterBarFilterValue;
    }

### Properties

#### `filterId: string`

A unique identifier for the filter item.

#### `filterValue?: SkyFilterBarFilterValue`

The value of the filter item.

 SkyFilterBarFilterValue
------------------------

Type: Interface

Represents a value for a filter item.

    interface SkyFilterBarFilterValue {
      displayValue?: string;
      value: unknown;
    }

### Properties

#### `displayValue?: string`

A human-readable string for use with values that can't be displayed to the user.

#### `value: unknown`

The real value for the filter.

 SkyFilterItemLookupComponent
-----------------------------

Type: Component

Selector: `sky-filter-item-lookup`

A filter bar item that opens a selection modal for complex filter configuration. Use this component for lookup-type filter fields where users select one or more options from a list of values.

### Inputs

#### `filterId: InputSignal<string>`

Required

A unique identifier for the filter item.

#### `labelText: InputSignal<string>`

Required

The label to display for the filter item.

#### `searchDescriptorProperty: InputSignal<string>`

Required

The object property to display for each filter value in the selection modal when users open the filter.

#### `searchIdProperty: InputSignal<string>`

Required

The object property that represents a unique identifier for each filter value in the selection modal when users open the filter.

### Outputs

#### `searchAsync: EventEmitter<SkyFilterItemLookupSearchAsyncArgs>`

Fires when users enter search information and allows results to be returned via an observable. The event also fires with empty search text when the filter is opened.

 SkyFilterItemLookupSearchAsyncArgs
-----------------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the selection modal opened by a filter item lookup component.

    interface SkyFilterItemLookupSearchAsyncArgs {
      continuationData?: unknown;
      filterId: string;
      offset: number;
      result?: Observable<SkyFilterItemLookupSearchAsyncResult>;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token that can be set and then passed back with any future searches. This is helpful for applications that use a token to fetch data instead of an offset.

#### `filterId: string`

The unique identifier for the filter.

#### `offset: number`

The offset index of the first result to return. For example, when search is executed as a result of an infinite scroll event, the offset is set to the number of items already displayed.

#### `result?: Observable<SkyFilterItemLookupSearchAsyncResult>`

An observable that represents the search results. Consumers should set this when the event fires so the filter item lookup component can subscribe to it and then display the results.

#### `searchText: string`

The search text entered by the user.

 SkyFilterItemLookupSearchAsyncResult
-------------------------------------

Type: Interface

The result of searching for items to display in a filter item lookup selection modal.

    interface SkyFilterItemLookupSearchAsyncResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items that match the search criteria. When more items match the search criteria, set the `hasMore` property to `true`. More records can be lazy-loaded as users scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list.

 SkyFilterItemModalComponent
----------------------------

Type: Component

Selector: `sky-filter-item-modal`

A filter bar item that opens a modal for complex filter configuration. Use this component when your filter requires a rich UI with multiple inputs, date pickers, or other complex controls that don't fit in an inline filter.

### Inputs

#### `filterId: InputSignal<string>`

Required

A unique identifier for the filter item.

#### `labelText: InputSignal<string>`

Required

The label to display for the filter item.

#### `modalComponent: InputSignal<Type<SkyFilterItemModal<TData>>>`

Required

The modal component to display when the user selects the filter. The component needs to inject a `SkyFilterItemModalInstance` object on instantiation to receive the modal instance and context from the modal service. The return value of the modal save action needs to be a `SkyFilterBarFilterValue`.

#### `modalSize: InputSignal<SkyFilterItemModalSizeType>`

The size of the modal to display. The valid options are `"small"`, `"medium"`, `"large"`, and `"fullScreen"`.

### Outputs

#### `modalOpened: EventEmitter<SkyFilterItemModalOpenedArgs<TData>>`

Fires when the user clicks the filter item. To pass additional context data to a filter modal, consumers must subscribe to this event and return the context using the observable property on the event args.

 SkyFilterItemModal
-------------------

Type: Interface

A type marker for passing context object data types into the filter modal component.

    interface SkyFilterItemModal {
      modalInstance: SkyFilterItemModalInstance<TData>;
    }

### Properties

#### `modalInstance: SkyFilterItemModalInstance<TData>`

The filter modal instance to be injected into the component.

 SkyFilterItemModalInstance
---------------------------

Type: Class

A specialized `SkyModalInstance` wrapper.

### Properties

#### `context: SkyFilterItemModalContext<TData>`

The context provided to the filter modal component.

### Methods

#### `cancel(): void`

Closes the modal instance with `reason="cancel"`.

#### Returns

`void`

#### `save(args: SkyFilterItemModalSavedArgs): void`

Closes the modal instance with `reason="save"`.

#### Parameters

##### `args: SkyFilterItemModalSavedArgs`

#### Returns

`void`

 SkyFilterItemModalContext
--------------------------

Type: Class

The context object that is provided to a filter modal.

### Properties

#### `additionalContext: TData`

An untyped property that can track any config information relevant to the filter modal that existing options do not include.

#### `filterLabelText: string`

The name of the filter. We recommend using this value for the modal's heading.

#### `filterValue: SkyFilterBarFilterValue`

The value of the filter.

 SkyFilterItemModalOpenedArgs
-----------------------------

Type: Interface

Arguments passed to a filter modal when it opens.

    interface SkyFilterItemModalOpenedArgs {
      data?: Observable<TData>;
      filterId: string;
    }

### Properties

#### `data?: Observable<TData>`

An observable representing data that is passed to the filter modal as additional context.

#### `filterId: string`

The unique identifier for the filter.

 SkyFilterItemModalSavedArgs
----------------------------

Type: Interface

Arguments passed back from a filter modal when the user has saved.

    interface SkyFilterItemModalSavedArgs {
      filterValue: SkyFilterBarFilterValue | undefined;
    }

### Properties

#### `filterValue: SkyFilterBarFilterValue | undefined`

The filter value.

 SkyFilterItemModalSizeType
---------------------------

Type: Type alias

    type SkyFilterItemModalSizeType = "small" | "medium" | "large" | "fullScreen"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFilterBarHarness
--------------------

Type: Class

`import { SkyFilterBarHarness } from '@skyux/filter-bar/testing';`

Harness for interacting with a filter bar component in tests.

### Methods

#### `clickClearFilters(): Promise<void>`

Clicks the clear filters button.

#### Returns

`Promise<void>`

#### `getItem(filter: SkyFilterItemHarnessFilters): Promise<SkyFilterItemHarness>`

Gets a specific filter item based on the filter criteria.

#### Parameters

##### `filter: SkyFilterItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyFilterItemHarness>`

#### `getItems(filters?: SkyFilterItemHarnessFilters): Promise<SkyFilterItemHarness[]>`

Gets an array of filter items based on the filter criteria. If no filter is provided, returns all filter items.

#### Parameters

##### `filters?: SkyFilterItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyFilterItemHarness[]>`

#### `hasActiveFilters(): Promise<boolean>`

Checks if the filter bar has active filters.

#### Returns

`Promise<boolean>`

#### `hasFilterPicker(): Promise<boolean>`

Checks if the filter picker button is visible.

#### Returns

`Promise<boolean>`

#### `openFilterPicker(): Promise<SkySelectionModalHarness>`

Clicks the filter picker button and returns a harness for the selection modal that it opened.

#### Returns

`Promise<SkySelectionModalHarness>`

#### `SkyFilterBarHarness.with(filters: SkyFilterBarHarnessFilters): HarnessPredicate<SkyFilterBarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterBarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterBarHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterBarHarness>`

 SkyFilterBarHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterBarHarness` instances.

    interface SkyFilterBarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyFilterItemHarness
---------------------

Type: Class

`import { SkyFilterItemHarness } from '@skyux/filter-bar/testing';`

Harness to interact with a filter item component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the filter item to open its modal.

#### Returns

`Promise<void>`

#### `getFilterValue(): Promise<undefined | string>`

Gets the filter item value.

#### Returns

`Promise<undefined | string>`

#### `getLabelText(): Promise<string>`

Gets the filter item label.

#### Returns

`Promise<string>`

#### `SkyFilterItemHarness.with(filters: SkyFilterItemHarnessFilters): HarnessPredicate<SkyFilterItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFilterBarItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFilterItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyFilterItemHarness>`

 SkyFilterItemHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFilterItemHarness` instances.

    interface SkyFilterItemHarnessFilters {
      filterId?: string;
      labelText?: string;
    }

### Properties

#### `filterId?: string`

Finds a filter item whose filter id matches the given value.

#### `labelText?: string`

Finds a filter item whose label text matches the given value.
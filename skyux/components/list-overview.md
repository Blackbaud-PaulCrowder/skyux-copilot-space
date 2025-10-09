               

 List overview (deprecated)
==========================

Lists display data in a consistent, flexible way.

Lists and their features are deprecated. We will remove them in a future major version. We recommend using [data manager](/skyux/components/data-manager.md) instead.

 Related information
--------------------

### Components

*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)
*   [List view grid](/skyux/components/list-view-grid.md)

 Installation
-------------

NPM package

`@skyux/list-builder`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder/src/lib/modules/list/list.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder`Copy None found.

 SkyListModule
--------------

Type: Module

`import { SkyListModule } from '@skyux/list-builder';`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

 SkyListComponent
-----------------

Type: Component

Selector: `sky-list`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

### Inputs

#### `appliedFilters: ListFilterModel[]`

The set of filters to apply to list data. These filters create a filter summary when the list includes the [`sky-list-filter-summary`](/skyux/components/list/filters.md) component.

Default: `[]`

#### `data: any[] | Observable<any[]>`

The data to display. The list component requires this property or the `dataProvider` property. For checklist or multiselect grids, each row requires an `id` property to manage selected items with the `selectedIds` input and the `selectedIdsChange` event. If you do not provide an `id`, the list automatically generates one. To update data in your view outside of a `dataProvider`, you must use an observable instead of a static array.

Default: `[]`

#### `dataProvider: ListDataProvider`

The data provider that obtains the data to display. The list component requires this property or the `data` property. For lists that use `dataProvider` instead of `data`, consumers are responsible for managing all `ListDataRequestModel` properties.

Default: `SkyListInMemoryDataProvider`

#### `initialTotal: number`

The total number of items for the initial data set when initialized. When used in conjunction with `data` and `dataProvider`, it allows an initial data to be set with the need to call the `dataProvider`.

#### `search: (data: any, searchText: string) => boolean`

The function to apply as a global sort on the list.

#### `selectedIds: string[] | Observable<string[]>`

The set of IDs for the items to select in a checklist or multiselect grid. The IDs match the `id` properties of the `data` objects. Items with IDs that are not included are de-selected in the checklist or multiselect grid.

#### `sortFields: ListSortFieldSelectorModel | ListSortFieldSelectorModel[] | Observable<ListSortFieldSelectorModel[]> | Observable<ListSortFieldSelectorModel>`

The set of fields to sort by. If array of fields then sorted by order of array. For information about `ListSortFieldSelectorModel`, see the [shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

### Outputs

#### `appliedFiltersChange: EventEmitter<ListFilterModel[]>`

Emits the filters applied to the list.

#### `selectedIdsChange: EventEmitter<Map<string, boolean>>`

For list views that support item selection, emits the selected entries.

 ListDataRequestModel
---------------------

Type: Class

### Properties

#### `filters: ListFilterModel[]`

The function that determines whether items are filtered. This property is required when using an in-memory data provider.

#### `isToolbarDisabled: boolean`

Whether to disable the search bar and filter button.

Default: `false`

#### `pageNumber: number`

The current page number.

#### `pageSize: number`

The number of items to display per page.

#### `search: ListSearchModel`

The function to dynamically manage the data source when users change the text in the list field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `sort: ListSortModel`

The set of fields to sort by.

 ListDataResponseModel
----------------------

Type: Class

### Properties

#### `count: number`

The total number of records in the list.

#### `items: ListItemModel[]`

An array of the items returned. For information about `ListItemModel`, see the [shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

 ListSearchModel
----------------

Type: Class

Specifies a function to dynamically manage the data source when users change the text in the list field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

### Properties

#### `fieldSelectors: string[]`

The columns to search. The columns correspond to `field` values that you specify with the list component's `data` property.

Default: `[]`

#### `functions: ((data: any, searchText: string) => boolean)[]`

The array of functions that returns a `boolean` value of `true` when the search is successful. This property accepts a function of type `(data: any, searchText: string) => boolean>.`

Default: `[]`

#### `searchText: string`

The text to search.

Default: `""`

 ListSelectedModel
------------------

Type: Class

Contains data about the selected items in the list.

### Properties

#### `selectedIdMap: Map<string, boolean>`

A map of key value pairs that consists of IDs for selected items and boolean values for their selected states.

 ListSortLabelModel
-------------------

Type: Class

These properties are a work in progress, and we do not recommend using them.

### Properties

#### `descending: boolean`

Whether to sort in descending order.

Default: `false`

#### `fieldSelector: string`

The fields to sort.

#### `fieldType: string`

The label type.

#### `global: boolean`

Whether to sort all fields.

Default: `false`

#### `text: string`

The text for the label.

 ListSortModel
--------------

Type: Class

Specifies a set of fields to sort by.

### Properties

#### `available: ListSortLabelModel[]`

The list of available views to sort.

Default: `[]`

#### `fieldSelectors: ListSortFieldSelectorModel[]`

The fields to sort. For information about `ListSortFieldSelectorModel`, see the [shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

Default: `[]`

#### `global: ListSortLabelModel[]`

The list views that the sort applies to.

Default: `[]`
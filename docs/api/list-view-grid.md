---
component: 'list-view-grid'
type: 'api-documentation'
description: 'API documentation for the list-view-grid component including components, interfaces, and types.'
---

# List View Grid API Documentation

## Components and Directives

#### SkyListViewGridComponent

Displays a grid for a
[SKY UX-themed list of data](https://developer.blackbaud.com/skyux/components/list/overview)
using the [grid component](https://developer.blackbaud.com/skyux/components/grid).
You must install `SkyListModule` as a dependency.

**Selector:** `sky-list-view-grid`

**Package:** `@skyux/list-builder-view-grids`

**Inputs:**

- `displayedColumns`: `string[] | Observable<string[]>` - The columns to display by default based on the ID or field of the item.
- `enableMultiselect`: `boolean` - Whether to enable the multiselect feature to display a column of checkboxes
on the left side of the grid. Multiselect also displays an action bar with buttons to
select and clear all checkboxes. Multiselect defaults to the `id` property on the list's
`data` object. (default: false)
- `fit`: `string` - How the grid fits to its parent. `"width"` fits the grid to the parent's full
width, and `"scroll"` allows the grid to exceed the parent's width. If the grid does not have
enough columns to fill the parent's width, it always stretches to the parent's full width. (default: "width")
- `height`: `number | Observable<number>` - The height of the grid.
- `hiddenColumns`: `string[] | Observable<string[]>` - The columns to hide by default based on the ID or field of the item.
- `highlightSearchText`: `boolean` - Whether to highlight search text within the grid. (default: true)
- `rowHighlightedId`: `string` - The ID of the row to highlight. The ID matches the `id` property of
the `data` object. Typically, this property is used in conjunction with the
[flyout component](https://developer.blackbaud.com/skyux/components/flyout) to
indicate the currently selected row.
- `search`: `(data: any, searchText: string) => boolean` - The search function to apply on the view data.
- `settingsKey`: `string` - The unique key for the UI Config Service that retrieves stored settings from
a database. The service saves configuration settings for users and returns `selectedColumnIds`
for the columns to display and the preferred column order. For more information, see the
[sticky settings documentation](https://developer.blackbaud.com/skyux/learn/get-started/advanced/sticky-settings).
- `width`: `number | Observable<number>` - The width of the grid.
- `messageStream`: `Subject<SkyListViewGridMessage>` - The observable to send commands to the grid.
The commands should respect the `SkyListViewGridMessage` type.
- `name`: `string` - The name of the view.

**Outputs:**

- `rowDeleteCancel`: `EventEmitter<SkyListViewGridRowDeleteCancelArgs>` - Fires when users cancel the deletion of a row.
- `rowDeleteConfirm`: `EventEmitter<SkyListViewGridRowDeleteConfirmArgs>` - Fires when users confirm the deletion of a row.
- `selectedColumnIdsChange`: `EventEmitter<string[]>` - Fires when columns change. This includes changes to the displayed columns and changes
to the order of columns. The event emits an array of IDs for the displayed columns that
reflects the column order.

#### SkyListComponent

**Selector:** `sky-list`

**Package:** `@skyux/list-builder`

**Inputs:**

- `appliedFilters`: `ListFilterModel[]` - The set of filters to apply to list data.
These filters create a filter summary when the list includes the
[`sky-list-filter-summary`](https://developer.blackbaud.com/skyux/components/list/filters)
component. (default: [])
- `data`: `any[] | Observable<any[]>` - The data to display. The list component requires this property or the
`dataProvider` property. For checklist or multiselect grids, each row requires an
`id` property to manage selected items with the `selectedIds` input and the
`selectedIdsChange` event. If you do not provide an `id`, the list automatically
generates one. To update data in your view outside of a `dataProvider`, you must use
an observable instead of a static array. (default: [])
- `dataProvider`: `ListDataProvider` - The data provider that obtains the data to display. The list component requires
this property or the `data` property. For lists that use `dataProvider` instead of `data`,
consumers are responsible for managing all `ListDataRequestModel` properties. (default: SkyListInMemoryDataProvider)
- `defaultView`: `ListViewComponent`
- `initialTotal`: `number` - The total number of items for the initial data set when initialized. When
used in conjunction with `data` and `dataProvider`, it allows an initial data to be
set with the need to call the `dataProvider`.
- `search`: `(data: any, searchText: string) => boolean` - The function to apply as a global sort on the list.
- `selectedIds`: `string[] | Observable<string[]>` - The set of IDs for the items to select in a checklist or multiselect grid.
The IDs match the `id` properties of the `data` objects. Items with IDs that are not
included are de-selected in the checklist or multiselect grid.
- `sortFields`: `ListSortFieldSelectorModel | ListSortFieldSelectorModel[] | Observable<ListSortFieldSelectorModel[]> | Observable<ListSortFieldSelectorModel>` - The set of fields to sort by. If array of fields then sorted by order of array.
For information about `ListSortFieldSelectorModel`, see the
[shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

**Outputs:**

- `appliedFiltersChange`: `EventEmitter<ListFilterModel[]>` - Emits the filters applied to the list.
- `selectedIdsChange`: `EventEmitter<Map<string, boolean>>` - For list views that support item selection, emits the selected entries.

#### SkyGridComponent

**Selector:** `sky-grid`

**Package:** `@skyux/grids`

**Inputs:**

- `data`: `any[]` - The data for the grid. Each item requires an `id` and a property that maps
to the `field` or `id` property of each column in the grid.
- `enableMultiselect`: `boolean` - Whether to enable the multiselect feature to display a column of
checkboxes on the left side of the grid. You can specify a unique ID with
the `multiselectRowId` property, but multiselect defaults to the `id` property on
the `data` object. (default: false)
- `fit`: `string` - How the grid fits to its parent. The valid options are `width`,
which fits the grid to the parent's full width, and `scroll`, which allows the grid
to exceed the parent's width. If the grid does not have enough columns to fill
the parent's width, it always stretches to the parent's full width. (default: "width")
- `hasToolbar`: `boolean` - Whether to display a toolbar with the grid. (default: false)
- `height`: `number` - The height of the grid.
- `highlightText`: `string` - Text to highlight within the grid.
Typically, this property is used in conjunction with search.
- `messageStream`: `Subject<SkyGridMessage>` - The observable to send commands to the grid.
- `multiselectRowId`: `string` - The unique ID that matches a property on the `data` object.
By default, this property uses the `id` property.
- `rowHighlightedId`: `string` - The ID of the row to highlight. The ID matches the `id` property
of the `data` object. Typically, this property is used in conjunction with
the flyout component to indicate the currently selected row.
- `settingsKey`: `string` - The unique key for the UI Config Service to retrieve stored settings from a database.
The UI Config Service saves configuration settings for users and returns
`selectedColumnIds` to preserve the columns to display and the preferred column order. You  must provide `id` values for your `sky-grid-column` elements because the UI Config Service depends on those values to organize columns based on user settings. For more information about the UI Config Service, see [the sticky settings documentation](https://developer.blackbaud.com/skyux/learn/develop/sticky-settings).
- `sortField`: `ListSortFieldSelectorModel` - Displays a caret in the column that was used to sort the grid. This is particularly useful
when you programmatically sort data and want to visually indicate how the grid was sorted.
This property accepts a `ListSortFieldSelectorModel` value with the following properties:
- `fieldSelector` Represents the current sort field. This property accepts `string` values.
- `descending` Indicates whether to sort in descending order. The caret that visually
indicates the sort order points down for descending order and up for ascending order.
This property accepts `boolean` values. Default is `false`.
- `width`: `number` - The width of the grid in pixels.
- `columns`: `SkyGridColumnModel[]` - Columns and column properties for the grid.
- `selectedColumnIds`: `string[]` - The columns to display in the grid based on the `id` or `field` properties
of the columns. If no columns are specified, then the grid displays all columns.
- `selectedRowIds`: `string[]` - The set of IDs for the rows to select in a multiselect grid.
The IDs match the `id` properties of the `data` objects.
Rows with IDs that are not included are de-selected in the grid.

**Outputs:**

- `columnWidthChange`: `EventEmitter<SkyGridColumnWidthModelChange[]>` - Fires when the width of a column changes.
- `multiselectSelectionChange`: `EventEmitter<SkyGridSelectedRowsModelChange>` - Fires when the selection of multiselect checkboxes changes.
Emits an array of IDs for the selected rows based on the `multiselectRowId` property
that the consumer provides.
- `rowDeleteCancel`: `EventEmitter<SkyGridRowDeleteCancelArgs>`
- `rowDeleteConfirm`: `EventEmitter<SkyGridRowDeleteConfirmArgs>`
- `selectedColumnIdsChange`: `EventEmitter<string[]>` - Fires when the columns to display in the grid change or when the order of the columns changes.
The event emits an array of IDs for the displayed columns that reflects the column order.
- `sortFieldChange`: `EventEmitter<ListSortFieldSelectorModel>` - Fires when the active sort field changes.
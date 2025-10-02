---
component: 'list-filters'
type: 'api-documentation'
description: 'API documentation for the list-filters component including components, interfaces, and types.'
---

# List Filters API Documentation

## Components and Directives

#### SkyListFilterSummaryComponent

Creates a filter summary based on the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property. Place this component within the
[`sky-list-toolbar`](https://developer.blackbaud.com/skyux/components/list/toolbar) component.

**Selector:** `sky-list-filter-summary`

**Package:** `@skyux/list-builder`

**Outputs:**

- `summaryItemClick`: `EventEmitter<ListFilterModel>` - Emits a `ListFilterModel` when users select a summary item. A common use case is
to open a filter modal when this event is received.

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
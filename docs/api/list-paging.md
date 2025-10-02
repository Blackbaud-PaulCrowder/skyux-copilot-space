---
component: 'list-paging'
type: 'api-documentation'
description: 'API documentation for the list-paging component including components, interfaces, and types.'
---

# List Paging API Documentation

## Components and Directives

#### SkyListPagingComponent

Displays a pagination control for a SKY UX-themed list of data.

**Selector:** `sky-list-paging`

**Package:** `@skyux/list-builder`

**Inputs:**

- `maxPages`: `number | Observable<number>` - The maximum pages to display. (default: 5)
- `pageNumber`: `number | Observable<number>` - The current page number. (default: 1)
- `pageSize`: `number | Observable<number>` - The number of list items per page. (default: 10)

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

#### SkyPagingComponent

**Selector:** `sky-paging`

**Package:** `@skyux/lists`

**Inputs:**

- `currentPage`: `number` - The page number of the current page. Page numbers start at 1 and increment. (default: 1)
- `itemCount`: `number` - The total number of items across all pages. (default: 0)
- `maxPages`: `number` - The maximum number of pages to display in the pagination control. (default: 5)
- `pageSize`: `number` - The number of items to display per page. (default: 10)
- `pagingLabel`: `string | undefined` - The label for the pagination control when an application includes
multiple paging components on the same page. The label should be unique and descriptive
to help users of assistive technology differentiate pagination controls
and understand what each one does. (default: "Pagination")

**Outputs:**

- `contentChange`: `EventEmitter<SkyPagingContentChangeArgs>` - Fires when the current page changes and emits the new current page with a function
to call when loading the new page completes. Handling this event will display the
wait component until the callback function is called, and focus will move to the top
of the list for keyboard navigation if the list contents are placed inside the
sky-paging-content element.
- `currentPageChange`: `EventEmitter<number>` - Fires when the current page changes and emits the new current page.
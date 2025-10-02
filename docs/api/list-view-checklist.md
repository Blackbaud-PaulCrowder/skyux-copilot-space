---
component: 'list-view-checklist'
type: 'api-documentation'
description: 'API documentation for the list-view-checklist component including components, interfaces, and types.'
---

# List View Checklist API Documentation

## Components and Directives

#### SkyListViewChecklistItemComponent

**Selector:** `sky-list-view-checklist-item`

**Package:** `@skyux/list-builder-view-checklist`

**Inputs:**

- `item`: `ListViewChecklistItemModel`

#### SkyListViewChecklistComponent

**Selector:** `sky-list-view-checklist`

**Package:** `@skyux/list-builder-view-checklist`

**Inputs:**

- `description`: `string` - The name of the description field selector. (default: "description")
- `label`: `string` - The name of the label field selector. (default: "label")
- `search`: `(data: any, searchText: string) => boolean` - The search function to apply on the view data.
The default function searches view data on label, description,
and category if field selectors are defined for the given field. (default: default search function)
- `name`: `string` - The name of the view.
- `selectMode`: `string` - How many items users can select.
`"single"` allows users to select one item in the checklist, while `"multiple"`
allows users to select multiple items in the checklist. (default: "multiple")
- `showOnlySelected`: `boolean` - Whether to display selected items only. (default: false)

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
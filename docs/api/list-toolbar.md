---
component: 'list-toolbar'
type: 'api-documentation'
description: 'API documentation for the list-toolbar component including components, interfaces, and types.'
---

# List Toolbar API Documentation

## Components and Directives

#### SkyListToolbarItemComponent

Defines a toolbar item for the list toolbar.

**Selector:** `sky-list-toolbar-item`

**Package:** `@skyux/list-builder`

**Inputs:**

- `id`: `string` - The ID of the item.
- `index`: `number` - The index of the item at the given item location. (default: -1)
- `location`: `string` - The toolbar location of the item. The valid options are `"left"`,
`"center"`, and `"right"`. (default: "left")

#### SkyListToolbarSearchActionsComponent

Displays custom actions in the toolbar beside to the search bar.

**Selector:** `sky-list-toolbar-search-actions`

**Package:** `@skyux/list-builder`

#### SkyListToolbarSortComponent

Adds a sort dropdown to the list toolbar.

**Selector:** `sky-list-toolbar-sort`

**Package:** `@skyux/list-builder`

**Inputs:**

- `descending`: `boolean` - Whether to sort data in descending order. (default: false)
- `field`: `string` - The data field to sort the list on.
- `label`: `string` - The label for a sort option.
- `type`: `string` - The data type of the data field to sort the list on.

#### SkyListToolbarViewActionsComponent

Adds a section on the right side of the toolbar for items that substantially change
or affect the view of the list. This includes simple filters and view switchers.
If the view section includes more than one item, simple filters appear on the left
and view switchers appear on the right.

**Selector:** `sky-list-toolbar-view-actions`

**Package:** `@skyux/list-builder`

#### SkyListToolbarComponent

Displays a toolbar for a SKY UX-themed list of data.

**Selector:** `sky-list-toolbar`

**Package:** `@skyux/list-builder`

**Inputs:**

- `placeholder`: `string` - Placeholder text for the search bar that the list toolbar creates with
a [search component](https://developer.blackbaud.com/skyux/components/search). (default: "Find in this list")
- `searchEnabled`: `boolean | Observable<boolean>` - Whether to enable the search bar. (default: true)
- `searchText`: `string | Observable<string>` - The text string to search with.
- `sortSelectorEnabled`: `boolean | Observable<boolean>` - Whether to enable the sort selector. (default: false)
- `toolbarType`: `string` - Display the search bar in the standard position or in a separate section.
To highlight the search bar in a section above all other toolbar items,
set this property to `search`. (default: "standard")
- `inMemorySearchEnabled`: `boolean` - Whether to use the in-memory search.
Setting this to `false` will allow consumers to run their own searches remotely,
and push new values to the list component by updating the `data` property. (default: true)

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

#### SkyToolbarComponent

Displays actions for lists, records, and tiles.

**Selector:** `sky-toolbar`

**Package:** `@skyux/layout`

**Inputs:**

- `listDescriptor`: `string | undefined` - A descriptor for the items that the toolbar manipulates. Use a plural term. The descriptor helps set the toolbar's `aria-label` attributes for search inputs, sort buttons, and filter buttons to provide text equivalents for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
---
component: 'description-list'
type: 'api-documentation'
description: 'API documentation for the description-list component including components, interfaces, and types.'
---

# Description List API Documentation

## Components and Directives

#### LayoutDescriptionListHelpKeyExampleComponent

**Selector:** `app-layout-description-list-help-key-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListHorizontalExampleComponent

**Selector:** `app-layout-description-list-horizontal-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListInlineHelpExampleComponent

**Selector:** `app-layout-description-list-inline-help-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListLongDescriptionExampleComponent

**Selector:** `app-layout-description-list-long-description-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListVerticalExampleComponent

**Selector:** `app-layout-description-list-vertical-example`

**Package:** `@skyux/code-examples`

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

#### SkyDescriptionListContentComponent

Wraps the term-description pairs in the description list.

**Selector:** `sky-description-list-content`

**Package:** `@skyux/layout`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
placed beside the description list content label. Clicking the button invokes global help as configured by the application.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the description list content. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.

#### SkyDescriptionListDescriptionComponent

Specifies the description in a term-description pair.

**Selector:** `sky-description-list-description`

**Package:** `@skyux/layout`

#### SkyDescriptionListTermComponent

Specifies the term in a term-description pair. To display a help button beside
the term, include a help button element in the sky-description-list-term element
and a sky-control-help CSS class on that element.

**Selector:** `sky-description-list-term`

**Package:** `@skyux/layout`

#### SkyDescriptionListComponent

Creates a description list to display term-description pairs.

**Selector:** `sky-description-list`

**Package:** `@skyux/layout`

**Inputs:**

- `listItemWidth`: `string | undefined` - The width of term-description pairs when `mode` is set to `"horizontal"`. By default,
the width is responsive based on the width of the container element.
- `defaultDescription`: `string` - The default description to display when no description is provided
for a term-description pair. (default: "None found")
- `mode`: `SkyDescriptionListModeType` - How to display term-description pairs within the description list. (default: "vertical")
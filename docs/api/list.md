---
component: 'list'
type: 'api-documentation'
description: 'API documentation for the list component including components, interfaces, and types.'
---

# List API Documentation

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

#### SkyListColumnSelectorActionComponent

Provides a column selector modal for a list grid view when placed in a
[list toolbar](https://developer.blackbaud.com/skyux/components/list/toolbar).

**Selector:** `sky-list-column-selector-action`

**Package:** `@skyux/list-builder-view-grids`

**Inputs:**

- `gridView`: `SkyListViewGridComponent` - Enables the column selector in the list toolbar. Set this attribute to the instance of
the `sky-grid-view` component using the component's template reference variable.
- `helpKey`: `string` - The `helpKey` string to associate with a help button in the grid header. When users select
the button, the `helpOpened` event broadcasts the `helpKey` parameter.

**Outputs:**

- `helpOpened`: `EventEmitter<string>` - Fires when users click the help button and broadcasts the `helpKey`.

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

#### LayoutDefinitionListBasicExampleComponent

**Selector:** `app-layout-definition-list-basic-example`

**Package:** `@skyux/code-examples`

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

#### ListsFilterInlineExampleComponent

**Selector:** `app-lists-filter-inline-example`

**Package:** `@skyux/code-examples`

#### ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Package:** `@skyux/code-examples`

#### ListsInfiniteScrollRepeaterExampleComponent

**Selector:** `app-lists-infinite-scroll-repeater-example`

**Package:** `@skyux/code-examples`

#### ListsPagingBasicExampleComponent

**Selector:** `app-lists-paging-basic-example`

**Package:** `@skyux/code-examples`

#### ListsPagingWithContentExampleComponent

**Selector:** `app-lists-paging-with-content-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterAddRemoveExampleComponent

**Selector:** `app-lists-repeater-add-remove-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterBasicExampleComponent

**Selector:** `app-lists-repeater-basic-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Package:** `@skyux/code-examples`

#### ListsSortBasicExampleComponent

**Selector:** `app-lists-sort-basic-example`

**Package:** `@skyux/code-examples`

#### PagesPageListPageListLayoutExampleComponent

**Selector:** `app-pages-page-list-page-list-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### SkyListFilterButtonComponent

Contains a filter button for the list toolbar. Place a
[`sky-filter-button`](https://developer.blackbaud.com/skyux/components/filter)
component inside this component to open a modal with filtering options.
To apply filter options, use the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property.

**Selector:** `sky-list-filter-button`

**Package:** `@skyux/list-builder`

#### SkyListFilterInlineItemComponent

Creates a filter in the list's inline filter area.

**Selector:** `sky-list-filter-inline-item`

**Package:** `@skyux/list-builder`

**Inputs:**

- `defaultValue`: `any` - The default value of the filter. If the value of the filter
is set to the default value, then the filter is not applied.
- `filter`: `(item: ListItemModel, filter: any) => boolean` - The function that determines whether an item is filtered.
This property is required when using an in-memory data provider. For information
about `ListItemModel`, see the
[shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).
- `name`: `string` - The name of the filter.
- `template`: `TemplateRef<unknown>` - The template for the filter. The template can access the `filter`
variable that contains the `value` of the filter control, which should be bound to
`ngModel`, and the `changed` function, which should be called when the model changes.
- `value`: `any` - The current value of the filter.

#### SkyListFilterInlineComponent

Creates an inline filter area for the list. Place each filter
in a `sky-list-filter-inline-item` component.

**Selector:** `sky-list-filter-inline`

**Package:** `@skyux/list-builder`

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

#### SkyListPagingComponent

Displays a pagination control for a SKY UX-themed list of data.

**Selector:** `sky-list-paging`

**Package:** `@skyux/list-builder`

**Inputs:**

- `maxPages`: `number | Observable<number>` - The maximum pages to display. (default: 5)
- `pageNumber`: `number | Observable<number>` - The current page number. (default: 1)
- `pageSize`: `number | Observable<number>` - The number of list items per page. (default: 10)

#### SkyListSecondaryActionComponent

Adds actions to the secondary actions dropdown in the list toolbar.

**Selector:** `sky-list-secondary-action`

**Package:** `@skyux/list-builder`

#### SkyListSecondaryActionsComponent

Adds a dropdown to the list toolbar for secondary actions. If the dropdown does not
include actions, the secondary actions dropdown is hidden.

**Selector:** `sky-list-secondary-actions`

**Package:** `@skyux/list-builder`

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

#### SkyDefinitionListContentComponent

Wraps the label-value pairs in the definition list.

**Selector:** `sky-definition-list-content`

**Package:** `@skyux/layout`

#### SkyDefinitionListHeadingComponent

Specifies a title for the definition list.

**Selector:** `sky-definition-list-heading`

**Package:** `@skyux/layout`

#### SkyDefinitionListLabelComponent

Specifies the label in a label-value pair.

**Selector:** `sky-definition-list-label`

**Package:** `@skyux/layout`

#### SkyDefinitionListValueComponent

Specifies the value in a label-value pair.

**Selector:** `sky-definition-list-value`

**Package:** `@skyux/layout`

#### SkyDefinitionListComponent

Creates a definition list to display label-value pairs.

**Selector:** `sky-definition-list`

**Package:** `@skyux/layout`

**Inputs:**

- `defaultValue`: `string | undefined` - The default value to display when no value is provided
for a label-value pair. (default: "None found")
- `labelWidth`: `string | undefined` - The width of the label portion of the definition list. (default: "90px")

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

#### SkyLinkListRecentlyAccessedComponent

A component that displays a list of recently accessed links, such as within a `<sky-page-links>` component.

**Selector:** `sky-link-list-recently-accessed`

**Package:** `@skyux/pages`

**Inputs:**

- `recentLinks`: `InputSignal<SkyRecentLinksInput>` - Option to pass links as an array of `SkyRecentLink` objects,
a `SkyRecentlyAccessedGetLinksArgs` object for `SkyRecentlyAccessedService`,
or `'loading'` to display a loading indicator.

#### SkyLinkListItemComponent

A wrapper for each link in a link list.

**Selector:** `sky-link-list-item`

**Package:** `@skyux/pages`

#### SkyLinkListComponent

A component that displays a list of links, such as within a `<sky-page-links>` component.

**Selector:** `sky-link-list`

**Package:** `@skyux/pages`

**Inputs:**

- `headingText`: `InputSignal<undefined | string>` - The text to display as the list's heading.
- `links`: `InputSignal<SkyPageLinksInput>` - Option to pass links as an array of `SkyPageLink` objects or `'loading'` to display a loading indicator.

#### SkyModalLinkListComponent

A component that displays a list of links such as within a `<sky-page-links>` component.

**Selector:** `sky-modal-link-list`

**Package:** `@skyux/pages`

**Inputs:**

- `headingText`: `InputSignal<undefined | string>` - The text to display as the list's heading.
- `links`: `InputSignal<SkyPageModalLinksInput>` - Option to pass links as an array of `SkyPageModalLink` objects or `'loading'` to display a loading indicator.
               

 List filters (deprecated)
=========================

List filters provide filtering capabilities for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

Lists and their features are deprecated. We will remove them in a future major version. We recommend using [data manager](/skyux/components/data-manager.md) instead.

 Related information
--------------------

### Components

*   [Filter](/skyux/components/filter.md)
*   [List overview](/skyux/components/list-overview.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)
*   [List view grid](/skyux/components/list-view-grid.md)

 Installation
-------------

NPM package

`@skyux/list-builder`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder/src/lib/modules/list-filters/list-filters.module.ts#L30) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder`Copy None found.

 SkyListFiltersModule
---------------------

Type: Module

`import { SkyListFiltersModule } from '@skyux/list-builder';`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

 SkyListFilterInlineComponent
-----------------------------

Type: Component

Selector: `sky-list-filter-inline`

Creates an inline filter area for the list. Place each filter in a `sky-list-filter-inline-item` component.

 SkyListFilterInlineItemComponent
---------------------------------

Type: Component

Selector: `sky-list-filter-inline-item`

Creates a filter in the list's inline filter area.

### Inputs

#### `name: string`

Required

The name of the filter.

#### `template: TemplateRef<unknown>`

Required

The template for the filter. The template can access the `filter` variable that contains the `value` of the filter control, which should be bound to `ngModel`, and the `changed` function, which should be called when the model changes.

#### `defaultValue: any`

The default value of the filter. If the value of the filter is set to the default value, then the filter is not applied.

#### `filter: (item: ListItemModel, filter: any) => boolean`

The function that determines whether an item is filtered. This property is required when using an in-memory data provider. For information about `ListItemModel`, see the [shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

#### `value: any`

The current value of the filter.

 SkyListFilterSummaryComponent
------------------------------

Type: Component

Selector: `sky-list-filter-summary`

Creates a filter summary based on the [list component's](/skyux/components/list/overview#list-properties.md) `appliedFilters` property. Place this component within the [`sky-list-toolbar`](/skyux/components/list/toolbar.md) component.

### Outputs

#### `summaryItemClick: EventEmitter<ListFilterModel>`

Emits a `ListFilterModel` when users select a summary item. A common use case is to open a filter modal when this event is received.

 SkyListFilterButtonComponent
-----------------------------

Type: Component

Selector: `sky-list-filter-button`

Contains a filter button for the list toolbar. Place a [`sky-filter-button`](/skyux/components/filter.md) component inside this component to open a modal with filtering options. To apply filter options, use the [list component's](/skyux/components/list/overview#list-properties.md) `appliedFilters` property.

 ListFilterModel
----------------

Type: Class

### Properties

#### `defaultValue: any`

The default value of the filter. When a filter equals the default value, the filter does not affect the list.

#### `dismissible: boolean`

Whether users can dismiss the filter's summary item.

Default: `true`

#### `filterFunction: (item: ListItemModel, filter: any) => boolean`

The function that determines whether items are filtered. This property is required when using an in-memory data provider. For information about `ListItemModel`, see the [shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).

#### `label: string`

The label for the filter's summary item. The label defaults to the `value` of the filter.

#### `name: string`

The name of the filter.

#### `value: any`

The current value of the filter.
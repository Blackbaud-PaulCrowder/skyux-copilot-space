---
component: 'fluid-grid'
type: 'api-documentation'
description: 'API documentation for the fluid-grid component including components, interfaces, and types.'
---

# Fluid Grid API Documentation

## Components and Directives

#### LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Package:** `@skyux/code-examples`

#### SkyFluidGridComponent

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the
alignment, padding, and margins do not behave as expected.

**Selector:** `sky-fluid-grid`

**Package:** `@skyux/layout`

**Inputs:**

- `disableMargin`: `boolean | undefined` - Disables the outer left and right margin of the fluid grid container. (default: false)
- `gutterSize`: `SkyFluidGridGutterSizeType` - The type that defines the size of the padding
between columns. (default: "large")

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
---
component: 'id'
type: 'api-documentation'
description: 'API documentation for the id component including components, interfaces, and types.'
---

# Id API Documentation

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

#### AgGridDataEntryGridBasicExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-basic-example`

**Package:** `@skyux/code-examples`

#### AgGridDataEntryGridDataManagerAddedExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-data-manager-added-example`

**Package:** `@skyux/code-examples`

#### AgGridDataEntryGridFocusExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-focus-example`

**Package:** `@skyux/code-examples`

#### AgGridDataEntryGridInlineHelpExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-inline-help-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridBasicMultiselectExampleComponent

**Selector:** `app-ag-grid-data-grid-basic-multiselect-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridBasicExampleComponent

**Selector:** `app-ag-grid-data-grid-basic-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridDataManagerMultiselectExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-multiselect-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridDataManagerExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridInlineHelpExampleComponent

**Selector:** `app-ag-grid-data-grid-inline-help-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridPagingExampleComponent

**Selector:** `app-ag-grid-data-grid-paging-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridTemplateRefColumnExampleComponent

**Selector:** `app-ag-grid-data-grid-template-ref-column-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridTopScrollExampleComponent

**Selector:** `app-ag-grid-data-grid-top-scroll-example`

**Package:** `@skyux/code-examples`

#### AutonumericOptionsProviderExampleComponent

**Selector:** `app-autonumeric-options-provider-example`

**Package:** `@skyux/code-examples`

#### CoreIdExampleComponent

**Selector:** `app-core-id-example`

**Package:** `@skyux/code-examples`

#### LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Package:** `@skyux/code-examples`

#### ValidationEmailValidationControlValidatorExampleComponent

**Selector:** `app-validation-email-validation-control-validator-example`

**Package:** `@skyux/code-examples`

#### ValidationEmailValidationDirectiveExampleComponent

**Selector:** `app-validation-email-validation-directive-example`

**Package:** `@skyux/code-examples`

#### ValidationUrlValidationControlValidatorExampleComponent

**Selector:** `app-validation-url-validation-control-validator-example`

**Package:** `@skyux/code-examples`

#### ValidationUrlValidationDirectiveExampleComponent

**Selector:** `app-validation-url-validation-directive-example`

**Package:** `@skyux/code-examples`

#### SkyEmailValidationDirective

Adds email address validation to an input element. The directive uses `NgModel` to bind data.

**Selector:** `[skyEmailValidation]`

**Package:** `@skyux/validation`

#### SkyUrlValidationDirective

Adds URL validation to an input element. The directive uses `NgModel` to bind data.

**Selector:** `[skyUrlValidation]`

**Package:** `@skyux/validation`

**Inputs:**

- `skyUrlValidation`: `SkyUrlValidationOptions | undefined` - Configuration options for the URL validation component.

#### SkyAgGridDataManagerAdapterDirective

**Selector:** `[skyAgGridDataManagerAdapter]`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `viewId`: `string | undefined`

#### SkyAgGridRowDeleteComponent

Component for rendering the inline delete template in the overlay.

**Selector:** `sky-ag-grid-row-delete`

**Package:** `@skyux/ag-grid`

#### SkyAgGridRowDeleteDirective

**Selector:** `[skyAgGridRowDelete]`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `rowDeleteIds`: `ModelSignal<string[]>` - The IDs of the data in the rows where the inline delete appears.

**Outputs:**

- `rowDeleteCancel`: `OutputEmitterRef<SkyAgGridRowDeleteCancelArgs>` - Emits a `SkyAgGridRowDeleteCancelArgs` object when a row's inline delete is cancelled.
- `rowDeleteConfirm`: `OutputEmitterRef<SkyAgGridRowDeleteConfirmArgs>` - Emits a `SkyAgGridRowDeleteConfirmArgs` object when a row's inline delete is confirmed.

#### SkyAgGridWrapperComponent

**Selector:** `sky-ag-grid-wrapper`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `minHeight`: `InputSignalWithTransform<number, unknown>` - The minimum height of the grid in pixels. The default value is `50`.
- `compact`: `boolean` - Enable a compact layout for the grid when using modern theme. Compact layout uses
a smaller font size and row height to display more data in a smaller space.

#### SkyAgGridCellEditorAutocompleteComponent

**Selector:** `sky-ag-grid-cell-editor-autocomplete`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorCurrencyComponent

**Selector:** `sky-ag-grid-cell-editor-currency`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorDatepickerComponent

**Selector:** `sky-ag-grid-cell-editor-datepicker`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorLookupComponent

**Selector:** `sky-ag-grid-cell-editor-lookup`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorNumberComponent

**Selector:** `sky-ag-grid-cell-editor-number`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorTextComponent

**Selector:** `sky-ag-grid-cell-editor-text`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellRendererCurrencyValidatorComponent

**Selector:** `sky-ag-grid-cell-renderer-currency-validator`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `parameters`: `SkyCellRendererCurrencyParams`

#### SkyAgGridCellRendererCurrencyComponent

**Selector:** `sky-ag-grid-cell-renderer-currency`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `params`: `SkyCellRendererCurrencyParams`

#### SkyAgGridCellRendererLookupComponent

**Selector:** `sky-cell-renderer-lookup`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellRendererRowSelectorComponent

**Selector:** `sky-ag-grid-cell-renderer-row-selector`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellRendererValidatorTooltipComponent

**Selector:** `sky-ag-grid-cell-renderer-validator-tooltip`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `params`: `SkyCellRendererValidatorParams`

#### SkyAgGridCellValidatorTooltipComponent

**Selector:** `sky-ag-grid-cell-validator-tooltip`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `params`: `SkyCellRendererValidatorParams | undefined`

#### SkyAgGridHeaderGroupComponent

**Selector:** `sky-header-group`

**Package:** `@skyux/ag-grid`

#### SkyAgGridHeaderComponent

**Selector:** `sky-ag-grid-header`

**Package:** `@skyux/ag-grid`

#### SkyFluidGridComponent

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the
alignment, padding, and margins do not behave as expected.

**Selector:** `sky-fluid-grid`

**Package:** `@skyux/layout`

**Inputs:**

- `disableMargin`: `boolean | undefined` - Disables the outer left and right margin of the fluid grid container. (default: false)
- `gutterSize`: `SkyFluidGridGutterSizeType` - The type that defines the size of the padding
between columns. (default: "large")

#### SkyInputBoxControlDirective

**Selector:** `input:not([skyId]):not(.sky-form-control),select:not([skyId]):not(.sky-form-control),textarea:not([skyId]):not(.sky-form-control)`

**Package:** `@skyux/forms`

**Inputs:**

- `autocomplete`: `string | undefined`

#### SkySelectionBoxGridComponent

Creates a grid layout for an array of selection boxes.

**Selector:** `sky-selection-box-grid`

**Package:** `@skyux/forms`

**Inputs:**

- `alignItems`: `SkySelectionBoxGridAlignItemsType` - How to display the selection boxes in the grid. (default: 'center')

#### SkyGridColumnComponent

Specifies the column information.

**Selector:** `sky-grid-column`

**Package:** `@skyux/grids`

**Inputs:**

- `alignment`: `SkyGridColumnAlignment` - The horizontal alignment of the column's data and header.
Options include: `"left"`, `"center"`, and `"right"`. (default: "left")
- `description`: `string` - The description for the column.
- `excludeFromHighlighting`: `boolean` - Whether to disable the highlighting of search text in the column. (default: false)
- `field`: `string` - The property to retrieve cell information from an entry on the grid `data` array.
You must provide either the `id` or `field` property for every column,
but do not provide both. If `id` does not exist on a column, then `field` is the entry
for the grid `selectedColumnIds` array.
- `heading`: `string` - Text to display in the column header.
- `hidden`: `boolean` - Whether the column is initially hidden when grid `selectedColumnIds` are not provided. (default: false)
- `id`: `string` - The unique ID for the column. You must provide either the `id` or `field` property
for every column, but do not provide both. If `field` does not exist on a column,
then the `id` property retrieves cell information from an entry on the grid `data` array.
- `inlineHelpPopover`: `any` - The template to display inside an inline help popup for this column.
- `isSortable`: `boolean` - Whether the column sorts the grid when users click the column header. (default: true)
- `locked`: `boolean` - Whether the column is locked. The intent is to display locked columns first
on the left side of the grid. If set to `true`, then users cannot drag the column
to another position and or drag other columns before the locked column. (default: false)
- `search`: `(value: any, searchText: string) => boolean` - The search function to apply for the specific column. By default,
the column executes a string compare on the column data. (default: (value, searchText) => value.toString().toLowerCase().indexOf(searchText) !== -1)
- `template`: `TemplateRef<unknown>` - The template for a column. This can be assigned as a reference
to the `template` attribute, or it can be assigned as a child of the `template` element
inside the `sky-grid-column` component. The template has access to the `value` variable,
which contains the value passed to the column, and the `row` variable, which contains
the entire row data.
- `type`: `string`
- `width`: `number` - The width of the column in pixels.
If undefined, the column width is evenly distributed.

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

#### SkyIdDirective

Sets the element's `id` attribute to a unique ID. To reference this unique ID on other elements,
such as in a `label` element's `for` attribute, assign this directive to a template reference
variable, then use its `id` property.

**Selector:** `[skyId]`

**Package:** `@skyux/core`
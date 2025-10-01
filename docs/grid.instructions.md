---
component: 'grid'
description: 'Design guidelines, API documentation, and usage instructions for the grid component extracted from SKY UX documentation.'
---

# Grid Component Guidelines

## Component Overview
Grids provide a SKY UX-themed layout for tabular data. Grid is deprecated in favor of data grid. For more information, see the grid deprecation instructions.

## Usage

### ✅ Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

**✅ Do use grids to display data for users to visually scan and compare values.**

### ❌ Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use repeater or box layouts instead. If the content requires multiple templated columns, use repeaters instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use repeaters instead.

**❌ Don't use grids to display data that requires a complex layout.**

## Anatomy

- List count
- Toolbar
- Multiselect toolbar
- Header row
- Row selection checkbox
- Context-menu dropdown button
- Data
- Alternate row striping
- Row divider
- Selected row background
- Pagination
- Summary action bar

## Options

### Context-menu dropdown

Use context-menu dropdowns in the first column when users need to access multiple actions in the rows.

### Multiselect

Use multiselect when:

- Users need to act on more than one row at a time.
- The list is presented as a full page, a full-page modal, or a full page within a flyout.

Don't use multiselect when:

- The list is presented in a tile, page section, or other container that might flow off the screen.

To let users select or clear all items and to view only selected items, include the multiselect toolbar. When users select rows, the summary action bar should fly in from the bottom of the page for actions that users can take on the selected items.

**✅ Use multiselect to let users act on more than one row at a time.**

### Sorting

If users are likely to sort based on the data in columns, enable sorting so that they can select column headers to toggle between ascending and descending order for the specified fields in columns. If users need to sort by data in a templated column, use the sort component instead to let them select the data to sort on.

### Filtering

If users are likely to work with a subset of items in the grid, enable filtering so that they can focus on those items.

### Templated items

When columns represent composite information instead of single values, use templated columns to lay out content as necessary.

## Behavior and states

### Fit

The fit determines how to place the grid within its parent. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

#### Scroll

The scroll option allows grids to take as much space as necessary by adding a horizontal scrollbar. This is most useful for grids with large numbers of columns.

#### Width

The width option fixes the width of the grid to its container and resizes columns to fit. This is most useful for simple grids in smaller containers, such as tiles, where the content fits neatly in the allotted space.

**Grids with large numbers of columns can fit to the parent container by using a horizontal scrollbar to take as much space as necessary.**

### Reordering columns

Users can reorder columns by dragging and dropping.

### Resizing columns

Users can resize columns by selecting and dragging or by using the keyboard.

### Responsiveness

Grids perform poorly in small viewports. The columns in fixed-width grids shrink down to the point of being unreadable, and scrolling grids require a lot of interaction to view the content. Use repeaters instead if possible.

## Related information

### Components

- Card
- Dropdown
- Filter
- Infinite scroll
- List view grid
- Paging
- Repeater
- Sort
- Summary action bar
- Toolbar

### Guidelines

- Page design

## API Documentation

### Components and Directives

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
- `name`: `string` - The name of the view. **[Required]**

**Outputs:**

- `rowDeleteCancel`: `EventEmitter<SkyListViewGridRowDeleteCancelArgs>` - Fires when users cancel the deletion of a row.
- `rowDeleteConfirm`: `EventEmitter<SkyListViewGridRowDeleteConfirmArgs>` - Fires when users confirm the deletion of a row.
- `selectedColumnIdsChange`: `EventEmitter<string[]>` - Fires when columns change. This includes changes to the displayed columns and changes
to the order of columns. The event emits an array of IDs for the displayed columns that
reflects the column order.

⚠️ **This component is deprecated.**

#### SkyListViewGridModule

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### ListViewGridColumnsOrchestrator

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### ListViewGridColumnsLoadAction

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### ListViewDisplayedGridColumnsOrchestrator

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### ListViewDisplayedGridColumnsLoadAction

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### GridStateAction

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### GridStateModel

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### GridStateDispatcher

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### GridStateOrchestrator

**Package:** `@skyux/list-builder-view-grids`

#### GridState

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### SkyListViewGridMessageType

The command for the list view grid to respond to.

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### SkyListViewGridMessage

Communicates commands to the list view grid.

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### SkyListViewGridRowDeleteCancelArgs

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### SkyListViewGridRowDeleteConfirmArgs

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### SkyListViewGridFixtureCell

Properties of a list view grid cell.

**Package:** `@skyux/list-builder-view-grids/testing`

#### SkyListViewGridFixtureHeader

Properties of a list view grid header.

**Package:** `@skyux/list-builder-view-grids/testing`

#### SkyListViewGridFixtureRow

Properties of a list view grid row.

**Package:** `@skyux/list-builder-view-grids/testing`

#### SkyListViewGridFixture

Allows interaction with a SKY UX list view grid component.

**Package:** `@skyux/list-builder-view-grids/testing`

⚠️ **This component is deprecated.**

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

#### LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Package:** `@skyux/code-examples`

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

#### SkyAgGridModule

**Package:** `@skyux/ag-grid`

#### SkyAgGridService

`SkyAgGridService` provides methods to get AG Grid `gridOptions` to ensure grids match SKY UX functionality. The `gridOptions` can be overridden, and include registered SKY UX column types.

**Package:** `@skyux/ag-grid`

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

#### SkyAgGridRowDeleteCancelArgs

Information regarding a row whose deletion has been cancelled.

**Package:** `@skyux/ag-grid`

#### SkyAgGridRowDeleteConfirmArgs

Information regarding a row whose deletion has been confirmed.

**Package:** `@skyux/ag-grid`

#### SkyAgGridAutocompleteProperties

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorInitialAction

The initial action that a cell editor should take when initialized.

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellEditorUtils

**Package:** `@skyux/ag-grid`

#### SkyAgGridCurrencyProperties

**Package:** `@skyux/ag-grid`

#### SkyAgGridDatepickerProperties

**Package:** `@skyux/ag-grid`

#### SkyAgGridHeaderGroupInfo

To display a help button beside the column group header, create a component containing
[`sky-help-inline`](https://developer.blackbaud.com/skyux/components/help-inline),
and inject SkyAgGridHeaderGroupInfo to access the column group
information, such as display name.
Add the component to the `headerGroupComponentParams.inlineHelpComponent`
property of the [column group definition](https://www.ag-grid.com/angular-data-grid/column-groups/).

**Package:** `@skyux/ag-grid`

#### SkyAgGridHeaderGroupParams

Interface to use for the
[`headerGroupComponentParams`](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-groupsHeader-headerGroupComponentParams)
property on `ColGroupDef`.

**Package:** `@skyux/ag-grid`

#### SkyAgGridHeaderInfo

To display a help button beside the column header, create a component containing
[`sky-help-inline`](https://developer.blackbaud.com/skyux/components/help-inline),
and inject SkyAgGridHeaderInfo to access the column information, such
as display name.
Add the component to the `headerComponentParams.inlineHelpComponent`
property of the [column definition](https://www.ag-grid.com/angular-data-grid/column-definitions/).

**Package:** `@skyux/ag-grid`

#### SkyAgGridHeaderParams

Interface to use for the
[`headerComponentParams`](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-header-headerComponentParams)
property on `ColDef`.

**Package:** `@skyux/ag-grid`

#### SkyAgGridLookupProperties

**Package:** `@skyux/ag-grid`

#### SkyAgGridNumberProperties

**Package:** `@skyux/ag-grid`

#### SkyGetGridOptionsArgs

**Package:** `@skyux/ag-grid`

#### SkyAgGridTextProperties

**Package:** `@skyux/ag-grid`

#### SkyAgGridValidatorProperties

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

#### SkyFluidGridModule

**Package:** `@skyux/layout`

#### SkyFluidGridGutterSizeType

**Package:** `@skyux/layout`

#### SkyFluidGridHarnessFilters

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyFluidGridHarness

Harness for interacting with a fluid grid component in tests.

**Package:** `@skyux/layout/testing`

#### SkySelectionBoxGridComponent

Creates a grid layout for an array of selection boxes.

**Selector:** `sky-selection-box-grid`

**Package:** `@skyux/forms`

**Inputs:**

- `alignItems`: `SkySelectionBoxGridAlignItemsType` - How to display the selection boxes in the grid. (default: 'center')

#### SkySelectionBoxGridAlignItemsType

**Package:** `@skyux/forms`

#### SkySelectionBoxGridAlignItems

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkySelectionBoxGridHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxGridHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxGridHarness

Harness for interacting with a selection box grid component in tests.

**Package:** `@skyux/forms/testing`

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

⚠️ **This component is deprecated.**

#### SkyGridColumnModel

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

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

⚠️ **This component is deprecated.**

#### SkyGridModule

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridColumnAlignment

Represents the horizontal alignment of the column's data and header.

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridColumnDescriptionModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridColumnHeadingModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridColumnInlineHelpPopoverModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridColumnWidthModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridMessageType

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridMessage

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridRowDeleteCancelArgs

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridRowDeleteConfig

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridRowDeleteConfirmArgs

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridSelectedRowsModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridSelectedRowsSource

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyGridUIConfig

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

### Code Examples

#### Basic setup (without data manager)

**Selector:** `app-ag-grid-data-entry-grid-basic-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataEntryGridBasicExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
  protected searchText = '';

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
      headerName: 'Context menu',
      headerComponentParams: {
        headerHidden: true,
      },
    },
    {
      field: 'name',
      headerName: 'Name',
      type: SkyCellType.Text,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: string): boolean => String(value).length <= 10,
          validatorMessage: `Value exceeds maximum length`,
        },
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: number): boolean => value >= 18,
          validatorMessage: `Age must be 18+`,
        },
      },
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
    {
      colId: 'validationCurrency',
      field: 'validationCurrency',
      headerName: 'Validation currency',
      type: [SkyCellType.CurrencyValidator],
    },
    {
      colId: 'validationDate',
      field: 'validationDate',
      headerName: 'Validation date',
      type: [SkyCellType.Date, SkyCellType.Validator],
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: Date): boolean =>
            !!value && value > new Date(1985, 9, 26),
          validatorMessage: 'Enter a future date',
        },
      },
    },
  ];

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected openModal(): void {
    const context = new EditModalContext();

    context.gridData = this.gridData;

    const options: SkyModalConfigurationInterface = {
      ariaDescribedBy: 'docs-edit-grid-modal-content',
      providers: [
        {
          provide: EditModalContext,
          useValue: context,
        },
      ],
      size: 'large',
    };

    const modalInstance = this.#modalSvc.open(EditModalComponent, options);

    modalInstance.closed.subscribe((result) => {
      if (result.reason === 'cancel' || result.reason === 'close') {
        alert('Edits canceled!');
      } else {
        this.gridData = result.data as AgGridDemoRow[];

        if (this.#gridApi) {
          this.#gridApi.refreshCells();
        }

        alert('Saving data!');
      }
    });
  }

  protected searchApplied(searchText: string | void): void {
    this.searchText = searchText ?? '';

    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });

      const displayedRowCount = this.#gridApi.getDisplayedRowCount();

      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Data manager setup

**Selector:** `app-ag-grid-data-entry-grid-data-manager-added-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';
import { FilterModalComponent } from './filter-modal.component';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager setup
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-data-manager-added-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [ViewGridComponent, SkyDataManagerModule],
})
export class AgGridDataEntryGridDataManagerAddedExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #activeViewId = 'dataEntryGridWithDataManagerView';

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
      },
    },
    views: [
      {
        viewId: 'dataEntryGridWithDataManagerView',
        displayedColumnIds: [
          'selected',
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
          'validationCurrency',
          'validationDate',
        ],
      },
    ],
  });

  #dataManagerConfig = {
    filterModalComponent: FilterModalComponent,
    sortOptions: [
      {
        id: 'az',
        label: 'Name (A - Z)',
        descending: false,
        propertyName: 'name',
      },
      {
        id: 'za',
        label: 'Name (Z - A)',
        descending: true,
        propertyName: 'name',
      },
    ],
  };

  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((activeViewId) => {
        this.#activeViewId = activeViewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: this.#activeViewId,
      dataManagerConfig: this.#dataManagerConfig,
      defaultDataState: this.#defaultDataState,
    });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  protected openModal(): void {
    const context = new EditModalContext();
    context.gridData = this.items.slice();

    this.#changeDetectorRef.markForCheck();

    const options: SkyModalConfigurationInterface = {
      ariaDescribedBy: 'docs-edit-grid-modal-content',
      providers: [
        {
          provide: EditModalContext,
          useValue: context,
        },
      ],
      size: 'large',
    };

    const modalInstance = this.#modalSvc.open(EditModalComponent, options);

    modalInstance.closed.subscribe((result) => {
      if (result.reason === 'cancel' || result.reason === 'close') {
        alert('Edits canceled!');
      } else {
        this.items = result.data as AgGridDemoRow[];
        alert('Saving data!');
      }

      this.#changeDetectorRef.markForCheck();
    });
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Setting initial focus for keyboard navigation

**Selector:** `app-ag-grid-data-entry-grid-focus-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyInputBoxModule } from '@skyux/forms';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';

import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Setting initial focus for keyboard navigation
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-focus-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkyInputBoxModule],
})
export class AgGridDataEntryGridFocusExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions = inject(SkyAgGridService).getEditableGridOptions({
    gridOptions: {
      columnDefs: [
        {
          field: 'name',
          headerName: 'Name',
          type: SkyCellType.Text,
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: string): boolean => String(value).length <= 10,
              validatorMessage: `Value exceeds maximum length`,
            },
          },
        },
        {
          field: 'age',
          headerName: 'Age',
          type: SkyCellType.Number,
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: number): boolean => value >= 18,
              validatorMessage: `Age must be 18+`,
            },
          },
          maxWidth: 60,
        },
        {
          field: 'startDate',
          headerName: 'Start date',
          type: SkyCellType.Date,
          editable: true,
          sort: 'asc',
        },
        {
          field: 'endDate',
          headerName: 'End date',
          type: SkyCellType.Date,
          editable: true,
          valueFormatter: (
            params: ValueFormatterParams<AgGridDemoRow, Date>,
          ): string => this.#endDateFormatter(params),
        },
        {
          field: 'department',
          headerName: 'Department',
          type: SkyCellType.Autocomplete,
          editable: true,
        },
        {
          field: 'jobTitle',
          headerName: 'Title',
          type: SkyCellType.Autocomplete,
          editable: true,
        },
        {
          colId: 'validationCurrency',
          field: 'validationCurrency',
          headerName: 'Validation currency',
          type: [SkyCellType.CurrencyValidator],
          editable: true,
        },
        {
          colId: 'validationDate',
          field: 'validationDate',
          headerName: 'Validation date',
          type: [SkyCellType.Date, SkyCellType.Validator],
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: Date): boolean =>
                !!value && value > new Date(1985, 9, 26),
              validatorMessage: 'Enter a future date',
            },
          },
        },
      ],
      focusGridInnerElement: (params) => {
        params.api.startEditingCell({
          rowIndex: 0,
          colKey: 'name',
        });
        return true;
      },
    },
  });

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-input-box
  labelText="Start here"
  helpPopoverContent="Then tab to the grid"
  stacked
>
  <input type="text" />
</sky-input-box>
<div class="sky-margin-stacked-md">
  <sky-ag-grid-wrapper>
    <ag-grid-angular
      class="sky-ag-grid-editable"
      [gridOptions]="gridOptions"
      [rowData]="gridData"
    />
  </sky-ag-grid-wrapper>
</div>
<sky-input-box
  labelText="Or start here"
  helpPopoverContent="Then tab backwards to the grid"
  stacked
>
  <input type="text" />
</sky-input-box>

```

#### Basic setup with inline help (without data manager)

**Selector:** `app-ag-grid-data-entry-grid-inline-help-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';
import {
  SkyModalCloseArgs,
  SkyModalConfigurationInterface,
  SkyModalService,
} from '@skyux/modals';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';
import { InlineHelpComponent } from './inline-help.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with inline help (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-inline-help-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataEntryGridInlineHelpExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
  protected searchText = '';

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
      headerName: 'Context menu',
      headerComponentParams: {
        headerHidden: true,
      },
    },
    {
      field: 'name',
      headerName: 'Name',
      type: SkyCellType.Text,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: string): boolean => String(value).length <= 10,
          validatorMessage: `Value exceeds maximum length`,
        },
      },
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: number): boolean => value >= 18,
          validatorMessage: `Age must be 18+`,
        },
      },
      maxWidth: 60,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      colId: 'validationCurrency',
      field: 'validationCurrency',
      headerName: 'Validation currency',
      type: [SkyCellType.CurrencyValidator],
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      colId: 'validationDate',
      field: 'validationDate',
      headerName: 'Validation date',
      type: [SkyCellType.Date, SkyCellType.Validator],
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: Date): boolean =>
            !!value && value > new Date(1985, 9, 26),
          validatorMessage: 'Enter a future date',
        },
      },
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
  ];
  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected openModal(): void {
    const context = new EditModalContext();
    context.gridData = this.gridData;

    const options: SkyModalConfigurationInterface = {
      providers: [
        {
          provide: EditModalContext,
          useValue: context,
        },
      ],
      ariaDescribedBy: 'docs-edit-grid-modal-content',
      size: 'large',
    };

    const modalInstance = this.#modalSvc.open(EditModalComponent, options);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel' || result.reason === 'close') {
        alert('Edits canceled!');
      } else {
        this.gridData = result.data as AgGridDemoRow[];
        this.#gridApi?.refreshCells();

        alert('Saving data!');
      }
    });
  }

  protected searchApplied(searchText: string | void): void {
    this.searchText = searchText ?? '';

    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });
      const displayedRowCount = this.#gridApi.getDisplayedRowCount();

      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Basic multiselect setup (without data manager)

**Selector:** `app-ag-grid-data-grid-basic-multiselect-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic multiselect setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-basic-multiselect-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridBasicMultiselectExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
  ];

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
    });
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Basic setup (without data manager)

**Selector:** `app-ag-grid-data-grid-basic-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridBasicExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

  #columnDefs: ColDef[] = [
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
  ];

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      rowSelection: { mode: 'singleRow' },
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
    });
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Data manager multiselect setup

**Selector:** `app-ag-grid-data-grid-data-manager-multiselect-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import {
  SkyDataManagerConfig,
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA } from './data';
import { FilterModalComponent } from './filter-modal.component';
import { Filters } from './filters';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager multiselect setup
 */
@Component({
  selector: 'app-ag-grid-data-grid-data-manager-multiselect-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [SkyDataManagerModule, ViewGridComponent],
})
export class AgGridDataGridDataManagerMultiselectExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #dataManagerConfig: SkyDataManagerConfig = {
    filterModalComponent: FilterModalComponent,
    sortOptions: [
      {
        id: 'az',
        label: 'Name (A - Z)',
        descending: false,
        propertyName: 'name',
      },
      {
        id: 'za',
        label: 'Name (Z - A)',
        descending: true,
        propertyName: 'name',
      },
    ],
  };

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
        jobTitle: 'any',
      } satisfies Filters,
    },
    views: [
      {
        viewId: 'dataGridMultiselectWithDataManagerView',
        displayedColumnIds: [
          'selected',
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
        ],
      },
    ],
  });

  #activeViewId = 'dataGridMultiselectWithDataManagerView';
  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((activeViewId) => {
        this.#activeViewId = activeViewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: this.#activeViewId,
      dataManagerConfig: this.#dataManagerConfig,
      defaultDataState: this.#defaultDataState,
    });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Data manager setup

**Selector:** `app-ag-grid-data-grid-data-manager-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA } from './data';
import { FilterModalComponent } from './filter-modal.component';
import { Filters } from './filters';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager setup
 */
@Component({
  selector: 'app-ag-grid-data-grid-data-manager-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [SkyDataManagerModule, ViewGridComponent],
})
export class AgGridDataGridDataManagerExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #activeViewId = 'dataGridWithDataManagerView';

  #dataManagerConfig = {
    filterModalComponent: FilterModalComponent,
    sortOptions: [
      {
        id: 'az',
        label: 'Name (A - Z)',
        descending: false,
        propertyName: 'name',
      },
      {
        id: 'za',
        label: 'Name (Z - A)',
        descending: true,
        propertyName: 'name',
      },
    ],
  };

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
        jobTitle: 'any',
      } satisfies Filters,
    },
    views: [
      {
        viewId: 'dataGridWithDataManagerView',
        displayedColumnIds: [
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
        ],
      },
    ],
  });

  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((activeViewId) => {
        this.#activeViewId = activeViewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: this.#activeViewId,
      dataManagerConfig: this.#dataManagerConfig,
      defaultDataState: this.#defaultDataState,
    });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Basic setup with inline help (without data manager)

**Selector:** `app-ag-grid-data-grid-inline-help-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { InlineHelpComponent } from './inline-help.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with inline help (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-inline-help-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataGridInlineHelpExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected searchText = '';
  protected noRowsTemplate: string;

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
  ];

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);

  constructor() {
    this.noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: this.onGridReady.bind(this),
      },
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected searchApplied(searchText: string | void): void {
    if (searchText) {
      this.searchText = searchText;
    } else {
      this.searchText = '';
    }
    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });
      const displayedRowCount = this.#gridApi.getDisplayedRowCount();

      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Basic setup with paging (without data manager)

**Selector:** `app-ag-grid-data-grid-paging-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import { ActivatedRoute, NavigationEnd, Router } from '@angular/router';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyPagingModule } from '@skyux/lists';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { Subscription } from 'rxjs';
import { filter, map } from 'rxjs/operators';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with paging (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-paging-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkyPagingModule],
})
export class AgGridDataGridPagingExampleComponent implements OnInit, OnDestroy {
  protected currentPage = 1;

  protected readonly pageSize = 3;

  #columnDefs: ColDef[] = [
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
  ];

  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

  #gridApi: GridApi | undefined;
  #subscriptions = new Subscription();

  readonly #activatedRoute = inject(ActivatedRoute);
  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #router = inject(Router);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
      rowSelection: { mode: 'singleRow' },
      pagination: true,
      suppressPaginationPanel: true,
      paginationPageSize: this.pageSize,
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
    });
  }

  public ngOnInit(): void {
    this.#subscriptions.add(
      this.#activatedRoute.queryParamMap
        .pipe(map((params) => params.get('page') ?? '1'))
        .subscribe((page) => {
          this.currentPage = Number(page);
          this.#gridApi?.paginationGoToPage(this.currentPage - 1);
          this.#changeDetectorRef.detectChanges();
        }),
    );

    this.#subscriptions.add(
      this.#router.events
        .pipe(filter((event) => event instanceof NavigationEnd))
        .subscribe(() => {
          const page = this.#activatedRoute.snapshot.paramMap.get('page');

          if (page) {
            this.currentPage = Number(page);
          }

          this.#gridApi?.paginationGoToPage(this.currentPage - 1);
          this.#changeDetectorRef.detectChanges();
        }),
    );
  }

  public ngOnDestroy(): void {
    this.#subscriptions.unsubscribe();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#gridApi.paginationGoToPage(this.currentPage - 1);
  }

  protected async onPageChange(page: number): Promise<void> {
    await this.#router.navigate(['.'], {
      relativeTo: this.#activatedRoute,
      queryParams: { page: page.toString(10) },
      queryParamsHandling: 'merge',
    });
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Basic setup with template ref column type (without data manager)

**Selector:** `app-ag-grid-data-grid-template-ref-column-example`

**TypeScript:**

```typescript
import {
  Component,
  OnInit,
  TemplateRef,
  ViewChild,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  GridOptions,
  ModuleRegistry,
} from 'ag-grid-community';

import { AG_GRID_DEMO_DATA } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with template ref column type (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-template-ref-column-example',
  templateUrl: './example.component.html',
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridTemplateRefColumnExampleComponent implements OnInit {
  @ViewChild('boldColumn', { static: true })
  protected boldColumn: TemplateRef<unknown> | undefined;

  @ViewChild('emphasizedColumn', { static: true })
  protected emphasizedColumn: TemplateRef<unknown> | undefined;

  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);

  public ngOnInit(): void {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: [
          {
            field: 'name',
            headerName: 'Name',
            initialWidth: 150,
          },
          {
            field: 'age',
            headerName: 'Age',
            type: SkyCellType.Number,
            maxWidth: 80,
            resizable: false,
          },
          {
            field: 'department',
            headerName: 'Department',
            type: SkyCellType.Template,
            cellRendererParams: {
              template: this.boldColumn,
            },
            initialWidth: 220,
          },
          {
            field: 'jobTitle',
            headerName: 'Title',
            type: SkyCellType.Template,
            cellRendererParams: {
              template: this.emphasizedColumn,
            },
            initialWidth: 220,
          },
        ],
      },
    });
  }
}

```

**Template:**

```html
<ng-template #boldColumn let-value="value">
  <strong>{{ value }}</strong>
</ng-template>
<ng-template #emphasizedColumn let-value="value" let-row="row">
  @if (row['jobLevel']) {
    <span class="sky-margin-inline-sm sky-pull-right">{{
      row['jobLevel']
    }}</span>
  }
  <em>{{ value }}</em>
</ng-template>
<sky-ag-grid-wrapper>
  <ag-grid-angular [gridOptions]="gridOptions" [rowData]="gridData" />
</sky-ag-grid-wrapper>

```

#### Basic setup with top scrollbar (without data manager)

**Selector:** `app-ag-grid-data-grid-top-scroll-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with top scrollbar (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-top-scroll-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataGridTopScrollExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected searchText = '';
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;

  #columnDefs: ColDef[] = [
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      field: 'name',
      headerName: 'Name',
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
  ];

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: (gridReadyEvent): void => {
          this.onGridReady(gridReadyEvent);
        },
        context: {
          enableTopScroll: true,
        },
      },
    });
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
  }

  protected searchApplied(searchText: string | void): void {
    this.searchText = searchText ?? '';

    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });
      const displayedRowCount = this.#gridApi.getDisplayedRowCount();
      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Fluid grid with basic setup

**Selector:** `app-layout-fluid-grid-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyFluidGridGutterSizeType, SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Fluid grid with basic setup
 */
@Component({
  selector: 'app-layout-fluid-grid-example',
  templateUrl: './example.component.html',
  styles: [
    `
      .highlight-columns .sky-column {
        background-color: #97eced;
        border: 1px solid #56e0e1;
        overflow-wrap: break-word;
      }
    `,
  ],
  imports: [SkyFluidGridModule],
})
export class LayoutFluidGridExampleComponent {
  public gutterSize: SkyFluidGridGutterSizeType | undefined;
  public disableMargin = false;
}

```

**Template:**

```html
<div class="highlight-columns">
  <sky-fluid-grid
    data-sky-id="fluid-grid"
    [disableMargin]="disableMargin"
    [gutterSize]="gutterSize"
  >
    <sky-row data-sky-id="test-row">
      <sky-column data-sky-id="test-column" [screenSmall]="1">
        [screenSmall]="1"
      </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="5"> [screenSmall]="5" </sky-column>
      <sky-column [screenSmall]="7"> [screenSmall]="7" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="8"> [screenSmall]="8" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="9"> [screenSmall]="9" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="10"> [screenSmall]="10" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="11"> [screenSmall]="11" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column
        data-sky-id="dynamic-column"
        [screenXSmall]="6"
        [screenSmall]="8"
        [screenMedium]="9"
        [screenLarge]="10"
      >
        [screenXSmall]="6" [screenSmall]="8" [screenMedium]="9"
        [screenLarge]="10"
      </sky-column>
      <sky-column
        [screenXSmall]="6"
        [screenSmall]="4"
        [screenMedium]="3"
        [screenLarge]="2"
      >
        [screenXSmall]="6" [screenSmall]="4" [screenMedium]="3"
        [screenLarge]="2"
      </sky-column>
    </sky-row>

    <sky-row data-sky-id="reverse-row" [reverseColumnOrder]="true">
      <sky-column [screenSmall]="4"> First column </sky-column>
      <sky-column [screenSmall]="4"> Second column </sky-column>
      <sky-column [screenSmall]="4"> Third column </sky-column>
    </sky-row>
  </sky-fluid-grid>
</div>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
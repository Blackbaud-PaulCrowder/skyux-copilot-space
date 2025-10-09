                  

 Data grid
=========

Data grids provide a SKY UX-themed layout for tabular data. Combine data grids with [data managers](/skyux/components/data-manager.md) to allow users to manipulate larger data sets.

 Usage
------

### Use when

Use data grids to display large amounts of data when users need to compare values between rows or scan for specific values or outliers.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-do-use.fad6b74d8d400193ebcb4d2da75c6ca2.png)

Do use data grids to help users scan data and compare values.

### Don't use when

Don't use data grids to display content that requires a complex layout. To display multiple templated columns, visual content such as graphs or images, or content that users are likely to view in small viewports such as phones, use [repeaters](/skyux/components/repeater.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-dont-use.f169e260ec769cfb825d70f245529441.png)

Don't use data grids to display visual content or other complex layouts.

 Anatomy
--------

1

Header row

2

Row divider

3

[Data manager](/skyux/components/data-manager.md) toolbar (optional)

4

Filter bar (optional)

5

Item count (optional)

6

[Data manager](/skyux/components/data-manager.md) multiselect toolbar (optional)

7

Help button (optional)

8

Row selection checkbox (optional)

9

[Context-menu dropdown](/skyux/components/dropdown.md) button (optional)

10

Selected row (optional)

11

[Pagination](/skyux/components/paging.md) (optional)

12

[Summary action bar](/skyux/components/summary-action-bar.md) (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-anatomy.5b66888fcda4fff4c319b2d065ba4dd6.png)

 Options
--------

### Context-menu dropdown

To display actions that affect individual items in the data grid, use [context-menu dropdowns](/skyux/components/dropdown.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-context-menu.91ed3dcda87cfc85d5d950941e5c0df9.png)

### Help button

When you need to supplement a data grid column header with additional information but don't require persistent inline help, you can place a [help button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

### Filtering

To let users narrow down their list of items to a set they are interested in using structured criteria, use [filtering](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-filter.367e29dd3e23371a33221348e648acd9.png)

### Multiselect

To let users select and perform actions on multiple rows, use [data manager](/skyux/components/data-manager.md) and enable multiselect.

Only use multiselect when the data grid container is a page, full-page modal, or flyout. Don't use multiselect with data grids in tiles, page sections, or other containers that can flow off the screen.

To let users select or clear all rows and view only selected items, include the multiselect toolbar. To display actions that users can perform on selected rows, display the [summary action bar](/skyux/components/summary-action-bar.md) below the data grid.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-multiselect.199563ac5386ce05c04a735a27062470.png)

Do use multiselect to let users perform actions on multiple rows.

### Sorting

Make column headers sortable. Sort by the leftmost column or the primary record column in the data grid. Always indicate a data grid’s sort order.

Only include the [sort button](/skyux/components/sort.md) in the toolbar if the list includes other views in addition to the data grid (e.g., repeater) or it contains templated columns where users need to sort by another property in that column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-double-sort.77632d7a87b0698940263e1fc0075e5c.png)

Don't use a sort button if the list only uses data grid view and not templated columns. Rely on column headers for sorting.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-multiple-view-sort.b3261ef07efece81bc2c16f4edbe78b4.png)

Do use a sort button when there are other views of the data in addition to a data grid to supporting sorting in those views (without column headers).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-templated-sort.06353de653d2f2c63b6f11d725cde9ca.png)

Do use a sort button when there are templated columns to provide sort options for multiple properties within a single templated column (e.g., First name and last name).

### Templated items

To display composite information instead of single values, use templated columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-templated-items.98d8a20d65af6a50bcc3cf4922b96710.png)

 Behavior and states
--------------------

### Fit

The fit determines how to place data grids within their containers. If a container is wider than the data grid, the fit stretches the data grid to fill the container.

The `scroll` option provides a horizontal scrollbar when data grids are wider than their containers, while the `width` option resizes data grid columns to fit in the fixed width of the container. The `scroll` option is useful for data grids with many columns, and the `width` option is useful for simple grids in small containers where content fits neatly in the allotted space.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-grid/data-grid-horizontal-scroll.3e5dbeb192f699b79bb04fc5d11d9e12.png)

Data grids with many columns use horizontal scrollbars to fit in narrower containers.

### Reordering columns

To reorder columns, users can drag and drop them.

### Resizing columns

To resize columns, users can select and drag.

### Responsiveness

Data grids perform poorly in small viewports, such as mobile devices. Columns in fixed-width grids shrink to the point of being unreadable, and grids with horizontal scrollbars require a great deal of effort to view content. If you expect users to view content in small viewports, use [repeaters](/skyux/components/repeater.md) or another pattern instead.

 Related information
--------------------

### Components

*   [Data entry grid](/skyux/components/data-entry-grid.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Dropdown](/skyux/components/dropdown.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Paging](/skyux/components/paging.md)
*   [Repeater](/skyux/components/repeater.md)
*   [Sort](/skyux/components/sort.md)
*   [Summary action bar](/skyux/components/summary-action-bar.md)

### Guidelines

*   [Filter lists](/skyux/design/guidelines/filtering-lists.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)

 Installation
-------------

NPM package

`@skyux/ag-grid`[View in NPM](https://www.npmjs.com/package/@skyux/ag-grid) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/ag-grid/src/lib/modules/ag-grid/ag-grid.module.ts#L27) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/ag-grid`Copy None found.

 Setup
------

In addition to the `@skyux/ag-grid` package, you need to install the [`ag-grid-angular`](https://www.ag-grid.com/angular-grid/) and [`ag-grid-community`](https://www.npmjs.com/package/ag-grid-community) packages.

If you use the data entry grid with [the enterprise version of AG Grid instead of the free community version](https://www.ag-grid.com/documentation/angular/licensing/), the data entry grid turns on all enterprise features by default.

 AG Grid styles
---------------

To add the SKY UX styles for AG Grid to your SPA, run `ng g @skyux/packages:add-ag-grid-styles --project _my-app_`, which adds `"@skyux/ag-grid/css/sky-ag-grid.css"` to the `styles` section of your [`angular.json`](https://angular.io/guide/workspace-config#styles-and-scripts-configuration). For editable grids, include the class `sky-ag-grid-editable` on the `ag-grid-angular` element.

 AG Grid wrapper component
--------------------------

The `sky-ag-grid-wrapper` component provides WCAG-compliant keyboard navigation and sticky column headers for grids that use auto height. Use the `sky-ag-grid-wrapper` component to wrap all instances of `ag-grid-angular`. The wrapper does not constrain standard AG Grid functionality.

 Data manager directive
-----------------------

If you use a data entry grid within a [data manager component](/skyux/components/data-manager.md), the `skyAgGridDataManagerAdapter` directive can manage some standard interactions between the data entry grid and the data manager service. Add the directive should to the `sky-data-view` element that contains the data entry grid to initialize properties from the data state and keep the data entry grid in sync with the data state. When the data entry grid changes, the data state is updated, and when the data state changes, the data entry grid responds to the changes. The directive manages:

*   column visibility and order
*   selected rows
*   active sort state when selected by column header

Other properties of the data state, such as filters and applying the sort, still need to be implemented for each use.

 Passing cell editor parameters
-------------------------------

You can pass inputs to the SKY UX components used in cell editors via the [column definition's `cellEditorParams` property.](https://www.ag-grid.com/javascript-grid-column-properties/) The component properties are nested under `skyComponentProperties`. All component properties should be supported, and you can see the defined types by importing `SkyCellEditorDatepickerProperties` or `SkyCellEditorAutocompleteProperties`. `cellEditorParams` can also be a function that returns a param object for dynamic editing params. See the demo for examples of using an object or a function.

 Using other SKY UX components in columns
-----------------------------------------

For full control over a SKY UX component rendered in a cell, you can create your own [cell renderer](https://www.ag-grid.com/javascript-grid-cell-rendering-components/) and place the component inside it. For example, to include a context menu in your grid, you create a cell renderer and place the context menu in the cell renderer. See the demo for an example.

Additionally, you can inject content into a SKY UX template ref column type. This is especially useful for data entry grids with row actions that need to be usable while editing neighboring cells. See the code examples for more information.

 SkyAgGridModule
----------------

Type: Module

`import { SkyAgGridModule } from '@skyux/ag-grid';`

 SkyAgGridWrapperComponent
--------------------------

Type: Component

Selector: `sky-ag-grid-wrapper`

### Inputs

#### `compact: boolean`

Enable a compact layout for the grid when using modern theme. Compact layout uses a smaller font size and row height to display more data in a smaller space.

#### `minHeight: InputSignalWithTransform<number, unknown>`

The minimum height of the grid in pixels. The default value is `50`.

 SkyAgGridService
-----------------

Type: Service

`SkyAgGridService` provides methods to get AG Grid `gridOptions` to ensure grids match SKY UX functionality. The `gridOptions` can be overridden, and include registered SKY UX column types.

### Methods

#### `getEditableGridOptions(args: SkyGetGridOptionsArgs): GridOptions`

Returns [AG Grid `gridOptions`](https://www.ag-grid.com/javascript-grid-properties/) with default SKY UX options, styling, and cell editors registered for editable grids.

#### Parameters

##### `args: SkyGetGridOptionsArgs`

#### Returns

`GridOptions`

#### `getGridOptions(args: SkyGetGridOptionsArgs): GridOptions`

Returns [AG Grid `gridOptions`](https://www.ag-grid.com/javascript-grid-properties/) with default SKY UX options, styling, and cell renderers registered for read-only grids.

#### Parameters

##### `args: SkyGetGridOptionsArgs`

#### Returns

`GridOptions`

 SkyGetGridOptionsArgs
----------------------

Type: Interface

    interface SkyGetGridOptionsArgs {
      dateFormat?: string;
      gridOptions: GridOptions;
      locale?: string;
    }

### Properties

#### `dateFormat?: string`

The format to use for formatting date strings in the `SkyCellType.Date` column.

#### `gridOptions: GridOptions`

The [AG Grid `gridOptions`](https://www.ag-grid.com/javascript-grid-properties/) that override default SKY UX `gridOptions`. SKY UX column types for components and column `cellClassRules` enforce required cell styling and cannot be overridden.

#### `locale?: string`

The locale for location-specific formatting, such as date values for the `SkyCellType.Date` column.

 SkyAgGridRowDeleteDirective
----------------------------

Type: Directive

Selector: `[skyAgGridRowDelete]`

### Inputs

#### `rowDeleteIds: ModelSignal<string[]>`

The IDs of the data in the rows where the inline delete appears.

### Outputs

#### `rowDeleteCancel: OutputEmitterRef<SkyAgGridRowDeleteCancelArgs>`

Emits a `SkyAgGridRowDeleteCancelArgs` object when a row's inline delete is cancelled.

#### `rowDeleteConfirm: OutputEmitterRef<SkyAgGridRowDeleteConfirmArgs>`

Emits a `SkyAgGridRowDeleteConfirmArgs` object when a row's inline delete is confirmed.

 SkyAgGridRowDeleteConfirmArgs
------------------------------

Type: Interface

Information regarding a row whose deletion has been confirmed.

    interface SkyAgGridRowDeleteConfirmArgs {
      id: string;
    }

### Properties

#### `id: string`

The id of the data in the row whose deletion has been confirmed.

 SkyAgGridRowDeleteCancelArgs
-----------------------------

Type: Interface

Information regarding a row whose deletion has been cancelled.

    interface SkyAgGridRowDeleteCancelArgs {
      id: string;
    }

### Properties

#### `id: string`

The id of the data in the row whose deletion has been cancelled.

 SkyAgGridCellEditorInitialAction
---------------------------------

Type: Enumeration

The initial action that a cell editor should take when initialized.

    enum SkyAgGridCellEditorInitialAction {
      Delete = 0,
      Highlighted = 1,
      Replace = 2,
      Untouched = 3,
    }

### Properties

#### `SkyAgGridCellEditorInitialAction.Delete`

The cell should be cleared.

#### `SkyAgGridCellEditorInitialAction.Highlighted`

The cell value should be highlighted.

#### `SkyAgGridCellEditorInitialAction.Replace`

The cell value should be replaced with the initializing value.

#### `SkyAgGridCellEditorInitialAction.Untouched`

The cell should not be modified and the cursor is placed at the end of the value.

 SkyAgGridCellEditorUtils
-------------------------

Type: Class

### Methods

#### `SkyAgGridCellEditorUtils.getEditorInitialAction(params: ICellEditorParams<any, any, any> | undefined): SkyAgGridCellEditorInitialAction`

Gets the initial action that a cell editor should take when initialized.

#### Parameters

##### `params: ICellEditorParams<any, any, any> | undefined`

The editor's initializing parameters.

#### Returns

`SkyAgGridCellEditorInitialAction`

#### `SkyAgGridCellEditorUtils.subtractOrZero(minuend: null | number | undefined, subtrahend: number): number`

Returns the difference between the minuend and subtrahend. If the minuend is not defined, returns 0.

#### Parameters

##### `minuend: null | number | undefined`

The number from which another number is subtracted.

##### `subtrahend: number`

The number that is subtracted from the minuend.

#### Returns

`number`

 SkyCellType
------------

Type: Enumeration

These column types can be used by setting the AG Grid [column definition `type`](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing) to one of the following values. Any [SKY UX component](/skyux/components.md) can be made into a [cell editor](https://www.ag-grid.com/javascript-grid-cell-editor/) or [cell renderer](https://www.ag-grid.com/javascript-grid-cell-rendering-components/) component. If you would like to use a component that does not have a column definition yet, please consider [contributing it](/skyux/contribute/contribution-process.md) to the SKY UX data entry grid module, or [file an issue](/skyux/contribute/contribution-process/file-issue.md) in the [`@skyux/ag-grid` repo](https://github.com/blackbaud/skyux-ag-grid).

    enum SkyCellType {
      Autocomplete = "skyCellAutocomplete",
      Currency = "skyCellCurrency",
      CurrencyValidator = "skyCellCurrencyValidator",
      Date = "skyCellDate",
      Lookup = "skyCellLookup",
      Number = "skyCellNumber",
      NumberValidator = "skyCellNumberValidator",
      RightAligned = "skyCellRightAligned",
      RowSelector = "skyCellRowSelector",
      Template = "skyCellTemplate",
      Text = "skyCellText",
      Validator = "skyCellValidator",
    }

### Properties

#### `SkyCellType.Autocomplete`

**Edit mode**

Cells in the column will be edited as [SKY UX autocomplete components](/skyux/components/autocomplete.md). You can set any of the autocomplete component's properties by passing `SkyCellEditorAutocompleteParams` in the [column definition's `cellEditorParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing). These params can be updated as other cell edits are made or [provided dynamically](https://www.ag-grid.com/javascript-grid-cell-editing/#dynamic-parameters) based on other cell values. See the demo for an example. Text can be entered and a value selected from the provided list.

**Read-only mode**

Cells the column will display the currently selected value's name property by default. If the autocomplete needs to show a different property or needs to be formatted in any way, you can [define a `valueFormatter`](https://www.ag-grid.com/javascript-grid-value-formatters/) on the column definition.

#### `SkyCellType.Currency`

**Edit mode**

Cells in the column will be edited as a currency amount.

**Read-only mode**

Formats the display as currency using [SKY UX numeric components](/skyux/components/numeric.md).

#### `SkyCellType.CurrencyValidator`

**Edit and read-only modes**

Combines [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Currency and [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator, where the value is displayed as a currency and passed to a validator function.

#### `SkyCellType.Date`

**Edit mode**

Cells in the column will be edited as [SKY UX datepicker components](/skyux/components/datepicker.md). You can set any of the datepicker component's properties by passing `SkyCellEditorDatepickerParams` in the [column definition's `cellEditorParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing). These params can be updated as other cell edits are made or [provided dynamically](https://www.ag-grid.com/javascript-grid-cell-editing/#dynamic-parameters) based on other cell values. See the demo for an example. Date values can be entered.

**Read-only mode**

Cells in the column will display the currently selected date formatted as `MM-DD-YYYY`, or the date format of the locale passed to `getGridOptions()`. If you would like to overwrite this format, you can [define a `valueFormatter`](https://www.ag-grid.com/javascript-grid-value-formatters/) on the column definition. See the demo for an example.

#### `SkyCellType.Lookup`

**Edit mode**

Cells in the column will be edited as [SKY UX lookup components](https://developer.blackbaud.com/skyux-v5/components/lookup). You can set any of the lookup component's properties by passing `SkyCellEditorLookupParams` in the [column definition's `cellEditorParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing). These params can be updated as other cell edits are made or [provided dynamically](https://www.ag-grid.com/javascript-grid-cell-editing/#dynamic-parameters) based on other cell values. See the demo for an example. Text can be entered and a value selected from the provided list.

**Read-only mode**

Cells the column will display, by default, either: the name(s) of the selected value(s) if there are less than 6, or a summary count of the values if there are more than 5. If the lookup needs to show a different property or needs to be formatted in any way, you can [define a `valueFormatter`](https://www.ag-grid.com/javascript-grid-value-formatters/) on the column definition.

#### `SkyCellType.Number`

**Edit mode**

Cells in the column will be edited as HTML number `inputs`. Only numbers can be entered.

**Read-only mode**

Cells in the column will render as the number value.

#### `SkyCellType.NumberValidator`

**Edit and read-only modes**

Combines [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Number and [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator, where the value is displayed as a number and passed to a validator function.

#### `SkyCellType.RightAligned`

**Edit and read-only modes**

The header and cells in the column will render right aligned.

#### `SkyCellType.RowSelector`

**Edit and read-only modes**

Cells in the column will render as [SKY UX checkbox components](/skyux/components/checkbox.md). It allows the user to select multiple rows, and adds a highlight to selected rows. The [Ag Grid `rowNode`](https://www.ag-grid.com/javascript-grid-row-node/) will be updated to reflect the selected state.

#### `SkyCellType.Template`

**Read-only mode**

Cells in the column will render in a `TemplateRef` passed in the column definition's `cellRendererParams.template` property, with `value` and `row` context. See the demo for an example.

#### `SkyCellType.Text`

**Edit mode**

Cells in the column will be edited as HTML text `inputs`. Any characters can be entered.

**Read-only mode**

Cells in the column will render as their string value.

#### `SkyCellType.Validator`

**Edit and read-only modes**

Cells in the column will be passed to a validator function that flags erroneous entries. You can set the validator function and message by passing a `SkyAgGridValidatorProperties` object as `skyComponentProperties` to [column definition's `cellRendererParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing), like `skyComponentProperties.validator` and `skyComponentProperties.validatorMessage`. [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator can be combined with other cell types, such as [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Autocomplete or [SkyCellType](/skyux/components/data-grid?docs-active-tab=design#enum_sky-cell-type.md).Date, by using the array syntax for the [column definition's `type` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing).

 SkyAgGridHeaderInfo
--------------------

Type: Service

To display a help button beside the column header, create a component containing [`sky-help-inline`](/skyux/components/help-inline.md), and inject SkyAgGridHeaderInfo to access the column information, such as display name. Add the component to the `headerComponentParams.inlineHelpComponent` property of the [column definition](https://www.ag-grid.com/angular-data-grid/column-definitions/).

### Properties

#### `column: Column<any> | undefined`

[Column information from AG Grid](https://www.ag-grid.com/angular-data-grid/column-object/).

#### `context: any`

AG Grid's [`context` field](https://www.ag-grid.com/angular-data-grid/context/).

#### `displayName: string | undefined`

Display name of the column.

 SkyAgGridHeaderParams
----------------------

Type: Interface

Interface to use for the [`headerComponentParams`](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-header-headerComponentParams) property on `ColDef`.

    interface SkyAgGridHeaderParams {
      headerHidden?: boolean;
      inlineHelpComponent?: Type<unknown>;
    }

### Properties

#### `headerHidden?: boolean`

Hides the column header text. Each column should have a `headerName` defined in the column definition for accessibility. This option allows that text to be hidden from view while still being available to screen readers.

#### `inlineHelpComponent?: Type<unknown>`

The component to display as inline help beside the column header.

 SkyAgGridHeaderGroupInfo
-------------------------

Type: Service

To display a help button beside the column group header, create a component containing [`sky-help-inline`](/skyux/components/help-inline.md), and inject SkyAgGridHeaderGroupInfo to access the column group information, such as display name. Add the component to the `headerGroupComponentParams.inlineHelpComponent` property of the [column group definition](https://www.ag-grid.com/angular-data-grid/column-groups/).

### Properties

#### `columnGroup: ColumnGroup<any> | undefined`

[Column group information from AG Grid](https://www.ag-grid.com/angular-data-grid/column-object-group/).

#### `context: any`

AG Grid's [`context` field](https://www.ag-grid.com/angular-data-grid/context/).

#### `displayName: string | undefined`

Display name of the column group.

 SkyAgGridHeaderGroupParams
---------------------------

Type: Interface

Interface to use for the [`headerGroupComponentParams`](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-groupsHeader-headerGroupComponentParams) property on `ColGroupDef`.

    interface SkyAgGridHeaderGroupParams {
      inlineHelpComponent?: Type<unknown>;
    }

### Properties

#### `inlineHelpComponent?: Type<unknown>`

The component to display as inline help beside the column group header.

 SkyAgGridAutocompleteProperties
--------------------------------

Type: Interface

    interface SkyAgGridAutocompleteProperties {
      allowAnyValue?: boolean;
      data?: unknown[];
      debounceTime?: number;
      descriptorProperty?: string;
      highlightSearchText?: boolean;
      propertiesToSearch?: string[];
      search?: (searchText: string, data?: unknown[]) => unknown[] | Promise<unknown[]>;
      searchFilters?: ((searchText: string, item: unknown) => boolean)[];
      searchResultsLimit?: number;
      searchResultTemplate?: TemplateRef<unknown>;
      searchTextMinimumCharacters?: number;
      selectionChange?: (event: SkyAutocompleteSelectionChange) => void;
    }

### Properties

#### `allowAnyValue?: boolean`

Allows users to specify arbitrary values not in the search results.

#### `data?: unknown[]`

The static data source for the autocomplete cell to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use search instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime?: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

#### `descriptorProperty?: string`

The object property to display in the text input after users select an item in the dropdown list.

#### `highlightSearchText?: boolean`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

#### `propertiesToSearch?: string[]`

The array of object properties to search when utilizing the `data` property and the built-in search function.

#### `search?: (searchText: string, data?: unknown[]) => unknown[] | Promise<unknown[]>`

The function that dynamically manages the data to display in search results when users change the text in the autocomplete cell. The search function must return an array or a promise of an array.

#### `searchFilters?: ((searchText: string, item: unknown) => boolean)[]`

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultsLimit?: number`

The maximum number of search results to display in the dropdown list. By default, the autocomplete component displays all matching results.

#### `searchResultTemplate?: TemplateRef<unknown>`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchTextMinimumCharacters?: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

#### `selectionChange?: (event: SkyAutocompleteSelectionChange) => void`

Output that fires when users select items in the dropdown list.

 SkyAutocompleteProperties
--------------------------

Type: Interface

Warning: **Deprecated.** Use [SkyAgGridAutocompleteProperties](/skyux/components/data-grid?docs-active-tab=design#interface_sky-ag-grid-autocomplete-properties.md) instead.

    interface SkyAutocompleteProperties {
      allowAnyValue?: boolean;
      data?: unknown[];
      debounceTime?: number;
      descriptorProperty?: string;
      highlightSearchText?: boolean;
      propertiesToSearch?: string[];
      search?: (searchText: string, data?: unknown[]) => unknown[] | Promise<unknown[]>;
      searchFilters?: ((searchText: string, item: unknown) => boolean)[];
      searchResultsLimit?: number;
      searchResultTemplate?: TemplateRef<unknown>;
      searchTextMinimumCharacters?: number;
      selectionChange?: (event: SkyAutocompleteSelectionChange) => void;
    }

### Properties

#### `allowAnyValue?: boolean`

Allows users to specify arbitrary values not in the search results.

#### `data?: unknown[]`

The static data source for the autocomplete cell to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use search instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime?: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

#### `descriptorProperty?: string`

The object property to display in the text input after users select an item in the dropdown list.

#### `highlightSearchText?: boolean`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

#### `propertiesToSearch?: string[]`

The array of object properties to search when utilizing the `data` property and the built-in search function.

#### `search?: (searchText: string, data?: unknown[]) => unknown[] | Promise<unknown[]>`

The function that dynamically manages the data to display in search results when users change the text in the autocomplete cell. The search function must return an array or a promise of an array.

#### `searchFilters?: ((searchText: string, item: unknown) => boolean)[]`

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultsLimit?: number`

The maximum number of search results to display in the dropdown list. By default, the autocomplete component displays all matching results.

#### `searchResultTemplate?: TemplateRef<unknown>`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchTextMinimumCharacters?: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

#### `selectionChange?: (event: SkyAutocompleteSelectionChange) => void`

Output that fires when users select items in the dropdown list.

 SkyCellEditorAutocompleteParams
--------------------------------

Type: Interface

    interface SkyCellEditorAutocompleteParams {
      skyComponentProperties?: SkyAgGridAutocompleteProperties | SkyAutocompleteProperties;
    }

### Properties

#### `skyComponentProperties?: SkyAgGridAutocompleteProperties | SkyAutocompleteProperties`

The parameters provided to the autocomplete component.

 SkyAgGridCurrencyProperties
----------------------------

Type: Interface

    interface SkyAgGridCurrencyProperties {
      currencySymbol?: string;
      decimalPlaces?: string | number;
      negativeBracketsTypeOnBlur?: null | "(,)" | "[,]" | "<,>" | "{,}" | "〈,〉" | "｢,｣" | "⸤,⸥" | "⟦,⟧" | "‹,›" | "«,»";
    }

### Properties

#### `currencySymbol?: string`

The currency symbol to display in the cell.

#### `decimalPlaces?: string | number`

The number of decimal places to display on the currency.

#### `negativeBracketsTypeOnBlur?: null | "(,)" | "[,]" | "<,>" | "{,}" | "〈,〉" | "｢,｣" | "⸤,⸥" | "⟦,⟧" | "‹,›" | "«,»"`

Adds the specified brackets around negative values when unfocused.

 SkyAgGridDatepickerProperties
------------------------------

Type: Interface

    interface SkyAgGridDatepickerProperties {
      dateFormat?: string;
      disabled?: boolean;
      maxDate?: Date;
      minDate?: Date;
      skyDatepickerNoValidate?: boolean;
      startingDay?: number;
    }

### Properties

#### `dateFormat?: string`

The date format for the input.

#### `disabled?: boolean`

Whether to disable the datepicker cell.

#### `maxDate?: Date`

The latest date that is available in the calendar.

#### `minDate?: Date`

The earliest date that is available in the calendar. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate?: boolean`

Whether to disable date validation on the datepicker input.

#### `startingDay?: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday.

 SkyDatepickerProperties
------------------------

Type: Interface

Warning: **Deprecated.** Use [SkyAgGridDatepickerProperties](/skyux/components/data-grid?docs-active-tab=design#interface_sky-ag-grid-datepicker-properties.md) instead.

    interface SkyDatepickerProperties {
      dateFormat?: string;
      disabled?: boolean;
      maxDate?: Date;
      minDate?: Date;
      skyDatepickerNoValidate?: boolean;
      startingDay?: number;
    }

### Properties

#### `dateFormat?: string`

The date format for the input.

#### `disabled?: boolean`

Whether to disable the datepicker cell.

#### `maxDate?: Date`

The latest date that is available in the calendar.

#### `minDate?: Date`

The earliest date that is available in the calendar. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate?: boolean`

Whether to disable date validation on the datepicker input.

#### `startingDay?: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday.

 SkyCellEditorDatepickerParams
------------------------------

Type: Interface

    interface SkyCellEditorDatepickerParams {
      skyComponentProperties?: SkyAgGridDatepickerProperties | SkyDatepickerProperties;
    }

### Properties

#### `skyComponentProperties?: SkyAgGridDatepickerProperties | SkyDatepickerProperties`

The parameters provided to the datepicker component.

 SkyAgGridLookupProperties
--------------------------

Type: Interface

    interface SkyAgGridLookupProperties {
      addClick?: (args: SkyLookupAddClickEventArgs) => void;
      ariaLabel?: string;
      ariaLabelledBy?: string;
      autocompleteAttribute?: string;
      data?: unknown[];
      debounceTime?: number;
      descriptorProperty?: string;
      disabled?: boolean;
      enableShowMore?: boolean;
      idProperty?: string;
      placeholderText?: string;
      propertiesToSearch?: string[];
      search?: SkyAutocompleteSearchFunction;
      searchAsync?: (args: SkyAutocompleteSearchAsyncArgs) => void;
      searchFilters?: SkyAutocompleteSearchFunctionFilter[];
      searchResultsLimit?: number;
      searchResultTemplate?: TemplateRef<unknown>;
      searchTextMinimumCharacters?: number;
      selectMode?: SkyLookupSelectModeType;
      showAddButton?: boolean;
      showMoreConfig?: SkyLookupShowMoreConfig;
    }

### Properties

#### `addClick?: (args: SkyLookupAddClickEventArgs) => void`

Fires when users select the button to add options to the list.

#### `ariaLabel?: string`

The `aria-label` text for the lookup cell. If neither `ariaLabel` nor `ariaLabelledBy` are specified, the `aria-label` defaults to the column's `headerName`, `headerTooltip`, `field`, or `colId`.

#### `ariaLabelledBy?: string`

The ID of the HTML element that labels the lookup cell. If neither `ariaLabel` nor `ariaLabelledBy` are specified, the `aria-label` defaults to the column's `headerName`, `headerTooltip`, `field`, or `colId`.

#### `autocompleteAttribute?: string`

The value to provide to the autocomplete attribute on the form input.

#### `data?: unknown[]`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide data to the lookup component.

The data source for the lookup cell to search when users enter text. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime?: number`

How many milliseconds to wait before searching while users enter text in the lookup field.

#### `descriptorProperty?: string`

The object property to display in the text input after users select an item in the dropdown list.

#### `disabled?: boolean`

Whether to disable the lookup cell.

#### `enableShowMore?: boolean`

Whether to enable users to open a picker where they can view all options.

#### `idProperty?: string`

The property that represents the object's unique identifier. Specifying this property enables token animations and more efficient rendering. This property is required when using `enableShowMore` and `searchAsync` together.

#### `placeholderText?: string`

Placeholder text to display in the lookup field.

#### `propertiesToSearch?: string[]`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide data to the lookup component.

The array of object properties to search when using the `data` property and the built-in search function.

#### `search?: SkyAutocompleteSearchFunction`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide searched data to the lookup component.

The function that dynamically manages the data to display in search results when users change the text in the lookup cell. The search function must return an array or a promise of an array.

#### `searchAsync?: (args: SkyAutocompleteSearchAsyncArgs) => void`

Fires when users enter new search information and allows results to be returned via an observable. The event is also fired when the "Show more" picker is opened without search text.

#### `searchFilters?: SkyAutocompleteSearchFunctionFilter[]`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide searched data to the lookup component.

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultsLimit?: number`

The maximum number of search results to display in the dropdown list. By default, the lookup component displays all matching results. This property has no effect on the results in the "Show more" picker.

#### `searchResultTemplate?: TemplateRef<unknown>`

The template that formats each option in the dropdown list. The lookup component injects values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchTextMinimumCharacters?: number`

The minimum number of characters that users must enter before the lookup component searches the data source and displays search results in the dropdown list.

#### `selectMode?: SkyLookupSelectModeType`

The ability for users to select one option or multiple options.

#### `showAddButton?: boolean`

Whether to display a button that lets users add options to the list.

#### `showMoreConfig?: SkyLookupShowMoreConfig`

Configuration options for the picker that displays all options.

 SkyCellEditorLookupParams
--------------------------

Type: Interface

    interface SkyCellEditorLookupParams {
      skyComponentProperties?: SkyAgGridLookupProperties;
    }

### Properties

#### `skyComponentProperties?: SkyAgGridLookupProperties`

The parameters provided to the lookup component.

 SkyAgGridNumberProperties
--------------------------

Type: Interface

    interface SkyAgGridNumberProperties {
      max?: number;
      min?: number;
    }

### Properties

#### `max?: number`

The maximum number that users can enter in the cell.

#### `min?: number`

The minimum number that users can enter in the cell.

 SkyAgGridTextProperties
------------------------

Type: Interface

    interface SkyAgGridTextProperties {
      maxlength?: number;
    }

### Properties

#### `maxlength?: number`

The maximum length of the text that users can enter into the cell.

 SkyAgGridValidatorProperties
-----------------------------

Type: Interface

    interface SkyAgGridValidatorProperties {
      validator?: (value: unknown, data?: unknown, rowIndex?: null | number) => boolean;
      validatorMessage?: string | ((value: unknown, data?: unknown, rowIndex?: null | number) => string);
      valueResourceObservable?: (value: unknown, data?: unknown, rowIndex?: null | number) => Observable<string>;
    }

### Properties

#### `validator?: (value: unknown, data?: unknown, rowIndex?: null | number) => boolean`

A function that returns true if the value is valid, or false if it is not. Invalid values will be highlighted and display a validation message.

#### `validatorMessage?: string | ((value: unknown, data?: unknown, rowIndex?: null | number) => string)`

Either a string or a function that returns a string. The message to display when the value is invalid.

#### `valueResourceObservable?: (value: unknown, data?: unknown, rowIndex?: null | number) => Observable<string>`

An optional function that returns an observable that emits a string. Can be used with resources to localize the value displayed in the cell.
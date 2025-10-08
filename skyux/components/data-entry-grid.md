# Design

                  Skip to Main Content

 Data entry grid
===============

Data entry grids use the third-party [AG Grid library](https://www.ag-grid.com/angular-getting-started/) to provide a spreadsheet-like user interface to enter and edit large amounts of data. SKY UX provides styles, a service for default grid options, and components to render and edit cells. To learn about AG Grid and its capabilities, see the [getting-started guide](https://www.ag-grid.com/angular-getting-started/) and [additional documentation.](https://www.ag-grid.com/documentation-main/documentation.php)

 Usage
------

### Use when

Use data entry grids when:

*   Users have experience working with spreadsheets.
*   Users edit many values at the same time.
*   The dataset is large.

### Don't use when

Don't use data entry grids when:

*   Data is view-only. Use [data grid](/skyux/components/data-grid.md) instead.
*   Users need guidance for the task they are completing.
*   Users only edit a small number of values at a time.
*   The dataset is small.

 Anatomy
--------

1

Header cell

2

Editable cell

3

Focused cell

4

Help button (optional)

5

Read-only cell (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/anatomy.1d30011d0909147c5dc28b47af1a27ce.png)

 Options
--------

### Disabled columns

To prevent users from editing the data in particular columns, disable the columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-disabled.b5acebc7cd358d14d1a2670ceb9c40c7.png)

### Help button

When you need to supplement a data entry grid column header with additional information but don't require persistent inline help, you can place a [help button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

### Validation

To call attention to incorrect formats in cells, such as incorrect dates or currency values, enable validation. The component handles the styling automatically, so you don't need to worry about rendering the styling, but you do need to provide validation messages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-validation.3516b3b12310f005becf240cce76d1c6.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Currency and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator, where the value is displayed as a currency and passed to a validator function.

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Number and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator, where the value is displayed as a number and passed to a validator function.

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

Cells in the column will be passed to a validator function that flags erroneous entries. You can set the validator function and message by passing a `SkyAgGridValidatorProperties` object as `skyComponentProperties` to [column definition's `cellRendererParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing), like `skyComponentProperties.validator` and `skyComponentProperties.validatorMessage`. [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Validator can be combined with other cell types, such as [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Autocomplete or [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=design#enum_sky-cell-type.md).Date, by using the array syntax for the [column definition's `type` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing).

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

Warning: **Deprecated.** Use [SkyAgGridAutocompleteProperties](/skyux/components/data-entry-grid?docs-active-tab=design#interface_sky-ag-grid-autocomplete-properties.md) instead.

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

Warning: **Deprecated.** Use [SkyAgGridDatepickerProperties](/skyux/components/data-entry-grid?docs-active-tab=design#interface_sky-ag-grid-datepicker-properties.md) instead.

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

# Development

                  Skip to Main Content

 Data entry grid
===============

Data entry grids use the third-party [AG Grid library](https://www.ag-grid.com/angular-getting-started/) to provide a spreadsheet-like user interface to enter and edit large amounts of data. SKY UX provides styles, a service for default grid options, and components to render and edit cells. To learn about AG Grid and its capabilities, see the [getting-started guide](https://www.ag-grid.com/angular-getting-started/) and [additional documentation.](https://www.ag-grid.com/documentation-main/documentation.php)

 Usage
------

### Use when

Use data entry grids when:

*   Users have experience working with spreadsheets.
*   Users edit many values at the same time.
*   The dataset is large.

### Don't use when

Don't use data entry grids when:

*   Data is view-only. Use [data grid](/skyux/components/data-grid.md) instead.
*   Users need guidance for the task they are completing.
*   Users only edit a small number of values at a time.
*   The dataset is small.

 Anatomy
--------

1

Header cell

2

Editable cell

3

Focused cell

4

Help button (optional)

5

Read-only cell (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/anatomy.1d30011d0909147c5dc28b47af1a27ce.png)

 Options
--------

### Disabled columns

To prevent users from editing the data in particular columns, disable the columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-disabled.b5acebc7cd358d14d1a2670ceb9c40c7.png)

### Help button

When you need to supplement a data entry grid column header with additional information but don't require persistent inline help, you can place a [help button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

### Validation

To call attention to incorrect formats in cells, such as incorrect dates or currency values, enable validation. The component handles the styling automatically, so you don't need to worry about rendering the styling, but you do need to provide validation messages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-validation.3516b3b12310f005becf240cce76d1c6.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Currency and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Validator, where the value is displayed as a currency and passed to a validator function.

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Number and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Validator, where the value is displayed as a number and passed to a validator function.

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

Cells in the column will be passed to a validator function that flags erroneous entries. You can set the validator function and message by passing a `SkyAgGridValidatorProperties` object as `skyComponentProperties` to [column definition's `cellRendererParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing), like `skyComponentProperties.validator` and `skyComponentProperties.validatorMessage`. [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Validator can be combined with other cell types, such as [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Autocomplete or [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=development#enum_sky-cell-type.md).Date, by using the array syntax for the [column definition's `type` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing).

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

Warning: **Deprecated.** Use [SkyAgGridAutocompleteProperties](/skyux/components/data-entry-grid?docs-active-tab=development#interface_sky-ag-grid-autocomplete-properties.md) instead.

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

Warning: **Deprecated.** Use [SkyAgGridDatepickerProperties](/skyux/components/data-entry-grid?docs-active-tab=development#interface_sky-ag-grid-datepicker-properties.md) instead.

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

# Examples

                                Skip to Main Content

 Data entry grid
===============

Data entry grids use the third-party [AG Grid library](https://www.ag-grid.com/angular-getting-started/) to provide a spreadsheet-like user interface to enter and edit large amounts of data. SKY UX provides styles, a service for default grid options, and components to render and edit cells. To learn about AG Grid and its capabilities, see the [getting-started guide](https://www.ag-grid.com/angular-getting-started/) and [additional documentation.](https://www.ag-grid.com/documentation-main/documentation.php)

Usage
------

### Use when

Use data entry grids when:

*   Users have experience working with spreadsheets.
*   Users edit many values at the same time.
*   The dataset is large.

### Don't use when

Don't use data entry grids when:

*   Data is view-only. Use [data grid](/skyux/components/data-grid.md) instead.
*   Users need guidance for the task they are completing.
*   Users only edit a small number of values at a time.
*   The dataset is small.

 Anatomy
--------

1

Header cell

2

Editable cell

3

Focused cell

4

Help button (optional)

5

Read-only cell (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/anatomy.1d30011d0909147c5dc28b47af1a27ce.png)

 Options
--------

### Disabled columns

To prevent users from editing the data in particular columns, disable the columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-disabled.b5acebc7cd358d14d1a2670ceb9c40c7.png)

### Help button

When you need to supplement a data entry grid column header with additional information but don't require persistent inline help, you can place a [help button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

### Validation

To call attention to incorrect formats in cells, such as incorrect dates or currency values, enable validation. The component handles the styling automatically, so you don't need to worry about rendering the styling, but you do need to provide validation messages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/data-entry-grid/options-validation.3516b3b12310f005becf240cce76d1c6.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Data manager](/skyux/components/data-manager.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Currency and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Validator, where the value is displayed as a currency and passed to a validator function.

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

Combines [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Number and [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Validator, where the value is displayed as a number and passed to a validator function.

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

Cells in the column will be passed to a validator function that flags erroneous entries. You can set the validator function and message by passing a `SkyAgGridValidatorProperties` object as `skyComponentProperties` to [column definition's `cellRendererParams` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing), like `skyComponentProperties.validator` and `skyComponentProperties.validatorMessage`. [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Validator can be combined with other cell types, such as [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Autocomplete or [SkyCellType](/skyux/components/data-entry-grid?docs-active-tab=examples#enum_sky-cell-type.md).Date, by using the array syntax for the [column definition's `type` property](https://www.ag-grid.com/angular-data-grid/column-properties/#reference-editing).

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

Warning: **Deprecated.** Use [SkyAgGridAutocompleteProperties](/skyux/components/data-entry-grid?docs-active-tab=examples#interface_sky-ag-grid-autocomplete-properties.md) instead.

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

Warning: **Deprecated.** Use [SkyAgGridDatepickerProperties](/skyux/components/data-entry-grid?docs-active-tab=examples#interface_sky-ag-grid-datepicker-properties.md) instead.

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

### Basic setup (without data manager)

Edit in StackBlitz

Edit

NameSort column Name, not currently sorted

AgeSort column Age, not currently sorted

Start dateSort column Start date, currently ascending

End dateSort column End date, not currently sorted

DepartmentSort column Department, not currently sorted

TitleSort column Title, not currently sorted

Billy Bob

55

12/1/1994

N/A

Customer Support

Account Manager

Jane Deere

33

7/15/2009

N/A

Engineering

Principal Software Engineer

David Smith

51

1/1/2012

06/15/2018

Engineering

Product Manager

Emily Johnson

41

1/15/2014

N/A

Marketing

Events Manager

John Doe

38

9/1/2017

09/30/2017

Sales

Nicole Davidson

22

11/1/2019

N/A

Engineering

Software Engineer

Carl Roberts

23

11/1/2019

N/A

Engineering

UX Designer

to of

Page of

Show code

Copy

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
Copy

    import { ChangeDetectionStrategy, Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { AgGridDemoRow } from './data';
    
    @Component({
      selector: 'app-context-menu',
      templateUrl: './context-menu.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [SkyDropdownModule],
    })
    export class ContextMenuComponent implements ICellRendererAngularComp {
      protected contextMenuAriaLabel = '';
      protected deleteAriaLabel = '';
      protected markInactiveAriaLabel = '';
      protected moreInfoAriaLabel = '';
    
      #name: string | undefined;
    
      public agInit(params: ICellRendererParams<AgGridDemoRow>): void {
        this.#name = params.data?.name;
        this.contextMenuAriaLabel = `Context menu for ${this.#name}`;
        this.deleteAriaLabel = `Delete ${this.#name}`;
        this.markInactiveAriaLabel = `Mark ${this.#name} inactive`;
        this.moreInfoAriaLabel = `More info for ${this.#name}`;
      }
    
      public refresh(): boolean {
        return false;
      }
    
      protected actionClicked(action: string): void {
        console.error(`${action} clicked for ${this.#name}`);
      }
    }
Copy

    export interface AutocompleteOption {
      id: string;
      name: string;
    }
    
    export const DEPARTMENTS = [
      {
        id: '1',
        name: 'Marketing',
      },
      {
        id: '2',
        name: 'Sales',
      },
      {
        id: '3',
        name: 'Engineering',
      },
      {
        id: '4',
        name: 'Customer Support',
      },
    ];
    
    export const JOB_TITLES: Record<string, AutocompleteOption[]> = {
      Marketing: [
        {
          id: '1',
          name: 'Social Media Coordinator',
        },
        {
          id: '2',
          name: 'Blog Manager',
        },
        {
          id: '3',
          name: 'Events Manager',
        },
      ],
      Sales: [
        {
          id: '4',
          name: 'Business Development Representative',
        },
        {
          id: '5',
          name: 'Account Executive',
        },
      ],
      Engineering: [
        {
          id: '6',
          name: 'Software Engineer',
        },
        {
          id: '7',
          name: 'Senior Software Engineer',
        },
        {
          id: '8',
          name: 'Principal Software Engineer',
        },
        {
          id: '9',
          name: 'UX Designer',
        },
        {
          id: '10',
          name: 'Product Manager',
        },
      ],
      'Customer Support': [
        {
          id: '11',
          name: 'Customer Support Representative',
        },
        {
          id: '12',
          name: 'Account Manager',
        },
        {
          id: '13',
          name: 'Customer Support Specialist',
        },
      ],
    };
    
    export interface AgGridDemoRow {
      selected?: boolean;
      name: string;
      age: number;
      startDate: Date;
      endDate?: Date;
      department: AutocompleteOption;
      jobTitle?: AutocompleteOption;
    }
    
    export const AG_GRID_DEMO_DATA: AgGridDemoRow[] = [
      {
        selected: true,
        name: 'Billy Bob',
        age: 55,
        startDate: new Date('12/1/1994'),
        department: DEPARTMENTS[3],
        jobTitle: JOB_TITLES['Customer Support'][1],
      },
      {
        selected: false,
        name: 'Jane Deere',
        age: 33,
        startDate: new Date('7/15/2009'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][2],
      },
      {
        selected: false,
        name: 'John Doe',
        age: 38,
        startDate: new Date('9/1/2017'),
        endDate: new Date('9/30/2017'),
        department: DEPARTMENTS[1],
      },
      {
        selected: false,
        name: 'David Smith',
        age: 51,
        startDate: new Date('1/1/2012'),
        endDate: new Date('6/15/2018'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][4],
      },
      {
        selected: true,
        name: 'Emily Johnson',
        age: 41,
        startDate: new Date('1/15/2014'),
        department: DEPARTMENTS[0],
        jobTitle: JOB_TITLES['Marketing'][2],
      },
      {
        selected: false,
        name: 'Nicole Davidson',
        age: 22,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][0],
      },
      {
        selected: false,
        name: 'Carl Roberts',
        age: 23,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][3],
      },
    ];
Copy

    import { AgGridDemoRow } from './data';
    
    export class EditModalContext {
      public gridData: AgGridDemoRow[] = [];
    }
Copy

    <sky-modal headingText="Edit employee information">
      <sky-modal-content>
        <sky-ag-grid-wrapper>
          <ag-grid-angular
            class="sky-ag-grid-editable"
            [gridOptions]="gridOptions"
            [rowData]="gridData"
          />
        </sky-ag-grid-wrapper>
      </sky-modal-content>
      <sky-modal-footer>
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="instance.save(gridData)"
        >
          Save
        </button>
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="instance.cancel()"
        >
          Cancel
        </button>
      </sky-modal-footer>
    </sky-modal>
    <ng-template #markInactiveAction let-value="value" let-row="row">
      <app-mark-inactive [name]="row?.name" />
    </ng-template>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      OnInit,
      TemplateRef,
      ViewChild,
      inject,
    } from '@angular/core';
    import {
      SkyAgGridAutocompleteProperties,
      SkyAgGridDatepickerProperties,
      SkyAgGridModule,
      SkyAgGridService,
      SkyCellType,
    } from '@skyux/ag-grid';
    import { SkyAutocompleteSelectionChange } from '@skyux/lookup';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridApi,
      GridOptions,
      GridReadyEvent,
      ICellEditorParams,
      IRowNode,
      ModuleRegistry,
      NewValueParams,
    } from 'ag-grid-community';
    
    import { AgGridDemoRow, DEPARTMENTS, JOB_TITLES } from './data';
    import { EditModalContext } from './edit-modal-context';
    import { MarkInactiveComponent } from './mark-inactive.component';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-edit-modal',
      templateUrl: './edit-modal.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [
        AgGridModule,
        SkyAgGridModule,
        SkyModalModule,
        MarkInactiveComponent,
      ],
    })
    export class EditModalComponent implements OnInit {
      @ViewChild('markInactiveAction', { static: true })
      protected markInactiveAction: TemplateRef<unknown> | undefined;
    
      protected gridData: AgGridDemoRow[];
      protected gridOptions: GridOptions | undefined;
    
      #gridApi: GridApi | undefined;
    
      protected readonly instance = inject(SkyModalInstance);
      readonly #agGridSvc = inject(SkyAgGridService);
      readonly #changeDetectorRef = inject(ChangeDetectorRef);
      readonly #context = inject(EditModalContext);
    
      constructor() {
        this.gridData = this.#context.gridData;
      }
    
      public ngOnInit(): void {
        const columnDefs: ColDef[] = [
          {
            colId: 'markInactiveAction',
            headerName: 'Mark inactive',
            type: SkyCellType.Template,
            editable: true,
            cellRendererParams: {
              template: this.markInactiveAction,
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
            cellEditorParams: {
              skyComponentProperties: {
                maxlength: 10,
              },
            },
            editable: true,
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
            cellEditorParams: {
              skyComponentProperties: {
                min: 18,
              },
            },
            editable: true,
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
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridDatepickerProperties } => {
              return { skyComponentProperties: { minDate: params.data.startDate } };
            },
          },
          {
            field: 'department',
            headerName: 'Department',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              return {
                skyComponentProperties: {
                  data: DEPARTMENTS,
                  selectionChange: (
                    change: SkyAutocompleteSelectionChange,
                  ): void => {
                    this.#departmentSelectionChange(change, params.node);
                  },
                },
              };
            },
            onCellValueChanged: (event: NewValueParams): void => {
              if (event.newValue !== event.oldValue) {
                this.#clearJobTitle(event.node);
              }
            },
          },
          {
            field: 'jobTitle',
            headerName: 'Title',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              const selectedDepartment = params.data?.department?.name;
    
              const editParams: {
                skyComponentProperties: SkyAgGridAutocompleteProperties;
              } = { skyComponentProperties: { data: [] } };
    
              if (selectedDepartment) {
                editParams.skyComponentProperties.data =
                  JOB_TITLES[selectedDepartment];
              }
    
              return editParams;
            },
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
            cellRendererParams: {
              skyComponentProperties: {
                validator: (value: Date): boolean =>
                  !!value && value > new Date(1985, 9, 26),
                validatorMessage: 'Please enter a future date',
              },
            },
            editable: true,
          },
        ];
    
        this.gridOptions = {
          columnDefs: columnDefs,
          onGridReady: (gridReadyEvent): void => {
            this.onGridReady(gridReadyEvent);
          },
        };
    
        this.gridOptions = this.#agGridSvc.getEditableGridOptions({
          gridOptions: this.gridOptions,
        });
    
        this.#changeDetectorRef.markForCheck();
      }
    
      public onGridReady(gridReadyEvent: GridReadyEvent): void {
        this.#gridApi = gridReadyEvent.api;
    
        this.#changeDetectorRef.markForCheck();
      }
    
      #departmentSelectionChange(
        change: SkyAutocompleteSelectionChange,
        node: IRowNode<AgGridDemoRow>,
      ): void {
        if (change.selectedItem && change.selectedItem !== node.data?.department) {
          this.#clearJobTitle(node);
        }
      }
    
      #clearJobTitle(node: IRowNode<AgGridDemoRow> | null): void {
        if (node?.data) {
          node.data.jobTitle = undefined;
          this.#changeDetectorRef.markForCheck();
    
          if (this.#gridApi) {
            this.#gridApi.refreshCells({ rowNodes: [node] });
          }
        }
      }
    }
Copy

    <sky-toolbar>
      <sky-toolbar-item>
        <button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
          Edit
        </button>
      </sky-toolbar-item>
      <sky-toolbar-item>
        <sky-search
          [debounceTime]="250"
          [searchText]="searchText"
          (searchApply)="searchApplied($event)"
          (searchChange)="searchApplied($event)"
          (searchClear)="searchApplied($event)"
        />
      </sky-toolbar-item>
    </sky-toolbar>
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [overlayNoRowsTemplate]="noRowsTemplate"
        [rowData]="gridData"
      />
    </sky-ag-grid-wrapper>
Copy

    <button
      type="button"
      class="sky-btn sky-btn-link-inline"
      [attr.aria-label]="markInactiveAriaLabel"
      (click)="markInactive()"
    >
      Mark inactive
    </button>
Copy

    import { ChangeDetectionStrategy, Component, Input } from '@angular/core';
    
    @Component({
      standalone: true,
      selector: 'app-mark-inactive',
      templateUrl: './mark-inactive.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
    })
    export class MarkInactiveComponent {
      @Input()
      public set name(value: string | undefined) {
        this.#_name = value;
        if (value) {
          this.markInactiveAriaLabel = `Mark ${value} inactive`;
        }
      }
    
      public get name(): string | undefined {
        return this.#_name;
      }
    
      protected markInactiveAriaLabel = '';
    
      #_name: string | undefined;
    
      protected markInactive(): void {
        console.error(`Mark inactive action clicked for ${this.name}`);
      }
    }

Copy

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
### Data manager setup

Edit in StackBlitz

Columns

Edit

Select all

Clear all

Show only selected items

       

NameSort column Name, not currently sorted

AgeSort column Age, not currently sorted

Start dateSort column Start date, currently ascending

End dateSort column End date, not currently sorted

DepartmentSort column Department, not currently sorted

TitleSort column Title, not currently sorted

Validation currencySort column Validation currency, not currently sorted

Billy Bob

55

12/1/1994

N/A

Customer Support

Account Manager

Jane Deere

33

7/15/2009

N/A

Engineering

Principal Software Engineer

David Smith

51

1/1/2012

06/15/2018

Engineering

Product Manager

Emily Johnson

41

1/15/2014

N/A

Marketing

Events Manager

John Doe

38

9/1/2017

09/30/2017

Sales

Account Executive

Nicole Davidson

22

11/1/2019

N/A

Engineering

Software Engineer

Carl Roberts

23

11/1/2019

N/A

Engineering

UX Designer

to of

Page of

Show code

Copy

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
Copy

    import { ChangeDetectionStrategy, Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { AgGridDemoRow } from './data';
    
    @Component({
      selector: 'app-context-menu',
      templateUrl: './context-menu.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [SkyDropdownModule],
    })
    export class ContextMenuComponent implements ICellRendererAngularComp {
      public contextMenuAriaLabel = '';
      public deleteAriaLabel = '';
      public markInactiveAriaLabel = '';
      public moreInfoAriaLabel = '';
    
      #name: string | undefined;
    
      public agInit(params: ICellRendererParams<AgGridDemoRow>): void {
        this.#name = params.data?.name;
        this.contextMenuAriaLabel = `Context menu for ${this.#name}`;
        this.deleteAriaLabel = `Delete ${this.#name}`;
        this.markInactiveAriaLabel = `Mark ${this.#name} inactive`;
        this.moreInfoAriaLabel = `More info for ${this.#name}`;
      }
    
      public refresh(): boolean {
        return false;
      }
    
      protected actionClicked(action: string): void {
        alert(`${action} clicked for ${this.#name}`);
      }
    }
Copy

    export interface AutocompleteOption {
      id: string;
      name: string;
    }
    
    export const DEPARTMENTS = [
      {
        id: '1',
        name: 'Marketing',
      },
      {
        id: '2',
        name: 'Sales',
      },
      {
        id: '3',
        name: 'Engineering',
      },
      {
        id: '4',
        name: 'Customer Support',
      },
    ];
    
    export const JOB_TITLES: Record<string, AutocompleteOption[]> = {
      Marketing: [
        {
          id: '1',
          name: 'Social Media Coordinator',
        },
        {
          id: '2',
          name: 'Blog Manager',
        },
        {
          id: '3',
          name: 'Events Manager',
        },
      ],
      Sales: [
        {
          id: '4',
          name: 'Business Development Representative',
        },
        {
          id: '5',
          name: 'Account Executive',
        },
      ],
      Engineering: [
        {
          id: '6',
          name: 'Software Engineer',
        },
        {
          id: '7',
          name: 'Senior Software Engineer',
        },
        {
          id: '8',
          name: 'Principal Software Engineer',
        },
        {
          id: '9',
          name: 'UX Designer',
        },
        {
          id: '10',
          name: 'Product Manager',
        },
      ],
      'Customer Support': [
        {
          id: '11',
          name: 'Customer Support Representative',
        },
        {
          id: '12',
          name: 'Account Manager',
        },
        {
          id: '13',
          name: 'Customer Support Specialist',
        },
      ],
    };
    
    export interface AgGridDemoRow {
      selected?: boolean;
      name: string;
      age: number;
      startDate: Date;
      endDate?: Date;
      department: AutocompleteOption;
      jobTitle?: AutocompleteOption;
    }
    
    export const AG_GRID_DEMO_DATA: AgGridDemoRow[] = [
      {
        selected: true,
        name: 'Billy Bob',
        age: 55,
        startDate: new Date('12/1/1994'),
        department: DEPARTMENTS[3],
        jobTitle: JOB_TITLES['Customer Support'][1],
      },
      {
        selected: false,
        name: 'Jane Deere',
        age: 33,
        startDate: new Date('7/15/2009'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][2],
      },
      {
        selected: false,
        name: 'John Doe',
        age: 38,
        startDate: new Date('9/1/2017'),
        endDate: new Date('9/30/2017'),
        department: DEPARTMENTS[1],
        jobTitle: JOB_TITLES['Sales'][1],
      },
      {
        selected: false,
        name: 'David Smith',
        age: 51,
        startDate: new Date('1/1/2012'),
        endDate: new Date('6/15/2018'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][4],
      },
      {
        selected: true,
        name: 'Emily Johnson',
        age: 41,
        startDate: new Date('1/15/2014'),
        department: DEPARTMENTS[0],
        jobTitle: JOB_TITLES['Marketing'][2],
      },
      {
        selected: false,
        name: 'Nicole Davidson',
        age: 22,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][0],
      },
      {
        selected: false,
        name: 'Carl Roberts',
        age: 23,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][3],
      },
    ];
Copy

    import { AgGridDemoRow } from './data';
    
    export class EditModalContext {
      public gridData: AgGridDemoRow[] = [];
    }
Copy

    <sky-modal headingText="Edit employee information">
      <sky-modal-content>
        <sky-ag-grid-wrapper>
          <ag-grid-angular
            class="sky-ag-grid-editable"
            [gridOptions]="gridOptions"
            [rowData]="gridData"
          />
        </sky-ag-grid-wrapper>
      </sky-modal-content>
      <sky-modal-footer>
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="instance.save(gridData)"
        >
          Save
        </button>
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="instance.cancel()"
        >
          Cancel
        </button>
      </sky-modal-footer>
    </sky-modal>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      inject,
    } from '@angular/core';
    import {
      SkyAgGridAutocompleteProperties,
      SkyAgGridDatepickerProperties,
      SkyAgGridModule,
      SkyAgGridService,
      SkyCellType,
    } from '@skyux/ag-grid';
    import { SkyAutocompleteSelectionChange } from '@skyux/lookup';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridApi,
      GridOptions,
      GridReadyEvent,
      ICellEditorParams,
      IRowNode,
      ModuleRegistry,
    } from 'ag-grid-community';
    
    import { AgGridDemoRow, DEPARTMENTS, JOB_TITLES } from './data';
    import { EditModalContext } from './edit-modal-context';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-edit-modal',
      templateUrl: './edit-modal.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [AgGridModule, SkyAgGridModule, SkyModalModule],
    })
    export class EditModalComponent {
      protected gridData: AgGridDemoRow[];
      protected gridOptions: GridOptions;
    
      #columnDefs: ColDef[];
      #gridApi: GridApi | undefined;
    
      protected readonly instance = inject(SkyModalInstance);
      readonly #agGridService = inject(SkyAgGridService);
      readonly #changeDetector = inject(ChangeDetectorRef);
      readonly #context = inject(EditModalContext);
    
      constructor() {
        this.#columnDefs = [
          {
            field: 'name',
            headerName: 'Name',
          },
          {
            field: 'age',
            headerName: 'Age',
            type: SkyCellType.Number,
            maxWidth: 60,
            editable: true,
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
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridDatepickerProperties } => {
              return {
                skyComponentProperties: {
                  minDate: params.data.startDate,
                },
              };
            },
          },
          {
            field: 'department',
            headerName: 'Department',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              return {
                skyComponentProperties: {
                  data: DEPARTMENTS,
                  selectionChange: (change): void => {
                    this.#departmentSelectionChange(change, params.node);
                  },
                },
              };
            },
            onCellValueChanged: (event): void => {
              if (event.newValue !== event.oldValue) {
                this.#clearJobTitle(event.node);
              }
            },
          },
          {
            field: 'jobTitle',
            headerName: 'Title',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              const selectedDepartment = params.data?.department?.name;
    
              const editParams: {
                skyComponentProperties: SkyAgGridAutocompleteProperties;
              } = { skyComponentProperties: { data: [] } };
    
              if (selectedDepartment) {
                editParams.skyComponentProperties.data =
                  JOB_TITLES[selectedDepartment];
              }
    
              return editParams;
            },
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
            cellRendererParams: {
              skyComponentProperties: {
                validator: (value: Date): boolean =>
                  !!value && value > new Date(1985, 9, 26),
                validatorMessage: 'Enter a future date.',
              },
            },
            editable: true,
          },
        ];
    
        this.gridData = this.#context.gridData;
    
        const gridOptions: GridOptions = {
          columnDefs: this.#columnDefs,
          onGridReady: (gridReadyEvent): void => {
            this.onGridReady(gridReadyEvent);
          },
        };
    
        this.gridOptions = this.#agGridService.getEditableGridOptions({
          gridOptions,
        });
    
        this.#changeDetector.markForCheck();
      }
    
      public onGridReady(gridReadyEvent: GridReadyEvent): void {
        this.#gridApi = gridReadyEvent.api;
        this.#changeDetector.markForCheck();
      }
    
      #departmentSelectionChange(
        change: SkyAutocompleteSelectionChange,
        node: IRowNode<AgGridDemoRow>,
      ): void {
        if (change.selectedItem && change.selectedItem !== node.data?.department) {
          this.#clearJobTitle(node);
        }
      }
    
      #clearJobTitle(node: IRowNode<AgGridDemoRow> | null): void {
        if (node?.data) {
          node.data.jobTitle = undefined;
    
          if (this.#gridApi) {
            this.#gridApi.refreshCells({
              rowNodes: [node],
            });
          }
        }
    
        this.#changeDetector.markForCheck();
      }
    }
Copy

    <sky-data-manager>
      <sky-data-manager-toolbar>
        <sky-data-manager-toolbar-left-item>
          <button
            class="sky-btn sky-btn-primary"
            type="button"
            (click)="openModal()"
          >
            Edit
          </button>
        </sky-data-manager-toolbar-left-item>
      </sky-data-manager-toolbar>
      <app-view-grid [items]="items" />
    </sky-data-manager>
Copy

    <sky-modal headingText="Filter employees">
      <sky-modal-content>
        <label [for]="jobTitleInput.id">Job Title</label>
        <select
          #jobTitleInput
          class="sky-form-control"
          skyId="jobTitleInput"
          [(ngModel)]="jobTitle"
        >
          <option value="any">Any job title</option>
          <option value="Product Manager">Product Manager</option>
          <option value="Software Engineer">Software Engineer</option>
        </select>
        <div class="sky-margin-stacked-lg">
          <sky-checkbox labelText="Hide Sales employees" [(ngModel)]="hideSales" />
        </div>
      </sky-modal-content>
      <sky-modal-footer>
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="applyFilters()"
        >
          Apply filters
        </button>
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="clearAllFilters()"
        >
          Clear all filters
        </button>
        <button class="sky-btn sky-btn-link" type="button" (click)="cancel()">
          Cancel
        </button>
      </sky-modal-footer>
    </sky-modal>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      inject,
    } from '@angular/core';
    import { FormsModule } from '@angular/forms';
    import { SkyIdModule } from '@skyux/core';
    import {
      SkyDataManagerFilterData,
      SkyDataManagerFilterModalContext,
    } from '@skyux/data-manager';
    import { SkyCheckboxModule } from '@skyux/forms';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { Filters } from './filters';
    
    @Component({
      selector: 'app-filter-modal',
      templateUrl: './filter-modal.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [FormsModule, SkyCheckboxModule, SkyIdModule, SkyModalModule],
    })
    export class FilterModalComponent {
      protected hideSales = false;
      protected jobTitle = '';
    
      readonly #changeDetector = inject(ChangeDetectorRef);
      readonly #context = inject(SkyDataManagerFilterModalContext);
      readonly #instance = inject(SkyModalInstance);
    
      constructor() {
        if (this.#context.filterData?.filters) {
          const filters = this.#context.filterData.filters as Filters;
    
          this.jobTitle = filters.jobTitle ?? 'any';
          this.hideSales = filters.hideSales ?? false;
        }
    
        this.#changeDetector.markForCheck();
      }
    
      protected applyFilters(): void {
        const result: SkyDataManagerFilterData = {};
    
        result.filtersApplied = this.jobTitle !== 'any' || this.hideSales;
        result.filters = {
          jobTitle: this.jobTitle,
          hideSales: this.hideSales,
        } satisfies Filters;
    
        this.#changeDetector.markForCheck();
        this.#instance.save(result);
      }
    
      protected clearAllFilters(): void {
        this.hideSales = false;
        this.jobTitle = 'any';
        this.#changeDetector.markForCheck();
      }
    
      protected cancel(): void {
        this.#instance.cancel();
      }
    }
Copy

    export interface Filters {
      jobTitle?: string;
      hideSales?: boolean;
    }
Copy

    <sky-data-view skyAgGridDataManagerAdapter [viewId]="viewConfig.id">
      @if (isActive && isGridInitialized) {
        <sky-ag-grid-wrapper>
          <ag-grid-angular
            [gridOptions]="gridOptions"
            [overlayNoRowsTemplate]="noRowsTemplate"
            [rowData]="displayedItems"
            (rowSelected)="onRowSelected($event)"
          />
        </sky-ag-grid-wrapper>
      }
    </sky-data-view>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      Input,
      OnDestroy,
      OnInit,
      inject,
    } from '@angular/core';
    import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
    import {
      SkyDataManagerService,
      SkyDataManagerState,
      SkyDataViewConfig,
    } from '@skyux/data-manager';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridApi,
      GridOptions,
      GridReadyEvent,
      ModuleRegistry,
      RowSelectedEvent,
      ValueFormatterParams,
    } from 'ag-grid-community';
    import { Subject, of, takeUntil } from 'rxjs';
    
    import { ContextMenuComponent } from './context-menu.component';
    import { AgGridDemoRow } from './data';
    import { Filters } from './filters';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-view-grid',
      templateUrl: './view-grid.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [AgGridModule, SkyAgGridModule],
    })
    export class ViewGridComponent implements OnInit, OnDestroy {
      @Input()
      public set items(value: AgGridDemoRow[]) {
        this.#_items = value;
        this.#changeDetectorRef.markForCheck();
        this.#gridApi?.refreshCells();
      }
    
      public get items(): AgGridDemoRow[] {
        return this.#_items;
      }
    
      #viewId = 'dataEntryGridWithDataManagerView';
    
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
        {
          field: 'validationCurrency',
          headerName: 'Validation currency',
          type: [SkyCellType.CurrencyValidator],
        },
        {
          field: 'validationDate',
          headerName: 'Validation date',
          type: [SkyCellType.Date, SkyCellType.Validator],
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: Date): boolean =>
                !!value && value > new Date(1985, 9, 26),
              validatorMessage: 'Please enter a future date',
            },
          },
        },
      ];
    
      protected displayedItems: AgGridDemoRow[] = [];
      protected gridOptions: GridOptions;
      protected isActive = false;
      protected isGridInitialized = false;
      protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
      protected viewConfig: SkyDataViewConfig = {
        id: this.#viewId,
        name: 'Data Grid View',
        iconName: 'table',
        searchEnabled: true,
        multiselectToolbarEnabled: true,
        columnPickerEnabled: true,
        filterButtonEnabled: true,
        columnOptions: [
          {
            id: 'selected',
            label: '',
            alwaysDisplayed: true,
          },
          {
            id: 'context',
            label: '',
            alwaysDisplayed: true,
          },
          {
            id: 'name',
            label: 'Name',
            description: 'The name of the employee.',
          },
          {
            id: 'age',
            label: 'Age',
            description: 'The age of the employee.',
          },
          {
            id: 'startDate',
            label: 'Start date',
            description: 'The start date of the employee.',
          },
          {
            id: 'endDate',
            label: 'End date',
            description: 'The end date of the employee.',
          },
          {
            id: 'department',
            label: 'Department',
            description: 'The department of the employee',
          },
          {
            id: 'jobTitle',
            label: 'Title',
            description: 'The job title of the employee.',
          },
          {
            id: 'validationCurrency',
            label: 'Validation currency',
            description: 'An example column for currency validation.',
          },
          {
            id: 'validationDate',
            label: 'Validation date',
            description: 'An example column for date validation.',
          },
        ],
      };
    
      #_items: AgGridDemoRow[] = [];
    
      #dataState = new SkyDataManagerState({});
      #gridApi: GridApi | undefined;
      #ngUnsubscribe = new Subject<void>();
    
      readonly #agGridSvc = inject(SkyAgGridService);
      readonly #changeDetectorRef = inject(ChangeDetectorRef);
      readonly #dataManagerSvc = inject(SkyDataManagerService);
    
      constructor() {
        this.gridOptions = this.#agGridSvc.getEditableGridOptions({
          gridOptions: {
            columnDefs: this.#columnDefs,
            onGridReady: this.onGridReady.bind(this),
          },
        });
      }
    
      public ngOnInit(): void {
        this.displayedItems = this.items;
    
        this.#dataManagerSvc.initDataView(this.viewConfig);
    
        this.#dataManagerSvc
          .getDataStateUpdates(this.#viewId)
          .pipe(takeUntil(this.#ngUnsubscribe))
          .subscribe((state) => {
            this.#dataState = state;
            this.#setInitialColumnOrder();
            this.#updateData();
            this.#changeDetectorRef.detectChanges();
          });
    
        this.#dataManagerSvc
          .getActiveViewIdUpdates()
          .pipe(takeUntil(this.#ngUnsubscribe))
          .subscribe((id) => {
            this.isActive = id === this.#viewId;
            this.#changeDetectorRef.detectChanges();
          });
      }
    
      public ngOnDestroy(): void {
        this.#ngUnsubscribe.next();
        this.#ngUnsubscribe.complete();
      }
    
      protected onGridReady(gridReadyEvent: GridReadyEvent): void {
        this.#gridApi = gridReadyEvent.api;
        this.#updateData();
        this.#changeDetectorRef.markForCheck();
      }
    
      protected onRowSelected(
        rowSelectedEvent: RowSelectedEvent<AgGridDemoRow>,
      ): void {
        if (!rowSelectedEvent.data?.selected) {
          this.#updateData();
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
    
      #filterItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
        let filteredItems = items;
        const filterData = this.#dataState.filterData;
    
        if (filterData?.filters) {
          const filters = filterData.filters as Filters;
    
          filteredItems = items.filter((item) => {
            return (
              (!!(filters.hideSales && item.department.name !== 'Sales') ||
                !filters.hideSales) &&
              ((filters.jobTitle !== 'any' &&
                item.jobTitle?.name === filters.jobTitle) ||
                !filters.jobTitle ||
                filters.jobTitle === 'any')
            );
          });
        }
    
        return filteredItems;
      }
    
      #searchItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
        let searchedItems = items;
        const searchText = this.#dataState.searchText;
    
        if (searchText) {
          searchedItems = items.filter((item) => {
            let property: keyof typeof item;
            for (property in item) {
              if (
                Object.prototype.hasOwnProperty.call(item, property) &&
                property === 'name'
              ) {
                const propertyText = item[property]?.toLowerCase();
                if (propertyText.includes(searchText)) {
                  return true;
                }
              }
            }
    
            return false;
          });
        }
    
        return searchedItems;
      }
    
      #setInitialColumnOrder(): void {
        const viewState = this.#dataState.getViewStateById(this.#viewId);
        const visibleColumns = viewState?.displayedColumnIds ?? [];
    
        this.#columnDefs.sort((col1, col2) => {
          const col1Index = visibleColumns.findIndex(
            (colId: string) => colId === col1.colId,
          );
          const col2Index = visibleColumns.findIndex(
            (colId: string) => colId === col2.colId,
          );
    
          if (col1Index === -1) {
            col1.hide = true;
            return 0;
          } else if (col2Index === -1) {
            col2.hide = true;
            return 0;
          } else {
            return col1Index - col2Index;
          }
        });
    
        this.isGridInitialized = true;
        this.#changeDetectorRef.markForCheck();
      }
    
      #updateData(): void {
        this.displayedItems = this.#filterItems(this.#searchItems(this.items));
    
        if (this.#dataState.onlyShowSelected) {
          this.displayedItems = this.displayedItems.filter((item) => item.selected);
        }
    
        if (this.displayedItems.length > 0) {
          this.#gridApi?.hideOverlay();
        } else {
          this.#gridApi?.showNoRowsOverlay();
        }
    
        this.#changeDetectorRef.markForCheck();
      }
    }

Copy

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
### Setting initial focus for keyboard navigation

Edit in StackBlitz

Start hereShow help content for

No Rows To Show

NameSort column Name, not currently sorted

AgeSort column Age, not currently sorted

Start dateSort column Start date, currently ascending

End dateSort column End date, not currently sorted

DepartmentSort column Department, not currently sorted

TitleSort column Title, not currently sorted

Billy Bob

55

12/1/1994

N/A

Customer Support

Account Manager

Jane Deere

33

7/15/2009

N/A

Engineering

Principal Software Engineer

David Smith

51

1/1/2012

06/15/2018

Engineering

Product Manager

Emily Johnson

41

1/15/2014

N/A

Marketing

Events Manager

John Doe

38

9/1/2017

09/30/2017

Sales

Nicole Davidson

22

11/1/2019

N/A

Engineering

Software Engineer

Carl Roberts

23

11/1/2019

N/A

Engineering

UX Designer

to of

Page of

Or start hereShow help content for

Show code

Copy

    export interface AutocompleteOption {
      id: string;
      name: string;
    }
    
    export const DEPARTMENTS = [
      {
        id: '1',
        name: 'Marketing',
      },
      {
        id: '2',
        name: 'Sales',
      },
      {
        id: '3',
        name: 'Engineering',
      },
      {
        id: '4',
        name: 'Customer Support',
      },
    ];
    
    export const JOB_TITLES: Record<string, AutocompleteOption[]> = {
      Marketing: [
        {
          id: '1',
          name: 'Social Media Coordinator',
        },
        {
          id: '2',
          name: 'Blog Manager',
        },
        {
          id: '3',
          name: 'Events Manager',
        },
      ],
      Sales: [
        {
          id: '4',
          name: 'Business Development Representative',
        },
        {
          id: '5',
          name: 'Account Executive',
        },
      ],
      Engineering: [
        {
          id: '6',
          name: 'Software Engineer',
        },
        {
          id: '7',
          name: 'Senior Software Engineer',
        },
        {
          id: '8',
          name: 'Principal Software Engineer',
        },
        {
          id: '9',
          name: 'UX Designer',
        },
        {
          id: '10',
          name: 'Product Manager',
        },
      ],
      'Customer Support': [
        {
          id: '11',
          name: 'Customer Support Representative',
        },
        {
          id: '12',
          name: 'Account Manager',
        },
        {
          id: '13',
          name: 'Customer Support Specialist',
        },
      ],
    };
    
    export interface AgGridDemoRow {
      selected?: boolean;
      name: string;
      age: number;
      startDate: Date;
      endDate?: Date;
      department: AutocompleteOption;
      jobTitle?: AutocompleteOption;
    }
    
    export const AG_GRID_DEMO_DATA: AgGridDemoRow[] = [
      {
        selected: true,
        name: 'Billy Bob',
        age: 55,
        startDate: new Date('12/1/1994'),
        department: DEPARTMENTS[3],
        jobTitle: JOB_TITLES['Customer Support'][1],
      },
      {
        selected: false,
        name: 'Jane Deere',
        age: 33,
        startDate: new Date('7/15/2009'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][2],
      },
      {
        selected: false,
        name: 'John Doe',
        age: 38,
        startDate: new Date('9/1/2017'),
        endDate: new Date('9/30/2017'),
        department: DEPARTMENTS[1],
      },
      {
        selected: false,
        name: 'David Smith',
        age: 51,
        startDate: new Date('1/1/2012'),
        endDate: new Date('6/15/2018'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][4],
      },
      {
        selected: true,
        name: 'Emily Johnson',
        age: 41,
        startDate: new Date('1/15/2014'),
        department: DEPARTMENTS[0],
        jobTitle: JOB_TITLES['Marketing'][2],
      },
      {
        selected: false,
        name: 'Nicole Davidson',
        age: 22,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][0],
      },
      {
        selected: false,
        name: 'Carl Roberts',
        age: 23,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][3],
      },
    ];
Copy

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

Copy

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
### Basic setup with inline help (without data manager)

Edit in StackBlitz

Edit

NameSort column Name, not currently sortedShow help content for

AgeSort column Age, not currently sortedShow help content for

Start dateSort column Start date, currently ascendingShow help content for

End dateSort column End date, not currently sortedShow help content for

DepartmentSort column Department, not currently sortedShow help content for

TitleSort column Title, not currently sortedShow help content for

Billy Bob

55

12/1/1994

N/A

Customer Support

Account Manager

Jane Deere

33

7/15/2009

N/A

Engineering

Principal Software Engineer

David Smith

51

1/1/2012

06/15/2018

Engineering

Product Manager

Emily Johnson

41

1/15/2014

N/A

Marketing

Events Manager

John Doe

38

9/1/2017

09/30/2017

Sales

Nicole Davidson

22

11/1/2019

N/A

Engineering

Software Engineer

Carl Roberts

23

11/1/2019

N/A

Engineering

UX Designer

to of

Page of

Show code

Copy

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
Copy

    import { ChangeDetectionStrategy, Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { AgGridDemoRow } from './data';
    
    @Component({
      selector: 'app-context-menu',
      templateUrl: './context-menu.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [SkyDropdownModule],
    })
    export class ContextMenuComponent implements ICellRendererAngularComp {
      public contextMenuAriaLabel = '';
      public deleteAriaLabel = '';
      public markInactiveAriaLabel = '';
      public moreInfoAriaLabel = '';
    
      #name: string | undefined;
    
      public agInit(params: ICellRendererParams<AgGridDemoRow>): void {
        this.#name = params.data?.name;
        this.contextMenuAriaLabel = `Context menu for ${this.#name}`;
        this.deleteAriaLabel = `Delete ${this.#name}`;
        this.markInactiveAriaLabel = `Mark ${this.#name} inactive`;
        this.moreInfoAriaLabel = `More info for ${this.#name}`;
      }
    
      public refresh(): boolean {
        return false;
      }
    
      protected actionClicked(action: string): void {
        alert(`${action} clicked for ${this.#name}`);
      }
    }
Copy

    export interface AutocompleteOption {
      id: string;
      name: string;
    }
    
    export const DEPARTMENTS = [
      {
        id: '1',
        name: 'Marketing',
      },
      {
        id: '2',
        name: 'Sales',
      },
      {
        id: '3',
        name: 'Engineering',
      },
      {
        id: '4',
        name: 'Customer Support',
      },
    ];
    
    export const JOB_TITLES: Record<string, AutocompleteOption[]> = {
      Marketing: [
        {
          id: '1',
          name: 'Social Media Coordinator',
        },
        {
          id: '2',
          name: 'Blog Manager',
        },
        {
          id: '3',
          name: 'Events Manager',
        },
      ],
      Sales: [
        {
          id: '4',
          name: 'Business Development Representative',
        },
        {
          id: '5',
          name: 'Account Executive',
        },
      ],
      Engineering: [
        {
          id: '6',
          name: 'Software Engineer',
        },
        {
          id: '7',
          name: 'Senior Software Engineer',
        },
        {
          id: '8',
          name: 'Principal Software Engineer',
        },
        {
          id: '9',
          name: 'UX Designer',
        },
        {
          id: '10',
          name: 'Product Manager',
        },
      ],
      'Customer Support': [
        {
          id: '11',
          name: 'Customer Support Representative',
        },
        {
          id: '12',
          name: 'Account Manager',
        },
        {
          id: '13',
          name: 'Customer Support Specialist',
        },
      ],
    };
    
    export interface AgGridDemoRow {
      selected?: boolean;
      name: string;
      age: number;
      startDate: Date;
      endDate?: Date;
      department: AutocompleteOption;
      jobTitle?: AutocompleteOption;
    }
    
    export const AG_GRID_DEMO_DATA: AgGridDemoRow[] = [
      {
        selected: true,
        name: 'Billy Bob',
        age: 55,
        startDate: new Date('12/1/1994'),
        department: DEPARTMENTS[3],
        jobTitle: JOB_TITLES['Customer Support'][1],
      },
      {
        selected: false,
        name: 'Jane Deere',
        age: 33,
        startDate: new Date('7/15/2009'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][2],
      },
      {
        selected: false,
        name: 'John Doe',
        age: 38,
        startDate: new Date('9/1/2017'),
        endDate: new Date('9/30/2017'),
        department: DEPARTMENTS[1],
      },
      {
        selected: false,
        name: 'David Smith',
        age: 51,
        startDate: new Date('1/1/2012'),
        endDate: new Date('6/15/2018'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][4],
      },
      {
        selected: true,
        name: 'Emily Johnson',
        age: 41,
        startDate: new Date('1/15/2014'),
        department: DEPARTMENTS[0],
        jobTitle: JOB_TITLES['Marketing'][2],
      },
      {
        selected: false,
        name: 'Nicole Davidson',
        age: 22,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][0],
      },
      {
        selected: false,
        name: 'Carl Roberts',
        age: 23,
        startDate: new Date('11/1/2019'),
        department: DEPARTMENTS[2],
        jobTitle: JOB_TITLES['Engineering'][3],
      },
    ];
Copy

    import { AgGridDemoRow } from './data';
    
    export class EditModalContext {
      public gridData: AgGridDemoRow[] = [];
    }
Copy

    <sky-modal headingText="Edit employee information">
      <sky-modal-content>
        <sky-ag-grid-wrapper>
          <ag-grid-angular
            class="sky-ag-grid-editable"
            [gridOptions]="gridOptions"
            [rowData]="gridData"
          />
        </sky-ag-grid-wrapper>
      </sky-modal-content>
      <sky-modal-footer>
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="instance.save(gridData)"
        >
          Save
        </button>
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="instance.cancel()"
        >
          Cancel
        </button>
      </sky-modal-footer>
    </sky-modal>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      inject,
    } from '@angular/core';
    import {
      SkyAgGridAutocompleteProperties,
      SkyAgGridDatepickerProperties,
      SkyAgGridModule,
      SkyAgGridService,
      SkyCellType,
    } from '@skyux/ag-grid';
    import { SkyAutocompleteSelectionChange } from '@skyux/lookup';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridApi,
      GridOptions,
      GridReadyEvent,
      ICellEditorParams,
      IRowNode,
      ModuleRegistry,
    } from 'ag-grid-community';
    
    import { AgGridDemoRow, DEPARTMENTS, JOB_TITLES } from './data';
    import { EditModalContext } from './edit-modal-context';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-edit-modal',
      templateUrl: './edit-modal.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [AgGridModule, SkyAgGridModule, SkyModalModule],
    })
    export class EditModalComponent {
      protected gridData: AgGridDemoRow[];
      protected gridOptions: GridOptions;
    
      #columnDefs: ColDef[];
      #gridApi: GridApi | undefined;
    
      protected readonly instance = inject(SkyModalInstance);
      readonly #agGridSvc = inject(SkyAgGridService);
      readonly #changeDetectorRef = inject(ChangeDetectorRef);
      readonly #context = inject(EditModalContext);
    
      constructor() {
        this.#columnDefs = [
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
            cellEditorParams: {
              skyComponentProperties: {
                maxlength: 10,
              },
            },
            editable: true,
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
            cellEditorParams: {
              skyComponentProperties: {
                min: 18,
              },
            },
            editable: true,
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
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridDatepickerProperties } => {
              return { skyComponentProperties: { minDate: params.data.startDate } };
            },
          },
          {
            field: 'department',
            headerName: 'Department',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              return {
                skyComponentProperties: {
                  data: DEPARTMENTS,
                  selectionChange: (change): void => {
                    this.#departmentSelectionChange(change, params.node);
                  },
                },
              };
            },
            onCellValueChanged: (event): void => {
              if (event.newValue !== event.oldValue) {
                this.#clearJobTitle(event.node);
              }
            },
          },
          {
            field: 'jobTitle',
            headerName: 'Title',
            type: SkyCellType.Autocomplete,
            editable: true,
            cellEditorParams: (
              params: ICellEditorParams<AgGridDemoRow>,
            ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
              const selectedDepartment = params.data?.department?.name;
              const editParams: {
                skyComponentProperties: SkyAgGridAutocompleteProperties;
              } = { skyComponentProperties: { data: [] } };
    
              if (selectedDepartment) {
                editParams.skyComponentProperties.data =
                  JOB_TITLES[selectedDepartment];
              }
    
              return editParams;
            },
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
            cellRendererParams: {
              skyComponentProperties: {
                validator: (value: Date): boolean =>
                  !!value && value > new Date(1985, 9, 26),
                validatorMessage: 'Please enter a future date',
              },
            },
            editable: true,
          },
        ];
    
        this.gridData = this.#context.gridData;
    
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
    
      #departmentSelectionChange(
        change: SkyAutocompleteSelectionChange,
        node: IRowNode<AgGridDemoRow>,
      ): void {
        if (change.selectedItem && change.selectedItem !== node.data?.department) {
          this.#clearJobTitle(node);
        }
      }
    
      #clearJobTitle(node: IRowNode<AgGridDemoRow> | null): void {
        if (node?.data) {
          node.data.jobTitle = undefined;
    
          this.#changeDetectorRef.markForCheck();
          this.#gridApi?.refreshCells({ rowNodes: [node] });
        }
      }
    }
Copy

    <sky-toolbar>
      <sky-toolbar-item>
        <button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
          Edit
        </button>
      </sky-toolbar-item>
      <sky-toolbar-item>
        <sky-search
          [debounceTime]="250"
          [searchText]="searchText"
          (searchApply)="searchApplied($event)"
          (searchChange)="searchApplied($event)"
          (searchClear)="searchApplied($event)"
        />
      </sky-toolbar-item>
    </sky-toolbar>
    
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [overlayNoRowsTemplate]="noRowsTemplate"
        [rowData]="gridData"
      />
    </sky-ag-grid-wrapper>
Copy

    <sky-help-inline
      class="sky-control-help"
      [ariaLabel]="'Information about ' + displayName"
      (actionClick)="onHelpClick()"
    />
Copy

    import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
    import { SkyAgGridHeaderInfo } from '@skyux/ag-grid';
    import { SkyHelpInlineModule } from '@skyux/help-inline';
    
    @Component({
      selector: 'app-inline-help',
      templateUrl: './inline-help.component.html',
      styles: [
        `
          :host {
            display: block;
          }
        `,
      ],
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [SkyHelpInlineModule],
    })
    export class InlineHelpComponent {
      protected displayName: string | undefined;
    
      readonly #headerInfo = inject(SkyAgGridHeaderInfo);
    
      constructor() {
        this.displayName = this.#headerInfo.displayName;
      }
    
      protected onHelpClick(): void {
        alert(`Help was clicked for ${this.displayName}.`);
      }
    }

Copy

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
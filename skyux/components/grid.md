                  

 Grid (deprecated)
=================

Grids provide a SKY UX-themed layout for tabular data.

Grid is deprecated in favor of [data grid](/skyux/components/data-grid.md). For more information, see the [grid deprecation instructions](/skyux/learn/develop/deprecation/grid.md).

 Usage
------

### Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-use-when.f1dd0c57bff4b8c061f0b7843e8f4f6b.png)

Do use grids to display data for users to visually scan and compare values.

### Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use [repeater](/skyux/components/repeater.md) or [box layouts](/skyux/components/box.md) instead. If the content requires multiple templated columns, use [repeaters](/skyux/components/repeater.md) instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use [repeaters](/skyux/components/repeater.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-dont-use-complex.c53a294dcf1c276c9460540b30f9db41.png)

Don't use grids to display data that requires a complex layout.

 Anatomy
--------

1

List count  (optional)

2

Toolbar  (optional)

3

Multiselect toolbar  (optional)

4

Header row

5

Row selection checkbox  (optional)

6

Context-menu dropdown button  (optional)

7

Data

8

Alternate row striping

9

Row divider

10

Selected row background

11

Pagination  (optional)

12

Summary action bar  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-annotated.2078a18d996154869834da1e14f7188b.png)

 Options
--------

### Context-menu dropdown

Use [context-menu dropdowns](/skyux/components/dropdown.md) in the first column when users need to access multiple actions in the rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-context-menu.79ed533cf6be167c24e20b4ac10475e9.png)

### Multiselect

Use multiselect when:

*   Users need to act on more than one row at a time.
*   The list is presented as a full page, a full-page modal, or a full page within a flyout.

Don't use multiselect when:

*   The list is presented in a tile, page section, or other container that might flow off the screen.

To let users select or clear all items and to view only selected items, include the multiselect toolbar. When users select rows, the [summary action bar](/skyux/components/summary-action-bar.md) should fly in from the bottom of the page for actions that users can take on the selected items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-multi.117eadc999971a154211128757e2e064.png)

Use multiselect to let users act on more than one row at a time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-multi-dont-tile.4c0da8a82f665d7a5b4cb2d3f27095f3.png)

Don't use multiselect when the list might flow off the screen.

### Sorting

If users are likely to sort based on the data in columns, enable sorting so that they can select column headers to toggle between ascending and descending order for the specified fields in columns. If users need to sort by data in a templated column, use the [sort component](/skyux/components/sort.md) instead to let them select the data to sort on.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-sort.b404bc1620ad6bc67c99e7a0c2afced1.png)

### Filtering

If users are likely to work with a subset of items in the grid, enable filtering so that they can focus on those items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-filter.73c3d4b39bb01fd6a33c067d849002e4.png)

### Templated items

When columns represent composite information instead of single values, use templated columns to lay out content as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-option-template-column.e41c78498bce25f1474336536ef98ec2.png)

 Behavior and states
--------------------

### Fit

The fit determines how to place the grid within its parent. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

#### Scroll

The `scroll` option allows grids to take as much space as necessary by adding a horizontal scrollbar. This is most useful for grids with large numbers of columns.

#### Width

The `width` option fixes the width of the grid to its container and resizes columns to fit. This is most useful for simple grids in smaller containers, such as tiles, where the content fits neatly in the allotted space.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-fit-scroll.95296ada4c865e31ad5f434be3ca660f.png)

Grids with large numbers of columns can fit to the parent container by using a horizontal scrollbar to take as much space as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-fit-width.61eb37963e74a72cda971d36ef55dff1.png)

Simple grids in smaller containers can resize columns to fit the grid to its container.

### Reordering columns

Users can reorder columns by dragging and dropping.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-reorder.ce9ecc4b00d051b4b7aaafb42a052444.png)

### Resizing columns

Users can resize columns by selecting and dragging or by using the keyboard.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/grids/img/guidelines/grid-resize.3e3c23a204cebe4ed69d2c020f5c1520.png)

### Responsiveness

Grids perform poorly in small viewports. The columns in fixed-width grids shrink down to the point of being unreadable, and scrolling grids require a lot of interaction to view the content. Use [repeaters](/skyux/components/repeater.md) instead if possible.

 Related information
--------------------

### Components

*   [Card](/skyux/components/card.md)
*   [Dropdown](/skyux/components/dropdown.md)
*   [Filter](/skyux/components/filter.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [List view grid](/skyux/components/list-view-grid.md)
*   [Paging](/skyux/components/paging.md)
*   [Repeater](/skyux/components/repeater.md)
*   [Sort](/skyux/components/sort.md)
*   [Summary action bar](/skyux/components/summary-action-bar.md)
*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/grids`[View in NPM](https://www.npmjs.com/package/@skyux/grids) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/grids/src/lib/modules/grid/grid.module.ts#L44) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/grids`Copy None found.

 SkyGridModule
--------------

Type: Module

`import { SkyGridModule } from '@skyux/grids';`

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

 SkyGridComponent
-----------------

Type: Component

Selector: `sky-grid`

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

### Inputs

#### `columns: SkyGridColumnModel[]`

Columns and column properties for the grid.

#### `data: any[]`

The data for the grid. Each item requires an `id` and a property that maps to the `field` or `id` property of each column in the grid.

#### `enableMultiselect: boolean`

Whether to enable the multiselect feature to display a column of checkboxes on the left side of the grid. You can specify a unique ID with the `multiselectRowId` property, but multiselect defaults to the `id` property on the `data` object.

Default: `false`

#### `fit: string`

How the grid fits to its parent. The valid options are `width`, which fits the grid to the parent's full width, and `scroll`, which allows the grid to exceed the parent's width. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

Default: `"width"`

#### `hasToolbar: boolean`

Whether to display a toolbar with the grid.

Default: `false`

#### `height: number`

The height of the grid.

#### `highlightText: string`

Text to highlight within the grid. Typically, this property is used in conjunction with search.

#### `messageStream: Subject<SkyGridMessage>`

The observable to send commands to the grid.

#### `multiselectRowId: string`

The unique ID that matches a property on the `data` object. By default, this property uses the `id` property.

#### `rowHighlightedId: string`

The ID of the row to highlight. The ID matches the `id` property of the `data` object. Typically, this property is used in conjunction with the flyout component to indicate the currently selected row.

#### `selectedColumnIds: string[]`

The columns to display in the grid based on the `id` or `field` properties of the columns. If no columns are specified, then the grid displays all columns.

#### `selectedRowIds: string[]`

The set of IDs for the rows to select in a multiselect grid. The IDs match the `id` properties of the `data` objects. Rows with IDs that are not included are de-selected in the grid.

#### `settingsKey: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users and returns `selectedColumnIds` to preserve the columns to display and the preferred column order. You must provide `id` values for your `sky-grid-column` elements because the UI Config Service depends on those values to organize columns based on user settings. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

#### `sortField: ListSortFieldSelectorModel`

Displays a caret in the column that was used to sort the grid. This is particularly useful when you programmatically sort data and want to visually indicate how the grid was sorted. This property accepts a `ListSortFieldSelectorModel` value with the following properties:

*   `fieldSelector` Represents the current sort field. This property accepts `string` values.
*   `descending` Indicates whether to sort in descending order. The caret that visually indicates the sort order points down for descending order and up for ascending order. This property accepts `boolean` values. Default is `false`.

#### `width: number`

The width of the grid in pixels.

### Outputs

#### `columnWidthChange: EventEmitter<SkyGridColumnWidthModelChange[]>`

Fires when the width of a column changes.

#### `multiselectSelectionChange: EventEmitter<SkyGridSelectedRowsModelChange>`

Fires when the selection of multiselect checkboxes changes. Emits an array of IDs for the selected rows based on the `multiselectRowId` property that the consumer provides.

#### `selectedColumnIdsChange: EventEmitter<string[]>`

Fires when the columns to display in the grid change or when the order of the columns changes. The event emits an array of IDs for the displayed columns that reflects the column order.

#### `sortFieldChange: EventEmitter<ListSortFieldSelectorModel>`

Fires when the active sort field changes.

 SkyGridColumnComponent
-----------------------

Type: Component

Selector: `sky-grid-column`

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

Specifies the column information.

### Inputs

#### `alignment: SkyGridColumnAlignment`

The horizontal alignment of the column's data and header. Options include: `"left"`, `"center"`, and `"right"`.

Default: `"left"`

#### `description: string`

The description for the column.

#### `excludeFromHighlighting: boolean`

Whether to disable the highlighting of search text in the column.

Default: `false`

#### `field: string`

The property to retrieve cell information from an entry on the grid `data` array. You must provide either the `id` or `field` property for every column, but do not provide both. If `id` does not exist on a column, then `field` is the entry for the grid `selectedColumnIds` array.

#### `heading: string`

Text to display in the column header.

#### `hidden: boolean`

Whether the column is initially hidden when grid `selectedColumnIds` are not provided.

Default: `false`

#### `id: string`

The unique ID for the column. You must provide either the `id` or `field` property for every column, but do not provide both. If `field` does not exist on a column, then the `id` property retrieves cell information from an entry on the grid `data` array.

#### `inlineHelpPopover: any`

The template to display inside an inline help popup for this column.

#### `isSortable: boolean`

Whether the column sorts the grid when users click the column header.

Default: `true`

#### `locked: boolean`

Whether the column is locked. The intent is to display locked columns first on the left side of the grid. If set to `true`, then users cannot drag the column to another position and or drag other columns before the locked column.

Default: `false`

#### `search: (value: any, searchText: string) => boolean`

The search function to apply for the specific column. By default, the column executes a string compare on the column data.

Default: `(value, searchText) => value.toString().toLowerCase().indexOf(searchText) !== -1`

#### `template: TemplateRef<unknown>`

The template for a column. This can be assigned as a reference to the `template` attribute, or it can be assigned as a child of the `template` element inside the `sky-grid-column` component. The template has access to the `value` variable, which contains the value passed to the column, and the `row` variable, which contains the entire row data.

#### `width: number`

The width of the column in pixels. If undefined, the column width is evenly distributed.

 SkyGridColumnAlignment
-----------------------

Type: Type alias

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

Represents the horizontal alignment of the column's data and header.

    type SkyGridColumnAlignment = "left" | "center" | "right"

 SkyGridColumnWidthModelChange
------------------------------

Type: Interface

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

    interface SkyGridColumnWidthModelChange {
      field?: string;
      id?: string;
      width: number;
    }

### Properties

#### `field?: string`

The field of the column.

#### `id?: string`

The ID of the column.

#### `width: number`

The width of the column in pixels.

 SkyGridColumnModel
-------------------

Type: Class

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

### Properties

#### `alignment: SkyGridColumnAlignment`

The horizontal alignment of the column's data and header.

#### `description: string`

#### `excludeFromHighlighting: boolean`

#### `field: string`

#### `heading: string`

#### `hidden: boolean`

#### `id: string`

#### `inlineHelpPopover: any`

#### `isSortable: boolean`

Default: `true`

#### `locked: boolean`

#### `searchFunction: (data: any, searchText: string) => boolean`

#### `template: TemplateRef<unknown>`

#### `type: string`

#### `width: number`

 SkyGridSelectedRowsModelChange
-------------------------------

Type: Interface

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

    interface SkyGridSelectedRowsModelChange {
      selectedRowIds?: string[];
    }

### Properties

#### `selectedRowIds?: string[]`

The IDs of the rows that are selected.

 SkyGridMessage
---------------

Type: Interface

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

    interface SkyGridMessage {
      type: SkyGridMessageType;
    }

### Properties

#### `type: SkyGridMessageType`

The type of message being sent.

 SkyGridMessageType
-------------------

Type: Enumeration

Warning: **Deprecated.** `SkyGridComponent` and its features are deprecated. We recommend using the data grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-grid](/skyux/components/data-grid.md)

    enum SkyGridMessageType {
      AbortDeleteRow = 3,
      ClearAll = 1,
      PromptDeleteRow = 2,
      SelectAll = 0,
    }

### Properties

#### `SkyGridMessageType.AbortDeleteRow`

#### `SkyGridMessageType.ClearAll`

Clears the multiselect checkboxes for all rows in the grid.

#### `SkyGridMessageType.PromptDeleteRow`

#### `SkyGridMessageType.SelectAll`

Selects the multiselect checkboxes for all rows in the grid.
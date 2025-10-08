# Design

                      Skip to Main Content

 List view grid (deprecated)
===========================

The list view grid component displays a grid for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

List view grid and its features are deprecated. We will remove it in a future major version. We recommend using [data grid](/skyux/components/data-grid.md) instead.

 Usage
------

### Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-use-when.f1dd0c57bff4b8c061f0b7843e8f4f6b.png)

Do use grids to display data for users to visually scan and compare values.

### Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use [repeaters](/skyux/components/repeater.md) or [card views](/skyux/components/card.md) instead. If the content requires multiple templated columns, use [repeaters](/skyux/components/repeater.md) instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use [repeaters](/skyux/components/repeater.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-dont-use-complex.c53a294dcf1c276c9460540b30f9db41.png)

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

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-annotated.40b6a29be8171a8c9967ce8dcda10b2e.png)

 Options
--------

### Context-menu dropdown

Use [context-menu dropdowns](/skyux/components/dropdown.md) in the first column when users need to access multiple actions in the rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-context-menu.79ed533cf6be167c24e20b4ac10475e9.png)

### Multiselect

Use multiselect when:

*   Users need to act on more than one row at a time.
*   The list is presented as a full page, a full-page modal, or a full page within a flyout.

Don't use multiselect when:

*   The list is presented in a tile, page section, or other container that might flow off the screen.

To let users select or clear all items and to view only selected items, include the multiselect toolbar. When users select rows, the [summary action bar](/skyux/components/summary-action-bar.md) should fly in from the bottom of the page for actions that users can take on the selected items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-multi.117eadc999971a154211128757e2e064.png)

Use multiselect to let users act on more than one row at a time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-multi-dont-tile.4c0da8a82f665d7a5b4cb2d3f27095f3.png)

Don't use multiselect when the list might flow off the screen.

### Sorting

If users are likely to sort based on the data in columns, enable sorting so that they can select column headers to toggle between ascending and descending order for the specified fields in columns. If users need to sort by data in a templated column, use the [sort component](/skyux/components/sort.md) instead to let them select the data to sort on.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-sort.b404bc1620ad6bc67c99e7a0c2afced1.png)

### Filtering

If users are likely to work with a subset of items in the grid, enable filtering so that they can focus on those items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-filter.73c3d4b39bb01fd6a33c067d849002e4.png)

### Templated items

When columns represent composite information instead of single values, use templated columns to lay out content as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-template-column.e41c78498bce25f1474336536ef98ec2.png)

 Behavior and states
--------------------

### Fit

The fit determines how to place the grid within its parent. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

#### Scroll

The scroll option allows grids to take as much space as necessary by adding a horizontal scrollbar. This is most useful for grids with large numbers of columns.

#### Width

The width option fixes the width of the grid to its container and resizes columns to fit. This is most useful for simple grids in smaller containers, such as tiles, where the content fits neatly in the allotted space.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-fit-scroll.95296ada4c865e31ad5f434be3ca660f.png)

Grids with large numbers of columns can fit to the parent container by using a horizontal scrollbar to take as much space as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-fit-width.61eb37963e74a72cda971d36ef55dff1.png)

Simple grids in smaller containers can resize columns to fit the grid to its container.

### Reordering columns

Users can reorder columns by dragging and dropping.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-reorder.ce9ecc4b00d051b4b7aaafb42a052444.png)

### Resizing columns

Users can resize columns by selecting and dragging or by using the keyboard.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-resize.3e3c23a204cebe4ed69d2c020f5c1520.png)

### Responsiveness

Grids perform poorly in small viewports. The columns in fixed-width grids shrink down to the point of being unreadable, and scrolling grids require a lot of interaction to view the content. Use [repeaters](/skyux/components/repeater.md) instead if possible.

 Related information
--------------------

### Components

*   [Card](/skyux/components/card.md)
*   [Flyout](/skyux/components/flyout.md)
*   [Grid](/skyux/components/grid.md)
*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)

### Guidelines

*   [Page layout](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/list-builder-view-grids`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder-view-grids) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder-view-grids/src/lib/modules/list-view-grid/list-view-grid.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder-view-grids`Copy None found.

 SkyListViewGridModule
----------------------

Type: Module

`import { SkyListViewGridModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyListViewGridComponent
-------------------------

Type: Component

Selector: `sky-list-view-grid`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

Displays a grid for a [SKY UX-themed list of data](/skyux/components/list/overview.md) using the [grid component](/skyux/components/grid.md). You must install `SkyListModule` as a dependency.

### Inputs

#### `name: string`

Required

The name of the view.

#### `displayedColumns: string[] | Observable<string[]>`

The columns to display by default based on the ID or field of the item.

#### `enableMultiselect: boolean`

Whether to enable the multiselect feature to display a column of checkboxes on the left side of the grid. Multiselect also displays an action bar with buttons to select and clear all checkboxes. Multiselect defaults to the `id` property on the list's `data` object.

Default: `false`

#### `fit: string`

How the grid fits to its parent. `"width"` fits the grid to the parent's full width, and `"scroll"` allows the grid to exceed the parent's width. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

Default: `"width"`

#### `height: number | Observable<number>`

The height of the grid.

#### `hiddenColumns: string[] | Observable<string[]>`

The columns to hide by default based on the ID or field of the item.

#### `highlightSearchText: boolean`

Whether to highlight search text within the grid.

Default: `true`

#### `messageStream: Subject<SkyListViewGridMessage>`

The observable to send commands to the grid. The commands should respect the `SkyListViewGridMessage` type.

#### `rowHighlightedId: string`

The ID of the row to highlight. The ID matches the `id` property of the `data` object. Typically, this property is used in conjunction with the [flyout component](/skyux/components/flyout.md) to indicate the currently selected row.

#### `search: (data: any, searchText: string) => boolean`

The search function to apply on the view data.

#### `settingsKey: string`

The unique key for the UI Config Service that retrieves stored settings from a database. The service saves configuration settings for users and returns `selectedColumnIds` for the columns to display and the preferred column order. For more information, see the [sticky settings documentation](/skyux/learn/get-started/advanced/sticky-settings.md).

#### `width: number | Observable<number>`

The width of the grid.

### Outputs

#### `rowDeleteCancel: EventEmitter<SkyListViewGridRowDeleteCancelArgs>`

Fires when users cancel the deletion of a row.

#### `rowDeleteConfirm: EventEmitter<SkyListViewGridRowDeleteConfirmArgs>`

Fires when users confirm the deletion of a row.

#### `selectedColumnIdsChange: EventEmitter<string[]>`

Fires when columns change. This includes changes to the displayed columns and changes to the order of columns. The event emits an array of IDs for the displayed columns that reflects the column order.

 SkyListViewGridMessageType
---------------------------

Type: Enumeration

The command for the list view grid to respond to.

    enum SkyListViewGridMessageType {
      AbortDeleteRow = 1,
      PromptDeleteRow = 0,
    }

### Properties

#### `SkyListViewGridMessageType.AbortDeleteRow`

Cancels the deletion of a row in the list view grid.

#### `SkyListViewGridMessageType.PromptDeleteRow`

Deletes of a row in the list view grid.

 SkyListViewGridMessage
-----------------------

Type: Interface

Communicates commands to the list view grid.

    interface SkyListViewGridMessage {
      data?: { abortDeleteRow?: { id: string }; promptDeleteRow?: { id: string } };
      type: SkyListViewGridMessageType;
    }

### Properties

#### `data?: { abortDeleteRow?: { id: string }; promptDeleteRow?: { id: string } }`

The data required to carry out the command.

#### `type: SkyListViewGridMessageType`

The type of message to send.

 SkyListViewGridRowDeleteCancelArgs
-----------------------------------

Type: Interface

    interface SkyListViewGridRowDeleteCancelArgs {
      id: string;
    }

### Properties

#### `id: string`

The ID of the row where the Cancel button was clicked to cancel deleting the row.

 SkyListViewGridRowDeleteConfirmArgs
------------------------------------

Type: Interface

    interface SkyListViewGridRowDeleteConfirmArgs {
      id: string;
    }

### Properties

#### `id: string`

The ID of the row where the Confirm button was clicked to delete the row.

 SkyListColumnSelectorActionModule
----------------------------------

Type: Module

`import { SkyListColumnSelectorActionModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyListColumnSelectorActionComponent
-------------------------------------

Type: Component

Selector: `sky-list-column-selector-action`

Provides a column selector modal for a list grid view when placed in a [list toolbar](/skyux/components/list/toolbar.md).

### Inputs

#### `gridView: SkyListViewGridComponent`

Enables the column selector in the list toolbar. Set this attribute to the instance of the `sky-grid-view` component using the component's template reference variable.

#### `helpKey: string`

The `helpKey` string to associate with a help button in the grid header. When users select the button, the `helpOpened` event broadcasts the `helpKey` parameter.

### Outputs

#### `helpOpened: EventEmitter<string>`

Fires when users click the help button and broadcasts the `helpKey`.

 SkyColumnSelectorModule
------------------------

Type: Module

`import { SkyColumnSelectorModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyColumnSelectorContext
-------------------------

Type: Class

### Properties

#### `columns: SkyColumnSelectorModel[]`

#### `selectedColumnIds: string[]`

 SkyColumnSelectorModel
-----------------------

Type: Class

### Properties

#### `description: string`

#### `heading: string`

#### `id: string`

# Development

                      Skip to Main Content

 List view grid (deprecated)
===========================

The list view grid component displays a grid for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

List view grid and its features are deprecated. We will remove it in a future major version. We recommend using [data grid](/skyux/components/data-grid.md) instead.

 Usage
------

### Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-use-when.f1dd0c57bff4b8c061f0b7843e8f4f6b.png)

Do use grids to display data for users to visually scan and compare values.

### Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use [repeaters](/skyux/components/repeater.md) or [card views](/skyux/components/card.md) instead. If the content requires multiple templated columns, use [repeaters](/skyux/components/repeater.md) instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use [repeaters](/skyux/components/repeater.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-dont-use-complex.c53a294dcf1c276c9460540b30f9db41.png)

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

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-annotated.40b6a29be8171a8c9967ce8dcda10b2e.png)

 Options
--------

### Context-menu dropdown

Use [context-menu dropdowns](/skyux/components/dropdown.md) in the first column when users need to access multiple actions in the rows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-context-menu.79ed533cf6be167c24e20b4ac10475e9.png)

### Multiselect

Use multiselect when:

*   Users need to act on more than one row at a time.
*   The list is presented as a full page, a full-page modal, or a full page within a flyout.

Don't use multiselect when:

*   The list is presented in a tile, page section, or other container that might flow off the screen.

To let users select or clear all items and to view only selected items, include the multiselect toolbar. When users select rows, the [summary action bar](/skyux/components/summary-action-bar.md) should fly in from the bottom of the page for actions that users can take on the selected items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-multi.117eadc999971a154211128757e2e064.png)

Use multiselect to let users act on more than one row at a time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-multi-dont-tile.4c0da8a82f665d7a5b4cb2d3f27095f3.png)

Don't use multiselect when the list might flow off the screen.

### Sorting

If users are likely to sort based on the data in columns, enable sorting so that they can select column headers to toggle between ascending and descending order for the specified fields in columns. If users need to sort by data in a templated column, use the [sort component](/skyux/components/sort.md) instead to let them select the data to sort on.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-sort.b404bc1620ad6bc67c99e7a0c2afced1.png)

### Filtering

If users are likely to work with a subset of items in the grid, enable filtering so that they can focus on those items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-filter.73c3d4b39bb01fd6a33c067d849002e4.png)

### Templated items

When columns represent composite information instead of single values, use templated columns to lay out content as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-option-template-column.e41c78498bce25f1474336536ef98ec2.png)

 Behavior and states
--------------------

### Fit

The fit determines how to place the grid within its parent. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

#### Scroll

The scroll option allows grids to take as much space as necessary by adding a horizontal scrollbar. This is most useful for grids with large numbers of columns.

#### Width

The width option fixes the width of the grid to its container and resizes columns to fit. This is most useful for simple grids in smaller containers, such as tiles, where the content fits neatly in the allotted space.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-fit-scroll.95296ada4c865e31ad5f434be3ca660f.png)

Grids with large numbers of columns can fit to the parent container by using a horizontal scrollbar to take as much space as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-fit-width.61eb37963e74a72cda971d36ef55dff1.png)

Simple grids in smaller containers can resize columns to fit the grid to its container.

### Reordering columns

Users can reorder columns by dragging and dropping.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-reorder.ce9ecc4b00d051b4b7aaafb42a052444.png)

### Resizing columns

Users can resize columns by selecting and dragging or by using the keyboard.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder-view-grids/img/guidelines/list-view-grids/grid-resize.3e3c23a204cebe4ed69d2c020f5c1520.png)

### Responsiveness

Grids perform poorly in small viewports. The columns in fixed-width grids shrink down to the point of being unreadable, and scrolling grids require a lot of interaction to view the content. Use [repeaters](/skyux/components/repeater.md) instead if possible.

 Related information
--------------------

### Components

*   [Card](/skyux/components/card.md)
*   [Flyout](/skyux/components/flyout.md)
*   [Grid](/skyux/components/grid.md)
*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)

### Guidelines

*   [Page layout](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/list-builder-view-grids`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder-view-grids) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder-view-grids/src/lib/modules/list-view-grid/list-view-grid.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder-view-grids`Copy None found.

 SkyListViewGridModule
----------------------

Type: Module

`import { SkyListViewGridModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyListViewGridComponent
-------------------------

Type: Component

Selector: `sky-list-view-grid`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

Displays a grid for a [SKY UX-themed list of data](/skyux/components/list/overview.md) using the [grid component](/skyux/components/grid.md). You must install `SkyListModule` as a dependency.

### Inputs

#### `name: string`

Required

The name of the view.

#### `displayedColumns: string[] | Observable<string[]>`

The columns to display by default based on the ID or field of the item.

#### `enableMultiselect: boolean`

Whether to enable the multiselect feature to display a column of checkboxes on the left side of the grid. Multiselect also displays an action bar with buttons to select and clear all checkboxes. Multiselect defaults to the `id` property on the list's `data` object.

Default: `false`

#### `fit: string`

How the grid fits to its parent. `"width"` fits the grid to the parent's full width, and `"scroll"` allows the grid to exceed the parent's width. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

Default: `"width"`

#### `height: number | Observable<number>`

The height of the grid.

#### `hiddenColumns: string[] | Observable<string[]>`

The columns to hide by default based on the ID or field of the item.

#### `highlightSearchText: boolean`

Whether to highlight search text within the grid.

Default: `true`

#### `messageStream: Subject<SkyListViewGridMessage>`

The observable to send commands to the grid. The commands should respect the `SkyListViewGridMessage` type.

#### `rowHighlightedId: string`

The ID of the row to highlight. The ID matches the `id` property of the `data` object. Typically, this property is used in conjunction with the [flyout component](/skyux/components/flyout.md) to indicate the currently selected row.

#### `search: (data: any, searchText: string) => boolean`

The search function to apply on the view data.

#### `settingsKey: string`

The unique key for the UI Config Service that retrieves stored settings from a database. The service saves configuration settings for users and returns `selectedColumnIds` for the columns to display and the preferred column order. For more information, see the [sticky settings documentation](/skyux/learn/get-started/advanced/sticky-settings.md).

#### `width: number | Observable<number>`

The width of the grid.

### Outputs

#### `rowDeleteCancel: EventEmitter<SkyListViewGridRowDeleteCancelArgs>`

Fires when users cancel the deletion of a row.

#### `rowDeleteConfirm: EventEmitter<SkyListViewGridRowDeleteConfirmArgs>`

Fires when users confirm the deletion of a row.

#### `selectedColumnIdsChange: EventEmitter<string[]>`

Fires when columns change. This includes changes to the displayed columns and changes to the order of columns. The event emits an array of IDs for the displayed columns that reflects the column order.

 SkyListViewGridMessageType
---------------------------

Type: Enumeration

The command for the list view grid to respond to.

    enum SkyListViewGridMessageType {
      AbortDeleteRow = 1,
      PromptDeleteRow = 0,
    }

### Properties

#### `SkyListViewGridMessageType.AbortDeleteRow`

Cancels the deletion of a row in the list view grid.

#### `SkyListViewGridMessageType.PromptDeleteRow`

Deletes of a row in the list view grid.

 SkyListViewGridMessage
-----------------------

Type: Interface

Communicates commands to the list view grid.

    interface SkyListViewGridMessage {
      data?: { abortDeleteRow?: { id: string }; promptDeleteRow?: { id: string } };
      type: SkyListViewGridMessageType;
    }

### Properties

#### `data?: { abortDeleteRow?: { id: string }; promptDeleteRow?: { id: string } }`

The data required to carry out the command.

#### `type: SkyListViewGridMessageType`

The type of message to send.

 SkyListViewGridRowDeleteCancelArgs
-----------------------------------

Type: Interface

    interface SkyListViewGridRowDeleteCancelArgs {
      id: string;
    }

### Properties

#### `id: string`

The ID of the row where the Cancel button was clicked to cancel deleting the row.

 SkyListViewGridRowDeleteConfirmArgs
------------------------------------

Type: Interface

    interface SkyListViewGridRowDeleteConfirmArgs {
      id: string;
    }

### Properties

#### `id: string`

The ID of the row where the Confirm button was clicked to delete the row.

 SkyListColumnSelectorActionModule
----------------------------------

Type: Module

`import { SkyListColumnSelectorActionModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyListColumnSelectorActionComponent
-------------------------------------

Type: Component

Selector: `sky-list-column-selector-action`

Provides a column selector modal for a list grid view when placed in a [list toolbar](/skyux/components/list/toolbar.md).

### Inputs

#### `gridView: SkyListViewGridComponent`

Enables the column selector in the list toolbar. Set this attribute to the instance of the `sky-grid-view` component using the component's template reference variable.

#### `helpKey: string`

The `helpKey` string to associate with a help button in the grid header. When users select the button, the `helpOpened` event broadcasts the `helpKey` parameter.

### Outputs

#### `helpOpened: EventEmitter<string>`

Fires when users click the help button and broadcasts the `helpKey`.

 SkyColumnSelectorModule
------------------------

Type: Module

`import { SkyColumnSelectorModule } from '@skyux/list-builder-view-grids';`

Warning: **Deprecated.** List builder view grid and its features are deprecated. Use data entry grid instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-entry-grid](/skyux/components/data-entry-grid.md).

 SkyColumnSelectorContext
-------------------------

Type: Class

### Properties

#### `columns: SkyColumnSelectorModel[]`

#### `selectedColumnIds: string[]`

 SkyColumnSelectorModel
-----------------------

Type: Class

### Properties

#### `description: string`

#### `heading: string`

#### `id: string`
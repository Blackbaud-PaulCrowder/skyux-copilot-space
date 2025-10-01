---
component: 'list-view-grid'
description: 'Design guidelines, API documentation, and usage instructions for the list-view-grid component extracted from SKY UX documentation.'
---

# List View Grid Component Guidelines

## Component Overview
The list view grid component displays a grid for a SKY UX-themed list of data. List view grid and its features are deprecated. We will remove it in a future major version. We recommend using data grid instead.

## Usage

### ✅ Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

**✅ Do use grids to display data for users to visually scan and compare values.**

### ❌ Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use repeaters or card views instead. If the content requires multiple templated columns, use repeaters instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use repeaters instead.

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
- Flyout
- Grid
- List overview
- List filters
- List paging
- List toolbar
- List view checklist

### Guidelines

- Page layout

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
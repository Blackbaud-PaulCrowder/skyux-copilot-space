---
component: 'grid'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the grid component extracted from SKY UX documentation.'
---

# Grid Design Guidelines

## Component Overview
Grids provide a SKY UX-themed layout for tabular data. Grid is deprecated in favor of data grid. For more information, see the grid deprecation instructions.

## Usage

### ✅ Use when

Use grids when users need to view a large amount of data to visually scan for certain values or outliers and to compare values between rows.

### ❌ Don't use when

Don't use grids when the content calls for a more complex layout. If you need to display visual content such as graphs or images, use repeater or box layouts instead. If the content requires multiple templated columns, use repeaters instead. If the content includes many fields and users are likely to view it in small viewports such as phones, use repeaters instead.

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

### Sorting

If users are likely to sort based on the data in columns, enable sorting so that they can select column headers to toggle between ascending and descending order for the specified fields in columns. If users need to sort by data in a templated column, use the sort component instead to let them select the data to sort on.

### Filtering

If users are likely to work with a subset of items in the grid, enable filtering so that they can focus on those items.

### Templated items

When columns represent composite information instead of single values, use templated columns to lay out content as necessary.

## Behavior and states

### Fit

The fit determines how to place the grid within its parent. If the grid does not have enough columns to fill the parent's width, it always stretches to the parent's full width.

###### Scroll

The scroll option allows grids to take as much space as necessary by adding a horizontal scrollbar. This is most useful for grids with large numbers of columns.

###### Width

The width option fixes the width of the grid to its container and resizes columns to fit. This is most useful for simple grids in smaller containers, such as tiles, where the content fits neatly in the allotted space.

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
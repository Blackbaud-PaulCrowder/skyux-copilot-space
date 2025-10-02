---
component: 'data-grid'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the data-grid component extracted from SKY UX documentation.'
---

# Data Grid Design Guidelines

## Component Overview
Data grids provide a SKY UX-themed layout for tabular data. Combine data grids with data managers to allow users to manipulate larger data sets.

## Usage

### ✅ Use when

Use data grids to display large amounts of data when users need to compare values between rows or scan for specific values or outliers.

### ❌ Don't use when

Don't use data grids to display content that requires a complex layout. To display multiple templated columns, visual content such as graphs or images, or content that users are likely to view in small viewports such as phones, use repeaters instead.

## Anatomy

- Header row
- Row divider
- Data manager toolbar
- Filter bar
- Item count
- Data manager multiselect toolbar
- Help button
- Row selection checkbox
- Context-menu dropdown button
- Selected row
- Pagination
- Summary action bar

## Options

### Context-menu dropdown

To display actions that affect individual items in the data grid, use context-menu dropdowns.

### Help button

When you need to supplement a data grid column header with additional information but don't require persistent inline help, you can place a help button beside the header to invoke contextual user assistance.

### Filtering

To let users narrow down their list of items to a set they are interested in using structured criteria, use filtering.

### Multiselect

To let users select and perform actions on multiple rows, use data manager and enable multiselect.

Only use multiselect when the data grid container is a page, full-page modal, or flyout. Don't use multiselect with data grids in tiles, page sections, or other containers that can flow off the screen.

To let users select or clear all rows and view only selected items, include the multiselect toolbar. To display actions that users can perform on selected rows, display the summary action bar below the data grid.

### Sorting

Make column headers sortable. Sort by the leftmost column or the primary record column in the data grid. Always indicate a data grid’s sort order.

Only include the sort button in the toolbar if the list includes other views in addition to the data grid (e.g., repeater) or it contains templated columns where users need to sort by another property in that column.

### Templated items

To display composite information instead of single values, use templated columns.

## Behavior and states

### Fit

The fit determines how to place data grids within their containers. If a container is wider than the data grid, the fit stretches the data grid to fill the container.

The scroll option provides a horizontal scrollbar when data grids are wider than their containers, while the width option resizes data grid columns to fit in the fixed width of the container. The scroll option is useful for data grids with many columns, and the width option is useful for simple grids in small containers where content fits neatly in the allotted space.

### Reordering columns

To reorder columns, users can drag and drop them.

### Resizing columns

To resize columns, users can select and drag.

### Responsiveness

Data grids perform poorly in small viewports, such as mobile devices. Columns in fixed-width grids shrink to the point of being unreadable, and grids with horizontal scrollbars require a great deal of effort to view content. If you expect users to view content in small viewports, use repeaters or another pattern instead.

## Related information

### Components

- Data entry grid
- Data manager
- Dropdown
- Infinite scroll
- Paging
- Repeater
- Sort
- Summary action bar

### Guidelines

- Filter lists
- List page
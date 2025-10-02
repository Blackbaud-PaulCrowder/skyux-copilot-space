---
component: 'data-entry-grid'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the data-entry-grid component extracted from SKY UX documentation.'
---

# Data Entry Grid Design Guidelines

## Component Overview
Data entry grids use the third-party AG Grid library to provide a spreadsheet-like user interface to enter and edit large amounts of data. SKY UX provides styles, a service for default grid options, and components to render and edit cells. To learn about AG Grid and its capabilities, see the getting-started guide and additional documentation.

## Usage

### ✅ Use when

Use data entry grids when:

- Users have experience working with spreadsheets.
- Users edit many values at the same time.
- The dataset is large.

### ❌ Don't use when

Don't use data entry grids when:

- Data is view-only. Use data grid instead.
- Users need guidance for the task they are completing.
- Users only edit a small number of values at a time.
- The dataset is small.

## Anatomy

- Header cell
- Editable cell
- Focused cell
- Help button
- Read-only cell

## Options

### Disabled columns

To prevent users from editing the data in particular columns, disable the columns.

### Help button

When you need to supplement a data entry grid column header with additional information but don't require persistent inline help, you can place a help button beside the header to invoke contextual user assistance.

### Validation

To call attention to incorrect formats in cells, such as incorrect dates or currency values, enable validation. The component handles the styling automatically, so you don't need to worry about rendering the styling, but you do need to provide validation messages.

## Related information

### Components

- Data grid
- Data manager

### Guidelines

- Form design
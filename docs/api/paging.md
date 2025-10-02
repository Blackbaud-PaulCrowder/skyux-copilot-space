---
component: 'paging'
type: 'api-documentation'
description: 'API documentation for the paging component including components, interfaces, and types.'
---

# Paging API Documentation

## Components and Directives

#### AgGridDataGridPagingExampleComponent

**Selector:** `app-ag-grid-data-grid-paging-example`

**Package:** `@skyux/code-examples`

#### ListsPagingBasicExampleComponent

**Selector:** `app-lists-paging-basic-example`

**Package:** `@skyux/code-examples`

#### ListsPagingWithContentExampleComponent

**Selector:** `app-lists-paging-with-content-example`

**Package:** `@skyux/code-examples`

#### SkyListPagingComponent

Displays a pagination control for a SKY UX-themed list of data.

**Selector:** `sky-list-paging`

**Package:** `@skyux/list-builder`

**Inputs:**

- `maxPages`: `number | Observable<number>` - The maximum pages to display. (default: 5)
- `pageNumber`: `number | Observable<number>` - The current page number. (default: 1)
- `pageSize`: `number | Observable<number>` - The number of list items per page. (default: 10)

#### SkyPagingContentComponent

**Selector:** `sky-paging-content`

**Package:** `@skyux/lists`

#### SkyPagingComponent

**Selector:** `sky-paging`

**Package:** `@skyux/lists`

**Inputs:**

- `currentPage`: `number` - The page number of the current page. Page numbers start at 1 and increment. (default: 1)
- `itemCount`: `number` - The total number of items across all pages. (default: 0)
- `maxPages`: `number` - The maximum number of pages to display in the pagination control. (default: 5)
- `pageSize`: `number` - The number of items to display per page. (default: 10)
- `pagingLabel`: `string | undefined` - The label for the pagination control when an application includes
multiple paging components on the same page. The label should be unique and descriptive
to help users of assistive technology differentiate pagination controls
and understand what each one does. (default: "Pagination")

**Outputs:**

- `contentChange`: `EventEmitter<SkyPagingContentChangeArgs>` - Fires when the current page changes and emits the new current page with a function
to call when loading the new page completes. Handling this event will display the
wait component until the callback function is called, and focus will move to the top
of the list for keyboard navigation if the list contents are placed inside the
sky-paging-content element.
- `currentPageChange`: `EventEmitter<number>` - Fires when the current page changes and emits the new current page.
---
component: 'list-paging'
description: 'Design guidelines, API documentation, and usage instructions for the list-paging component extracted from SKY UX documentation.'
---

# List Paging Component Guidelines

## Component Overview
The list paging component displays a pagination control for a SKY UX-themed list of data. Lists and their features are deprecated. We will remove them in a future major version. We recommend using data manager and paging instead.

## Related information

### Components

- List overview
- List filters
- List toolbar
- List view checklist
- List view grid
- Paging

## API Documentation

### Components and Directives

#### SkyListPagingComponent

Displays a pagination control for a SKY UX-themed list of data.

**Selector:** `sky-list-paging`

**Package:** `@skyux/list-builder`

**Inputs:**

- `maxPages`: `number | Observable<number>` - The maximum pages to display. (default: 5)
- `pageNumber`: `number | Observable<number>` - The current page number. (default: 1)
- `pageSize`: `number | Observable<number>` - The number of list items per page. (default: 10)

⚠️ **This component is deprecated.**

#### SkyListPagingModule

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingModel

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetItemsPerPageAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetMaxPagesAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetPageNumberAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
---
component: 'list-filters'
description: 'Design guidelines, API documentation, and usage instructions for the list-filters component extracted from SKY UX documentation.'
---

# List Filters Component Guidelines

## Component Overview
List filters provide filtering capabilities for a SKY UX-themed list of data. Lists and their features are deprecated. We will remove them in a future major version. We recommend using data manager instead.

## Related information

### Components

- Filter
- List overview
- List paging
- List toolbar
- List view checklist
- List view grid

## API Documentation

### Components and Directives

#### SkyListFilterSummaryComponent

Creates a filter summary based on the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property. Place this component within the
[`sky-list-toolbar`](https://developer.blackbaud.com/skyux/components/list/toolbar) component.

**Selector:** `sky-list-filter-summary`

**Package:** `@skyux/list-builder`

**Outputs:**

- `summaryItemClick`: `EventEmitter<ListFilterModel>` - Emits a `ListFilterModel` when users select a summary item. A common use case is
to open a filter modal when this event is received.

⚠️ **This component is deprecated.**

#### SkyListFiltersModule

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListFiltersOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListFiltersUpdateAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
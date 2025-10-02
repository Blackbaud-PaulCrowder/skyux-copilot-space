---
component: 'filter-bar'
type: 'api-documentation'
description: 'API documentation for the filter-bar component including components, interfaces, and types.'
---

# Filter Bar API Documentation

## Components and Directives

#### FilterBarBasicExampleComponent

**Selector:** `app-filter-bar-basic-example`

**Package:** `@skyux/code-examples`

#### SkyFilterBarComponent

The top-level filter bar component.

**Selector:** `sky-filter-bar`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `appliedFilters`: `ModelSignal<undefined | SkyFilterBarFilterItem[]>` - An array of filter items containing the IDs and values of the filters that have been set.
- `selectedFilterIds`: `ModelSignal<undefined | string[]>` - An array of filter IDs that the user has selected using the built-in selection modal. Setting this input to undefined results in all filters being displayed.
---
component: 'list-view-checklist'
description: 'Design guidelines, API documentation, and usage instructions for the list-view-checklist component extracted from SKY UX documentation.'
---

# List View Checklist Component Guidelines

## Component Overview
The list view checklist displays a checklist within a SKY UX-themed list of data and enables consumers to define a custom search function for the data. List view checklist and its features are deprecated. We will remove it in a future major version. We recommend using selection modal instead.

## Related information

### Components

- List overview
- List filters
- List paging
- List toolbar
- List view grid

## API Documentation

### Components and Directives

#### SkyListViewChecklistItemComponent

**Selector:** `sky-list-view-checklist-item`

**Package:** `@skyux/list-builder-view-checklist`

**Inputs:**

- `item`: `ListViewChecklistItemModel`

⚠️ **This component is deprecated.**

#### SkyListViewChecklistComponent

**Selector:** `sky-list-view-checklist`

**Package:** `@skyux/list-builder-view-checklist`

**Inputs:**

- `description`: `string` - The name of the description field selector. (default: "description")
- `label`: `string` - The name of the label field selector. (default: "label")
- `search`: `(data: any, searchText: string) => boolean` - The search function to apply on the view data.
The default function searches view data on label, description,
and category if field selectors are defined for the given field. (default: default search function)
- `name`: `string` - The name of the view. **[Required]**
- `selectMode`: `string` - How many items users can select.
`"single"` allows users to select one item in the checklist, while `"multiple"`
allows users to select multiple items in the checklist. (default: "multiple")
- `showOnlySelected`: `boolean` - Whether to display selected items only. (default: false)

⚠️ **This component is deprecated.**

#### SkyListViewChecklistModule

**Package:** `@skyux/list-builder-view-checklist`

⚠️ **This component is deprecated.**

#### ListViewChecklistItemModel

**Package:** `@skyux/list-builder-view-checklist`

⚠️ **This component is deprecated.**

#### ListViewChecklistItemsOrchestrator

**Package:** `@skyux/list-builder-view-checklist`

⚠️ **This component is deprecated.**

#### ListViewChecklistItemsLoadAction

**Package:** `@skyux/list-builder-view-checklist`

⚠️ **This component is deprecated.**

#### SkyListViewChecklistFixture

Allows interaction with a SKY UX list view checklist component.

**Package:** `@skyux/list-builder-view-checklist/testing`

⚠️ **This component is deprecated.**

#### SkyListViewChecklistItem

Properties of a list view checklist item.

**Package:** `@skyux/list-builder-view-checklist/testing`

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
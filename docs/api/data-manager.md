---
component: 'data-manager'
type: 'api-documentation'
description: 'API documentation for the data-manager component including components, interfaces, and types.'
---

# Data Manager API Documentation

## Components and Directives

#### AgGridDataEntryGridDataManagerAddedExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-data-manager-added-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridDataManagerMultiselectExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-multiselect-example`

**Package:** `@skyux/code-examples`

#### AgGridDataGridDataManagerExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-example`

**Package:** `@skyux/code-examples`

#### DataManagerBasicExampleComponent

**Selector:** `app-data-manager-basic-example`

**Package:** `@skyux/code-examples`

#### SkyDataManagerColumnPickerComponent

**Selector:** `sky-data-manager-column-picker`

**Package:** `@skyux/data-manager`

#### SkyDataManagerToolbarLeftItemComponent

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are
rendered after the standard toolbar actions and before the search box. Each item should be
wrapped in its own `sky-data-manager-toolbar-left-item`. The items render in the order they are in in the template.

**Selector:** `sky-data-manager-toolbar-left-item`

**Package:** `@skyux/data-manager`

#### SkyDataManagerToolbarPrimaryItemComponent

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are
rendered as the first items in the toolbar and should be standard actions. Each item should be
wrapped in its own `sky-data-manager-toolbar-primary-item`. The items render in the order they are in in the template.

**Selector:** `sky-data-manager-toolbar-primary-item`

**Package:** `@skyux/data-manager`

#### SkyDataManagerToolbarRightItemComponent

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are
rendered in `sky-toolbar-view-actions` on the right side of the toolbar and before the view
switcher icons (if present). Each item should be wrapped in its own
`sky-data-manager-toolbar-right-item`. The items render in the order they are in in the template.

**Selector:** `sky-data-manager-toolbar-right-item`

**Package:** `@skyux/data-manager`

#### SkyDataManagerToolbarSectionComponent

A wrapper for items to be rendered in `SkyDataManagerToolbarComponent`. The contents are
rendered in an additional toolbar row beneath the primary toolbar and above the multiselect
toolbar (if present).

**Selector:** `sky-data-manager-toolbar-section`

**Package:** `@skyux/data-manager`

#### SkyDataManagerToolbarComponent

Renders a `sky-toolbar` with the contents specified by the active view's `SkyDataViewConfig`
and the `SkyDataManagerToolbarLeftItemComponent`, `SkyDataManagerToolbarRightItemComponent`,
and `SkyDataManagerToolbarSectionComponent` wrappers.

**Selector:** `sky-data-manager-toolbar`

**Package:** `@skyux/data-manager`

#### SkyDataManagerComponent

The top-level data manager component. Provide `SkyDataManagerService` at this level.

**Selector:** `sky-data-manager`

**Package:** `@skyux/data-manager`

#### SkyAgGridDataManagerAdapterDirective

**Selector:** `[skyAgGridDataManagerAdapter]`

**Package:** `@skyux/ag-grid`

**Inputs:**

- `viewId`: `string | undefined`
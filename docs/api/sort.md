---
component: 'sort'
type: 'api-documentation'
description: 'API documentation for the sort component including components, interfaces, and types.'
---

# Sort API Documentation

## Components and Directives

#### ListsSortBasicExampleComponent

**Selector:** `app-lists-sort-basic-example`

**Package:** `@skyux/code-examples`

#### SkyListToolbarSortComponent

Adds a sort dropdown to the list toolbar.

**Selector:** `sky-list-toolbar-sort`

**Package:** `@skyux/list-builder`

**Inputs:**

- `descending`: `boolean` - Whether to sort data in descending order. (default: false)
- `field`: `string` - The data field to sort the list on.
- `label`: `string` - The label for a sort option.
- `type`: `string` - The data type of the data field to sort the list on.

#### SkySortItemComponent

**Selector:** `sky-sort-item`

**Package:** `@skyux/lists`

**Inputs:**

- `active`: `boolean | undefined` - Whether the sorting option is active.

**Outputs:**

- `itemSelect`: `EventEmitter<any>` - Fires when a sort item is selected.

#### SkySortComponent

**Selector:** `sky-sort`

**Package:** `@skyux/lists`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the sort button. This sets the
sort button's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Sort constituents." Context is especially important when multiple filter buttons are in close proximity.
In toolbars, sort buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Sort <listDescriptor>."
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `showButtonText`: `boolean | undefined` - Whether to display a "Sort" label beside the icon on the sort button. (default: false)
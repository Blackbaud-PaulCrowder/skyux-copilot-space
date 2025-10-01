---
component: 'list-toolbar'
description: 'Design guidelines, API documentation, and usage instructions for the list-toolbar component extracted from SKY UX documentation.'
---

# List Toolbar Component Guidelines

## Component Overview
The list toolbar component displays a toolbar for a SKY UX-themed list of data. Lists and their features are deprecated. We will remove them in a future major version. We recommend using data manager instead.

## Usage

### ✅ Use when

Do use the list toolbar above a list of records to display actions that manipulate the contents of the list. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. When multiple views of the list are available, the view switcher is docked on the right side of the toolbar.

**✅ Do use list toolbars to display actions that manipulate list items.**

## Options

### Composition

For more information about how to arrange content in a list toolbar, see the toolbar design guidelines.

### Sorting

If you use the toolbar with a grid view, you have two options to let users sort the list:

- The sort button in the toolbar
- Clickable column headers

Don't use both sorting options on the same list because it can confuse users about which option is applied.

## Related information

### Components

- List overview
- List filters
- List paging
- List view checklist
- List view grid
- Search
- Toolbar

## API Documentation

### Components and Directives

#### SkyListToolbarItemComponent

Defines a toolbar item for the list toolbar.

**Selector:** `sky-list-toolbar-item`

**Package:** `@skyux/list-builder`

**Inputs:**

- `id`: `string` - The ID of the item.
- `index`: `number` - The index of the item at the given item location. (default: -1)
- `location`: `string` - The toolbar location of the item. The valid options are `"left"`,
`"center"`, and `"right"`. (default: "left")

⚠️ **This component is deprecated.**

#### SkyListToolbarSearchActionsComponent

Displays custom actions in the toolbar beside to the search bar.

**Selector:** `sky-list-toolbar-search-actions`

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyListToolbarSortComponent

Adds a sort dropdown to the list toolbar.

**Selector:** `sky-list-toolbar-sort`

**Package:** `@skyux/list-builder`

**Inputs:**

- `descending`: `boolean` - Whether to sort data in descending order. (default: false)
- `field`: `string` - The data field to sort the list on. **[Required]**
- `label`: `string` - The label for a sort option. **[Required]**
- `type`: `string` - The data type of the data field to sort the list on. **[Required]**

⚠️ **This component is deprecated.**

#### SkyListToolbarViewActionsComponent

Adds a section on the right side of the toolbar for items that substantially change
or affect the view of the list. This includes simple filters and view switchers.
If the view section includes more than one item, simple filters appear on the left
and view switchers appear on the right.

**Selector:** `sky-list-toolbar-view-actions`

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyListToolbarComponent

Displays a toolbar for a SKY UX-themed list of data.

**Selector:** `sky-list-toolbar`

**Package:** `@skyux/list-builder`

**Inputs:**

- `placeholder`: `string` - Placeholder text for the search bar that the list toolbar creates with
a [search component](https://developer.blackbaud.com/skyux/components/search). (default: "Find in this list")
- `searchEnabled`: `boolean | Observable<boolean>` - Whether to enable the search bar. (default: true)
- `searchText`: `string | Observable<string>` - The text string to search with.
- `sortSelectorEnabled`: `boolean | Observable<boolean>` - Whether to enable the sort selector. (default: false)
- `toolbarType`: `string` - Display the search bar in the standard position or in a separate section.
To highlight the search bar in a section above all other toolbar items,
set this property to `search`. (default: "standard")
- `inMemorySearchEnabled`: `boolean` - Whether to use the in-memory search.
Setting this to `false` will allow consumers to run their own searches remotely,
and push new values to the list component by updating the `data` property. (default: true)

⚠️ **This component is deprecated.**

#### SkyListToolbarModule

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarItemsDisableAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarItemsLoadAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarItemsRemoveAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarSetExistsAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarSetTypeAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarShowMultiselectToolbarAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarItemModel

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarModel

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListToolbarOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
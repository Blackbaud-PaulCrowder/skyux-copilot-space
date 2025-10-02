---
component: 'toolbar'
type: 'api-documentation'
description: 'API documentation for the toolbar component including components, interfaces, and types.'
---

# Toolbar API Documentation

## Components and Directives

#### LayoutToolbarBasicExampleComponent

**Selector:** `app-layout-toolbar-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutToolbarSectionedExampleComponent

**Selector:** `app-layout-toolbar-sectioned-example`

**Package:** `@skyux/code-examples`

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

#### SkyListToolbarItemComponent

Defines a toolbar item for the list toolbar.

**Selector:** `sky-list-toolbar-item`

**Package:** `@skyux/list-builder`

**Inputs:**

- `id`: `string` - The ID of the item.
- `index`: `number` - The index of the item at the given item location. (default: -1)
- `location`: `string` - The toolbar location of the item. The valid options are `"left"`,
`"center"`, and `"right"`. (default: "left")

#### SkyListToolbarSearchActionsComponent

Displays custom actions in the toolbar beside to the search bar.

**Selector:** `sky-list-toolbar-search-actions`

**Package:** `@skyux/list-builder`

#### SkyListToolbarSortComponent

Adds a sort dropdown to the list toolbar.

**Selector:** `sky-list-toolbar-sort`

**Package:** `@skyux/list-builder`

**Inputs:**

- `descending`: `boolean` - Whether to sort data in descending order. (default: false)
- `field`: `string` - The data field to sort the list on.
- `label`: `string` - The label for a sort option.
- `type`: `string` - The data type of the data field to sort the list on.

#### SkyListToolbarViewActionsComponent

Adds a section on the right side of the toolbar for items that substantially change
or affect the view of the list. This includes simple filters and view switchers.
If the view section includes more than one item, simple filters appear on the left
and view switchers appear on the right.

**Selector:** `sky-list-toolbar-view-actions`

**Package:** `@skyux/list-builder`

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

#### SkyTextEditorToolbarComponent

**Selector:** `sky-text-editor-toolbar`

**Package:** `@skyux/text-editor`

**Inputs:**

- `disabled`: `boolean` (default: false)
- `fontList`: `SkyTextEditorFont[]` (default: [])
- `fontSizeList`: `number[]` (default: [])
- `linkWindowOptions`: `SkyTextEditorLinkWindowOptionsType[]` (default: [])
- `toolbarActions`: `SkyTextEditorToolbarActionType[]` (default: [])
- `editorFocusStream`: `Subject<void>`
- `styleState`: `SkyTextEditorStyleState`

#### SkyToolbarItemComponent

Specifies a container for an item in the toolbar.

**Selector:** `sky-toolbar-item`

**Package:** `@skyux/layout`

#### SkyToolbarSectionComponent

Specifies a section to group items within the toolbar. The section displays items in a separate horizontal row.

**Selector:** `sky-toolbar-section`

**Package:** `@skyux/layout`

#### SkyToolbarViewActionsComponent

Adds a section on the right side of the toolbar for items that substantially alter
the view of the content container. This includes simple filters and view switchers.

**Selector:** `sky-toolbar-view-actions`

**Package:** `@skyux/layout`

#### SkyToolbarComponent

Displays actions for lists, records, and tiles.

**Selector:** `sky-toolbar`

**Package:** `@skyux/layout`

**Inputs:**

- `listDescriptor`: `string | undefined` - A descriptor for the items that the toolbar manipulates. Use a plural term. The descriptor helps set the toolbar's `aria-label` attributes for search inputs, sort buttons, and filter buttons to provide text equivalents for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
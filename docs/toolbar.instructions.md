---
component: 'toolbar'
description: 'Design guidelines, API documentation, and usage instructions for the toolbar component extracted from SKY UX documentation.'
---

# Toolbar Component Guidelines

## Component Overview
The toolbar component displays actions to manipulate a list or to manipulate the individual items in the list.

## Usage

### ✅ Use when

Use list toolbars to display actions that manipulate the contents of lists of records. Place frequently used actions directly in the toolbar, and place less-frequently used actions in the more actions menu. When multiple views are available, dock the view switcher on the right.

Use toolbars to display actions that manipulate lists within containers, such as boxes or modals. Only place the most important actions directly in the toolbar because containers have limited horizontal real estate. Place all other actions in the more actions dropdown.

For guidance on how to incorporate filters into lists within containers, see filter lists guidelines.

### ❌ Don't use when

Don't use toolbars on record page headers to display page actions. Instead, place page actions directly below the record details.

Don't use toolbars in action hub headers to display actions related to action hub content. Instead, place common action buttons directly on the page below the page title.

## Options

Only include toolbar options that are relevant to a particular list, and organize them consistently in their designated locations.

### Standard toolbar actions

Place standard actions to the far left of the toolbar, and organize them from left to right based on the order in this section.

Don't include primary action buttons in toolbars.

## Behavior and states

### Toolbar action wrapping

Do not extend the standard actions and more actions menu beyond 50 percent of the toolbar.

If the standard actions extend beyond 50 percent of the toolbar, create a more actions menu for at least two of the rightmost actions.

### Small form factors

On small screens, action buttons switch to icon-only buttons, the search field collapses into a search icon, and the view switcher collapses into a single icon. Buttons without icons go in the more actions menu, and the more actions button, view switcher, and any other buttons with dropdowns display their options when selected.

## Layout

When two toolbars are stacked, place a border separator between them.

**✅ Do include a border separator between the toolbars.**

## Related information

### Components

- Box
- Buttons
- Data manager
- Search

### Guidelines

- List page
- Record page
- Terminology

## API Documentation

### Components and Directives

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

#### SkyDataManagerToolbarHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarHarness

Harness for interacting with a data manager toolbar component in tests.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarLeftItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarLeftItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarLeftItemHarness

Harness to interact with a data manager toolbar left item component in tests.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarPrimaryItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarPrimaryItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarPrimaryItemHarness

Harness to interact with a data manager toolbar primary item component in tests.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarRightItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarRightItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarRightItemHarness

Harness to interact with a data manager toolbar right item component in tests.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarSectionHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarSectionHarness

Harness to interact with a data manager toolbar section component in tests.

**Package:** `@skyux/data-manager/testing`

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

#### SkyTextEditorToolbarActionType

**Package:** `@skyux/text-editor`

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

#### SkyToolbarModule

**Package:** `@skyux/layout`

#### SkyToolbarHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarHarness

Harness for interacting with a toolbar component in tests.

**Package:** `@skyux/layout/testing`

#### SkyToolbarItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarItemHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarItemHarness

Harness to interact with a toolbar item component in tests.

**Package:** `@skyux/layout/testing`

#### SkyToolbarSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarSectionHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarSectionHarness

Harness to interact with a toolbar section component in tests.

**Package:** `@skyux/layout/testing`

#### SkyToolbarViewActionsHarness

Harness to interact with a toolbar view actions component in tests.

**Package:** `@skyux/layout/testing`

### Code Examples

#### Toolbar with basic setup

**Selector:** `app-layout-toolbar-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyToolbarModule } from '@skyux/layout';

/**
 * @title Toolbar with basic setup
 */
@Component({
  selector: 'app-layout-toolbar-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule, SkyToolbarModule],
})
export class LayoutToolbarBasicExampleComponent {
  public onButtonClicked(buttonText: string): void {
    alert(buttonText + ' clicked!');
  }
}

```

**Template:**

```html
<sky-toolbar data-sky-id="basic-toolbar">
  <sky-toolbar-item data-sky-id="toolbar-item-1">
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="onButtonClicked('Button 1')"
    >
      Button 1
    </button>
  </sky-toolbar-item>
  <sky-toolbar-item data-sky-id="toolbar-item-2">
    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="onButtonClicked('Button 2')"
    >
      Button 2
    </button>
  </sky-toolbar-item>
  <sky-toolbar-view-actions>
    <button
      class="sky-btn sky-btn-default sky-btn-icon"
      title="Sort descending"
      type="button"
      (click)="onButtonClicked('Expand')"
    >
      <sky-icon iconName="chevron-double-down" />
    </button>
    <button
      class="sky-btn sky-btn-default sky-btn-icon"
      title="Sort ascending"
      type="button"
      (click)="onButtonClicked('Collapse')"
    >
      <sky-icon iconName="chevron-double-up" />
    </button>
  </sky-toolbar-view-actions>
</sky-toolbar>

```

#### Toolbar with sections

**Selector:** `app-layout-toolbar-sectioned-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyToolbarModule } from '@skyux/layout';

/**
 * @title Toolbar with sections
 */
@Component({
  selector: 'app-layout-toolbar-sectioned-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule, SkyToolbarModule],
})
export class LayoutToolbarSectionedExampleComponent {
  public onButtonClicked(buttonText: string): void {
    alert(buttonText + ' clicked!');
  }
}

```

**Template:**

```html
<sky-toolbar data-sky-id="sectioned-toolbar">
  <sky-toolbar-section data-sky-id="top-section">
    <sky-toolbar-item data-sky-id="toolbar-item-1">
      <button
        class="sky-btn sky-btn-primary"
        type="button"
        (click)="onButtonClicked('Button 1')"
      >
        Button 1
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item data-sky-id="toolbar-item-2">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Button 2')"
      >
        Button 2
      </button>
    </sky-toolbar-item>
    <sky-toolbar-view-actions>
      <button
        class="sky-btn sky-btn-default sky-btn-icon"
        title="Sort descending"
        type="button"
        (click)="onButtonClicked('Expand')"
      >
        <sky-icon iconName="chevron-double-down" />
      </button>
      <button
        class="sky-btn sky-btn-default sky-btn-icon"
        title="Sort ascending"
        type="button"
        (click)="onButtonClicked('Collapse')"
      >
        <sky-icon iconName="chevron-double-up" />
      </button>
    </sky-toolbar-view-actions>
  </sky-toolbar-section>
  <sky-toolbar-section data-sky-id="bottom-section">
    <sky-toolbar-item data-sky-id="sort-button">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Sort')"
      >
        <sky-icon iconName="arrow-sort" /> Sort
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item data-sky-id="filter-button">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Filter')"
      >
        <sky-icon iconName="filter" /> Filter
      </button>
    </sky-toolbar-item>
  </sky-toolbar-section>
</sky-toolbar>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
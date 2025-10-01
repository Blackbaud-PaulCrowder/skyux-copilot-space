---
component: 'vertical-tabs'
description: 'Design guidelines, API documentation, and usage instructions for the vertical-tabs component extracted from SKY UX documentation.'
---

# Vertical Tabs Component Guidelines

## Component Overview
Vertical tabs divide and categorize content on pages with a large number of categories.

## Usage

### ✅ Use when

Use vertical tabs when you expect horizontal tabs to exceed the available horizontal space because of the number of tabs or the length of tab labels.

Use collapsible groups to organize vertical tabs that fit naturally into multiple categories.

### ❌ Don't use when

Don't use vertical tabs when horizontal tabs are appropriate. If the expected number of tabs is small and grouping is not necessary, use horizontal tabs instead.

Don't use vertical tabs as containers for other tabs. Change the workflow instead of nesting multiple sets of tabs.

Don't use vertical tabs when the workflow requires users to view and perform actions on each tab. Use split views instead.

Don't use vertical tabs in modals. Use sectioned forms instead. The two approaches look similar, but sectioned forms have additional features, such as displaying validation errors in form sections.

## Anatomy

- Vertical tabset
- Unselected tab
- Tab label
- Selected tab
- Tabset border
- Selected tab group
- Tab group label
- Unselected tab group
- Expand/collapse icon

## Options

### Collapsible groups

You can organize vertical tabs into collapsible groups when the categories help users.

## Behavior and states

### States

## Layout

Vertical tabs are always the bottom-most content in their containers. Don't include additional content after vertical tabs.

## Related information

### Components

- Sectioned form
- Split view
- Tabs

### Guidelines

- Page design

## API Documentation

### Components and Directives

#### TabsVerticalTabsBasicExampleComponent

**Selector:** `app-tabs-vertical-tabs-basic-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsGroupedExampleComponent

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsMixedExampleComponent

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**Package:** `@skyux/code-examples`

#### SkyVerticalTabsetGroupComponent

**Selector:** `sky-vertical-tabset-group`

**Package:** `@skyux/tabs`

**Inputs:**

- `groupHeading`: `string | undefined` - The header for the collapsible group of tabs.
- `disabled`: `boolean | undefined` - Whether to disable the ability to expand and collapse the group. (default: false)
- `open`: `boolean | undefined` - Whether the collapsible group is expanded. (default: false)

#### SkyVerticalTabsetComponent

**Selector:** `sky-vertical-tabset`

**Package:** `@skyux/tabs`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `maintainTabContent`: `boolean | undefined` - Whether the vertical tabset loads tab content during initialization so that it
displays content without moving around elements in the content container. (default: false)
- `showTabsText`: `string | undefined` - The text to display on the show tabs button on mobile devices.
- `ariaRole`: `string` - The ARIA role for the vertical tabset
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating how the tabset functions and what it controls. For information about how
an ARIA role indicates what an item represents on a web page, see the
[WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles). (default: "tablist")

**Outputs:**

- `activeChange`: `EventEmitter<number>` - Fires when the active tab changes. Emits the index of the active tab. The
index is based on the tab's position when it loads.

#### SkyVerticalTabsetModule

**Package:** `@skyux/tabs`

#### SkyVerticalTabsetGroupHarnessFilters

A set of criteria that can be used to filter a list of  `SkyVerticalTabsetGroupHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabsetGroupHarness

Harness for interacting with a vertical tabset group in tests.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabsetHarnessFilters

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabsetHarness

Harness for interacting with the vertical tabset component in tests.

**Package:** `@skyux/tabs/testing`

### Code Examples

#### Vertical tabs with basic setup

**Selector:** `app-tabs-vertical-tabs-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

/**
 * @title Vertical tabs with basic setup
 */
@Component({
  selector: 'app-tabs-vertical-tabs-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsBasicExampleComponent {}

```

**Template:**

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-basic">
  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 content </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 2" [active]="true">
    Tab 2 content
  </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

#### Vertical tabs with grouped tabs

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-grouped-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsGroupedExampleComponent {
  protected groups: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: false,
      isDisabled: false,
      subTabs: [
        { tabHeading: 'Group 1 — Tab 1', content: 'Group 1 — Tab 1 Content' },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
          tabHeaderCount: 7,
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: true,
      isDisabled: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 2 — Tab 2 — Disabled',
          content: 'Group 2 — Tab 2 Content',
          disabled: true,
        },
      ],
    },
    {
      heading: 'Disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [],
    },
  ];
}

```

**Template:**

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-group" showTabsText="Tab list">
  @for (group of groups; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab
          [active]="tab.active"
          [tabHeading]="tab.tabHeading"
          [tabHeaderCount]="tab.tabHeaderCount"
          [disabled]="tab.disabled"
        >
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }
</sky-vertical-tabset>

```

#### Vertical tabs with grouped and ungrouped tabs

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped and ungrouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-mixed-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsMixedExampleComponent {
  protected groupedTabs: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: true,
      subTabs: [
        {
          tabHeading: 'Group 1 — Tab 1',
          content: 'Group 1 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 2 — Tab 2',
          content: 'Group 2 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 3 - disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [
        {
          tabHeading: 'Group 3 — Tab 1',
          content: 'Group 3 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 3 — Tab 2',
          content: 'Group 3 — Tab 2 Content',
        },
      ],
    },
  ];
}

```

**Template:**

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-mixed" showTabsText="Tab list">
  @for (group of groupedTabs; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab [active]="tab.active" [tabHeading]="tab.tabHeading">
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }

  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 Content </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 2" [tabHeaderCount]="3">
    Tab 2 Content
  </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 Content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
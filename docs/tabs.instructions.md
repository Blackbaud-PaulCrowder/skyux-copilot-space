---
component: 'tabs'
description: 'Design guidelines, API documentation, and usage instructions for the tabs component extracted from SKY UX documentation.'
---

# Tabs Component Guidelines

## Component Overview
Tabs divide and categorize large amounts of content on a page.

## Usage

### ✅ Use when

Use tabs when users require quick access to different slices of the same data.

Use tabs when users need to complete different tasks on a page and each task includes a significant amount of data.

### ❌ Don't use when

Don't use tabs within another tab. Change the workflow instead of nesting multiple sets of tabs.

Don't use tabs when they are likely to overflow the available horizontal space. The collapsed behavior of tabs will accommodate small screen resolutions or cases where users add many tabs themselves, but it is not intended as the default experience with a tabset. Use vertical tabs instead.

## Anatomy

- Selected tab
- Unselected tab
- Tab border
- Tab panel
- Close tab button
- Add tab button

## Options

### Add and close

If users need to work with a subset of tabs in a large tabset, let them add and close tabs to display only the relevant tabs.

If a new tab includes multiple options on what to display, use action buttons in the tab view to let users make selections.

### Tab layouts

The following tab layouts can be used for organizing content within a tab panel.

#### Blocks

Use blocks tab layout for laying out blocks of content in a tab panel.

Place a fluid grid or other grid layouts via flexbox or CSS grid in page content area to acheive a large range of content layouts.

#### List

Use the list layout for lists of data.

#### Fit

Use the fit layout for content to fill the content area and be anchored to the edges of the tab panel.

#### None

Use the none layout for custom layouts and content within a tab panel.

## Behavior and states

### Overflowing tabs

If the tabset includes too many tabs to fit in the tab bar's available horizontal space, the tabs collapse into a dropdown.

### States

## Layout

### Tab order

Organize tabs according to the specific needs of the page or record, with the most important or commonly used tabs on the left. For example, organize record page tabs into four groups:

- Overview tab (optional)
- Context-specific tabs
- SKY Add-in tabs (optional)
- Common tabs (optional)

### Placement and spacing

Tabs are always the last (bottommost) content in their container. Don't put additional content under tabs.

The tab border extends the full width of the container. Don't use left or right margins on the tab border, and ignore any padding that the container defines.

Tab content does not have additional left or right padding. The left and right gutters align with the gutters for content outside the tabs.

## Content

Use short, straightforward labels to clearly communicate the purpose of tabs. For consistency, use “Overview” when the first tab displays summary information. For example, use an Overview tab on record pages to display primary or identifying data and inform users about the current state and history of the record.

## Related information

### Components

- Action buttons
- Vertical tabs

### Guidelines

- Content containers
- Page design

## API Documentation

### Components and Directives

#### PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageRecordPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### TabsDynamicAddCloseExampleComponent

**Selector:** `app-tabs-dynamic-add-close-example`

**Package:** `@skyux/code-examples`

#### TabsDynamicExampleComponent

**Selector:** `app-tabs-dynamic-example`

**Package:** `@skyux/code-examples`

#### TabsStaticAddCloseExampleComponent

**Selector:** `app-tabs-static-add-close-example`

**Package:** `@skyux/code-examples`

#### TabsStaticExampleComponent

**Selector:** `app-tabs-static-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsBasicExampleComponent

**Selector:** `app-tabs-vertical-tabs-basic-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsGroupedExampleComponent

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsMixedExampleComponent

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**Package:** `@skyux/code-examples`

#### TabsWizardBasicExampleComponent

**Selector:** `app-tabs-wizard-basic-example`

**Package:** `@skyux/code-examples`

#### SkyTabsModule

**Package:** `@skyux/tabs`

#### SkyTabsetButtonsDisplayMode

**Package:** `@skyux/tabs`

#### SkyTabsetNavButtonType

The nav button type.

**Package:** `@skyux/tabs`

#### SkyTabsetNavButtonComponent

Creates a button to navigate between tabs in a tabset when `tabStyle` is `"wizard"`.

**Selector:** `sky-tabset-nav-button`

**Package:** `@skyux/tabs`

**Inputs:**

- `buttonText`: `string` - The label to display on the nav button. The following are the defaults for each `buttonType`:
`next` = "Next", `previous` = "Previous", `finish` = "Finish"
- `buttonType`: `SkyTabsetNavButtonType | undefined` - The type of nav button to include. **[Required]**
- `disabled`: `boolean | undefined` - Whether to disable the nav button.
Defaults to the disabled state of the next tab for `next`, the existence of a previous tab for `previous`,
and false for `finish`.
- `tabset`: `SkyTabsetComponent | undefined` - The tabset wizard component to associate with the nav button. **[Required]**

#### SkyTabsetStyle

**Package:** `@skyux/tabs`

#### SkyTabsetTabIndexesChange

**Package:** `@skyux/tabs`

#### SkyTabsetComponent

**Selector:** `sky-tabset`

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
- `active`: `SkyTabIndex | undefined` - Activates a tab by its `tabIndex` property.
- `permalinkId`: `string` - Distinguishes a tabset's unique state in the URL by generating a query parameter
that is written as `?<queryParam>-active-tab=<sanitized-tab-heading>`.
The query parameter's value is parsed automatically from the selected tab's heading text,
but you can supply a custom query parameter value for each tab with its `permalinkValue`.
This input only applies when `tabStyle` is `"tabs"`
- `tabStyle`: `SkyTabsetStyle` - The behavior for a series of tabs. (default: "tabs")

**Outputs:**

- `activeChange`: `EventEmitter<SkyTabIndex>` - Fires when the active tab changes. This event emits the index of the active tab.
- `newTab`: `EventEmitter<void>` - Fires when users click the button to add a new tab.
The new tab button is added to the tab area when you specify a listener for this event.
This event only applies when `tabStyle` is `"tabs"`.
- `openTab`: `EventEmitter<void>` - Fires when users click the button to open a tab.
The open tab button is added to the tab area when you specify a listener for this event.
This event only applies when `tabStyle` is `"tabs"`.
- `tabIndexesChange`: `EventEmitter<SkyTabsetTabIndexesChange>` - Fires when any tab's `tabIndex` value changes.
This event only applies when `tabStyle` is `"tabs"`.

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

#### SkyTabsetFixtureTab

Properties of a SKY UX tab.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetFixture

Allows interaction with a SKY UX tabset component.

**Package:** `@skyux/tabs/testing`

⚠️ **This component is deprecated.**

#### SkyTabsetHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabsetHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetHarness

Harness for interacting with a tabset component in tests.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetNavButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabsetNavButtonHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetNavButtonHarness

Harness to interact with tabset nav buttons in wizard style tabset tests.

**Package:** `@skyux/tabs/testing`

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

#### List page with tabs layout using data manager

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageTabsLayoutExampleComponent {}

```

**Template:**

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + contactName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + contactName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + contactName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Record page with tabs layout using data manager

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyAlertModule, SkyLabelModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [
    RecordPageContentComponent,
    SkyAlertModule,
    SkyAvatarModule,
    SkyLabelModule,
    SkyPageModule,
  ],
})
export class PagesPageRecordPageTabsLayoutExampleComponent {}

```

**Template:**

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + attachmentName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + attachmentName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + attachmentName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Sectioned form inside modal

**Selector:** `app-tabs-sectioned-form-modal-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Sectioned form inside modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-sectioned-form-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class TabsSectionedFormModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  public openModal(): void {
    const modalInstance = this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel') {
        console.log(`Modal cancelled`);
      } else if (result.reason === 'save') {
        console.log(`Modal saved`);
      }
    });
  }
}

```

**Template:**

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
  Open sectioned form
</button>

```

#### Tabs bound to an array, with add and close buttons

**Selector:** `app-tabs-dynamic-add-close-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs bound to an array, with add and close buttons
 */
@Component({
  selector: 'app-tabs-dynamic-add-close-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsDynamicAddCloseExampleComponent {
  protected tabArray = [
    {
      tabHeading: 'Tab 1',
      tabContent: 'Content for Tab 1',
    },
    {
      tabHeading: 'Tab 2',
      tabContent: 'Content for Tab 2',
    },
    {
      tabHeading: 'Tab 3',
      tabContent: 'Content for Tab 3',
    },
  ];

  #tabCounter = 3;

  protected onNewTabClick(): void {
    this.#tabCounter++;

    this.tabArray.push({
      tabHeading: 'Tab ' + this.#tabCounter,
      tabContent: 'Content for Tab' + this.#tabCounter,
    });
  }

  protected onCloseClick(arrayIndex: number): void {
    this.tabArray.splice(arrayIndex, 1);
  }
}

```

**Template:**

```html
<sky-tabset
  ariaLabel="Tab demonstration"
  data-sky-id="tab-demo"
  (newTab)="onNewTabClick()"
>
  @for (tab of tabArray; track tab; let i = $index) {
    <sky-tab [tabHeading]="tab.tabHeading" (close)="onCloseClick(i)">
      {{ tab.tabContent }}
    </sky-tab>
  }
</sky-tabset>

```

#### Tabs bound to an array

**Selector:** `app-tabs-dynamic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs bound to an array
 */
@Component({
  selector: 'app-tabs-dynamic-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsDynamicExampleComponent {
  protected tabArray = [
    {
      tabHeading: 'Tab 1',
      tabContent: 'A list containing 25012 items',
    },
    {
      tabHeading: 'Tab 2',
      tabContent: 'A list containing 280 items',
    },
    {
      tabHeading: 'Tab 3',
      tabContent: "This tab doesn't have a list of items",
    },
  ];
}

```

**Template:**

```html
<sky-tabset ariaLabel="Tab demonstration" data-sky-id="tab-demo">
  @for (tab of tabArray; track tab) {
    <sky-tab [tabHeading]="tab.tabHeading">
      {{ tab.tabContent }}
    </sky-tab>
  }
</sky-tabset>

```

#### Tabs with add and close buttons

**Selector:** `app-tabs-static-add-close-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs with add and close buttons
 */
@Component({
  selector: 'app-tabs-static-add-close-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsStaticAddCloseExampleComponent {
  protected showTab3 = true;

  public onNewTabClick(): void {
    alert('Add tab clicked!');
  }
}

```

**Template:**

```html
<sky-tabset
  data-sky-id="tab-demo"
  ariaLabel="Tab demonstration"
  (newTab)="onNewTabClick()"
>
  <sky-tab [tabHeading]="'Tab 1'"> Content for Tab 1 </sky-tab>
  <sky-tab [tabHeading]="'Tab 2'"> Content for Tab 2 </sky-tab>
  @if (showTab3) {
    <sky-tab [tabHeading]="'Tab 3'" (close)="showTab3 = false">
      Content for Tab 3
    </sky-tab>
  }
</sky-tabset>

```

#### Tabs with basic setup

**Selector:** `app-tabs-static-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs with basic setup
 */
@Component({
  selector: 'app-tabs-static-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsStaticExampleComponent {}

```

**Template:**

```html
<sky-tabset ariaLabel="Tab demonstration" data-sky-id="tab-demo">
  <sky-tab [tabHeading]="'Tab 1'"> Content for Tab 1 </sky-tab>
  <sky-tab [tabHeading]="'Tab 2'"> Content for Tab 2 </sky-tab>
  <sky-tab [tabHeading]="'Tab 3'"> Content for Tab 3 </sky-tab>
</sky-tabset>

```

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

#### Wizard in a modal

**Selector:** `app-tabs-wizard-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard in a modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-wizard-basic-example',
  templateUrl: './example.component.html',
})
export class TabsWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  #modalSize = 'large';

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent, { size: this.#modalSize });
  }
}

```

**Template:**

```html
<button type="button" class="sky-btn sky-btn-default" (click)="openWizard()">
  Open Wizard
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
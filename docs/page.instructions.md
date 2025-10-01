---
component: 'page'
description: 'Design guidelines, API documentation, and usage instructions for the page component extracted from SKY UX documentation.'
---

# Page Component Guidelines

## Component Overview
Pages provide consistent, responsive containers for common page layouts. This component replaces a deprecated version. For update instructions, see the deprecated page component.

## Usage

### ✅ Use when

Use pages to apply consistent background colors and standardized layouts to all pages.

### ❌ Don't use when

Don't use pages in modals.

## Anatomy

### Standard heading without page links

### Hub and spoke heading with page links

- Header
- Heading
- Content area
- Alert
- Avatar
- Details
- Actions

## Options

### Layouts

#### Blocks

For record pages, use the blocks layout to organize content into modular blocks. For a wide range of possible layouts, place a fluid grid or another grid layout via flexbox or CSS grid in the content area.

#### List

For list pages, use the list layout to display lists of data.

#### Tabs

For record pages or list pages, use the tabs layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see tabs.

#### Fit

For split view pages, use the fit layout to fill the content area and anchor content to the edges.

#### None

For custom content that doesn't work well with predefined layouts or spacing, use the none layout.

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

#### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

**Page headings descibe the content on pages.**

#### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

**Hub and spoke navigation connects child pages to a single parent hub page.**

**The hub and spoke pattern connects a parent hub page to child spoke pages. Users navigate to spokes from the hub.**

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

**❌ Don't go more than one level deep in hub and spoke headings.**

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use tabs to group large amounts of content within a page.

**❌ Don't use the hub and spoke pattern to connect a record page to its child pages.**

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an alert in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) avatar in the top left of record pages.

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the record page guidelines.

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the record page guidelines.

### Page links

#### Link lists

For blocks layout pages, you can add link lists for navigation in a way that is similar to action hubs. Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's Content guidelines.

#### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

**Page links provide navigation to other pages or tasks from a page.**

#### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness behaviors below.

**Page link lists are positioned to the right of the page content.**

## Behaviors and states

### Responsiveness

Page layouts reflow content at the xs breakpoint of 767px.

## Related information

### Guidelines

- Action hub
- Buttons and links
- List page
- Record page
- Split view page

### Components

- Alert
- Avatar
- Buttons
- Fluid grid
- Split view
- Tabs

## API Documentation

### Components and Directives

#### IndicatorsWaitPageExampleComponent

**Selector:** `app-indicators-wait-page-example`

**Package:** `@skyux/code-examples`

#### LayoutPageSummaryBasicExampleComponent

**Selector:** `app-layout-page-summary-basic-example`

**Package:** `@skyux/code-examples`

#### PagesActionHubExampleComponent

**Selector:** `app-pages-action-hub-example`

**Package:** `@skyux/code-examples`

#### PagesPageHomePageBlocksLayoutExampleComponent

**Selector:** `app-pages-page-home-page-blocks-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageListPageListLayoutExampleComponent

**Selector:** `app-pages-page-list-page-list-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageRecordPageBlocksLayoutExampleComponent

**Selector:** `app-pages-page-record-page-blocks-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageRecordPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageSplitViewPageFitLayoutExampleComponent

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**Package:** `@skyux/code-examples`

#### SplitViewPageBoundExampleComponent

**Selector:** `app-split-view-page-bound-example`

**Package:** `@skyux/code-examples`

#### ListPagingSetItemsPerPageAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetMaxPagesAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetPageNumberAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyDocsTableOfContentsPageComponent

**Selector:** `sky-docs-toc-page`

**Package:** `@skyux/docs-tools`

**Inputs:**

- `menuHeadingText`: `InputSignal<string>`

#### SkyPageSummaryAlertComponent

Displays messages that require immediate attention as [alerts](https://developer.blackbaud.com/skyux/components/alert) within
the page summary.

**Selector:** `sky-page-summary-alert`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryContentComponent

Displays content in the arbitrary section of the page summary.

**Selector:** `sky-page-summary-content`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryImageComponent

Displays an image in the page summary to identify a record
or help users complete a core task.

**Selector:** `sky-page-summary-image`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryKeyInfoComponent

Highlights important information about a page in the key information section of the
page summary.

**Selector:** `sky-page-summary-key-info`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryStatusComponent

Displays [labels](https://developer.blackbaud.com/skyux/components/label)
to highlight important status information about a page's content.

**Selector:** `sky-page-summary-status`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummarySubtitleComponent

Specifies a subtitle to identify the page content.

**Selector:** `sky-page-summary-subtitle`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryTitleComponent

Specifies a title to identify the page content.

**Selector:** `sky-page-summary-title`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryComponent

Specifies the components to display in the page summary.

**Selector:** `sky-page-summary`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryModule

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryFixture

Allows interaction with a SKY UX page summary component.

**Package:** `@skyux/layout/testing`

⚠️ **This component is deprecated.**

#### SkyPageLink

Displays links to related information or recently accessed items.

**Package:** `@skyux/pages`

#### SkyPageLinksInput

**Package:** `@skyux/pages`

#### SkyPageModalLink

Displays links to related information or recently accessed items.

**Package:** `@skyux/pages`

#### SkyPageModalLinksInput

**Package:** `@skyux/pages`

#### SkyPageHeaderActionsComponent

Displays buttons within the page header for page actions and applies spacing between buttons.
Appears below the page header details.

**Selector:** `sky-page-header-actions`

**Package:** `@skyux/pages`

#### SkyPageHeaderAlertsComponent

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

**Selector:** `sky-page-header-alerts`

**Package:** `@skyux/pages`

#### SkyPageHeaderAvatarComponent

Displays an avatar within the page header to the left of the page title.
If no size is specified for the avatar component it will display at size
small on xs breakpoints and size large on small and above breakpoints.

**Selector:** `sky-page-header-avatar`

**Package:** `@skyux/pages`

#### SkyPageHeaderDetailsComponent

Displays additional information in the page header, like record details.
Appears below the title and above the page actions.

**Selector:** `sky-page-header-details`

**Package:** `@skyux/pages`

#### SkyPageHeaderComponent

Displays page heading's contents using spacing that corresponds to the parent page's layout

**Selector:** `sky-page-header`

**Package:** `@skyux/pages`

**Inputs:**

- `pageTitle`: `string | undefined` - The title of the current page.
- `parentLink`: `SkyPageLink | undefined` - A link to the parent page of the current page.

#### SkyPageHeaderModule

**Package:** `@skyux/pages`

#### SkyPageContentComponent

Displays page contents using spacing that corresponds to the parent
page's layout.

**Selector:** `sky-page-content`

**Package:** `@skyux/pages`

#### SkyPageLinksComponent

Displays page links on the right side of the page, or below the page content
on mobile devices.

**Selector:** `sky-page-links`

**Package:** `@skyux/pages`

#### SkyPageComponent

Displays a page using the specified layout. The page component is a responsive container,
meaning content will respect the breakpoints within the page element instead of the window.
This is helpful if there is other content to the left or right of the page.

**Selector:** `sky-page`

**Package:** `@skyux/pages`

**Inputs:**

- `layout`: `InputSignal<SkyPageLayoutType>` - The page layout that applies spacing to the page header and content. Use the layout
that corresponds with the top-level component type used on the page, or use `fit` to
constrain the page contents to the available viewport.
Use `none` for custom content that does not adhere to predefined spacing or constraints. (default: "none")
- `helpKey`: `string | undefined` - A help key that identifies the page's default [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help) content to display.

#### SkyPageModule

**Package:** `@skyux/pages`

#### SkyPageLayoutType

**Package:** `@skyux/pages`

#### SkyPageHeaderHarnessFilters

A set of criteria that can be used to filter a list of SkyPageHeaderHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyPageHeaderHarness

Harness for interacting with a page header component in tests.

**Package:** `@skyux/pages/testing`

#### SkyPageHarnessFilters

A set of criteria that can be used to filter a list of SkyPageHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyPageHarness

Harness for interacting with a page component in tests.

**Package:** `@skyux/pages/testing`

### Code Examples

#### Embed error within the page markup

**Selector:** `app-errors-error-embedded-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyErrorModule } from '@skyux/errors';

/**
 * @title Embed error within the page markup
 */
@Component({
  selector: 'app-errors-error-embedded-example',
  templateUrl: './example.component.html',
  imports: [SkyErrorModule],
})
export class ErrorsErrorEmbeddedExampleComponent {
  protected customAction(): void {
    alert('action clicked!');
  }
}

```

**Template:**

```html
<sky-error errorType="broken">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Try again
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="notfound">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="construction">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="security">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error>
  <sky-error-image>
    <img
      alt=""
      role="presentation"
      src="data:image/png;base64,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"
    />
  </sky-error-image>
  <sky-error-title> Custom error with a custom image. </sky-error-title>
  <sky-error-description> Custom description. </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="broken">
  <sky-error-title [replaceDefaultTitle]="true">
    Custom error with a default image.
  </sky-error-title>
  <sky-error-description [replaceDefaultDescription]="true">
    Custom description.
  </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

```

#### Wait applied to a page

**Selector:** `app-indicators-wait-page-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';

/**
 * @title Wait applied to a page
 */
@Component({
  standalone: true,
  selector: 'app-indicators-wait-page-example',
  templateUrl: './example.component.html',
})
export class IndicatorsWaitPageExampleComponent implements OnDestroy {
  protected isWaiting = false;

  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#waitSvc.dispose();
  }

  protected togglePageWait(isBlocking: boolean): void {
    if (!this.isWaiting) {
      if (isBlocking) {
        this.#waitSvc.beginBlockingPageWait();
      } else {
        this.#waitSvc.beginNonBlockingPageWait();
      }
    } else if (isBlocking) {
      this.#waitSvc.endBlockingPageWait();
    } else {
      this.#waitSvc.endNonBlockingPageWait();
    }

    this.isWaiting = !this.isWaiting;
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(true)"
>
  Show page wait
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(false)"
>
  Show non-blocking page wait
</button>

```

#### Page summary with basic setup

**Selector:** `app-layout-page-summary-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyCheckboxModule } from '@skyux/forms';
import {
  SkyAlertModule,
  SkyKeyInfoModule,
  SkyLabelModule,
} from '@skyux/indicators';
import { SkyPageSummaryModule } from '@skyux/layout';

/**
 * @title Page summary with basic setup
 */
@Component({
  selector: 'app-layout-page-summary-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyAlertModule,
    SkyAvatarModule,
    SkyCheckboxModule,
    SkyKeyInfoModule,
    SkyLabelModule,
    SkyPageSummaryModule,
  ],
})
export class LayoutPageSummaryBasicExampleComponent {
  protected name = 'Robert C. Hernandez';
  protected showAlert = true;
  protected showContent = true;
  protected showImage = true;
  protected showKeyInfo = true;
  protected showStatus = true;
  protected showSubtitle = true;
  protected showTitle = true;
}

```

**Template:**

```html
<sky-page-summary>
  @if (showAlert) {
    <sky-page-summary-alert>
      <sky-alert alertType="info"> This is an alert. </sky-alert>
    </sky-page-summary-alert>
  }
  @if (showImage) {
    <sky-page-summary-image>
      <sky-avatar [name]="name" [canChange]="true" />
    </sky-page-summary-image>
  }
  @if (showTitle) {
    <sky-page-summary-title>
      {{ name }}
    </sky-page-summary-title>
  }
  @if (showSubtitle) {
    <sky-page-summary-subtitle> Board member </sky-page-summary-subtitle>
  }
  @if (showStatus) {
    <sky-page-summary-status>
      <sky-label labelType="success"> Fundraiser </sky-label>
      <sky-label> Inactive </sky-label>
    </sky-page-summary-status>
  }
  @if (showContent) {
    <sky-page-summary-content>
      This is the arbitrary content section. You can display any kind of content
      to complement the content on a page. We recommend that you display content
      to support the key tasks of users of users who visit the page. We also
      recommend that you keep in mind the context of how users will use the
      content and limit the amount of content to avoid overloading the summary.
    </sky-page-summary-content>
  }
  @if (showKeyInfo) {
    <sky-page-summary-key-info>
      <sky-key-info>
        <sky-key-info-value> $1,500 </sky-key-info-value>
        <sky-key-info-label> Largest gift </sky-key-info-label>
      </sky-key-info>
      <sky-key-info>
        <sky-key-info-value> 37 </sky-key-info-value>
        <sky-key-info-label> Total gifts </sky-key-info-label>
      </sky-key-info>
    </sky-page-summary-key-info>
  }
</sky-page-summary>

<ul class="sky-list-unstyled">
  <li>
    <sky-checkbox labelText="Show title" [(ngModel)]="showTitle" />
  </li>
  <li>
    <sky-checkbox labelText="Show subtitle" [(ngModel)]="showSubtitle" />
  </li>
  <li>
    <sky-checkbox labelText="Show image" [(ngModel)]="showImage" />
  </li>
  <li>
    <sky-checkbox labelText="Show record status" [(ngModel)]="showStatus" />
  </li>
  <li>
    <sky-checkbox labelText="Show key information" [(ngModel)]="showKeyInfo" />
  </li>
  <li>
    <sky-checkbox
      labelText="Show arbitrary content"
      [(ngModel)]="showContent"
    />
  </li>
  <li>
    <sky-checkbox labelText="Show alert" [(ngModel)]="showAlert" />
  </li>
</ul>

```

#### Action hub with basic setup

**Selector:** `app-pages-action-hub-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyActionHubModule, SkyPageModalLinksInput } from '@skyux/pages';

import { MODAL_TITLE } from './modal-title-token';
import { SettingsModalComponent } from './settings-modal.component';

const pastHours = Array.from(Array(5).keys()).map((i) => {
  const date = new Date();
  date.setHours(date.getHours() - (i + 1));
  return date;
});

/**
 * @title Action hub with basic setup
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-action-hub-example',
  templateUrl: './example.component.html',
  imports: [SkyActionHubModule],
})
export class PagesActionHubExampleComponent {
  public buttons = [
    {
      label: 'Action 1',
      ariaLabel: 'Accounts action 1',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Action 2',
      ariaLabel: 'Accounts action 2',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Action 3',
      ariaLabel: 'Accounts action 3',
      permalink: {
        url: '#',
      },
    },
  ];

  public needsAttention = [
    {
      title: '9',
      message: 'updates from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '8',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '7',
      message: 'possible duplicates from constituent lists',
      permalink: {
        url: '#',
      },
    },
    {
      title: '6',
      message: 'updates from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '5',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '4',
      message: 'possible duplicates from constituent lists',
      permalink: {
        url: '#',
      },
    },
    {
      title: '3',
      message: 'update from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '2',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '1',
      message: 'possible duplicate from constituent lists',
      permalink: {
        url: '#',
      },
    },
  ];

  public recentLinks = [
    {
      label: 'Recent 1',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[0],
    },
    {
      label: 'Recent 2',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[1],
    },
    {
      label: 'Recent 3',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[2],
    },
    {
      label: 'Recent 4',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[3],
    },
    {
      label: 'Recent 5',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[4],
    },
  ];

  public relatedLinks = [
    {
      label: 'Link 1',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Link 2',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Link 3',
      permalink: {
        url: '#',
      },
    },
  ];

  public settingsLinks: SkyPageModalLinksInput = [
    {
      label: 'Number',
      modal: {
        component: SettingsModalComponent,
        config: {
          size: 'large',
          providers: [
            {
              provide: MODAL_TITLE,
              useValue: 'Number',
            },
          ],
        },
      },
    },
    {
      label: 'Color',
      modal: {
        component: SettingsModalComponent,
        config: {
          size: 'large',
          providers: [
            {
              provide: MODAL_TITLE,
              useValue: 'Color',
            },
          ],
        },
      },
    },
  ];

  public title = 'Active accounts';
}

```

**Template:**

```html
<sky-action-hub
  data-sky-id="action-hub"
  [needsAttention]="needsAttention"
  [recentLinks]="recentLinks"
  [relatedLinks]="relatedLinks"
  [settingsLinks]="settingsLinks"
  [title]="title"
>
  <sky-action-hub-buttons>
    @for (button of buttons; track button) {
      <a
        class="sky-btn sky-btn-default sky-margin-inline-sm"
        [attr.aria-label]="button.ariaLabel"
        [href]="button.permalink.url"
      >
        {{ button.label }}
      </a>
    }
  </sky-action-hub-buttons>

  <sky-action-hub-content>
    <h2 class="sky-font-heading-2">Additional content</h2>
    <p>More content can go here as needed for the functional area.</p>
  </sky-action-hub-content>
</sky-action-hub>

```

#### Home page with blocks layout, using tile dashboard and recently accessed links

**Selector:** `app-pages-page-home-page-blocks-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyPageModule, SkyRecentLink } from '@skyux/pages';

import { HomePageContentComponent } from './home-page-content.component';

/**
 * @title Home page with blocks layout, using tile dashboard and recently accessed links
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-home-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [HomePageContentComponent, SkyIconModule, SkyPageModule],
})
export class PagesPageHomePageBlocksLayoutExampleComponent {
  protected readonly recentLinks: SkyRecentLink[] = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

**Template:**

```html
<sky-page layout="blocks">
  <sky-page-header pageTitle="Home">
    <sky-page-header-actions>
      <button type="button" class="sky-btn sky-btn-default">
        <sky-icon iconName="add" /> New
      </button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-home-page-content />
  </sky-page-content>

  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Resources">
      <sky-link-list-item>
        <a href="#">Help</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Support</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Training</a>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

```

#### List page with list layout using data manager

**Selector:** `app-pages-page-list-page-list-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with list layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-list-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageListLayoutExampleComponent {}

```

**Template:**

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + dashboardName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + dashboardName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Copy ' + dashboardName">
        Copy
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + dashboardName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

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

#### Record page with blocks layout using box components

**Selector:** `app-pages-page-record-page-blocks-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with blocks layout using box components
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [RecordPageContentComponent, SkyPageModule],
})
export class PagesPageRecordPageBlocksLayoutExampleComponent {
  protected readonly recentLinks = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

**Template:**

```html
<sky-page layout="blocks" helpKey="example-help">
  <sky-page-header
    pageTitle="$500 pledge"
    [parentLink]="{
      label: 'Pledges',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  />
  <sky-page-content>
    <app-record-page-content />
  </sky-page-content>
  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Related links">
      <sky-link-list-item>
        <a href="#">Analysis</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Tools</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <button type="button" class="sky-btn-link-inline">Settings</button>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

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

#### Split view page with fit layout

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyAlertModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { SplitViewPageContentComponent } from './split-view-page-content.component';

/**
 * @title Split view page with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-split-view-page-fit-layout-example',
  templateUrl: './example.component.html',
  imports: [SkyAlertModule, SkyPageModule, SplitViewPageContentComponent],
})
export class PagesPageSplitViewPageFitLayoutExampleComponent {}

```

**Template:**

```html
<sky-page layout="fit" helpKey="example-help">
  <sky-page-header
    pageTitle="Expenses to approve"
    [parentLink]="{
      label: 'Expenses',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  >
    <sky-page-header-alerts>
      <sky-alert alertType="warning" descriptionType="warning">
        There are multiple expense approvals due soon.
      </sky-alert>
    </sky-page-header-alerts>
    <sky-page-header-actions>
      <button class="sky-btn sky-btn-default" type="button">Approve all</button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-split-view-page-content />
  </sky-page-content>
</sky-page>

```

#### Page bound split view in a page component with fit layout

**Selector:** `app-split-view-page-bound-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyAlertModule } from '@skyux/indicators';
import { SkyDescriptionListModule, SkyPageSummaryModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import { SkyPageModule } from '@skyux/pages';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

import { Record } from './record';

interface DemoForm {
  approvedAmount: FormControl<number>;
  comments: FormControl<string>;
}

/**
 * @title Page bound split view in a page component with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-split-view-page-bound-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyAlertModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyPageModule,
    SkyPageSummaryModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewPageBoundExampleComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items: Record[] = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
    {
      id: 5,
      amount: 456.24,
      date: '5/16/2020',
      vendor: 'Wish',
      receiptImage: 'wish-delivery-order.png',
      approvedAmount: 456.24,
      comments: '',
    },
    {
      id: 6,
      amount: 62.37,
      date: '5/16/2020',
      vendor: 'Staples',
      receiptImage: 'staples-paper-bulk-order.png',
      approvedAmount: 62.37,
      comments: '',
    },
    {
      id: 7,
      amount: 51.84,
      date: '5/17/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-17-19.png',
      approvedAmount: 51.84,
      comments: '',
    },
    {
      id: 8,
      amount: 92.55,
      date: '5/18/2020',
      vendor: 'Home Depot',
      receiptImage: 'home-depot-order.png',
      approvedAmount: 0.0,
      comments: '',
    },
    {
      id: 9,
      amount: 38.29,
      date: '5/18/2020',
      vendor: 'Papa Johns',
      receiptImage: 'papa-johns-order.png',
      approvedAmount: 38.29,
      comments: '',
    },
  ];

  protected activeRecord: Record;
  protected splitViewDemoForm: FormGroup<DemoForm>;
  protected splitViewStream = new Subject<SkySplitViewMessage>();
  protected unapprovedTransaction = true;

  #_activeIndex = 0;

  readonly #confirmSvc = inject(SkyConfirmService);

  constructor() {
    // Start with the first item selected.
    this.activeIndex = 0;
    this.activeRecord = this.items[this.activeIndex];

    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(this.activeRecord.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(this.activeRecord.comments, {
        nonNullable: true,
      }),
    });
  }

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: Record): void {
    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(record.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(record.comments, { nonNullable: true }),
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action.toLowerCase() === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord.approvedAmount = parseFloat(
      `${this.splitViewDemoForm.value.approvedAmount ?? 0}`,
    );

    this.activeRecord.comments = this.splitViewDemoForm.value.comments ?? '';

    this.unapprovedTransaction =
      this.items.findIndex((item) => item.amount !== item.approvedAmount) >= 0;

    this.splitViewDemoForm.reset(this.splitViewDemoForm.value);
  }

  #setFocusInWorkspace(): void {
    const message: SkySplitViewMessage = {
      type: SkySplitViewMessageType.FocusWorkspace,
    };

    this.splitViewStream.next(message);
  }
}

```

**Template:**

```html
<sky-page layout="fit">
  <div class="page-flex">
    <div class="page-flex-header">
      <sky-page-summary>
        @if (unapprovedTransaction) {
          <sky-page-summary-alert>
            <sky-alert alertType="info"
              >There is an unapproved transaction.</sky-alert
            >
          </sky-page-summary-alert>
        }
        <sky-page-summary-title> SKY Developers, LLC </sky-page-summary-title>
        <sky-page-summary-subtitle>
          Petty Cash Transactions
        </sky-page-summary-subtitle>
        <sky-page-summary-content>
          The transactions below cover various operating expenses which do not
          fall under one of the budgets areas of expenditures.
        </sky-page-summary-content>
      </sky-page-summary>
    </div>
    <div class="page-flex-main">
      <sky-split-view dock="fill" [messageStream]="splitViewStream">
        <sky-split-view-drawer [ariaLabel]="'Transaction list'">
          <sky-repeater [activeIndex]="activeIndex">
            @for (item of items; track item; let i = $index) {
              <sky-repeater-item
                (click)="onItemClick(i)"
                (keyup.enter)="onItemClick(i)"
              >
                <sky-repeater-item-content>
                  {{ item.amount }} <br />
                  {{ item.date }} <br />
                  {{ item.vendor }}
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-split-view-drawer>

        <sky-split-view-workspace [ariaLabel]="'Transaction form'">
          <sky-split-view-workspace-content class="sky-padding-even-xl">
            <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
              <sky-description-list labelWidth="150px">
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt amount
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.amount }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term> Date </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.date }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Vendor
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.vendor }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt image
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.receiptImage }}
                  </sky-description-list-description>
                </sky-description-list-content>
              </sky-description-list>
              <sky-input-box labelText="Approved amount" stacked="true">
                <input formControlName="approvedAmount" type="text" />
              </sky-input-box>
              <sky-input-box labelText="Comments">
                <textarea formControlName="comments"></textarea>
              </sky-input-box>
            </form>
          </sky-split-view-workspace-content>
          <sky-split-view-workspace-footer>
            <sky-summary-action-bar>
              <sky-summary-action-bar-actions>
                <sky-summary-action-bar-primary-action
                  (actionClick)="onApprove()"
                >
                  Approve expense
                </sky-summary-action-bar-primary-action>
                <sky-summary-action-bar-secondary-actions>
                  <sky-summary-action-bar-secondary-action
                    (actionClick)="onDeny()"
                  >
                    Deny expense
                  </sky-summary-action-bar-secondary-action>
                </sky-summary-action-bar-secondary-actions>
              </sky-summary-action-bar-actions>
            </sky-summary-action-bar>
          </sky-split-view-workspace-footer>
        </sky-split-view-workspace>
      </sky-split-view>
    </div>
  </div>
</sky-page>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
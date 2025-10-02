---
component: 'page'
type: 'api-documentation'
description: 'API documentation for the page component including components, interfaces, and types.'
---

# Page API Documentation

## Components and Directives

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

#### SkyPageSummaryContentComponent

Displays content in the arbitrary section of the page summary.

**Selector:** `sky-page-summary-content`

**Package:** `@skyux/layout`

#### SkyPageSummaryImageComponent

Displays an image in the page summary to identify a record
or help users complete a core task.

**Selector:** `sky-page-summary-image`

**Package:** `@skyux/layout`

#### SkyPageSummaryKeyInfoComponent

Highlights important information about a page in the key information section of the
page summary.

**Selector:** `sky-page-summary-key-info`

**Package:** `@skyux/layout`

#### SkyPageSummaryStatusComponent

Displays [labels](https://developer.blackbaud.com/skyux/components/label)
to highlight important status information about a page's content.

**Selector:** `sky-page-summary-status`

**Package:** `@skyux/layout`

#### SkyPageSummarySubtitleComponent

Specifies a subtitle to identify the page content.

**Selector:** `sky-page-summary-subtitle`

**Package:** `@skyux/layout`

#### SkyPageSummaryTitleComponent

Specifies a title to identify the page content.

**Selector:** `sky-page-summary-title`

**Package:** `@skyux/layout`

#### SkyPageSummaryComponent

Specifies the components to display in the page summary.

**Selector:** `sky-page-summary`

**Package:** `@skyux/layout`

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
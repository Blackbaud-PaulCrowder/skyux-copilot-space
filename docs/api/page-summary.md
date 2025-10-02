---
component: 'page-summary'
type: 'api-documentation'
description: 'API documentation for the page-summary component including components, interfaces, and types.'
---

# Page Summary API Documentation

## Components and Directives

#### LayoutPageSummaryBasicExampleComponent

**Selector:** `app-layout-page-summary-basic-example`

**Package:** `@skyux/code-examples`

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
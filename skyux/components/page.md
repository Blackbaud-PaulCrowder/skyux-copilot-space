# Design

                  Skip to Main Content

 Page
====

Pages provide consistent, responsive containers for common page layouts.

 Usage
------

### Use when

Use pages to apply consistent background colors and standardized layouts to all pages.

### Don't use when

Don't use pages in modals.

 Anatomy
--------

### Standard heading without page links

1

Header

2

Heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

[Avatar](/skyux/components/avatar.md) (optional)

6

Details (optional)

7

Actions (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-heading.0f513db7d271182cea483e6ecae854ca.png)

### Hub and spoke heading with page links

1

Header

2

Hub and spoke heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

Details (optional)

6

Actions (optional)

7

Page links area (optional)

8

Recently accessed link list (optional)

9

Page link list (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-hub.f9e8a05879794ae622f087a03d19b4cd.png)

 Options
--------

### Layouts

#### Blocks

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md), use the `blocks` layout to organize content into modular blocks. For a wide range of possible layouts, place a [fluid grid](/skyux/components/fluid-grid.md) or another grid layout via flexbox or CSS grid in the content area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-blocks-layout.76f82ea0c799d06acf73237b9266995e.png)

#### List

For [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `list` layout to display lists of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-list-layout.6a565c1ad637e53a00eea686b207b8a7.png)

#### Tabs

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md) or [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `tabs` layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see [tabs](/skyux/components/tabs.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-tabs-layout.cd00761effd67b07f9163f9dca6c9c52.png)

#### Fit

For [split view pages](/skyux/design/guidelines/page-layouts/split-view-page.md), use the `fit` layout to fill the content area and anchor content to the edges.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-fit-layout.2deadebc41c1f7f0e8e8cc83f1aed4d0.png)

#### None

For custom content that doesn't work well with predefined layouts or spacing, use the `none` layout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-none-layout.4a100252343c541041581837fd7b9eb4.png)

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

#### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-heading.62580a83a844948a6b1e8e75d4f4b406.png)

Page headings descibe the content on pages.

#### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke.f706d1d121110c699ad87ab958a8d51c.png)

Hub and spoke navigation connects child pages to a single parent hub page.

Hub

Hubs are parent pages with links to child pages that users can only navigate to from the hub. None found.

Spoke

Spokes are child pages that users only navigate to from a hub. Don't use hub and spoke heading when users can navigate to a child page from multiple places. None found.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke-diagram.4929796f70eeb8a3415c59e2ee377a42.png)

The hub and spoke pattern connects a parent hub page to child spoke pages. Users navigate to spokes from the hub.

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-breadcrumb-dont.458dc4831b8a02f26ad2b6fe293bede6.png)

Don't go more than one level deep in hub and spoke headings.

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use [tabs](/skyux/components/tabs.md) to group large amounts of content within a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-record-dont.ce87f18a349fc58e9cf133cb03d4ff82.png)

Don't use the hub and spoke pattern to connect a record page to its child pages.

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an [alert](/skyux/components/alert.md) in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) [avatar](/skyux/components/avatar.md) in the top left of [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Page links

#### Link lists

For `blocks` layout pages, you can add link lists for navigation in a way that is similar to [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md). Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's [Content guidelines](/skyux/design/guidelines/page-layouts/action-hub#section-content.md).

#### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-links-home.072443de8a2e9e96b37fdd3706ada2d0.png)

Page links provide navigation to other pages or tasks from a page.

#### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness [behaviors](/skyux/components/page#section-behaviors-and-states.md) below.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-page-links-layout.b22d6d87b0ba15518d15682fc93e2167.png)

Page link lists are positioned to the right of the page content.

 Behaviors and states
---------------------

### Responsiveness

Page layouts reflow content at the `xs` breakpoint of 767px.

![Blocks layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-blocks.bc588a127d94b27ec442496fcf02f456.png)

![List layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-list.d11e67ec7ac52ea211ee882b5acd0c28.png)

![Tabs layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-tabs.a05d5c647e4c54d3e35ab4aead6e840d.png)

![Fit layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-fit.ed1a9f74d40c7a3d68321a70f62fef52.png)

 Related information
--------------------

### Guidelines

*   [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)
*   [Buttons and links](/skyux/design/guidelines/buttons-links.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

### Components

*   [Alert](/skyux/components/alert.md)
*   [Avatar](/skyux/components/avatar.md)
*   [Buttons](/skyux/components/button.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

 Installation
-------------

NPM package

`@skyux/pages`[View in NPM](https://www.npmjs.com/package/@skyux/pages) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/pages/src/lib/modules/page/page.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/pages`Copy None found.

 SkyPageModule
--------------

Type: Module

`import { SkyPageModule } from '@skyux/pages';`

 SkyPageComponent
-----------------

Type: Component

Selector: `sky-page`

Displays a page using the specified layout. The page component is a responsive container, meaning content will respect the breakpoints within the page element instead of the window. This is helpful if there is other content to the left or right of the page.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the page's default [global help](/skyux/learn/develop/global-help.md) content to display.

#### `layout: InputSignal<SkyPageLayoutType>`

The page layout that applies spacing to the page header and content. Use the layout that corresponds with the top-level component type used on the page, or use `fit` to constrain the page contents to the available viewport. Use `none` for custom content that does not adhere to predefined spacing or constraints.

Default: `"none"`

 SkyPageContentComponent
------------------------

Type: Component

Selector: `sky-page-content`

Displays page contents using spacing that corresponds to the parent page's layout.

 SkyPageLinksComponent
----------------------

Type: Component

Selector: `sky-page-links`

Displays page links on the right side of the page, or below the page content on mobile devices.

 SkyPageLayoutType
------------------

Type: Type alias

    type SkyPageLayoutType = "none" | "fit" | "blocks" | "list" | "tabs"

 SkyPageHeaderModule
--------------------

Type: Module

`import { SkyPageHeaderModule } from '@skyux/pages';`

 SkyPageHeaderComponent
-----------------------

Type: Component

Selector: `sky-page-header`

Displays page heading's contents using spacing that corresponds to the parent page's layout

### Inputs

#### `pageTitle: string | undefined`

The title of the current page.

#### `parentLink: SkyPageLink | undefined`

A link to the parent page of the current page.

 SkyPageHeaderDetailsComponent
------------------------------

Type: Component

Selector: `sky-page-header-details`

Displays additional information in the page header, like record details. Appears below the title and above the page actions.

 SkyPageHeaderActionsComponent
------------------------------

Type: Component

Selector: `sky-page-header-actions`

Displays buttons within the page header for page actions and applies spacing between buttons. Appears below the page header details.

 SkyPageHeaderAlertsComponent
-----------------------------

Type: Component

Selector: `sky-page-header-alerts`

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

 SkyPageHeaderAvatarComponent
-----------------------------

Type: Component

Selector: `sky-page-header-avatar`

Displays an avatar within the page header to the left of the page title. If no size is specified for the avatar component it will display at size small on xs breakpoints and size large on small and above breakpoints.

 SkyPageLink
------------

Type: Interface

Displays links to related information or recently accessed items.

    interface SkyPageLink {
      label: string;
      permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string };
    }

### Properties

#### `label: string`

The link text.

#### `permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string }`

The link destination.

 SkyPageLinksInput
------------------

Type: Type alias

    type SkyPageLinksInput = SkyPageLink[] | "loading" | undefined

 SkyLinkListModule
------------------

Type: Module

`import { SkyLinkListModule } from '@skyux/pages';`

 SkyLinkListComponent
---------------------

Type: Component

Selector: `sky-link-list`

A component that displays a list of links, such as within a `<sky-page-links>` component.

### Inputs

#### `headingText: InputSignal<undefined | string>`

The text to display as the list's heading.

#### `links: InputSignal<SkyPageLinksInput>`

Option to pass links as an array of `SkyPageLink` objects or `'loading'` to display a loading indicator.

 SkyLinkListItemComponent
-------------------------

Type: Component

Selector: `sky-link-list-item`

A wrapper for each link in a link list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPageHarness
---------------

Type: Class

`import { SkyPageHarness } from '@skyux/pages/testing';`

Harness for interacting with a page component in tests.

### Methods

#### `getLayout(): Promise<SkyPageLayoutType>`

Gets the current layout.

#### Returns

`Promise<SkyPageLayoutType>`

#### `getPageHeader(filters?: SkyPageHeaderHarnessFilters): Promise<SkyPageHeaderHarness>`

Gets the first page header that matches the given filters.

#### Parameters

##### `filters?: SkyPageHeaderHarnessFilters`

filters for which page header to return

#### Returns

`Promise<SkyPageHeaderHarness>`

#### `SkyPageHarness.with(filters: SkyPageHarnessFilters): HarnessPredicate<SkyPageHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHarness>`

 SkyPageHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHarness](/skyux/components/page?docs-active-tab=design#class_sky-page-harness.md) instances.

    interface SkyPageHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPageHeaderHarness
---------------------

Type: Class

`import { SkyPageHeaderHarness } from '@skyux/pages/testing';`

Harness for interacting with a page header component in tests.

### Methods

#### `getPageTitle(): Promise<undefined | string>`

Gets the current page title.

#### Returns

`Promise<undefined | string>`

#### `getParentLinkText(): Promise<string>`

Gets the current page title.

#### Returns

`Promise<string>`

#### `SkyPageHeaderHarness.with(filters: SkyPageHeaderHarnessFilters): HarnessPredicate<SkyPageHeaderHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHeaderHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHeaderHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHeaderHarness>`

 SkyPageHeaderHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHeaderHarness](/skyux/components/page?docs-active-tab=design#class_sky-page-header-harness.md) instances.

    interface SkyPageHeaderHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListHarness
-------------------

Type: Class

`import { SkyLinkListHarness } from '@skyux/pages/testing';`

Harness for interacting with a link list component in tests.

### Methods

#### `getHeadingText(): Promise<undefined | string>`

Gets the link list's heading text. If there are no links, this will return `undefined`.

#### Returns

`Promise<undefined | string>`

#### `getListItem(filter: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness>`

Gets a specific link list item based on the filter criteria.

#### Parameters

##### `filter: SkyLinkListItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness>`

#### `getListItems(filter?: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness[]>`

Gets an array of link list items based on the filter criteria. If no filter is provided, returns all link list items.

#### Parameters

##### `filter?: SkyLinkListItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness[]>`

#### `isVisible(): Promise<boolean>`

Whether the link list is showing a list of links.

#### Returns

`Promise<boolean>`

#### `isWaiting(): Promise<boolean>`

Gets the status of the wait indicator.

#### Returns

`Promise<boolean>`

#### `SkyLinkListHarness.with(filters: SkyLinkListHarnessFilters): HarnessPredicate<SkyLinkListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListHarness>`

 SkyLinkListHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListHarness](/skyux/components/page?docs-active-tab=design#class_sky-link-list-harness.md) instances.

    interface SkyLinkListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListItemHarness
-----------------------

Type: Class

`import { SkyLinkListItemHarness } from '@skyux/pages/testing';`

Harness for interacting with a linked list item in tests.

### Methods

#### `click(): Promise<void>`

Clicks the item.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the text content of the item.

#### Returns

`Promise<string>`

#### `SkyLinkListItemHarness.with(filters: SkyLinkListItemHarnessFilters): HarnessPredicate<SkyLinkListItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListItemHarness>`

 SkyLinkListItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListItemHarness](/skyux/components/page?docs-active-tab=design#class_sky-link-list-item-harness.md) instances.

    interface SkyLinkListItemHarnessFilters {
      dataSkyId?: string | RegExp;
      text?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `text?: string`

Only find instances whose text content matches the given value.

# Development

                  Skip to Main Content

 Page
====

Pages provide consistent, responsive containers for common page layouts.

 Usage
------

### Use when

Use pages to apply consistent background colors and standardized layouts to all pages.

### Don't use when

Don't use pages in modals.

 Anatomy
--------

### Standard heading without page links

1

Header

2

Heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

[Avatar](/skyux/components/avatar.md) (optional)

6

Details (optional)

7

Actions (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-heading.0f513db7d271182cea483e6ecae854ca.png)

### Hub and spoke heading with page links

1

Header

2

Hub and spoke heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

Details (optional)

6

Actions (optional)

7

Page links area (optional)

8

Recently accessed link list (optional)

9

Page link list (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-hub.f9e8a05879794ae622f087a03d19b4cd.png)

 Options
--------

### Layouts

#### Blocks

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md), use the `blocks` layout to organize content into modular blocks. For a wide range of possible layouts, place a [fluid grid](/skyux/components/fluid-grid.md) or another grid layout via flexbox or CSS grid in the content area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-blocks-layout.76f82ea0c799d06acf73237b9266995e.png)

#### List

For [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `list` layout to display lists of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-list-layout.6a565c1ad637e53a00eea686b207b8a7.png)

#### Tabs

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md) or [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `tabs` layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see [tabs](/skyux/components/tabs.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-tabs-layout.cd00761effd67b07f9163f9dca6c9c52.png)

#### Fit

For [split view pages](/skyux/design/guidelines/page-layouts/split-view-page.md), use the `fit` layout to fill the content area and anchor content to the edges.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-fit-layout.2deadebc41c1f7f0e8e8cc83f1aed4d0.png)

#### None

For custom content that doesn't work well with predefined layouts or spacing, use the `none` layout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-none-layout.4a100252343c541041581837fd7b9eb4.png)

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

#### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-heading.62580a83a844948a6b1e8e75d4f4b406.png)

Page headings descibe the content on pages.

#### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke.f706d1d121110c699ad87ab958a8d51c.png)

Hub and spoke navigation connects child pages to a single parent hub page.

Hub

Hubs are parent pages with links to child pages that users can only navigate to from the hub. None found.

Spoke

Spokes are child pages that users only navigate to from a hub. Don't use hub and spoke heading when users can navigate to a child page from multiple places. None found.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke-diagram.4929796f70eeb8a3415c59e2ee377a42.png)

The hub and spoke pattern connects a parent hub page to child spoke pages. Users navigate to spokes from the hub.

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-breadcrumb-dont.458dc4831b8a02f26ad2b6fe293bede6.png)

Don't go more than one level deep in hub and spoke headings.

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use [tabs](/skyux/components/tabs.md) to group large amounts of content within a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-record-dont.ce87f18a349fc58e9cf133cb03d4ff82.png)

Don't use the hub and spoke pattern to connect a record page to its child pages.

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an [alert](/skyux/components/alert.md) in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) [avatar](/skyux/components/avatar.md) in the top left of [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Page links

#### Link lists

For `blocks` layout pages, you can add link lists for navigation in a way that is similar to [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md). Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's [Content guidelines](/skyux/design/guidelines/page-layouts/action-hub#section-content.md).

#### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-links-home.072443de8a2e9e96b37fdd3706ada2d0.png)

Page links provide navigation to other pages or tasks from a page.

#### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness [behaviors](/skyux/components/page#section-behaviors-and-states.md) below.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-page-links-layout.b22d6d87b0ba15518d15682fc93e2167.png)

Page link lists are positioned to the right of the page content.

 Behaviors and states
---------------------

### Responsiveness

Page layouts reflow content at the `xs` breakpoint of 767px.

![Blocks layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-blocks.bc588a127d94b27ec442496fcf02f456.png)

![List layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-list.d11e67ec7ac52ea211ee882b5acd0c28.png)

![Tabs layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-tabs.a05d5c647e4c54d3e35ab4aead6e840d.png)

![Fit layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-fit.ed1a9f74d40c7a3d68321a70f62fef52.png)

 Related information
--------------------

### Guidelines

*   [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)
*   [Buttons and links](/skyux/design/guidelines/buttons-links.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

### Components

*   [Alert](/skyux/components/alert.md)
*   [Avatar](/skyux/components/avatar.md)
*   [Buttons](/skyux/components/button.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

 Installation
-------------

NPM package

`@skyux/pages`[View in NPM](https://www.npmjs.com/package/@skyux/pages) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/pages/src/lib/modules/page/page.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/pages`Copy None found.

 SkyPageModule
--------------

Type: Module

`import { SkyPageModule } from '@skyux/pages';`

 SkyPageComponent
-----------------

Type: Component

Selector: `sky-page`

Displays a page using the specified layout. The page component is a responsive container, meaning content will respect the breakpoints within the page element instead of the window. This is helpful if there is other content to the left or right of the page.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the page's default [global help](/skyux/learn/develop/global-help.md) content to display.

#### `layout: InputSignal<SkyPageLayoutType>`

The page layout that applies spacing to the page header and content. Use the layout that corresponds with the top-level component type used on the page, or use `fit` to constrain the page contents to the available viewport. Use `none` for custom content that does not adhere to predefined spacing or constraints.

Default: `"none"`

 SkyPageContentComponent
------------------------

Type: Component

Selector: `sky-page-content`

Displays page contents using spacing that corresponds to the parent page's layout.

 SkyPageLinksComponent
----------------------

Type: Component

Selector: `sky-page-links`

Displays page links on the right side of the page, or below the page content on mobile devices.

 SkyPageLayoutType
------------------

Type: Type alias

    type SkyPageLayoutType = "none" | "fit" | "blocks" | "list" | "tabs"

 SkyPageHeaderModule
--------------------

Type: Module

`import { SkyPageHeaderModule } from '@skyux/pages';`

 SkyPageHeaderComponent
-----------------------

Type: Component

Selector: `sky-page-header`

Displays page heading's contents using spacing that corresponds to the parent page's layout

### Inputs

#### `pageTitle: string | undefined`

The title of the current page.

#### `parentLink: SkyPageLink | undefined`

A link to the parent page of the current page.

 SkyPageHeaderDetailsComponent
------------------------------

Type: Component

Selector: `sky-page-header-details`

Displays additional information in the page header, like record details. Appears below the title and above the page actions.

 SkyPageHeaderActionsComponent
------------------------------

Type: Component

Selector: `sky-page-header-actions`

Displays buttons within the page header for page actions and applies spacing between buttons. Appears below the page header details.

 SkyPageHeaderAlertsComponent
-----------------------------

Type: Component

Selector: `sky-page-header-alerts`

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

 SkyPageHeaderAvatarComponent
-----------------------------

Type: Component

Selector: `sky-page-header-avatar`

Displays an avatar within the page header to the left of the page title. If no size is specified for the avatar component it will display at size small on xs breakpoints and size large on small and above breakpoints.

 SkyPageLink
------------

Type: Interface

Displays links to related information or recently accessed items.

    interface SkyPageLink {
      label: string;
      permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string };
    }

### Properties

#### `label: string`

The link text.

#### `permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string }`

The link destination.

 SkyPageLinksInput
------------------

Type: Type alias

    type SkyPageLinksInput = SkyPageLink[] | "loading" | undefined

 SkyLinkListModule
------------------

Type: Module

`import { SkyLinkListModule } from '@skyux/pages';`

 SkyLinkListComponent
---------------------

Type: Component

Selector: `sky-link-list`

A component that displays a list of links, such as within a `<sky-page-links>` component.

### Inputs

#### `headingText: InputSignal<undefined | string>`

The text to display as the list's heading.

#### `links: InputSignal<SkyPageLinksInput>`

Option to pass links as an array of `SkyPageLink` objects or `'loading'` to display a loading indicator.

 SkyLinkListItemComponent
-------------------------

Type: Component

Selector: `sky-link-list-item`

A wrapper for each link in a link list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPageHarness
---------------

Type: Class

`import { SkyPageHarness } from '@skyux/pages/testing';`

Harness for interacting with a page component in tests.

### Methods

#### `getLayout(): Promise<SkyPageLayoutType>`

Gets the current layout.

#### Returns

`Promise<SkyPageLayoutType>`

#### `getPageHeader(filters?: SkyPageHeaderHarnessFilters): Promise<SkyPageHeaderHarness>`

Gets the first page header that matches the given filters.

#### Parameters

##### `filters?: SkyPageHeaderHarnessFilters`

filters for which page header to return

#### Returns

`Promise<SkyPageHeaderHarness>`

#### `SkyPageHarness.with(filters: SkyPageHarnessFilters): HarnessPredicate<SkyPageHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHarness>`

 SkyPageHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHarness](/skyux/components/page?docs-active-tab=development#class_sky-page-harness.md) instances.

    interface SkyPageHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPageHeaderHarness
---------------------

Type: Class

`import { SkyPageHeaderHarness } from '@skyux/pages/testing';`

Harness for interacting with a page header component in tests.

### Methods

#### `getPageTitle(): Promise<undefined | string>`

Gets the current page title.

#### Returns

`Promise<undefined | string>`

#### `getParentLinkText(): Promise<string>`

Gets the current page title.

#### Returns

`Promise<string>`

#### `SkyPageHeaderHarness.with(filters: SkyPageHeaderHarnessFilters): HarnessPredicate<SkyPageHeaderHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHeaderHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHeaderHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHeaderHarness>`

 SkyPageHeaderHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHeaderHarness](/skyux/components/page?docs-active-tab=development#class_sky-page-header-harness.md) instances.

    interface SkyPageHeaderHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListHarness
-------------------

Type: Class

`import { SkyLinkListHarness } from '@skyux/pages/testing';`

Harness for interacting with a link list component in tests.

### Methods

#### `getHeadingText(): Promise<undefined | string>`

Gets the link list's heading text. If there are no links, this will return `undefined`.

#### Returns

`Promise<undefined | string>`

#### `getListItem(filter: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness>`

Gets a specific link list item based on the filter criteria.

#### Parameters

##### `filter: SkyLinkListItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness>`

#### `getListItems(filter?: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness[]>`

Gets an array of link list items based on the filter criteria. If no filter is provided, returns all link list items.

#### Parameters

##### `filter?: SkyLinkListItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness[]>`

#### `isVisible(): Promise<boolean>`

Whether the link list is showing a list of links.

#### Returns

`Promise<boolean>`

#### `isWaiting(): Promise<boolean>`

Gets the status of the wait indicator.

#### Returns

`Promise<boolean>`

#### `SkyLinkListHarness.with(filters: SkyLinkListHarnessFilters): HarnessPredicate<SkyLinkListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListHarness>`

 SkyLinkListHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListHarness](/skyux/components/page?docs-active-tab=development#class_sky-link-list-harness.md) instances.

    interface SkyLinkListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListItemHarness
-----------------------

Type: Class

`import { SkyLinkListItemHarness } from '@skyux/pages/testing';`

Harness for interacting with a linked list item in tests.

### Methods

#### `click(): Promise<void>`

Clicks the item.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the text content of the item.

#### Returns

`Promise<string>`

#### `SkyLinkListItemHarness.with(filters: SkyLinkListItemHarnessFilters): HarnessPredicate<SkyLinkListItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListItemHarness>`

 SkyLinkListItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListItemHarness](/skyux/components/page?docs-active-tab=development#class_sky-link-list-item-harness.md) instances.

    interface SkyLinkListItemHarnessFilters {
      dataSkyId?: string | RegExp;
      text?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `text?: string`

Only find instances whose text content matches the given value.

# Examples

                    Skip to Main Content

 Page
====

Pages provide consistent, responsive containers for common page layouts.

Usage
------

### Use when

Use pages to apply consistent background colors and standardized layouts to all pages.

### Don't use when

Don't use pages in modals.

 Anatomy
--------

### Standard heading without page links

1

Header

2

Heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

[Avatar](/skyux/components/avatar.md) (optional)

6

Details (optional)

7

Actions (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-heading.0f513db7d271182cea483e6ecae854ca.png)

### Hub and spoke heading with page links

1

Header

2

Hub and spoke heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

Details (optional)

6

Actions (optional)

7

Page links area (optional)

8

Recently accessed link list (optional)

9

Page link list (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-hub.f9e8a05879794ae622f087a03d19b4cd.png)

 Options
--------

### Layouts

#### Blocks

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md), use the `blocks` layout to organize content into modular blocks. For a wide range of possible layouts, place a [fluid grid](/skyux/components/fluid-grid.md) or another grid layout via flexbox or CSS grid in the content area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-blocks-layout.76f82ea0c799d06acf73237b9266995e.png)

#### List

For [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `list` layout to display lists of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-list-layout.6a565c1ad637e53a00eea686b207b8a7.png)

#### Tabs

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md) or [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `tabs` layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see [tabs](/skyux/components/tabs.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-tabs-layout.cd00761effd67b07f9163f9dca6c9c52.png)

#### Fit

For [split view pages](/skyux/design/guidelines/page-layouts/split-view-page.md), use the `fit` layout to fill the content area and anchor content to the edges.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-fit-layout.2deadebc41c1f7f0e8e8cc83f1aed4d0.png)

#### None

For custom content that doesn't work well with predefined layouts or spacing, use the `none` layout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-none-layout.4a100252343c541041581837fd7b9eb4.png)

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

#### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-heading.62580a83a844948a6b1e8e75d4f4b406.png)

Page headings descibe the content on pages.

#### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke.f706d1d121110c699ad87ab958a8d51c.png)

Hub and spoke navigation connects child pages to a single parent hub page.

Hub

Hubs are parent pages with links to child pages that users can only navigate to from the hub. None found.

Spoke

Spokes are child pages that users only navigate to from a hub. Don't use hub and spoke heading when users can navigate to a child page from multiple places. None found.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke-diagram.4929796f70eeb8a3415c59e2ee377a42.png)

The hub and spoke pattern connects a parent hub page to child spoke pages. Users navigate to spokes from the hub.

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-breadcrumb-dont.458dc4831b8a02f26ad2b6fe293bede6.png)

Don't go more than one level deep in hub and spoke headings.

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use [tabs](/skyux/components/tabs.md) to group large amounts of content within a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-record-dont.ce87f18a349fc58e9cf133cb03d4ff82.png)

Don't use the hub and spoke pattern to connect a record page to its child pages.

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an [alert](/skyux/components/alert.md) in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) [avatar](/skyux/components/avatar.md) in the top left of [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Page links

#### Link lists

For `blocks` layout pages, you can add link lists for navigation in a way that is similar to [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md). Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's [Content guidelines](/skyux/design/guidelines/page-layouts/action-hub#section-content.md).

#### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-links-home.072443de8a2e9e96b37fdd3706ada2d0.png)

Page links provide navigation to other pages or tasks from a page.

#### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness [behaviors](/skyux/components/page#section-behaviors-and-states.md) below.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-page-links-layout.b22d6d87b0ba15518d15682fc93e2167.png)

Page link lists are positioned to the right of the page content.

 Behaviors and states
---------------------

### Responsiveness

Page layouts reflow content at the `xs` breakpoint of 767px.

![Blocks layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-blocks.bc588a127d94b27ec442496fcf02f456.png)

![List layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-list.d11e67ec7ac52ea211ee882b5acd0c28.png)

![Tabs layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-tabs.a05d5c647e4c54d3e35ab4aead6e840d.png)

![Fit layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-fit.ed1a9f74d40c7a3d68321a70f62fef52.png)

 Related information
--------------------

### Guidelines

*   [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)
*   [Buttons and links](/skyux/design/guidelines/buttons-links.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

### Components

*   [Alert](/skyux/components/alert.md)
*   [Avatar](/skyux/components/avatar.md)
*   [Buttons](/skyux/components/button.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

 Installation
-------------

NPM package

`@skyux/pages`[View in NPM](https://www.npmjs.com/package/@skyux/pages) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/pages/src/lib/modules/page/page.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/pages`Copy None found.

 SkyPageModule
--------------

Type: Module

`import { SkyPageModule } from '@skyux/pages';`

 SkyPageComponent
-----------------

Type: Component

Selector: `sky-page`

Displays a page using the specified layout. The page component is a responsive container, meaning content will respect the breakpoints within the page element instead of the window. This is helpful if there is other content to the left or right of the page.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the page's default [global help](/skyux/learn/develop/global-help.md) content to display.

#### `layout: InputSignal<SkyPageLayoutType>`

The page layout that applies spacing to the page header and content. Use the layout that corresponds with the top-level component type used on the page, or use `fit` to constrain the page contents to the available viewport. Use `none` for custom content that does not adhere to predefined spacing or constraints.

Default: `"none"`

 SkyPageContentComponent
------------------------

Type: Component

Selector: `sky-page-content`

Displays page contents using spacing that corresponds to the parent page's layout.

 SkyPageLinksComponent
----------------------

Type: Component

Selector: `sky-page-links`

Displays page links on the right side of the page, or below the page content on mobile devices.

 SkyPageLayoutType
------------------

Type: Type alias

    type SkyPageLayoutType = "none" | "fit" | "blocks" | "list" | "tabs"

 SkyPageHeaderModule
--------------------

Type: Module

`import { SkyPageHeaderModule } from '@skyux/pages';`

 SkyPageHeaderComponent
-----------------------

Type: Component

Selector: `sky-page-header`

Displays page heading's contents using spacing that corresponds to the parent page's layout

### Inputs

#### `pageTitle: string | undefined`

The title of the current page.

#### `parentLink: SkyPageLink | undefined`

A link to the parent page of the current page.

 SkyPageHeaderDetailsComponent
------------------------------

Type: Component

Selector: `sky-page-header-details`

Displays additional information in the page header, like record details. Appears below the title and above the page actions.

 SkyPageHeaderActionsComponent
------------------------------

Type: Component

Selector: `sky-page-header-actions`

Displays buttons within the page header for page actions and applies spacing between buttons. Appears below the page header details.

 SkyPageHeaderAlertsComponent
-----------------------------

Type: Component

Selector: `sky-page-header-alerts`

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

 SkyPageHeaderAvatarComponent
-----------------------------

Type: Component

Selector: `sky-page-header-avatar`

Displays an avatar within the page header to the left of the page title. If no size is specified for the avatar component it will display at size small on xs breakpoints and size large on small and above breakpoints.

 SkyPageLink
------------

Type: Interface

Displays links to related information or recently accessed items.

    interface SkyPageLink {
      label: string;
      permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string };
    }

### Properties

#### `label: string`

The link text.

#### `permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string }`

The link destination.

 SkyPageLinksInput
------------------

Type: Type alias

    type SkyPageLinksInput = SkyPageLink[] | "loading" | undefined

 SkyLinkListModule
------------------

Type: Module

`import { SkyLinkListModule } from '@skyux/pages';`

 SkyLinkListComponent
---------------------

Type: Component

Selector: `sky-link-list`

A component that displays a list of links, such as within a `<sky-page-links>` component.

### Inputs

#### `headingText: InputSignal<undefined | string>`

The text to display as the list's heading.

#### `links: InputSignal<SkyPageLinksInput>`

Option to pass links as an array of `SkyPageLink` objects or `'loading'` to display a loading indicator.

 SkyLinkListItemComponent
-------------------------

Type: Component

Selector: `sky-link-list-item`

A wrapper for each link in a link list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPageHarness
---------------

Type: Class

`import { SkyPageHarness } from '@skyux/pages/testing';`

Harness for interacting with a page component in tests.

### Methods

#### `getLayout(): Promise<SkyPageLayoutType>`

Gets the current layout.

#### Returns

`Promise<SkyPageLayoutType>`

#### `getPageHeader(filters?: SkyPageHeaderHarnessFilters): Promise<SkyPageHeaderHarness>`

Gets the first page header that matches the given filters.

#### Parameters

##### `filters?: SkyPageHeaderHarnessFilters`

filters for which page header to return

#### Returns

`Promise<SkyPageHeaderHarness>`

#### `SkyPageHarness.with(filters: SkyPageHarnessFilters): HarnessPredicate<SkyPageHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHarness>`

 SkyPageHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHarness](/skyux/components/page?docs-active-tab=examples#class_sky-page-harness.md) instances.

    interface SkyPageHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPageHeaderHarness
---------------------

Type: Class

`import { SkyPageHeaderHarness } from '@skyux/pages/testing';`

Harness for interacting with a page header component in tests.

### Methods

#### `getPageTitle(): Promise<undefined | string>`

Gets the current page title.

#### Returns

`Promise<undefined | string>`

#### `getParentLinkText(): Promise<string>`

Gets the current page title.

#### Returns

`Promise<string>`

#### `SkyPageHeaderHarness.with(filters: SkyPageHeaderHarnessFilters): HarnessPredicate<SkyPageHeaderHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHeaderHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHeaderHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHeaderHarness>`

 SkyPageHeaderHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHeaderHarness](/skyux/components/page?docs-active-tab=examples#class_sky-page-header-harness.md) instances.

    interface SkyPageHeaderHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListHarness
-------------------

Type: Class

`import { SkyLinkListHarness } from '@skyux/pages/testing';`

Harness for interacting with a link list component in tests.

### Methods

#### `getHeadingText(): Promise<undefined | string>`

Gets the link list's heading text. If there are no links, this will return `undefined`.

#### Returns

`Promise<undefined | string>`

#### `getListItem(filter: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness>`

Gets a specific link list item based on the filter criteria.

#### Parameters

##### `filter: SkyLinkListItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness>`

#### `getListItems(filter?: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness[]>`

Gets an array of link list items based on the filter criteria. If no filter is provided, returns all link list items.

#### Parameters

##### `filter?: SkyLinkListItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness[]>`

#### `isVisible(): Promise<boolean>`

Whether the link list is showing a list of links.

#### Returns

`Promise<boolean>`

#### `isWaiting(): Promise<boolean>`

Gets the status of the wait indicator.

#### Returns

`Promise<boolean>`

#### `SkyLinkListHarness.with(filters: SkyLinkListHarnessFilters): HarnessPredicate<SkyLinkListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListHarness>`

 SkyLinkListHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListHarness](/skyux/components/page?docs-active-tab=examples#class_sky-link-list-harness.md) instances.

    interface SkyLinkListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListItemHarness
-----------------------

Type: Class

`import { SkyLinkListItemHarness } from '@skyux/pages/testing';`

Harness for interacting with a linked list item in tests.

### Methods

#### `click(): Promise<void>`

Clicks the item.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the text content of the item.

#### Returns

`Promise<string>`

#### `SkyLinkListItemHarness.with(filters: SkyLinkListItemHarnessFilters): HarnessPredicate<SkyLinkListItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListItemHarness>`

 SkyLinkListItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListItemHarness](/skyux/components/page?docs-active-tab=examples#class_sky-link-list-item-harness.md) instances.

    interface SkyLinkListItemHarnessFilters {
      dataSkyId?: string | RegExp;
      text?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `text?: string`

Only find instances whose text content matches the given value.

### Home page with blocks layout, using tile dashboard and recently accessed links

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import { SkyHelpTestingModule } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageHomePageBlocksLayoutExampleComponent } from './example.component';
    
    describe('Record page blocks layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageHomePageBlocksLayoutExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageHomePageBlocksLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
    
        return { pageHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageHomePageBlocksLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should have a blocks layout', async () => {
        const { pageHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('blocks');
      });
    
      it('should have the correct page header text', async () => {
        const { pageHarness } = await setupTest();
    
        const pageHeaderHarness = await pageHarness.getPageHeader();
    
        await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo('Home');
    
        await expectAsync(
          pageHeaderHarness.getParentLinkText(),
        ).toBeRejectedWithError(/No parent link was found in the page header/);
      });
    });
Copy

    <sky-tile-dashboard [(config)]="dashboardConfig" />
Copy

    import { Component } from '@angular/core';
    import { SkyTileDashboardConfig, SkyTilesModule } from '@skyux/tiles';
    
    import { TileMyActionsComponent } from './tile-my-actions.component';
    import { TileUpdatesComponent } from './tile-updates.component';
    
    @Component({
      selector: 'app-home-page-content',
      templateUrl: './home-page-content.component.html',
      imports: [SkyTilesModule],
    })
    export class HomePageContentComponent {
      protected dashboardConfig: SkyTileDashboardConfig = {
        tiles: [
          {
            id: 'tile-updates',
            componentType: TileUpdatesComponent,
          },
          {
            id: 'tile-my-actions',
            componentType: TileMyActionsComponent,
          },
        ],
        layout: {
          singleColumn: {
            tiles: [
              {
                id: 'tile-updates',
                isCollapsed: false,
              },
              {
                id: 'tile-my-actions',
                isCollapsed: false,
              },
            ],
          },
          multiColumn: [
            {
              tiles: [
                {
                  id: 'tile-updates',
                  isCollapsed: false,
                },
              ],
            },
            {
              tiles: [
                {
                  id: 'tile-my-actions',
                  isCollapsed: false,
                },
              ],
            },
          ],
        },
      };
    }
Copy

    <sky-tile tileName="My actions">
      <sky-tile-title> My actions </sky-tile-title>
      <sky-tile-summary> 3 </sky-tile-summary>
      <sky-tile-content>
        <sky-tile-content-section>
          <sky-repeater data-sky-id="repeater-example">
            @for (item of items; track item) {
              <sky-repeater-item [itemName]="item.accessibilityLabel">
                @if (item.title) {
                  <sky-repeater-item-title class="example-repeater-flex">
                    <div class="example-repeater-item-title sky-margin-stacked-sm">
                      <a href="/">{{ item.title }}</a>
                    </div>
                    <div class="sky-font-deemphasized">{{ item.date }}</div>
                  </sky-repeater-item-title>
                }
                <sky-repeater-item-context-menu>
                  <sky-dropdown buttonType="context-menu">
                    <sky-dropdown-menu>
                      <sky-dropdown-item>
                        <button
                          type="button"
                          [attr.aria-label]="
                            'Action 1 for ' +
                            (item.title ?? item.accessibilityLabel)
                          "
                          (click)="onActionClicked('Action 1')"
                        >
                          Edit
                        </button>
                      </sky-dropdown-item>
                      <sky-dropdown-item>
                        <button
                          type="button"
                          [attr.aria-label]="
                            'Action 2 for ' +
                            (item.title ?? item.accessibilityLabel)
                          "
                          (click)="onActionClicked('Action 2')"
                        >
                          Mark as complete
                        </button>
                      </sky-dropdown-item>
                    </sky-dropdown-menu>
                  </sky-dropdown>
                </sky-repeater-item-context-menu>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-tile-content-section>
      </sky-tile-content>
    </sky-tile>
Copy

    import { Component } from '@angular/core';
    import { SkyRepeaterModule } from '@skyux/lists';
    import { SkyDropdownModule } from '@skyux/popovers';
    import { SkyTilesModule } from '@skyux/tiles';
    
    @Component({
      selector: 'app-tile-my-actions',
      styles: `
        :host {
          display: block;
        }
      `,
      templateUrl: './tile-my-actions.component.html',
      imports: [SkyTilesModule, SkyDropdownModule, SkyRepeaterModule],
    })
    export class TileMyActionsComponent {
      protected items: {
        date: string;
        status?: string;
        title?: string;
        accessibilityLabel?: string;
      }[] = [
        {
          title: 'Send invitation to Spring Ball',
          date: 'Today',
        },
        {
          title: 'Review portal activity',
          date: '10/2/2024',
        },
        {
          title: 'Assign prospects',
          date: '10/3/2024',
        },
      ];
      protected onActionClicked(buttonText: string): void {
        alert(buttonText + ' was clicked!');
      }
    }
Copy

    <sky-tile tileName="Updates" [showSettings]="false">
      <sky-tile-title> Updates </sky-tile-title>
      <sky-tile-summary> 2 </sky-tile-summary>
      <sky-tile-content>
        <sky-tile-content-section>
          <h3 class="sky-font-heading-3 sky-margin-stacked-sm">
            <a href="#">Prepare for Giving Tuesday</a>
          </h3>
          <div class="sky-font-deemphasized sky-margin-stacked-sm">10/1/2025</div>
          <div>
            Tips for creating a clear and compelling message, leveraging social
            media and email marketing, and providing multiple ways for donors to
            give.
          </div>
        </sky-tile-content-section>
        <sky-tile-content-section>
          <h3 class="sky-font-heading-3 sky-margin-stacked-sm">
            <a href="#">What's new</a>
          </h3>
          <div class="sky-font-deemphasized sky-margin-stacked-sm">9/28/2025</div>
          <ul>
            <li>Enhancement visualizations in reporting capabilities</li>
            <li>New automation for routine tasks</li>
            <li>Scan attachments for viruses</li>
          </ul>
        </sky-tile-content-section>
      </sky-tile-content>
    </sky-tile>
Copy

    import { Component } from '@angular/core';
    import { SkyTilesModule } from '@skyux/tiles';
    
    @Component({
      selector: 'app-tile-updates',
      styles: `
        :host {
          display: block;
        }
      `,
      templateUrl: './tile-updates.component.html',
      imports: [SkyTilesModule],
    })
    export class TileUpdatesComponent {}

Copy

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
### List page with list layout using data manager

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

    import { Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { Item } from './item';
    
    @Component({
      selector: 'app-dashboards-grid-context-menu',
      templateUrl: './dashboards-grid-context-menu.component.html',
      imports: [SkyDropdownModule],
    })
    export class DashboardGridContextMenuComponent
      implements ICellRendererAngularComp
    {
      protected dashboardName = '';
    
      public agInit(params: ICellRendererParams<Item>): void {
        this.dashboardName = params.data?.dashboard ?? '';
      }
    
      public refresh(): boolean {
        return false;
      }
    }
Copy

    <sky-page layout="list" helpKey="example-help">
      <sky-page-header pageTitle="Dashboards" />
      <sky-page-content>
        <app-list-page-content />
      </sky-page-content>
    </sky-page>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageListPageListLayoutExampleComponent } from './example.component';
    
    describe('List page list layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageListPageListLayoutExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageListPageListLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { pageHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageListPageListLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        });
      });
    
      it('should have a list layout', async () => {
        const { pageHarness } = await setupTest();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('list');
      });
    
      it('should have the correct page header text', async () => {
        const { pageHarness } = await setupTest();
    
        const pageHeaderHarness = await pageHarness.getPageHeader();
    
        await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
          'Dashboards',
        );
      });
    
      it('should have the correct help key', async () => {
        const { helpController } = await setupTest();
    
        helpController.expectCurrentHelpKey('example-help');
      });
    });
Copy

    export interface Item {
      dashboard: string;
      name: string;
      lastUpdated: string;
    }
Copy

    <sky-data-manager>
      <div class="sky-margin-stacked-xs">
        <sky-data-manager-toolbar>
          <sky-data-manager-toolbar-primary-item>
            <button
              aria-label="New dashboard"
              class="sky-btn sky-btn-default"
              type="button"
            >
              <sky-icon iconName="add" />
              New
            </button>
          </sky-data-manager-toolbar-primary-item>
        </sky-data-manager-toolbar>
      </div>
      <div class="sky-margin-stacked-sm">
        <sky-key-info class="sky-padding-horizontal-sm" layout="horizontal">
          <sky-key-info-value class="sky-font-display-4">
            {{ items.length }}
          </sky-key-info-value>
          <sky-key-info-label> Dashboards </sky-key-info-label>
        </sky-key-info>
      </div>
      <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
        <sky-ag-grid-wrapper>
          <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
        </sky-ag-grid-wrapper>
      </sky-data-view>
    </sky-data-manager>
Copy

    import { Component, OnInit, inject } from '@angular/core';
    import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
    import {
      SkyDataManagerModule,
      SkyDataManagerService,
      SkyDataManagerState,
      SkyDataViewConfig,
    } from '@skyux/data-manager';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridOptions,
      ICellRendererParams,
      ModuleRegistry,
    } from 'ag-grid-community';
    
    import { DashboardGridContextMenuComponent } from './dashboards-grid-context-menu.component';
    import { Item } from './item';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-list-page-content',
      templateUrl: './list-page-content.component.html',
      providers: [SkyDataManagerService],
      imports: [
        AgGridModule,
        SkyAgGridModule,
        SkyDataManagerModule,
        SkyIconModule,
        SkyKeyInfoModule,
      ],
    })
    export class ListPageContentComponent implements OnInit {
      protected items: Item[] = [
        {
          dashboard: 'Cash Flow Tracker',
          name: 'Kanesha Hutto',
          lastUpdated: '06/21/2023',
        },
        {
          dashboard: 'Accounts Receivable Dashboard',
          name: 'Kristeen Lunsford',
          lastUpdated: '06/30/2023',
        },
        {
          dashboard: 'Accounts Payable Dashboard',
          name: 'Darcel Lenz',
          lastUpdated: '04/20/2023',
        },
        {
          dashboard: 'Budget vs. Actual',
          name: 'Barbara Durr',
          lastUpdated: '12/04/2023',
        },
        {
          dashboard: 'Balance Sheet - New',
          name: 'Ilene Woo',
          lastUpdated: '12/20/2023',
        },
        {
          dashboard: 'Debt Management',
          name: 'Tonja Sanderson',
          lastUpdated: '09/10/2023',
        },
      ];
    
      protected gridOptions: GridOptions;
    
      #columnDefs: ColDef[] = [
        {
          colId: 'contextMenu',
          headerName: '',
          sortable: false,
          cellRenderer: DashboardGridContextMenuComponent,
          maxWidth: 55,
        },
        {
          colId: 'dashboard',
          field: 'dashboard',
          headerName: 'Name',
          width: 150,
          cellRenderer: (params: ICellRendererParams): string => {
            return `<a href="/">${params.value}</a>`;
          },
        },
        {
          colId: 'name',
          field: 'name',
          headerName: 'Created By',
        },
        {
          colId: 'lastUpdated',
          field: 'lastUpdated',
          headerName: 'Last Updated',
        },
      ];
    
      #viewConfig: SkyDataViewConfig = {
        id: 'gridView',
        name: 'Grid View',
        searchEnabled: true,
      };
    
      readonly #dataManagerService = inject(SkyDataManagerService);
      readonly #agGridSvc = inject(SkyAgGridService);
    
      constructor() {
        this.gridOptions = this.#agGridSvc.getGridOptions({
          gridOptions: {
            columnDefs: this.#columnDefs,
          },
        });
      }
    
      public ngOnInit(): void {
        this.#dataManagerService.initDataManager({
          activeViewId: 'gridView',
          dataManagerConfig: {},
          defaultDataState: new SkyDataManagerState({
            views: [
              {
                viewId: 'gridView',
                displayedColumnIds: [
                  'contextMenu',
                  'dashboard',
                  'name',
                  'lastUpdated',
                ],
              },
            ],
          }),
        });
    
        this.#dataManagerService.initDataView(this.#viewConfig);
      }
    }

Copy

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
### List page with tabs layout using data manager

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

    import { Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { Contact } from './contact';
    
    @Component({
      selector: 'app-contacts-grid-context-menu',
      templateUrl: './contact-context-menu.component.html',
      imports: [SkyDropdownModule],
    })
    export class ContactContextMenuComponent implements ICellRendererAngularComp {
      protected contactName = '';
    
      public agInit(params: ICellRendererParams<Contact>): void {
        this.contactName = params.data?.name ?? '';
      }
    
      public refresh(): boolean {
        return false;
      }
    }
Copy

    export interface Contact {
      name: string;
      organization: string;
      emailAddress: string;
    }
Copy

    <sky-page layout="tabs" helpKey="example-help">
      <sky-page-header pageTitle="Contacts" />
      <sky-page-content>
        <app-list-page-content />
      </sky-page-content>
    </sky-page>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageListPageTabsLayoutExampleComponent } from './example.component';
    
    describe('List page tabs layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageListPageTabsLayoutExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageListPageTabsLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { pageHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageListPageTabsLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should have a tabs layout', async () => {
        const { pageHarness } = await setupTest();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
      });
    
      it('should have the correct page header text', async () => {
        const { pageHarness } = await setupTest();
    
        const pageHeaderHarness = await pageHarness.getPageHeader();
    
        await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
          'Contacts',
        );
      });
    
      it('should have the correct help key', async () => {
        const { helpController } = await setupTest();
    
        helpController.expectCurrentHelpKey('example-help');
      });
    });
Copy

    <sky-data-manager>
      <div class="sky-margin-stacked-xs">
        <sky-data-manager-toolbar>
          <sky-data-manager-toolbar-primary-item>
            <button
              aria-label="New contact"
              class="sky-btn sky-btn-default"
              type="button"
            >
              <sky-icon iconName="add" />
              New
            </button>
          </sky-data-manager-toolbar-primary-item>
        </sky-data-manager-toolbar>
      </div>
      <div class="sky-margin-stacked-sm">
        <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
          <sky-key-info-value class="sky-font-display-4">
            {{ contacts.length }}
          </sky-key-info-value>
          <sky-key-info-label> Contacts </sky-key-info-label>
        </sky-key-info>
      </div>
      <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
        <sky-ag-grid-wrapper>
          <ag-grid-angular [gridOptions]="gridOptions" [rowData]="contacts" />
        </sky-ag-grid-wrapper>
      </sky-data-view>
    </sky-data-manager>
Copy

    import { Component, Input, OnInit, inject } from '@angular/core';
    import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
    import {
      SkyDataManagerModule,
      SkyDataManagerService,
      SkyDataManagerState,
      SkyDataViewConfig,
    } from '@skyux/data-manager';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridOptions,
      ICellRendererParams,
      ModuleRegistry,
    } from 'ag-grid-community';
    
    import { ContactContextMenuComponent } from './contact-context-menu.component';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    interface Contact {
      name: string;
      organization: string;
      emailAddress: string;
    }
    
    @Component({
      selector: 'app-list-page-contacts-grid',
      templateUrl: './list-page-contacts-grid.component.html',
      providers: [SkyDataManagerService],
      imports: [
        AgGridModule,
        SkyAgGridModule,
        SkyDataManagerModule,
        SkyIconModule,
        SkyKeyInfoModule,
      ],
    })
    export class ListPageContactsGridComponent implements OnInit {
      @Input()
      public contacts: Contact[] = [];
    
      protected gridOptions: GridOptions;
    
      #dataManagerService = inject(SkyDataManagerService);
      #agGridSvc = inject(SkyAgGridService);
    
      #columnDefs: ColDef[] = [
        {
          colId: 'contextMenu',
          headerName: '',
          sortable: false,
          cellRenderer: ContactContextMenuComponent,
          maxWidth: 55,
        },
        {
          colId: 'name',
          field: 'name',
          headerName: 'Name',
          width: 150,
          cellRenderer: (params: ICellRendererParams): string => {
            return `<a href="/">${params.value}</a>`;
          },
        },
        {
          colId: 'organization',
          field: 'organization',
          headerName: 'Organization',
        },
        {
          colId: 'emailAddress',
          field: 'emailAddress',
          headerName: 'Email Address',
        },
      ];
    
      #viewConfig: SkyDataViewConfig = {
        id: 'gridView',
        name: 'Grid View',
        searchEnabled: true,
        columnPickerEnabled: true,
        columnOptions: [
          { id: 'contextMenu', label: 'Context menu', alwaysDisplayed: true },
          { id: 'name', label: 'Name' },
          { id: 'organization', label: 'Organization' },
          { id: 'emailAddress', label: 'Email Address' },
        ],
      };
    
      constructor() {
        this.gridOptions = this.#agGridSvc.getGridOptions({
          gridOptions: {
            columnDefs: this.#columnDefs,
          },
        });
      }
    
      public ngOnInit(): void {
        this.#dataManagerService.initDataManager({
          activeViewId: 'gridView',
          dataManagerConfig: {},
          defaultDataState: new SkyDataManagerState({
            views: [
              {
                viewId: 'gridView',
                displayedColumnIds: [
                  'contextMenu',
                  'name',
                  'organization',
                  'emailAddress',
                ],
              },
            ],
          }),
        });
    
        this.#dataManagerService.initDataView(this.#viewConfig);
      }
    }
Copy

    <sky-tabset [(active)]="activeTabIndex">
      <sky-tab tabHeading="My contacts" layout="list">
        @if (activeTabIndex === 0) {
          <app-list-page-contacts-grid [contacts]="myContacts" />
        }
      </sky-tab>
      <sky-tab tabHeading="All contacts" layout="list">
        @if (activeTabIndex === 1) {
          <app-list-page-contacts-grid [contacts]="allContacts" />
        }
      </sky-tab>
    </sky-tabset>
Copy

    import { Component } from '@angular/core';
    import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';
    
    import { Contact } from './contact';
    import { ListPageContactsGridComponent } from './list-page-contacts-grid.component';
    
    @Component({
      selector: 'app-list-page-content',
      templateUrl: './list-page-content.component.html',
      imports: [ListPageContactsGridComponent, SkyTabsModule],
    })
    export class ListPageContentComponent {
      protected activeTabIndex: SkyTabIndex = 0;
    
      protected myContacts: Contact[] = [
        {
          name: 'Wonda Lumpkin',
          organization: 'Riverfront College of the Arts',
          emailAddress: 'wlumpkin@yahoo.com',
        },
        {
          name: 'Eliza Vanhorn',
          organization: 'Summit School of the Arts',
          emailAddress: 'evanhorn@outlook.com',
        },
        {
          name: 'Ed Sipes',
          organization: 'Reflections Middle School',
          emailAddress: 'esipes@yahoo.com',
        },
        {
          name: 'Elwood Farris',
          organization: 'Sandy Lagoon College',
          emailAddress: 'elfarris@gmail.com',
        },
        {
          name: 'Cristen Sizemore',
          organization: 'Grafton Vision Health',
          emailAddress: 'cristen.sizemore@aol.com',
        },
        {
          name: 'Latrice Ashmore',
          organization: 'Food Bank of Rapid City',
          emailAddress: 'lashmore@gmail.com',
        },
      ];
    
      protected allContacts = [
        ...this.myContacts,
        {
          name: 'Kanesha Hutto',
          organization: 'Los Angeles College of the Arts',
          emailAddress: 'khutto@yahoo.com',
        },
        {
          name: 'Kristeen Lunsford',
          organization: 'Food Bank of Los Angeles',
          emailAddress: 'kristeen.lunsford@yahoo.com',
        },
        {
          name: 'Barbara Durr',
          organization: 'Riverfront Middle School',
          emailAddress: 'bdurr@gmail.com',
        },
        {
          name: 'Ilene Woo',
          organization: 'Rapid City High School',
          emailAddress: 'ilene.woo@aol.com',
        },
        {
          name: 'Darcel Lenz',
          organization: 'Riverfront College of the Arts',
          emailAddress: 'dlenz@yahoo.com',
        },
      ];
    }

Copy

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
### Record page with blocks layout using box components

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageRecordPageBlocksLayoutExampleComponent } from './example.component';
    
    describe('Record page blocks layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageRecordPageBlocksLayoutExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageRecordPageBlocksLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { pageHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageRecordPageBlocksLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should have a blocks layout', async () => {
        const { pageHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('blocks');
      });
    
      it('should have the correct page header text', async () => {
        const { pageHarness } = await setupTest();
    
        const pageHeaderHarness = await pageHarness.getPageHeader();
    
        await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
          '$500 pledge',
        );
    
        await expectAsync(pageHeaderHarness.getParentLinkText()).toBeResolvedTo(
          'Pledges',
        );
      });
    
      it('should have the correct help key', async () => {
        const { helpController } = await setupTest();
    
        helpController.expectCurrentHelpKey('example-help');
      });
    });
Copy

    <sky-fluid-grid gutterSize="medium" [disableMargin]="true">
      <sky-row>
        <sky-column [screenMedium]="4" [screenSmall]="12">
          <sky-box class="sky-margin-stacked-xl" headingText="Details">
            <sky-box-controls>
              <button
                aria-label="Edit button for details"
                class="sky-btn sky-btn-icon-borderless"
                type="button"
              >
                <sky-icon iconName="edit" />
              </button>
            </sky-box-controls>
            <sky-box-content>
              <sky-description-list mode="vertical">
                @for (recordDetail of recordDetails; track recordDetail.detail) {
                  <sky-description-list-content>
                    <sky-description-list-term>
                      {{ recordDetail.detail }}
                    </sky-description-list-term>
                    <sky-description-list-description>
                      {{ recordDetail.info }}
                    </sky-description-list-description>
                  </sky-description-list-content>
                }
              </sky-description-list>
            </sky-box-content>
          </sky-box>
        </sky-column>
        <sky-column [screenMedium]="4" [screenSmall]="12">
          <sky-box class="sky-margin-stacked-xl" headingText="Payments">
            <sky-box-content>
              <div class="box-2-content">
                <div class="box-2-actuals">
                  <h3 class="sky-font-heading-4">Actuals</h3>
                  @for (
                    actual of actualPayments;
                    track actual.category;
                    let i = $index
                  ) {
                    <sky-key-info
                      [ngClass]="{
                        'sky-margin-stacked-lg': i < actualPayments.length - 1
                      }"
                    >
                      <sky-key-info-value class="sky-font-display-3">
                        {{ actual.value }}
                      </sky-key-info-value>
                      <sky-key-info-label>{{ actual.category }}</sky-key-info-label>
                    </sky-key-info>
                  }
                </div>
                <div class="box-2-projected">
                  <h3 class="sky-font-heading-4">Projected</h3>
                  @for (
                    projected of projectedPayments;
                    track projected;
                    let i = $index
                  ) {
                    <sky-key-info
                      [ngClass]="{
                        'sky-margin-stacked-lg': i < projectedPayments.length - 1
                      }"
                    >
                      <sky-key-info-value class="sky-font-display-3">
                        {{ projected.value }}
                      </sky-key-info-value>
                      <sky-key-info-label>
                        {{ projected.category }}
                      </sky-key-info-label>
                    </sky-key-info>
                  }
                </div>
              </div>
            </sky-box-content>
          </sky-box>
        </sky-column>
        <sky-column [screenMedium]="4" [screenSmall]="12">
          <sky-box headingText="Recent activity">
            <sky-box-content>
              <sky-repeater>
                @for (activity of recentActivity; track activity.activity) {
                  <sky-repeater-item>
                    <sky-repeater-item-content>
                      <div class="sky-margin-stacked-xs">
                        {{ activity.activity }}
                      </div>
                      <div class="sky-font-deemphasized">{{ activity.date }}</div>
                    </sky-repeater-item-content>
                  </sky-repeater-item>
                }
              </sky-repeater>
            </sky-box-content>
          </sky-box>
        </sky-column>
      </sky-row>
    </sky-fluid-grid>
Copy

    .box-2-content {
      display: flex;
    
      div {
        display: flex;
        flex-direction: column;
        flex-grow: 1;
      }
    
      .box-2-actuals {
        margin-right: 60px;
      }
    }
Copy

    import { CommonModule } from '@angular/common';
    import { Component } from '@angular/core';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    import {
      SkyBoxModule,
      SkyDescriptionListModule,
      SkyFluidGridModule,
    } from '@skyux/layout';
    import { SkyRepeaterModule } from '@skyux/lists';
    
    @Component({
      selector: 'app-record-page-content',
      templateUrl: './record-page-content.component.html',
      styleUrls: ['./record-page-content.component.scss'],
      imports: [
        CommonModule,
        SkyBoxModule,
        SkyDescriptionListModule,
        SkyFluidGridModule,
        SkyIconModule,
        SkyKeyInfoModule,
        SkyRepeaterModule,
      ],
    })
    export class RecordPageContentComponent {
      protected recordDetails = [
        {
          detail: 'Designation',
          info: 'General operating',
        },
        {
          detail: 'Source',
          info: 'Online donation form',
        },
        {
          detail: 'Status',
          info: 'Active',
        },
        {
          detail: 'Due date',
          info: '12/12/2023',
        },
        {
          detail: 'Create date',
          info: '01/05/2023',
        },
        {
          detail: 'Frequency',
          info: 'Quarterly',
        },
      ];
    
      protected actualPayments = [
        {
          category: 'Amount',
          value: '$845.00',
        },
        {
          category: 'Assigned',
          value: '$800.00',
        },
        {
          category: 'Applied',
          value: '$800.00',
        },
        {
          category: 'Payments',
          value: 25,
        },
      ];
    
      protected projectedPayments = [
        {
          category: 'Amount',
          value: '$0',
        },
        {
          category: 'Line items',
          value: 0,
        },
      ];
    
      protected recentActivity = [
        {
          activity: '$250.00 payment processed successfully.',
          date: '07/01/2023 12:02 am',
        },
        {
          activity: '$150.00 payment processed successfully.',
          date: '06/15/2023 12:02 am',
        },
        {
          activity: '$250.00 payment processed successfully.',
          date: '04/01/2023 12:02 am',
        },
      ];
    }

Copy

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
### Record page with tabs layout using data manager

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

    export interface Attachment {
      name: string;
      description: string;
      size: string;
      dateAdded: string;
    }
Copy

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
Copy

    import { Component } from '@angular/core';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    import { ICellRendererAngularComp } from 'ag-grid-angular';
    import { ICellRendererParams } from 'ag-grid-community';
    
    import { Attachment } from './attachment';
    
    @Component({
      selector: 'app-attachments-grid-context-menu',
      templateUrl: './attachments-grid-context-menu.component.html',
      imports: [SkyDropdownModule],
    })
    export class AttachmentsGridContextMenuComponent
      implements ICellRendererAngularComp
    {
      protected attachmentName = '';
    
      public agInit(params: ICellRendererParams<Attachment>): void {
        this.attachmentName = params.data?.name ?? '';
      }
    
      public refresh(): boolean {
        return false;
      }
    }
Copy

    export interface Detail {
      detail: string;
      info: string;
    }
Copy

    <sky-page layout="tabs" helpKey="example-help">
      <sky-page-header pageTitle="Charlene Conners">
        <sky-page-header-alerts>
          <sky-alert alertType="warning" descriptionType="warning">
            Missing phone number for Charlene Conners.
          </sky-alert>
        </sky-page-header-alerts>
        <sky-page-header-avatar>
          <sky-avatar name="Charlene Conners" />
        </sky-page-header-avatar>
        <sky-page-header-details>
          <sky-label labelType="info" descriptionType="important-info">
            VIP
          </sky-label>
        </sky-page-header-details>
        <sky-page-header-actions>
          <button class="sky-btn sky-btn-default" type="button">
            Email contact
          </button>
          <button class="sky-btn sky-btn-default" type="button">
            Add to my contacts
          </button>
        </sky-page-header-actions>
      </sky-page-header>
      <sky-page-content>
        <app-record-page-content />
      </sky-page-content>
    </sky-page>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageRecordPageTabsLayoutExampleComponent } from './example.component';
    
    describe('Record page tabs layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageRecordPageTabsLayoutExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageRecordPageTabsLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { pageHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageRecordPageTabsLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should have a tabs layout', async () => {
        const { pageHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
      });
    
      it('should have the correct page header text', async () => {
        const { pageHarness } = await setupTest();
    
        const pageHeaderHarness = await pageHarness.getPageHeader();
    
        await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
          'Charlene Conners',
        );
      });
    
      it('should have the correct help key', async () => {
        const { helpController } = await setupTest();
    
        helpController.expectCurrentHelpKey('example-help');
      });
    });
Copy

    <sky-data-manager>
      <div class="sky-margin-stacked-xs">
        <sky-data-manager-toolbar>
          <sky-data-manager-toolbar-primary-item>
            <button
              aria-label="New attachment"
              class="sky-btn sky-btn-default"
              type="button"
            >
              <sky-icon iconName="add" />
              New
            </button>
          </sky-data-manager-toolbar-primary-item>
        </sky-data-manager-toolbar>
      </div>
      <div class="sky-margin-stacked-sm">
        <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
          <sky-key-info-value class="sky-font-display-4">
            {{ items.length }}
          </sky-key-info-value>
          <sky-key-info-label> Attachments </sky-key-info-label>
        </sky-key-info>
      </div>
      <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
        <sky-ag-grid-wrapper>
          <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
        </sky-ag-grid-wrapper>
      </sky-data-view>
    </sky-data-manager>
Copy

    import { Component, OnInit, inject } from '@angular/core';
    import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
    import {
      SkyDataManagerModule,
      SkyDataManagerService,
      SkyDataManagerState,
      SkyDataViewConfig,
    } from '@skyux/data-manager';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    
    import { AgGridModule } from 'ag-grid-angular';
    import {
      AllCommunityModule,
      ColDef,
      GridOptions,
      ICellRendererParams,
      ModuleRegistry,
    } from 'ag-grid-community';
    
    import { Attachment } from './attachment';
    import { AttachmentsGridContextMenuComponent } from './attachments-grid-context-menu.component';
    
    ModuleRegistry.registerModules([AllCommunityModule]);
    
    @Component({
      selector: 'app-record-page-attachments-tab',
      templateUrl: './record-page-attachments-tab.component.html',
      providers: [SkyDataManagerService],
      imports: [
        AgGridModule,
        SkyAgGridModule,
        SkyDataManagerModule,
        SkyKeyInfoModule,
        SkyIconModule,
      ],
    })
    export class RecordPageAttachmentsTabComponent implements OnInit {
      protected items: Attachment[] = [
        {
          name: 'Agreement.pdf',
          description: 'Cardholder agreement',
          size: '10 KB',
          dateAdded: '01/28/2023',
        },
        {
          name: 'Appendix.pdf',
          description: 'Updated terms 2023',
          size: '25 KB',
          dateAdded: '05/05/2023',
        },
      ];
      protected gridOptions: GridOptions;
    
      #dataManagerService = inject(SkyDataManagerService);
      #agGridSvc = inject(SkyAgGridService);
    
      #columnDefs: ColDef[] = [
        {
          colId: 'contextMenu',
          headerName: '',
          sortable: false,
          cellRenderer: AttachmentsGridContextMenuComponent,
          maxWidth: 55,
        },
        {
          colId: 'name',
          field: 'name',
          headerName: 'Name',
          width: 150,
          cellRenderer: (params: ICellRendererParams): string => {
            return `<a href="/">${params.value}</a>`;
          },
        },
        {
          colId: 'description',
          field: 'description',
          headerName: 'Description',
        },
        {
          colId: 'size',
          field: 'size',
          headerName: 'Size',
        },
        {
          colId: 'dateAdded',
          field: 'dateAdded',
          headerName: 'Date Added',
        },
      ];
    
      #viewConfig: SkyDataViewConfig = {
        id: 'gridView',
        name: 'Grid View',
        searchEnabled: true,
      };
    
      constructor() {
        this.gridOptions = this.#agGridSvc.getGridOptions({
          gridOptions: {
            columnDefs: this.#columnDefs,
          },
        });
      }
    
      public ngOnInit(): void {
        this.#dataManagerService.initDataManager({
          activeViewId: 'gridView',
          dataManagerConfig: {},
          defaultDataState: new SkyDataManagerState({
            views: [
              {
                viewId: 'gridView',
                displayedColumnIds: [
                  'contextMenu',
                  'name',
                  'description',
                  'size',
                  'dateAdded',
                ],
              },
            ],
          }),
        });
    
        this.#dataManagerService.initDataView(this.#viewConfig);
      }
    }
Copy

    <sky-tabset [(active)]="activeTabIndex">
      <sky-tab tabHeading="Overview" layout="blocks">
        <app-record-page-overview-tab />
      </sky-tab>
      <sky-tab tabHeading="Notes" layout="list">
        <app-record-page-notes-tab />
      </sky-tab>
      <sky-tab tabHeading="Attachments" layout="list">
        @if (activeTabIndex === 2) {
          <app-record-page-attachments-tab />
        }
      </sky-tab>
    </sky-tabset>
Copy

    import { Component } from '@angular/core';
    import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';
    
    import { RecordPageAttachmentsTabComponent } from './record-page-attachments-tab.component';
    import { RecordPageNotesTabComponent } from './record-page-notes-tab.component';
    import { RecordPageOverviewTabComponent } from './record-page-overview-tab.component';
    
    @Component({
      selector: 'app-record-page-content',
      templateUrl: './record-page-content.component.html',
      imports: [
        RecordPageAttachmentsTabComponent,
        RecordPageNotesTabComponent,
        RecordPageOverviewTabComponent,
        SkyTabsModule,
      ],
    })
    export class RecordPageContentComponent {
      protected activeTabIndex: SkyTabIndex = 0;
    }
Copy

    <div class="sky-margin-stacked-xs">
      <sky-toolbar>
        <sky-toolbar-item>
          <button
            class="sky-btn sky-btn-default"
            type="button"
            aria-label="New note"
          >
            <sky-icon iconName="add" />
            New
          </button>
        </sky-toolbar-item>
        <sky-toolbar-item>
          <sky-sort [showButtonText]="true">
            <sky-sort-item>
              <span aria-label="Sort notes by date created (newest first)">
                Date created (newest first)
              </span>
            </sky-sort-item>
            <sky-sort-item>
              <span aria-label="Sort notes by date created (oldest first)">
                Date created (oldest first)
              </span>
            </sky-sort-item>
          </sky-sort>
        </sky-toolbar-item>
        <sky-toolbar-item>
          <button
            class="sky-btn sky-btn-default"
            type="button"
            aria-label="Export notes"
          >
            <sky-icon iconName="document-xls" />
            Export
          </button>
        </sky-toolbar-item>
        <sky-toolbar-item>
          <sky-search placeholderText="Find in notes" />
        </sky-toolbar-item>
      </sky-toolbar>
    </div>
    <div class="sky-margin-stacked-sm">
      <sky-key-info layout="horizontal">
        <sky-key-info-value class="sky-font-display-4">
          {{ notes.length }}
        </sky-key-info-value>
        <sky-key-info-label> Notes </sky-key-info-label>
      </sky-key-info>
    </div>
    <sky-repeater>
      @for (note of notes; track note.noteNumber) {
        <sky-repeater-item>
          <sky-repeater-item-context-menu>
            <sky-dropdown
              buttonType="context-menu"
              [label]="
                'Context menu for note ' + note.noteNumber + ' from ' + note.date
              "
            >
              <sky-dropdown-menu>
                <sky-dropdown-item>
                  <button
                    type="button"
                    [attr.aria-label]="
                      'Edit note ' + note.noteNumber + ' from ' + note.date
                    "
                  >
                    Edit
                  </button>
                </sky-dropdown-item>
                <sky-dropdown-item>
                  <button
                    type="button"
                    [attr.aria-label]="
                      'Delete note ' + note.noteNumber + ' from ' + note.date
                    "
                  >
                    Delete
                  </button>
                </sky-dropdown-item>
              </sky-dropdown-menu>
            </sky-dropdown>
          </sky-repeater-item-context-menu>
          <sky-repeater-item-content>
            <div class="sky-margin-stacked-xs">
              {{ note.content }}
            </div>
            <div class="sky-font-deemphasized">{{ note.date }}</div>
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
Copy

    import { Component } from '@angular/core';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    import { SkyToolbarModule } from '@skyux/layout';
    import { SkyRepeaterModule, SkySortModule } from '@skyux/lists';
    import { SkySearchModule } from '@skyux/lookup';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    @Component({
      selector: 'app-record-page-notes-tab',
      templateUrl: './record-page-notes-tab.component.html',
      imports: [
        SkyDropdownModule,
        SkyIconModule,
        SkyKeyInfoModule,
        SkyRepeaterModule,
        SkySearchModule,
        SkySortModule,
        SkyToolbarModule,
      ],
    })
    export class RecordPageNotesTabComponent {
      protected notes = [
        {
          noteNumber: 1,
          content: 'Attended our gala last year and had a great time.',
          date: '11/17/2024',
        },
        {
          noteNumber: 2,
          content:
            'Is a business owner and has a lot of connections in the community.',
          date: '10/11/2024',
        },
      ];
    }
Copy

    <sky-fluid-grid gutterSize="medium" [disableMargin]="true">
      <sky-row>
        <sky-column [screenSmall]="4" [screenXSmall]="12">
          <sky-box class="sky-margin-stacked-xl" headingText="Details">
            <sky-box-controls>
              <button
                aria-label="Edit button for details"
                class="sky-btn sky-btn-icon-borderless"
                type="button"
              >
                <sky-icon iconName="edit" />
              </button>
            </sky-box-controls>
            <sky-box-content>
              <sky-description-list mode="vertical">
                @for (recordDetail of recordDetails; track recordDetail.detail) {
                  <sky-description-list-content>
                    <sky-description-list-term>
                      {{ recordDetail.detail }}
                    </sky-description-list-term>
                    <sky-description-list-description>
                      {{ recordDetail.info }}
                    </sky-description-list-description>
                  </sky-description-list-content>
                }
              </sky-description-list>
            </sky-box-content>
          </sky-box>
        </sky-column>
        <sky-column [screenSmall]="4" [screenXSmall]="12">
          <sky-box class="sky-margin-stacked-xl" headingText="Payments">
            <sky-box-content>
              <div class="box-2-content">
                <div class="box-2-actuals">
                  <h3 class="sky-font-heading-4">Actuals</h3>
                  @for (
                    actual of actualPayments;
                    track actual.category;
                    let i = $index
                  ) {
                    <sky-key-info
                      [ngClass]="{
                        'sky-margin-stacked-lg': i < actualPayments.length - 1
                      }"
                    >
                      <sky-key-info-value class="sky-font-display-3">
                        {{ actual.value }}
                      </sky-key-info-value>
                      <sky-key-info-label>{{ actual.category }}</sky-key-info-label>
                    </sky-key-info>
                  }
                </div>
                <div class="box-2-projected">
                  <h3 class="sky-font-heading-4">Projected</h3>
                  @for (
                    projected of projectedPayments;
                    track projected;
                    let i = $index
                  ) {
                    <sky-key-info
                      [ngClass]="{
                        'sky-margin-stacked-lg': i < projectedPayments.length - 1
                      }"
                    >
                      <sky-key-info-value class="sky-font-display-3">
                        {{ projected.value }}
                      </sky-key-info-value>
                      <sky-key-info-label>
                        {{ projected.category }}
                      </sky-key-info-label>
                    </sky-key-info>
                  }
                </div>
              </div>
            </sky-box-content>
          </sky-box>
        </sky-column>
        <sky-column [screenSmall]="4" [screenXSmall]="12">
          <sky-box headingText="Recent activity">
            <sky-box-content>
              <sky-repeater>
                @for (activity of recentActivity; track activity.activity) {
                  <sky-repeater-item>
                    <sky-repeater-item-content>
                      <div class="sky-margin-stacked-xs">
                        {{ activity.activity }}
                      </div>
                      <div class="sky-font-deemphasized">{{ activity.date }}</div>
                    </sky-repeater-item-content>
                  </sky-repeater-item>
                }
              </sky-repeater>
            </sky-box-content>
          </sky-box>
        </sky-column>
      </sky-row>
    </sky-fluid-grid>
Copy

    .box-2-content {
      display: flex;
    
      div {
        display: flex;
        flex-direction: column;
        flex-grow: 1;
      }
    
      .box-2-actuals {
        margin-right: 60px;
      }
    }
Copy

    import { CommonModule } from '@angular/common';
    import { Component } from '@angular/core';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    import {
      SkyBoxModule,
      SkyDescriptionListModule,
      SkyFluidGridModule,
    } from '@skyux/layout';
    import { SkyRepeaterModule } from '@skyux/lists';
    
    import { Detail } from './detail';
    
    @Component({
      selector: 'app-record-page-overview-tab',
      templateUrl: './record-page-overview-tab.component.html',
      styleUrls: ['./record-page-overview-tab.component.scss'],
      imports: [
        CommonModule,
        SkyBoxModule,
        SkyDescriptionListModule,
        SkyFluidGridModule,
        SkyIconModule,
        SkyKeyInfoModule,
        SkyRepeaterModule,
      ],
    })
    export class RecordPageOverviewTabComponent {
      protected recordDetails: Detail[] = [
        {
          detail: 'Designation',
          info: 'General operating',
        },
        {
          detail: 'Source',
          info: 'Online donation form',
        },
        {
          detail: 'Status',
          info: 'Active',
        },
        {
          detail: 'Due date',
          info: '12/12/2023',
        },
        {
          detail: 'Create date',
          info: '01/05/2023',
        },
        {
          detail: 'Frequency',
          info: 'Quarterly',
        },
      ];
    
      protected actualPayments = [
        {
          category: 'Amount',
          value: '$845.00',
        },
        {
          category: 'Assigned',
          value: '$800.00',
        },
        {
          category: 'Applied',
          value: '$800.00',
        },
        {
          category: 'Payments',
          value: 25,
        },
      ];
    
      protected projectedPayments = [
        {
          category: 'Amount',
          value: '$0',
        },
        {
          category: 'Line items',
          value: 0,
        },
      ];
    
      protected recentActivity = [
        {
          activity: '$250.00 payment processed successfully.',
          date: '07/01/2023 12:02 am',
        },
        {
          activity: '$150.00 payment processed successfully.',
          date: '06/15/2023 12:02 am',
        },
        {
          activity: '$250.00 payment processed successfully.',
          date: '04/01/2023 12:02 am',
        },
      ];
    }

Copy

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
### Split view page with fit layout

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    
    import { PagesPageSplitViewPageFitLayoutExampleComponent } from './example.component';
    
    describe('Split view page fit layout example', () => {
      async function setupTest(): Promise<{
        pageHarness: SkyPageHarness;
        fixture: ComponentFixture<PagesPageSplitViewPageFitLayoutExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          PagesPageSplitViewPageFitLayoutExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const pageHarness = await loader.getHarness(SkyPageHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { pageHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            PagesPageSplitViewPageFitLayoutExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should have a fit layout', async () => {
        const { pageHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('fit');
      });
    
      it('should have the correct help key', async () => {
        const { helpController } = await setupTest();
    
        helpController.expectCurrentHelpKey('example-help');
      });
    });
Copy

    <sky-split-view dock="fill" [messageStream]="splitViewStream">
      <sky-split-view-drawer [ariaLabel]="'Transaction list'" [width]="listWidth">
        <sky-repeater [activeIndex]="activeIndex">
          @for (item of items; track item.id; let i = $index) {
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
    
      <sky-split-view-workspace ariaLabel="Transaction form">
        <sky-split-view-workspace-content class="sky-padding-even-xl">
          <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
            <sky-description-list class="sky-margin-stacked-xl">
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
                <sky-description-list-term> Vendor </sky-description-list-term>
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
            <div>
              <sky-input-box stacked="true" labelText="Approved amount">
                <input
                  formControlName="approvedAmount"
                  name="approvedAmount"
                  type="text"
                />
              </sky-input-box>
            </div>
    
            <div>
              <sky-input-box stacked="true" labelText="Comments">
                <textarea formControlName="comments" name="comments"></textarea>
              </sky-input-box>
            </div>
          </form>
        </sky-split-view-workspace-content>
        <sky-split-view-workspace-footer>
          <sky-summary-action-bar>
            <sky-summary-action-bar-actions>
              <sky-summary-action-bar-primary-action (actionClick)="onApprove()">
                Approve expense
              </sky-summary-action-bar-primary-action>
              <sky-summary-action-bar-secondary-actions>
                <sky-summary-action-bar-secondary-action (actionClick)="onDeny()">
                  Deny expense
                </sky-summary-action-bar-secondary-action>
              </sky-summary-action-bar-secondary-actions>
            </sky-summary-action-bar-actions>
          </sky-summary-action-bar>
        </sky-split-view-workspace-footer>
      </sky-split-view-workspace>
    </sky-split-view>
Copy

    import { Component, inject } from '@angular/core';
    import { FormBuilder, FormsModule, ReactiveFormsModule } from '@angular/forms';
    import { SkySummaryActionBarModule } from '@skyux/action-bars';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyDescriptionListModule } from '@skyux/layout';
    import { SkyRepeaterModule } from '@skyux/lists';
    import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
    import {
      SkySplitViewMessage,
      SkySplitViewMessageType,
      SkySplitViewModule,
    } from '@skyux/split-view';
    
    import { Subject } from 'rxjs';
    
    interface WorkspaceItem {
      id: number;
      amount: number;
      date: string;
      vendor: string;
      receiptImage: string;
      approvedAmount: number;
      comments: string;
    }
    
    @Component({
      selector: 'app-split-view-page-content',
      templateUrl: './split-view-page-content.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyDescriptionListModule,
        SkyInputBoxModule,
        SkyRepeaterModule,
        SkySplitViewModule,
        SkySummaryActionBarModule,
      ],
    })
    export class SplitViewPageContentComponent {
      protected set activeIndex(value: number) {
        this.#_activeIndex = value;
        this.activeRecord = this.items[this.#_activeIndex];
        this.#loadFormGroup(this.activeRecord);
      }
    
      protected get activeIndex(): number {
        return this.#_activeIndex;
      }
    
      protected items: WorkspaceItem[] = [
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
    
      protected activeRecord = this.items[0];
      protected listWidth: number | undefined;
      protected splitViewStream = new Subject<SkySplitViewMessage>();
    
      protected splitViewDemoForm = inject(FormBuilder).group({
        approvedAmount: [this.activeRecord.approvedAmount],
        comments: [this.activeRecord.comments],
      });
    
      #_activeIndex = 0;
    
      #confirmSvc = inject(SkyConfirmService);
    
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
    
      #loadFormGroup(record: WorkspaceItem): void {
        this.splitViewDemoForm.setValue({
          approvedAmount: record.approvedAmount,
          comments: record.comments,
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
            if (closeArgs.action === 'yes') {
              this.#saveForm();
            }
    
            this.#loadWorkspace(index);
          });
      }
    
      #saveForm(): void {
        this.activeRecord = Object.assign(
          this.activeRecord,
          this.splitViewDemoForm.value,
        );
    
        this.splitViewDemoForm.markAsPristine();
      }
    
      #setFocusInWorkspace(): void {
        this.splitViewStream.next({
          type: SkySplitViewMessageType.FocusWorkspace,
        });
      }
    }

Copy

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
### Data manager with split view in a fit layout page.

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

    <sky-page layout="fit">
      <sky-page-header pageTitle="Split view with data manager" />
      <sky-page-content>
        <sky-data-manager [dock]="dock">
          <sky-data-manager-toolbar />
          <sky-data-view viewId="dataManagerView">
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
    
              <sky-split-view-workspace ariaLabel="Transaction form">
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
                        <sky-description-list-term>
                          Date
                        </sky-description-list-term>
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
          </sky-data-view>
        </sky-data-manager>
      </sky-page-content>
    </sky-page>
Copy

    import { HarnessLoader } from '@angular/cdk/testing';
    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { provideNoopAnimations } from '@angular/platform-browser/animations';
    import { SkyDataManagerHarness } from '@skyux/data-manager/testing';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    import { SkyRepeaterHarness } from '@skyux/lists/testing';
    import { SkyPageHarness } from '@skyux/pages/testing';
    import { SkySplitViewHarness } from '@skyux/split-view/testing';
    
    import { PagesPageDataManagerSplitViewFitLayoutExampleComponent } from './example.component';
    
    describe('Data manager with split view in a fit layout page example', () => {
      async function setupTest(): Promise<{
        fixture: ComponentFixture<PagesPageDataManagerSplitViewFitLayoutExampleComponent>;
        loader: HarnessLoader;
        component: PagesPageDataManagerSplitViewFitLayoutExampleComponent;
      }> {
        await TestBed.configureTestingModule({
          imports: [PagesPageDataManagerSplitViewFitLayoutExampleComponent],
          providers: [provideNoopAnimations()],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          PagesPageDataManagerSplitViewFitLayoutExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const component = fixture.componentInstance;
    
        return { fixture, loader, component };
      }
    
      it('should create the component', async () => {
        const { fixture, component } = await setupTest();
    
        fixture.detectChanges();
    
        expect(component).toBeTruthy();
      });
    
      it('should have correct page layout', async () => {
        const { fixture, loader } = await setupTest();
    
        fixture.detectChanges();
    
        const pageHarness = await loader.getHarness(SkyPageHarness);
        await expectAsync(pageHarness.getLayout()).toBeResolvedTo('fit');
      });
    
      it('should initialize with first item selected', async () => {
        const { fixture, component } = await setupTest();
    
        fixture.detectChanges();
    
        expect(component.activeIndex).toBe(0);
        expect(component.activeRecord).toEqual(component.items[0]);
      });
    
      it('should set up data manager with correct configuration', async () => {
        const { fixture, loader } = await setupTest();
    
        fixture.detectChanges();
    
        const dataManagerHarness = await loader.getHarness(SkyDataManagerHarness);
    
        // Verify dock type is 'fill'
        await expectAsync(dataManagerHarness.getDockType()).toBeResolvedTo('fill');
    
        // Get the data view
        const dataView = await dataManagerHarness.getView({
          viewId: 'dataManagerView',
        });
        expect(dataView).toBeTruthy();
      });
    
      it('should set up split view with correct configuration', async () => {
        const { fixture, loader } = await setupTest();
    
        fixture.detectChanges();
    
        const splitViewHarness = await loader.getHarness(SkySplitViewHarness);
    
        // Verify dock type is 'fill'
        await expectAsync(splitViewHarness.getDockType()).toBeResolvedTo('fill');
    
        // Verify both drawer and workspace are visible
        await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
          true,
        );
        await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
          true,
        );
    
        // Get drawer and workspace harnesses
        const drawerHarness = await splitViewHarness.getDrawer();
        const workspaceHarness = await splitViewHarness.getWorkspace();
    
        // Verify aria labels
        await expectAsync(drawerHarness.getAriaLabel()).toBeResolvedTo(
          'Transaction list',
        );
        await expectAsync(workspaceHarness.getAriaLabel()).toBeResolvedTo(
          'Transaction form',
        );
      });
    
      it('should display repeater items in the drawer', async () => {
        const { fixture, loader, component } = await setupTest();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        const splitViewHarness = await loader.getHarness(SkySplitViewHarness);
        const drawerHarness = await splitViewHarness.getDrawer();
    
        // Get the repeater harness from the drawer
        const repeaterHarness =
          await drawerHarness.queryHarness(SkyRepeaterHarness);
        expect(repeaterHarness).toBeTruthy();
    
        // Verify all items are displayed
        const repeaterItems = await repeaterHarness.getRepeaterItems();
        expect(repeaterItems.length).toBe(4);
    
        // Verify the active index is properly set in the component (first item should be active initially)
        expect(component.activeIndex).toBe(0);
      });
    
      it('should display form fields in the workspace', async () => {
        const { fixture, loader, component } = await setupTest();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        const splitViewHarness = await loader.getHarness(SkySplitViewHarness);
        const workspaceHarness = await splitViewHarness.getWorkspace();
        const contentHarness = await workspaceHarness.getContent();
    
        // Get input box harnesses
        const inputBoxes = await contentHarness.queryHarnesses(SkyInputBoxHarness);
        expect(inputBoxes.length).toBe(2);
    
        // Verify the input labels
        await expectAsync(inputBoxes[0].getLabelText()).toBeResolvedTo(
          'Approved amount',
        );
        await expectAsync(inputBoxes[1].getLabelText()).toBeResolvedTo('Comments');
    
        // Verify initial values match the first item using form controls
        const approvedAmountControl =
          component.splitViewDemoForm.controls.approvedAmount;
        const commentsControl = component.splitViewDemoForm.controls.comments;
    
        expect(approvedAmountControl.value).toBe(73.19);
        expect(commentsControl.value).toBe('');
      });
    
      it('should switch active record when clicking repeater items', async () => {
        const { fixture, loader, component } = await setupTest();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        const splitViewHarness = await loader.getHarness(SkySplitViewHarness);
        const drawerHarness = await splitViewHarness.getDrawer();
        const repeaterHarness =
          await drawerHarness.queryHarness(SkyRepeaterHarness);
        const repeaterItems = await repeaterHarness.getRepeaterItems();
    
        // Verify initial state
        expect(component.activeIndex).toBe(0);
        expect(component.activeRecord.id).toBe(1);
    
        // Click on the second item (index 1)
        await repeaterItems[1].click();
        fixture.detectChanges();
        await fixture.whenStable();
    
        // Verify the active record changed
        expect(component.activeIndex).toBe(1);
        expect(component.activeRecord.id).toBe(2);
        expect(component.activeRecord.vendor).toBe('Office Max');
    
        // Verify form was updated with new record data
        const approvedAmountControl =
          component.splitViewDemoForm.controls.approvedAmount;
        const commentsControl = component.splitViewDemoForm.controls.comments;
    
        expect(approvedAmountControl.value).toBe(214.12);
        expect(commentsControl.value).toBe('');
      });
    
      it('should update form when editing form fields', async () => {
        const { fixture, component } = await setupTest();
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        // Get form controls
        const approvedAmountControl =
          component.splitViewDemoForm.controls.approvedAmount;
        const commentsControl = component.splitViewDemoForm.controls.comments;
    
        // Verify initial values
        expect(approvedAmountControl.value).toBe(73.19);
        expect(commentsControl.value).toBe('');
        expect(component.splitViewDemoForm.dirty).toBe(false);
    
        // Update form values - setValue() doesn't mark form as dirty, so we need to mark it explicitly
        approvedAmountControl.setValue(100.0);
        approvedAmountControl.markAsDirty();
        commentsControl.setValue('Test comment');
        commentsControl.markAsDirty();
    
        fixture.detectChanges();
    
        // Verify form is dirty after changes
        expect(component.splitViewDemoForm.dirty).toBe(true);
    
        // Verify new values
        expect(approvedAmountControl.value).toBe(100.0);
        expect(commentsControl.value).toBe('Test comment');
      });
    });
Copy

    export interface Record {
      id: number;
      amount: number;
      date: string;
      vendor: string;
      receiptImage: string;
      approvedAmount: number;
      comments: string;
    }

Copy

    import { Component, OnInit, inject } from '@angular/core';
    import {
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkySummaryActionBarModule } from '@skyux/action-bars';
    import {
      SkyDataManagerDockType,
      SkyDataManagerModule,
      SkyDataManagerService,
      SkyDataManagerState,
      SkyDataViewConfig,
    } from '@skyux/data-manager';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyDescriptionListModule } from '@skyux/layout';
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
     * @title Data manager with split view in a fit layout page.
     * @docsDemoHidden
     */
    @Component({
      selector: 'app-pages-page-split-view-data-manager-example',
      templateUrl: './example.component.html',
      imports: [
        SkyPageModule,
        SkyDataManagerModule,
        FormsModule,
        ReactiveFormsModule,
        SkyDescriptionListModule,
        SkyInputBoxModule,
        SkyRepeaterModule,
        SkySplitViewModule,
        SkySummaryActionBarModule,
      ],
      providers: [SkyDataManagerService],
    })
    export class PagesPageDataManagerSplitViewFitLayoutExampleComponent
      implements OnInit
    {
      public set activeIndex(value: number) {
        this.#_activeIndex = value;
        this.activeRecord = this.items[this.#_activeIndex];
        this.#loadFormGroup(this.activeRecord);
      }
    
      public get activeIndex(): number {
        return this.#_activeIndex;
      }
    
      public items = [
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
      ];
    
      public activeRecord: Record;
      public splitViewDemoForm: FormGroup<DemoForm>;
      public splitViewStream = new Subject<SkySplitViewMessage>();
    
      public dock: SkyDataManagerDockType = 'fill';
    
      #splitViewConfig: SkyDataViewConfig = {
        id: 'dataManagerView',
        name: 'Split View Data Manager View',
        sortEnabled: true,
        searchEnabled: true,
      };
    
      #_activeIndex = 0;
    
      readonly #dataManagerService = inject(SkyDataManagerService);
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
    
      public ngOnInit(): void {
        this.#dataManagerService.initDataManager({
          activeViewId: 'dataManagerView',
          dataManagerConfig: {},
          defaultDataState: new SkyDataManagerState({
            views: [
              {
                viewId: 'dataManagerView',
              },
            ],
          }),
        });
        this.#dataManagerService.initDataView(this.#splitViewConfig);
      }
    
      public onItemClick(index: number): void {
        // Prevent workspace from loading new data if the current workspace form is dirty.
        if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
          this.#openConfirmModal(index);
        } else {
          this.#loadWorkspace(index);
        }
      }
    
      public onApprove(): void {
        console.log('Approved clicked!');
        this.#saveForm();
      }
    
      public onDeny(): void {
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
        this.activeRecord.approvedAmount =
          this.splitViewDemoForm.value.approvedAmount ?? 0;
        this.activeRecord.comments = this.splitViewDemoForm.value.comments ?? '';
    
        this.splitViewDemoForm.reset(this.splitViewDemoForm.value);
      }
    
      #setFocusInWorkspace(): void {
        const message: SkySplitViewMessage = {
          type: SkySplitViewMessageType.FocusWorkspace,
        };
        this.splitViewStream.next(message);
      }
    }

# Testing

                  Skip to Main Content

 Page
====

Pages provide consistent, responsive containers for common page layouts.

 Usage
------

### Use when

Use pages to apply consistent background colors and standardized layouts to all pages.

### Don't use when

Don't use pages in modals.

 Anatomy
--------

### Standard heading without page links

1

Header

2

Heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

[Avatar](/skyux/components/avatar.md) (optional)

6

Details (optional)

7

Actions (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-heading.0f513db7d271182cea483e6ecae854ca.png)

### Hub and spoke heading with page links

1

Header

2

Hub and spoke heading

3

Content area

4

[Alert](/skyux/components/alert.md) (optional)

5

Details (optional)

6

Actions (optional)

7

Page links area (optional)

8

Recently accessed link list (optional)

9

Page link list (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-anatomy-hub.f9e8a05879794ae622f087a03d19b4cd.png)

 Options
--------

### Layouts

#### Blocks

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md), use the `blocks` layout to organize content into modular blocks. For a wide range of possible layouts, place a [fluid grid](/skyux/components/fluid-grid.md) or another grid layout via flexbox or CSS grid in the content area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-blocks-layout.76f82ea0c799d06acf73237b9266995e.png)

#### List

For [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `list` layout to display lists of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-list-layout.6a565c1ad637e53a00eea686b207b8a7.png)

#### Tabs

For [record pages](/skyux/design/guidelines/page-layouts/record-page.md) or [list pages](/skyux/design/guidelines/page-layouts/list-page.md), use the `tabs` layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see [tabs](/skyux/components/tabs.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-tabs-layout.cd00761effd67b07f9163f9dca6c9c52.png)

#### Fit

For [split view pages](/skyux/design/guidelines/page-layouts/split-view-page.md), use the `fit` layout to fill the content area and anchor content to the edges.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-fit-layout.2deadebc41c1f7f0e8e8cc83f1aed4d0.png)

#### None

For custom content that doesn't work well with predefined layouts or spacing, use the `none` layout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-none-layout.4a100252343c541041581837fd7b9eb4.png)

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

#### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-heading.62580a83a844948a6b1e8e75d4f4b406.png)

Page headings descibe the content on pages.

#### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke.f706d1d121110c699ad87ab958a8d51c.png)

Hub and spoke navigation connects child pages to a single parent hub page.

Hub

Hubs are parent pages with links to child pages that users can only navigate to from the hub. None found.

Spoke

Spokes are child pages that users only navigate to from a hub. Don't use hub and spoke heading when users can navigate to a child page from multiple places. None found.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-spoke-diagram.4929796f70eeb8a3415c59e2ee377a42.png)

The hub and spoke pattern connects a parent hub page to child spoke pages. Users navigate to spokes from the hub.

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-breadcrumb-dont.458dc4831b8a02f26ad2b6fe293bede6.png)

Don't go more than one level deep in hub and spoke headings.

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use [tabs](/skyux/components/tabs.md) to group large amounts of content within a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/hub-record-dont.ce87f18a349fc58e9cf133cb03d4ff82.png)

Don't use the hub and spoke pattern to connect a record page to its child pages.

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an [alert](/skyux/components/alert.md) in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) [avatar](/skyux/components/avatar.md) in the top left of [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

### Page links

#### Link lists

For `blocks` layout pages, you can add link lists for navigation in a way that is similar to [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md). Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's [Content guidelines](/skyux/design/guidelines/page-layouts/action-hub#section-content.md).

#### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-links-home.072443de8a2e9e96b37fdd3706ada2d0.png)

Page links provide navigation to other pages or tasks from a page.

#### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness [behaviors](/skyux/components/page#section-behaviors-and-states.md) below.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/page-page-links-layout.b22d6d87b0ba15518d15682fc93e2167.png)

Page link lists are positioned to the right of the page content.

 Behaviors and states
---------------------

### Responsiveness

Page layouts reflow content at the `xs` breakpoint of 767px.

![Blocks layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-blocks.bc588a127d94b27ec442496fcf02f456.png)

![List layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-list.d11e67ec7ac52ea211ee882b5acd0c28.png)

![Tabs layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-tabs.a05d5c647e4c54d3e35ab4aead6e840d.png)

![Fit layout in small viewport](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/page/xs-page-layout-fit.ed1a9f74d40c7a3d68321a70f62fef52.png)

 Related information
--------------------

### Guidelines

*   [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)
*   [Buttons and links](/skyux/design/guidelines/buttons-links.md)
*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

### Components

*   [Alert](/skyux/components/alert.md)
*   [Avatar](/skyux/components/avatar.md)
*   [Buttons](/skyux/components/button.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

 Installation
-------------

NPM package

`@skyux/pages`[View in NPM](https://www.npmjs.com/package/@skyux/pages) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/pages/src/lib/modules/page/page.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/pages`Copy None found.

 SkyPageModule
--------------

Type: Module

`import { SkyPageModule } from '@skyux/pages';`

 SkyPageComponent
-----------------

Type: Component

Selector: `sky-page`

Displays a page using the specified layout. The page component is a responsive container, meaning content will respect the breakpoints within the page element instead of the window. This is helpful if there is other content to the left or right of the page.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the page's default [global help](/skyux/learn/develop/global-help.md) content to display.

#### `layout: InputSignal<SkyPageLayoutType>`

The page layout that applies spacing to the page header and content. Use the layout that corresponds with the top-level component type used on the page, or use `fit` to constrain the page contents to the available viewport. Use `none` for custom content that does not adhere to predefined spacing or constraints.

Default: `"none"`

 SkyPageContentComponent
------------------------

Type: Component

Selector: `sky-page-content`

Displays page contents using spacing that corresponds to the parent page's layout.

 SkyPageLinksComponent
----------------------

Type: Component

Selector: `sky-page-links`

Displays page links on the right side of the page, or below the page content on mobile devices.

 SkyPageLayoutType
------------------

Type: Type alias

    type SkyPageLayoutType = "none" | "fit" | "blocks" | "list" | "tabs"

 SkyPageHeaderModule
--------------------

Type: Module

`import { SkyPageHeaderModule } from '@skyux/pages';`

 SkyPageHeaderComponent
-----------------------

Type: Component

Selector: `sky-page-header`

Displays page heading's contents using spacing that corresponds to the parent page's layout

### Inputs

#### `pageTitle: string | undefined`

The title of the current page.

#### `parentLink: SkyPageLink | undefined`

A link to the parent page of the current page.

 SkyPageHeaderDetailsComponent
------------------------------

Type: Component

Selector: `sky-page-header-details`

Displays additional information in the page header, like record details. Appears below the title and above the page actions.

 SkyPageHeaderActionsComponent
------------------------------

Type: Component

Selector: `sky-page-header-actions`

Displays buttons within the page header for page actions and applies spacing between buttons. Appears below the page header details.

 SkyPageHeaderAlertsComponent
-----------------------------

Type: Component

Selector: `sky-page-header-alerts`

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

 SkyPageHeaderAvatarComponent
-----------------------------

Type: Component

Selector: `sky-page-header-avatar`

Displays an avatar within the page header to the left of the page title. If no size is specified for the avatar component it will display at size small on xs breakpoints and size large on small and above breakpoints.

 SkyPageLink
------------

Type: Interface

Displays links to related information or recently accessed items.

    interface SkyPageLink {
      label: string;
      permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string };
    }

### Properties

#### `label: string`

The link text.

#### `permalink: { route?: { commands: any[]; extras?: NavigationExtras }; url?: string }`

The link destination.

 SkyPageLinksInput
------------------

Type: Type alias

    type SkyPageLinksInput = SkyPageLink[] | "loading" | undefined

 SkyLinkListModule
------------------

Type: Module

`import { SkyLinkListModule } from '@skyux/pages';`

 SkyLinkListComponent
---------------------

Type: Component

Selector: `sky-link-list`

A component that displays a list of links, such as within a `<sky-page-links>` component.

### Inputs

#### `headingText: InputSignal<undefined | string>`

The text to display as the list's heading.

#### `links: InputSignal<SkyPageLinksInput>`

Option to pass links as an array of `SkyPageLink` objects or `'loading'` to display a loading indicator.

 SkyLinkListItemComponent
-------------------------

Type: Component

Selector: `sky-link-list-item`

A wrapper for each link in a link list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPageHarness
---------------

Type: Class

`import { SkyPageHarness } from '@skyux/pages/testing';`

Harness for interacting with a page component in tests.

### Methods

#### `getLayout(): Promise<SkyPageLayoutType>`

Gets the current layout.

#### Returns

`Promise<SkyPageLayoutType>`

#### `getPageHeader(filters?: SkyPageHeaderHarnessFilters): Promise<SkyPageHeaderHarness>`

Gets the first page header that matches the given filters.

#### Parameters

##### `filters?: SkyPageHeaderHarnessFilters`

filters for which page header to return

#### Returns

`Promise<SkyPageHeaderHarness>`

#### `SkyPageHarness.with(filters: SkyPageHarnessFilters): HarnessPredicate<SkyPageHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHarness>`

 SkyPageHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHarness](/skyux/components/page?docs-active-tab=testing#class_sky-page-harness.md) instances.

    interface SkyPageHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPageHeaderHarness
---------------------

Type: Class

`import { SkyPageHeaderHarness } from '@skyux/pages/testing';`

Harness for interacting with a page header component in tests.

### Methods

#### `getPageTitle(): Promise<undefined | string>`

Gets the current page title.

#### Returns

`Promise<undefined | string>`

#### `getParentLinkText(): Promise<string>`

Gets the current page title.

#### Returns

`Promise<string>`

#### `SkyPageHeaderHarness.with(filters: SkyPageHeaderHarnessFilters): HarnessPredicate<SkyPageHeaderHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPageHeaderHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPageHeaderHarnessFilters`

#### Returns

`HarnessPredicate<SkyPageHeaderHarness>`

 SkyPageHeaderHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPageHeaderHarness](/skyux/components/page?docs-active-tab=testing#class_sky-page-header-harness.md) instances.

    interface SkyPageHeaderHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListHarness
-------------------

Type: Class

`import { SkyLinkListHarness } from '@skyux/pages/testing';`

Harness for interacting with a link list component in tests.

### Methods

#### `getHeadingText(): Promise<undefined | string>`

Gets the link list's heading text. If there are no links, this will return `undefined`.

#### Returns

`Promise<undefined | string>`

#### `getListItem(filter: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness>`

Gets a specific link list item based on the filter criteria.

#### Parameters

##### `filter: SkyLinkListItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness>`

#### `getListItems(filter?: SkyLinkListItemHarnessFilters): Promise<SkyLinkListItemHarness[]>`

Gets an array of link list items based on the filter criteria. If no filter is provided, returns all link list items.

#### Parameters

##### `filter?: SkyLinkListItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyLinkListItemHarness[]>`

#### `isVisible(): Promise<boolean>`

Whether the link list is showing a list of links.

#### Returns

`Promise<boolean>`

#### `isWaiting(): Promise<boolean>`

Gets the status of the wait indicator.

#### Returns

`Promise<boolean>`

#### `SkyLinkListHarness.with(filters: SkyLinkListHarnessFilters): HarnessPredicate<SkyLinkListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListHarness>`

 SkyLinkListHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListHarness](/skyux/components/page?docs-active-tab=testing#class_sky-link-list-harness.md) instances.

    interface SkyLinkListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLinkListItemHarness
-----------------------

Type: Class

`import { SkyLinkListItemHarness } from '@skyux/pages/testing';`

Harness for interacting with a linked list item in tests.

### Methods

#### `click(): Promise<void>`

Clicks the item.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the text content of the item.

#### Returns

`Promise<string>`

#### `SkyLinkListItemHarness.with(filters: SkyLinkListItemHarnessFilters): HarnessPredicate<SkyLinkListItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLinkListItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLinkListItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyLinkListItemHarness>`

 SkyLinkListItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyLinkListItemHarness](/skyux/components/page?docs-active-tab=testing#class_sky-link-list-item-harness.md) instances.

    interface SkyLinkListItemHarnessFilters {
      dataSkyId?: string | RegExp;
      text?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `text?: string`

Only find instances whose text content matches the given value.
                  

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
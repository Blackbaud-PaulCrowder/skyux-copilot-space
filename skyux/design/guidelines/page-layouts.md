             Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Page design](/skyux/design/guidelines/page-layouts.md)

Page design
===========

Page design patterns accommodate a wide variety scenarios and workflow requirements to facilitate consistent, cohesive user experiences.

On this page
============

1.  [Page patterns](/skyux/design/guidelines/page-layouts#page-patterns.md)
2.  [Page titles](/skyux/design/guidelines/page-layouts#page-titles.md)
3.  [Fluid grid system](/skyux/design/guidelines/page-layouts#fluid-grid-system.md)
4.  [Responsive design](/skyux/design/guidelines/page-layouts#responsive-design.md)
5.  [Primary button guidelines](/skyux/design/guidelines/page-layouts#primary-button-guidelines.md)

[

Page patterns
-------------

](/skyux/design/guidelines/page-layouts#page-patterns.md)

While you can use SKY UX to create any page layout you need, Blackbaud solutions utilize on some common page patterns.

[![Action hub illustration](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/action-hub-layout.a3aced5c70d6498e074343cb5d92770d.png)](/skyux/design/guidelines/page-layouts/action-hub.md)

### [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)

Direct users to important actions and provide quick access to common tasks.

[![List page illustration](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page-layout.aeeabfcee757924d6d60b5e1a1e52658.png)](/skyux/design/guidelines/page-layouts/list-page.md)

### [List page](/skyux/design/guidelines/page-layouts/list-page.md)

Present a list for users to review and search, and enable users to manipulate list items.

[![Record page illustration](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page-layout.bdbfc8a78850bbe4effad5bd161b6708.png)](/skyux/design/guidelines/page-layouts/record-page.md)

### [Record page](/skyux/design/guidelines/page-layouts/record-page.md)

Aggregate tasks and content related to a particular record.

[![Split view page illustration](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/split-view-layout.b0788358dbc27cb50ac89298a819e19c.png)](/skyux/design/guidelines/page-layouts/split-view-page.md)

### [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

Provide a workspace for users to quickly work through a list of items.

[

Page titles
-----------

](/skyux/design/guidelines/page-layouts#page-titles.md)

Page titles uniquely identify the contents of pages. They are concise and direct, and they indicate the purpose of the pages to get users up to speed quickly. For guidance on creating page titles, see the [Content guidelines](/skyux/design/guidelines/content#page-titles.md).

[

Fluid grid system
-----------------

](/skyux/design/guidelines/page-layouts#fluid-grid-system.md)

SKY UX layouts use a [fluid grid](/skyux/components/fluid-grid.md) system to respond to changes in the size of devices or viewports. Fluid grids provide padding on both sides of columns for consistent spacing between columns and at the edges. Columns are fluid, but spacing is constant.

This fluid grid system supports multiple page layouts and conforms to [design principles](/skyux/design/principles.md).

To organize content in fluid grids, consider the type of content and how users interact with it. On pages with dynamic or time-sensitive content, organize content containers to emphasize tasks and make the best use of space at all screen sizes. On pages that primarily display information, maintain the relative position of containers regardless of screen size.

If you hide or display content based on screen size, use layouts that ensure the correct placement at all screen sizes. Don't rely on the expected fluid grid behavior. Move the surrounding content to maintain consistent positioning and fill the available space.

When you hide a single container, content moves up within the same column. Content doesn't move when you hide a container at the bottom of a column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/container-shift-up.867ea897f6babf3fad96e06b18a0a6c1.png)

Containers in a column move up to fill space.

When you hide all containers in a column, the surrounding content moves to the left.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/container-shift-left.9cc2f8a03f15dd487c4a702c0e6dc03a.png)

Columns move left when you hide an entire column.

[

Responsive design
-----------------

](/skyux/design/guidelines/page-layouts#responsive-design.md)

We rely on the column drop pattern to create responsive designs. This pattern utilizes a multi-column layout and the full width of the screen. The column drop pattern displays columns horizontally at full width and then stacks columns vertically when the screen width becomes too narrow for the content. When and how to stack columns at different breakpoints depends on the content.

For example, a box-based page with column-based content layout responds as follows:

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/page-three-column-full.0e711dadbb81c380800fc229f1a3ee7c.png)

Large viewport

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/page-three-column-mobile.433883ef6f1df0774b187030299c0f07.png)

Small viewport

In containers, content laid out within a fluid guid will restructure as the size of the viewport changes. For example, a container with a [repeater](/skyux/components/repeater.md) responds as follows:

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/repeater-content-full.c6445aecc38324a0a903bc9b2fd924e4.png)

Large viewport

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/repeater-content-mobile.9643ab3a79e8085539eb3537b1fb5fe5.png)

Small viewport

### Responsive component behavior

Many components also respond at different breakpoints to best present page content based on screen width.

[Action buttons](/skyux/components/action-button.md) adapt their presentation at smaller viewport widths to stack vertically instead of horizontally.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/responsive-action-button.1550dee43c17b2b95b4ecb61819c2f9b.png)

[Tabs](/skyux/components/tabs.md) collapse into a dropdown when the number of tabs exceeds the available horizontal space.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/responsive-tabs.35949c688a864d3bbd7c8e437211b4f0.png)

Horizontal [description lists](/skyux/components/description-list.md) respond to the width of their containers and change to 1- or 2-column layouts when appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/responsive-description-list-full.af8d696eaa17d967a73d3640edf970ed.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/responsive-description-list-two-column.03a8f775ef311e6000a2eff292ce423f.png)

[

Primary button guidelines
-------------------------

](/skyux/design/guidelines/page-layouts#primary-button-guidelines.md)

All SKY UX page layouts follow consistent guidelines for the placement and styling of primary buttons.

Usage

Use a primary action to trigger the most important or most frequently used action on a page or modal. If the action applies to an entire page, place the button in the page header. If the action applies to child content, place the button in the container for that content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-usage-page-level.d41f8d7366756aae876a6f206592774a.png)

Do use primary buttons in the containers that they directly impact.

Don't use multiple primary actions. Pages and modals only include one primary button to ensure that it draws user attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-usage-dont-multiple-actions.f47781d38e22b21d45a75093975aa95e.png)

Don't use multiple primary buttons.

Don't use multiple primary buttons when users have multiple options to complete a primary action. Instead, use [action buttons](/skyux/components/action-button.md) to present the initial decision.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-usage-dont-multiple-ways.d337e49da27f69f10ad9f66f2283a0ab.png)

Don't use multiple primary buttons to present options.

Don't use primary buttons when pages and modals don't have a most important or most frequently used action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-usage-no-primary.ae6fef2ce7f2041992af75fa7d0dba97.png)

Some pages don't have a primary action.

Placement

For a list page where the primary action applies to list items, place the primary action in the summary action bar that appears when users select list items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-list-multiselect.4e6ae5fb45895965cf38db0b67b7961d.png)

Do place a primary action that applies to list items in the summary action bar.

For a record page, place the primary action to the left of the other actions under the page title.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-record.47fc89fc8dd131c9a712451f9857a538.png)

Do place the primary action to the left of the page actions on a record page.

For a split view page, place the primary action in the summary action bar below the split view workspace.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-split-view.4cde9507589b34ccef1d036b5b4b95fb.png)

Do place the primary action in the summary action bar below the split view workspace.

Don't place a primary action on an action hub page. Action hubs use other patterns such as the Needs attention section to direct users to important actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-action-hub.cc1ec4a85198ee8dfcd91e1ae2ea11d7.png)

Don't place a primary action on an action hub page.

Don't place a primary action in the list toolbar on a list page. List pages are not recommended for completing predictable tasks and do not suggest any particular action in the list toolbar.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/primary-list-toolbar.a9130d3157d874c8c00fefb1e4971778.png)

Don't place a primary action in the list toolbar.
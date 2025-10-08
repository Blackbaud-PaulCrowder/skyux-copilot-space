             Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Page design](/skyux/design/guidelines/page-layouts.md)
5.  [List page](/skyux/design/guidelines/page-layouts/list-page.md)

List page
=========

List pages allow the user to filter, sort, search and take action on lists of items.

[

Usage
-----

](/skyux/design/guidelines/page-layouts/list-page#usage.md)

### Use when

Use list pages when users need to work with an item or collection of items and you can't otherwise provide a first-class experience for the task.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-page-use-when.700f9a6fee8d5750e5caa57dcae3aeea.png)

Do use list pages when users need to work with a set, subset or individual item.

### Don't use when

Don't use list pages when you can predict what users need to do and can provide a first-class experience for that task.

[

Anatomy
-------

](/skyux/design/guidelines/page-layouts/list-page#anatomy.md)

1

[Page](/skyux/components/page.md)

2

Page heading

3

List

4

[Pagination](/skyux/components/paging.md)

5

[Tabs](/skyux/components/tabs.md) (optional)

6

View switcher  (optional)

7

[Toolbar](/skyux/components/toolbar.md) (optional)

8

[Filter bar](/skyux/design/guidelines/filtering-lists.md) (optional)

9

Summary details (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-page-anatomy.d162aa04033f3a1544bec6eef766dd65.png)

[

Options
-------

](/skyux/design/guidelines/page-layouts/list-page#options.md)

### Tabs

You can use [tabs](/skyux/components/tabs.md) to provide [pre-filtered views of lists](/skyux/design/guidelines/filtering-lists#pre-filtering-full-page-lists.md) to support common tasks. Only provide pre-filtered views if there will always be items in those views.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-page-options-tabs.5f91251d1111b81c8fd7021490e8cc98.png)

You can use tabs to provide pre-filtered views of lists.

### View switcher

The view switcher lets users control how to display a list. They can display it as a [data grid](/skyux/components/data-grid.md), [repeater](/skyux/components/repeater.md), or map. The view switcher is made from the [icon radio buttons](/skyux/components/radio.md) component.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-view-switcher.dec8b3825a3862ecadf47f1f5cbe5054.png)

### Toolbar

The [toolbar](/skyux/components/toolbar.md) displays actions to manipulate individual list items or the entire list. Don't include a primary action in list toolbars. If the page supports a specific, predictable workflow, consider using a different [page layout, such as action hubs or split view pages](/skyux/design/guidelines/page-layouts#page-layouts.md).

### Filter bar

The [filter bar](/skyux/design/guidelines/filtering-lists.md) enables users to adjust lists to only display the items that match their specific criteria.

### Summary details

Use [small key info components](/skyux/components/key-info.md) to highlight important information about lists that users should know at a glance. Use the first key info component to indicate the number of items in the list. Most lists should include this list count.

To assist users with their tasks, you can display up to two additional summary items to the right of the list count. For example, in a list of gifts, you can highlight the total amount of all gifts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-count.8378fb30e0a7146555fbb94e560aa67b.png)

Do include a list count and optionally up to two other key info items as summary details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-count-summaries.a458ebdfe3ff80c93a95e8ec31df0dcb.png)

Don't include data in the summary details that doesn't help users interpret lists.

Don't display a list count when a list of fewer than 15 items is unlikely to change.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-count-small-fixed-list.732b2a92852843beca2b09d4d0a6b513.png)

Don't display a list count when a list is small and unlikely to change.

#### Updates to summary details

When filters or search criteria are applied to a list, update the list count and summary details to reflect the filtered list. Add “match” to the list count label to reflect the list is in a filtered state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-count-filtered.3ab2c3792e6df8ec1b60fb8eeb59ac4d.png)

Do update summary details when filters or search criteria are applied to a list. To provide context, update the list count label to include 'match.'

[

Behavior and states
-------------------

](/skyux/design/guidelines/page-layouts/list-page#behavior-and-states.md)

### Links to records

Links to records in the list should navigate users to the record page.

### Pagination

Use pagination with 30 items per page to divide up lists. Don't use infinite scroll.

[

Content
-------

](/skyux/design/guidelines/page-layouts/list-page#content.md)

### Tab label

The tab should only include the descriptive label. Do not include the list count in the tab.

[

Layout
------

](/skyux/design/guidelines/page-layouts/list-page#layout.md)

### List page with a single list

1.  [Page](/skyux/design/guidelines/page-layouts/list-page/components/page.md) using `list` layout.
2.  `sky-margin-stacked-xs` class included on the toolbar with filters before summary details.
3.  `sky-margin-stacked-sm` class included on the summary details area.
4.  `sky-padding-horizontal-sm` class included on the summary details area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-page-list-layout.ffdbec48ee827dfa7a9cc24940e31f4a.png)

### List page with multiple lists in tabs

1.  [Page](/skyux/design/guidelines/page-layouts/list-page/components/page.md) using `tabs` layout.
2.  `sky-margin-stacked-xs` class included on the toolbar with filters before summary details.
3.  `sky-margin-stacked-sm` class included on the summary details area.
4.  `sky-padding-horizontal-sm` class included on the summary details area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/list-page/list-page-tabs-layout.e08a98de0ab19dcd0703b912e4f5d8e9.png)

[

Related information
-------------------

](/skyux/design/guidelines/page-layouts/list-page#related-information.md)

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Page](/skyux/components/page.md)
*   [Repeater](/skyux/components/repeater.md)
*   [Tabs](/skyux/components/tabs.md)
*   [Toolbar](/skyux/components/toolbar.md)

### Guidelines

*   [Filtering lists](/skyux/design/guidelines/filtering-lists.md)
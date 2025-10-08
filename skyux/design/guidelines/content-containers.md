            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Content containers](/skyux/design/guidelines/content-containers.md)

Content containers
==================

On this page
============

1.  [Divide a page into sections of related content](/skyux/design/guidelines/content-containers#divide-a-page-into-sections-of-related-content.md)
2.  [Present instances of a collection of related items](/skyux/design/guidelines/content-containers#present-instances-of-a-collection-of-related-items.md)
3.  [Reveal content that is not always visible](/skyux/design/guidelines/content-containers#reveal-content-that-is-not-always-visible.md)

[

Divide a page into sections of related content
----------------------------------------------

](/skyux/design/guidelines/content-containers#divide-a-page-into-sections-of-related-content.md)

For more information about using containers, see the [page design guidelines](/skyux/design/guidelines/page-layouts.md).

### [Tab](/skyux/components/tabs.md)

Tabs organize large subsets of page content into categories. [Record pages](/skyux/design/guidelines/page-layouts/record-page.md) use tabs to categorize content on complex records. [List pages](/skyux/design/guidelines/page-layouts/list-page.md) use tabs to display multiple related lists. Treat tabs like pages and include any other container or arrangement of content.

### [Vertical tab](/skyux/components/vertical-tabs.md)

Vertical tabs also organize large subsets of page content into categories. They perform better than horizontal tabs when space is limited or the number of categories is large. You can group vertical tabs to organize very large numbers of categories.

### [Box](/skyux/components/box.md)

Boxes group related content and actions. [Action hubs](/skyux/design/guidelines/page-layouts/action-hub.md) and [record pages](/skyux/design/guidelines/page-layouts/record-page.md) use boxes in [fluid grids](/skyux/components/fluid-grid.md) to group related information and contextual actions.

### Page section

Page sections divide pages into vertical sections using [typography](/skyux/design/styles/typography.md) and spacing. Use the `sky-font-heading-2` class and follow [spacing guidelines](/skyux/design/styles/spacing.md) to position the section heading and the content underneath it.

You can divide page sections into horizontal sections using the [fluid grid](/skyux/components/fluid-grid.md) component.

### [Tile](/skyux/components/tile.md)

Tiles are containers for content from external sources. When the contents of a page may contain many containers and the layout cannot be predetermined, tile dashboards can automatically arrange tiles and give users the flexibility to reorganize tiles to meet their needs. The Add-ins tab on [record pages](/skyux/design/guidelines/page-layouts/record-page.md) commonly uses tiles.

The content inside tiles will vary widely, and tiles can contain toolbars to house action related to their content.

[

Present instances of a collection of related items
--------------------------------------------------

](/skyux/design/guidelines/content-containers#present-instances-of-a-collection-of-related-items.md)

### [Repeater list](/skyux/components/repeater.md)

Repeater lists display lists of items that do not use columns. The content and presentation inside the row can be determined per list. Rows in a repeater list can be selected (multi-select via checkbox) for bulk actions. Each row can contain hyperlinks (usually on the “primary” label), but row-specific actions should be collected into the row's context menu.

Repeaters can be used in full-page formats, tabs, boxes, or modals.

### [Data grid](/skyux/components/data-grid.md)

Data grids list items in table format (i.e. defined columns). Content and presentation of each row and column can be determined per list, but must conform to column breakdowns. Columns can be shown/hidden/reordered, and content can be sorted based on values inside specific columns.

Data grids commonly use [data manager](/skyux/components/data-manager.md) and a [toolbar](/skyux/components/toolbar.md) to provide search, column selection, and other actions.

Use data grids in full-page formats or inside of full-page tabs. Within smaller containers such as boxes, use repeaters instead because they scale down better than data grids.

[

Reveal content that is not always visible
-----------------------------------------

](/skyux/design/guidelines/content-containers#reveal-content-that-is-not-always-visible.md)

### [Modal](/skyux/components/modal.md)

Modals focus user attention on specific tasks. Modals are appropriate in scenarios that meet one or more of these conditions:

*   Users cannot complete the task until they provide more information or make additional choices.
    
*   The task is self-contained and does not need the context of the underlying page.
    
*   The task is secondary to the purpose of the underlying page.
    
*   The task interface is too complex to fit within the container where it was invoked.
    
*   The interface where the task is invoked would be too distracting for the user to efficiently complete the task inline.
    

### [Confirmation dialog](/skyux/components/confirm.md)

Confirmation dialogs are simplified modals that focus user attention on a specific question. Confirmation dialogs are appropriate in scenarios that meet these conditions:

*   An action could be destructive or especially costly when performed by mistake.
    
*   Users needs to respond to a single question to proceed with the action.
    
*   The response to the question requires no input fields.
    

### [Flyout](/skyux/components/flyout.md)

Flyouts are non-modal containers that slide out from the side of a page and lay over page content to display large amounts of supplementary information related to user tasks. They allow users to access information without navigating to another page, and they can contain lists, record views, graphs, or other information displays. Flyouts are appropriate in these scenarios:

*   Users need to drill into an analytical insight without spawning another workflow.
    
*   Users need to drill into child records and still retain the context of the parent record.
    
*   Users need more detail about an item on a [split view page](/skyux/design/guidelines/page-layouts/split-view-page.md) list without leaving the page.
    

### [Popover](/skyux/components/popover.md)

Popovers display small chunks of contextual content that do not always need to be visible. Popovers are appropriate when:

*   Users select a button or link to display the popover, and the interaction does not change the system state.
    
*   The popover content directly relates to the user's current task.
    
*   The popover content does not require scrolling on a mobile device.
    

If the content is valuable to see most of the time, use [persistent inline help](/skyux/design/guidelines/user-assistance#persistent-inline-help.md) instead. If the amount of content requires scrolling on a mobile device, use a [flyout](/skyux/components/flyout.md) instead.

### [Toast](/skyux/components/toast.md)

Toasts show small chunks of information related to the completion of a background process. Toasts are appropriate when:

*   The user needs to know about a change in system state due to a background process.
    
*   The information is important enough to notify the user regardless of their current task or context in the system.
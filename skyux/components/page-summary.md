                 

 Page summary (deprecated)
=========================

The page summary displays critical information and actions for users to access quickly and frequently.

Page summary is deprecated in favor of [page](/skyux/components/page.md)'s `sky-page-header` component. For more information, see the [page summary deprecation instructions](/skyux/learn/develop/deprecation/page-summary.md).

 Usage
------

### Use when

Use page summary effectively by limiting the number of items included. The page summary is prime real estate on the page, and when you limit the number of items, you magnify the impact of each one.

 Options
--------

### Toolbar

Use the [toolbar component](/skyux/components/toolbar.md) a to add page summary actions in a SKY UX-themed toolbar. Only include actions that relate to the page as a whole, and exclude actions that are specific to the tiles on the page. Limit the number of actions in the toolbar. If the page summary requires many actions, re-examine the tasks and consider alternative workflows.

Display the toolbar below the page summary. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. Actions to collapse and expand all tiles on the record are docked on the right side of the toolbar.

 Content
--------

### Title and subtitle

You can display a title and subtitle in the summary to uniquely identify the page content. You can pull data for the title from multiple sources, and you can combine multiple pieces of data in the title. The data to use depends on your users and the context in which they visit the page. You can display additional information in the subtitle. For example, you can display a record's natural language name in the title and its system-generated or coded identifier in the subtitle.

### Image

You can display an image in the summary to help users identify a record or complete a core task. We recommend that you do not include images just for decorative purposes because they are likely to distract users and interfere with task completion.

### Status

You can display important status information about a page's content with labels in the status section of the page summary.

### Arbitrary content

You can highlight important information about a page's content in the key information section of the page summary. This section can display any type of content, but it generally highlights a key information block such as important summary numbers.

### Alert

You can display messages that require immediate attention as alerts within the page summary. For example, you can display system-generated messages when certain criteria are met.

 Related information
--------------------

### Components

*   [Toolbar](/skyux/components/toolbar.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/page-summary/page-summary.module.ts#L39) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyPageSummaryModule
---------------------

Type: Module

`import { SkyPageSummaryModule } from '@skyux/layout';`

Warning: **Deprecated.** `SkyPageSummaryModule` is deprecated. For page templates and techniques to summarize page content, see the page design guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/page-layouts](/skyux/design/guidelines/page-layouts.md).

 SkyPageSummaryComponent
------------------------

Type: Component

Selector: `sky-page-summary`

Warning: **Deprecated.** `SkyPageSummaryComponent` is deprecated. For page templates and techniques to summarize page content, see the page design guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/page-layouts](/skyux/design/guidelines/page-layouts.md).

Specifies the components to display in the page summary.

 SkyPageSummaryTitleComponent
-----------------------------

Type: Component

Selector: `sky-page-summary-title`

Specifies a title to identify the page content.

 SkyPageSummarySubtitleComponent
--------------------------------

Type: Component

Selector: `sky-page-summary-subtitle`

Specifies a subtitle to identify the page content.

 SkyPageSummaryAlertComponent
-----------------------------

Type: Component

Selector: `sky-page-summary-alert`

Displays messages that require immediate attention as [alerts](/skyux/components/alert.md) within the page summary.

 SkyPageSummaryContentComponent
-------------------------------

Type: Component

Selector: `sky-page-summary-content`

Displays content in the arbitrary section of the page summary.

 SkyPageSummaryImageComponent
-----------------------------

Type: Component

Selector: `sky-page-summary-image`

Displays an image in the page summary to identify a record or help users complete a core task.

 SkyPageSummaryKeyInfoComponent
-------------------------------

Type: Component

Selector: `sky-page-summary-key-info`

Highlights important information about a page in the key information section of the page summary.

 SkyPageSummaryStatusComponent
------------------------------

Type: Component

Selector: `sky-page-summary-status`

Displays [labels](/skyux/components/label.md) to highlight important status information about a page's content.
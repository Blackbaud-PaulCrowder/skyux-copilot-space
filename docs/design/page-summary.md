---
component: 'page-summary'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the page-summary component extracted from SKY UX documentation.'
---

# Page Summary Design Guidelines

## Component Overview
The page summary displays critical information and actions for users to access quickly and frequently. Page summary is deprecated in favor of page's sky-page-header component. For more information, see the page summary deprecation instructions.

## Usage

### ✅ Use when

Use page summary effectively by limiting the number of items included. The page summary is prime real estate on the page, and when you limit the number of items, you magnify the impact of each one.

## Options

### Toolbar

Use the toolbar component a to add page summary actions in a SKY UX-themed toolbar. Only include actions that relate to the page as a whole, and exclude actions that are specific to the tiles on the page. Limit the number of actions in the toolbar. If the page summary requires many actions, re-examine the tasks and consider alternative workflows.

Display the toolbar below the page summary. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. Actions to collapse and expand all tiles on the record are docked on the right side of the toolbar.

## Content

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

## Related information

### Components

- Toolbar
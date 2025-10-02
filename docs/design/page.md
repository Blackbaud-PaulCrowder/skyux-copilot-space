---
component: 'page'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the page component extracted from SKY UX documentation.'
---

# Page Design Guidelines

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

###### Blocks

For record pages, use the blocks layout to organize content into modular blocks. For a wide range of possible layouts, place a fluid grid or another grid layout via flexbox or CSS grid in the content area.

###### List

For list pages, use the list layout to display lists of data.

###### Tabs

For record pages or list pages, use the tabs layout to organize large amounts of content into tab panels. Each tab panel can have a different layout. For more information, see tabs.

###### Fit

For split view pages, use the fit layout to fill the content area and anchor content to the edges.

###### None

For custom content that doesn't work well with predefined layouts or spacing, use the none layout.

### Heading

Page headings uniquely identify page content for users. You can use a standard heading or a hub and spoke heading.

###### Heading

Use headings to identify and describe the content of pages. When users arrive on a page, the heading confirms they are where they expect. Keep in mind that heading text may also identify the page for users in other contexts, such as links, buttons, and menus.

###### Hub and spoke heading

Use hub and spoke headings when users can only navigate to child pages from a central hub page. The headings on child pages link back to the hub.

Hub and spoke headings only go one level deep to connect hub pages to their child spoke pages. Don't use the headings to track browsing history.

Don't use hub and spoke headings to navigate between a parent record page and its child pages. Use tabs to group large amounts of content within a page.

### Alert

To highlight critical information that users absolutely must see when they visit the page, you can display an alert in the header. Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

### Avatar

To help users recognize or identify records, you can display a large (100px) avatar in the top left of record pages.

### Details

To supplement page headings with content that is relevant across all views, you can display page details under the headings. For more information, see the record page guidelines.

### Actions

To highlight the most important or most frequently used actions on a page, you can include page actions in the header. For more information, see the record page guidelines.

### Page links

###### Link lists

For blocks layout pages, you can add link lists for navigation in a way that is similar to action hubs. Always use headings to organize page links into groups and limit the number of links to 10 or fewer.

For groups of page links to add for action hubs, see the action hub's Content guidelines.

###### Recently accessed link list

Use the recently accessed link list to display up to five items a user accessed most recently in reverse chronological order.

###### Layout

Page links display to the right of the page content when space is available. In a smaller viewport, page links display under the page content. See responsiveness behaviors below.

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
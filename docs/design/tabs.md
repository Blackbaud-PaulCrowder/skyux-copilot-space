---
component: 'tabs'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the tabs component extracted from SKY UX documentation.'
---

# Tabs Design Guidelines

## Component Overview
Tabs divide and categorize large amounts of content on a page.

## Usage

### ✅ Use when

Use tabs when users require quick access to different slices of the same data.

Use tabs when users need to complete different tasks on a page and each task includes a significant amount of data.

### ❌ Don't use when

Don't use tabs within another tab. Change the workflow instead of nesting multiple sets of tabs.

Don't use tabs when they are likely to overflow the available horizontal space. The collapsed behavior of tabs will accommodate small screen resolutions or cases where users add many tabs themselves, but it is not intended as the default experience with a tabset. Use vertical tabs instead.

## Anatomy

- Selected tab
- Unselected tab
- Tab border
- Tab panel
- Close tab button
- Add tab button

## Options

### Add and close

If users need to work with a subset of tabs in a large tabset, let them add and close tabs to display only the relevant tabs.

If a new tab includes multiple options on what to display, use action buttons in the tab view to let users make selections.

### Tab layouts

The following tab layouts can be used for organizing content within a tab panel.

###### Blocks

Use blocks tab layout for laying out blocks of content in a tab panel.

Place a fluid grid or other grid layouts via flexbox or CSS grid in page content area to acheive a large range of content layouts.

###### List

Use the list layout for lists of data.

###### Fit

Use the fit layout for content to fill the content area and be anchored to the edges of the tab panel.

###### None

Use the none layout for custom layouts and content within a tab panel.

## Behavior and states

### Overflowing tabs

If the tabset includes too many tabs to fit in the tab bar's available horizontal space, the tabs collapse into a dropdown.

### States

## Layout

### Tab order

Organize tabs according to the specific needs of the page or record, with the most important or commonly used tabs on the left. For example, organize record page tabs into four groups:

- Overview tab (optional)
- Context-specific tabs
- SKY Add-in tabs (optional)
- Common tabs (optional)

### Placement and spacing

Tabs are always the last (bottommost) content in their container. Don't put additional content under tabs.

The tab border extends the full width of the container. Don't use left or right margins on the tab border, and ignore any padding that the container defines.

Tab content does not have additional left or right padding. The left and right gutters align with the gutters for content outside the tabs.

## Content

Use short, straightforward labels to clearly communicate the purpose of tabs. For consistency, use “Overview” when the first tab displays summary information. For example, use an Overview tab on record pages to display primary or identifying data and inform users about the current state and history of the record.

## Related information

### Components

- Action buttons
- Vertical tabs

### Guidelines

- Content containers
- Page design
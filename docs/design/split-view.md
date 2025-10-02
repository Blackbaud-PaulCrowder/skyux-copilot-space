---
component: 'split-view'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the split-view component extracted from SKY UX documentation.'
---

# Split View Design Guidelines

## Component Overview
A split view displays a workspace beside a list to let users view details and take actions for the selected item.

## Usage

### ✅ Use when

Use split views when users need to work through a list of items with the intent of taking action on each item.

### ❌ Don't use when

Don't use split views when users are likely to interact with a small number of items in the list. Use regular lists instead, and follow the flyout guidelines to determine whether to use flyouts or navigate to selected records.

## Anatomy

### Large viewport

### Small viewport

- List panel
- Workspace panel
- Summary action bar

## Options

### List type

Repeaters are the most common list type because they enable flexible content layouts.

Tree views can be used when items are hierarchical. If items at different levels have different types, you can use multiple views in the workspace panel.

We recommend against using grids if possible. They do not scale well at the typically small width of the list.

### List manipulation

If users need to search for specific items in the list or show and hide items with certain statuses, include a search input or status checkbox filter in the list panel.

When possible, pre-filter the list to relevant items and pre-sort it to the expected useful order. If you can't predict how users will use the list, include a toolbar to let them add items or filter, sort, and search the list.

## Behavior and states

### Automatically advance to the next item

If users are likely to work through the list sequentially, remove the selected item and automatically advance to the next item after users invoke the primary action in the workspace.

### Place focus in the workspace

When users select an item in the list, place focus on the first focusable element in the workspace so that users can start working immediately.

### Change panel width

Users can change the panel widths using drag-and-drop or keyboard interactions. If the list content is wider than the panel, a horizontal scrollbar appears.

### Responsiveness

In smaller viewports, the split view automatically switches from a side-by-side view to a panel-switching interaction where users switch between the list and the workspace.

## Content

### List item

Use up to three pieces of data to identify the item. If additional content is needed to uniquely identify the item, put it in the workspace view instead of overloading the list item.

## Layout

A split view should be the last item on a page. Do not place additional content below it.

## Related information

### Components

- Repeater
- Summary action bar

### Guidelines

- Form design
- Split view page
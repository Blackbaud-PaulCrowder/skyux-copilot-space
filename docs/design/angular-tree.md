---
component: 'angular-tree'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the angular-tree component extracted from SKY UX documentation.'
---

# Angular Tree Design Guidelines

## Component Overview
Tree views provide hierarchical list views with multiple modes for selecting items in the lists.

## Usage

### ✅ Use when

Use tree views to represent hierarchical information. You can make tree views read-only or allow users to select list items.

## Anatomy

- Expand/collapse button
- List item
- Checkbox
- Context menu
- Help inline button

## Options

### Selection mode

You can use the single-select and multiselect modes to allow users to select list items.

You can use the cascading selection mode to select descendant nodes when users select items. Use this mode when users are likely to select all descendants within nodes.

You can use the leaf-only selection mode to limit user selections to leaf nodes. Use this mode when higher-level nodes are categories that contain leaf nodes for users to select.

### Help inline button

When you need to supplement a tree view list item with additional information but don't require persistent inline help, you can place a help inline button beside the list item to invoke contextual user assistance.

### Navigation mode

When users need to work with the items in hierarchical lists and take actions, you can place tree views within split views. When users select items to work on, tree views highlight those items with the active state.

### Read-only mode

You can use the read-only mode to allow users to view hierarchical information in cases where items are not selectable and are not used for navigation. You can still include interactive elements such as hyperlinks in the list items.

### Context menus

When users need to perform actions on items in hierarchical lists, you can include context menus to provide access to those actions.

## Behavior and states

### Expand and collapse nodes

The button beside items expands and collapses the node.

### States

## Related information

### Components

- Angular tree component
- Data grid
- Dropdown
- Help inline button
- Repeater
- Split view
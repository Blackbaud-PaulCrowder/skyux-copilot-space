---
component: 'dropdown'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the dropdown component extracted from SKY UX documentation.'
---

# Dropdown Design Guidelines

## Component Overview
Dropdown buttons display menus that group sets of actions or functions.

## Usage

### ✅ Use when

Use dropdowns when users require access to multiple, related actions or when users require access to multiple, unrelated actions and you do not have room for multiple buttons.

Use context-menu dropdowns when actions affect individual items in a list.

For details on when to include a delete action in a context-menu dropdown, see the manage data guidelines.

Use icon-only dropdowns when you do not have room for text labels. For example, use icon-only dropdowns in list toolbars when screen widths are narrow.

### ❌ Don't use when

Don't use dropdowns as form inputs. Use HTML <select> fields instead.

## Anatomy

- Dropdown button
- Dropdown menu
- Action

## Options

### Button types

### Button styles

Dropdown buttons can use the default or primary styles inherited from SKY UX buttons. For details about when to use the primary style, see the primary action guidelines.

## Behavior and states

### Behavior

The popover component defines the behavior of dropdown menus.

### States

Dropdown buttons inherit the styling for states such as hover and disabled from SKY UX buttons.

## Content

### Dropdown menu action text

For actions that clearly apply to the object associated with the context menu, use the following format for the action wording:

<Verb>

For dropdown buttons with one type of action, use the following format:

Button text: <Verb>

Menu item: <Direct object>

For dropdown buttons with more than one type of action, use the following format:

Button icon: fa-ellipsis-hsky-i-ellipsis

Button text: More

Menu item: <Verb> <direct object>

## Layout

### Placement

Place context-menu dropdowns to the left of all row-specific content but to the right of all list controls, such as expand-collapse actions in tree views and checkboxes in grids or repeaters.

Default dropdowns are positioned with the same alignment and margins as SKY UX buttons.

### Menu items

Organize menu items to place the most important or frequently used options at the top of the list and the least important or least frequently used items at the bottom.

## Related information

### Components

- Buttons
- Popovers

### Guidelines

- Buttons and links
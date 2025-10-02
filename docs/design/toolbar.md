---
component: 'toolbar'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the toolbar component extracted from SKY UX documentation.'
---

# Toolbar Design Guidelines

## Component Overview
The toolbar component displays actions to manipulate a list or to manipulate the individual items in the list.

## Usage

### ✅ Use when

Use list toolbars to display actions that manipulate the contents of lists of records. Place frequently used actions directly in the toolbar, and place less-frequently used actions in the more actions menu. When multiple views are available, dock the view switcher on the right.

Use toolbars to display actions that manipulate lists within containers, such as boxes or modals. Only place the most important actions directly in the toolbar because containers have limited horizontal real estate. Place all other actions in the more actions dropdown.

For guidance on how to incorporate filters into lists within containers, see filter lists guidelines.

### ❌ Don't use when

Don't use toolbars on record page headers to display page actions. Instead, place page actions directly below the record details.

Don't use toolbars in action hub headers to display actions related to action hub content. Instead, place common action buttons directly on the page below the page title.

## Options

Only include toolbar options that are relevant to a particular list, and organize them consistently in their designated locations.

### Standard toolbar actions

Place standard actions to the far left of the toolbar, and organize them from left to right based on the order in this section.

Don't include primary action buttons in toolbars.

## Behavior and states

### Toolbar action wrapping

Do not extend the standard actions and more actions menu beyond 50 percent of the toolbar.

If the standard actions extend beyond 50 percent of the toolbar, create a more actions menu for at least two of the rightmost actions.

### Small form factors

On small screens, action buttons switch to icon-only buttons, the search field collapses into a search icon, and the view switcher collapses into a single icon. Buttons without icons go in the more actions menu, and the more actions button, view switcher, and any other buttons with dropdowns display their options when selected.

## Layout

When two toolbars are stacked, place a border separator between them.

## Related information

### Components

- Box
- Buttons
- Data manager
- Search

### Guidelines

- List page
- Record page
- Terminology
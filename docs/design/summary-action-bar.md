---
component: 'summary-action-bar'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the summary-action-bar component extracted from SKY UX documentation.'
---

# Summary Action Bar Design Guidelines

## Component Overview
The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.

## Usage

### ✅ Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

Use summary action bars for actions that are taken on the selected record in split views.

Use summary action bars when you need to show summary information related to the forms in modals.

### ❌ Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

## Anatomy

- Actions
- Summary information

## Behavior and states

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

## Options

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

## Related information

### Components

- Data entry grid
- Data grid
- Modal
- Repeater

### Guidelines

- Form design
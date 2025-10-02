---
component: 'filter'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the filter component extracted from SKY UX documentation.'
---

# Filter Design Guidelines

## Component Overview
Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

## Usage

### ✅ Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a Filter button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the filtering lists guidelines.

### ❌ Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use persistent inline filters instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a filter bar instead to make filters always available and directly selectable.

## Anatomy

- Toolbar (transparent)
- Filter button
- Expandable filter section (transparent)
- Simple filters

## Behaviors and states

## Layout

Filter buttons appear in the toolbar above lists.

## Related information

### Components

- Toolbar

### Guidelines

- Filter lists
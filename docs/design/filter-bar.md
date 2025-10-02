---
component: 'filter-bar'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the filter-bar component extracted from SKY UX documentation.'
---

# Filter Bar Design Guidelines

## Component Overview
The filter bar presents users with inline filter options to narrow lists. It allows for a large number of filter options. The filter bar component does not currently integrate the data manager component, but integration is coming soon.

## Usage

### ✅ Use when

Use the filter bar when the main or only task on a page is to narrow a collection of items or manipulate a pre-filtered collection. Use a filter bar or tabs to support the filtering tasks on dedicated full-page lists, such as list pages or in tabs on record pages.

Use the filter bar with pre-filtered lists where filters are already active when:

- Users need to adjust preset filter values or add additional filters to refine lists.
- Users access lists through calls to action and need to further narrow the lists before taking action.

### ❌ Don't use when

Don't use the filter bar when:

- Users need regular access to a small number of lists.
- One list in a small group of lists needs priority or will be used most frequently.
- A small number of lists have different tasks for users to complete.

Use pre-filtered lists in tabs instead.

## Anatomy

- Toolbar divider
- Filter bar label
- Filter button (filter not set)
- Filter button (filter set)
- Clear filters button
- Filter chooser button

## Options

### Filter chooser

When a list requires many filters to give users multiple ways to narrow the collection of items, include a filter chooser to let users select the filters to include in the filter bar.

Within filter choosers, organize filters alphabetically. If some filters will be used most of the time, include them directly in the filter bar by default.

## Behavior and states

### Filter types

The filter bar can support multiple types of selection methods for filtering. Use the following filter types for selection and display of filters in the filter bar.

### Clear all values

When users select Clear all values, confirm their intention with a confirmation modal before removing the filter values to avoid losing their work by mistake.

### Updates to summary details

When filters or search criteria are applied to a list, update the list count and summary details to reflect the filtered list. Add "match" to the list count label to reflect the list is in a filtered state.

## Content

## Related information

### Guidelines

- Form design
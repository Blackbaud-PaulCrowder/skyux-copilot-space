---
component: 'paging'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the paging component extracted from SKY UX documentation.'
---

# Paging Design Guidelines

## Component Overview
The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.

## Usage

### ✅ Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

- Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
- Avoiding wait times of more than a couple seconds while items load.
- Using less space so that the page composition better communicates the relationship between the list and other elements on the page.

### ❌ Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the wizard instead.

Don't use the paging component when a list is presented in a split view.

## Anatomy

- Paging content
- Previous button
- Current page
- Pages
- Next button

## Options

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

### Number of items per page

To determine how many items to display per page:

- Optimize for performance to load items within 2 seconds.
- Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
- Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

## Behavior and states

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

### Loading new items

When users navigate to a new set of items, the list is disabled and a wait indicator appears in the paging content area until the new items finish loading.

## Related information

### Components

- Data grid
- Data manager
- Infinite scroll
- Split view
- Wizard

### Guidelines

- Filtering lists
- List page
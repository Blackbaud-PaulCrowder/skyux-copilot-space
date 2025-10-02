---
component: 'key-info'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the key-info component extracted from SKY UX documentation.'
---

# Key Info Design Guidelines

## Component Overview
The key info component highlights important summary information.

## Usage

### ✅ Use when

Use key info to highlight important summary information.

Use key info to show the total number of items in a list. Use the horizontal layout and place the key info at the top of the list.

### ❌ Don't use when

Don't use key info when different data visualizations are more appropriate for large amounts of data. For example, don't group multiple key info components to track how data changes over time. Use alternative visualizations such as data grids, bar charts, or line charts instead.

Don't use key info when data doesn't require user attention or doesn't drive user action. Use description lists instead.

## Anatomy

- Value
- Label
- Help inline button

## Options

### Layout

Use the default vertical layout with the label under the value in most situations.

Use the horizontal layout with the label beside the value for scenarios where vertical space is at a premium. For example, use the horizontal layout and the small size to display the total number of items in a list.

### Size

Use the large key info when the values need to stand out in places such as data visualizations, dashboards, and landing pages.

Use the small key info to highlight information that doesn't require the large size to stand out, such as the total number of items in a list.

### Help inline button

When you need to supplement a key info label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

## Behavior and states

### Link styling

You can style the key info component as a link to let users select the value to navigate to a different location.

## Layout

### Horizontal layout

When laying out key info components horizontally:

- Use "sky-margin-inline-xxl" for consistent spacing between elements.
- Don't overwhelm users with more than 6 elements without headings or grouping.

## Related information

### Components

- Description list
- Help inline button

### Guidelines

- Call out information
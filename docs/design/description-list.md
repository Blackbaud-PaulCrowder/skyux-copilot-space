---
component: 'description-list'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the description-list component extracted from SKY UX documentation.'
---

# Description List Design Guidelines

## Component Overview
Description lists display scannable data that pair terms with descriptions.

## Usage

### ✅ Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

Use description lists in longDescription mode to display glossaries or other data where the descriptions are complete sentences or longer.

### ❌ Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use key info or other methods to call out information instead.

Don't use description lists when users can understand data based on its context and don't need a label.

## Anatomy

- Term
- Description
- Help inline button

## Options

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a help inline button beside the term to invoke contextual user assistance.

## Behavior and states

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

## Content

Don't use colons or other punctuation after description list terms.

## Layout

### Horizontal lists

Use horizontal mode to display up to 6 term-description pairs in description lists that stand alone.

### Vertical lists

Use vertical mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a fluid grid to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

## Related information

### Components

- Fluid grid
- Help inline button
- Key info

### Guidelines

- Call out information
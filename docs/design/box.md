---
component: 'box'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the box component extracted from SKY UX documentation.'
---

# Box Design Guidelines

## Component Overview
Boxes provide containers to group related content and actions.

## Usage

### ✅ Use when

Use boxes as containers for related content and actions on pages such action hubs and record pages.

### ❌ Don't use when

Don't use boxes to separate individual items in a list. Use repeaters or other layout approaches instead.

Don't use boxes to organize content in modal forms or split view workspaces. Use headers and spacing instead.

Don't add boxes to pre-defined sections of page layouts. For example, don't add boxes around lists on list pages or around related links on action hubs.

## Anatomy

- Container
- Content
- Heading
- Help inline button
- Control button

## Options

### Heading

In general, boxes should include short headings to describe their contents. However, headings are optional so that consumers can exclude them when boxes contain content that doesn't require headings, such as visualizations or multimedia content.

To match to a page's semantic and visual hierarchy, adjust the box heading's headingLevel and headingStyle properties. In most cases, box headings follow the page heading in the page hierarchy, and these properties should be set to 2.

### Help inline button

When you need to supplement a box with additional information but don't require persistent inline help, you can place a help inline button beside the heading to invoke contextual user assistance.

### Control button

You can include a button in the top right to provide an edit action or a context menu with multiple actions.

Don't include multiple buttons in boxes. Instead, break up content so that boxes only contain related content that users can manage together.

## Layout

Use proper spacing between boxes. Depending on your scenario, you can use fluid grid, CSS flexbox, CSS Grid or spacing classes.

## Related information

### Components

- Action hub
- Fluid grid
- Help inline button

### Guidelines

- Action hub page
- Record page
- Spacing
---
component: 'popover'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the popover component extracted from SKY UX documentation.'
---

# Popover Design Guidelines

## Component Overview
Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.

## Usage

### ✅ Use when

Use popovers to display additional contextual content that is valuable some of the time.

### ❌ Don't use when

Don't use popovers when the content is valuable most of the time. Use persistent inline help instead.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

Don't use popovers when a large amount of content is necessary. Use a flyout instead.

## Anatomy

- Content area
- Highlight border
- Element pointer

## Options

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on click actions rather than mouseenter actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

## Behavior and states

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

## Content

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

Don't include a large amount of content, form inputs, or complex interactions.

## Layout

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

## Related information

### Guidelines

- User assistance
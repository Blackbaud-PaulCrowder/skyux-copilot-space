---
component: 'wait'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the wait component extracted from SKY UX documentation.'
---

# Wait Design Guidelines

## Component Overview
The wait component and service create waits on individual elements and on pages.

## Accessibility

### Text equivalents

The wait component provides default text equivalents for screen readers to support accessibility. These ARIA values are available when users tab to a wait icon, when a wait loads, and when a wait closes. For page-level waits, the default values are sufficient for most scenarios, but for element-level waits, we recommend more specific text equivalents to describe the elements.

For example, element-level nonblocking waits default to "Loading." when they initially load and to "Loading complete." when loading finishes. If multiple elements on a page require waits, then screen readers repeat these generic messages. To support users of assistive technologies, we recommend more descriptive values, such as "Gift details loading." and "Loading complete for gift details."

### Focus

When a focused element on a page is placed in a waiting state, focus automatically shifts to the page's body element. If the waiting state for that element finishes before any additional change in focus, then the focus automatically reverts to the previously focused element.
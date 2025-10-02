---
component: 'back-to-top'
type: 'api-documentation'
description: 'API documentation for the back-to-top component including components, interfaces, and types.'
---

# Back To Top API Documentation

## Components and Directives

#### LayoutBackToTopInfiniteScrollExampleComponent

**Selector:** `app-layout-back-to-top-infinite-scroll-example`

**Package:** `@skyux/code-examples`

#### LayoutBackToTopRepeaterExampleComponent

**Selector:** `app-layout-back-to-top-repeater-example`

**Package:** `@skyux/code-examples`

#### SkyBackToTopComponent

**Selector:** `sky-back-to-top`

**Package:** `@skyux/layout`

#### SkyBackToTopDirective

Associates a button with an element on the page and displays that button
to return to the element after users scroll away.

**Selector:** `[skyBackToTop]`

**Package:** `@skyux/layout`

**Inputs:**

- `skyBackToTop`: `"" | SkyBackToTopOptions | undefined` - Configuration options for the back to top component.
- `skyBackToTopMessageStream`: `Subject<SkyBackToTopMessage> | undefined` - The observable to send commands to the back to top component.
The commands respect the `SkyBackToTopMessage` type.
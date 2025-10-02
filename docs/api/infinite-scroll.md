---
component: 'infinite-scroll'
type: 'api-documentation'
description: 'API documentation for the infinite-scroll component including components, interfaces, and types.'
---

# Infinite Scroll API Documentation

## Components and Directives

#### LayoutBackToTopInfiniteScrollExampleComponent

**Selector:** `app-layout-back-to-top-infinite-scroll-example`

**Package:** `@skyux/code-examples`

#### ListsInfiniteScrollRepeaterExampleComponent

**Selector:** `app-lists-infinite-scroll-repeater-example`

**Package:** `@skyux/code-examples`

#### SkyInfiniteScrollComponent

**Selector:** `sky-infinite-scroll`

**Package:** `@skyux/lists`

**Inputs:**

- `enabled`: `boolean | undefined` - Whether to make the infinite scroll component active when more data is available
to load. By default, infinite scroll is inactive and does not call the load function. (default: false)
- `loading`: `boolean | undefined` - Whether data is loading because of a `scrollEnd` event. Setting the property
to `true` disables new `scrollEnd` events from firing until it changes to `false`. If this
property is not specified, the infinite scroll component watches the DOM for changes
and fires `scrollEnd` events when changes occur on its parent DOM element. Relying
on this default behavior could fire an excessive number of `scrollEnd` events
if the DOM changes are not related to loading data, so we strongly recommend using this
property to explicitly set the infinite scroll's loading state.

**Outputs:**

- `scrollEnd`: `EventEmitter<void>` - Fires when scrolling triggers the need to load more data or when users select the button
to load more data. This event only fires when the `enabled` property is set to `true`
and data is not already loading.
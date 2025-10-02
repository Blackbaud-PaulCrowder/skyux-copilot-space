---
component: 'page-deprecated'
type: 'api-documentation'
description: 'API documentation for the page-deprecated component including components, interfaces, and types.'
---

# Page Deprecated API Documentation

## Components and Directives

#### SkyPageComponent

Displays a page using the specified layout. The page component is a responsive container,
meaning content will respect the breakpoints within the page element instead of the window.
This is helpful if there is other content to the left or right of the page.

**Selector:** `sky-page`

**Package:** `@skyux/pages`

**Inputs:**

- `layout`: `InputSignal<SkyPageLayoutType>` - The page layout that applies spacing to the page header and content. Use the layout
that corresponds with the top-level component type used on the page, or use `fit` to
constrain the page contents to the available viewport.
Use `none` for custom content that does not adhere to predefined spacing or constraints. (default: "none")
- `helpKey`: `string | undefined` - A help key that identifies the page's default [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help) content to display.
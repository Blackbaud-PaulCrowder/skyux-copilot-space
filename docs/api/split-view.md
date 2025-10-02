---
component: 'split-view'
type: 'api-documentation'
description: 'API documentation for the split-view component including components, interfaces, and types.'
---

# Split View API Documentation

## Components and Directives

#### PagesPageSplitViewPageFitLayoutExampleComponent

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**Package:** `@skyux/code-examples`

#### SplitViewBasicExampleComponent

**Selector:** `app-split-view-basic-example`

**Package:** `@skyux/code-examples`

#### SplitViewPageBoundExampleComponent

**Selector:** `app-split-view-page-bound-example`

**Package:** `@skyux/code-examples`

#### SkySplitViewDrawerComponent

Specifies the content to display in the split view's list panel.

**Selector:** `sky-split-view-drawer`

**Package:** `@skyux/split-view`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the list panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `width`: `number | undefined` - Sets the list panel's width in pixels. (default: 320)

#### SkySplitViewWorkspaceContentComponent

Specifies the content to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace-content`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceFooterComponent

Specifies the footer to display in the split view's workspace panel. This component is often used with a summary action bar.

**Selector:** `sky-split-view-workspace-footer`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceHeaderComponent

Specifies the header to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace-header`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceComponent

Contains the content, footer, and header to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace`

**Package:** `@skyux/split-view`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the workspace panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### SkySplitViewComponent

Displays a list alongside a workspace where users can view details for selected items
and take actions.

**Selector:** `sky-split-view`

**Package:** `@skyux/split-view`

**Inputs:**

- `messageStream`: `Subject<SkySplitViewMessage>` - The observable that sends commands to the split view component.
The commands should respect the `SkySplitViewMessage` type.
- `backButtonText`: `string` - The label for the button that appears in the workspace header in responsive mode.
The button returns users to the list. (default: "Back to list")
- `bindHeightToWindow`: `boolean` - Whether the split view's height is bound to the window height. (default: false)
- `dock`: `SkySplitViewDockType` - How the split view docks to its container. Use `fill` to dock
the split view to the container's size where the container is a `sky-page` component
with its `layout` input set to `fit`, or where the container is another element with
a relative or absolute position and a fixed size. (default: "none")
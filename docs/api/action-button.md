---
component: 'action-button'
type: 'api-documentation'
description: 'API documentation for the action-button component including components, interfaces, and types.'
---

# Action Button API Documentation

## Components and Directives

#### LayoutActionButtonBasicExampleComponent

**Selector:** `app-layout-action-button-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutActionButtonPermalinkExampleComponent

**Selector:** `app-layout-action-button-permalink-example`

**Package:** `@skyux/code-examples`

#### SkyActionButtonContainerComponent

Wraps action buttons to ensures that they have consistent height and spacing.

**Selector:** `sky-action-button-container`

**Package:** `@skyux/layout`

**Inputs:**

- `alignItems`: `SkyActionButtonContainerAlignItemsType` - How to display the action buttons inside the action button container.
Options are `"center"` or `"left"`. (default: "center")

#### SkyActionButtonDetailsComponent

Specifies a description to display on an action button.

**Selector:** `sky-action-button-details`

**Package:** `@skyux/layout`

#### SkyActionButtonHeaderComponent

Specifies a header to display on an action button.

**Selector:** `sky-action-button-header`

**Package:** `@skyux/layout`

#### SkyActionButtonIconComponent

Specifies an icon to display on the action button.

**Selector:** `sky-action-button-icon`

**Package:** `@skyux/layout`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.

#### SkyActionButtonComponent

Creates a button to present users with an option to move forward with tasks.

**Selector:** `sky-action-button`

**Package:** `@skyux/layout`

**Inputs:**

- `permalink`: `SkyActionButtonPermalink | undefined` - The link for the action button.

**Outputs:**

- `actionClick`: `EventEmitter<any>` - Fires when users select the action button.
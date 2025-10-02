---
component: 'inline-delete'
type: 'api-documentation'
description: 'API documentation for the inline-delete component including components, interfaces, and types.'
---

# Inline Delete API Documentation

## Components and Directives

#### LayoutInlineDeleteCustomExampleComponent

**Selector:** `app-layout-inline-delete-custom-example`

**Package:** `@skyux/code-examples`

#### LayoutInlineDeleteRepeaterExampleComponent

**Selector:** `app-layout-inline-delete-repeater-example`

**Package:** `@skyux/code-examples`

#### SkyInlineDeleteComponent

**Selector:** `sky-inline-delete`

**Package:** `@skyux/layout`

**Inputs:**

- `pending`: `boolean | undefined` - Whether the deletion is pending. (default: false)

**Outputs:**

- `cancelTriggered`: `EventEmitter<void>` - Fires when users click the cancel button.
- `deleteTriggered`: `EventEmitter<void>` - Fires when users click the delete button.
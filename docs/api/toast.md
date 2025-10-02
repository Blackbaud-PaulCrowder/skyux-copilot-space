---
component: 'toast'
type: 'api-documentation'
description: 'API documentation for the toast component including components, interfaces, and types.'
---

# Toast API Documentation

## Components and Directives

#### ToastBasicExampleComponent

**Selector:** `app-toast-basic-example`

**Package:** `@skyux/code-examples`

#### ToastCustomComponentExampleComponent

**Selector:** `app-toast-custom-component-example`

**Package:** `@skyux/code-examples`

#### SkyToastComponent

**Selector:** `sky-toast`

**Package:** `@skyux/toast`

**Inputs:**

- `autoClose`: `boolean | undefined` - Whether to automatically close the toast. Only close toasts
automatically if users can access the messages after the toasts close.
- `toastType`: `SkyToastType | undefined` - The `SkyToastType` type for the toast to determine the color and icon to display.

**Outputs:**

- `closed`: `EventEmitter<void>` - Fires when the toast closes.
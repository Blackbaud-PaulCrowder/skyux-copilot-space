---
component: 'inline-form'
type: 'api-documentation'
description: 'API documentation for the inline-form component including components, interfaces, and types.'
---

# Inline Form API Documentation

## Components and Directives

#### InlineFormBasicExampleComponent

**Selector:** `app-inline-form-basic-example`

**Package:** `@skyux/code-examples`

#### InlineFormCustomButtonsExampleComponent

**Selector:** `app-inline-form-custom-buttons-example`

**Package:** `@skyux/code-examples`

#### InlineFormRepeatersExampleComponent

**Selector:** `app-inline-form-repeaters-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Package:** `@skyux/code-examples`

#### SkyInlineFormComponent

Renders form content in the current view instead of a separate modal.

**Selector:** `sky-inline-form`

**Package:** `@skyux/inline-form`

**Inputs:**

- `template`: `TemplateRef<unknown> | undefined` - The template to instantiate the inline form.
- `config`: `SkyInlineFormConfig | undefined` - Configuration options for the buttons to display with the inline form.
- `showForm`: `boolean | undefined` - Whether to display the inline form. Users can toggle between displaying
and hiding the inline form. (default: false)

**Outputs:**

- `close`: `EventEmitter<SkyInlineFormCloseArgs>` - Fires when users close the inline form.
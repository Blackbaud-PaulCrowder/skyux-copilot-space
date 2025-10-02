---
component: 'sectioned-form'
type: 'api-documentation'
description: 'API documentation for the sectioned-form component including components, interfaces, and types.'
---

# Sectioned Form API Documentation

## Components and Directives

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### SkySectionedFormSectionComponent

Creates an individual form to display as a section within the sectioned form.

**Selector:** `sky-sectioned-form-section`

**Package:** `@skyux/tabs`

**Inputs:**

- `active`: `boolean | undefined` - Whether the section is active when the form loads. (default: false)
- `heading`: `string | undefined` - The section header.
- `itemCount`: `number | undefined` - The number of items within the section. A counter appears beside the section header.

#### SkySectionedFormComponent

Creates a container for the sectioned forms.

**Selector:** `sky-sectioned-form`

**Package:** `@skyux/tabs`

**Inputs:**

- `maintainSectionContent`: `boolean | undefined` - Whether the sectioned form loads section content during initialization so that it
displays content without moving around elements in the content container. (default: false)
- `messageStream`: `Subject<SkySectionedFormMessage>`

**Outputs:**

- `indexChanged`: `EventEmitter<number>` - Fires when the active tab changes and emits the index of the active
section. The index is based on the section's position when the form loads.
- `tabsVisibleChanged`: `EventEmitter<boolean>` - Fires when the sectioned form tabs are shown or hidden.
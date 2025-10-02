---
component: 'card'
type: 'api-documentation'
description: 'API documentation for the card component including components, interfaces, and types.'
---

# Card API Documentation

## Components and Directives

#### LayoutCardBasicExampleComponent

**Selector:** `app-layout-card-basic-example`

**Package:** `@skyux/code-examples`

#### SkyCardActionsComponent

Specifies an action that users can perform on the card.

**Selector:** `sky-card-actions`

**Package:** `@skyux/layout`

#### SkyCardContentComponent

Specifies the content to display in the body of the card.

**Selector:** `sky-card-content`

**Package:** `@skyux/layout`

#### SkyCardTitleComponent

Specifies a title to identify what the card represents.

**Selector:** `sky-card-title`

**Package:** `@skyux/layout`

#### SkyCardComponent

Creates a a small container to highlight important information.

**Selector:** `sky-card`

**Package:** `@skyux/layout`

**Inputs:**

- `selectable`: `boolean | undefined` - Whether to display a checkbox to the right of the card title.
Users can select multiple checkboxes and perform actions on the selected cards. (default: false)
- `selected`: `boolean | undefined` - Whether the card is selected. This only applies to card where
`selectable` is set to `true`. (default: false)
- `size`: `string` - The size of the card. The valid options are `"large"` and `"small"`. (default: "large")

**Outputs:**

- `selectedChange`: `EventEmitter<boolean>` - Fires when users select or deselect the card.
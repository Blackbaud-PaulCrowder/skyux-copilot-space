---
component: 'icon'
type: 'api-documentation'
description: 'API documentation for the icon component including components, interfaces, and types.'
---

# Icon API Documentation

## Components and Directives

#### FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Package:** `@skyux/code-examples`

#### FormsRadioIconExampleComponent

**Selector:** `app-forms-radio-icon-example`

**Package:** `@skyux/code-examples`

#### IconBasicExampleComponent

**Selector:** `app-icon-basic-example`

**Package:** `@skyux/code-examples`

#### IconIconButtonExampleComponent

**Selector:** `app-icon-icon-button-example`

**Package:** `@skyux/code-examples`

#### SkyActionButtonIconComponent

Specifies an icon to display on the action button.

**Selector:** `sky-action-button-icon`

**Package:** `@skyux/layout`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.

#### SkyIconComponent

**Selector:** `sky-icon`

**Package:** `@skyux/icon`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.
- `iconSize`: `InputSignal<undefined | SkyIconSize>` - The icon size. Size is independent of font size. (default: "m")
- `variant`: `SkyIconVariantType | undefined` - The icon variant. If the variant doesn't exist for the
specified icon, the normal icon is displayed. This property only applies when using SKY UX icons.
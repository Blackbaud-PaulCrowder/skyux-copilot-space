---
component: 'format'
type: 'api-documentation'
description: 'API documentation for the format component including components, interfaces, and types.'
---

# Format API Documentation

## Components and Directives

#### AutonumericInternationalFormattingExampleComponent

**Selector:** `app-autonumeric-international-formatting-example`

**Package:** `@skyux/code-examples`

#### LayoutFormatExampleComponent

**Selector:** `app-layout-format-example`

**Package:** `@skyux/code-examples`

#### SkyFormatComponent

**Selector:** `sky-format`

**Package:** `@skyux/layout`

**Inputs:**

- `args`: `TemplateRef<any>[] | undefined` - An array of `TemplateRef` objects to be placed in the template, where the `nth`
item is placed at the `{n}` location in the template.
- `text`: `string | undefined` - The tokenized string that represents the template. Tokens use the `{n}` notation
where `n` is the ordinal of the item to replace the token.
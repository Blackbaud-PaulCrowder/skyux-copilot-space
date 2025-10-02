---
component: 'text-expand'
type: 'api-documentation'
description: 'API documentation for the text-expand component including components, interfaces, and types.'
---

# Text Expand API Documentation

## Components and Directives

#### LayoutTextExpandRepeaterExampleComponent

**Selector:** `app-layout-text-expand-repeater-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandInlineExampleComponent

**Selector:** `app-layout-text-expand-inline-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandModalExampleComponent

**Selector:** `app-layout-text-expand-modal-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandNewlineExampleComponent

**Selector:** `app-layout-text-expand-newline-example`

**Package:** `@skyux/code-examples`

#### SkyTextExpandRepeaterComponent

**Selector:** `sky-text-expand-repeater`

**Package:** `@skyux/layout`

**Inputs:**

- `data`: `InputSignal<undefined | TData[]>` - The data to truncate.
- `itemTemplate`: `InputSignal<undefined | TemplateRef<unknown>>` - The template for items in the list.
- `listStyle`: `InputSignal<undefined | SkyTextExpandRepeaterListStyleType>` - The style of bullet to use (default: "unordered")
- `maxItems`: `InputSignalWithTransform<number, unknown>` - The number of items to display before truncating the list. If not supplied, all items are shown.

#### SkyTextExpandComponent

**Selector:** `sky-text-expand`

**Package:** `@skyux/layout`

**Inputs:**

- `expandModalTitle`: `string | undefined` - The title to display when the component expands the full text in a modal. (default: "Expanded view")
- `truncateNewlines`: `boolean` - Whether to replace newline characters in truncated text with spaces. (default: true)
- `maxExpandedLength`: `number` - The maximum number of text characters to display inline when users select the link
to expand the full text. If the text exceeds this limit, then the component expands
the full text in a modal instead. (default: 600)
- `maxExpandedNewlines`: `number` - The maximum number of newline characters to display inline when users select
the link to expand the full text. If the text exceeds this limit, then
the component expands the full text in a modal view instead. (default: 2)
- `maxLength`: `number` - The number of text characters to display before truncating the text.
To avoid truncating text in the middle of a word, the component looks for a space
in the 10 characters before the last character. (default: 200)
- `text`: `string` - The text to truncate.
---
component: 'text-expand-repeater'
type: 'api-documentation'
description: 'API documentation for the text-expand-repeater component including components, interfaces, and types.'
---

# Text Expand Repeater API Documentation

## Components and Directives

#### LayoutTextExpandRepeaterExampleComponent

**Selector:** `app-layout-text-expand-repeater-example`

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

#### SkyRepeaterComponent

Creates a container to display repeater items.

**Selector:** `sky-repeater`

**Package:** `@skyux/lists`

**Inputs:**

- `activeIndex`: `number | undefined` - The index of the repeater item to visually highlight as active.
For example, use this property in conjunction with the
[split view component](https://developer.blackbaud.com/skyux/components/split-view)
to highlight a repeater item while users edit it. Only one item can be active at a time.
- `ariaLabel`: `string | undefined` - The ARIA label for the repeater list.
This sets the repeater list's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label). (default: "List of items")
- `reorderable`: `boolean | undefined` - Whether users can change the order of items in the repeater list.
Each repeater item also has `reorderable` property to indicate whether
users can change its order. (default: false)
- `expandMode`: `SkyRepeaterExpandModeType` - The layout that determines which repeater items are expanded by default and whether
repeater items are expandable and collapsible. Collapsed items display titles only.
The valid options are `multiple`, `none`, and `single`.
- `multiple` loads repeater items in an expanded state unless `isExpanded` is set to
`false` for a repeater item. This layout allows users to expand and collapse
as many repeater items as necessary. It is best-suited to repeater items where body
content is important but users don't always need to see it.
- `none` loads all repeater items in an expanded state and does not allow users to
collapse them. This default layout provides the quickest access to the details in the
repeater items. It is best-suited to repeater items with concise content
that users need to view frequently.
- `single` loads one repeater item in an expanded state and collapses all others.
The expanded repeater item is the first one where `isExpanded` is set to `true`. This layout
allows users to expand one item at a time. It provides the most compact view and is
best-suited to repeater items where the most important information is in the titles
and users only occasionally need to view the body content. (default: "none")

**Outputs:**

- `activeIndexChange`: `EventEmitter<number>` - Fires when the active repeater item changes.
- `orderChange`: `EventEmitter<any[]>` - Fires when users change the order of repeater items.
This event emits an ordered array of the `tag` properties that the consumer provides for each repeater item.
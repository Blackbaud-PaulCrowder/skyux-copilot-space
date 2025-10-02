---
component: 'repeater'
type: 'api-documentation'
description: 'API documentation for the repeater component including components, interfaces, and types.'
---

# Repeater API Documentation

## Components and Directives

#### InlineFormRepeatersExampleComponent

**Selector:** `app-inline-form-repeaters-example`

**Package:** `@skyux/code-examples`

#### LayoutBackToTopRepeaterExampleComponent

**Selector:** `app-layout-back-to-top-repeater-example`

**Package:** `@skyux/code-examples`

#### LayoutInlineDeleteRepeaterExampleComponent

**Selector:** `app-layout-inline-delete-repeater-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandRepeaterExampleComponent

**Selector:** `app-layout-text-expand-repeater-example`

**Package:** `@skyux/code-examples`

#### ListsInfiniteScrollRepeaterExampleComponent

**Selector:** `app-lists-infinite-scroll-repeater-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterAddRemoveExampleComponent

**Selector:** `app-lists-repeater-add-remove-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterBasicExampleComponent

**Selector:** `app-lists-repeater-basic-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Package:** `@skyux/code-examples`

#### SkyTextExpandRepeaterComponent

**Selector:** `sky-text-expand-repeater`

**Package:** `@skyux/layout`

**Inputs:**

- `data`: `InputSignal<undefined | TData[]>` - The data to truncate.
- `itemTemplate`: `InputSignal<undefined | TemplateRef<unknown>>` - The template for items in the list.
- `listStyle`: `InputSignal<undefined | SkyTextExpandRepeaterListStyleType>` - The style of bullet to use (default: "unordered")
- `maxItems`: `InputSignalWithTransform<number, unknown>` - The number of items to display before truncating the list. If not supplied, all items are shown.

#### SkyRepeaterItemContentComponent

Displays content text when the repeater is expanded.

**Selector:** `sky-repeater-item-content`

**Package:** `@skyux/lists`

#### SkyRepeaterItemContextMenuComponent

Wraps and styles a
[`skyux-dropdown` component](https://developer.blackbaud.com/skyux-popovers/docs/dropdown).

**Selector:** `sky-repeater-item-context-menu`

**Package:** `@skyux/lists`

#### SkyRepeaterItemTitleComponent

Displays a header inside the repeater item.

**Selector:** `sky-repeater-item-title`

**Package:** `@skyux/lists`

#### SkyRepeaterItemComponent

Creates an individual repeater item.

**Selector:** `sky-repeater-item`

**Package:** `@skyux/lists`

**Inputs:**

- `inlineFormConfig`: `SkyInlineFormConfig | undefined` - Configuration options for the buttons to display on an inline form
within the repeater. This property accepts
[a `SkyInlineFormConfig` object](https://developer.blackbaud.com/skyux/components/inline-form#skyinlineformconfig-properties).
- `inlineFormTemplate`: `TemplateRef<unknown> | undefined` - Specifies [an Angular `TemplateRef`](https://angular.io/api/core/TemplateRef) to use
as a template to instantiate an inline form within the repeater.
- `reorderable`: `boolean | undefined` - Whether users can change the order of the repeater item.
The repeater component's `reorderable` property must also be set to `true`. (default: false)
- `selectable`: `boolean | undefined` - Whether to display a checkbox in the left of the repeater item. (default: false)
- `showInlineForm`: `boolean | undefined` - Whether to display an inline form within the repeater.
Users can toggle between displaying and hiding the inline form. (default: false)
- `tag`: `any` - The object that the repeater component returns for this repeater item
when the `orderChange` event fires. This is required
if you set the `reorderable` property to `true`.
- `disabled`: `boolean | undefined` - Whether to exclude an item when cycling through.
- `isExpanded`: `boolean` - Whether the repeater item is expanded. (default: true)
- `isSelected`: `boolean | undefined` - Whether the repeater item's checkbox is selected.
When users select the repeater item, the specified property on your model is updated accordingly. (default: false)
- `itemName`: `string | undefined` - The human-readable name for the repeater item that is available for multiple purposes,
such as accessibility and instrumentation. For example, the component uses the name to
construct ARIA labels for the repeater item controls
to [support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If not specified, the repeater item's title will be used for this value.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

**Outputs:**

- `collapse`: `EventEmitter<void>` - Fires when users collapse the repeater item.
- `expand`: `EventEmitter<void>` - Fires when users expand the repeater item.
- `inlineFormClose`: `EventEmitter<SkyInlineFormCloseArgs>` - Fires when the repeater includes an inline form and users close it. This event emits
[a `SkyInlineFormCloseArgs` type](https://developer.blackbaud.com/skyux/components/inline-form#skyinlineformcloseargs-properties).
- `isSelectedChange`: `EventEmitter<boolean>` - Fires when users select or clear the checkbox for the repeater item.

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
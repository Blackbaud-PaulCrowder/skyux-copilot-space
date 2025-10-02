---
component: 'popover'
type: 'api-documentation'
description: 'API documentation for the popover component including components, interfaces, and types.'
---

# Popover API Documentation

## Components and Directives

#### HelpInlinePopoverExampleComponent

**Selector:** `app-help-inline-popover-example`

**Package:** `@skyux/code-examples`

#### PopoversDropdownBasicExampleComponent

**Selector:** `app-popovers-dropdown-basic-example`

**Package:** `@skyux/code-examples`

#### PopoversPopoverBasicExampleComponent

**Selector:** `app-popovers-popover-basic-example`

**Package:** `@skyux/code-examples`

#### PopoversPopoverProgrammaticExampleComponent

**Selector:** `app-popovers-popover-programmatic-example`

**Package:** `@skyux/code-examples`

#### SkyPopoverContentComponent

**Selector:** `sky-popover-content`

**Package:** `@skyux/popovers`

#### SkyPopoverComponent

**Selector:** `sky-popover`

**Package:** `@skyux/popovers`

**Inputs:**

- `popoverTitle`: `string | undefined` - The title for the popover.
- `alignment`: `SkyPopoverAlignment` - The horizontal alignment of the popover in relation to the trigger element.
The `skyPopoverAlignment` property on the popover directive takes precedence over this property when specified. (default: "center")
- `placement`: `SkyPopoverPlacement` - The placement of the popover in relation to the trigger element.
The `skyPopoverPlacement` property on the popover directive takes precedence over this property when specified. (default: "above")
- `popoverType`: `SkyPopoverType` - The type of popover. (default: "info")

**Outputs:**

- `popoverClosed`: `EventEmitter<SkyPopoverComponent>` - Fires when users close the popover.
- `popoverOpened`: `EventEmitter<SkyPopoverComponent>` - Fires when users open the popover.

#### SkyPopoverDirective

**Selector:** `[skyPopover]`

**Package:** `@skyux/popovers`

**Inputs:**

- `skyPopoverAlignment`: `SkyPopoverAlignment | undefined` - The horizontal alignment of the popover in relation to the trigger element.
- `skyPopoverPlacement`: `SkyPopoverPlacement | undefined` - The placement of the popover in relation to the trigger element.
- `skyPopover`: `SkyPopoverComponent | undefined` - The popover component to display. Add this directive to the trigger element that opens the popover.
- `skyPopoverMessageStream`: `Subject<SkyPopoverMessage>` - The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.
- `skyPopoverTrigger`: `SkyPopoverTrigger` - The user action that displays the popover.
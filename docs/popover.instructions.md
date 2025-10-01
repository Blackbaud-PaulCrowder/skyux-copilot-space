---
component: 'popover'
description: 'Design guidelines, API documentation, and usage instructions for the popover component extracted from SKY UX documentation.'
---

# Popover Component Guidelines

## Component Overview
Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.

## Usage

### ✅ Use when

Use popovers to display additional contextual content that is valuable some of the time.

### ❌ Don't use when

Don't use popovers when the content is valuable most of the time. Use persistent inline help instead.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

Don't use popovers when a large amount of content is necessary. Use a flyout instead.

## Anatomy

- Content area
- Highlight border
- Element pointer

## Options

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on click actions rather than mouseenter actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

## Behavior and states

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

## Content

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

Don't include a large amount of content, form inputs, or complex interactions.

## Layout

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

## Related information

### Guidelines

- User assistance

## API Documentation

### Components and Directives

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
- `skyPopover`: `SkyPopoverComponent | undefined` - The popover component to display. Add this directive to the trigger element that opens the popover. **[Required]**
- `skyPopoverMessageStream`: `Subject<SkyPopoverMessage>` - The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.
- `skyPopoverTrigger`: `SkyPopoverTrigger` - The user action that displays the popover.

#### SkyPopoverModule

**Package:** `@skyux/popovers`

#### SkyPopoverAlignment

Represents the horizontal alignment of the popover in relation to the trigger element.

**Package:** `@skyux/popovers`

#### SkyPopoverMessageType

The type of message to send to the popover component.

**Package:** `@skyux/popovers`

#### SkyPopoverMessage

Specifies messages to be sent to the popover component.

**Package:** `@skyux/popovers`

#### SkyPopoverPlacement

Represents the placement of the popover in relation to the trigger element.

**Package:** `@skyux/popovers`

#### SkyPopoverPosition

**Package:** `@skyux/popovers`

#### SkyPopoverTrigger

The user action that displays the popover.

**Package:** `@skyux/popovers`

⚠️ **This component is deprecated.**

#### SkyPopoverType

The style type of the popover.

**Package:** `@skyux/popovers`

#### SkyPopoversFixtureDropdownItem

**Package:** `@skyux/popovers/testing`

#### SkyPopoversFixtureDropdownMenu

**Package:** `@skyux/popovers/testing`

#### SkyPopoversFixtureDropdown

**Package:** `@skyux/popovers/testing`

#### SkyPopoverFixture

Provides information for and interaction with a SKY UX popover component.
By using the fixture API, a test insulates itself against updates to the internals
of a component, such as changing its DOM structure.

**Package:** `@skyux/popovers/testing`

⚠️ **This component is deprecated.**

#### SkyPopoverTestingModule

**Package:** `@skyux/popovers/testing`

#### SkyPopoverContentHarnessFilters

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyPopoverContentHarness

Harness for interacting with a popover content component in tests.

**Package:** `@skyux/popovers/testing`

#### SkyPopoverHarnessFilters

A set of criteria that can be used to filter a list of SkyPopoverHarness instances.

**Package:** `@skyux/popovers/testing`

#### SkyPopoverHarness

Harness for interacting with a popover component in tests.

**Package:** `@skyux/popovers/testing`

#### SkyGridColumnInlineHelpPopoverModelChange

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

### Code Examples

#### Help inline button with popover

**Selector:** `app-help-inline-popover-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline button with popover
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-popover-example',
  templateUrl: './example.component.html',
})
export class HelpInlinePopoverExampleComponent {}

```

**Template:**

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    popoverContent="The estimated income expected for the current year."
    popoverTitle="Projected revenue"
  />
</h3>

```

#### Dropdown with basic setup

**Selector:** `app-popovers-dropdown-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

interface DropdownItem {
  name: string;
  disabled: boolean;
}

/**
 * @title Dropdown with basic setup
 */
@Component({
  selector: 'app-popovers-dropdown-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDropdownModule],
})
export class PopoversDropdownBasicExampleComponent {
  protected items: DropdownItem[] = [
    { name: 'Option 1', disabled: false },
    { name: 'Disabled option', disabled: true },
    { name: 'Option 3', disabled: false },
    { name: 'Option 4', disabled: false },
    { name: 'Option 5', disabled: false },
  ];

  public actionClicked(action: string): void {
    alert(`You selected ${action}.`);
  }
}

```

**Template:**

```html
<sky-dropdown data-sky-id="dropdown-example" label="Test dropdown">
  <sky-dropdown-button> Show dropdown </sky-dropdown-button>
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>
<br />
<sky-dropdown buttonType="context-menu" label="Code example context menu">
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Popover with basic setup

**Selector:** `app-popovers-popover-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import {
  SkyPopoverAlignment,
  SkyPopoverModule,
  SkyPopoverPlacement,
} from '@skyux/popovers';

/**
 * @title Popover with basic setup
 */
@Component({
  selector: 'app-popovers-popover-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyPopoverModule],
})
export class PopoversPopoverBasicExampleComponent {
  public popoverAlignment: SkyPopoverAlignment | undefined;
  public popoverBody = 'This is a popover.';
  public popoverPlacement: SkyPopoverPlacement | undefined;
  public popoverTitle: string | undefined = 'Did you know?';
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  data-sky-id="popover-example"
  type="button"
  [skyPopover]="myPopover"
  [skyPopoverAlignment]="popoverAlignment"
  [skyPopoverPlacement]="popoverPlacement"
>
  Open popover
</button>

<sky-popover #myPopover [popoverTitle]="popoverTitle">
  {{ popoverBody }}
</sky-popover>

```

#### Popover with programmatic interactions

**Selector:** `app-popovers-popover-programmatic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';
import {
  SkyPopoverMessage,
  SkyPopoverMessageType,
  SkyPopoverModule,
} from '@skyux/popovers';

import { Subject } from 'rxjs';

/**
 * @title Popover with programmatic interactions
 */
@Component({
  selector: 'app-popovers-popover-programmatic-example',
  templateUrl: './example.component.html',
  imports: [SkyHelpInlineModule, SkyPopoverModule],
})
export class PopoversPopoverProgrammaticExampleComponent {
  protected popoverController = new Subject<SkyPopoverMessage>();

  #popoverOpen = false;

  protected onPopoverStateChange(isOpen: boolean): void {
    this.#popoverOpen = isOpen;
  }

  protected openPopover(): void {
    if (!this.#popoverOpen) {
      this.#sendMessage(SkyPopoverMessageType.Open);
    }
  }

  #sendMessage(type: SkyPopoverMessageType): void {
    const message: SkyPopoverMessage = { type };
    this.popoverController.next(message);
  }
}

```

**Template:**

```html
<sky-help-inline
  ariaLabel="Information about Popover using message stream"
  [skyPopover]="myPopover"
  [skyPopoverMessageStream]="popoverController"
/>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openPopover()"
>
  Open popover with message stream
</button>

<sky-popover
  #myPopover
  (popoverClosed)="onPopoverStateChange(false)"
  (popoverOpened)="onPopoverStateChange(true)"
>
  This is a popover.
</sky-popover>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
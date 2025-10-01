---
component: 'help-inline'
description: 'Design guidelines, API documentation, and usage instructions for the help-inline component extracted from SKY UX documentation.'
---

# Help Inline Component Guidelines

## Component Overview
The help inline button beside a field or other item lets users display more information about that item.

## Usage

### ✅ Use when

Use help inline buttons to invoke help content that users don't need to see every time or that is too long for persistent inline help. This provides access to supplementary information while avoiding most of the visual noise that comes with persistent inline help.

Use help inline buttons when users may need initial assistance but:

- The tasks are performed frequently.
- Ramifications of mistakes are small.

### ❌ Don't use when

Don't use help inline buttons when a small amount of persistent inline text can help users understand tasks. Use persistent inline help instead when:

- Tasks are complex and performed infrequently.
- User actions have far-reaching consequences that are not obvious.

## Options

### Popover

Display help content in popovers when a small amount of user assistance content is valuable some of the time. For larger amounts of user assistance, use the helpKey option instead to display content in a flyout or in the help widget, which is for internal Blackbaud use only.

### Help widget or other container

For longer help content that doesn't fit in popovers, use the helpKey option. Blackbaud developers use helpKey to open content in the help widget, which is for internal Blackbaud use only, and it can be also launch content in other containers, such as flyouts or new windows. To launch content from help inline buttons, see global help.

## Layout

### Page-level and modal-level help

For complex tasks where users need comprehensive documentation, they invoke help at the page or modal level.

In Blackbaud solutions, users invoke help from the omnibar or a modal heading. To display context-sensitive help content, Blackbaud developers use the help widget, which is for internal Blackbaud use only.

### Element-level help

Place the help inline button to the right of the label for the element that the help content supports.

**✅ Do use help inline buttons to invoke element-specific help content.**

## Related information

### Guidelines

- Form design

### Components

- Box
- Data entry grid
- Data grid
- Description list
- File attachment
- File drop
- Flyout
- Input box
- Key info
- Modal
- Passive progress indicator
- Popover
- Single file attachment
- Status indicator
- Text editor
- Tile
- Toggle switch
- Waterfall progress indicator

## API Documentation

### Components and Directives

#### HelpInlineActionClickExampleComponent

**Selector:** `app-help-inline-action-click-example`

**Package:** `@skyux/code-examples`

#### HelpInlineHelpKeyExampleComponent

**Selector:** `app-help-inline-help-key-example`

**Package:** `@skyux/code-examples`

#### HelpInlinePopoverExampleComponent

**Selector:** `app-help-inline-popover-example`

**Package:** `@skyux/code-examples`

#### SkyHelpInlineComponent

Inserts a help button beside an element, such as a field, to display contextual information about the element.

**Selector:** `sky-help-inline`

**Package:** `@skyux/help-inline`

**Inputs:**

- `ariaControls`: `string | undefined` - The ID of the element that the help inline button controls.
This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure).
For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).
- `ariaExpanded`: `boolean | undefined` - Whether an element or popover controlled by the help inline button is expanded. If popoverContent is specified,
this value is overridden with popover expanded status.
- `ariaLabel`: `string | undefined` - The ARIA label for the help inline button. This sets the button's `aria-label` to provide a text equivalent for screen readers.
Will be overridden if label text is set. (default: "Show help content")
- `helpKey`: `string | undefined` - A unique key that identifies the [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help) content to display when the button is clicked.
- `labelledBy`: `string | undefined` - The ID of the element associated with the help inline button. This is used to set the button's `aria-labelledby`
to provides a text equivalent for screen readers. Takes precedence over `ariaLabel` and `labelText` inputs.
- `popoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, clicking the help inline button opens a popover with this content and optional title.
- `popoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `popoverContent` is
also specified.
- `labelText`: `string | undefined` - The label of the component the help inline button is attached to.

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when the user clicks the help inline button.

#### SkyHelpInlineModule

**Package:** `@skyux/help-inline`

#### SkyHelpInlineHarnessFilters

A set of criteria that can be used to filter a list of `SkyHelpInlineHarness` instances.

**Package:** `@skyux/help-inline/testing`

#### SkyHelpInlineHarness

Harness for interacting with a help inline button component in tests.

**Package:** `@skyux/help-inline/testing`

#### SkyHelpInlineHarnessFilters

A set of criteria that can be used to filter a list of SkyHelpInlineHarness instances.

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

#### SkyHelpInlineHarness

Harness for interacting with a help inline component in tests.

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

### Code Examples

#### Help inline button with action click

**Selector:** `app-help-inline-action-click-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline button with action click
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-action-click-example',
  templateUrl: './example.component.html',
})
export class HelpInlineActionClickExampleComponent {
  public onActionClick(): void {
    alert('Use help inline to show supplemental information to the user.');
  }
}

```

**Template:**

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    (actionClick)="onActionClick()"
  />
</h3>

```

#### Help inline with help key

**Selector:** `app-help-inline-help-key-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline with help key
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-help-key-example',
  templateUrl: './example.component.html',
})
export class HelpInlineHelpKeyExampleComponent {}

```

**Template:**

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    helpKey="projected-revenue"
  />
</h3>

```

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
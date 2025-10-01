---
component: 'key-info'
description: 'Design guidelines, API documentation, and usage instructions for the key-info component extracted from SKY UX documentation.'
---

# Key Info Component Guidelines

## Component Overview
The key info component highlights important summary information.

## Usage

### ✅ Use when

Use key info to highlight important summary information.

Use key info to show the total number of items in a list. Use the horizontal layout and place the key info at the top of the list.

### ❌ Don't use when

Don't use key info when different data visualizations are more appropriate for large amounts of data. For example, don't group multiple key info components to track how data changes over time. Use alternative visualizations such as data grids, bar charts, or line charts instead.

Don't use key info when data doesn't require user attention or doesn't drive user action. Use description lists instead.

## Anatomy

- Value
- Label
- Help inline button

## Options

### Layout

Use the default vertical layout with the label under the value in most situations.

Use the horizontal layout with the label beside the value for scenarios where vertical space is at a premium. For example, use the horizontal layout and the small size to display the total number of items in a list.

### Size

Use the large key info when the values need to stand out in places such as data visualizations, dashboards, and landing pages.

Use the small key info to highlight information that doesn't require the large size to stand out, such as the total number of items in a list.

### Help inline button

When you need to supplement a key info label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

## Behavior and states

### Link styling

You can style the key info component as a link to let users select the value to navigate to a different location.

## Layout

### Horizontal layout

When laying out key info components horizontally:

- Use "sky-margin-inline-xxl" for consistent spacing between elements.
- Don't overwhelm users with more than 6 elements without headings or grouping.

## Related information

### Components

- Description list
- Help inline button

### Guidelines

- Call out information

## API Documentation

### Components and Directives

#### IndicatorsKeyInfoBasicExampleComponent

**Selector:** `app-indicators-key-info-basic-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `value`: `number | undefined`

#### IndicatorsKeyInfoHelpKeyExampleComponent

**Selector:** `app-indicators-key-info-help-key-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `value`: `number | undefined`

#### SkyKeyInfoLabelComponent

Specifies a label to display in smaller text under or beside the value.
To display a help button beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-key-info` element and a `sky-control-help` CSS class on that help button element.

**Selector:** `sky-key-info-label`

**Package:** `@skyux/indicators`

#### SkyKeyInfoLayoutType

**Package:** `@skyux/indicators`

#### SkyKeyInfoValueComponent

Specifies a value to display in larger, bold text.

**Selector:** `sky-key-info-value`

**Package:** `@skyux/indicators`

#### SkyKeyInfoComponent

**Selector:** `sky-key-info`

**Package:** `@skyux/indicators`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
placed beside the key info. Clicking the button invokes global help as configured by the application.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the key info. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `layout`: `SkyKeyInfoLayoutType | undefined` - The layout for the key info. The vertical layout places the label under the
value, while the horizontal layout places the label beside the value. (default: "vertical")

#### SkyKeyInfoModule

**Package:** `@skyux/indicators`

#### SkyKeyInfoHarnessFilters

A set of criteria that can be used to filter a list of SkyKeyInfoHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyKeyInfoHarness

Harness for interacting with a key info component in tests.

**Package:** `@skyux/indicators/testing`

#### SkyPageSummaryKeyInfoComponent

Highlights important information about a page in the key information section of the
page summary.

**Selector:** `sky-page-summary-key-info`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

### Code Examples

#### Key info with basic setup

**Selector:** `app-indicators-key-info-basic-example`

**TypeScript:**

```typescript
import { Component, Input } from '@angular/core';
import { SkyKeyInfoLayoutType, SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Key info with basic setup
 */
@Component({
  selector: 'app-indicators-key-info-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule],
})
export class IndicatorsKeyInfoBasicExampleComponent {
  @Input()
  public set value(value: number | undefined) {
    this.#_value = value;

    this.layout =
      this.#_value && this.#_value >= 100 ? 'vertical' : 'horizontal';
  }

  public get value(): number | undefined {
    return this.#_value;
  }

  protected layout: SkyKeyInfoLayoutType = 'vertical';

  #_value: number | undefined = 575;
}

```

**Template:**

```html
<sky-key-info
  data-sky-id="key-info-example"
  helpPopoverTitle="Help"
  [layout]="layout"
  [helpPopoverContent]="helpContent"
>
  <sky-key-info-value class="sky-font-display-3">
    {{ value }}
  </sky-key-info-value>
  <sky-key-info-label> New members </sky-key-info-label>
</sky-key-info>
<ng-template #helpContent>
  This help content can add clarity and provide next steps.
</ng-template>

```

#### Key info with help key

**Selector:** `app-indicators-key-info-help-key-example`

**TypeScript:**

```typescript
import { Component, Input } from '@angular/core';
import { SkyKeyInfoLayoutType, SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Key info with help key
 */
@Component({
  selector: 'app-indicators-key-info-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule],
})
export class IndicatorsKeyInfoHelpKeyExampleComponent {
  @Input()
  public set value(value: number | undefined) {
    this.#_value = value;

    this.layout =
      this.#_value && this.#_value >= 100 ? 'vertical' : 'horizontal';
  }

  public get value(): number | undefined {
    return this.#_value;
  }

  protected layout: SkyKeyInfoLayoutType = 'vertical';

  #_value: number | undefined = 575;
}

```

**Template:**

```html
<sky-key-info
  data-sky-id="key-info-example"
  helpKey="new-member-help"
  [layout]="layout"
>
  <sky-key-info-value class="sky-font-display-3">
    {{ value }}
  </sky-key-info-value>
  <sky-key-info-label> New members </sky-key-info-label>
</sky-key-info>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
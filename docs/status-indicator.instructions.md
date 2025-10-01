---
component: 'status-indicator'
description: 'Design guidelines, API documentation, and usage instructions for the status-indicator component extracted from SKY UX documentation.'
---

# Status Indicator Component Guidelines

## Component Overview
Status indicators highlight important status information that users need to address.

## Usage

### ✅ Use when

Use status indicators when users must address or be aware of important information while completing tasks.

Use status indicators to call out important status information for items in a list or specific properties on a record.

Use status indicators to highlight validation errors on input fields.

### ❌ Don't use when

Don't use status indicators to highlight statuses in the page summary. Use labels instead.

Don't use status indicators when no user action is necessary and status information is not important enough to highlight. Use plain text instead to avoid the overuse of status indicators.

## Anatomy

- Icon
- Text label
- Help inline button

## Options

### Status type

### Description type

Use a description type with status indicators to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

### Help inline button

When you need to supplement a status indicator label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

## Related information

### Components

- Alert
- Help inline button
- Label
- Toast

### Guidelines

- Call out information

## API Documentation

### Components and Directives

#### IndicatorsStatusIndicatorBasicExampleComponent

**Selector:** `app-indicators-status-indicator-basic-example`

**Package:** `@skyux/code-examples`

#### IndicatorsStatusIndicatorHelpKeyExampleComponent

**Selector:** `app-indicators-status-indicator-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyStatusIndicatorComponent

Displays status text with an icon matching the specified indicator type.
To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-status-indicator` element and a `sky-control-help`
CSS class on that help button element.

**Selector:** `sky-status-indicator`

**Package:** `@skyux/indicators`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
placed beside the status indicator label. Clicking the button invokes global help as configured by the application.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the status indicator. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `customDescription`: `string | undefined` - The text to be read by screen readers for users who cannot see
the indicator icon when `descriptionType` is `custom`.
- `descriptionType`: `SkyIndicatorDescriptionType | undefined` - The predefined text to be read by screen readers for users who
cannot see the indicator icon. **[Required]**
- `indicatorType`: `SkyIndicatorIconType` - The style for the status indicator, which determines the icon. (default: "warning")

#### SkyStatusIndicatorModule

**Package:** `@skyux/indicators`

#### SkyStatusIndicatorHarnessFilters

A set of criteria that can be used to filter a list of SkyStatusIndicatorHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyStatusIndicatorHarness

Harness for interacting with a status indicator component in tests.

**Package:** `@skyux/indicators/testing`

### Code Examples

#### Status indicator with basic setup

**Selector:** `app-indicators-status-indicator-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Status indicator with basic setup
 */
@Component({
  selector: 'app-indicators-status-indicator-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyStatusIndicatorModule],
})
export class IndicatorsStatusIndicatorBasicExampleComponent {}

```

**Template:**

```html
<sky-status-indicator
  data-sky-id="status-indicator-error"
  descriptionType="error"
  indicatorType="danger"
>
  Danger status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-important-info"
  descriptionType="important-info"
  indicatorType="info"
>
  Info status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-completed"
  descriptionType="completed"
  indicatorType="success"
>
  Success status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-warning"
  descriptionType="warning"
  indicatorType="warning"
>
  Warning status indicator
</sky-status-indicator>

<sky-status-indicator
  customDescription="Custom warning"
  data-sky-id="status-indicator-custom"
  descriptionType="custom"
  indicatorType="warning"
>
  Warning status indicator with custom screen reader description
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-error-with-help"
  descriptionType="error"
  indicatorType="danger"
  helpPopoverContent="
    This contextual help can provide more information about
    the status as well as possible next steps."
>
  Danger status indicator with help
</sky-status-indicator>

```

#### Status indicator with help key

**Selector:** `app-indicators-status-indicator-help-key-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Status indicator with help key
 */
@Component({
  selector: 'app-indicators-status-indicator-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyStatusIndicatorModule],
})
export class IndicatorsStatusIndicatorHelpKeyExampleComponent {}

```

**Template:**

```html
<sky-status-indicator
  data-sky-id="status-indicator-error"
  descriptionType="error"
  indicatorType="danger"
>
  Danger status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-important-info"
  descriptionType="important-info"
  indicatorType="info"
>
  Info status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-completed"
  descriptionType="completed"
  indicatorType="success"
>
  Success status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-warning"
  descriptionType="warning"
  indicatorType="warning"
>
  Warning status indicator
</sky-status-indicator>

<sky-status-indicator
  customDescription="Custom warning"
  data-sky-id="status-indicator-custom"
  descriptionType="custom"
  indicatorType="warning"
>
  Warning status indicator with custom screen reader description
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-error-with-help-key"
  descriptionType="error"
  indicatorType="danger"
  helpKey="danger-help"
>
  Danger status indicator with help key
</sky-status-indicator>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
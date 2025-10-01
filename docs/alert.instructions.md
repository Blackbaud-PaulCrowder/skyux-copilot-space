---
component: 'alert'
description: 'Design guidelines, API documentation, and usage instructions for the alert component extracted from SKY UX documentation.'
---

# Alert Component Guidelines

## Component Overview
Alerts highlight critical information that users absolutely must see when they visit a page.

## Usage

### ✅ Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

**✅ Do use alerts when users need to view information before the rest of the page.**

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

**✅ Do use alerts for information that is important in the current context.**

### ❌ Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use labels or status indicators instead.

**❌ Don't use alerts to highlight statuses on records or pages.**

Don't use alerts to display messages about the success or failure of user actions. Use toasts instead.

**❌ Don't use alerts to highlight the outcomes of user actions.**

## Anatomy

- Alert icon
- Text
- Close button

## Options

### Alert type

Use the danger alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

Use the warning alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

Use the success alert for messages that convey a positive or successful state.

Use the info alert for messages that provide helpful information or context but do not require user action.

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

## Content

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

## Layout

Always place alerts at the top of the page above the page header.

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

**❌ Don't accumulate multiple alerts at the top of a page.**

## Related information

### Components

- Label
- Status indicator
- Toast

### Guidelines

- Call out information

## API Documentation

### Components and Directives

#### IndicatorsAlertBasicExampleComponent

**Selector:** `app-indicators-alert-basic-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `days`: `number` (default: 9)

#### SkyAlertComponent

**Selector:** `sky-alert`

**Package:** `@skyux/indicators`

**Inputs:**

- `closeable`: `boolean | undefined` - Whether to include a close button for users to dismiss the alert. (default: false)
- `closed`: `boolean | undefined` - Whether the alert is closed. (default: false)
- `alertType`: `SkyIndicatorIconType | undefined` - The style for the alert, which determines the icon and background color.
The valid options are `danger`, `info`, `success`, and `warning`. (default: "warning")
- `customDescription`: `string | undefined` - The text to be read by screen readers for users who cannot see
the indicator icon when `descriptionType` is `custom`.
- `descriptionType`: `SkyIndicatorDescriptionType | undefined` - The predefined text to be read by screen readers for users who cannot see the alert icon.
This property is optional but will be required in future versions of SKY UX.

**Outputs:**

- `closedChange`: `EventEmitter<boolean>` - Fires when users close the alert.

#### SkyAlertModule

**Package:** `@skyux/indicators`

#### SkyAlertFixture

Allows interaction with a SKY UX alert component.

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

#### SkyAlertHarnessFilters

A set of criteria that can be used to filter a list of SkyAlertHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyAlertHarness

Harness for interacting with an alert component in tests.

**Package:** `@skyux/indicators/testing`

#### SkyPageSummaryAlertComponent

Displays messages that require immediate attention as [alerts](https://developer.blackbaud.com/skyux/components/alert) within
the page summary.

**Selector:** `sky-page-summary-alert`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageHeaderAlertsComponent

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

**Selector:** `sky-page-header-alerts`

**Package:** `@skyux/pages`

### Code Examples

#### Alert with basic setup

**Selector:** `app-indicators-alert-basic-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, Input } from '@angular/core';
import { SkyAlertModule } from '@skyux/indicators';

/**
 * @title Alert with basic setup
 */
@Component({
  selector: 'app-indicators-alert-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyAlertModule],
})
export class IndicatorsAlertBasicExampleComponent {
  @Input()
  public days = 9;

  protected onClosedChange(event: boolean): void {
    alert(`Alert closed with: ${event}`);
  }
}

```

**Template:**

```html
<sky-alert
  data-sky-id="alert-example"
  [alertType]="days < 8 ? 'danger' : 'warning'"
  [closeable]="days >= 8"
  [descriptionType]="days < 8 ? 'danger' : 'important-warning'"
  (closedChange)="onClosedChange($event)"
>
  Your password expires in {{ days }} day(s)!
</sky-alert>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
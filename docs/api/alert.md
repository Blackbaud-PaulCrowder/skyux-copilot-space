---
component: 'alert'
type: 'api-documentation'
description: 'API documentation for the alert component including components, interfaces, and types.'
---

# Alert API Documentation

## Components and Directives

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

#### SkyPageSummaryAlertComponent

Displays messages that require immediate attention as [alerts](https://developer.blackbaud.com/skyux/components/alert) within
the page summary.

**Selector:** `sky-page-summary-alert`

**Package:** `@skyux/layout`

#### SkyPageHeaderAlertsComponent

Displays alerts within the page header and applies spacing between alerts. Appears above the page title.

**Selector:** `sky-page-header-alerts`

**Package:** `@skyux/pages`
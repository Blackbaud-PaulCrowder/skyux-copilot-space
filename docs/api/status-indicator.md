---
component: 'status-indicator'
type: 'api-documentation'
description: 'API documentation for the status-indicator component including components, interfaces, and types.'
---

# Status Indicator API Documentation

## Components and Directives

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
cannot see the indicator icon.
- `indicatorType`: `SkyIndicatorIconType` - The style for the status indicator, which determines the icon. (default: "warning")
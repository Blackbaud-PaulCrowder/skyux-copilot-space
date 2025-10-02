---
component: 'key-info'
type: 'api-documentation'
description: 'API documentation for the key-info component including components, interfaces, and types.'
---

# Key Info API Documentation

## Components and Directives

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

#### SkyPageSummaryKeyInfoComponent

Highlights important information about a page in the key information section of the
page summary.

**Selector:** `sky-page-summary-key-info`

**Package:** `@skyux/layout`
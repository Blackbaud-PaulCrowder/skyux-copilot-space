---
component: 'wait'
type: 'api-documentation'
description: 'API documentation for the wait component including components, interfaces, and types.'
---

# Wait API Documentation

## Components and Directives

#### IndicatorsWaitElementExampleComponent

**Selector:** `app-indicators-wait-element-example`

**Package:** `@skyux/code-examples`

#### IndicatorsWaitPageExampleComponent

**Selector:** `app-indicators-wait-page-example`

**Package:** `@skyux/code-examples`

#### SkyWaitComponent

**Selector:** `sky-wait`

**Package:** `@skyux/indicators`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the wait icon.
This sets the icon's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility) when an element or page loads and when users tab to a wait icon.
The default value varies based on whether the wait is for an element or a page and whether it is a blocking wait. For example, the default for a page-level blocking wait is "Page loading. Please wait."
For element-level waits, we recommend that consumers overwrite the default to describe the specific element.
"For more information, see the Design tab and the [WAI-ARIA `aria-label` definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `isFullPage`: `boolean | undefined` - When set to `true`, wait indication appears on the page level instead of the
parent element level. We recommend that you use the `beginBlockingPageWait` or
`beginNonBlockingPageWait` functions of the `SkyWaitService` instead of setting this
on the component level. (default: false)
- `isNonBlocking`: `boolean | undefined` - When set to `true`, wait indication appears in the bottom left corner of the element
instead of hiding the entire parent element. (default: false)
- `isWaiting`: `boolean | undefined` - When set to `true`, wait indication appears on the parent element of the `sky-wait` component.
- `screenReaderCompletedText`: `string | undefined` - Screen reader text [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility) when the wait toggles off.
 The default varies based on whether the wait is for an element or a page.
For example, the default for a page-level wait is "Page loading complete."
For element-level waits, we recommend that consumers overwrite the default to describe the specific element.
For more information, see the Design tab and the [WCAG documentation on status messages](https://www.w3.org/WAI/WCAG21/Understanding/status-messages.html).
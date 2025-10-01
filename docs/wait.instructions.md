---
component: 'wait'
description: 'Design guidelines, API documentation, and usage instructions for the wait component extracted from SKY UX documentation.'
---

# Wait Component Guidelines

## Component Overview
The wait component and service create waits on individual elements and on pages.

## Accessibility

### Text equivalents

The wait component provides default text equivalents for screen readers to support accessibility. These ARIA values are available when users tab to a wait icon, when a wait loads, and when a wait closes. For page-level waits, the default values are sufficient for most scenarios, but for element-level waits, we recommend more specific text equivalents to describe the elements.

For example, element-level nonblocking waits default to "Loading." when they initially load and to "Loading complete." when loading finishes. If multiple elements on a page require waits, then screen readers repeat these generic messages. To support users of assistive technologies, we recommend more descriptive values, such as "Gift details loading." and "Loading complete for gift details."

### Focus

When a focused element on a page is placed in a waiting state, focus automatically shifts to the page's body element. If the waiting state for that element finishes before any additional change in focus, then the focus automatically reverts to the previously focused element.

## API Documentation

### Components and Directives

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

#### SkyWaitModule

**Package:** `@skyux/indicators`

#### SkyWaitService

**Package:** `@skyux/indicators`

#### SkyWaitFixture

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

#### SkyWaitHarnessFilters

A set of criteria that can be used to filter a list of SkyWaitHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyWaitHarness

Harness for interacting with a wait component in tests.

**Package:** `@skyux/indicators/testing`

### Code Examples

#### Wait applied to an element

**Selector:** `app-indicators-wait-element-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyWaitModule } from '@skyux/indicators';

/**
 * @title Wait applied to an element
 */
@Component({
  selector: 'app-indicators-wait-element-example',
  styles: `
    .wrapper {
      height: 200px;
      width: 200px;
      margin: 10px;
    }
  `,
  templateUrl: './example.component.html',
  imports: [SkyWaitModule],
})
export class IndicatorsWaitElementExampleComponent {
  protected isWaiting = false;
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="isWaiting = !isWaiting"
>
  Toggle wait
</button>

<div class="wrapper">
  The <code>sky-wait</code> directive can apply to a large area.
  <sky-wait data-sky-id="wait-example" [isWaiting]="isWaiting" />
</div>

```

#### Wait applied to a page

**Selector:** `app-indicators-wait-page-example`

**TypeScript:**

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';

/**
 * @title Wait applied to a page
 */
@Component({
  standalone: true,
  selector: 'app-indicators-wait-page-example',
  templateUrl: './example.component.html',
})
export class IndicatorsWaitPageExampleComponent implements OnDestroy {
  protected isWaiting = false;

  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#waitSvc.dispose();
  }

  protected togglePageWait(isBlocking: boolean): void {
    if (!this.isWaiting) {
      if (isBlocking) {
        this.#waitSvc.beginBlockingPageWait();
      } else {
        this.#waitSvc.beginNonBlockingPageWait();
      }
    } else if (isBlocking) {
      this.#waitSvc.endBlockingPageWait();
    } else {
      this.#waitSvc.endNonBlockingPageWait();
    }

    this.isWaiting = !this.isWaiting;
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(true)"
>
  Show page wait
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(false)"
>
  Show non-blocking page wait
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
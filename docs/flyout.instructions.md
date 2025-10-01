---
component: 'flyout'
description: 'Design guidelines, API documentation, and usage instructions for the flyout component extracted from SKY UX documentation.'
---

# Flyout Component Guidelines

## Component Overview
Flyouts display large quantities of supplementary information related to a task.

## Usage

### ✅ Use when

Use flyouts to display large amounts of supplementary information related to user tasks. The flyout container slides out from the side of the page and lays over page content. It can contain lists, record views, graphs, or other information displays.

**✅ Do use flyouts to display large amounts of supplementary information related to user tasks.**

Use flyouts to drill into analytical insights so that users can quickly glance into what makes up those insights without spawning new workflows.

**✅ Do use flyouts to let users drill into analytical insights.**

Use flyouts to drill into child records so that users can retain the context of the parent records. Flyouts only cover part of the page, so users can refer to the page for context.

**✅ Do use flyouts to drill into child records.**

### ❌ Don't use when

Don't use flyouts to navigate from one record to another instance of the same record type. For example, if users on a constituent record select a link to a different constituent record, navigate to the new record. Do not open it in a flyout.

**❌ Don't use flyouts to navigate from one record to another instance of the same record type.**

Don't use flyouts to navigate from a child page to its parent page. For example, if users on a gift record select a link to return to a constituent record, navigate to a full-page view of the constituent record. Do not open it in a flyout.

**❌ Don't use flyouts to navigate from a child page to its parent page.**

Don't use flyouts when another flyout is already open. If users select a link in a flyout, close the flyout and navigate to the new link location. In other words, limit flyouts to a single drill-in. On further drilling, open a full page.

**❌ Don't use flyouts when another flyout is already open.**

Don't use flyouts on pages that don't make sense when it closes. For example, on a page to enter grades for a class of students, displaying the names of students doesn't provide value without the grade entry form, so don't use a flyout to display the grade entry form.

**❌ Don't use flyouts to display essential information.**

Don't use flyouts to display small amounts of additional information. Flyouts are for large amounts of supplementary information. To display smaller amounts of information, use a popover component or an expandable repeater.

**❌ Don't use flyouts for small amounts of additional information.**

Don't use flyouts to display items that need a long time to load such as system-generated reports. Instead, let users continue to use the system, and use toasts to let them know when the content is available.

**❌ Don't use flyouts for items that take a long time to load.**

Don't use flyouts to link to external sites. Open external sites in new tabs. For example, when users select a constituent address, a Google map of that address opens in a new tab.

**❌ Don't use flyouts to display external content.**

Don't use flyouts for tasks where users require a full-screen view of details or where they take multiple actions within the view. Navigate to a full page instead.

**❌ Don't use flyouts for tasks that require a full-screen view.**

## Behavior and states

### Background page remains active

The background page remains active behind a flyout. When users select a link on the background page to open another record in a list, the flyout loads the new record. When users select a link inside the flyout, the system navigates away from the current page.

When users select a non-interactive element on the background page, the flyout closes. However, when users select a non-interactive element on the background page on touch devices, the flyout does not close because users need to be able touch the background page in order to scroll.

### Independent scrolling

The flyout and its background page scroll independently. When users touch, hover, or focus on the background page, only the background content scrolls. Similarly, when users touch, hover, or focus on the flyout, only the flyout scrolls. This allows users to adjust the content in the flyout without losing context from the page.

### Drag to resize

Users can select the flyout's left border and drag it to adjust the size. The size can range from 320px to 20px less than the full screen size. If users expand the flyout to the full screen size, it slides 20px to the right to keep a portion of the background page in view. The default size is 50 percent of the screen or 320px, whichever is larger. When users resize the panel, the system remembers their preferred size globally.

### Help panel

The flyout covers the omnibar, but the help panel remains visible in the upper right corner of the screen. The help panel should recognize that the flyout is open and provide appropriate guidance based on the context.

### Modal dialog behavior

When users perform actions in the flyout to launch modal dialogs, the modal dialogs should cover the entire page.

### Responsiveness

Do not use a flyout when a screen is smaller than 480px. At smaller resolutions, the flyout covers too much of the screen and loses much of its value. For smaller screen sizes, navigate directly to the appropriate record or list.

## Options

### Next and previous buttons

When a flyout opens records in a list, you can include buttons in the toolbar to open the next record or previous record. For example, if users open a flyout on a constituent record to view the first gift in a list of gifts, the next button opens the second gift in the list. When you include the next and previous buttons in the flyout toolbar, a visual indicator highlights the currently selected row on the page.

### List toolbar

When a flyout displays a list, you can include an option in the toolbar to leave the "preview" list and create a new list for further manipulation. The create list button navigates to a new page that contains the new list.

## Accessibility

## Related information

### Guidelines

- Content containers

## API Documentation

### Components and Directives

#### FlyoutBasicExampleComponent

**Selector:** `app-flyout-basic-example`

**Package:** `@skyux/code-examples`

#### FlyoutCustomHeadersExampleComponent

**Selector:** `app-flyout-custom-headers-example`

**Package:** `@skyux/code-examples`

#### SkyFlyoutInstance

Represents a single displayed flyout.

**Package:** `@skyux/flyout`

#### SkyFlyoutComponent

**Selector:** `sky-flyout`

**Package:** `@skyux/flyout`

#### SkyFlyoutModule

**Package:** `@skyux/flyout`

#### SkyFlyoutLegacyService

Launches flyouts and provides a common look and feel.
This service dynamically generates the flyout component and appends it directly to the
document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

**Package:** `@skyux/flyout`

⚠️ **This component is deprecated.**

#### SkyFlyoutService

Launches flyouts and provides a common look and feel.
This service dynamically generates the flyout component and appends it directly to the
document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

**Package:** `@skyux/flyout`

#### SkyFlyoutAction

**Package:** `@skyux/flyout`

#### SkyFlyoutBeforeCloseHandler

Handler for notifying the flyout when it is appropriate to close the flyout. This will be returned from the flyout instance's `beforeClose` observable.

**Package:** `@skyux/flyout`

#### SkyFlyoutCloseArgs

Arguments used when closing a flyout programmatically.

**Package:** `@skyux/flyout`

#### SkyFlyoutConfig

Specifies the configuration options to set up a flyout.

**Package:** `@skyux/flyout`

#### SkyFlyoutMessageType

**Package:** `@skyux/flyout`

#### SkyFlyoutMessage

**Package:** `@skyux/flyout`

#### SkyFlyoutPermalink

**Package:** `@skyux/flyout`

#### SkyFlyoutHarness

Harness for interacting with a flyout component in tests.

**Package:** `@skyux/flyout/testing`

### Code Examples

#### Flyout with basic setup

**Selector:** `app-flyout-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyFlyoutInstance, SkyFlyoutService } from '@skyux/flyout';

import { FlyoutComponent } from './flyout.component';

/**
 * @title Flyout with basic setup
 */
@Component({
  standalone: true,
  selector: 'app-flyout-basic-example',
  templateUrl: './example.component.html',
})
export class FlyoutBasicExampleComponent {
  #flyout: SkyFlyoutInstance<FlyoutComponent> | undefined;

  readonly #flyoutSvc = inject(SkyFlyoutService);

  protected closeAndRemoveFlyout(): void {
    if (this.#flyout?.isOpen) {
      this.#flyoutSvc.close();
    }

    this.#flyout = undefined;
  }

  public openFlyoutWithCustomWidth(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
      defaultWidth: 350,
      maxWidth: 500,
      minWidth: 200,
    });

    this.#flyout.closed.subscribe(() => {
      this.#flyout = undefined;
    });
  }

  protected openSimpleFlyout(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
    });

    this.#flyout.closed.subscribe(() => {
      this.#flyout = undefined;
    });
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openSimpleFlyout()"
>
  Open flyout
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openFlyoutWithCustomWidth()"
>
  Open flyout with custom width
</button>

<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="closeAndRemoveFlyout()"
>
  Close flyout programmatically
</button>

```

#### Flyouts with customized headers

**Selector:** `app-flyout-custom-headers-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyFlyoutInstance, SkyFlyoutService } from '@skyux/flyout';

import { FlyoutComponent } from './flyout.component';

/**
 * @title Flyouts with customized headers
 */
@Component({
  standalone: true,
  selector: 'app-flyout-custom-headers-example',
  templateUrl: './example.component.html',
})
export class FlyoutCustomHeadersExampleComponent {
  public recordNumber = 0;
  public primaryActionCallback(): void {
    alert('Primary action clicked!');
  }

  #flyout: SkyFlyoutInstance<FlyoutComponent> | undefined;

  readonly #flyoutSvc = inject(SkyFlyoutService);

  public openFlyoutWithIterators(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
      showIterator: true,
      iteratorNextButtonDisabled: this.#nextButtonDisabled(),
      iteratorPreviousButtonDisabled: this.#previousButtonDisabled(),
    });

    this.#flyout.iteratorNextButtonClick.subscribe(() => {
      alert('Next iterator button clicked!');
      this.recordNumber += 1;
      this.#flyout!.iteratorNextButtonDisabled = this.#nextButtonDisabled();
      this.#flyout!.iteratorPreviousButtonDisabled =
        this.#previousButtonDisabled();
    });

    this.#flyout.iteratorPreviousButtonClick.subscribe(() => {
      alert('Previous iterator button clicked!');
      this.recordNumber -= 1;
      this.#flyout!.iteratorNextButtonDisabled = this.#nextButtonDisabled();
      this.#flyout!.iteratorPreviousButtonDisabled =
        this.#previousButtonDisabled();
    });

    this.#flyout.closed.subscribe(() => {
      this.#flyout = undefined;
    });
  }

  public openFlyoutWithPrimaryAction(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
      primaryAction: {
        label: 'Save',
        callback: () => {
          this.primaryActionCallback();
        },
      },
    });
  }

  public openFlyoutWithRoutePermalink(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
      permalink: {
        label: 'Go to Components page',
        route: {
          commands: ['/components'],
          extras: {
            fragment: 'helloWorld',
            queryParams: {
              foo: 'bar',
            },
          },
        },
      },
    });

    this.#flyout.closed.subscribe(() => {
      this.#flyout = undefined;
    });
  }

  public openFlyoutWithUrlPermalink(): void {
    this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
      ariaLabelledBy: 'flyout-title',
      ariaRole: 'dialog',
      permalink: {
        label: `Visit blackbaud.com`,
        url: 'http://www.blackbaud.com',
      },
    });

    this.#flyout.closed.subscribe(() => {
      this.#flyout = undefined;
    });
  }

  #nextButtonDisabled(): boolean {
    return this.recordNumber >= 3;
  }

  #previousButtonDisabled(): boolean {
    return this.recordNumber <= 0;
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openFlyoutWithUrlPermalink()"
>
  Open flyout with a URL permalink
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openFlyoutWithRoutePermalink()"
>
  Open flyout with an Angular routing permalink
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openFlyoutWithIterators()"
>
  Open flyout with iterators
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openFlyoutWithPrimaryAction()"
>
  Open flyout with primary action
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
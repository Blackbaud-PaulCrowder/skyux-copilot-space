---
component: 'toast'
description: 'Design guidelines, API documentation, and usage instructions for the toast component extracted from SKY UX documentation.'
---

# Toast Component Guidelines

## Component Overview
Toasts display messages over page content and provide a common look and feel.

## Usage

### ✅ Use when

Use toasts when users need to know about changes in system state due to background processes.

Use toasts when information is important enough to notify users regardless of their current tasks or context.

## Content

Toasts provide lightweight, time-sensitive information that is relevant to users when it appears. They guide users on actions to take and should include links for those actions whenever possible.

The text must be clear and concise, and punctuation is subjective depending on the scenario.

## Behavior and states

If a toast is the only place users can see a message, display the toast until users manually close it. Only close toasts automatically if users can access the messages after the toasts close.

## Related information

### Guidelines

- Calling out information
- Content containers
- Error handling

## API Documentation

### Components and Directives

#### ToastBasicExampleComponent

**Selector:** `app-toast-basic-example`

**Package:** `@skyux/code-examples`

#### ToastCustomComponentExampleComponent

**Selector:** `app-toast-custom-component-example`

**Package:** `@skyux/code-examples`

#### SkyToastInstance

**Package:** `@skyux/toast`

#### SkyToastComponent

**Selector:** `sky-toast`

**Package:** `@skyux/toast`

**Inputs:**

- `autoClose`: `boolean | undefined` - Whether to automatically close the toast. Only close toasts
automatically if users can access the messages after the toasts close.
- `toastType`: `SkyToastType | undefined` - The `SkyToastType` type for the toast to determine the color and icon to display.

**Outputs:**

- `closed`: `EventEmitter<void>` - Fires when the toast closes.

#### SkyToastModule

**Package:** `@skyux/toast`

#### SkyToastLegacyService

**Package:** `@skyux/toast`

⚠️ **This component is deprecated.**

#### SkyToastService

**Package:** `@skyux/toast`

#### SkyToastConfig

Specifies the configuration options to set up a toast.

**Package:** `@skyux/toast`

#### SkyToastContainerOptions

Global configuration options for displaying toast components.

**Package:** `@skyux/toast`

#### SkyToastDisplayDirection

**Package:** `@skyux/toast`

#### SkyToastType

**Package:** `@skyux/toast`

#### SkyToastHarnessFilters

A set of criteria that can be used to filter a list of `SkyToastHarness` instances.

**Package:** `@skyux/toast/testing`

#### SkyToastHarness

Harness for interacting with the toast component in tests.

**Package:** `@skyux/toast/testing`

#### SkyToasterHarness

Harness for interacting with toasts' host component in tests.
Use this harness to query and interact with `SkyToastHarness` for open toast components.

**Package:** `@skyux/toast/testing`

### Code Examples

#### Toast with basic setup

**Selector:** `app-toast-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyToastService, SkyToastType } from '@skyux/toast';

/**
 * @title Toast with basic setup
 */
@Component({
  standalone: true,
  selector: 'app-toast-basic-example',
  templateUrl: './example.component.html',
})
export class ToastBasicExampleComponent {
  readonly #toastSvc = inject(SkyToastService);

  public openToast(): void {
    this.#toastSvc.openMessage('This is a sample toast message.', {
      type: SkyToastType.Success,
    });
  }

  public closeAll(): void {
    this.#toastSvc.closeAll();
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-primary sky-margin-inline-sm"
  type="button"
  (click)="openToast()"
>
  Open toast
</button>
<button class="sky-btn sky-btn-default" type="button" (click)="closeAll()">
  Close all
</button>

```

#### Toast with custom content component

**Selector:** `app-toast-custom-component-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyToastService, SkyToastType } from '@skyux/toast';

import { CustomToastContext } from './custom-context';
import { CustomToastComponent } from './custom-toast.component';

/**
 * @title Toast with custom content component
 */
@Component({
  standalone: true,
  selector: 'app-toast-custom-component-example',
  templateUrl: './example.component.html',
})
export class ToastCustomComponentExampleComponent {
  readonly #toastSvc = inject(SkyToastService);

  public openToast(): void {
    const context = new CustomToastContext(
      'This toast has embedded a custom component for its content.',
    );

    this.#toastSvc.openComponent(
      CustomToastComponent,
      {
        type: SkyToastType.Success,
      },
      [
        {
          provide: CustomToastContext,
          useValue: context,
        },
      ],
    );
  }

  public closeAll(): void {
    this.#toastSvc.closeAll();
  }
}

```

**Template:**

```html
<div><strong>Custom message:</strong> {{ context.message }}</div>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
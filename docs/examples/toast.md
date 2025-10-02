---
component: 'toast'
type: 'code-examples'
description: 'Code examples for the toast component.'
---

# Toast Code Examples

## Toast with basic setup

**Component:** ToastBasicExampleComponent

**Selector:** `app-toast-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyToastType } from '@skyux/toast';
import { SkyToasterHarness } from '@skyux/toast/testing';

import { ToastBasicExampleComponent } from './example.component';

describe('Basic toast example', () => {
  let fixture: ComponentFixture<ToastBasicExampleComponent>;
  let loader: HarnessLoader;

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ToastBasicExampleComponent, NoopAnimationsModule],
    });

    fixture = TestBed.createComponent(ToastBasicExampleComponent);
    loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
  });

  async function setupTest(): Promise<{
    toasterHarness: SkyToasterHarness;
  }> {
    fixture.componentInstance.openToast();
    fixture.detectChanges();

    const toasterHarness: SkyToasterHarness =
      await loader.getHarness(SkyToasterHarness);

    return { toasterHarness };
  }

  it('should open success toasts', async () => {
    const { toasterHarness } = await setupTest();

    fixture.componentInstance.openToast();
    fixture.detectChanges();

    await expectAsync(toasterHarness.getNumberOfToasts()).toBeResolvedTo(2);

    const toast = await toasterHarness.getToastByMessage(
      'This is a sample toast message.',
    );

    await expectAsync(toast.getType()).toBeResolvedTo(SkyToastType.Success);
  });

  it('should close all toasts', async () => {
    fixture.componentInstance.openToast();
    fixture.detectChanges();
    fixture.componentInstance.closeAll();
    fixture.detectChanges();

    await expectAsync(loader.getHarness(SkyToasterHarness)).toBeRejected();
  });
});

```

#### example.component.ts

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

#### example.component.html

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

---

## Toast with custom content component

**Component:** ToastCustomComponentExampleComponent

**Selector:** `app-toast-custom-component-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### custom-context.ts

```typescript
export class CustomToastContext {
  constructor(public message: string) {}
}

```

#### custom-toast-harness.ts

```typescript
import { ComponentHarness } from '@angular/cdk/testing';

export class CustomToastHarness extends ComponentHarness {
  /**
   * @internal
   */
  public static hostSelector = 'app-toast-content-example';

  public async getText(): Promise<string> {
    return await (await this.host()).text();
  }
}

```

#### custom-toast.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyToastInstance } from '@skyux/toast';

import { CustomToastContext } from './custom-context';

@Component({
  standalone: true,
  selector: 'app-toast-content-example',
  templateUrl: './custom-toast.component.html',
})
export class CustomToastComponent {
  protected readonly context = inject(CustomToastContext);
  readonly #instance = inject(SkyToastInstance);

  protected close(): void {
    this.#instance.close();
  }
}

```

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyToastType } from '@skyux/toast';
import { SkyToasterHarness } from '@skyux/toast/testing';

import { CustomToastHarness } from './custom-toast-harness';
import { ToastCustomComponentExampleComponent } from './example.component';

describe('Custom component toast demo', () => {
  let fixture: ComponentFixture<ToastCustomComponentExampleComponent>;
  let loader: HarnessLoader;

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ToastCustomComponentExampleComponent, NoopAnimationsModule],
    });

    fixture = TestBed.createComponent(ToastCustomComponentExampleComponent);
    loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
  });

  async function setupTest(): Promise<{
    toasterHarness: SkyToasterHarness;
  }> {
    fixture.componentInstance.openToast();
    fixture.detectChanges();

    const toasterHarness: SkyToasterHarness =
      await loader.getHarness(SkyToasterHarness);

    return { toasterHarness };
  }

  it('should open custom component in toast', async () => {
    const { toasterHarness } = await setupTest();

    const toasts = await toasterHarness.getToasts();
    const customHarness = await toasts[0].queryHarness(CustomToastHarness);

    await expectAsync(toasts[0].getType()).toBeResolvedTo(SkyToastType.Success);
    await expectAsync(customHarness.getText()).toBeResolvedTo(
      'Custom message: This toast has embedded a custom component for its content.',
    );
  });

  it('should close all toasts', async () => {
    fixture.componentInstance.openToast();
    fixture.detectChanges();
    fixture.componentInstance.closeAll();
    fixture.detectChanges();

    await expectAsync(loader.getHarness(SkyToasterHarness)).toBeRejected();
  });
});

```

#### example.component.ts

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

#### custom-toast.component.html

```html
<div><strong>Custom message:</strong> {{ context.message }}</div>

```

#### example.component.html

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

---
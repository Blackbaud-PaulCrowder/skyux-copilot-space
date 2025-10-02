---
component: 'wait'
type: 'code-examples'
description: 'Code examples for the wait component.'
---

# Wait Code Examples

## Wait applied to an element

**Component:** IndicatorsWaitElementExampleComponent

**Selector:** `app-indicators-wait-element-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyWaitHarness } from '@skyux/indicators/testing';

import { IndicatorsWaitElementExampleComponent } from './example.component';

describe('Basic wait', () => {
  async function setupTest(): Promise<{
    waitHarness: SkyWaitHarness;
    fixture: ComponentFixture<IndicatorsWaitElementExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsWaitElementExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const waitHarness = await loader.getHarness(
      SkyWaitHarness.with({ dataSkyId: 'wait-example' }),
    );

    return { waitHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsWaitElementExampleComponent],
    });
  });

  it('should show the wait component when the user performs an action', async () => {
    const { waitHarness, fixture } = await setupTest();

    (fixture.nativeElement as HTMLElement)
      .querySelector<HTMLButtonElement>('.sky-btn')
      ?.click();

    fixture.detectChanges();

    await expectAsync(waitHarness.isWaiting()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isFullPage()).toBeResolvedTo(false);
    await expectAsync(waitHarness.isNonBlocking()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

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

#### example.component.html

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

---

## Wait applied to a page

**Component:** IndicatorsWaitPageExampleComponent

**Selector:** `app-indicators-wait-page-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyWaitHarness } from '@skyux/indicators/testing';

import { IndicatorsWaitPageExampleComponent } from './example.component';

describe('Page wait', () => {
  function setupTest(): {
    rootLoader: HarnessLoader;
    el: HTMLElement;
    fixture: ComponentFixture<IndicatorsWaitPageExampleComponent>;
  } {
    const fixture = TestBed.createComponent(IndicatorsWaitPageExampleComponent);
    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const el = fixture.nativeElement as HTMLElement;

    return { rootLoader, el, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsWaitPageExampleComponent],
    });
  });

  it('should show the page wait component when the user performs an action', async () => {
    const { rootLoader, el } = setupTest();

    const buttons = el.querySelectorAll<HTMLButtonElement>('.sky-btn');

    buttons[0].click();

    const waitHarness = await rootLoader.getHarness(
      SkyWaitHarness.with({ servicePageWaitType: 'blocking' }),
    );

    await expectAsync(waitHarness.isWaiting()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isFullPage()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isNonBlocking()).toBeResolvedTo(false);
  });

  it('should show the non-blocking page wait component when the user performs an action', async () => {
    const { rootLoader, el } = setupTest();

    const buttons = el.querySelectorAll<HTMLButtonElement>('.sky-btn');

    buttons[1].click();

    const waitHarness = await rootLoader.getHarness(
      SkyWaitHarness.with({ servicePageWaitType: 'non-blocking' }),
    );

    await expectAsync(waitHarness.isWaiting()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isFullPage()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isNonBlocking()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

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

#### example.component.html

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

---
---
component: 'flyout'
type: 'code-examples'
description: 'Code examples for the flyout component.'
---

# Flyout Code Examples

## Flyout with basic setup

**Component:** FlyoutBasicExampleComponent

**Selector:** `app-flyout-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyFlyoutHarness } from '@skyux/flyout/testing';

import { FlyoutBasicExampleComponent } from './example.component';

describe('Basic flyout example', () => {
  async function setupTest(): Promise<{
    flyoutHarness: SkyFlyoutHarness;
    fixture: ComponentFixture<FlyoutBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [FlyoutBasicExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(FlyoutBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    fixture.componentInstance.openFlyoutWithCustomWidth();

    const flyoutHarness: SkyFlyoutHarness =
      await loader.getHarness(SkyFlyoutHarness);

    return { flyoutHarness, fixture };
  }

  it('should set up the flyout', async () => {
    const { flyoutHarness } = await setupTest();

    await expectAsync(flyoutHarness.getAriaLabelledBy()).toBeResolvedTo(
      'flyout-title',
    );
    await expectAsync(flyoutHarness.getAriaRole()).toBeResolvedTo('dialog');
    await expectAsync(flyoutHarness.getFlyoutWidth()).toBeResolvedTo(350);
    await expectAsync(flyoutHarness.getFlyoutMinWidth()).toBeResolvedTo(200);
    await expectAsync(flyoutHarness.getFlyoutMaxWidth()).toBeResolvedTo(500);

    await flyoutHarness.closeFlyout();
  });
});

```

#### example.component.ts

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

#### flyout.component.ts

```typescript
import { Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-flyout',
  template: `
    <div class="sky-padding-even-xl">
      <h2>Sample flyout</h2>
      <p>
        Flyouts can display large quantities of supplementary information
        related to a task, including:
      </p>
      <ul>
        <li>lists</li>
        <li>records</li>
        <li>analytics</li>
      </ul>
    </div>
  `,
})
export class FlyoutComponent {}

```

#### example.component.html

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

---

## Flyouts with customized headers

**Component:** FlyoutCustomHeadersExampleComponent

**Selector:** `app-flyout-custom-headers-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyFlyoutHarness } from '@skyux/flyout/testing';

import { FlyoutCustomHeadersExampleComponent } from './example.component';

describe('Custom headers flyout example', () => {
  async function setupTest(option?: string): Promise<{
    flyoutHarness: SkyFlyoutHarness;
    fixture: ComponentFixture<FlyoutCustomHeadersExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [FlyoutCustomHeadersExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      FlyoutCustomHeadersExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    switch (option) {
      case 'url':
        fixture.componentInstance.openFlyoutWithUrlPermalink();
        break;
      case 'action':
        fixture.componentInstance.openFlyoutWithPrimaryAction();
        break;
      default:
        fixture.componentInstance.openFlyoutWithIterators();
        break;
    }

    const flyoutHarness: SkyFlyoutHarness =
      await loader.getHarness(SkyFlyoutHarness);

    return { flyoutHarness, fixture };
  }

  it('should set up the flyout with iterators', async () => {
    const { flyoutHarness, fixture } = await setupTest();

    await expectAsync(flyoutHarness.getAriaLabelledBy()).toBeResolvedTo(
      'flyout-title',
    );
    await expectAsync(flyoutHarness.getAriaRole()).toBeResolvedTo('dialog');

    expect(fixture.componentInstance.recordNumber).toBe(0);
    await flyoutHarness.clickNextIteratorButton();
    expect(fixture.componentInstance.recordNumber).toBe(1);
    await flyoutHarness.clickPreviousIteratorButton();
    expect(fixture.componentInstance.recordNumber).toBe(0);
    // previous button is disabled
    await expectAsync(
      flyoutHarness.clickPreviousIteratorButton(),
    ).toBeRejectedWithError(
      'Could not click the previous iterator because it is disabled.',
    );
  });

  it('should set up the flyout with permalink', async () => {
    const { flyoutHarness } = await setupTest('url');

    await expectAsync(flyoutHarness.getPermalinkButtonLabel()).toBeResolvedTo(
      'Visit blackbaud.com',
    );
    await expectAsync(flyoutHarness.getPermalinkButtonRoute()).toBeResolvedTo(
      'http://www.blackbaud.com',
    );
  });

  it('should set up the flyout with primary action', async () => {
    const { flyoutHarness, fixture } = await setupTest('action');

    await expectAsync(
      flyoutHarness.getPrimaryActionButtonLabel(),
    ).toBeResolvedTo('Save');

    const actionSpy = spyOn(fixture.componentInstance, 'primaryActionCallback');
    await flyoutHarness.clickPrimaryActionButton();
    expect(actionSpy).toHaveBeenCalledTimes(1);
  });
});

```

#### example.component.ts

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

#### flyout.component.ts

```typescript
import { Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-flyout',
  template: `
    <div class="sky-padding-even-xl">
      <h2>Sample flyout</h2>
      <p>
        Flyouts can display large quantities of supplementary information
        related to a task, including:
      </p>
      <ul>
        <li>lists</li>
        <li>records</li>
        <li>analytics</li>
      </ul>
    </div>
  `,
})
export class FlyoutComponent {}

```

#### example.component.html

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

---
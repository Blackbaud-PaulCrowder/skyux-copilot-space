---
component: 'summary-action-bar'
type: 'code-examples'
description: 'Code examples for the summary-action-bar component.'
---

# Summary Action Bar Code Examples

## Basic summary action bar

**Component:** ActionBarsSummaryActionBarBasicExampleComponent

**Selector:** `app-action-bars-summary-action-bar-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';

import { ActionBarsSummaryActionBarBasicExampleComponent } from './example.component';

describe('Basic summary action bar example', () => {
  async function setupTest(): Promise<{
    harness: SkySummaryActionBarHarness;
    fixture: ComponentFixture<ActionBarsSummaryActionBarBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ActionBarsSummaryActionBarBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        ActionBarsSummaryActionBarBasicExampleComponent,
        NoopAnimationsModule,
      ],
    });
  });

  it('should set up primary actions', async () => {
    const { harness, fixture } = await setupTest();

    const primaryActionHarness = await harness.getPrimaryAction();
    await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
      'Primary action',
    );

    const spy = spyOn(fixture.componentInstance, 'onPrimaryActionClick');
    await primaryActionHarness.click();
    expect(spy).toHaveBeenCalled();
  });

  it('should set up secondary actions', async () => {
    const { harness, fixture } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const actions = await secondaryActions.getActions();
    expect(actions.length).toBe(2);

    const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
    const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');

    await actions[1].click();
    expect(spy2).toHaveBeenCalled();

    const secondaryAction = await secondaryActions.getAction({
      dataSkyId: 'secondary-action',
    });
    await secondaryAction.click();
    expect(spy1).toHaveBeenCalled();
  });

  it('should set up the summary', async () => {
    const { harness } = await setupTest();

    const summary = await harness.getSummary();
    const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
    expect(keyInfos.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Basic summary action bar
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule],
})
export class ActionBarsSummaryActionBarBasicExampleComponent {
  public onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }
}

```

#### example.component.html

```html
<sky-summary-action-bar data-sky-id="donation-summary">
  <sky-summary-action-bar-actions>
    <sky-summary-action-bar-primary-action
      (actionClick)="onPrimaryActionClick()"
    >
      Primary action
    </sky-summary-action-bar-primary-action>
    <sky-summary-action-bar-secondary-actions>
      <sky-summary-action-bar-secondary-action
        data-sky-id="secondary-action"
        (actionClick)="onSecondaryActionClick()"
      >
        Secondary action
      </sky-summary-action-bar-secondary-action>
      <sky-summary-action-bar-secondary-action
        data-sky-id="secondary-action-2"
        (actionClick)="onSecondaryAction2Click()"
      >
        Secondary action 2
      </sky-summary-action-bar-secondary-action>
    </sky-summary-action-bar-secondary-actions>
  </sky-summary-action-bar-actions>
  <sky-summary-action-bar-summary>
    <sky-key-info>
      <sky-key-info-value>$250</sky-key-info-value>
      <sky-key-info-label>Given this month</sky-key-info-label>
    </sky-key-info>
    <sky-key-info>
      <sky-key-info-value>$1,000</sky-key-info-value>
      <sky-key-info-label>Given this year</sky-key-info-label>
    </sky-key-info>
    <sky-key-info>
      <sky-key-info-value>$1,300</sky-key-info-value>
      <sky-key-info-label>Given all time</sky-key-info-label>
    </sky-key-info>
  </sky-summary-action-bar-summary>
</sky-summary-action-bar>

```

---

## Summary action bar with errors

**Component:** ActionBarsSummaryActionBarErrorExampleComponent

**Selector:** `app-action-bars-summary-action-bar-error-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';

import { ActionBarsSummaryActionBarErrorExampleComponent } from './example.component';

describe('Error summary action bar example', () => {
  async function setupTest(): Promise<{
    harness: SkySummaryActionBarHarness;
    fixture: ComponentFixture<ActionBarsSummaryActionBarErrorExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ActionBarsSummaryActionBarErrorExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        ActionBarsSummaryActionBarErrorExampleComponent,
        NoopAnimationsModule,
      ],
    });
  });

  it('should add an error on clicking secondary action button to add single error', async () => {
    const { harness } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const singleErrorAction = await secondaryActions.getAction({
      dataSkyId: 'single-error-action',
    });

    await singleErrorAction.click();

    await expectAsync(
      harness.hasError({ message: 'Monthly donation is missing.' }),
    ).toBeResolvedTo(true);
  });

  it('should add errors on clicking secondary action button to add multiple errors', async () => {
    const { harness } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const singleErrorAction = await secondaryActions.getActions();

    await singleErrorAction[1].click();

    const errors = await harness.getErrors();
    expect(errors.length).toBe(2);
  });

  it('should set up the summary', async () => {
    const { harness } = await setupTest();

    const summary = await harness.getSummary();
    const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
    expect(keyInfos.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { toSignal } from '@angular/core/rxjs-interop';
import { FormBuilder, FormControl, ReactiveFormsModule } from '@angular/forms';
import {
  SkySummaryActionBarError,
  SkySummaryActionBarModule,
} from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { of, switchMap } from 'rxjs';

interface donationSummary {
  value: number;
  label: string;
}

/**
 * @title Summary action bar with errors
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-error-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule, ReactiveFormsModule],
})
export class ActionBarsSummaryActionBarErrorExampleComponent {
  protected donationSummary = new FormControl<donationSummary[] | null>([
    {
      value: 250,
      label: 'Given this month',
    },
    {
      value: 1000,
      label: 'Given this year',
    },
    {
      value: 1300,
      label: 'Given all time',
    },
  ]);
  protected exampleForm = inject(FormBuilder).group({
    donationSummary: this.donationSummary,
  });

  protected formErrors = toSignal<SkySummaryActionBarError[] | undefined>(
    this.donationSummary.statusChanges.pipe(
      switchMap(() => {
        const errors = this.donationSummary.errors;

        return of(
          errors
            ? Object.values(errors).map((error) => ({
                message: error as string,
              }))
            : undefined,
        );
      }),
    ),
  );

  protected onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  protected singleError(): void {
    this.donationSummary.setErrors({
      singleError: 'Monthly donation is missing.',
    });
  }

  protected multipleErrors(): void {
    this.donationSummary.setErrors({
      firstError: 'Monthly donation is missing.',
      secondError: 'Yearly donation is missing.',
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="exampleForm">
  <sky-summary-action-bar
    data-sky-id="donation-summary"
    [formErrors]="formErrors()"
  >
    <sky-summary-action-bar-actions>
      <sky-summary-action-bar-primary-action
        (actionClick)="onPrimaryActionClick()"
      >
        Primary action
      </sky-summary-action-bar-primary-action>
      <sky-summary-action-bar-secondary-actions>
        <sky-summary-action-bar-secondary-action
          data-sky-id="single-error-action"
          (actionClick)="singleError()"
        >
          Single error action
        </sky-summary-action-bar-secondary-action>
        <sky-summary-action-bar-secondary-action
          data-sky-id="multiple-error-action"
          (actionClick)="multipleErrors()"
        >
          Multiple errors action
        </sky-summary-action-bar-secondary-action>
      </sky-summary-action-bar-secondary-actions>
    </sky-summary-action-bar-actions>
    <sky-summary-action-bar-summary>
      @for (info of donationSummary.value; track info) {
        <sky-key-info>
          <sky-key-info-value>${{ info.value }}</sky-key-info-value>
          <sky-key-info-label>{{ info.label }}</sky-key-info-label>
        </sky-key-info>
      }
    </sky-summary-action-bar-summary>
  </sky-summary-action-bar>
</form>

```

---

## Modal with summary action bar

**Component:** ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Modal with summary action bar
 */
@Component({
  standalone: true,
  selector: 'app-action-bars-summary-action-bar-modal-example',
  templateUrl: './example.component.html',
})
export class ActionBarsSummaryActionBarModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  protected openModal(): void {
    this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });
  }
}

```

#### modal.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
import { SkyModalInstance } from '@skyux/modals';

import { ModalComponent } from './modal.component';

describe('Modal summary action bar example', () => {
  async function setupTest(): Promise<{
    harness: SkySummaryActionBarHarness;
    fixture: ComponentFixture<ModalComponent>;
  }> {
    const fixture = TestBed.createComponent(ModalComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalComponent, NoopAnimationsModule],
      providers: [SkyModalInstance],
    });
  });

  it('should set up primary actions', async () => {
    const { harness, fixture } = await setupTest();

    const primaryActionHarness = await harness.getPrimaryAction();
    await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
      'Primary action',
    );

    const spy = spyOn(fixture.componentInstance, 'save');
    await primaryActionHarness.click();
    expect(spy).toHaveBeenCalled();
  });

  it('should set up secondary actions', async () => {
    const { harness, fixture } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const actions = await secondaryActions.getActions();
    expect(actions.length).toBe(2);

    const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
    const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');

    await actions[1].click();
    expect(spy2).toHaveBeenCalled();

    const secondaryAction = await secondaryActions.getAction({
      dataSkyId: 'secondary-action',
    });
    await secondaryAction.click();
    expect(spy1).toHaveBeenCalled();
  });

  it('should set up the summary', async () => {
    const { harness } = await setupTest();

    const summary = await harness.getSummary();
    const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
    expect(keyInfos.length).toBe(3);
  });
});

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [SkyKeyInfoModule, SkyModalModule, SkySummaryActionBarModule],
})
export class ModalComponent {
  readonly #modalInstance = inject(SkyModalInstance);

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }

  protected cancel(): void {
    this.#modalInstance.cancel();
  }

  public save(): void {
    this.#modalInstance.save();
  }
}

```

#### example.component.html

```html
<button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
  Open modal
</button>

```

#### modal.component.html

```html
<sky-modal headingText="Modal with summary action bar">
  <sky-modal-content> Hello world! </sky-modal-content>
  <sky-modal-footer>
    <sky-summary-action-bar data-sky-id="donation-summary">
      <sky-summary-action-bar-actions>
        <sky-summary-action-bar-primary-action (actionClick)="save()">
          Primary action
        </sky-summary-action-bar-primary-action>
        <sky-summary-action-bar-secondary-actions>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action"
            (actionClick)="onSecondaryActionClick()"
          >
            Secondary action
          </sky-summary-action-bar-secondary-action>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action-2"
            (actionClick)="onSecondaryAction2Click()"
          >
            Secondary action 2
          </sky-summary-action-bar-secondary-action>
        </sky-summary-action-bar-secondary-actions>
        <sky-summary-action-bar-cancel (actionClick)="cancel()">
          Cancel
        </sky-summary-action-bar-cancel>
      </sky-summary-action-bar-actions>
      <sky-summary-action-bar-summary>
        <sky-key-info>
          <sky-key-info-value>$250</sky-key-info-value>
          <sky-key-info-label>Given this month</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,000</sky-key-info-value>
          <sky-key-info-label>Given this year</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,300</sky-key-info-value>
          <sky-key-info-label>Given all time</sky-key-info-label>
        </sky-key-info>
      </sky-summary-action-bar-summary>
    </sky-summary-action-bar>
  </sky-modal-footer>
</sky-modal>

```

---

## Tab with summary action bar

**Component:** ActionBarsSummaryActionBarTabExampleComponent

**Selector:** `app-action-bars-summary-action-bar-tab-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';

import { ActionBarsSummaryActionBarTabExampleComponent } from './example.component';

describe('Basic summary action bar example', () => {
  async function setupTest(): Promise<{
    harness: SkySummaryActionBarHarness;
    fixture: ComponentFixture<ActionBarsSummaryActionBarTabExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ActionBarsSummaryActionBarTabExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        ActionBarsSummaryActionBarTabExampleComponent,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should set up primary actions', async () => {
    const { harness, fixture } = await setupTest();

    const primaryActionHarness = await harness.getPrimaryAction();
    await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
      'Primary action',
    );

    const spy = spyOn(fixture.componentInstance, 'onPrimaryActionClick');
    await primaryActionHarness.click();
    expect(spy).toHaveBeenCalled();
  });

  it('should set up secondary actions', async () => {
    const { harness, fixture } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const actions = await secondaryActions.getActions();
    expect(actions.length).toBe(2);

    const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
    const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');

    await actions[1].click();
    expect(spy2).toHaveBeenCalled();

    const secondaryAction = await secondaryActions.getAction({
      dataSkyId: 'secondary-action',
    });
    await secondaryAction.click();
    expect(spy1).toHaveBeenCalled();
  });

  it('should set up the summary', async () => {
    const { harness } = await setupTest();

    const summary = await harness.getSummary();
    const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
    expect(keyInfos.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tab with summary action bar
 * @docsDemoHidden
 */
@Component({
  selector: 'app-action-bars-summary-action-bar-tab-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule, SkySummaryActionBarModule, SkyTabsModule],
})
export class ActionBarsSummaryActionBarTabExampleComponent {
  public onPrimaryActionClick(): void {
    alert('Primary action button clicked.');
  }

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }
}

```

#### example.component.html

```html
<sky-tabset [active]="0">
  <sky-tab tabHeading="Tab 1"> Tab without summary action bar. </sky-tab>
  <sky-tab tabHeading="Tab 2">
    Tab with summary action bar.
    <sky-summary-action-bar data-sky-id="donation-summary">
      <sky-summary-action-bar-actions>
        <sky-summary-action-bar-primary-action
          (actionClick)="onPrimaryActionClick()"
        >
          Primary action
        </sky-summary-action-bar-primary-action>
        <sky-summary-action-bar-secondary-actions>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action"
            (actionClick)="onSecondaryActionClick()"
          >
            Secondary action
          </sky-summary-action-bar-secondary-action>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action-2"
            (actionClick)="onSecondaryAction2Click()"
          >
            Secondary action 2
          </sky-summary-action-bar-secondary-action>
        </sky-summary-action-bar-secondary-actions>
      </sky-summary-action-bar-actions>
      <sky-summary-action-bar-summary>
        <sky-key-info>
          <sky-key-info-value>$250</sky-key-info-value>
          <sky-key-info-label>Given this month</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,000</sky-key-info-value>
          <sky-key-info-label>Given this year</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,300</sky-key-info-value>
          <sky-key-info-label>Given all time</sky-key-info-label>
        </sky-key-info>
      </sky-summary-action-bar-summary>
    </sky-summary-action-bar>
  </sky-tab>
</sky-tabset>

```

---
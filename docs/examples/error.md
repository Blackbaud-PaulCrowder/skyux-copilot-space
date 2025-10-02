---
component: 'error'
type: 'code-examples'
description: 'Code examples for the error component.'
---

# Error Code Examples

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

## Embed error within the page markup

**Component:** ErrorsErrorEmbeddedExampleComponent

**Selector:** `app-errors-error-embedded-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyErrorModule } from '@skyux/errors';

/**
 * @title Embed error within the page markup
 */
@Component({
  selector: 'app-errors-error-embedded-example',
  templateUrl: './example.component.html',
  imports: [SkyErrorModule],
})
export class ErrorsErrorEmbeddedExampleComponent {
  protected customAction(): void {
    alert('action clicked!');
  }
}

```

#### example.component.html

```html
<sky-error errorType="broken">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Try again
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="notfound">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="construction">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="security">
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Go back
    </button>
  </sky-error-action>
</sky-error>

<sky-error>
  <sky-error-image>
    <img
      alt=""
      role="presentation"
      src="data:image/png;base64,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"
    />
  </sky-error-image>
  <sky-error-title> Custom error with a custom image. </sky-error-title>
  <sky-error-description> Custom description. </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

<sky-error errorType="broken">
  <sky-error-title [replaceDefaultTitle]="true">
    Custom error with a default image.
  </sky-error-title>
  <sky-error-description [replaceDefaultDescription]="true">
    Custom description.
  </sky-error-description>
  <sky-error-action>
    <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
      Custom action
    </button>
  </sky-error-action>
</sky-error>

```

---

## Show an error inside a modal

**Component:** ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyErrorModalService } from '@skyux/errors';

/**
 * @title Show an error inside a modal
 */
@Component({
  standalone: true,
  selector: 'app-errors-error-modal-example',
  templateUrl: './example.component.html',
})
export class ErrorsErrorModalExampleComponent {
  readonly #errorSvc = inject(SkyErrorModalService);

  public openErrorModal(): void {
    this.#errorSvc.open({
      errorTitle: 'Something went wrong.',
      errorDescription: 'Close the modal, and come back later.',
      errorCloseText: 'Close',
    });
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="openErrorModal()"
>
  Open error modal
</button>

```

---

## Input box with custom errors

**Component:** FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { FormsInputBoxWithCustomFormErrorsExampleComponent } from './example.component';

describe('Input box with custom form errors example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    fixture: ComponentFixture<FormsInputBoxWithCustomFormErrorsExampleComponent>;
    inputBoxHarness: SkyInputBoxHarness;
  }> {
    const fixture = TestBed.createComponent(
      FormsInputBoxWithCustomFormErrorsExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const inputBoxHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { fixture, inputBoxHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsInputBoxWithCustomFormErrorsExampleComponent],
    });
  });

  it('should not allow invalid color to be selected', async () => {
    const { fixture, inputBoxHarness } = await setupTest({
      dataSkyId: 'input-box-favorite-color',
    });

    fixture.detectChanges();

    const selectEl = await inputBoxHarness.querySelector('select');

    // Select the "invalid" option.
    await selectEl.selectOptions(7);

    await expectAsync(
      inputBoxHarness.hasCustomFormError('invalid'),
    ).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box with custom errors
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class FormsInputBoxWithCustomFormErrorsExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    favoriteColor: this.favoriteColor,
  });
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box
    data-sky-id="input-box-favorite-color"
    labelText="Favorite color"
  >
    <select formControlName="favoriteColor">
      <option value="none">None</option>
      <option value="red">Red</option>
      <option value="orange">Orange</option>
      <option value="yellow">Yellow</option>
      <option value="green">Green</option>
      <option value="blue">Blue</option>
      <option value="purple">Purple</option>
      <option value="invalid">Invalid Color</option>
    </select>
    @if (favoriteColor.errors?.['invalid']) {
      <sky-form-error
        errorName="invalid"
        errorText="The color Invalid Color is not a color"
      />
    }
  </sky-input-box>
</form>

```

---

## Modal with form errors

**Component:** ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### context.ts

```typescript
import { ModalDemoData } from './data';

export class ModalDemoContext {
  constructor(public data: ModalDemoData) {}
}

```

#### data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { ModalDemoData } from './data';

@Injectable({
  providedIn: 'root',
})
export class ModalDemoDataService {
  #data: ModalDemoData = {
    value1: 'Hello world',
  };

  public load(): Observable<ModalDemoData> {
    // Simulate a network request to get data.
    return of(this.#data).pipe(delay(1000));
  }

  public save(data: ModalDemoData, error = false): Observable<ModalDemoData> {
    if (!error) {
      this.#data = data;
    }

    // Simulate a network request to save data.
    return of(this.#data).pipe(delay(1000));
  }
}

```

#### data.ts

```typescript
export interface ModalDemoData {
  value1?: string | null;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalHarness } from '@skyux/modals/testing';

import { Observable, of } from 'rxjs';

import { ModalDemoDataService } from './data.service';
import { ModalsModalWithErrorExampleComponent } from './example.component';

class mockWaitSvc {
  public blockingWrap(data: unknown): Observable<unknown> {
    return of(data);
  }
}

describe('Basic modal', () => {
  async function setupTest(): Promise<{
    modalHarness: SkyModalHarness;
    fixture: ComponentFixture<ModalsModalWithErrorExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ModalsModalWithErrorExampleComponent,
    );
    fixture.componentInstance.onOpenModalClick();
    fixture.detectChanges();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const modalHarness = await loader.getHarness(
      SkyModalHarness.with({
        dataSkyId: 'modal-example',
      }),
    );

    return { modalHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalsModalWithErrorExampleComponent],
      providers: [
        {
          provide: SkyWaitService,
          useClass: mockWaitSvc,
        },
        ModalDemoDataService,
      ],
    });
  });

  it('should open the correct modal', async () => {
    const { modalHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(modalHarness.getAriaRole()).toBeResolvedTo('dialog');
    await expectAsync(modalHarness.getSize()).toBeResolvedTo('medium');
    await expectAsync(modalHarness.isFullPage()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with form errors
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-with-error-example',
  templateUrl: './example.component.html',
})
export class ModalsModalWithErrorExampleComponent implements OnDestroy {
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalError, SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalDemoContext } from './context';
import { ModalDemoDataService } from './data.service';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
})
export class ModalComponent {
  protected exampleForm: FormGroup<{
    value1: FormControl<string | null | undefined>;
  }>;

  readonly #context = inject(ModalDemoContext);
  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #instance = inject(SkyModalInstance);
  readonly #waitSvc = inject(SkyWaitService);

  public errors: SkyModalError[] = [];

  constructor() {
    this.exampleForm = new FormGroup({
      value1: new FormControl(this.#context.data.value1),
    });
  }

  protected saveForm(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
      .subscribe((data) => {
        // Notify the modal instance that data was saved and return the saved data.
        this.#instance.save(data);
      });
  }

  protected saveFormWithFormError(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value, true))
      .subscribe(() => {
        this.errors = [{ message: 'There was an error saving the form.' }];
      });
  }

  protected cancelForm(): void {
    this.#instance.cancel();
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### modal.component.html

```html
<form [formGroup]="exampleForm" (submit)="saveForm()">
  <sky-modal
    data-sky-id="modal-example"
    headingText="Modal title"
    [isDirty]="exampleForm.dirty"
    [formErrors]="errors"
  >
    <sky-modal-content>
      <sky-input-box labelText="An input inside a modal">
        <input formControlName="value1" type="text" />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Save</button>
      <button
        class="sky-btn sky-btn-link"
        type="button"
        (click)="saveFormWithFormError()"
      >
        Save form with an error
      </button>
      <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

---
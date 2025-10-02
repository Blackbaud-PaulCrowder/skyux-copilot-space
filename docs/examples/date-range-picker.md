---
component: 'date-range-picker'
type: 'code-examples'
description: 'Code examples for the date-range-picker component.'
---

# Date Range Picker Code Examples

## Date range picker with basic setup

**Component:** DatetimeDateRangePickerBasicExampleComponent

**Selector:** `app-datetime-date-range-picker-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyDateRangeCalculatorId } from '@skyux/datetime';
import { SkyDateRangePickerHarness } from '@skyux/datetime/testing';

import { DatetimeDateRangePickerBasicExampleComponent } from '../../date-range-picker/basic/example.component';

describe('Basic date range picker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyDateRangePickerHarness;
    fixture: ComponentFixture<DatetimeDateRangePickerBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      DatetimeDateRangePickerBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyDateRangePickerHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        DatetimeDateRangePickerBasicExampleComponent,
        NoopAnimationsModule,
      ],
    });
  });

  it('should set initial value', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'last-donation',
    });

    await expectAsync(harness.getLabelText()).toBeResolvedTo('Last donation');
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Donations received today are updated at the top of each hour.',
    );
    await harness.clickHelpInline();
    await expectAsync(harness.getHelpPopoverContent()).toBeResolvedTo(
      'By default, donations include one-time gifts, pledges, and matching gifts. To customize, see Giving settings.',
    );
  });

  it('should throw an error if a weekend is selected', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'last-donation',
    });

    await harness.selectCalculator(SkyDateRangeCalculatorId.SpecificRange);
    await harness.setEndDateValue('05/22/2022');

    await expectAsync(harness.hasError('dateWeekend')).toBeResolvedTo(true);
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
import {
  SkyDateRangeCalculation,
  SkyDateRangeCalculatorId,
  SkyDateRangePickerModule,
} from '@skyux/datetime';

function dateRangeExcludesWeekend(
  control: AbstractControl<SkyDateRangeCalculation>,
): ValidationErrors | null {
  const startDate = control.value.startDate;
  const endDate = control.value.endDate;

  const isWeekend = (value: unknown): boolean => {
    return (
      value instanceof Date && (value.getDay() === 6 || value.getDay() === 0)
    );
  };

  if (isWeekend(startDate) || isWeekend(endDate)) {
    return { dateWeekend: true };
  }

  return null;
}

/**
 * @title Date range picker with basic setup
 */
@Component({
  selector: 'app-datetime-date-range-picker-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyDateRangePickerModule],
})
export class DatetimeDateRangePickerBasicExampleComponent {
  protected dateFormat: string | undefined;
  protected disabled = false;
  protected hintText =
    'Donations received today are updated at the top of each hour.';
  protected labelText = 'Last donation';

  protected lastDonation = new FormControl<SkyDateRangeCalculation>(
    {
      value: {
        calculatorId: SkyDateRangeCalculatorId.AnyTime,
      },
      disabled: this.disabled,
    },
    {
      nonNullable: true,
      validators: [dateRangeExcludesWeekend],
    },
  );

  protected formGroup = inject(FormBuilder).group({
    lastDonation: this.lastDonation,
  });
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-date-range-picker
      data-sky-id="last-donation"
      formControlName="lastDonation"
      [dateFormat]="dateFormat"
      [helpPopoverContent]="inlineHelpPopover"
      [hintText]="hintText"
      [labelText]="labelText"
    >
      @if (lastDonation.errors?.['dateWeekend']) {
        <sky-form-error
          errorName="dateWeekend"
          errorText="Do not pick a weekend."
        />
      }
    </sky-date-range-picker>
  </form>
</div>

<ng-template #inlineHelpPopover>
  By default, donations include one-time gifts, pledges, and matching gifts. To
  customize, see <a>Giving settings</a>.
</ng-template>

```

---

## Date range picker with custom calculator

**Component:** DatetimeDateRangePickerCustomCalculatorExampleComponent

**Selector:** `app-datetime-date-range-picker-custom-calculator-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject, signal } from '@angular/core';
import { takeUntilDestroyed } from '@angular/core/rxjs-interop';
import {
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import {
  SkyDateRangeCalculation,
  SkyDateRangeCalculator,
  SkyDateRangeCalculatorId,
  SkyDateRangeCalculatorType,
  SkyDateRangePickerModule,
  SkyDateRangeService,
} from '@skyux/datetime';

/**
 * @title Date range picker with custom calculator
 */
@Component({
  selector: 'app-datetime-date-range-picker-custom-calculator-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyDateRangePickerModule,
  ],
})
export class DatetimeDateRangePickerCustomCalculatorExampleComponent {
  readonly #dateRangeSvc = inject(SkyDateRangeService);

  protected customCalculators: SkyDateRangeCalculatorId[] | undefined;
  protected disabled = false;
  protected hintText =
    'Donations received today are updated at the top of each hour.';
  protected labelText = 'Last donation';

  protected lastDonation = new FormControl<SkyDateRangeCalculation>(
    {
      value: {
        calculatorId: SkyDateRangeCalculatorId.AnyTime,
      },
      disabled: this.disabled,
    },
    { nonNullable: true },
  );

  protected formGroup = inject(FormBuilder).group({
    lastDonation: this.lastDonation,
  });

  protected selectedCalculator = signal<SkyDateRangeCalculator | undefined>(
    this.#getCalculatorById(SkyDateRangeCalculatorId.AnyTime),
  );

  constructor() {
    const since1999Calculator = this.#dateRangeSvc.createCalculator({
      shortDescription: 'Since 1999',
      type: SkyDateRangeCalculatorType.Relative,
      getValue: () => {
        return {
          startDate: new Date('1/1/1999'),
          endDate: new Date(),
        };
      },
    });

    const dateBeforeToday = this.#dateRangeSvc.createCalculator({
      shortDescription: 'Date before today',
      type: SkyDateRangeCalculatorType.Before,
      validate: (value): ValidationErrors | null => {
        if (value?.endDate && value.endDate > new Date()) {
          return {
            dateIsAfterToday: true,
          };
        }

        return null;
      },
      getValue: () => {
        return {
          endDate: new Date(),
        };
      },
    });

    this.customCalculators = [
      SkyDateRangeCalculatorId.SpecificRange,
      SkyDateRangeCalculatorId.LastFiscalYear,
      since1999Calculator.calculatorId,
      dateBeforeToday.calculatorId,
      SkyDateRangeCalculatorId.AnyTime,
    ];

    this.lastDonation.valueChanges
      .pipe(takeUntilDestroyed())
      .subscribe((value) => {
        const selectedCalculator = this.#getCalculatorById(value?.calculatorId);

        this.selectedCalculator.set(selectedCalculator);
      });
  }

  #getCalculatorById(id: SkyDateRangeCalculatorId): SkyDateRangeCalculator {
    return this.#dateRangeSvc.filterCalculators([id])[0];
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-date-range-picker
      formControlName="lastDonation"
      [calculatorIds]="customCalculators"
      [helpPopoverContent]="inlineHelpPopover"
      [hintText]="hintText"
      [labelText]="labelText"
    >
      @if (
        lastDonation.errors?.['skyDateRange']?.errors?.['dateIsAfterToday']
      ) {
        <sky-form-error
          errorName="dateIsAfterToday"
          errorText="Enter a date before today."
        />
      }
    </sky-date-range-picker>
  </form>
  <p>
    Selected calculator: {{ selectedCalculator()?.shortDescription$ | async }}
  </p>
</div>

<ng-template #inlineHelpPopover>
  By default, donations include one-time gifts, pledges, and matching gifts. To
  customize, see <a>Giving settings</a>.
</ng-template>

```

---

## Date range picker with help key

**Component:** DatetimeDateRangePickerHelpKeyExampleComponent

**Selector:** `app-datetime-date-range-picker-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyDateRangePickerHarness } from '@skyux/datetime/testing';

import { DatetimeDateRangePickerHelpKeyExampleComponent } from './example.component';

describe('Basic date range picker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyDateRangePickerHarness;
    fixture: ComponentFixture<DatetimeDateRangePickerHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      DatetimeDateRangePickerHelpKeyExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpController = TestBed.inject(SkyHelpTestingController);

    const harness = await loader.getHarness(
      SkyDateRangePickerHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        DatetimeDateRangePickerHelpKeyExampleComponent,
        NoopAnimationsModule,
        SkyHelpTestingModule,
      ],
    });
  });

  it('should set initial value', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'last-donation',
    });

    await expectAsync(harness.getLabelText()).toBeResolvedTo('Last donation');
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Donations received today are updated at the top of each hour.',
    );
  });

  it('should have the correct help key', async () => {
    const { harness, helpController } = await setupTest({
      dataSkyId: 'last-donation',
    });

    await harness.clickHelpInline();

    helpController.expectCurrentHelpKey('dates-help');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyDateRangeCalculation,
  SkyDateRangeCalculatorId,
  SkyDateRangePickerModule,
} from '@skyux/datetime';

/**
 * @title Date range picker with help key
 */
@Component({
  selector: 'app-datetime-date-range-picker-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyDateRangePickerModule],
})
export class DatetimeDateRangePickerHelpKeyExampleComponent {
  protected dateFormat: string | undefined;
  protected disabled = false;
  protected hintText =
    'Donations received today are updated at the top of each hour.';
  protected labelText = 'Last donation';

  protected lastDonation = new FormControl<SkyDateRangeCalculation>(
    {
      value: {
        calculatorId: SkyDateRangeCalculatorId.AnyTime,
      },
      disabled: this.disabled,
    },
    {
      nonNullable: true,
    },
  );

  protected formGroup = inject(FormBuilder).group({
    lastDonation: this.lastDonation,
  });
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-date-range-picker
      data-sky-id="last-donation"
      formControlName="lastDonation"
      helpKey="dates-help"
      [dateFormat]="dateFormat"
      [hintText]="hintText"
      [labelText]="labelText"
    />
  </form>
</div>

```

---
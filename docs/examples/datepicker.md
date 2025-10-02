---
component: 'datepicker'
type: 'code-examples'
description: 'Code examples for the datepicker component.'
---

# Datepicker Code Examples

## Datepicker with basic setup

**Component:** DatetimeDatepickerBasicExampleComponent

**Selector:** `app-datetime-datepicker-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyDatepickerHarness } from '@skyux/datetime/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { DatetimeDatepickerBasicExampleComponent } from './example.component';

describe('Basic datepicker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    inputHarness: SkyInputBoxHarness;
    datepickerHarness: SkyDatepickerHarness;
    fixture: ComponentFixture<DatetimeDatepickerBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      DatetimeDatepickerBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const inputHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );
    const datepickerHarness =
      await inputHarness.queryHarness(SkyDatepickerHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { inputHarness, datepickerHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [DatetimeDatepickerBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should have initial setup values', async () => {
    const { inputHarness, datepickerHarness, fixture } = await setupTest({
      dataSkyId: 'datepicker-example',
    });

    await expectAsync(inputHarness.getHintText()).toBeResolvedTo(
      'Must be before your 1 year anniversary. Use the format MM/DD/YYYY.',
    );

    await datepickerHarness.clickCalendarButton();

    await inputHarness.clickHelpInline();
    await expectAsync(inputHarness.getHelpPopoverContent()).toBeResolvedTo(
      fixture.componentInstance.helpPopoverContent,
    );

    await datepickerHarness.clickCalendarButton();
    const calendarHarness = await datepickerHarness.getDatepickerCalendar();
    await expectAsync(calendarHarness.getSelectedValue()).toBeResolvedTo(
      'Friday, October 12th 2001',
    );
  });

  it('should throw an error if selecting a weekend', async () => {
    const { inputHarness, datepickerHarness } = await setupTest({
      dataSkyId: 'datepicker-example',
    });

    await datepickerHarness.clickCalendarButton();
    const calendarHarness = await datepickerHarness.getDatepickerCalendar();

    await calendarHarness.clickDate('Saturday, October 13th 2001');
    await expectAsync(
      inputHarness.hasCustomFormError('invalidWeekend'),
    ).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyDatepickerModule } from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';

interface DemoForm {
  startDate: FormControl<Date | string | null>;
}

function validateDate(
  control: AbstractControl<Date | string | null>,
): ValidationErrors | null {
  const date = control.value;
  if (date instanceof Date) {
    const day = date?.getDay();

    return day !== undefined && (day === 0 || day === 6)
      ? {
          invalidWeekend: true,
        }
      : null;
  }
  return null;
}

/**
 * @title Datepicker with basic setup
 */
@Component({
  selector: 'app-datetime-datepicker-basic-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyDatepickerModule,
    SkyInputBoxModule,
  ],
})
export class DatetimeDatepickerBasicExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected startDate: FormControl<Date | string | null>;
  protected hintText = 'Must be before your 1 year anniversary.';

  public helpPopoverContent =
    'If you need help with registration, choose a date at least 8 business days after you arrive. The process takes up to 7 business days from the start date.';

  constructor() {
    this.startDate = new FormControl<Date | string | null>(
      new Date('10/12/2001'),
      {
        validators: [Validators.required, validateDate],
      },
    );

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      startDate: this.startDate,
    });
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-input-box
      data-sky-id="datepicker-example"
      labelText="Start date"
      [helpPopoverContent]="helpPopoverContent"
      [hintText]="hintText"
    >
      <sky-datepicker>
        <input formControlName="startDate" skyDatepickerInput type="text" />
      </sky-datepicker>
      @if (startDate.errors?.['invalidWeekend']) {
        <sky-form-error
          errorName="invalidWeekend"
          errorText="Start date must not be on a weekend."
        />
      }
    </sky-input-box>
  </form>

  <p>
    Selected date: <code>{{ startDate.value | json }}</code>
  </p>
</div>

```

---

## Datepicker with custom dates

**Component:** DatetimeDatepickerCustomDatesExampleComponent

**Selector:** `app-datetime-datepicker-custom-dates-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyDatepickerCalendarChange,
  SkyDatepickerCustomDate,
  SkyDatepickerModule,
} from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

/**
 * @title Datepicker with custom dates
 */
@Component({
  selector: 'app-datetime-datepicker-custom-dates-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyDatepickerModule,
    SkyInputBoxModule,
  ],
})
export class DatetimeDatepickerCustomDatesExampleComponent {
  protected formGroup: FormGroup;

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.formGroup = this.#formBuilder.group({
      startDate: new FormControl(),
    });
  }

  protected onCalendarDateRangeChange(
    event: SkyDatepickerCalendarChange,
  ): void {
    if (event) {
      // Bind observable to `customDates` argument and simulate delay for async process to finish.
      // Normally, `getCustomDates()` would be replaced by an async call to fetch data.
      event.customDates = this.#getCustomDates(event).pipe(delay(2000));
    }
  }

  /**
   * Generate fake custom dates based on the date range returned from the event.
   * This is for demonstration purposes only.
   */
  #getCustomDates(
    event: SkyDatepickerCalendarChange,
  ): Observable<SkyDatepickerCustomDate[]> {
    const getNextDate = function (startDate: Date, daysToAdd: number): Date {
      const newDate = new Date(startDate);
      newDate.setDate(newDate.getDate() + daysToAdd);
      return newDate;
    };

    const customDates: SkyDatepickerCustomDate[] = [];
    customDates.push({
      date: event.startDate,
      disabled: false,
      keyDate: true,
      keyDateText: ['Onboarding meeting'],
    });

    customDates.push({
      date: getNextDate(event.startDate, 8),
      disabled: false,
      keyDate: true,
      keyDateText: ['Department all hands'],
    });

    customDates.push({
      date: getNextDate(event.startDate, 9),
      disabled: false,
      keyDate: true,
      keyDateText: ['Company retreat'],
    });

    customDates.push({
      date: getNextDate(event.startDate, 10),
      disabled: true,
      keyDate: true,
      keyDateText: ['Federal holiday'],
    });

    customDates.push({
      date: getNextDate(event.startDate, 11),
      disabled: true,
      keyDate: false,
      keyDateText: [],
    });

    customDates.push({
      date: getNextDate(event.startDate, 12),
      disabled: false,
      keyDate: true,
      keyDateText: ['New hire review due'],
    });

    customDates.push({
      date: getNextDate(event.startDate, 13),
      disabled: false,
      keyDate: true,
      keyDateText: ['Key note speaker', 'Focus group'],
    });

    customDates.push({
      date: event.endDate,
      disabled: false,
      keyDate: true,
      keyDateText: ['Customer lunch and learn'],
    });

    return of(customDates);
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-input-box labelText="Start date">
      <sky-datepicker
        (calendarDateRangeChange)="onCalendarDateRangeChange($event)"
      >
        <input formControlName="startDate" skyDatepickerInput type="text" />
      </sky-datepicker>
    </sky-input-box>
  </form>

  <p>
    Selected date: <code>{{ formGroup.value.startDate | json }}</code>
  </p>
</div>

```

---

## Fuzzy datepicker

**Component:** DatetimeDatepickerFuzzyExampleComponent

**Selector:** `app-datetime-datepicker-fuzzy-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyDatepickerHarness } from '@skyux/datetime/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { DatetimeDatepickerFuzzyExampleComponent } from './example.component';

describe('Fuzzy datepicker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    inputHarness: SkyInputBoxHarness;
    datepickerHarness: SkyDatepickerHarness;
    fixture: ComponentFixture<DatetimeDatepickerFuzzyExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      DatetimeDatepickerFuzzyExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const inputHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );
    const datepickerHarness =
      await inputHarness.queryHarness(SkyDatepickerHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { inputHarness, datepickerHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [DatetimeDatepickerFuzzyExampleComponent, NoopAnimationsModule],
    });
  });

  it('should have initial setup values', async () => {
    const { inputHarness, datepickerHarness, fixture } = await setupTest({
      dataSkyId: 'fuzzy-datepicker-example',
    });

    await expectAsync(inputHarness.getHintText()).toBeResolvedTo(
      "Include a partial date if you don't have the exact date.",
    );

    await datepickerHarness.clickCalendarButton();

    await inputHarness.clickHelpInline();
    await expectAsync(inputHarness.getHelpPopoverContent()).toBeResolvedTo(
      fixture.componentInstance.helpPopoverContent,
    );

    await datepickerHarness.clickCalendarButton();
    const calendarHarness = await datepickerHarness.getDatepickerCalendar();
    await expectAsync(calendarHarness.getSelectedValue()).toBeResolvedTo(
      'Saturday, November 5th 1955',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyDatepickerModule } from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';

/**
 * @title Fuzzy datepicker
 */
@Component({
  selector: 'app-datetime-datepicker-fuzzy-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDatepickerModule,
    SkyInputBoxModule,
  ],
})
export class DatetimeDatepickerFuzzyExampleComponent {
  protected formGroup: FormGroup;
  protected hintText =
    "Include a partial date if you don't have the exact date.";
  public helpPopoverContent =
    'Your date of birth ensures that your benefits include the supplemental at-home services for your age group.';

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      dob: new FormControl(new Date(1955, 10, 5), {
        validators: Validators.required,
      }),
    });
  }

  protected get getFuzzyDateForDisplay(): string {
    return JSON.stringify(this.formGroup.get('dob')?.value);
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-input-box
      data-sky-id="fuzzy-datepicker-example"
      labelText="Date of birth"
      [helpPopoverContent]="helpPopoverContent"
      [hintText]="hintText"
    >
      <sky-datepicker>
        <input
          formControlName="dob"
          skyFuzzyDatepickerInput
          type="text"
          [futureDisabled]="true"
        />
      </sky-datepicker>
    </sky-input-box>
  </form>

  <p>
    Selected date: <code>{{ getFuzzyDateForDisplay }}</code>
  </p>
</div>

```

---
---
component: 'timepicker'
type: 'code-examples'
description: 'Code examples for the timepicker component.'
---

# Timepicker Code Examples

## Timepicker with basic setup

**Component:** DatetimeTimepickerBasicExampleComponent

**Selector:** `app-datetime-timepicker-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTimepickerHarness } from '@skyux/datetime/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { DatetimeTimepickerBasicExampleComponent } from './example.component';

describe('Basic timepicker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    inputHarness: SkyInputBoxHarness;
    timepickerHarness: SkyTimepickerHarness;
    fixture: ComponentFixture<DatetimeTimepickerBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      DatetimeTimepickerBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const inputHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );
    const timepickerHarness =
      await inputHarness.queryHarness(SkyTimepickerHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { inputHarness, timepickerHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [DatetimeTimepickerBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should have initial setup values', async () => {
    const { inputHarness, timepickerHarness, fixture } = await setupTest({
      dataSkyId: 'timepicker-example',
    });

    await expectAsync(inputHarness.getHintText()).toBeResolvedTo(
      'Choose a time that allows for late arrivals.',
    );

    await timepickerHarness.clickSelectorButton();

    await inputHarness.clickHelpInline();
    await expectAsync(inputHarness.getHelpPopoverContent()).toBeResolvedTo(
      fixture.componentInstance.helpPopoverContent,
    );

    await timepickerHarness.clickSelectorButton();
    const selectorHarness = await timepickerHarness.getTimepickerSelector();
    await expectAsync(selectorHarness.getSelectedValue()).toBeResolvedTo(
      '2:45 AM',
    );
    await expectAsync(
      (await timepickerHarness.getControl()).isDisabled(),
    ).toBeResolvedTo(false);
  });

  it('should throw an error if selecting an invalid time', async () => {
    const { inputHarness, timepickerHarness } = await setupTest({
      dataSkyId: 'timepicker-example',
    });

    await timepickerHarness.clickSelectorButton();
    const selectorHarness = await timepickerHarness.getTimepickerSelector();

    await selectorHarness.clickMinute('40');
    await expectAsync(
      inputHarness.hasCustomFormError('invalidMinute'),
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
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyTimepickerModule, SkyTimepickerTimeOutput } from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';

interface DemoForm {
  time: FormControl<SkyTimepickerTimeOutput | string>;
}

function isTimepickerOutput(value: unknown): value is SkyTimepickerTimeOutput {
  return !!(value && typeof value === 'object' && 'minute' in value);
}

function validateTime(
  control: AbstractControl<SkyTimepickerTimeOutput | string>,
): ValidationErrors | null {
  const minute = isTimepickerOutput(control.value)
    ? control.value.minute
    : undefined;

  return minute && minute % 15 !== 0 ? { invalidMinute: true } : null;
}

/**
 * @title Timepicker with basic setup
 */
@Component({
  selector: 'app-datetime-timepicker-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyTimepickerModule,
  ],
})
export class DatetimeTimepickerBasicExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected time: FormControl<SkyTimepickerTimeOutput | string>;

  protected hintText = 'Choose a time that allows for late arrivals.';

  public helpPopoverContent =
    'Allow time to complete all activities that your team signed up for. All activities take about 30 minutes, except the ropes course, which takes 60 minutes.';

  constructor() {
    this.time = new FormControl('2:45', {
      nonNullable: true,
      validators: [Validators.required, validateTime],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({ time: this.time });
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-input-box
      data-sky-id="timepicker-example"
      labelText="Start time"
      [helpPopoverContent]="helpPopoverContent"
      [hintText]="hintText"
    >
      <sky-timepicker #timepicker>
        <input
          formControlName="time"
          timeFormat="hh"
          [skyTimepickerInput]="timepicker"
        />
      </sky-timepicker>
      @if (time.errors?.['invalidMinute']) {
        <sky-form-error
          errorName="invalidMinute"
          errorText="Start time must be a 15-minute increment."
        />
      }
    </sky-input-box>
  </form>
</div>

```

---
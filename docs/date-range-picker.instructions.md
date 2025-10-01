---
component: 'date-range-picker'
description: 'Design guidelines, API documentation, and usage instructions for the date-range-picker component extracted from SKY UX documentation.'
---

# Date Range Picker Component Guidelines

## Component Overview
The date range picker's text input and dropdown let users select a date range from a set of well-known options.

## Usage

### ✅ Use when

Use the date range picker when users need to select a range of dates or a single date relative to the current day, such as yesterday.

## Anatomy

- Label
- Select field
- Help inline button
- Hint text

## Options

### Help inline button

When you need to supplement a date range picker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a date range picker, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a date range picker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the date range picker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the date range picker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Specific range

When users select "Specific range," from and to date fields appear.

### Responsiveness

On smaller viewports, the date fields that appear when users select "Specific range" reflow into a one-column layout.

## Related information

### Components

- Datepicker
- Field group
- Help inline button
- Input box

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### DatetimeDateRangePickerBasicExampleComponent

**Selector:** `app-datetime-date-range-picker-basic-example`

**Package:** `@skyux/code-examples`

#### DatetimeDateRangePickerCustomCalculatorExampleComponent

**Selector:** `app-datetime-date-range-picker-custom-calculator-example`

**Package:** `@skyux/code-examples`

#### DatetimeDateRangePickerHelpKeyExampleComponent

**Selector:** `app-datetime-date-range-picker-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyDateRangePickerComponent

**Selector:** `sky-date-range-picker`

**Package:** `@skyux/datetime`

**Inputs:**

- `dateFormat`: `string | undefined` - The date format for
[the `sky-datepicker` components](https://developer.blackbaud.com/skyux/components/datepicker)
that make up the date range picker. The text input is a composite component of
up to two `sky-datepicker` components. (default: "MM/DD/YYYY")
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the date range picker label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to date range picker. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `labelText`: `string | undefined` - The text to display as the date range picker's label.
- `stacked`: `boolean` - Whether the date range picker is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the date range picker. (default: false)
- `calculatorIds`: `SkyDateRangeCalculatorId[]` - IDs for the date range options to include in the picker's dropdown.
The options specify calculator objects that return two `Date` objects to represent date ranges.
By default, this property includes all `SkyDateRangeCalculatorId` values.
- `disabled`: `boolean` - Whether to disable the date range picker on template-driven forms. Don't use
this input on reactive forms because they may overwrite the input or leave
the control out of sync. To set the disabled state on reactive forms,
use the `FormControl` instead. (default: false)
- `label`: `string | undefined` - The label for the date range picker.

#### SkyDateRangePickerModule

**Package:** `@skyux/datetime`

#### SkyDateRangePickerFilters

A set of criteria that can be used to filter a list of `SkyDateRangePickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDateRangePickerHarness

Harness for interacting with date range picker components in tests.

**Package:** `@skyux/datetime/testing`

### Code Examples

#### Date range picker with basic setup

**Selector:** `app-datetime-date-range-picker-basic-example`

**TypeScript:**

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

**Template:**

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

#### Date range picker with custom calculator

**Selector:** `app-datetime-date-range-picker-custom-calculator-example`

**TypeScript:**

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

**Template:**

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

#### Date range picker with help key

**Selector:** `app-datetime-date-range-picker-help-key-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
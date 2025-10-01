---
component: 'datepicker'
description: 'Design guidelines, API documentation, and usage instructions for the datepicker component extracted from SKY UX documentation.'
---

# Datepicker Component Guidelines

## Component Overview
The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use datepickers when users need to enter valid dates.

## Anatomy

- Label
- Input field
- Picker button
- Default hint text
- Picker
- Required field marker
- Help inline button
- Additional hint text
- Key date
- Key date popover
- Disabled date

## Options

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

- Month, day, and year
- Month and day
- Month and year
- Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

- Constraints on the input
- Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the datepicker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

## Related information

### Components

- Date range picker
- Field group
- Help inline button
- Input box
- Popover

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### DatetimeDatepickerBasicExampleComponent

**Selector:** `app-datetime-datepicker-basic-example`

**Package:** `@skyux/code-examples`

#### DatetimeDatepickerCustomDatesExampleComponent

**Selector:** `app-datetime-datepicker-custom-dates-example`

**Package:** `@skyux/code-examples`

#### DatetimeDatepickerFuzzyExampleComponent

**Selector:** `app-datetime-datepicker-fuzzy-example`

**Package:** `@skyux/code-examples`

#### SkyDatepickerCalendarChange

Specifies changes in the datepicker calendar.

**Package:** `@skyux/datetime`

#### SkyDatepickerCalendarComponent

**Selector:** `sky-datepicker-calendar`

**Package:** `@skyux/datetime`

**Inputs:**

- `customDates`: `SkyDatepickerCustomDate[] | undefined`
- `isDaypickerWaiting`: `boolean | undefined`
- `maxDate`: `Date | undefined`
- `minDate`: `Date | undefined`
- `selectedDate`: `Date | undefined` - currently selected date
- `startAtDate`: `Date | undefined`
- `startingDay`: `number` - starting day of the week from 0-6 (0=Sunday, ..., 6=Saturday)

**Outputs:**

- `calendarDateRangeChange`: `EventEmitter<undefined | SkyDatepickerCalendarChange>`
- `calendarModeChange`: `EventEmitter<string>`
- `selectedDateChange`: `EventEmitter<Date>`

#### SkyDatepickerConfigService

**Package:** `@skyux/datetime`

#### SkyDatepickerCustomDate

The configuration for a custom date.

**Package:** `@skyux/datetime`

#### SkyDatepickerInputDirective

Provides date input functionality for inputs and handles date parsing, formatting and
validation. It emits valid dates as `Date` objects and invalid dates as raw string values.

**Selector:** `[skyDatepickerInput]`

**Package:** `@skyux/datetime`

**Inputs:**

- `skyDatepickerNoValidate`: `boolean | undefined` - Whether to disable date validation on the datepicker input. (default: false)
- `dateFormat`: `string | undefined` - The date format for the input. Place this attribute on the `input` element
to override the default in the `SkyDatepickerConfigService`. (default: "MM/DD/YYYY")
- `disabled`: `boolean` - Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `maxDate`: `Date | undefined` - The latest date that is available in the calendar. Place this attribute on
the `input` element to override the default in `SkyDatepickerConfigService`.
- `minDate`: `Date | undefined` - The earliest date that is available in the calendar. Place this attribute on
the `input` element to override the default in `SkyDatepickerConfigService`. To avoid validation errors, the time associated with the minimum date must be midnight. This is necessary because the datepicker automatically sets the time on the `Date` object for selected dates to midnight in the current user's time zone.
- `skyDatepickerInput`: `"" | SkyDatepickerComponent | undefined` - Creates the datepicker input and calendar. Place this directive on an `input` element,
and wrap the input in a `sky-datepicker` component. The value that users select is driven
through the `ngModel` attribute specified on the `input` element. **[Required]**
- `startAtDate`: `Date | undefined` - The date to open the calendar to initially. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`. (default: The current date)
- `startingDay`: `number` - The starting day of the week in the calendar, where `0` sets the starting day
to Sunday. Place this attribute on the `input` element to override the default
in `SkyDatepickerConfigService`. (default: 0)
- `strict`: `boolean` - Whether the format of the date value must match the format from the `dateFormat` value.
If this property is `true` and the datepicker input directive cannot find an exact match, then
the input is marked as invalid.
If this property is `false` and the datepicker input directive cannot find an exact match, then
it attempts to format the string based on the [ISO 8601 standard format](https://www.iso.org/iso-8601-date-and-time-format.html). (default: false)

#### SkyDatepickerComponent

Creates the datepicker button and calendar.
You must wrap this component around an input with the `skyDatepickerInput`
or `skyFuzzyDatepickerInput` directive.

**Selector:** `sky-datepicker`

**Package:** `@skyux/datetime`

**Inputs:**

- `pickerClass`: `string | undefined` - Adds a class to the datepicker. (default: "")

**Outputs:**

- `calendarDateChange`: `OutputEmitterRef<Date>` - Fires when a user selects a date from the calendar.
- `calendarDateRangeChange`: `EventEmitter<SkyDatepickerCalendarChange>` - Fires when the range of displayed dates in the calendar changes. Provides the
current range of displayed dates and a mutable `customDate` property consumers can use
to modify individual dates on the calendar.
- `dateFormatChange`: `EventEmitter<string>`
- `openChange`: `EventEmitter<boolean>`

#### SkyDatepickerModule

**Package:** `@skyux/datetime`

#### SkyFuzzyDatepickerInputDirective

**Selector:** `[skyFuzzyDatepickerInput]`

**Package:** `@skyux/datetime`

**Inputs:**

- `skyDatepickerNoValidate`: `boolean | undefined` - Whether to disable date validation on the fuzzy datepicker input. (default: false)
- `dateFormat`: `string | undefined` - The date format for the input. Place this attribute on the `input` element
to override the default in `SkyDatepickerConfigService`. (default: "MM/DD/YYYY")
- `disabled`: `boolean | undefined` - Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `futureDisabled`: `boolean | undefined` - Whether to prevent users from specifying dates that are in the future.
Place this attribute on the `input` element. (default: false)
- `maxDate`: `SkyFuzzyDate | undefined` - The latest fuzzy date allowed. Place this attribute on the `input` element
to prevent fuzzy dates after a specified date. This property accepts
a `SkyFuzzyDate` value that includes numeric month, day, and year values.
For example: `{ month: 1, day: 1, year: 2027 }`.
- `minDate`: `SkyFuzzyDate | undefined` - The earliest fuzzy date allowed. Place this attribute on the `input` element
to prevent fuzzy dates before a specified date. This property accepts a `SkyFuzzyDate` value
that includes numeric month, day, and year values.
For example: `{ month: 1, day: 1, year: 2007 }`.
- `startAtDate`: `SkyFuzzyDate | undefined` - The fuzzy date to open the calendar to initially.
This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values.
For example: `{ month: 1, day: 1, year: 2007 }`. (default: The current date)
- `startingDay`: `number` - The starting day of the week in the calendar, where `0` sets the starting day
to Sunday. Place this attribute on the `input` element to override the default
in `SkyDatepickerConfigService`. (default: 0)
- `yearRequired`: `boolean | undefined` - Whether to require the year in fuzzy dates. (default: false)

#### SkyDatepickerCalendarHarnessFilters

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerCalendarHarness

Harness for interacting with datepicker calendar in tests.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerFilters

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerHarness

Harness for interacting with datepicker components in tests.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerInputHarness

Harness to interact with the datepicker input harness.

**Package:** `@skyux/datetime/testing`

#### SkyFuzzyDatepickerInputHarness

Harness to interact with the fuzzy datepicker input harness.

**Package:** `@skyux/datetime/testing`

#### SkyAgGridCellEditorDatepickerComponent

**Selector:** `sky-ag-grid-cell-editor-datepicker`

**Package:** `@skyux/ag-grid`

#### SkyCellEditorDatepickerParams

**Package:** `@skyux/ag-grid`

#### SkyAgGridDatepickerProperties

**Package:** `@skyux/ag-grid`

#### SkyDatepickerProperties

**Package:** `@skyux/ag-grid`

⚠️ **This component is deprecated.**

### Code Examples

#### Datepicker with basic setup

**Selector:** `app-datetime-datepicker-basic-example`

**TypeScript:**

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

**Template:**

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

#### Datepicker with custom dates

**Selector:** `app-datetime-datepicker-custom-dates-example`

**TypeScript:**

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

**Template:**

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

#### Fuzzy datepicker

**Selector:** `app-datetime-datepicker-fuzzy-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
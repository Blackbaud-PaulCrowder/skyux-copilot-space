---
component: 'timepicker'
description: 'Design guidelines, API documentation, and usage instructions for the timepicker component extracted from SKY UX documentation.'
---

# Timepicker Component Guidelines

## Component Overview
The timepicker module creates a SKY UX-themed input field and picker for users to enter or select times. Timepickers must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use timepickers when users need to specify the time of day.

Use two timepickers when users need to specify start and stop times.

### ❌ Don't use when

Don't use timepickers when users need to specify general durations or time spans. Use radio buttons or HTML select fields instead.

**❌ Don't use timepickers when users specify hours and minutes as lengths of time.**

## Anatomy

- Label
- Picker button
- Input field
- Picker
- Required field marker
- Help inline button
- Hint text

## Options

### 12-hour timepicker

Use the 12-hour option for regions and users that use 12-hour time designations. This allows users to select hours, minutes, and "AM" or "PM."

### 24-hour timepicker

Use the 24-hour option for regions and users that use 24-hour time designations. This allows users to select hours and minutes.

### Required field marker

When a timepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a timepicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a timepicker, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a timepicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the timepicker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the timepicker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Keyboard entries

Users can use the keyboard to enter time values in the input field. Times automatically resolve to the correct format when the field loses focus.

## Layout

Use 1/2- or 1/3-width columns for individual timepicker fields inside modals, except when using small (300px) modals. When using two timepickers for start and stop times, use 10px of horizontal space between them.

## Related information

### Components

- Datepicker
- Field group
- Help inline button
- Input box
- Popover
- Radio button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### DatetimeTimepickerBasicExampleComponent

**Selector:** `app-datetime-timepicker-basic-example`

**Package:** `@skyux/code-examples`

#### SkyTimepickerTimeFormatType

**Package:** `@skyux/datetime`

#### SkyTimepickerTimeOutput

**Package:** `@skyux/datetime`

#### SkyTimepickerComponent

Creates a SKY UX-themed replacement for the HTML `input` element with `type="time"`.
The value that users select is driven through the `ngModel` attribute
specified on the `input` element. You must wrap this component around an `input`
with the `skyTimepickerInput` directive.

**Selector:** `sky-timepicker`

**Package:** `@skyux/datetime`

**Outputs:**

- `selectedTimeChanged`: `EventEmitter<SkyTimepickerTimeOutput>` - Fires when the value in the timepicker input changes.

#### SkyTimepickerInputDirective

**Selector:** `[skyTimepickerInput]`

**Package:** `@skyux/datetime`

**Inputs:**

- `returnFormat`: `string | undefined` - The custom time format. For examples,
see the [moment.js](https://momentjs.com/docs/#/displaying/format/) docs.
- `disabled`: `boolean` - Whether to disable the timepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `skyTimepickerInput`: `SkyTimepickerComponent | undefined` - Creates the timepicker input field and picker. Place this attribute on an `input` element,
and wrap the input in a `sky-timepicker` component.
This attribute must be set to the instance of the `sky-timepicker`. **[Required]**
- `timeFormat`: `SkyTimepickerTimeFormatType` - The 12-hour `hh` or 24-hour `HH` time format for the input. (default: "hh")

#### SkyTimepickerModule

**Package:** `@skyux/datetime`

#### SkyTimepickerFilters

A set of criteria that can be used to filter a list of `SkyTimepickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyTimepickerHarness

Harness for interacting with timepicker components in tests.

**Package:** `@skyux/datetime/testing`

#### SkyTimepickerInputHarness

Harness to interact with the timepicker input harness.

**Package:** `@skyux/datetime/testing`

#### SkyTimepickerSelectorHarness

Harness for interacting with a timepicker selector in tests.

**Package:** `@skyux/datetime/testing`

### Code Examples

#### Timepicker with basic setup

**Selector:** `app-datetime-timepicker-basic-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
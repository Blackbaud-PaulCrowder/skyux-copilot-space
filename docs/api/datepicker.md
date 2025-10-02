---
component: 'datepicker'
type: 'api-documentation'
description: 'API documentation for the datepicker component including components, interfaces, and types.'
---

# Datepicker API Documentation

## Components and Directives

#### DatetimeDatepickerBasicExampleComponent

**Selector:** `app-datetime-datepicker-basic-example`

**Package:** `@skyux/code-examples`

#### DatetimeDatepickerCustomDatesExampleComponent

**Selector:** `app-datetime-datepicker-custom-dates-example`

**Package:** `@skyux/code-examples`

#### DatetimeDatepickerFuzzyExampleComponent

**Selector:** `app-datetime-datepicker-fuzzy-example`

**Package:** `@skyux/code-examples`

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
through the `ngModel` attribute specified on the `input` element.
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

#### SkyAgGridCellEditorDatepickerComponent

**Selector:** `sky-ag-grid-cell-editor-datepicker`

**Package:** `@skyux/ag-grid`
---
component: 'timepicker'
type: 'api-documentation'
description: 'API documentation for the timepicker component including components, interfaces, and types.'
---

# Timepicker API Documentation

## Components and Directives

#### DatetimeTimepickerBasicExampleComponent

**Selector:** `app-datetime-timepicker-basic-example`

**Package:** `@skyux/code-examples`

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
This attribute must be set to the instance of the `sky-timepicker`.
- `timeFormat`: `SkyTimepickerTimeFormatType` - The 12-hour `hh` or 24-hour `HH` time format for the input. (default: "hh")
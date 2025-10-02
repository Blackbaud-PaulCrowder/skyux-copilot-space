---
component: 'date-range-picker'
type: 'api-documentation'
description: 'API documentation for the date-range-picker component including components, interfaces, and types.'
---

# Date Range Picker API Documentation

## Components and Directives

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
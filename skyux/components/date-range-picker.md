                   

 Date range picker
=================

The date range picker's text input and dropdown let users select a date range from a set of well-known options.

 Usage
------

### Use when

Use the date range picker when users need to select a range of dates or a single date relative to the current day, such as yesterday.

 Anatomy
--------

1

Label

2

Select field

3

Help inline button (optional)

4

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/date-range-picker/date-range-picker-anatomy.cebe74bf5965b3081953025890d0a880.png)

 Options
--------

### Help inline button

When you need to supplement a date range picker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a date range picker, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a date range picker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the date range picker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the date range picker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/date-range-picker/date-range-picker-options-stacked.604bf70bc5ae47d40c028ebed82734cc.png)

 Behavior and states
--------------------

### Specific range

When users select "Specific range," from and to date fields appear.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/date-range-picker/date-range-picker-behavior-specific-range.88feb132b1186e2c2d1104ef5323b499.png)

### Responsiveness

On smaller viewports, the date fields that appear when users select "Specific range" reflow into a one-column layout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/date-range-picker/date-range-picker-behavior-responsive.749272a53b84b7f42d55d96833e98e09.png)

 Related information
--------------------

### Components

*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/date-range-picker/date-range-picker.module.ts#L10) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 SkyDateRangePickerModule
-------------------------

Type: Module

`import { SkyDateRangePickerModule } from '@skyux/datetime';`

 SkyDateRangePickerComponent
----------------------------

Type: Component

Selector: `sky-date-range-picker`

### Inputs

#### `calculatorIds: SkyDateRangeCalculatorId[]`

IDs for the date range options to include in the picker's dropdown. The options specify calculator objects that return two `Date` objects to represent date ranges. By default, this property includes all `SkyDateRangeCalculatorId` values.

#### `dateFormat: string | undefined`

The date format for [the `sky-datepicker` components](/skyux/components/datepicker.md) that make up the date range picker. The text input is a composite component of up to two `sky-datepicker` components.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean`

Whether to disable the date range picker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the date range picker label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to date range picker. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `label: string | undefined`

Warning: **Deprecated.** Use the `labelText` input instead.

The label for the date range picker.

#### `labelText: string | undefined`

The text to display as the date range picker's label.

#### `stacked: boolean`

Whether the date range picker is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the date range picker.

Default: `false`

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyDateRangeService
--------------------

Type: Service

Creates and manages `SkyDateRangeCalculator` instances.

### Properties

#### `calculators: SkyDateRangeCalculator[]`

### Methods

#### `createCalculator(config: SkyDateRangeCalculatorConfig): SkyDateRangeCalculator`

Creates a custom date range calculator.

#### Parameters

##### `config: SkyDateRangeCalculatorConfig`

The calculator config.

#### Returns

`SkyDateRangeCalculator`

#### `filterCalculators(calculatorIds: SkyDateRangeCalculatorId[]): SkyDateRangeCalculator[]`

Returns calculators from an array of calculator IDs.

#### Parameters

##### `calculatorIds: SkyDateRangeCalculatorId[]`

The array of calculator IDs.

#### Returns

`SkyDateRangeCalculator[]`

#### `getCalculatorById(id: SkyDateRangeCalculatorId): Promise<SkyDateRangeCalculator>`

Warning: **Deprecated.** Call `filterCalculators()` instead.

Returns a calculator from a calculator ID.

#### Parameters

##### `id: SkyDateRangeCalculatorId`

The calculator ID.

#### Returns

`Promise<SkyDateRangeCalculator>`

#### `getCalculators(ids: SkyDateRangeCalculatorId[]): Promise<SkyDateRangeCalculator[]>`

Warning: **Deprecated.** Call `filterCalculators()` instead.

Returns calculators from an array of calculator IDs.

#### Parameters

##### `ids: SkyDateRangeCalculatorId[]`

The array of calculator IDs.

#### Returns

`Promise<SkyDateRangeCalculator[]>`

 SkyDateRange
-------------

Type: Interface

    interface SkyDateRange {
      endDate?: null | Date;
      startDate?: null | Date;
    }

### Properties

#### `endDate?: null | Date`

The last date in the date range.

#### `startDate?: null | Date`

The first date in the date range.

 SkyDateRangeCalculation
------------------------

Type: Interface

Represents the returned value of a `SkyDateRangeCalculator`.

    interface SkyDateRangeCalculation {
      calculatorId: SkyDateRangeCalculatorId;
      endDate?: null | Date;
      startDate?: null | Date;
    }

### Properties

#### `calculatorId: SkyDateRangeCalculatorId`

The calculator that determines the dates in the date range.

#### `endDate?: null | Date`

The last date in the date range.

#### `startDate?: null | Date`

The first date in the date range.

 SkyDateRangeCalculator
-----------------------

Type: Class

Represents the calculator.

### Properties

#### `calculatorId: SkyDateRangeCalculatorId`

The calculator ID that specifies calculator objects that represent date ranges.

#### `shortDescription: string`

Warning: **Deprecated.** Subscribe to the `shortDescription$` observable instead.

The text to display in the calculator select menu.

#### `type: SkyDateRangeCalculatorType`

The type of calculations available for the date range.

#### `shortDescription$: Observable<string>`

The text to display in the calculator select menu.

### Methods

#### `getValue(startDateInput?: null | Date, endDateInput?: null | Date): SkyDateRangeCalculation`

Gets the current value of the calculator.

#### Parameters

##### `startDateInput?: null | Date`

The start date.

##### `endDateInput?: null | Date`

The end date.

#### Returns

`SkyDateRangeCalculation`

#### `validate(value?: SkyDateRange): null | ValidationErrors`

Performs synchronous validation against the control.

#### Parameters

##### `value?: SkyDateRange`

#### Returns

`null | ValidationErrors`

 SkyDateRangeCalculatorConfig
-----------------------------

Type: Interface

The configuration for a date range calculator.

    interface SkyDateRangeCalculatorConfig {
      getValue: SkyDateRangeCalculatorGetValueFunction;
      shortDescription: string;
      type: SkyDateRangeCalculatorType;
      validate?: SkyDateRangeCalculatorValidateFunction;
    }

### Properties

#### `getValue: SkyDateRangeCalculatorGetValueFunction`

A callback function that returns a `SkyDateRange` value.

#### `shortDescription: string`

Text to display within the calculator select menu to represent your calculator.

#### `type: SkyDateRangeCalculatorType`

The type of calculator to create.

#### `validate?: SkyDateRangeCalculatorValidateFunction`

A callback function that accepts user-selected start and end dates. Returning an Angular `ValidationErrors` value invalidates the date range form control.

 SkyDateRangeCalculatorId
-------------------------

Type: Enumeration

`SkyDateRangeCalculatorId` values specify calculator objects that return two `Date` objects to represent date ranges. The values populate the options in the date range picker's dropdown. SKY UX uses `SkyDateRangeService` to create calculators and configures each one with a `validate` function to confirm that dates are compatible. For example, `validate` functions ensure that start dates are before end dates. SKY UX also configures calculators to call a `getValue` function after the `validate` function and return a range of two `Date` objects.

    enum SkyDateRangeCalculatorId {
      After = 2,
      AnyTime = 0,
      Before = 1,
      LastCalendarYear = 16,
      LastFiscalYear = 19,
      LastMonth = 10,
      LastQuarter = 13,
      LastWeek = 7,
      NextCalendarYear = 18,
      NextFiscalYear = 21,
      NextMonth = 12,
      NextQuarter = 15,
      NextWeek = 9,
      SpecificRange = 3,
      ThisCalendarYear = 17,
      ThisFiscalYear = 20,
      ThisMonth = 11,
      ThisQuarter = 14,
      ThisWeek = 8,
      Today = 5,
      Tomorrow = 6,
      Yesterday = 4,
    }

### Properties

#### `SkyDateRangeCalculatorId.After`

Enables users to select a start date with no end date.

#### `SkyDateRangeCalculatorId.AnyTime`

Selects no dates and considers all dates within the date range. This is the default selection.

#### `SkyDateRangeCalculatorId.Before`

Enables users to select an end date with no starting date.

#### `SkyDateRangeCalculatorId.LastCalendarYear`

Sets the start date to the first day of the year before the current year and the end date to the last day of that year.

#### `SkyDateRangeCalculatorId.LastFiscalYear`

Sets the start date to the first day of the fiscal year before the current fiscal year and the end date to the last day of that fiscal year. The fiscal year is Oct. 1 to Sept. 30.

#### `SkyDateRangeCalculatorId.LastMonth`

Sets the start date to the first day of the month before the current month and the end date to the last day of that month.

#### `SkyDateRangeCalculatorId.LastQuarter`

Sets the start date to the first day of the quarter before the current quarter and the end date to the last day of that quarter. Quarters are January to March, April to June, July to September, and October to December.

#### `SkyDateRangeCalculatorId.LastWeek`

Sets the start date to Sunday of the week before the current week and the end date to Saturday of that week.

#### `SkyDateRangeCalculatorId.NextCalendarYear`

Sets the start date to the first day of the year after the current year and the end date to the last day of that year.

#### `SkyDateRangeCalculatorId.NextFiscalYear`

Sets the start date to the first day of the fiscal year after the current fiscal year and the end date to the last day of that fiscal year. The fiscal year is Oct. 1 to Sept. 30.

#### `SkyDateRangeCalculatorId.NextMonth`

Sets the start date to the first day of the month after the current month and the end date to the last day of that month.

#### `SkyDateRangeCalculatorId.NextQuarter`

Sets the start date to the first day of the quarter after the current quarter and the end date to the last day of that quarter. Quarters are January to March, April to June, July to September, and October to December.

#### `SkyDateRangeCalculatorId.NextWeek`

Sets the start date to Sunday of the week after the current week and the end date to Saturday of that week.

#### `SkyDateRangeCalculatorId.SpecificRange`

Enables users to select specific start and end dates.

#### `SkyDateRangeCalculatorId.ThisCalendarYear`

Sets the start date to the first day of the current year and the end date to the last day of the year.

#### `SkyDateRangeCalculatorId.ThisFiscalYear`

Sets the start date to the first day of the current fiscal year and the end date to the last day of the fiscal year. The fiscal year is Oct. 1 to Sept. 30.

#### `SkyDateRangeCalculatorId.ThisMonth`

Sets the start date to the first day of the current month and the end date to the last day of the month.

#### `SkyDateRangeCalculatorId.ThisQuarter`

Sets the start date to the first day of the current quarter and the end date to the last day of the quarter. Quarters are January to March, April to June, July to September, and October to December.

#### `SkyDateRangeCalculatorId.ThisWeek`

Sets the start date to Sunday of the current week and the end date to Saturday.

#### `SkyDateRangeCalculatorId.Today`

Sets the start and end dates to the current day.

#### `SkyDateRangeCalculatorId.Tomorrow`

Sets the start and end dates to the day after the current day.

#### `SkyDateRangeCalculatorId.Yesterday`

Sets the start and end dates to the day before the current day.

 SkyDateRangeCalculatorType
---------------------------

Type: Enumeration

The types of calculations available for a date range calculator.

    enum SkyDateRangeCalculatorType {
      After = 0,
      Before = 1,
      Range = 2,
      Relative = 3,
    }

### Properties

#### `SkyDateRangeCalculatorType.After`

Includes an input for a date after the current date.

#### `SkyDateRangeCalculatorType.Before`

Includes an input for a date before the current date.

#### `SkyDateRangeCalculatorType.Range`

Includes two inputs for a range of dates.

#### `SkyDateRangeCalculatorType.Relative`

Does not accept any input but calculates a specific range based on the current date.

 SkyDateRangeCalculatorGetValueFunction
---------------------------------------

Type: Type alias

    type SkyDateRangeCalculatorGetValueFunction = (startDateInput?: Date | null, endDateInput?: Date | null) => SkyDateRange

 SkyDateRangeCalculatorValidateFunction
---------------------------------------

Type: Type alias

    type SkyDateRangeCalculatorValidateFunction = (value?: SkyDateRange) => ValidationErrors | null

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDateRangePickerHarness
--------------------------

Type: Class

`import { SkyDateRangePickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with date range picker components in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getEndDateValue(): Promise<string>`

Gets the end date value.

#### Returns

`Promise<string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help inline popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the label text.

#### Returns

`Promise<string>`

#### `getSelectedCalculator(): Promise<SkyDateRangeCalculatorId>`

Gets the selected calculator ID.

#### Returns

`Promise<SkyDateRangeCalculatorId>`

#### `getStartDateValue(): Promise<string>`

Gets the start date value.

#### Returns

`Promise<string>`

#### `hasEndDateBeforeStartDateError(): Promise<boolean>`

Whether date range picker end date before start date error is thrown.

#### Returns

`Promise<boolean>`

#### `hasEndDateRequiredError(): Promise<boolean>`

Whether end date input has required error.

#### Returns

`Promise<boolean>`

#### `hasError(errorName: string): Promise<boolean>`

Whether a custom error has fired.

#### Parameters

##### `errorName: string`

`errorName` property of the custom `sky-form-error`.

#### Returns

`Promise<boolean>`

#### `hasStartDateRequiredError(): Promise<boolean>`

Whether start date input has required error.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the date range picker component is disabled.

#### Returns

`Promise<boolean>`

#### `isEndDateVisible(): Promise<boolean>`

Whether end date datepicker is visible.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the date range picker has stacked enabled.

#### Returns

`Promise<boolean>`

#### `isStartDateVisible(): Promise<boolean>`

Whether start date datepicker is visible.

#### Returns

`Promise<boolean>`

#### `selectCalculator(calculatorId: SkyDateRangeCalculatorId): Promise<void>`

Selects the specified calculator.

#### Parameters

##### `calculatorId: SkyDateRangeCalculatorId`

#### Returns

`Promise<void>`

#### `setEndDateValue(newDate: string): Promise<void>`

Sets the end date.

#### Parameters

##### `newDate: string`

date input as a formatted string.

#### Returns

`Promise<void>`

#### `setStartDateValue(newDate: string): Promise<void>`

Sets the start date.

#### Parameters

##### `newDate: string`

date input as a formatted string.

#### Returns

`Promise<void>`

#### `SkyDateRangePickerHarness.with(filters: SkyDateRangePickerFilters): HarnessPredicate<SkyDateRangePickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDateRangePickerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDateRangePickerFilters`

#### Returns

`HarnessPredicate<SkyDateRangePickerHarness>`

 SkyDateRangePickerFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDateRangePickerHarness` instances.

    interface SkyDateRangePickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
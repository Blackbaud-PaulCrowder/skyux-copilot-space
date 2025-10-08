# Design

                   Skip to Main Content

 Datepicker
==========

The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use datepickers when users need to enter valid dates.

 Anatomy
--------

1

Label

2

Input field

3

Picker button

4

Default hint text

5

Picker

6

Required field marker (optional)

7

Help inline button (optional)

8

Additional hint text (optional)

9

Key date (optional)

10

Key date popover (optional)

11

Disabled date (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-anatomy.ff895423ee42690c816d1f7859e22753.png)

 Options
--------

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

*   Month, day, and year
*   Month and day
*   Month and year
*   Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

*   Constraints on the input
*   Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

You can display details about key dates in a [popover](/skyux/components/popover.md) that appears when users hover over the dates. Use plain text, and be as concise as possible. If key dates are important for multiple reasons, summarize or stack the details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-keydates.7de0268543b8f455792cb8c6ed6ded4e.png)

Do use key dates to alert users to highly relevant dates when they make selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-disabled.c72636b3f07f56b91e59833dbb7c0e27.png)

Do use disabled dates to prevent users from making invalid selections.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the datepicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-stacked.a4f02d3b201170fa3b62dfb577b9c49a.png)

 Behavior and states
--------------------

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-conversion.0cdcc1ce631eafe4cb43227b13290f34.png)

 Related information
--------------------

### Components

*   [Date range picker](/skyux/components/date-range-picker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Popover](/skyux/components/popover.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/datepicker/datepicker.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 Setup
------

To enable standard form features, you must wrap the datepicker in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyDatepickerModule
--------------------

Type: Module

`import { SkyDatepickerModule } from '@skyux/datetime';`

 SkyDatepickerComponent
-----------------------

Type: Component

Selector: `sky-datepicker`

Creates the datepicker button and calendar. You must wrap this component around an input with the `skyDatepickerInput` or `skyFuzzyDatepickerInput` directive.

### Inputs

#### `pickerClass: string | undefined`

Adds a class to the datepicker.

Default: `""`

### Outputs

#### `calendarDateRangeChange: EventEmitter<SkyDatepickerCalendarChange>`

Fires when the range of displayed dates in the calendar changes. Provides the current range of displayed dates and a mutable `customDate` property consumers can use to modify individual dates on the calendar.

 SkyDatepickerInputDirective
----------------------------

Type: Directive

Selector: `[skyDatepickerInput]`

Provides date input functionality for inputs and handles date parsing, formatting and validation. It emits valid dates as `Date` objects and invalid dates as raw string values.

### Inputs

#### `skyDatepickerInput: "" | SkyDatepickerComponent | undefined`

Required

Creates the datepicker input and calendar. Place this directive on an `input` element, and wrap the input in a `sky-datepicker` component. The value that users select is driven through the `ngModel` attribute specified on the `input` element.

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in the `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `maxDate: Date | undefined`

The latest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

#### `minDate: Date | undefined`

The earliest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the datepicker input.

Default: `false`

#### `startAtDate: Date | undefined`

The date to open the calendar to initially. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `strict: boolean`

Whether the format of the date value must match the format from the `dateFormat` value. If this property is `true` and the datepicker input directive cannot find an exact match, then the input is marked as invalid. If this property is `false` and the datepicker input directive cannot find an exact match, then it attempts to format the string based on the [ISO 8601 standard format](https://www.iso.org/iso-8601-date-and-time-format.html).

Default: `false`

 SkyDatepickerCalendarChange
----------------------------

Type: Interface

Specifies changes in the datepicker calendar.

    interface SkyDatepickerCalendarChange {
      customDates?: Observable<SkyDatepickerCustomDate[]>;
      endDate: Date;
      startDate: Date;
    }

### Properties

#### `customDates?: Observable<SkyDatepickerCustomDate[]>`

The observable that allows the consumer to push custom dates back to the calendar when the `SkyDatepickerCalendarChange` event fires. This is useful for displaying key dates or disabled dates each time the calendar changes. If disabled dates are provided, SKY UX will prevent the user from selecting the date from the calendar. However, consumers will still need to add a custom validator to prevent users from entering disabled dates in the text input.

#### `endDate: Date`

The end date.

#### `startDate: Date`

The start date.

 SkyDatepickerConfigService
---------------------------

Type: Service

### Properties

#### `dateFormat: string | undefined`

The date format for the input.

Default: `"MM/DD/YYYY"`

#### `maxDate: Date | undefined`

The latest selectable date that is available in the calendar.

#### `minDate: Date | undefined`

The earliest selectable date that is available in the calendar.

#### `startAtDate: Date | undefined`

The date to open the calendar to initially.

Default: `the current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday.

Default: `0`

 SkyDatepickerCustomDate
------------------------

Type: Interface

The configuration for a custom date.

    interface SkyDatepickerCustomDate {
      date: Date;
      disabled?: boolean;
      keyDate?: boolean;
      keyDateText?: string[];
    }

### Properties

#### `date: Date`

The date to customize.

#### `disabled?: boolean`

Whether to disable the date.

#### `keyDate?: boolean`

Whether to display the date as a key date in the calendar.

#### `keyDateText?: string[]`

Displays a popup of the provided text when hovering over the key date in the calendar.

 SkyFuzzyDatepickerInputDirective
---------------------------------

Type: Directive

Selector: `[skyFuzzyDatepickerInput]`

### Inputs

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean | undefined`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `futureDisabled: boolean | undefined`

Whether to prevent users from specifying dates that are in the future. Place this attribute on the `input` element.

Default: `false`

#### `maxDate: SkyFuzzyDate | undefined`

The latest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates after a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2027 }`.

#### `minDate: SkyFuzzyDate | undefined`

The earliest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates before a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the fuzzy datepicker input.

Default: `false`

#### `startAtDate: SkyFuzzyDate | undefined`

The fuzzy date to open the calendar to initially. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `yearRequired: boolean | undefined`

Whether to require the year in fuzzy dates.

Default: `false`

 SkyFuzzyDate
-------------

Type: Interface

    interface SkyFuzzyDate {
      day?: number;
      month?: number;
      year?: number;
    }

### Properties

#### `day?: number`

The day in a fuzzy date, where `1` sets the day to the first day of the specified month.

#### `month?: number`

The month in a fuzzy date, where `1` sets the month to January.

#### `year?: number`

The year in a fuzzy date.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDatepickerHarness
---------------------

Type: Class

`import { SkyDatepickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker components in tests.

### Methods

#### `clickCalendarButton(): Promise<void>`

Clicks the calendar button.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

Gets the datepicker input harness.

#### Returns

`Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

#### `getDatepickerCalendar(): Promise<SkyDatepickerCalendarHarness>`

Gets the `SkyDatepickerCalendarHarness` for the calendar picker controlled by the datepicker. Throws an error if the calendar picker is not open.

#### Returns

`Promise<SkyDatepickerCalendarHarness>`

#### `isDatepickerOpen(): Promise<boolean>`

Whether the datepicker calendar picker is open.

#### Returns

`Promise<boolean>`

#### `SkyDatepickerHarness.with(filters: SkyDatepickerFilters): HarnessPredicate<SkyDatepickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDatepickerHarness` that meets certain criteria.

These filters only work for standalone datepickers. For datepickers wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyDatepickerFilters`

#### Returns

`HarnessPredicate<SkyDatepickerHarness>`

 SkyDatepickerFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

    interface SkyDatepickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDatepickerInputHarness
--------------------------

Type: Class

`import { SkyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyFuzzyDatepickerInputHarness
-------------------------------

Type: Class

`import { SkyFuzzyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the fuzzy datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyDatepickerCalendarHarness
-----------------------------

Type: Class

`import { SkyDatepickerCalendarHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker calendar in tests.

### Methods

#### `clickDate(date: string): Promise<void>`

Clicks the specified date, month or year in the following format day format: dddd, MMMM Do YYYY month format: MMMM YYYY year format: YYYY

#### Parameters

##### `date: string`

#### Returns

`Promise<void>`

#### `clickNextButton(): Promise<void>`

Clicks the 'next' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the 'previous' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickTitleButton(): Promise<void>`

Clicks the 'title' button on the calendar header.

#### Returns

`Promise<void>`

#### `getCalendarMode(): Promise<string>`

Gets the current calendar mode.

#### Returns

`Promise<string>`

#### `getCalendarTitle(): Promise<string>`

Gets the current title.

#### Returns

`Promise<string>`

#### `getSelectedValue(): Promise<null | string>`

Gets the long date value of the currently selected calendar item.

#### Returns

`Promise<null | string>`

 SkyDatepickerCalendarHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

    interface SkyDatepickerCalendarHarnessFilters {}

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

# Development

                   Skip to Main Content

 Datepicker
==========

The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use datepickers when users need to enter valid dates.

 Anatomy
--------

1

Label

2

Input field

3

Picker button

4

Default hint text

5

Picker

6

Required field marker (optional)

7

Help inline button (optional)

8

Additional hint text (optional)

9

Key date (optional)

10

Key date popover (optional)

11

Disabled date (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-anatomy.ff895423ee42690c816d1f7859e22753.png)

 Options
--------

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

*   Month, day, and year
*   Month and day
*   Month and year
*   Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

*   Constraints on the input
*   Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

You can display details about key dates in a [popover](/skyux/components/popover.md) that appears when users hover over the dates. Use plain text, and be as concise as possible. If key dates are important for multiple reasons, summarize or stack the details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-keydates.7de0268543b8f455792cb8c6ed6ded4e.png)

Do use key dates to alert users to highly relevant dates when they make selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-disabled.c72636b3f07f56b91e59833dbb7c0e27.png)

Do use disabled dates to prevent users from making invalid selections.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the datepicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-stacked.a4f02d3b201170fa3b62dfb577b9c49a.png)

 Behavior and states
--------------------

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-conversion.0cdcc1ce631eafe4cb43227b13290f34.png)

 Related information
--------------------

### Components

*   [Date range picker](/skyux/components/date-range-picker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Popover](/skyux/components/popover.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/datepicker/datepicker.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 Setup
------

To enable standard form features, you must wrap the datepicker in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyDatepickerModule
--------------------

Type: Module

`import { SkyDatepickerModule } from '@skyux/datetime';`

 SkyDatepickerComponent
-----------------------

Type: Component

Selector: `sky-datepicker`

Creates the datepicker button and calendar. You must wrap this component around an input with the `skyDatepickerInput` or `skyFuzzyDatepickerInput` directive.

### Inputs

#### `pickerClass: string | undefined`

Adds a class to the datepicker.

Default: `""`

### Outputs

#### `calendarDateRangeChange: EventEmitter<SkyDatepickerCalendarChange>`

Fires when the range of displayed dates in the calendar changes. Provides the current range of displayed dates and a mutable `customDate` property consumers can use to modify individual dates on the calendar.

 SkyDatepickerInputDirective
----------------------------

Type: Directive

Selector: `[skyDatepickerInput]`

Provides date input functionality for inputs and handles date parsing, formatting and validation. It emits valid dates as `Date` objects and invalid dates as raw string values.

### Inputs

#### `skyDatepickerInput: "" | SkyDatepickerComponent | undefined`

Required

Creates the datepicker input and calendar. Place this directive on an `input` element, and wrap the input in a `sky-datepicker` component. The value that users select is driven through the `ngModel` attribute specified on the `input` element.

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in the `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `maxDate: Date | undefined`

The latest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

#### `minDate: Date | undefined`

The earliest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the datepicker input.

Default: `false`

#### `startAtDate: Date | undefined`

The date to open the calendar to initially. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `strict: boolean`

Whether the format of the date value must match the format from the `dateFormat` value. If this property is `true` and the datepicker input directive cannot find an exact match, then the input is marked as invalid. If this property is `false` and the datepicker input directive cannot find an exact match, then it attempts to format the string based on the [ISO 8601 standard format](https://www.iso.org/iso-8601-date-and-time-format.html).

Default: `false`

 SkyDatepickerCalendarChange
----------------------------

Type: Interface

Specifies changes in the datepicker calendar.

    interface SkyDatepickerCalendarChange {
      customDates?: Observable<SkyDatepickerCustomDate[]>;
      endDate: Date;
      startDate: Date;
    }

### Properties

#### `customDates?: Observable<SkyDatepickerCustomDate[]>`

The observable that allows the consumer to push custom dates back to the calendar when the `SkyDatepickerCalendarChange` event fires. This is useful for displaying key dates or disabled dates each time the calendar changes. If disabled dates are provided, SKY UX will prevent the user from selecting the date from the calendar. However, consumers will still need to add a custom validator to prevent users from entering disabled dates in the text input.

#### `endDate: Date`

The end date.

#### `startDate: Date`

The start date.

 SkyDatepickerConfigService
---------------------------

Type: Service

### Properties

#### `dateFormat: string | undefined`

The date format for the input.

Default: `"MM/DD/YYYY"`

#### `maxDate: Date | undefined`

The latest selectable date that is available in the calendar.

#### `minDate: Date | undefined`

The earliest selectable date that is available in the calendar.

#### `startAtDate: Date | undefined`

The date to open the calendar to initially.

Default: `the current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday.

Default: `0`

 SkyDatepickerCustomDate
------------------------

Type: Interface

The configuration for a custom date.

    interface SkyDatepickerCustomDate {
      date: Date;
      disabled?: boolean;
      keyDate?: boolean;
      keyDateText?: string[];
    }

### Properties

#### `date: Date`

The date to customize.

#### `disabled?: boolean`

Whether to disable the date.

#### `keyDate?: boolean`

Whether to display the date as a key date in the calendar.

#### `keyDateText?: string[]`

Displays a popup of the provided text when hovering over the key date in the calendar.

 SkyFuzzyDatepickerInputDirective
---------------------------------

Type: Directive

Selector: `[skyFuzzyDatepickerInput]`

### Inputs

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean | undefined`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `futureDisabled: boolean | undefined`

Whether to prevent users from specifying dates that are in the future. Place this attribute on the `input` element.

Default: `false`

#### `maxDate: SkyFuzzyDate | undefined`

The latest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates after a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2027 }`.

#### `minDate: SkyFuzzyDate | undefined`

The earliest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates before a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the fuzzy datepicker input.

Default: `false`

#### `startAtDate: SkyFuzzyDate | undefined`

The fuzzy date to open the calendar to initially. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `yearRequired: boolean | undefined`

Whether to require the year in fuzzy dates.

Default: `false`

 SkyFuzzyDate
-------------

Type: Interface

    interface SkyFuzzyDate {
      day?: number;
      month?: number;
      year?: number;
    }

### Properties

#### `day?: number`

The day in a fuzzy date, where `1` sets the day to the first day of the specified month.

#### `month?: number`

The month in a fuzzy date, where `1` sets the month to January.

#### `year?: number`

The year in a fuzzy date.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDatepickerHarness
---------------------

Type: Class

`import { SkyDatepickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker components in tests.

### Methods

#### `clickCalendarButton(): Promise<void>`

Clicks the calendar button.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

Gets the datepicker input harness.

#### Returns

`Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

#### `getDatepickerCalendar(): Promise<SkyDatepickerCalendarHarness>`

Gets the `SkyDatepickerCalendarHarness` for the calendar picker controlled by the datepicker. Throws an error if the calendar picker is not open.

#### Returns

`Promise<SkyDatepickerCalendarHarness>`

#### `isDatepickerOpen(): Promise<boolean>`

Whether the datepicker calendar picker is open.

#### Returns

`Promise<boolean>`

#### `SkyDatepickerHarness.with(filters: SkyDatepickerFilters): HarnessPredicate<SkyDatepickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDatepickerHarness` that meets certain criteria.

These filters only work for standalone datepickers. For datepickers wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyDatepickerFilters`

#### Returns

`HarnessPredicate<SkyDatepickerHarness>`

 SkyDatepickerFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

    interface SkyDatepickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDatepickerInputHarness
--------------------------

Type: Class

`import { SkyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyFuzzyDatepickerInputHarness
-------------------------------

Type: Class

`import { SkyFuzzyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the fuzzy datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyDatepickerCalendarHarness
-----------------------------

Type: Class

`import { SkyDatepickerCalendarHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker calendar in tests.

### Methods

#### `clickDate(date: string): Promise<void>`

Clicks the specified date, month or year in the following format day format: dddd, MMMM Do YYYY month format: MMMM YYYY year format: YYYY

#### Parameters

##### `date: string`

#### Returns

`Promise<void>`

#### `clickNextButton(): Promise<void>`

Clicks the 'next' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the 'previous' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickTitleButton(): Promise<void>`

Clicks the 'title' button on the calendar header.

#### Returns

`Promise<void>`

#### `getCalendarMode(): Promise<string>`

Gets the current calendar mode.

#### Returns

`Promise<string>`

#### `getCalendarTitle(): Promise<string>`

Gets the current title.

#### Returns

`Promise<string>`

#### `getSelectedValue(): Promise<null | string>`

Gets the long date value of the currently selected calendar item.

#### Returns

`Promise<null | string>`

 SkyDatepickerCalendarHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

    interface SkyDatepickerCalendarHarnessFilters {}

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

# Examples

                     Skip to Main Content

 Datepicker
==========

The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.Usage
------

### Use when

Use datepickers when users need to enter valid dates.

 Anatomy
--------

1

Label

2

Input field

3

Picker button

4

Default hint text

5

Picker

6

Required field marker (optional)

7

Help inline button (optional)

8

Additional hint text (optional)

9

Key date (optional)

10

Key date popover (optional)

11

Disabled date (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-anatomy.ff895423ee42690c816d1f7859e22753.png)

 Options
--------

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

*   Month, day, and year
*   Month and day
*   Month and year
*   Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

*   Constraints on the input
*   Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

You can display details about key dates in a [popover](/skyux/components/popover.md) that appears when users hover over the dates. Use plain text, and be as concise as possible. If key dates are important for multiple reasons, summarize or stack the details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-keydates.7de0268543b8f455792cb8c6ed6ded4e.png)

Do use key dates to alert users to highly relevant dates when they make selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-disabled.c72636b3f07f56b91e59833dbb7c0e27.png)

Do use disabled dates to prevent users from making invalid selections.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the datepicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-stacked.a4f02d3b201170fa3b62dfb577b9c49a.png)

 Behavior and states
--------------------

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-conversion.0cdcc1ce631eafe4cb43227b13290f34.png)

 Related information
--------------------

### Components

*   [Date range picker](/skyux/components/date-range-picker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Popover](/skyux/components/popover.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/datepicker/datepicker.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 Setup
------

To enable standard form features, you must wrap the datepicker in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyDatepickerModule
--------------------

Type: Module

`import { SkyDatepickerModule } from '@skyux/datetime';`

 SkyDatepickerComponent
-----------------------

Type: Component

Selector: `sky-datepicker`

Creates the datepicker button and calendar. You must wrap this component around an input with the `skyDatepickerInput` or `skyFuzzyDatepickerInput` directive.

### Inputs

#### `pickerClass: string | undefined`

Adds a class to the datepicker.

Default: `""`

### Outputs

#### `calendarDateRangeChange: EventEmitter<SkyDatepickerCalendarChange>`

Fires when the range of displayed dates in the calendar changes. Provides the current range of displayed dates and a mutable `customDate` property consumers can use to modify individual dates on the calendar.

 SkyDatepickerInputDirective
----------------------------

Type: Directive

Selector: `[skyDatepickerInput]`

Provides date input functionality for inputs and handles date parsing, formatting and validation. It emits valid dates as `Date` objects and invalid dates as raw string values.

### Inputs

#### `skyDatepickerInput: "" | SkyDatepickerComponent | undefined`

Required

Creates the datepicker input and calendar. Place this directive on an `input` element, and wrap the input in a `sky-datepicker` component. The value that users select is driven through the `ngModel` attribute specified on the `input` element.

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in the `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `maxDate: Date | undefined`

The latest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

#### `minDate: Date | undefined`

The earliest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the datepicker input.

Default: `false`

#### `startAtDate: Date | undefined`

The date to open the calendar to initially. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `strict: boolean`

Whether the format of the date value must match the format from the `dateFormat` value. If this property is `true` and the datepicker input directive cannot find an exact match, then the input is marked as invalid. If this property is `false` and the datepicker input directive cannot find an exact match, then it attempts to format the string based on the [ISO 8601 standard format](https://www.iso.org/iso-8601-date-and-time-format.html).

Default: `false`

 SkyDatepickerCalendarChange
----------------------------

Type: Interface

Specifies changes in the datepicker calendar.

    interface SkyDatepickerCalendarChange {
      customDates?: Observable<SkyDatepickerCustomDate[]>;
      endDate: Date;
      startDate: Date;
    }

### Properties

#### `customDates?: Observable<SkyDatepickerCustomDate[]>`

The observable that allows the consumer to push custom dates back to the calendar when the `SkyDatepickerCalendarChange` event fires. This is useful for displaying key dates or disabled dates each time the calendar changes. If disabled dates are provided, SKY UX will prevent the user from selecting the date from the calendar. However, consumers will still need to add a custom validator to prevent users from entering disabled dates in the text input.

#### `endDate: Date`

The end date.

#### `startDate: Date`

The start date.

 SkyDatepickerConfigService
---------------------------

Type: Service

### Properties

#### `dateFormat: string | undefined`

The date format for the input.

Default: `"MM/DD/YYYY"`

#### `maxDate: Date | undefined`

The latest selectable date that is available in the calendar.

#### `minDate: Date | undefined`

The earliest selectable date that is available in the calendar.

#### `startAtDate: Date | undefined`

The date to open the calendar to initially.

Default: `the current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday.

Default: `0`

 SkyDatepickerCustomDate
------------------------

Type: Interface

The configuration for a custom date.

    interface SkyDatepickerCustomDate {
      date: Date;
      disabled?: boolean;
      keyDate?: boolean;
      keyDateText?: string[];
    }

### Properties

#### `date: Date`

The date to customize.

#### `disabled?: boolean`

Whether to disable the date.

#### `keyDate?: boolean`

Whether to display the date as a key date in the calendar.

#### `keyDateText?: string[]`

Displays a popup of the provided text when hovering over the key date in the calendar.

 SkyFuzzyDatepickerInputDirective
---------------------------------

Type: Directive

Selector: `[skyFuzzyDatepickerInput]`

### Inputs

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean | undefined`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `futureDisabled: boolean | undefined`

Whether to prevent users from specifying dates that are in the future. Place this attribute on the `input` element.

Default: `false`

#### `maxDate: SkyFuzzyDate | undefined`

The latest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates after a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2027 }`.

#### `minDate: SkyFuzzyDate | undefined`

The earliest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates before a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the fuzzy datepicker input.

Default: `false`

#### `startAtDate: SkyFuzzyDate | undefined`

The fuzzy date to open the calendar to initially. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `yearRequired: boolean | undefined`

Whether to require the year in fuzzy dates.

Default: `false`

 SkyFuzzyDate
-------------

Type: Interface

    interface SkyFuzzyDate {
      day?: number;
      month?: number;
      year?: number;
    }

### Properties

#### `day?: number`

The day in a fuzzy date, where `1` sets the day to the first day of the specified month.

#### `month?: number`

The month in a fuzzy date, where `1` sets the month to January.

#### `year?: number`

The year in a fuzzy date.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDatepickerHarness
---------------------

Type: Class

`import { SkyDatepickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker components in tests.

### Methods

#### `clickCalendarButton(): Promise<void>`

Clicks the calendar button.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

Gets the datepicker input harness.

#### Returns

`Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

#### `getDatepickerCalendar(): Promise<SkyDatepickerCalendarHarness>`

Gets the `SkyDatepickerCalendarHarness` for the calendar picker controlled by the datepicker. Throws an error if the calendar picker is not open.

#### Returns

`Promise<SkyDatepickerCalendarHarness>`

#### `isDatepickerOpen(): Promise<boolean>`

Whether the datepicker calendar picker is open.

#### Returns

`Promise<boolean>`

#### `SkyDatepickerHarness.with(filters: SkyDatepickerFilters): HarnessPredicate<SkyDatepickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDatepickerHarness` that meets certain criteria.

These filters only work for standalone datepickers. For datepickers wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyDatepickerFilters`

#### Returns

`HarnessPredicate<SkyDatepickerHarness>`

 SkyDatepickerFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

    interface SkyDatepickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDatepickerInputHarness
--------------------------

Type: Class

`import { SkyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyFuzzyDatepickerInputHarness
-------------------------------

Type: Class

`import { SkyFuzzyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the fuzzy datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyDatepickerCalendarHarness
-----------------------------

Type: Class

`import { SkyDatepickerCalendarHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker calendar in tests.

### Methods

#### `clickDate(date: string): Promise<void>`

Clicks the specified date, month or year in the following format day format: dddd, MMMM Do YYYY month format: MMMM YYYY year format: YYYY

#### Parameters

##### `date: string`

#### Returns

`Promise<void>`

#### `clickNextButton(): Promise<void>`

Clicks the 'next' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the 'previous' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickTitleButton(): Promise<void>`

Clicks the 'title' button on the calendar header.

#### Returns

`Promise<void>`

#### `getCalendarMode(): Promise<string>`

Gets the current calendar mode.

#### Returns

`Promise<string>`

#### `getCalendarTitle(): Promise<string>`

Gets the current title.

#### Returns

`Promise<string>`

#### `getSelectedValue(): Promise<null | string>`

Gets the long date value of the currently selected calendar item.

#### Returns

`Promise<null | string>`

 SkyDatepickerCalendarHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

    interface SkyDatepickerCalendarHarnessFilters {}

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`

### Datepicker with basic setup

Edit in StackBlitz

Start dateShow help content for

Must be before your 1 year anniversary. Use the format MM/DD/YYYY.

Selected date: `"2001-10-12T04:00:00.000Z"`

Show code

Copy

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
Copy

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

Copy

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
### Datepicker with custom dates

Edit in StackBlitz

Start date

Use the format MM/DD/YYYY.

Selected date: `null`

Show code

Copy

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

Copy

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
### Fuzzy datepicker

Edit in StackBlitz

Date of birthShow help content for

Include a partial date if you don't have the exact date.

Selected date: `{"year":1955,"day":5,"month":11}`

Show code

Copy

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
Copy

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

Copy

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

# Testing

                   Skip to Main Content

 Datepicker
==========

The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use datepickers when users need to enter valid dates.

 Anatomy
--------

1

Label

2

Input field

3

Picker button

4

Default hint text

5

Picker

6

Required field marker (optional)

7

Help inline button (optional)

8

Additional hint text (optional)

9

Key date (optional)

10

Key date popover (optional)

11

Disabled date (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-anatomy.ff895423ee42690c816d1f7859e22753.png)

 Options
--------

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

*   Month, day, and year
*   Month and day
*   Month and year
*   Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

*   Constraints on the input
*   Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

You can display details about key dates in a [popover](/skyux/components/popover.md) that appears when users hover over the dates. Use plain text, and be as concise as possible. If key dates are important for multiple reasons, summarize or stack the details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-keydates.7de0268543b8f455792cb8c6ed6ded4e.png)

Do use key dates to alert users to highly relevant dates when they make selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-disabled.c72636b3f07f56b91e59833dbb7c0e27.png)

Do use disabled dates to prevent users from making invalid selections.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

Don't use `stacked` when the datepicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-options-stacked.a4f02d3b201170fa3b62dfb577b9c49a.png)

 Behavior and states
--------------------

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/datepicker/datepicker-conversion.0cdcc1ce631eafe4cb43227b13290f34.png)

 Related information
--------------------

### Components

*   [Date range picker](/skyux/components/date-range-picker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Popover](/skyux/components/popover.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/datepicker/datepicker.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 Setup
------

To enable standard form features, you must wrap the datepicker in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyDatepickerModule
--------------------

Type: Module

`import { SkyDatepickerModule } from '@skyux/datetime';`

 SkyDatepickerComponent
-----------------------

Type: Component

Selector: `sky-datepicker`

Creates the datepicker button and calendar. You must wrap this component around an input with the `skyDatepickerInput` or `skyFuzzyDatepickerInput` directive.

### Inputs

#### `pickerClass: string | undefined`

Adds a class to the datepicker.

Default: `""`

### Outputs

#### `calendarDateRangeChange: EventEmitter<SkyDatepickerCalendarChange>`

Fires when the range of displayed dates in the calendar changes. Provides the current range of displayed dates and a mutable `customDate` property consumers can use to modify individual dates on the calendar.

 SkyDatepickerInputDirective
----------------------------

Type: Directive

Selector: `[skyDatepickerInput]`

Provides date input functionality for inputs and handles date parsing, formatting and validation. It emits valid dates as `Date` objects and invalid dates as raw string values.

### Inputs

#### `skyDatepickerInput: "" | SkyDatepickerComponent | undefined`

Required

Creates the datepicker input and calendar. Place this directive on an `input` element, and wrap the input in a `sky-datepicker` component. The value that users select is driven through the `ngModel` attribute specified on the `input` element.

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in the `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `maxDate: Date | undefined`

The latest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

#### `minDate: Date | undefined`

The earliest date that is available in the calendar. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`. To avoid validation errors, the time associated with the minimum date is midnight. This is necessary because the datepicker automatically sets the time on the Date object for selected dates to midnight in the current user's time zone.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the datepicker input.

Default: `false`

#### `startAtDate: Date | undefined`

The date to open the calendar to initially. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar. `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `strict: boolean`

Whether the format of the date value must match the format from the `dateFormat` value. If this property is `true` and the datepicker input directive cannot find an exact match, then the input is marked as invalid. If this property is `false` and the datepicker input directive cannot find an exact match, then it attempts to format the string based on the [ISO 8601 standard format](https://www.iso.org/iso-8601-date-and-time-format.html).

Default: `false`

 SkyDatepickerCalendarChange
----------------------------

Type: Interface

Specifies changes in the datepicker calendar.

    interface SkyDatepickerCalendarChange {
      customDates?: Observable<SkyDatepickerCustomDate[]>;
      endDate: Date;
      startDate: Date;
    }

### Properties

#### `customDates?: Observable<SkyDatepickerCustomDate[]>`

The observable that allows the consumer to push custom dates back to the calendar when the `SkyDatepickerCalendarChange` event fires. This is useful for displaying key dates or disabled dates each time the calendar changes. If disabled dates are provided, SKY UX will prevent the user from selecting the date from the calendar. However, consumers will still need to add a custom validator to prevent users from entering disabled dates in the text input.

#### `endDate: Date`

The end date.

#### `startDate: Date`

The start date.

 SkyDatepickerConfigService
---------------------------

Type: Service

### Properties

#### `dateFormat: string | undefined`

The date format for the input.

Default: `"MM/DD/YYYY"`

#### `maxDate: Date | undefined`

The latest selectable date that is available in the calendar.

#### `minDate: Date | undefined`

The earliest selectable date that is available in the calendar.

#### `startAtDate: Date | undefined`

The date to open the calendar to initially.

Default: `the current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday.

Default: `0`

 SkyDatepickerCustomDate
------------------------

Type: Interface

The configuration for a custom date.

    interface SkyDatepickerCustomDate {
      date: Date;
      disabled?: boolean;
      keyDate?: boolean;
      keyDateText?: string[];
    }

### Properties

#### `date: Date`

The date to customize.

#### `disabled?: boolean`

Whether to disable the date.

#### `keyDate?: boolean`

Whether to display the date as a key date in the calendar.

#### `keyDateText?: string[]`

Displays a popup of the provided text when hovering over the key date in the calendar.

 SkyFuzzyDatepickerInputDirective
---------------------------------

Type: Directive

Selector: `[skyFuzzyDatepickerInput]`

### Inputs

#### `dateFormat: string | undefined`

The date format for the input. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `"MM/DD/YYYY"`

#### `disabled: boolean | undefined`

Whether to disable the datepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `futureDisabled: boolean | undefined`

Whether to prevent users from specifying dates that are in the future. Place this attribute on the `input` element.

Default: `false`

#### `maxDate: SkyFuzzyDate | undefined`

The latest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates after a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2027 }`.

#### `minDate: SkyFuzzyDate | undefined`

The earliest fuzzy date allowed. Place this attribute on the `input` element to prevent fuzzy dates before a specified date. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

#### `skyDatepickerNoValidate: boolean | undefined`

Whether to disable date validation on the fuzzy datepicker input.

Default: `false`

#### `startAtDate: SkyFuzzyDate | undefined`

The fuzzy date to open the calendar to initially. This property accepts a `SkyFuzzyDate` value that includes numeric month, day, and year values. For example: `{ month: 1, day: 1, year: 2007 }`.

Default: `The current date`

#### `startingDay: number`

The starting day of the week in the calendar, where `0` sets the starting day to Sunday. Place this attribute on the `input` element to override the default in `SkyDatepickerConfigService`.

Default: `0`

#### `yearRequired: boolean | undefined`

Whether to require the year in fuzzy dates.

Default: `false`

 SkyFuzzyDate
-------------

Type: Interface

    interface SkyFuzzyDate {
      day?: number;
      month?: number;
      year?: number;
    }

### Properties

#### `day?: number`

The day in a fuzzy date, where `1` sets the day to the first day of the specified month.

#### `month?: number`

The month in a fuzzy date, where `1` sets the month to January.

#### `year?: number`

The year in a fuzzy date.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDatepickerHarness
---------------------

Type: Class

`import { SkyDatepickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker components in tests.

### Methods

#### `clickCalendarButton(): Promise<void>`

Clicks the calendar button.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

Gets the datepicker input harness.

#### Returns

`Promise<SkyDatepickerInputHarness | SkyFuzzyDatepickerInputHarness>`

#### `getDatepickerCalendar(): Promise<SkyDatepickerCalendarHarness>`

Gets the `SkyDatepickerCalendarHarness` for the calendar picker controlled by the datepicker. Throws an error if the calendar picker is not open.

#### Returns

`Promise<SkyDatepickerCalendarHarness>`

#### `isDatepickerOpen(): Promise<boolean>`

Whether the datepicker calendar picker is open.

#### Returns

`Promise<boolean>`

#### `SkyDatepickerHarness.with(filters: SkyDatepickerFilters): HarnessPredicate<SkyDatepickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDatepickerHarness` that meets certain criteria.

These filters only work for standalone datepickers. For datepickers wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyDatepickerFilters`

#### Returns

`HarnessPredicate<SkyDatepickerHarness>`

 SkyDatepickerFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

    interface SkyDatepickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDatepickerInputHarness
--------------------------

Type: Class

`import { SkyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyFuzzyDatepickerInputHarness
-------------------------------

Type: Class

`import { SkyFuzzyDatepickerInputHarness } from '@skyux/datetime/testing';`

Harness to interact with the fuzzy datepicker input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

 SkyDatepickerCalendarHarness
-----------------------------

Type: Class

`import { SkyDatepickerCalendarHarness } from '@skyux/datetime/testing';`

Harness for interacting with datepicker calendar in tests.

### Methods

#### `clickDate(date: string): Promise<void>`

Clicks the specified date, month or year in the following format day format: dddd, MMMM Do YYYY month format: MMMM YYYY year format: YYYY

#### Parameters

##### `date: string`

#### Returns

`Promise<void>`

#### `clickNextButton(): Promise<void>`

Clicks the 'next' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickPreviousButton(): Promise<void>`

Clicks the 'previous' button on the calendar header.

#### Returns

`Promise<void>`

#### `clickTitleButton(): Promise<void>`

Clicks the 'title' button on the calendar header.

#### Returns

`Promise<void>`

#### `getCalendarMode(): Promise<string>`

Gets the current calendar mode.

#### Returns

`Promise<string>`

#### `getCalendarTitle(): Promise<string>`

Gets the current title.

#### Returns

`Promise<string>`

#### `getSelectedValue(): Promise<null | string>`

Gets the long date value of the currently selected calendar item.

#### Returns

`Promise<null | string>`

 SkyDatepickerCalendarHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

    interface SkyDatepickerCalendarHarnessFilters {}

 SkyInputBoxHarness
-------------------

Type: Class

`import { SkyInputBoxHarness } from '@skyux/forms/testing';`

Harness for interacting with an input box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCharacterCounter(): Promise<SkyCharacterCounterIndicatorHarness>`

Gets the character counter indicator for the input box or throws an error if a character limit is not specified.

#### Returns

`Promise<SkyCharacterCounterIndicatorHarness>`

#### `getCustomErrors(): Promise<SkyStatusIndicatorHarness[]>`

Gets a list of status indicator harnesses for errors not automatically handled by input box.

#### Returns

`Promise<SkyStatusIndicatorHarness[]>`

#### `getDisabled(): Promise<boolean>`

Indicates whether the input box has disabled styles applied.

#### Returns

`Promise<boolean>`

#### `getHelpPopover(): Promise<SkyPopoverHarness>`

Gets the help popover for the input box or throws an error if the help popover is not configured.

#### Returns

`Promise<SkyPopoverHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

2 Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the hint text for the input box.

#### Returns

`Promise<string>`

#### `getLabelText(): Promise<string>`

Gets the text for the input box label.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Indicates whether the input box has stacked styles applied.

#### Returns

`Promise<boolean>`

#### `hasCustomFormError(errorName: string): Promise<boolean>`

Whether the custom error is triggered.

#### Parameters

##### `errorName: string`

#### Returns

`Promise<boolean>`

#### `hasEmailError(): Promise<boolean>`

Whether the field is set to an invalid email address.

#### Returns

`Promise<boolean>`

#### `hasInvalidDateError(): Promise<boolean>`

Whether the field is set to an invalid date.

#### Returns

`Promise<boolean>`

#### `hasMaxDateError(): Promise<boolean>`

Whether the field is set to an invalid maximum date.

#### Returns

`Promise<boolean>`

#### `hasMaxLengthError(): Promise<boolean>`

Whether the field has more characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasMinDateError(): Promise<boolean>`

Whether the field is set to an invalid minimum date.

#### Returns

`Promise<boolean>`

#### `hasMinLengthError(): Promise<boolean>`

Whether the field has fewer characters than allowed.

#### Returns

`Promise<boolean>`

#### `hasPhoneFieldError(): Promise<boolean>`

Whether the field is set to an invalid phone number.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required field is empty.

#### Returns

`Promise<boolean>`

#### `hasTimeError(): Promise<boolean>`

Whether the field is set to an invalid time.

#### Returns

`Promise<boolean>`

#### `hasUrlError(): Promise<boolean>`

Whether the field is set to an invalid URL.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyInputBoxHarness.with(filters: SkyInputBoxHarnessFilters): HarnessPredicate<SkyInputBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInputBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInputBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyInputBoxHarness>`
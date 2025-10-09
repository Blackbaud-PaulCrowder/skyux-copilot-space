                    

 Timepicker
==========

The timepicker module creates a SKY UX-themed input field and picker for users to enter or select times. Timepickers must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use timepickers when users need to specify the time of day.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-usage-1.aca9e6c4a7c5d376facf20a34fc8d360.png)

Do use timepickers when users specify times in 12-hour or 24-hour formats.

Use two timepickers when users need to specify start and stop times.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-usage-2.afd8f0ce521915986503d1ad2874570c.png)

Do use two timepickers when users specify time ranges with start and stop times.

### Don't use when

Don't use timepickers when users need to specify general durations or time spans. Use [radio buttons](/skyux/components/radio.md) or HTML select fields instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-usage-3.6fdaccaeecf2f5d143c8c8dfaa72f96c.png)

Don't use timepickers when users specify hours and minutes as lengths of time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-usage-4.3553af59d99d6768e16ea0e5727e8287.png)

Do use radio buttons or HTML select fields when users specify durations or time spans.

 Anatomy
--------

1

Label

2

Picker button

3

Input field

4

Picker

5

Required field marker  (optional)

6

Help inline button  (optional)

7

Hint text  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-anatomy.bb37a758a26d5d101fee5c5837f50a8c.png)

 Options
--------

### 12-hour timepicker

Use the 12-hour option for regions and users that use 12-hour time designations. This allows users to select hours, minutes, and "AM" or "PM."

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-options-1.598d270148c625efee5b62984358ac7c.png)

### 24-hour timepicker

Use the 24-hour option for regions and users that use 24-hour time designations. This allows users to select hours and minutes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-options-2.d5a547cf88b97e1dec3335a4f025ed2c.png)

### Required field marker

When a timepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

### Help inline button

When you need to supplement a timepicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a timepicker, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a timepicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the timepicker from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the timepicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/timepicker/timepicker-options-stacked.957275d934f8d329c569f48601d1a7e6.png)

 Behavior and states
--------------------

### Keyboard entries

Users can use the keyboard to enter time values in the input field. Times automatically resolve to the correct format when the field loses focus.

 Layout
-------

Use 1/2- or 1/3-width columns for individual timepicker fields inside [modals](/skyux/components/modal.md), except when using small (300px) modals. When using two timepickers for start and stop times, use 10px of horizontal space between them.

 Related information
--------------------

### Components

*   [Datepicker](/skyux/components/datepicker.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Popover](/skyux/components/popover.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/datetime`[View in NPM](https://www.npmjs.com/package/@skyux/datetime) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/datetime/src/lib/modules/timepicker/timepicker.module.ts#L23) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/datetime`Copy None found.

 Setup
------

To enable standard form features, you must wrap the timepicker in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyTimepickerModule
--------------------

Type: Module

`import { SkyTimepickerModule } from '@skyux/datetime';`

 SkyTimepickerComponent
-----------------------

Type: Component

Selector: `sky-timepicker`

Creates a SKY UX-themed replacement for the HTML `input` element with `type="time"`. The value that users select is driven through the `ngModel` attribute specified on the `input` element. You must wrap this component around an `input` with the `skyTimepickerInput` directive.

### Outputs

#### `selectedTimeChanged: EventEmitter<SkyTimepickerTimeOutput>`

Fires when the value in the timepicker input changes.

 SkyTimepickerInputDirective
----------------------------

Type: Directive

Selector: `[skyTimepickerInput]`

### Inputs

#### `skyTimepickerInput: SkyTimepickerComponent | undefined`

Required

Creates the timepicker input field and picker. Place this attribute on an `input` element, and wrap the input in a `sky-timepicker` component. This attribute must be set to the instance of the `sky-timepicker`.

#### `disabled: boolean`

Whether to disable the timepicker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `returnFormat: string | undefined`

The custom time format. For examples, see the [moment.js](https://momentjs.com/docs/#/displaying/format/) docs.

#### `timeFormat: SkyTimepickerTimeFormatType`

The 12-hour `hh` or 24-hour `HH` time format for the input.

Default: `"hh"`

 SkyTimepickerTimeFormatType
----------------------------

Type: Type alias

    type SkyTimepickerTimeFormatType = "hh" | "HH"

 SkyTimepickerTimeOutput
------------------------

Type: Interface

    interface SkyTimepickerTimeOutput {
      customFormat: string;
      hour: number;
      iso8601: Date;
      local: string;
      meridie: string;
      minute: number;
      timezone: number;
    }

### Properties

#### `customFormat: string`

The time format string.

#### `hour: number`

The hour.

#### `iso8601: Date`

The date in [iso8601 format](https://www.iso.org/iso-8601-date-and-time-format.html).

#### `local: string`

The date in the current local time format.

#### `meridie: string`

The meridian (`AM` or `PM`).

#### `minute: number`

The minute.

#### `timezone: number`

The time zone.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTimepickerHarness
---------------------

Type: Class

`import { SkyTimepickerHarness } from '@skyux/datetime/testing';`

Harness for interacting with timepicker components in tests.

### Methods

#### `clickSelectorButton(): Promise<void>`

Clicks the selector button.

#### Returns

`Promise<void>`

#### `getControl(): Promise<SkyTimepickerInputHarness>`

Gets the timepicker input harness.

#### Returns

`Promise<SkyTimepickerInputHarness>`

#### `getTimepickerSelector(): Promise<SkyTimepickerSelectorHarness>`

Gets the `SkyTimepickerSelectorHarness` for the selector controlled by the timepicker. Throws an error if the selector is not open.

#### Returns

`Promise<SkyTimepickerSelectorHarness>`

#### `isTimepickerOpen(): Promise<boolean>`

Whether the timepicker calendar picker is open.

#### Returns

`Promise<boolean>`

#### `SkyTimepickerHarness.with(filters: SkyTimepickerFilters): HarnessPredicate<SkyTimepickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTimepickerHarness` that meets certain criteria.

These filters only work for standalone timepickers. For timepickers wrapped inside `sky-input-box`, place filters on the input box instead and query the timepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyTimepickerFilters`

#### Returns

`HarnessPredicate<SkyTimepickerHarness>`

 SkyTimepickerFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTimepickerHarness` instances.

    interface SkyTimepickerFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTimepickerSelectorHarness
-----------------------------

Type: Class

`import { SkyTimepickerSelectorHarness } from '@skyux/datetime/testing';`

Harness for interacting with a timepicker selector in tests.

### Methods

#### `clickHour(value: string): Promise<void>`

Clicks the specified hour button, or throws an error if it does not exist.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `clickMeridie(value: string): Promise<void>`

Clicks the specified meridie button, or throws an error if it does not exist.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `clickMinute(value: string): Promise<void>`

Clicks the specified minute button, or throws an error if it does not exist.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `getSelectedValue(): Promise<undefined | string>`

Gets the time value of the currently selected items.

#### Returns

`Promise<undefined | string>`

#### `getSelectorMode(): Promise<string>`

Gets the current calendar mode.

#### Returns

`Promise<string>`
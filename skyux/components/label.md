                 

 Label
=====

Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.

 Usage
------

### Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

 Options
--------

### Label type

Label type

When to use

Example

`danger`

Use the danger label to indicate error states on records.

Error: Expired

`warning`

Use the warning label to indicate records in states that could have minor consequences if not acted on or avoided.

Warning: Overdue

`success`

Use the success label to indicate records in a positive of successful state.

Success: Completed

`info`

Use the info alert to call attention to a state or property on a record that needs to be elevated in the information hierarchy but does not require user action.

Attention: Board member

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Label type

Description type

When to use

Example

Danger

`error`

Use when the label calls attention to an error state.  
Includes the text "Error: ".

Error: No longer validError: Declined

`important-warning`

Use when the label calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning: Expired

`danger`

Use when the label calls attention to information that could users help someone avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger: Do not print

Warning

`warning`

Use when the label calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning: Overdue

`caution`

Use when the label calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Caution: Hold application

Success

`success`

Use when the label calls attention to information that communicates a successful result or positive state. state.  
Includes the text "Success: ".

Success: Application accepted

Info

`attention`

Use when the label calls attention to information that should be elevated in the information hierarchy but does not require user action.  
Includes the text "Attention: ".

Attention: Top earner

Any

`custom`

Set your own label when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

 Layout
-------

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use [status indicators](/skyux/components/status-indicator.md) instead.

 Related information
--------------------

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/label/label.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyLabelModule
---------------

Type: Module

`import { SkyLabelModule } from '@skyux/indicators';`

 SkyLabelComponent
------------------

Type: Component

Selector: `sky-label`

### Inputs

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the indicator icon. This property is optional but will be required in future versions of SKY UX.

#### `labelType: SkyLabelType | undefined`

The type of label to display.

Default: `'info'`

 SkyLabelType
-------------

Type: Type alias

    type SkyLabelType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLabelHarness
----------------

Type: Class

`import { SkyLabelHarness } from '@skyux/indicators/testing';`

Harness for interacting with a label component in tests.

### Methods

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getLabelText(): Promise<string>`

Gets the text of the label component.

#### Returns

`Promise<string>`

#### `getLabelType(): Promise<SkyLabelType>`

Gets the `labelType` of the label component.

#### Returns

`Promise<SkyLabelType>`

#### `SkyLabelHarness.with(filters: SkyLabelHarnessFilters): HarnessPredicate<SkyLabelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLabelHarnessFilters`

#### Returns

`HarnessPredicate<SkyLabelHarness>`

 SkyLabelHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

    interface SkyLabelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
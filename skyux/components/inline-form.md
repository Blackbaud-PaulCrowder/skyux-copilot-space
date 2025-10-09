                  

 Inline form
===========

Inline forms render in context in the current view instead of in a separate modal. It is most commonly used in [grids](/skyux/components/grid.md) and [repeaters](/skyux/components/repeater.md).

 Usage
------

### Use when

Use inline forms when the add or edit form is simple in terms of the number of fields and the complexity of the input controls.

Use inline forms when the surrounding content will not distract users from the add or edit task.

Use inline forms when users are highly likely to add multiple records in succession.

Use inline forms to add or edit a subsection within a larger modal form.

Use inline forms when users can abandon the task while the add or edit form is open.

For more details on adding and editing data, see [managing data guidelines](/skyux/design/guidelines/managing-records.md)

### Don't use when

Don't use inline forms when the add or edit form requires a large amount of page morphing or users must scroll to complete the form.

Don't use inline forms within a paginated or infinite scroll list of items.

Don't use inline forms when users must finish the add or edit form before doing anything else.

 Anatomy
--------

1

Edit button

2

Inline form

3

Form field

4

Form action buttons

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/inline-form/inline-form-anatomy-modern.e1eeb8de1f898f8e59d3dc92b8af8cd2.png)

 Behavior and states
--------------------

### Edit form

When users click the Edit button, the inline form replaces the view-only content.

 Content
--------

### Primary buttons

The primary action on the inline form should be Save or Done.

Use Save if the inline form saves data to the database immediately.

Use Done if the inline form does not save data to the database immediately because it is part of a larger form.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Manage data](/skyux/design/guidelines/managing-records.md)

 Installation
-------------

NPM package

`@skyux/inline-form`[View in NPM](https://www.npmjs.com/package/@skyux/inline-form) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/inline-form/src/lib/modules/inline-form/inline-form.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/inline-form`Copy None found.

 SkyInlineFormModule
--------------------

Type: Module

`import { SkyInlineFormModule } from '@skyux/inline-form';`

 SkyInlineFormComponent
-----------------------

Type: Component

Selector: `sky-inline-form`

Renders form content in the current view instead of a separate modal.

### Inputs

#### `config: SkyInlineFormConfig | undefined`

Required

Configuration options for the buttons to display with the inline form.

#### `template: TemplateRef<unknown> | undefined`

Required

The template to instantiate the inline form.

#### `showForm: boolean | undefined`

Whether to display the inline form. Users can toggle between displaying and hiding the inline form.

Default: `false`

### Outputs

#### `close: EventEmitter<SkyInlineFormCloseArgs>`

Fires when users close the inline form.

 SkyInlineFormConfig
--------------------

Type: Interface

Specifies configuration options for the buttons to display with the inline form.

    interface SkyInlineFormConfig {
      buttonLayout: SkyInlineFormButtonLayout;
      buttons?: SkyInlineFormButtonConfig[];
    }

### Properties

#### `buttonLayout: SkyInlineFormButtonLayout`

The buttons to display with the inline form. The valid options are `Custom` for custom buttons, `DoneCancel` for Done and Cancel buttons, `DoneDeleteCancel` for Done, Delete, and Cancel buttons, `SaveCancel` for Save and Cancel buttons, and `SaveDeleteCancel` for Save, Delete, and Cancel buttons.

#### `buttons?: SkyInlineFormButtonConfig[]`

Configuration options for the inline form's buttons when `buttonLayout` is set to `Custom`.

 SkyInlineFormButtonConfig
--------------------------

Type: Interface

Specifies configuration options for the inline form's buttons when `buttonLayout` is set to `Custom`.

    interface SkyInlineFormButtonConfig {
      action: string;
      disabled?: boolean;
      styleType?: string;
      text: string;
    }

### Properties

#### `action: string`

The `string` value to return when users click a custom button. This correlates to the `reason` in `SkyInlineFormCloseArgs`. The standard values are `cancel`, `delete`, `done`, and `save`, but other custom values are also allowed.

#### `disabled?: boolean`

Whether to disable the button.

#### `styleType?: string`

The background color and style for the button. The valid options are `default`, `link`, and `primary`. These values set the background color and style from the [secondary, link, and primary button classes](/skyux/components/button.md) respectively.

#### `text: string`

The label for the button.

 SkyInlineFormButtonLayout
--------------------------

Type: Enumeration

    enum SkyInlineFormButtonLayout {
      Custom = 0,
      DoneCancel = 1,
      DoneDeleteCancel = 2,
      SaveCancel = 3,
      SaveDeleteCancel = 4,
    }

### Properties

#### `SkyInlineFormButtonLayout.Custom`

Displays custom buttons.

#### `SkyInlineFormButtonLayout.DoneCancel`

Displays Done and Cancel buttons.

#### `SkyInlineFormButtonLayout.DoneDeleteCancel`

Displays Done, Delete, and Cancel buttons.

#### `SkyInlineFormButtonLayout.SaveCancel`

Displays Save and Cancel buttons.

#### `SkyInlineFormButtonLayout.SaveDeleteCancel`

Displays Save, Delete, and Cancel buttons.

 SkyInlineFormCloseArgs
-----------------------

Type: Interface

    interface SkyInlineFormCloseArgs {
      reason: string;
    }

### Properties

#### `reason: string`

Returns a `string` value to explain why users clicked a custom button and initiated a `close` event. This correlates to either the `action` in `SkyInlineFormButtonConfig` for custom buttons or the standard value of `cancel`, `delete`, `done`, or `save` for predefined buttons.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInlineFormHarness
---------------------

Type: Class

`import { SkyInlineFormHarness } from '@skyux/inline-form/testing';`

Harness to interact with inline form components in tests.

### Methods

#### `getButton(filters: SkyInlineFormButtonHarnessFilters): Promise<SkyInlineFormButtonHarness>`

Gets a specific inline form button based on the filter criteria.

#### Parameters

##### `filters: SkyInlineFormButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyInlineFormButtonHarness>`

#### `getButtons(filters?: SkyInlineFormButtonHarnessFilters): Promise<SkyInlineFormButtonHarness[]>`

Gets an array of inline form buttons based on the filter criteria. If no filter is provided, returns all inline form buttons.

#### Parameters

##### `filters?: SkyInlineFormButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyInlineFormButtonHarness[]>`

#### `getTemplate(): Promise<SkyInlineFormTemplateHarness>`

Returns a harness wrapping the inline form's template when expanded.

#### Returns

`Promise<SkyInlineFormTemplateHarness>`

#### `isFormExpanded(): Promise<boolean>`

Whether the inline form is shown.

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

#### `SkyInlineFormHarness.with(filters: SkyInlineFormHarnessFilters): HarnessPredicate<SkyInlineFormHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInlineFormHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInlineFormHarnessFilters`

#### Returns

`HarnessPredicate<SkyInlineFormHarness>`

 SkyInlineFormHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInlineFormHarness` instances.

    interface SkyInlineFormHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyInlineFormButtonHarness
---------------------------

Type: Class

`import { SkyInlineFormButtonHarness } from '@skyux/inline-form/testing';`

Harness to interact with inline form button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getStyleType(): Promise<"link" | "primary" | "default">`

Gets the button style type.

#### Returns

`Promise<"link" | "primary" | "default">`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyInlineFormButtonHarness.with(filters: SkyInlineFormButtonHarnessFilters): HarnessPredicate<SkyInlineFormButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInlineFormButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInlineFormButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyInlineFormButtonHarness>`

 SkyInlineFormButtonHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInlineFormButtonHarness` instances.

    interface SkyInlineFormButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      styleType?: "link" | "primary" | "default";
      text?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `styleType?: "link" | "primary" | "default"`

Finds the button whose style type matches this value.

#### `text?: string`

Finds the button whose text matches this value.

 SkyInlineFormTemplateHarness
-----------------------------

Type: Class

`import { SkyInlineFormTemplateHarness } from '@skyux/inline-form/testing';`

Harness to interact with inline form template components in tests.

### Methods

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
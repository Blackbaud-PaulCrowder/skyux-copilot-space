# Design

                  Skip to Main Content

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

# Development

                  Skip to Main Content

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

# Examples

                    Skip to Main Content

 Inline form
===========

Inline forms render in context in the current view instead of in a separate modal. It is most commonly used in [grids](/skyux/components/grid.md) and [repeaters](/skyux/components/repeater.md).Usage
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

### Inline form with basic setup

Edit in StackBlitz

First name:

Jane

Show code

Copy

    <sky-inline-form
      data-sky-id="first-name"
      [config]="inlineFormConfig"
      [showForm]="showForm"
      [template]="inlineFormTemplate"
      (close)="onInlineFormClose($event)"
    >
      <table>
        <tr>
          <th>First name:</th>
          <td>
            {{ firstName }}
          </td>
          <td>
            <button
              aria-label="Edit"
              class="sky-btn sky-btn-icon-borderless"
              type="button"
              (click)="onInlineFormOpen()"
            >
              <sky-icon iconName="edit" />
            </button>
          </td>
        </tr>
      </table>
    </sky-inline-form>
    
    <ng-template #inlineFormTemplate>
      <form [formGroup]="formGroup">
        <sky-input-box labelText="First name">
          <input formControlName="firstName" type="text" />
        </sky-input-box>
      </form>
    </ng-template>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInlineFormHarness } from '@skyux/inline-form/testing';
    
    import { InlineFormBasicExampleComponent } from './example.component';
    
    describe('Inline form basic demo', () => {
      async function setupTest(options: { dataSkyId?: string }): Promise<{
        harness: SkyInlineFormHarness;
        fixture: ComponentFixture<InlineFormBasicExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [InlineFormBasicExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(InlineFormBasicExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const harness = await loader.getHarness(
          SkyInlineFormHarness.with({ dataSkyId: options.dataSkyId }),
        );
        return { harness, fixture };
      }
    
      it('should change the first name', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: 'first-name',
        });
    
        // You can query components inside the inline form when closed.
        const editButton = await harness.querySelector('button.sky-btn');
        await editButton.click();
    
        await expectAsync(harness.isFormExpanded()).toBeResolvedTo(true);
    
        // You can query inline form buttons when the form is open.
        const buttons = await harness.getButtons();
        expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
          'Jane',
        );
        await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
        await expectAsync(buttons[1].getStyleType()).toBeResolvedTo('link');
    
        // You can query components from the inline form template when the form is open.
        const inputHarness = await (
          await harness.getTemplate()
        ).querySelector('input');
    
        await inputHarness.sendKeys('t');
        await inputHarness.blur();
        fixture.detectChanges();
    
        await buttons[0].click();
        await expectAsync(harness.isFormExpanded()).toBeResolvedTo(false);
    
        await editButton.click();
        fixture.detectChanges();
        expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
          'Janet',
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
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    import {
      SkyInlineFormButtonLayout,
      SkyInlineFormCloseArgs,
      SkyInlineFormConfig,
      SkyInlineFormModule,
    } from '@skyux/inline-form';
    
    interface DemoForm {
      firstName: FormControl<string>;
    }
    
    /**
     * @title Inline form with basic setup
     */
    @Component({
      selector: 'app-inline-form-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyIconModule,
        SkyInlineFormModule,
        SkyInputBoxModule,
      ],
    })
    export class InlineFormBasicExampleComponent {
      protected firstName = 'Jane';
      public formGroup: FormGroup<DemoForm>;
    
      protected inlineFormConfig: SkyInlineFormConfig = {
        buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
      };
    
      protected showForm = false;
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          firstName: new FormControl<string>('', { nonNullable: true }),
        });
      }
    
      protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
        if (args.reason === 'save') {
          this.firstName = this.formGroup.value.firstName ?? '';
        }
    
        this.showForm = false;
        this.formGroup.patchValue({
          firstName: undefined,
        });
      }
    
      protected onInlineFormOpen(): void {
        this.showForm = true;
        this.formGroup.patchValue({
          firstName: this.firstName,
        });
      }
    }
### Inline form with custom buttons

Edit in StackBlitz

First name:

Jane

Show code

Copy

    <sky-inline-form
      data-sky-id="first-name"
      [config]="inlineFormConfig"
      [showForm]="showForm"
      [template]="inlineFormTemplate"
      (close)="onInlineFormClose($event)"
    >
      <table>
        <tr>
          <th>First name:</th>
          <td>
            {{ firstName }}
          </td>
          <td>
            <button
              aria-label="Edit"
              class="sky-btn sky-btn-icon-borderless"
              type="button"
              (click)="onInlineFormOpen()"
            >
              <sky-icon iconName="edit" />
            </button>
          </td>
        </tr>
      </table>
    </sky-inline-form>
    
    <ng-template #inlineFormTemplate>
      <form [formGroup]="formGroup">
        <sky-input-box labelText="First name">
          <input formControlName="firstName" required type="text" />
        </sky-input-box>
      </form>
    </ng-template>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInlineFormHarness } from '@skyux/inline-form/testing';
    
    import { InlineFormCustomButtonsExampleComponent } from './example.component';
    
    describe('Inline form custom button demo', () => {
      async function setupTest(options: { dataSkyId?: string }): Promise<{
        harness: SkyInlineFormHarness;
        fixture: ComponentFixture<InlineFormCustomButtonsExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [InlineFormCustomButtonsExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          InlineFormCustomButtonsExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const harness = await loader.getHarness(
          SkyInlineFormHarness.with({ dataSkyId: options.dataSkyId }),
        );
        return { harness, fixture };
      }
    
      it('should change the first name', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: 'first-name',
        });
    
        // You can query components inside the inline form when closed.
        const editButton = await harness.querySelector('button.sky-btn');
        await editButton.click();
    
        await expectAsync(harness.isFormExpanded()).toBeResolvedTo(true);
    
        // You can query inline form buttons when the form is open.
        const buttons = await harness.getButtons();
        expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
          'Jane',
        );
        await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
        await expectAsync(buttons[1].getStyleType()).toBeResolvedTo('default');
    
        // You can query components from the inline form template when the form is open.
        const inputHarness = await (
          await harness.getTemplate()
        ).querySelector('input');
    
        await inputHarness.sendKeys('t');
        await inputHarness.blur();
        fixture.detectChanges();
    
        await buttons[0].click();
        await expectAsync(harness.isFormExpanded()).toBeResolvedTo(false);
    
        await editButton.click();
        fixture.detectChanges();
        expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
          'Janet',
        );
      });
    });

Copy

    import { Component, OnInit, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    import {
      SkyInlineFormButtonLayout,
      SkyInlineFormCloseArgs,
      SkyInlineFormConfig,
      SkyInlineFormModule,
    } from '@skyux/inline-form';
    
    interface DemoForm {
      firstName: FormControl<string>;
    }
    
    /**
     * @title Inline form with custom buttons
     */
    @Component({
      selector: 'app-inline-form-custom-buttons-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyIconModule,
        SkyInlineFormModule,
        SkyInputBoxModule,
      ],
    })
    export class InlineFormCustomButtonsExampleComponent implements OnInit {
      protected firstName = 'Jane';
      public formGroup: FormGroup<DemoForm>;
    
      protected inlineFormConfig: SkyInlineFormConfig = {
        buttonLayout: SkyInlineFormButtonLayout.Custom,
        buttons: [
          {
            action: 'save',
            text: 'Save',
            styleType: 'primary',
          },
          {
            action: 'clear',
            text: 'Clear',
            styleType: 'default',
          },
          {
            action: 'reset',
            text: 'Reset',
            styleType: 'default',
          },
          {
            action: 'cancel',
            text: 'Cancel',
            styleType: 'link',
          },
        ],
      };
    
      protected showForm = false;
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          firstName: new FormControl<string>('', { nonNullable: true }),
        });
      }
    
      public ngOnInit(): void {
        this.formGroup.valueChanges.subscribe(() => {
          if (
            this.inlineFormConfig.buttons &&
            this.inlineFormConfig.buttons[0].disabled !== this.formGroup.invalid
          ) {
            this.inlineFormConfig.buttons[0].disabled = this.formGroup.invalid;
            this.inlineFormConfig = { ...{}, ...this.inlineFormConfig };
          }
        });
      }
    
      protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
        switch (args.reason) {
          case 'save':
            this.firstName = this.formGroup.value.firstName ?? '';
            this.showForm = false;
            break;
    
          case 'clear':
            this.formGroup.patchValue({ firstName: '' });
            break;
    
          case 'reset':
            this.formGroup.setValue({ firstName: this.firstName });
            break;
    
          default:
            this.showForm = false;
            break;
        }
      }
    
      protected onInlineFormOpen(): void {
        this.showForm = true;
        this.formGroup.patchValue({
          firstName: this.firstName,
        });
      }
    }
### Inline form with repeater

Edit in StackBlitz

2019 Spring Gala

Gala for friends and family

2019 Special Winter Event

A special event

2019 Donor Appreciation Event

Event for all donors and families

2020 Spring Gala

Gala for friends and family

Show code

Copy

    <sky-repeater>
      @for (item of items; track item) {
        <sky-repeater-item
          [inlineFormConfig]="inlineFormConfig"
          [inlineFormTemplate]="inlineFormTemplate"
          [showInlineForm]="activeInlineFormId === item.id"
          (inlineFormClose)="onInlineFormClose($event)"
        >
          <sky-repeater-item-title>
            <div class="sky-font-emphasized">
              {{ item.title }}
            </div>
          </sky-repeater-item-title>
          <sky-repeater-item-context-menu>
            <button
              aria-label="Edit"
              class="sky-btn sky-btn-icon-borderless"
              type="button"
              (click)="showInlineForm(item)"
            >
              <sky-icon iconName="edit" />
            </button>
          </sky-repeater-item-context-menu>
    
          <sky-repeater-item-content>
            {{ item.note }}
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
    
    <ng-template #inlineFormTemplate>
      <form novalidate [formGroup]="formGroup">
        <sky-input-box labelTex="Title" stacked="true">
          <input formControlName="title" type="text" />
        </sky-input-box>
        <sky-input-box labelText="Note">
          <input formControlName="note" type="text" />
        </sky-input-box>
      </form>
    </ng-template>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInlineFormHarness } from '@skyux/inline-form/testing';
    import { SkyRepeaterHarness } from '@skyux/lists/testing';
    
    import { InlineFormRepeatersExampleComponent } from './example.component';
    
    describe('Inline form with repeater demo', () => {
      async function setupTest(options: { itemId: number }): Promise<{
        repeaterHarness: SkyRepeaterHarness;
        inlineFormHarness: SkyInlineFormHarness;
        fixture: ComponentFixture<InlineFormRepeatersExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [InlineFormRepeatersExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          InlineFormRepeatersExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const repeaterHarness = await loader.getHarness(SkyRepeaterHarness);
        const item = await repeaterHarness.getRepeaterItems();
        const inlineFormHarness =
          await item[options.itemId].queryHarness(SkyInlineFormHarness);
    
        return { repeaterHarness, inlineFormHarness, fixture };
      }
    
      it('should set up the spring gala item inline form', async () => {
        const { inlineFormHarness } = await setupTest({
          itemId: 1,
        });
        const editButton = await inlineFormHarness?.querySelector('button.sky-btn');
        await editButton?.click();
        await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(true);
    
        // You can query inline form buttons when the form is open.
        const buttons = await inlineFormHarness?.getButtons();
        await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
        const cancelButton = buttons[1];
    
        await cancelButton.click();
        await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(
          false,
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
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    import {
      SkyInlineFormButtonLayout,
      SkyInlineFormCloseArgs,
      SkyInlineFormConfig,
    } from '@skyux/inline-form';
    import { SkyRepeaterModule } from '@skyux/lists';
    
    interface DemoForm {
      id: FormControl<string>;
      note: FormControl<string>;
      title: FormControl<string>;
    }
    
    interface Item {
      id: string;
      title: string | undefined;
      note: string | undefined;
    }
    
    /**
     * @title Inline form with repeater
     */
    @Component({
      selector: 'app-inline-form-repeaters-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyIconModule,
        SkyInputBoxModule,
        SkyRepeaterModule,
      ],
    })
    export class InlineFormRepeatersExampleComponent {
      protected activeInlineFormId: string | undefined;
      protected formGroup: FormGroup<DemoForm>;
    
      protected inlineFormConfig: SkyInlineFormConfig = {
        buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
      };
    
      protected items: Item[] = [
        {
          id: '1',
          title: '2019 Spring Gala',
          note: 'Gala for friends and family',
        },
        {
          id: '2',
          title: '2019 Special Winter Event',
          note: 'A special event',
        },
        {
          id: '3',
          title: '2019 Donor Appreciation Event',
          note: 'Event for all donors and families',
        },
        {
          id: '4',
          title: '2020 Spring Gala',
          note: 'Gala for friends and family',
        },
      ];
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          id: new FormControl('', { nonNullable: true }),
          title: new FormControl('', { nonNullable: true }),
          note: new FormControl('', { nonNullable: true }),
        });
      }
    
      protected showInlineForm(item: Item): void {
        this.activeInlineFormId = item.id;
        this.formGroup.patchValue({
          note: item.note,
          title: item.title,
        });
      }
    
      protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
        if (args.reason === 'save') {
          const found = this.items.find(
            (item) => item.id === this.activeInlineFormId,
          );
    
          if (found) {
            found.note = this.formGroup.value.note;
            found.title = this.formGroup.value.title;
          }
        }
    
        this.formGroup.patchValue({
          note: undefined,
          title: undefined,
        });
    
        // Close the active form.
        this.activeInlineFormId = undefined;
      }
    }

# Testing

                  Skip to Main Content

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
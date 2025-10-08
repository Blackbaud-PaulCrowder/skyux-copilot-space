# Design

                  Skip to Main Content

 Summary action bar
==================

The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.

 Usage
------

### Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-multi-list.eca66302425efc4ede29bb33f7a6552f.png)

Do use summary action bars for actions on a list of items.

Use summary action bars for actions that are taken on the selected record in [split views](/skyux/components/split-view.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-split-view.a4756d40b3b5ab883c7e80f2741d0756.png)

Do use summary action bars for actions in split views.

Use summary action bars when you need to show summary information related to the forms in [modals](/skyux/components/modal.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-modal.f2d6e98c71020b71fc5f203960636524.png)

Do use summary action bars for summary information in modals.

### Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/dont-use-overload.f9d736e6da09879cf3a6bd8b389c8282.png)

Don't use summary action bars for large amounts of content.

 Anatomy
--------

1

Actions

2

Summary information (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/anatomy.de4cf54c932033fda9a75bd01e8911a7.png)

 Behavior and states
--------------------

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/behavior-collapse.1664d7953414f7a8fbcc8df83bf590c2.png)

 Options
--------

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-wrap-summary.f015f5b8d79901092c13f702fff80b7b.png)

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-conditional-action.419a415cbcc6ce907504e7d57837bc1f.png)

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-context-menu.c8ab20b6d2fa3a6d7fe6861545df1950.png)

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-summary.a9ad346cca9114628894ee53578affa4.png)

 Related information
--------------------

### Components

*   [Data entry grid](/skyux/components/data-entry-grid.md)
*   [Data grid](/skyux/components/data-grid.md)
*   [Modal](/skyux/components/modal.md)
*   [Repeater](/skyux/components/repeater.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/action-bars`[View in NPM](https://www.npmjs.com/package/@skyux/action-bars) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/action-bars/src/lib/modules/summary-action-bar/summary-action-bar.module.ts#L31) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/action-bars`Copy None found.

 SkySummaryActionBarModule
--------------------------

Type: Module

`import { SkySummaryActionBarModule } from '@skyux/action-bars';`

 SkySummaryActionBarComponent
-----------------------------

Type: Component

Selector: `sky-summary-action-bar`

Contains the `sky-summary-action-bar-actions` and `sky-summary-action-bar-summary` components.

### Inputs

#### `formErrors: SkySummaryActionBarError[] | undefined`

 SkySummaryActionBarActionsComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-actions`

Contains actions for the `sky-summary-action-bar` component.

 SkySummaryActionBarPrimaryActionComponent
------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-primary-action`

Displays a primary button.

### Inputs

#### `disabled: boolean`

Whether to disable the primary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the primary action.

 SkySummaryActionBarSecondaryActionsComponent
---------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-actions`

Contains secondary actions specified with `sky-summary-action-bar-secondary-action` components.

 SkySummaryActionBarSecondaryActionComponent
--------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-action`

Specifies secondary actions.

### Inputs

#### `disabled: boolean`

Whether to disable a secondary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select a secondary action.

 SkySummaryActionBarCancelComponent
-----------------------------------

Type: Component

Selector: `sky-summary-action-bar-cancel`

Displays a cancel action.

### Inputs

#### `disabled: boolean`

Whether to disable the cancel action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the cancel action.

 SkySummaryActionBarSummaryComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-summary`

Specifies the summary information to display.

 SkySummaryActionBarError
-------------------------

Type: Interface

Contains an object with properties for displaying form-level errors in a summary action bar.

    interface SkySummaryActionBarError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySummaryActionBarHarness
---------------------------

Type: Class

`import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar component in tests.

### Methods

#### `collapseSummary(): Promise<void>`

In a smaller viewport, collapses the summary.

#### Returns

`Promise<void>`

#### `expandSummary(): Promise<void>`

In a smaller viewport, expands the summary.

#### Returns

`Promise<void>`

#### `getCancel(filters?: SkySummaryActionBarCancelHarnessFilters): Promise<SkySummaryActionBarCancelHarness>`

Gets the harness for the cancel action.

#### Parameters

##### `filters?: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarCancelHarness>`

#### `getErrors(): Promise<SkySummaryActionBarError[]>`

Gets the active errors.

#### Returns

`Promise<SkySummaryActionBarError[]>`

#### `getPrimaryAction(filters?: SkySummaryActionBarPrimaryActionHarnessFilters): Promise<SkySummaryActionBarPrimaryActionHarness>`

Gets the harness for the primary action.

#### Parameters

##### `filters?: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarPrimaryActionHarness>`

#### `getSecondaryActions(filters?: SkySummaryActionBarSecondaryActionsHarnessFilters): Promise<SkySummaryActionBarSecondaryActionsHarness>`

Gets the harness for the secondary actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSecondaryActionsHarness>`

#### `getSummary(filters?: SkySummaryActionBarSummaryHarnessFilters): Promise<SkySummaryActionBarSummaryHarness>`

Gets the harness for the summary information.

#### Parameters

##### `filters?: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSummaryHarness>`

#### `hasError(error: SkySummaryActionBarError): Promise<boolean>`

Whether the error has fired.

#### Parameters

##### `error: SkySummaryActionBarError`

#### Returns

`Promise<boolean>`

#### `isSummaryVisible(): Promise<boolean>`

Whether the summary information is visible.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarHarness.with(filters: SkySummaryActionBarHarnessFilters): HarnessPredicate<SkySummaryActionBarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarHarness>`

 SkySummaryActionBarHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-harness.md) instances.

    interface SkySummaryActionBarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarPrimaryActionHarness
----------------------------------------

Type: Class

`import { SkySummaryActionBarPrimaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar primary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarPrimaryActionHarness.with(filters: SkySummaryActionBarPrimaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarPrimaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

 SkySummaryActionBarPrimaryActionHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarPrimaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-primary-action-harness.md) instances.

    interface SkySummaryActionBarPrimaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionsHarness
-------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionsHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary actions component in tests. Use this harness to query harnesses for an individual action's [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-secondary-action-harness.md).

### Methods

#### `getAction(filters: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness>`

Gets a specific action based on the filter criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness>`

#### `getActions(filters?: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness[]>`

Gets an array of actions based on the filter criteria. If no filter is provided, returns all actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness[]>`

#### `SkySummaryActionBarSecondaryActionsHarness.with(filters: SkySummaryActionBarSecondaryActionsHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionsHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

 SkySummaryActionBarSecondaryActionsHarnessFilters
--------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionsHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-secondary-actions-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionsHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionHarness
------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarSecondaryActionHarness.with(filters: SkySummaryActionBarSecondaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

 SkySummaryActionBarSecondaryActionHarnessFilters
-------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-secondary-action-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSummaryHarness
----------------------------------

Type: Class

`import { SkySummaryActionBarSummaryHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar summary component in tests. Use this harness to query components inside the `sky-summary-action-bar-summary` component.

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

#### `SkySummaryActionBarSummaryHarness.with(filters: SkySummaryActionBarSummaryHarnessFilters): HarnessPredicate<SkySummaryActionBarSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSummaryHarness>`

 SkySummaryActionBarSummaryHarnessFilters
-----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSummaryHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-summary-harness.md) instances.

    interface SkySummaryActionBarSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarCancelHarness
---------------------------------

Type: Class

`import { SkySummaryActionBarCancelHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar cancel component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarCancelHarness.with(filters: SkySummaryActionBarCancelHarnessFilters): HarnessPredicate<SkySummaryActionBarCancelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarCancelHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarCancelHarness>`

 SkySummaryActionBarCancelHarnessFilters
----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarCancelHarness](/skyux/components/summary-action-bar?docs-active-tab=design#class_sky-summary-action-bar-cancel-harness.md) instances.

    interface SkySummaryActionBarCancelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Summary action bar
==================

The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.

 Usage
------

### Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-multi-list.eca66302425efc4ede29bb33f7a6552f.png)

Do use summary action bars for actions on a list of items.

Use summary action bars for actions that are taken on the selected record in [split views](/skyux/components/split-view.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-split-view.a4756d40b3b5ab883c7e80f2741d0756.png)

Do use summary action bars for actions in split views.

Use summary action bars when you need to show summary information related to the forms in [modals](/skyux/components/modal.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-modal.f2d6e98c71020b71fc5f203960636524.png)

Do use summary action bars for summary information in modals.

### Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/dont-use-overload.f9d736e6da09879cf3a6bd8b389c8282.png)

Don't use summary action bars for large amounts of content.

 Anatomy
--------

1

Actions

2

Summary information (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/anatomy.de4cf54c932033fda9a75bd01e8911a7.png)

 Behavior and states
--------------------

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/behavior-collapse.1664d7953414f7a8fbcc8df83bf590c2.png)

 Options
--------

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-wrap-summary.f015f5b8d79901092c13f702fff80b7b.png)

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-conditional-action.419a415cbcc6ce907504e7d57837bc1f.png)

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-context-menu.c8ab20b6d2fa3a6d7fe6861545df1950.png)

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-summary.a9ad346cca9114628894ee53578affa4.png)

 Related information
--------------------

### Components

*   [Data entry grid](/skyux/components/data-entry-grid.md)
*   [Data grid](/skyux/components/data-grid.md)
*   [Modal](/skyux/components/modal.md)
*   [Repeater](/skyux/components/repeater.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/action-bars`[View in NPM](https://www.npmjs.com/package/@skyux/action-bars) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/action-bars/src/lib/modules/summary-action-bar/summary-action-bar.module.ts#L31) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/action-bars`Copy None found.

 SkySummaryActionBarModule
--------------------------

Type: Module

`import { SkySummaryActionBarModule } from '@skyux/action-bars';`

 SkySummaryActionBarComponent
-----------------------------

Type: Component

Selector: `sky-summary-action-bar`

Contains the `sky-summary-action-bar-actions` and `sky-summary-action-bar-summary` components.

### Inputs

#### `formErrors: SkySummaryActionBarError[] | undefined`

 SkySummaryActionBarActionsComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-actions`

Contains actions for the `sky-summary-action-bar` component.

 SkySummaryActionBarPrimaryActionComponent
------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-primary-action`

Displays a primary button.

### Inputs

#### `disabled: boolean`

Whether to disable the primary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the primary action.

 SkySummaryActionBarSecondaryActionsComponent
---------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-actions`

Contains secondary actions specified with `sky-summary-action-bar-secondary-action` components.

 SkySummaryActionBarSecondaryActionComponent
--------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-action`

Specifies secondary actions.

### Inputs

#### `disabled: boolean`

Whether to disable a secondary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select a secondary action.

 SkySummaryActionBarCancelComponent
-----------------------------------

Type: Component

Selector: `sky-summary-action-bar-cancel`

Displays a cancel action.

### Inputs

#### `disabled: boolean`

Whether to disable the cancel action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the cancel action.

 SkySummaryActionBarSummaryComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-summary`

Specifies the summary information to display.

 SkySummaryActionBarError
-------------------------

Type: Interface

Contains an object with properties for displaying form-level errors in a summary action bar.

    interface SkySummaryActionBarError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySummaryActionBarHarness
---------------------------

Type: Class

`import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar component in tests.

### Methods

#### `collapseSummary(): Promise<void>`

In a smaller viewport, collapses the summary.

#### Returns

`Promise<void>`

#### `expandSummary(): Promise<void>`

In a smaller viewport, expands the summary.

#### Returns

`Promise<void>`

#### `getCancel(filters?: SkySummaryActionBarCancelHarnessFilters): Promise<SkySummaryActionBarCancelHarness>`

Gets the harness for the cancel action.

#### Parameters

##### `filters?: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarCancelHarness>`

#### `getErrors(): Promise<SkySummaryActionBarError[]>`

Gets the active errors.

#### Returns

`Promise<SkySummaryActionBarError[]>`

#### `getPrimaryAction(filters?: SkySummaryActionBarPrimaryActionHarnessFilters): Promise<SkySummaryActionBarPrimaryActionHarness>`

Gets the harness for the primary action.

#### Parameters

##### `filters?: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarPrimaryActionHarness>`

#### `getSecondaryActions(filters?: SkySummaryActionBarSecondaryActionsHarnessFilters): Promise<SkySummaryActionBarSecondaryActionsHarness>`

Gets the harness for the secondary actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSecondaryActionsHarness>`

#### `getSummary(filters?: SkySummaryActionBarSummaryHarnessFilters): Promise<SkySummaryActionBarSummaryHarness>`

Gets the harness for the summary information.

#### Parameters

##### `filters?: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSummaryHarness>`

#### `hasError(error: SkySummaryActionBarError): Promise<boolean>`

Whether the error has fired.

#### Parameters

##### `error: SkySummaryActionBarError`

#### Returns

`Promise<boolean>`

#### `isSummaryVisible(): Promise<boolean>`

Whether the summary information is visible.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarHarness.with(filters: SkySummaryActionBarHarnessFilters): HarnessPredicate<SkySummaryActionBarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarHarness>`

 SkySummaryActionBarHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-harness.md) instances.

    interface SkySummaryActionBarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarPrimaryActionHarness
----------------------------------------

Type: Class

`import { SkySummaryActionBarPrimaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar primary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarPrimaryActionHarness.with(filters: SkySummaryActionBarPrimaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarPrimaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

 SkySummaryActionBarPrimaryActionHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarPrimaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-primary-action-harness.md) instances.

    interface SkySummaryActionBarPrimaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionsHarness
-------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionsHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary actions component in tests. Use this harness to query harnesses for an individual action's [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-secondary-action-harness.md).

### Methods

#### `getAction(filters: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness>`

Gets a specific action based on the filter criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness>`

#### `getActions(filters?: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness[]>`

Gets an array of actions based on the filter criteria. If no filter is provided, returns all actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness[]>`

#### `SkySummaryActionBarSecondaryActionsHarness.with(filters: SkySummaryActionBarSecondaryActionsHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionsHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

 SkySummaryActionBarSecondaryActionsHarnessFilters
--------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionsHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-secondary-actions-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionsHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionHarness
------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarSecondaryActionHarness.with(filters: SkySummaryActionBarSecondaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

 SkySummaryActionBarSecondaryActionHarnessFilters
-------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-secondary-action-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSummaryHarness
----------------------------------

Type: Class

`import { SkySummaryActionBarSummaryHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar summary component in tests. Use this harness to query components inside the `sky-summary-action-bar-summary` component.

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

#### `SkySummaryActionBarSummaryHarness.with(filters: SkySummaryActionBarSummaryHarnessFilters): HarnessPredicate<SkySummaryActionBarSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSummaryHarness>`

 SkySummaryActionBarSummaryHarnessFilters
-----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSummaryHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-summary-harness.md) instances.

    interface SkySummaryActionBarSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarCancelHarness
---------------------------------

Type: Class

`import { SkySummaryActionBarCancelHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar cancel component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarCancelHarness.with(filters: SkySummaryActionBarCancelHarnessFilters): HarnessPredicate<SkySummaryActionBarCancelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarCancelHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarCancelHarness>`

 SkySummaryActionBarCancelHarnessFilters
----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarCancelHarness](/skyux/components/summary-action-bar?docs-active-tab=development#class_sky-summary-action-bar-cancel-harness.md) instances.

    interface SkySummaryActionBarCancelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Summary action bar
==================

The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.Usage
------

### Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-multi-list.eca66302425efc4ede29bb33f7a6552f.png)

Do use summary action bars for actions on a list of items.

Use summary action bars for actions that are taken on the selected record in [split views](/skyux/components/split-view.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-split-view.a4756d40b3b5ab883c7e80f2741d0756.png)

Do use summary action bars for actions in split views.

Use summary action bars when you need to show summary information related to the forms in [modals](/skyux/components/modal.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-modal.f2d6e98c71020b71fc5f203960636524.png)

Do use summary action bars for summary information in modals.

### Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/dont-use-overload.f9d736e6da09879cf3a6bd8b389c8282.png)

Don't use summary action bars for large amounts of content.

 Anatomy
--------

1

Actions

2

Summary information (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/anatomy.de4cf54c932033fda9a75bd01e8911a7.png)

 Behavior and states
--------------------

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/behavior-collapse.1664d7953414f7a8fbcc8df83bf590c2.png)

 Options
--------

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-wrap-summary.f015f5b8d79901092c13f702fff80b7b.png)

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-conditional-action.419a415cbcc6ce907504e7d57837bc1f.png)

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-context-menu.c8ab20b6d2fa3a6d7fe6861545df1950.png)

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-summary.a9ad346cca9114628894ee53578affa4.png)

 Related information
--------------------

### Components

*   [Data entry grid](/skyux/components/data-entry-grid.md)
*   [Data grid](/skyux/components/data-grid.md)
*   [Modal](/skyux/components/modal.md)
*   [Repeater](/skyux/components/repeater.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/action-bars`[View in NPM](https://www.npmjs.com/package/@skyux/action-bars) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/action-bars/src/lib/modules/summary-action-bar/summary-action-bar.module.ts#L31) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/action-bars`Copy None found.

 SkySummaryActionBarModule
--------------------------

Type: Module

`import { SkySummaryActionBarModule } from '@skyux/action-bars';`

 SkySummaryActionBarComponent
-----------------------------

Type: Component

Selector: `sky-summary-action-bar`

Contains the `sky-summary-action-bar-actions` and `sky-summary-action-bar-summary` components.

### Inputs

#### `formErrors: SkySummaryActionBarError[] | undefined`

 SkySummaryActionBarActionsComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-actions`

Contains actions for the `sky-summary-action-bar` component.

 SkySummaryActionBarPrimaryActionComponent
------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-primary-action`

Displays a primary button.

### Inputs

#### `disabled: boolean`

Whether to disable the primary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the primary action.

 SkySummaryActionBarSecondaryActionsComponent
---------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-actions`

Contains secondary actions specified with `sky-summary-action-bar-secondary-action` components.

 SkySummaryActionBarSecondaryActionComponent
--------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-action`

Specifies secondary actions.

### Inputs

#### `disabled: boolean`

Whether to disable a secondary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select a secondary action.

 SkySummaryActionBarCancelComponent
-----------------------------------

Type: Component

Selector: `sky-summary-action-bar-cancel`

Displays a cancel action.

### Inputs

#### `disabled: boolean`

Whether to disable the cancel action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the cancel action.

 SkySummaryActionBarSummaryComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-summary`

Specifies the summary information to display.

 SkySummaryActionBarError
-------------------------

Type: Interface

Contains an object with properties for displaying form-level errors in a summary action bar.

    interface SkySummaryActionBarError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySummaryActionBarHarness
---------------------------

Type: Class

`import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar component in tests.

### Methods

#### `collapseSummary(): Promise<void>`

In a smaller viewport, collapses the summary.

#### Returns

`Promise<void>`

#### `expandSummary(): Promise<void>`

In a smaller viewport, expands the summary.

#### Returns

`Promise<void>`

#### `getCancel(filters?: SkySummaryActionBarCancelHarnessFilters): Promise<SkySummaryActionBarCancelHarness>`

Gets the harness for the cancel action.

#### Parameters

##### `filters?: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarCancelHarness>`

#### `getErrors(): Promise<SkySummaryActionBarError[]>`

Gets the active errors.

#### Returns

`Promise<SkySummaryActionBarError[]>`

#### `getPrimaryAction(filters?: SkySummaryActionBarPrimaryActionHarnessFilters): Promise<SkySummaryActionBarPrimaryActionHarness>`

Gets the harness for the primary action.

#### Parameters

##### `filters?: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarPrimaryActionHarness>`

#### `getSecondaryActions(filters?: SkySummaryActionBarSecondaryActionsHarnessFilters): Promise<SkySummaryActionBarSecondaryActionsHarness>`

Gets the harness for the secondary actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSecondaryActionsHarness>`

#### `getSummary(filters?: SkySummaryActionBarSummaryHarnessFilters): Promise<SkySummaryActionBarSummaryHarness>`

Gets the harness for the summary information.

#### Parameters

##### `filters?: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSummaryHarness>`

#### `hasError(error: SkySummaryActionBarError): Promise<boolean>`

Whether the error has fired.

#### Parameters

##### `error: SkySummaryActionBarError`

#### Returns

`Promise<boolean>`

#### `isSummaryVisible(): Promise<boolean>`

Whether the summary information is visible.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarHarness.with(filters: SkySummaryActionBarHarnessFilters): HarnessPredicate<SkySummaryActionBarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarHarness>`

 SkySummaryActionBarHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-harness.md) instances.

    interface SkySummaryActionBarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarPrimaryActionHarness
----------------------------------------

Type: Class

`import { SkySummaryActionBarPrimaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar primary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarPrimaryActionHarness.with(filters: SkySummaryActionBarPrimaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarPrimaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

 SkySummaryActionBarPrimaryActionHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarPrimaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-primary-action-harness.md) instances.

    interface SkySummaryActionBarPrimaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionsHarness
-------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionsHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary actions component in tests. Use this harness to query harnesses for an individual action's [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-secondary-action-harness.md).

### Methods

#### `getAction(filters: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness>`

Gets a specific action based on the filter criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness>`

#### `getActions(filters?: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness[]>`

Gets an array of actions based on the filter criteria. If no filter is provided, returns all actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness[]>`

#### `SkySummaryActionBarSecondaryActionsHarness.with(filters: SkySummaryActionBarSecondaryActionsHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionsHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

 SkySummaryActionBarSecondaryActionsHarnessFilters
--------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionsHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-secondary-actions-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionsHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionHarness
------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarSecondaryActionHarness.with(filters: SkySummaryActionBarSecondaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

 SkySummaryActionBarSecondaryActionHarnessFilters
-------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-secondary-action-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSummaryHarness
----------------------------------

Type: Class

`import { SkySummaryActionBarSummaryHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar summary component in tests. Use this harness to query components inside the `sky-summary-action-bar-summary` component.

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

#### `SkySummaryActionBarSummaryHarness.with(filters: SkySummaryActionBarSummaryHarnessFilters): HarnessPredicate<SkySummaryActionBarSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSummaryHarness>`

 SkySummaryActionBarSummaryHarnessFilters
-----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSummaryHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-summary-harness.md) instances.

    interface SkySummaryActionBarSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarCancelHarness
---------------------------------

Type: Class

`import { SkySummaryActionBarCancelHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar cancel component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarCancelHarness.with(filters: SkySummaryActionBarCancelHarnessFilters): HarnessPredicate<SkySummaryActionBarCancelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarCancelHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarCancelHarness>`

 SkySummaryActionBarCancelHarnessFilters
----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarCancelHarness](/skyux/components/summary-action-bar?docs-active-tab=examples#class_sky-summary-action-bar-cancel-harness.md) instances.

    interface SkySummaryActionBarCancelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Basic summary action bar

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

    <sky-summary-action-bar data-sky-id="donation-summary">
      <sky-summary-action-bar-actions>
        <sky-summary-action-bar-primary-action
          (actionClick)="onPrimaryActionClick()"
        >
          Primary action
        </sky-summary-action-bar-primary-action>
        <sky-summary-action-bar-secondary-actions>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action"
            (actionClick)="onSecondaryActionClick()"
          >
            Secondary action
          </sky-summary-action-bar-secondary-action>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action-2"
            (actionClick)="onSecondaryAction2Click()"
          >
            Secondary action 2
          </sky-summary-action-bar-secondary-action>
        </sky-summary-action-bar-secondary-actions>
      </sky-summary-action-bar-actions>
      <sky-summary-action-bar-summary>
        <sky-key-info>
          <sky-key-info-value>$250</sky-key-info-value>
          <sky-key-info-label>Given this month</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,000</sky-key-info-value>
          <sky-key-info-label>Given this year</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,300</sky-key-info-value>
          <sky-key-info-label>Given all time</sky-key-info-label>
        </sky-key-info>
      </sky-summary-action-bar-summary>
    </sky-summary-action-bar>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
    import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
    
    import { ActionBarsSummaryActionBarBasicExampleComponent } from './example.component';
    
    describe('Basic summary action bar example', () => {
      async function setupTest(): Promise<{
        harness: SkySummaryActionBarHarness;
        fixture: ComponentFixture<ActionBarsSummaryActionBarBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ActionBarsSummaryActionBarBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
        );
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            ActionBarsSummaryActionBarBasicExampleComponent,
            NoopAnimationsModule,
          ],
        });
      });
    
      it('should set up primary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const primaryActionHarness = await harness.getPrimaryAction();
        await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
          'Primary action',
        );
    
        const spy = spyOn(fixture.componentInstance, 'onPrimaryActionClick');
        await primaryActionHarness.click();
        expect(spy).toHaveBeenCalled();
      });
    
      it('should set up secondary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const secondaryActions = await harness.getSecondaryActions();
        const actions = await secondaryActions.getActions();
        expect(actions.length).toBe(2);
    
        const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
        const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');
    
        await actions[1].click();
        expect(spy2).toHaveBeenCalled();
    
        const secondaryAction = await secondaryActions.getAction({
          dataSkyId: 'secondary-action',
        });
        await secondaryAction.click();
        expect(spy1).toHaveBeenCalled();
      });
    
      it('should set up the summary', async () => {
        const { harness } = await setupTest();
    
        const summary = await harness.getSummary();
        const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
        expect(keyInfos.length).toBe(3);
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkySummaryActionBarModule } from '@skyux/action-bars';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    
    /**
     * @title Basic summary action bar
     * @docsDemoHidden
     */
    @Component({
      selector: 'app-action-bars-summary-action-bar-basic-example',
      templateUrl: './example.component.html',
      imports: [SkyKeyInfoModule, SkySummaryActionBarModule],
    })
    export class ActionBarsSummaryActionBarBasicExampleComponent {
      public onPrimaryActionClick(): void {
        alert('Primary action button clicked.');
      }
    
      public onSecondaryActionClick(): void {
        alert('Secondary action button clicked.');
      }
    
      public onSecondaryAction2Click(): void {
        alert('Secondary action 2 button clicked.');
      }
    }
### Summary action bar with errors

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

    <form [formGroup]="exampleForm">
      <sky-summary-action-bar
        data-sky-id="donation-summary"
        [formErrors]="formErrors()"
      >
        <sky-summary-action-bar-actions>
          <sky-summary-action-bar-primary-action
            (actionClick)="onPrimaryActionClick()"
          >
            Primary action
          </sky-summary-action-bar-primary-action>
          <sky-summary-action-bar-secondary-actions>
            <sky-summary-action-bar-secondary-action
              data-sky-id="single-error-action"
              (actionClick)="singleError()"
            >
              Single error action
            </sky-summary-action-bar-secondary-action>
            <sky-summary-action-bar-secondary-action
              data-sky-id="multiple-error-action"
              (actionClick)="multipleErrors()"
            >
              Multiple errors action
            </sky-summary-action-bar-secondary-action>
          </sky-summary-action-bar-secondary-actions>
        </sky-summary-action-bar-actions>
        <sky-summary-action-bar-summary>
          @for (info of donationSummary.value; track info) {
            <sky-key-info>
              <sky-key-info-value>${{ info.value }}</sky-key-info-value>
              <sky-key-info-label>{{ info.label }}</sky-key-info-label>
            </sky-key-info>
          }
        </sky-summary-action-bar-summary>
      </sky-summary-action-bar>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
    import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
    
    import { ActionBarsSummaryActionBarErrorExampleComponent } from './example.component';
    
    describe('Error summary action bar example', () => {
      async function setupTest(): Promise<{
        harness: SkySummaryActionBarHarness;
        fixture: ComponentFixture<ActionBarsSummaryActionBarErrorExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ActionBarsSummaryActionBarErrorExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
        );
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            ActionBarsSummaryActionBarErrorExampleComponent,
            NoopAnimationsModule,
          ],
        });
      });
    
      it('should add an error on clicking secondary action button to add single error', async () => {
        const { harness } = await setupTest();
    
        const secondaryActions = await harness.getSecondaryActions();
        const singleErrorAction = await secondaryActions.getAction({
          dataSkyId: 'single-error-action',
        });
    
        await singleErrorAction.click();
    
        await expectAsync(
          harness.hasError({ message: 'Monthly donation is missing.' }),
        ).toBeResolvedTo(true);
      });
    
      it('should add errors on clicking secondary action button to add multiple errors', async () => {
        const { harness } = await setupTest();
    
        const secondaryActions = await harness.getSecondaryActions();
        const singleErrorAction = await secondaryActions.getActions();
    
        await singleErrorAction[1].click();
    
        const errors = await harness.getErrors();
        expect(errors.length).toBe(2);
      });
    
      it('should set up the summary', async () => {
        const { harness } = await setupTest();
    
        const summary = await harness.getSummary();
        const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
        expect(keyInfos.length).toBe(3);
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import { toSignal } from '@angular/core/rxjs-interop';
    import { FormBuilder, FormControl, ReactiveFormsModule } from '@angular/forms';
    import {
      SkySummaryActionBarError,
      SkySummaryActionBarModule,
    } from '@skyux/action-bars';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    
    import { of, switchMap } from 'rxjs';
    
    interface donationSummary {
      value: number;
      label: string;
    }
    
    /**
     * @title Summary action bar with errors
     * @docsDemoHidden
     */
    @Component({
      selector: 'app-action-bars-summary-action-bar-error-example',
      templateUrl: './example.component.html',
      imports: [SkyKeyInfoModule, SkySummaryActionBarModule, ReactiveFormsModule],
    })
    export class ActionBarsSummaryActionBarErrorExampleComponent {
      protected donationSummary = new FormControl<donationSummary[] | null>([
        {
          value: 250,
          label: 'Given this month',
        },
        {
          value: 1000,
          label: 'Given this year',
        },
        {
          value: 1300,
          label: 'Given all time',
        },
      ]);
      protected exampleForm = inject(FormBuilder).group({
        donationSummary: this.donationSummary,
      });
    
      protected formErrors = toSignal<SkySummaryActionBarError[] | undefined>(
        this.donationSummary.statusChanges.pipe(
          switchMap(() => {
            const errors = this.donationSummary.errors;
    
            return of(
              errors
                ? Object.values(errors).map((error) => ({
                    message: error as string,
                  }))
                : undefined,
            );
          }),
        ),
      );
    
      protected onPrimaryActionClick(): void {
        alert('Primary action button clicked.');
      }
    
      protected singleError(): void {
        this.donationSummary.setErrors({
          singleError: 'Monthly donation is missing.',
        });
      }
    
      protected multipleErrors(): void {
        this.donationSummary.setErrors({
          firstError: 'Monthly donation is missing.',
          secondError: 'Yearly donation is missing.',
        });
      }
    }
### Modal with summary action bar

Edit in StackBlitz

Open modal

Show code

Copy

    <button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
      Open modal
    </button>
Copy

    <sky-modal headingText="Modal with summary action bar">
      <sky-modal-content> Hello world! </sky-modal-content>
      <sky-modal-footer>
        <sky-summary-action-bar data-sky-id="donation-summary">
          <sky-summary-action-bar-actions>
            <sky-summary-action-bar-primary-action (actionClick)="save()">
              Primary action
            </sky-summary-action-bar-primary-action>
            <sky-summary-action-bar-secondary-actions>
              <sky-summary-action-bar-secondary-action
                data-sky-id="secondary-action"
                (actionClick)="onSecondaryActionClick()"
              >
                Secondary action
              </sky-summary-action-bar-secondary-action>
              <sky-summary-action-bar-secondary-action
                data-sky-id="secondary-action-2"
                (actionClick)="onSecondaryAction2Click()"
              >
                Secondary action 2
              </sky-summary-action-bar-secondary-action>
            </sky-summary-action-bar-secondary-actions>
            <sky-summary-action-bar-cancel (actionClick)="cancel()">
              Cancel
            </sky-summary-action-bar-cancel>
          </sky-summary-action-bar-actions>
          <sky-summary-action-bar-summary>
            <sky-key-info>
              <sky-key-info-value>$250</sky-key-info-value>
              <sky-key-info-label>Given this month</sky-key-info-label>
            </sky-key-info>
            <sky-key-info>
              <sky-key-info-value>$1,000</sky-key-info-value>
              <sky-key-info-label>Given this year</sky-key-info-label>
            </sky-key-info>
            <sky-key-info>
              <sky-key-info-value>$1,300</sky-key-info-value>
              <sky-key-info-label>Given all time</sky-key-info-label>
            </sky-key-info>
          </sky-summary-action-bar-summary>
        </sky-summary-action-bar>
      </sky-modal-footer>
    </sky-modal>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
    import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
    import { SkyModalInstance } from '@skyux/modals';
    
    import { ModalComponent } from './modal.component';
    
    describe('Modal summary action bar example', () => {
      async function setupTest(): Promise<{
        harness: SkySummaryActionBarHarness;
        fixture: ComponentFixture<ModalComponent>;
      }> {
        const fixture = TestBed.createComponent(ModalComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
        );
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [ModalComponent, NoopAnimationsModule],
          providers: [SkyModalInstance],
        });
      });
    
      it('should set up primary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const primaryActionHarness = await harness.getPrimaryAction();
        await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
          'Primary action',
        );
    
        const spy = spyOn(fixture.componentInstance, 'save');
        await primaryActionHarness.click();
        expect(spy).toHaveBeenCalled();
      });
    
      it('should set up secondary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const secondaryActions = await harness.getSecondaryActions();
        const actions = await secondaryActions.getActions();
        expect(actions.length).toBe(2);
    
        const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
        const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');
    
        await actions[1].click();
        expect(spy2).toHaveBeenCalled();
    
        const secondaryAction = await secondaryActions.getAction({
          dataSkyId: 'secondary-action',
        });
        await secondaryAction.click();
        expect(spy1).toHaveBeenCalled();
      });
    
      it('should set up the summary', async () => {
        const { harness } = await setupTest();
    
        const summary = await harness.getSummary();
        const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
        expect(keyInfos.length).toBe(3);
      });
    });
Copy

    import { Component, inject } from '@angular/core';
    import { SkySummaryActionBarModule } from '@skyux/action-bars';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    @Component({
      selector: 'app-modal',
      templateUrl: './modal.component.html',
      imports: [SkyKeyInfoModule, SkyModalModule, SkySummaryActionBarModule],
    })
    export class ModalComponent {
      readonly #modalInstance = inject(SkyModalInstance);
    
      public onSecondaryActionClick(): void {
        alert('Secondary action button clicked.');
      }
    
      public onSecondaryAction2Click(): void {
        alert('Secondary action 2 button clicked.');
      }
    
      protected cancel(): void {
        this.#modalInstance.cancel();
      }
    
      public save(): void {
        this.#modalInstance.save();
      }
    }

Copy

    import { Component, inject } from '@angular/core';
    import { SkyModalService } from '@skyux/modals';
    
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Modal with summary action bar
     */
    @Component({
      standalone: true,
      selector: 'app-action-bars-summary-action-bar-modal-example',
      templateUrl: './example.component.html',
    })
    export class ActionBarsSummaryActionBarModalExampleComponent {
      readonly #modalSvc = inject(SkyModalService);
    
      protected openModal(): void {
        this.#modalSvc.open(ModalComponent, {
          size: 'large',
        });
      }
    }
### Tab with summary action bar

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

    <sky-tabset [active]="0">
      <sky-tab tabHeading="Tab 1"> Tab without summary action bar. </sky-tab>
      <sky-tab tabHeading="Tab 2">
        Tab with summary action bar.
        <sky-summary-action-bar data-sky-id="donation-summary">
          <sky-summary-action-bar-actions>
            <sky-summary-action-bar-primary-action
              (actionClick)="onPrimaryActionClick()"
            >
              Primary action
            </sky-summary-action-bar-primary-action>
            <sky-summary-action-bar-secondary-actions>
              <sky-summary-action-bar-secondary-action
                data-sky-id="secondary-action"
                (actionClick)="onSecondaryActionClick()"
              >
                Secondary action
              </sky-summary-action-bar-secondary-action>
              <sky-summary-action-bar-secondary-action
                data-sky-id="secondary-action-2"
                (actionClick)="onSecondaryAction2Click()"
              >
                Secondary action 2
              </sky-summary-action-bar-secondary-action>
            </sky-summary-action-bar-secondary-actions>
          </sky-summary-action-bar-actions>
          <sky-summary-action-bar-summary>
            <sky-key-info>
              <sky-key-info-value>$250</sky-key-info-value>
              <sky-key-info-label>Given this month</sky-key-info-label>
            </sky-key-info>
            <sky-key-info>
              <sky-key-info-value>$1,000</sky-key-info-value>
              <sky-key-info-label>Given this year</sky-key-info-label>
            </sky-key-info>
            <sky-key-info>
              <sky-key-info-value>$1,300</sky-key-info-value>
              <sky-key-info-label>Given all time</sky-key-info-label>
            </sky-key-info>
          </sky-summary-action-bar-summary>
        </sky-summary-action-bar>
      </sky-tab>
    </sky-tabset>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { provideRouter } from '@angular/router';
    import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
    import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
    
    import { ActionBarsSummaryActionBarTabExampleComponent } from './example.component';
    
    describe('Basic summary action bar example', () => {
      async function setupTest(): Promise<{
        harness: SkySummaryActionBarHarness;
        fixture: ComponentFixture<ActionBarsSummaryActionBarTabExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ActionBarsSummaryActionBarTabExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
        );
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            ActionBarsSummaryActionBarTabExampleComponent,
            NoopAnimationsModule,
          ],
          providers: [provideRouter([])],
        });
      });
    
      it('should set up primary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const primaryActionHarness = await harness.getPrimaryAction();
        await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
          'Primary action',
        );
    
        const spy = spyOn(fixture.componentInstance, 'onPrimaryActionClick');
        await primaryActionHarness.click();
        expect(spy).toHaveBeenCalled();
      });
    
      it('should set up secondary actions', async () => {
        const { harness, fixture } = await setupTest();
    
        const secondaryActions = await harness.getSecondaryActions();
        const actions = await secondaryActions.getActions();
        expect(actions.length).toBe(2);
    
        const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
        const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');
    
        await actions[1].click();
        expect(spy2).toHaveBeenCalled();
    
        const secondaryAction = await secondaryActions.getAction({
          dataSkyId: 'secondary-action',
        });
        await secondaryAction.click();
        expect(spy1).toHaveBeenCalled();
      });
    
      it('should set up the summary', async () => {
        const { harness } = await setupTest();
    
        const summary = await harness.getSummary();
        const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
        expect(keyInfos.length).toBe(3);
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkySummaryActionBarModule } from '@skyux/action-bars';
    import { SkyKeyInfoModule } from '@skyux/indicators';
    import { SkyTabsModule } from '@skyux/tabs';
    
    /**
     * @title Tab with summary action bar
     * @docsDemoHidden
     */
    @Component({
      selector: 'app-action-bars-summary-action-bar-tab-example',
      templateUrl: './example.component.html',
      imports: [SkyKeyInfoModule, SkySummaryActionBarModule, SkyTabsModule],
    })
    export class ActionBarsSummaryActionBarTabExampleComponent {
      public onPrimaryActionClick(): void {
        alert('Primary action button clicked.');
      }
    
      public onSecondaryActionClick(): void {
        alert('Secondary action button clicked.');
      }
    
      public onSecondaryAction2Click(): void {
        alert('Secondary action 2 button clicked.');
      }
    }

# Testing

                  Skip to Main Content

 Summary action bar
==================

The summary action bar module provides a docked container for actions and summary information on forms or multiselect lists.

 Usage
------

### Use when

Use summary action bars to hold actions and summary information related to the parent container to which it is docked.

Use summary action bars for actions that users can take on multiple items in a list of items. When used with a multiselect list, hide the summary action bar until users select an item in the list. After users select an item, the summary action bar should fly in from the bottom of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-multi-list.eca66302425efc4ede29bb33f7a6552f.png)

Do use summary action bars for actions on a list of items.

Use summary action bars for actions that are taken on the selected record in [split views](/skyux/components/split-view.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-split-view.a4756d40b3b5ab883c7e80f2741d0756.png)

Do use summary action bars for actions in split views.

Use summary action bars when you need to show summary information related to the forms in [modals](/skyux/components/modal.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/use-modal.f2d6e98c71020b71fc5f203960636524.png)

Do use summary action bars for summary information in modals.

### Don't use when

Don't use summary action bars to wrap a large amount of content because it eats into the vertical space on the page. Show the least amount of information that users need to inform their actions. Explore alternate layouts if you need to show a large amount of summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/dont-use-overload.f9d736e6da09879cf3a6bd8b389c8282.png)

Don't use summary action bars for large amounts of content.

 Anatomy
--------

1

Actions

2

Summary information (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/anatomy.de4cf54c932033fda9a75bd01e8911a7.png)

 Behavior and states
--------------------

### Collapsing summary information

In smaller viewports, the summary information section becomes expandable/collapsible to allow more visible space for the main content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/behavior-collapse.1664d7953414f7a8fbcc8df83bf590c2.png)

 Options
--------

### Summary information

When users need summarized information about selected items in a list or data entered in a form as a confirmation before taking an action, put the relevant information in the summary information area.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-wrap-summary.f015f5b8d79901092c13f702fff80b7b.png)

### Conditional actions

In multiselect lists, items may be in mixed states where certain actions can only be taken on certain items. Expose all the possible actions, and append the number of items that action will be taken on when invoked.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-conditional-action.419a415cbcc6ce907504e7d57837bc1f.png)

### Secondary actions

Secondary actions collapse into a context menu at small viewport widths.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/responsive-context-menu.c8ab20b6d2fa3a6d7fe6861545df1950.png)

### Summary information

When the viewport width changes, summary information re-flows based on the available width.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/action-bars/img/option-summary.a9ad346cca9114628894ee53578affa4.png)

 Related information
--------------------

### Components

*   [Data entry grid](/skyux/components/data-entry-grid.md)
*   [Data grid](/skyux/components/data-grid.md)
*   [Modal](/skyux/components/modal.md)
*   [Repeater](/skyux/components/repeater.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/action-bars`[View in NPM](https://www.npmjs.com/package/@skyux/action-bars) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/action-bars/src/lib/modules/summary-action-bar/summary-action-bar.module.ts#L31) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/action-bars`Copy None found.

 SkySummaryActionBarModule
--------------------------

Type: Module

`import { SkySummaryActionBarModule } from '@skyux/action-bars';`

 SkySummaryActionBarComponent
-----------------------------

Type: Component

Selector: `sky-summary-action-bar`

Contains the `sky-summary-action-bar-actions` and `sky-summary-action-bar-summary` components.

### Inputs

#### `formErrors: SkySummaryActionBarError[] | undefined`

 SkySummaryActionBarActionsComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-actions`

Contains actions for the `sky-summary-action-bar` component.

 SkySummaryActionBarPrimaryActionComponent
------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-primary-action`

Displays a primary button.

### Inputs

#### `disabled: boolean`

Whether to disable the primary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the primary action.

 SkySummaryActionBarSecondaryActionsComponent
---------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-actions`

Contains secondary actions specified with `sky-summary-action-bar-secondary-action` components.

 SkySummaryActionBarSecondaryActionComponent
--------------------------------------------

Type: Component

Selector: `sky-summary-action-bar-secondary-action`

Specifies secondary actions.

### Inputs

#### `disabled: boolean`

Whether to disable a secondary action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select a secondary action.

 SkySummaryActionBarCancelComponent
-----------------------------------

Type: Component

Selector: `sky-summary-action-bar-cancel`

Displays a cancel action.

### Inputs

#### `disabled: boolean`

Whether to disable the cancel action.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<void>`

Fires when users select the cancel action.

 SkySummaryActionBarSummaryComponent
------------------------------------

Type: Component

Selector: `sky-summary-action-bar-summary`

Specifies the summary information to display.

 SkySummaryActionBarError
-------------------------

Type: Interface

Contains an object with properties for displaying form-level errors in a summary action bar.

    interface SkySummaryActionBarError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySummaryActionBarHarness
---------------------------

Type: Class

`import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar component in tests.

### Methods

#### `collapseSummary(): Promise<void>`

In a smaller viewport, collapses the summary.

#### Returns

`Promise<void>`

#### `expandSummary(): Promise<void>`

In a smaller viewport, expands the summary.

#### Returns

`Promise<void>`

#### `getCancel(filters?: SkySummaryActionBarCancelHarnessFilters): Promise<SkySummaryActionBarCancelHarness>`

Gets the harness for the cancel action.

#### Parameters

##### `filters?: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarCancelHarness>`

#### `getErrors(): Promise<SkySummaryActionBarError[]>`

Gets the active errors.

#### Returns

`Promise<SkySummaryActionBarError[]>`

#### `getPrimaryAction(filters?: SkySummaryActionBarPrimaryActionHarnessFilters): Promise<SkySummaryActionBarPrimaryActionHarness>`

Gets the harness for the primary action.

#### Parameters

##### `filters?: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarPrimaryActionHarness>`

#### `getSecondaryActions(filters?: SkySummaryActionBarSecondaryActionsHarnessFilters): Promise<SkySummaryActionBarSecondaryActionsHarness>`

Gets the harness for the secondary actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSecondaryActionsHarness>`

#### `getSummary(filters?: SkySummaryActionBarSummaryHarnessFilters): Promise<SkySummaryActionBarSummaryHarness>`

Gets the harness for the summary information.

#### Parameters

##### `filters?: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`Promise<SkySummaryActionBarSummaryHarness>`

#### `hasError(error: SkySummaryActionBarError): Promise<boolean>`

Whether the error has fired.

#### Parameters

##### `error: SkySummaryActionBarError`

#### Returns

`Promise<boolean>`

#### `isSummaryVisible(): Promise<boolean>`

Whether the summary information is visible.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarHarness.with(filters: SkySummaryActionBarHarnessFilters): HarnessPredicate<SkySummaryActionBarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarHarness>`

 SkySummaryActionBarHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-harness.md) instances.

    interface SkySummaryActionBarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarPrimaryActionHarness
----------------------------------------

Type: Class

`import { SkySummaryActionBarPrimaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar primary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarPrimaryActionHarness.with(filters: SkySummaryActionBarPrimaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarPrimaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarPrimaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarPrimaryActionHarness>`

 SkySummaryActionBarPrimaryActionHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarPrimaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-primary-action-harness.md) instances.

    interface SkySummaryActionBarPrimaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionsHarness
-------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionsHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary actions component in tests. Use this harness to query harnesses for an individual action's [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-secondary-action-harness.md).

### Methods

#### `getAction(filters: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness>`

Gets a specific action based on the filter criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness>`

#### `getActions(filters?: SkySummaryActionBarSecondaryActionHarnessFilters): Promise<SkySummaryActionBarSecondaryActionHarness[]>`

Gets an array of actions based on the filter criteria. If no filter is provided, returns all actions.

#### Parameters

##### `filters?: SkySummaryActionBarSecondaryActionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySummaryActionBarSecondaryActionHarness[]>`

#### `SkySummaryActionBarSecondaryActionsHarness.with(filters: SkySummaryActionBarSecondaryActionsHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionsHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionsHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionsHarness>`

 SkySummaryActionBarSecondaryActionsHarnessFilters
--------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionsHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-secondary-actions-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionsHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSecondaryActionHarness
------------------------------------------

Type: Class

`import { SkySummaryActionBarSecondaryActionHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar secondary action component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarSecondaryActionHarness.with(filters: SkySummaryActionBarSecondaryActionHarnessFilters): HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSecondaryActionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSecondaryActionHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSecondaryActionHarness>`

 SkySummaryActionBarSecondaryActionHarnessFilters
-------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSecondaryActionHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-secondary-action-harness.md) instances.

    interface SkySummaryActionBarSecondaryActionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarSummaryHarness
----------------------------------

Type: Class

`import { SkySummaryActionBarSummaryHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar summary component in tests. Use this harness to query components inside the `sky-summary-action-bar-summary` component.

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

#### `SkySummaryActionBarSummaryHarness.with(filters: SkySummaryActionBarSummaryHarnessFilters): HarnessPredicate<SkySummaryActionBarSummaryHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarSummaryHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarSummaryHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarSummaryHarness>`

 SkySummaryActionBarSummaryHarnessFilters
-----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarSummaryHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-summary-harness.md) instances.

    interface SkySummaryActionBarSummaryHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySummaryActionBarCancelHarness
---------------------------------

Type: Class

`import { SkySummaryActionBarCancelHarness } from '@skyux/action-bars/testing';`

Harness for interacting with a summary action bar cancel component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkySummaryActionBarCancelHarness.with(filters: SkySummaryActionBarCancelHarnessFilters): HarnessPredicate<SkySummaryActionBarCancelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySummaryActionBarCancelHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySummaryActionBarCancelHarnessFilters`

#### Returns

`HarnessPredicate<SkySummaryActionBarCancelHarness>`

 SkySummaryActionBarCancelHarnessFilters
----------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySummaryActionBarCancelHarness](/skyux/components/summary-action-bar?docs-active-tab=testing#class_sky-summary-action-bar-cancel-harness.md) instances.

    interface SkySummaryActionBarCancelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
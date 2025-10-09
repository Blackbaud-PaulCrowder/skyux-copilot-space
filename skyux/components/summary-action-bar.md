                  

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
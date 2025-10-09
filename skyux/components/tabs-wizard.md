                  

 Wizard
======

Wizards guide users through pre-defined steps in a particular order to represent a series of related decisions in a user's direct workflow.

This wizard implementation replaces a deprecated wizard that used `sky-progress-indicator`. We recommend this implementation that instead uses `tabStyle="wizard"` on the `sky-tabset` component.

 Usage
------

### Use when

Use wizards when a single task includes multiple steps that users must perform in a particular order. Wizards illustrate the step-by-step nature of tasks and reinforce progress toward final goals as users complete steps.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/wizard/wizard-usage-1.5f31ad737059741184e72544efc4295e.png)

Do use wizards for tasks broken into multiple steps.

Use wizards when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting.

Use wizards when the interaction complexity of each step is low. For example, steps can use standard form inputs and controls.

Use wizards in large-sized [modals](/skyux/components/modal.md) only to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### Don't use when

Don't use wizards for long or complex setup processes or when the complexity of steps varies drastically. Use [waterfall progress indicators](/skyux/components/progress-indicator-waterfall.md) instead.

Don't use wizards when tasks include more than six steps or require more time than a single sitting. Use [waterfall progress indicators](/skyux/components/progress-indicator-waterfall.md) instead.

Don't use wizards when users must be aware of sequential progress that they are not responsible for. Use [passive progress indicators](/skyux/components/progress-indicator-passive.md) instead.

Don't use wizards in small- or medium-sized [modals](/skyux/components/modal.md) because the component requires the horizontal space that large modals provide.

 Anatomy
--------

1

Modal

2

Current step indicator

3

Step indicator

4

Step controls

5

Disabled step indicator (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/wizard/wizard-anatomy.12d31babd2a932d712860da2f8d3d09e.png)

 Options
--------

### Disabled step indicators

To guide users through wizards in a particular order, you can disable steps and reinforce the step-by-step nature of the tasks. In most cases, we recommend disabling future steps until users meet the requirements on the preceding step, which enables the **Next** button.

 Behavior and states
--------------------

### Required inputs

On each step of the wizard, disable the progressive **Next** action until all required inputs are populated.

 Content
--------

### Step numbers

To help guide users through the predefined steps of wizards in the correct order, include sequential numbers in the step labels.

### Step controls

Labels for step controls should clearly indicate the actions that occur when users select the buttons. In general, use the default **Previous** and **Next** labels for the buttons that navigate between steps and the default **Finish** label for the button that completes the wizard and saves information to the database.

Use a [primary button](/skyux/components/button.md) for the most important action on each step, which is generally the **Finish** action on the final step and the **Next** action on the preceding steps. Use secondary buttons for less important actions and a link button for the **Cancel** action. Follow the [form design guidelines](/skyux/design/guidelines/form-design.md) and disable actions until all required inputs have valid values.

 Related information
--------------------

### Components

*   [Modal](/skyux/components/modal.md)
*   [Passive progress indicator](/skyux/components/progress-indicator-passive.md)
*   [Waterfall progress indicator](/skyux/components/progress-indicator-waterfall.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/tabs/tabs.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkyTabsModule
--------------

Type: Module

`import { SkyTabsModule } from '@skyux/tabs';`

 SkyTabsetComponent
-------------------

Type: Component

Selector: `sky-tabset`

### Inputs

#### `active: SkyTabIndex | undefined`

Activates a tab by its `tabIndex` property.

#### `ariaLabel: string | undefined`

The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `permalinkId: string`

Distinguishes a tabset's unique state in the URL by generating a query parameter that is written as `?<queryParam>-active-tab=<sanitized-tab-heading>`. The query parameter's value is parsed automatically from the selected tab's heading text, but you can supply a custom query parameter value for each tab with its `permalinkValue`. This input only applies when `tabStyle` is `"tabs"`

#### `tabStyle: SkyTabsetStyle`

The behavior for a series of tabs.

Default: `"tabs"`

### Outputs

#### `activeChange: EventEmitter<SkyTabIndex>`

Fires when the active tab changes. This event emits the index of the active tab.

#### `newTab: EventEmitter<void>`

Fires when users click the button to add a new tab. The new tab button is added to the tab area when you specify a listener for this event. This event only applies when `tabStyle` is `"tabs"`.

#### `openTab: EventEmitter<void>`

Fires when users click the button to open a tab. The open tab button is added to the tab area when you specify a listener for this event. This event only applies when `tabStyle` is `"tabs"`.

#### `tabIndexesChange: EventEmitter<SkyTabsetTabIndexesChange>`

Fires when any tab's `tabIndex` value changes. This event only applies when `tabStyle` is `"tabs"`.

 SkyTabComponent
----------------

Type: Component

Selector: `sky-tab`

### Inputs

#### `tabHeading: string | undefined`

Required

The tab header. When using tabs as the main navigation on a page, use [the Angular `Title` service](https://angular.io/docs/ts/latest/cookbook/set-document-title.html) and [the SKY UX `title` configuration property](/skyux/learn/reference/configuration#app.md) to reflect the tab header in the page title.

#### `active: boolean`

Whether the tab is active when the tabset loads. After initialization, the `active` property on the tabset component should be used to set the active tab.

Default: `false`

#### `disabled: boolean | undefined`

Whether to disable the tab.

Default: `false`

#### `layout: SkyTabLayoutType`

The tab layout that applies spacing to the tab container element. Use the layout that corresponds with the top-level component type used within the tab, or use `fit` to constrain the tab contents to the available viewport. Use `none` for custom content that does not adhere to predefined spacing or constraints.

Default: `"none"`

#### `permalinkValue: string | undefined`

The custom query parameter value for the tab. This works in conjunction with the tabset's `permalinkId` to distinguish the tab's unique state in the URL by generating a query parameter that is written as `?<queryParam>-active-tab=<sanitized-tab-heading`. By default, the query parameter's value is parsed automatically from the tab's heading text. This input only applies when the tabset's `tabStyle` is `"tabs"`.

#### `tabHeaderCount: string | undefined`

Warning: **Deprecated.** SKY UX no longer recommends adding counts to tabs.

Displays a counter beside the tab header. This input only applies when the tabset's `tabStyle` is `"tabs"`.

#### `tabIndexValue: SkyTabIndex | undefined`

The unique identifier for the tab. If not defined, the identifier is set to the position of the tab on load, starting with `0`.

### Outputs

#### `close: EventEmitter<void>`

Fires when users click the button to close the tab. The close button is added to the tab when you specify a listener for this event. This event only applies when the tabset's `tabStyle` is `"tabs"`.

 SkyTabsetNavButtonComponent
----------------------------

Type: Component

Selector: `sky-tabset-nav-button`

Creates a button to navigate between tabs in a tabset when `tabStyle` is `"wizard"`.

### Inputs

#### `buttonType: SkyTabsetNavButtonType | undefined`

Required

The type of nav button to include.

#### `tabset: SkyTabsetComponent | undefined`

Required

The tabset wizard component to associate with the nav button.

#### `buttonText: string`

The label to display on the nav button. The following are the defaults for each `buttonType`: `next` = "Next", `previous` = "Previous", `finish` = "Finish"

#### `disabled: boolean | undefined`

Whether to disable the nav button. Defaults to the disabled state of the next tab for `next`, the existence of a previous tab for `previous`, and false for `finish`.

 SkyTabsetNavButtonType
-----------------------

Type: Type alias

The nav button type.

    type SkyTabsetNavButtonType = "previous" | "next" | "finish"

 SkyTabIndex
------------

Type: Type alias

    type SkyTabIndex = string | number

 SkyTabLayoutType
-----------------

Type: Type alias

    type SkyTabLayoutType = "none" | "blocks" | "fit" | "list"

 SkyTabsetButtonsDisplayMode
----------------------------

Type: Type alias

    type SkyTabsetButtonsDisplayMode = "dropdown" | "tabs"

 SkyTabsetStyle
---------------

Type: Type alias

    type SkyTabsetStyle = "tabs" | "wizard"

 SkyTabsetTabIndexesChange
--------------------------

Type: Interface

    interface SkyTabsetTabIndexesChange {
      tabs?: { tabHeading?: string; tabIndex?: SkyTabIndex }[];
    }

### Properties

#### `tabs?: { tabHeading?: string; tabIndex?: SkyTabIndex }[]`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTabsetHarness
-----------------

Type: Class

`import { SkyTabsetHarness } from '@skyux/tabs/testing';`

Harness for interacting with a tabset component in tests.

### Methods

#### `clickDropdownTab(): Promise<void>`

In `dropdown` mode, clicks the dropdown tab to open the tab dropdown menu.

#### Returns

`Promise<void>`

#### `clickNewTabButton(): Promise<void>`

Clicks the new tab button if visible.

#### Returns

`Promise<void>`

#### `clickOpenTabButton(): Promise<void>`

Clicks the open tab button if visible.

#### Returns

`Promise<void>`

#### `clickTabButton(tabHeading: string): Promise<void>`

Clicks a tab button with a `tabHeading` matching the input.

#### Parameters

##### `tabHeading: string`

#### Returns

`Promise<void>`

#### `getActiveTabButton(): Promise<null | SkyTabButtonHarness>`

Gets the active tab button harness.

#### Returns

`Promise<null | SkyTabButtonHarness>`

#### `getAriaLabel(): Promise<null | string>`

Gets the tabset aria-label value.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the tabset aria-labelledby value.

#### Returns

`Promise<null | string>`

#### `getMode(): Promise<SkyTabsetButtonsDisplayMode>`

Gets the tabset's display mode.

#### Returns

`Promise<SkyTabsetButtonsDisplayMode>`

#### `getTabButtonHarness(filters: SkyTabButtonHarnessFilters): Promise<SkyTabButtonHarness>`

Gets a specific tab button based on the filter criteria.

#### Parameters

##### `filters: SkyTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTabButtonHarness>`

#### `getTabButtonHarnesses(filters?: SkyTabButtonHarnessFilters): Promise<SkyTabButtonHarness[]>`

Gets an array of tab button harnesses based on the filter criteria. If no filter is provided, returns all tab button harnesses.

#### Parameters

##### `filters?: SkyTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTabButtonHarness[]>`

#### `getTabContentHarness(tabHeading: string): Promise<SkyTabContentHarness>`

Gets a tab content harness for the tab with the given `tabHeading`.

#### Parameters

##### `tabHeading: string`

#### Returns

`Promise<SkyTabContentHarness>`

#### `isWizardTabset(): Promise<boolean>`

Whether the tabset is a Wizard component.

#### Returns

`Promise<boolean>`

#### `SkyTabsetHarness.with(filters: SkyTabsetHarnessFilters): HarnessPredicate<SkyTabsetHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTabsetHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTabsetHarnessFilters`

#### Returns

`HarnessPredicate<SkyTabsetHarness>`

 SkyTabsetHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTabsetHarness` instances.

    interface SkyTabsetHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTabButtonHarness
--------------------

Type: Class

`import { SkyTabButtonHarness } from '@skyux/tabs/testing';`

Harness for interacting with a tab button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the tab button.

#### Returns

`Promise<void>`

#### `clickRemoveButton(): Promise<void>`

Clicks the remove tab button if it is visible.

#### Returns

`Promise<void>`

#### `getPermalink(): Promise<null | string>`

Gets the permalink that the page routes to when the tab is clicked.

#### Returns

`Promise<null | string>`

#### `getTabContentHarness(): Promise<SkyTabContentHarness>`

Gets the `SkyTabContentHarness` controlled by this tab button.

#### Returns

`Promise<SkyTabContentHarness>`

#### `getTabHeading(): Promise<string>`

Gets the tab heading.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Gets whether the tab button is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Gets whether the tab button is disabled.

#### Returns

`Promise<boolean>`

#### `isInWizardTabset(): Promise<boolean>`

Whether the tab button is in a Wizard tabset.

#### Returns

`Promise<boolean>`

#### `SkyTabButtonHarness.with(filters: SkyTabButtonHarnessFilters): HarnessPredicate<SkyTabButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTabButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTabButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyTabButtonHarness>`

 SkyTabButtonHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTabButtonHarness` instances.

    interface SkyTabButtonHarnessFilters {
      tabHeading?: string;
    }

### Properties

#### `tabHeading?: string`

Finds tab button whose tab heading matches this value.

 SkyTabContentHarness
---------------------

Type: Class

`import { SkyTabContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a tab component in tests.

### Methods

#### `getLayout(): Promise<string>`

Gets the tab's layout.

#### Returns

`Promise<string>`

#### `isVisible(): Promise<boolean>`

Whether the tab content is visible.

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

 SkyTabContentHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTabContentHarness` instances.

    interface SkyTabContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTabsetNavButtonHarness
--------------------------

Type: Class

`import { SkyTabsetNavButtonHarness } from '@skyux/tabs/testing';`

Harness to interact with tabset nav buttons in wizard style tabset tests.

### Methods

#### `click(): Promise<void>`

Clicks the button.

#### Returns

`Promise<void>`

#### `getButtonText(): Promise<string>`

Gets the button text.

#### Returns

`Promise<string>`

#### `getButtonType(): Promise<null | SkyTabsetNavButtonType>`

Gets the button type.

#### Returns

`Promise<null | SkyTabsetNavButtonType>`

#### `isDisabled(): Promise<boolean>`

Whether the button is disabled.

#### Returns

`Promise<boolean>`

#### `SkyTabsetNavButtonHarness.with(filters: SkyTabsetNavButtonHarnessFilters): HarnessPredicate<SkyTabsetNavButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTabsetNavButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTabsetNavButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyTabsetNavButtonHarness>`

 SkyTabsetNavButtonHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTabsetNavButtonHarness` instances.

    interface SkyTabsetNavButtonHarnessFilters {
      buttonType?: SkyTabsetNavButtonType;
      dataSkyId?: string | RegExp;
    }

### Properties

#### `buttonType?: SkyTabsetNavButtonType`

Finds the tabset nav button whose `buttonType` matches the given value.

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
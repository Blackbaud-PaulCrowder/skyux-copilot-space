                  

 Tabs
====

Tabs divide and categorize large amounts of content on a page.

 Usage
------

### Use when

Use tabs when users require quick access to different slices of the same data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-usage-1.f1ae8612bac212d35c7d03c5a879a962.png)

Do use tabs to show different slices of the same data.

Use tabs when users need to complete different tasks on a page and each task includes a significant amount of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-usage-2.7f2854122d6462b231c4e305cbe5e229.png)

Do use tabs to group content for different tasks.

### Don't use when

Don't use tabs within another tab. Change the workflow instead of nesting multiple sets of tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-usage-3.f27513c44a2c15e605bf90030cd09bbe.png)

Don't use multiple sets of tabs on a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-usage-4.f159fd60cf85c5936d6cc647e5e61efc.png)

Don't combine vertical tabs and horizontal tabs.

Don't use tabs when they are likely to overflow the available horizontal space. The collapsed behavior of tabs will accommodate small screen resolutions or cases where users add many tabs themselves, but it is not intended as the default experience with a tabset. Use [vertical tabs](/skyux/components/vertical-tabs.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-usage-5.24a23cbec4d73f6c8e229c3db87074e6.png)

Don't use horizontal tabs when they are likely to overflow and collapse into a dropdown.

 Anatomy
--------

1

Selected tab

2

Unselected tab

3

Tab border

4

Tab panel

5

Close tab button (optional)

6

Add tab button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-anatomy.60311045d00db31cf6a944e82312cd11.png)

 Options
--------

### Add and close

If users need to work with a subset of tabs in a large tabset, let them add and close tabs to display only the relevant tabs.

If a new tab includes multiple options on what to display, use [action buttons](/skyux/components/action-button.md) in the tab view to let users make selections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-options-2.c402d51d22a56a153dae23a4c99ff0a6.png)

### Tab layouts

The following tab layouts can be used for organizing content within a tab panel.

#### Blocks

Use `blocks` tab layout for laying out blocks of content in a tab panel.

Place a [fluid grid](/skyux/components/fluid-grid.md) or other grid layouts via flexbox or CSS grid in page content area to acheive a large range of content layouts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-blocks.5ee71385e9fdc09a0576f7cbb917140b.png)

#### List

Use the `list` layout for lists of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-list.0fa4d3473687eb5bca352fb6bfa55b2e.png)

#### Fit

Use the `fit` layout for content to fill the content area and be anchored to the edges of the tab panel.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-fit.0dade380ec90d197adbde4b3cd19ca21.png)

#### None

Use the `none` layout for custom layouts and content within a tab panel.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-none.b10d7057d276beaa815c611e0040784d.png)

 Behavior and states
--------------------

### Overflowing tabs

If the tabset includes too many tabs to fit in the tab bar's available horizontal space, the tabs collapse into a dropdown.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-behavior-1.cfe4fc42fff057b65cf9b58a29010306.png)

### States

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-selected.3ccf2cbfbc21a1e9526874788b9086cb.png)

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-unselected.d15e75338c577a2cb7e32c709a9e8038.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-disabled.82be8822db8022128468d566387987e4.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-hover.6c59784be0ac9c2b91a2ad80a9905619.png)

Focus

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-focus.140044714b369f7a8b2db151150510c8.png)

Collapsed, closed

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-collapsed-closed.6e3492a87cd702257e321d5fb68993fe.png)

Collapsed, open

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-state-collapsed-open.98721b3b7af9d6473259324a2973e5fa.png)

 Layout
-------

### Tab order

Organize tabs according to the specific needs of the page or record, with the most important or commonly used tabs on the left. For example, organize [record page](/skyux/design/guidelines/page-layouts/record-page.md) tabs into four groups:

1.  Overview tab (optional)
2.  Context-specific tabs
3.  SKY Add-in tabs (optional)
4.  Common tabs (optional)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-content-record-page.8abef5147f291bdc6def74cfbecbe5fb.png)

Record pages use a standard order for tabs.

### Placement and spacing

Tabs are always the last (bottommost) content in their container. Don't put additional content under tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-1.b988840b53bbb4bdfd2b46bf58952b22.png)

Don't put additional content under tabs.

The tab border extends the full width of the container. Don't use left or right margins on the tab border, and ignore any padding that the container defines.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-2.45a3990dd7ea3f5a10b93e67d32c520d.png)

Do extend the tab border to the full width of the container.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-3.a8dae2ce4b203aa629203948d2ca76e0.png)

Don't apply the container's padding to the tab border.

Tab content does not have additional left or right padding. The left and right gutters align with the gutters for content outside the tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-layout-4.7ffbff42564c6ec19dce8c8d3b81fcd9.png)

Don't apply additional left or right padding to tab content.

 Content
--------

Use short, straightforward labels to clearly communicate the purpose of tabs. For consistency, use “Overview” when the first tab displays summary information. For example, use an Overview tab on [record pages](/skyux/design/guidelines/page-layouts/record-page.md) to display primary or identifying data and inform users about the current state and history of the record.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/tabs/tabs-content-1.a00795671908005b4239e86326931197.png)

 Related information
--------------------

### Components

*   [Action buttons](/skyux/components/action-button.md)
*   [Vertical tabs](/skyux/components/vertical-tabs.md)

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)

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
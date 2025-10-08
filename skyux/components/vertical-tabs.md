# Design

                  Skip to Main Content

 Vertical tabs
=============

Vertical tabs divide and categorize content on pages with a large number of categories.

 Usage
------

### Use when

Use vertical tabs when you expect horizontal tabs to exceed the available horizontal space because of the number of tabs or the length of tab labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-1.ab5393b2909b93f5cd5ad333976989d4.png)

Do use vertical tabs for a large number of tabs.

Use collapsible groups to organize vertical tabs that fit naturally into multiple categories.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-2.5c334f311d72443e51f3cbee081a5165.png)

Do use collapsible groups to organize vertical tabs into categories.

### Don't use when

Don't use vertical tabs when [horizontal tabs](/skyux/components/tabs.md) are appropriate. If the expected number of tabs is small and grouping is not necessary, use horizontal tabs instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-3.4c18c0e33181bf48fe71817e8d1c0584.png)

Don't use vertical tabs when you have enough space for horizontal tabs.

Don't use vertical tabs as containers for other tabs. Change the workflow instead of nesting multiple sets of tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-4.89f91dc11851633a2c4bdfb9d8f052cf.png)

Don't nest tabs within vertical tabs.

Don't use vertical tabs when the workflow requires users to view and perform actions on each tab. Use [split views](/skyux/components/split-view.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-5.eecad7fcf0cae57e34af6bd96848292e.png)

Don't use vertical tabs when users must interact with each tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-6.4f3dff14b4c1fc472dfdf168db985996.png)

Do use split views to display lists of items that users must work through.

Don't use vertical tabs in modals. Use [sectioned forms](/skyux/components/sectioned-form.md) instead. The two approaches look similar, but sectioned forms have additional features, such as displaying validation errors in form sections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-7.c424c6cb2a74d31dadab66066035a778.png)

Don't use vertical tabs in modals.

 Anatomy
--------

1

Vertical tabset

2

Unselected tab

3

Tab label

4

Selected tab

5

Tabset border

6

Selected tab group (optional)

7

Tab group label (optional)

8

Unselected tab group (optional)

9

Expand/collapse icon (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tab-anatomy.d88df03d2b5b866fbec8d934524b282d.png)

 Options
--------

### Collapsible groups

You can organize vertical tabs into collapsible groups when the categories help users.

 Behavior and states
--------------------

### States

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected.939f5d5a6b0d11a40ab9f39a45130095.png)

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected.fc25d03952a0b1708c66dd4f7dacbff6.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-disabled.d1eeb1d2046474c9013692e860e3a6ce.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-hover.a00f3c73310f0bd4419bad2557e7b936.png)

Group with selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected-group.2bf119997f3fb7adc57fde1dd459f7ba.png)

Group without selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected-group.18c6d9d74f8e54fc99af7d0f929c0524.png)

 Layout
-------

Vertical tabs are always the bottom-most content in their containers. Don't include additional content after vertical tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-layout-1.0747aee525204c91557b6ac9aa39d131.png)

Don't include content after vertical tabs.

 Related information
--------------------

### Components

*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/vertical-tabset/vertical-tabset.module.ts#L41) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkyVerticalTabsetModule
------------------------

Type: Module

`import { SkyVerticalTabsetModule } from '@skyux/tabs';`

 SkyVerticalTabsetComponent
---------------------------

Type: Component

Selector: `sky-vertical-tabset`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tablist` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tablist`.

The ARIA role for the vertical tabset [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tabset functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tablist"`

#### `maintainTabContent: boolean | undefined`

Whether the vertical tabset loads tab content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `showTabsText: string | undefined`

The text to display on the show tabs button on mobile devices.

### Outputs

#### `activeChange: EventEmitter<number>`

Fires when the active tab changes. Emits the index of the active tab. The index is based on the tab's position when it loads.

 SkyVerticalTabComponent
------------------------

Type: Component

Selector: `sky-vertical-tab`

### Inputs

#### `tabHeading: string | undefined`

Required

The tab header.

#### `active: boolean`

Whether the tab is active when the tabset loads.

Default: `false`

#### `ariaControls: string | undefined`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The HTML element ID of the element that contains the content that the vertical tab displays, which corresponds to the `tabId`. This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure). For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tab` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tab`.

The ARIA role for the vertical tab [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tab functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tab"`

#### `disabled: boolean | undefined`

Whether to disable the tab.

Default: `false`

#### `tabHeaderCount: number | undefined`

Displays an item count alongside the tab header to indicate how many list items the tab contains.

#### `tabId: string`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The ID for the tab.

 SkyVerticalTabsetGroupComponent
--------------------------------

Type: Component

Selector: `sky-vertical-tabset-group`

### Inputs

#### `disabled: boolean | undefined`

Whether to disable the ability to expand and collapse the group.

Default: `false`

#### `groupHeading: string | undefined`

The header for the collapsible group of tabs.

#### `open: boolean | undefined`

Whether the collapsible group is expanded.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyVerticalTabsetHarness
-------------------------

Type: Class

`import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';`

Harness for interacting with the vertical tabset component in tests.

### Methods

#### `clickShowTabsButton(): Promise<void>`

Click the show tabs button in mobile view.

#### Returns

`Promise<void>`

#### `getActiveTab(): Promise<undefined | SkyVerticalTabButtonHarness>`

Gets the `SkyVerticalTabButtonHarness` of the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabButtonHarness>`

#### `getActiveTabContent(): Promise<undefined | SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabContentHarness>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getGroup(filters: SkyVerticalTabsetGroupHarnessFilters): Promise<undefined | SkyVerticalTabsetGroupHarness>`

Gets a specific vertical tabset group based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

The filter criteria.

#### Returns

`Promise<undefined | SkyVerticalTabsetGroupHarness>`

#### `getGroups(filters?: SkyVerticalTabsetGroupHarnessFilters): Promise<SkyVerticalTabsetGroupHarness[]>`

Gets an array of vertical tabset groups based on the filter criteria. If no filter is provided, returns all vertical tabset groups.

#### Parameters

##### `filters?: SkyVerticalTabsetGroupHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabsetGroupHarness[]>`

#### `getShowTabsText(): Promise<undefined | string>`

Gets the text in the show tabs button in mobile view.

#### Returns

`Promise<undefined | string>`

#### `getTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab button based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isTabsVisible(): Promise<boolean>`

Whether the tabs are visible. In mobile view, vertical tabsets collapse to just the content pane with a button to show the tabs.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetHarness.with(filters: SkyVerticalTabsetHarnessFilters): HarnessPredicate<SkyVerticalTabsetHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetHarness>`

 SkyVerticalTabsetHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

    interface SkyVerticalTabsetHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyVerticalTabsetGroupHarness
------------------------------

Type: Class

`import { SkyVerticalTabsetGroupHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tabset group in tests.

### Methods

#### `click(): Promise<void>`

Clicks the group button to toggle its expanded state.

#### Returns

`Promise<void>`

#### `getGroupHeading(): Promise<string>`

Gets the group heading text.

#### Returns

`Promise<string>`

#### `getVerticalTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getVerticalTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isActive(): Promise<boolean>`

Whether a tab under this group is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the group is disabled.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the group is expanded.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetGroupHarness.with(filters: SkyVerticalTabsetGroupHarnessFilters): HarnessPredicate<SkyVerticalTabsetGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetGroupHarness>`

 SkyVerticalTabsetGroupHarnessFilters
-------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetGroupHarness` instances.

    interface SkyVerticalTabsetGroupHarnessFilters {
      dataSkyId?: string | RegExp;
      groupHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `groupHeading?: string`

Find tabset groups whose heading matches the given value.

 SkyVerticalTabButtonHarness
----------------------------

Type: Class

`import { SkyVerticalTabButtonHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab button in tests.

### Methods

#### `click(): Promise<void>`

Clicks the tab button to activate the tab.

#### Returns

`Promise<void>`

#### `getTabContent(): Promise<SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for this tab.

#### Returns

`Promise<SkyVerticalTabContentHarness>`

#### `getTabHeaderCount(): Promise<number>`

Gets the tab header count.

#### Returns

`Promise<number>`

#### `getTabHeading(): Promise<string>`

Gets the tab heading text.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the tab is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the tab is disabled.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabButtonHarness.with(filters: SkyVerticalTabButtonHarnessFilters): HarnessPredicate<SkyVerticalTabButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabButtonHarness>`

 SkyVerticalTabButtonHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabButtonHarness` instances.

    interface SkyVerticalTabButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      tabHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `tabHeading?: string`

Find a tab whose heading matches the given value.

 SkyVerticalTabContentHarness
-----------------------------

Type: Class

`import { SkyVerticalTabContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab content in tests.

### Methods

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

#### `SkyVerticalTabContentHarness.with(filters: SkyVerticalTabContentHarnessFilters): HarnessPredicate<SkyVerticalTabContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabContentHarness>`

 SkyVerticalTabContentHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabContentHarness` instances.

    interface SkyVerticalTabContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Vertical tabs
=============

Vertical tabs divide and categorize content on pages with a large number of categories.

 Usage
------

### Use when

Use vertical tabs when you expect horizontal tabs to exceed the available horizontal space because of the number of tabs or the length of tab labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-1.ab5393b2909b93f5cd5ad333976989d4.png)

Do use vertical tabs for a large number of tabs.

Use collapsible groups to organize vertical tabs that fit naturally into multiple categories.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-2.5c334f311d72443e51f3cbee081a5165.png)

Do use collapsible groups to organize vertical tabs into categories.

### Don't use when

Don't use vertical tabs when [horizontal tabs](/skyux/components/tabs.md) are appropriate. If the expected number of tabs is small and grouping is not necessary, use horizontal tabs instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-3.4c18c0e33181bf48fe71817e8d1c0584.png)

Don't use vertical tabs when you have enough space for horizontal tabs.

Don't use vertical tabs as containers for other tabs. Change the workflow instead of nesting multiple sets of tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-4.89f91dc11851633a2c4bdfb9d8f052cf.png)

Don't nest tabs within vertical tabs.

Don't use vertical tabs when the workflow requires users to view and perform actions on each tab. Use [split views](/skyux/components/split-view.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-5.eecad7fcf0cae57e34af6bd96848292e.png)

Don't use vertical tabs when users must interact with each tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-6.4f3dff14b4c1fc472dfdf168db985996.png)

Do use split views to display lists of items that users must work through.

Don't use vertical tabs in modals. Use [sectioned forms](/skyux/components/sectioned-form.md) instead. The two approaches look similar, but sectioned forms have additional features, such as displaying validation errors in form sections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-7.c424c6cb2a74d31dadab66066035a778.png)

Don't use vertical tabs in modals.

 Anatomy
--------

1

Vertical tabset

2

Unselected tab

3

Tab label

4

Selected tab

5

Tabset border

6

Selected tab group (optional)

7

Tab group label (optional)

8

Unselected tab group (optional)

9

Expand/collapse icon (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tab-anatomy.d88df03d2b5b866fbec8d934524b282d.png)

 Options
--------

### Collapsible groups

You can organize vertical tabs into collapsible groups when the categories help users.

 Behavior and states
--------------------

### States

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected.939f5d5a6b0d11a40ab9f39a45130095.png)

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected.fc25d03952a0b1708c66dd4f7dacbff6.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-disabled.d1eeb1d2046474c9013692e860e3a6ce.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-hover.a00f3c73310f0bd4419bad2557e7b936.png)

Group with selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected-group.2bf119997f3fb7adc57fde1dd459f7ba.png)

Group without selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected-group.18c6d9d74f8e54fc99af7d0f929c0524.png)

 Layout
-------

Vertical tabs are always the bottom-most content in their containers. Don't include additional content after vertical tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-layout-1.0747aee525204c91557b6ac9aa39d131.png)

Don't include content after vertical tabs.

 Related information
--------------------

### Components

*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/vertical-tabset/vertical-tabset.module.ts#L41) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkyVerticalTabsetModule
------------------------

Type: Module

`import { SkyVerticalTabsetModule } from '@skyux/tabs';`

 SkyVerticalTabsetComponent
---------------------------

Type: Component

Selector: `sky-vertical-tabset`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tablist` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tablist`.

The ARIA role for the vertical tabset [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tabset functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tablist"`

#### `maintainTabContent: boolean | undefined`

Whether the vertical tabset loads tab content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `showTabsText: string | undefined`

The text to display on the show tabs button on mobile devices.

### Outputs

#### `activeChange: EventEmitter<number>`

Fires when the active tab changes. Emits the index of the active tab. The index is based on the tab's position when it loads.

 SkyVerticalTabComponent
------------------------

Type: Component

Selector: `sky-vertical-tab`

### Inputs

#### `tabHeading: string | undefined`

Required

The tab header.

#### `active: boolean`

Whether the tab is active when the tabset loads.

Default: `false`

#### `ariaControls: string | undefined`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The HTML element ID of the element that contains the content that the vertical tab displays, which corresponds to the `tabId`. This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure). For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tab` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tab`.

The ARIA role for the vertical tab [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tab functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tab"`

#### `disabled: boolean | undefined`

Whether to disable the tab.

Default: `false`

#### `tabHeaderCount: number | undefined`

Displays an item count alongside the tab header to indicate how many list items the tab contains.

#### `tabId: string`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The ID for the tab.

 SkyVerticalTabsetGroupComponent
--------------------------------

Type: Component

Selector: `sky-vertical-tabset-group`

### Inputs

#### `disabled: boolean | undefined`

Whether to disable the ability to expand and collapse the group.

Default: `false`

#### `groupHeading: string | undefined`

The header for the collapsible group of tabs.

#### `open: boolean | undefined`

Whether the collapsible group is expanded.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyVerticalTabsetHarness
-------------------------

Type: Class

`import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';`

Harness for interacting with the vertical tabset component in tests.

### Methods

#### `clickShowTabsButton(): Promise<void>`

Click the show tabs button in mobile view.

#### Returns

`Promise<void>`

#### `getActiveTab(): Promise<undefined | SkyVerticalTabButtonHarness>`

Gets the `SkyVerticalTabButtonHarness` of the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabButtonHarness>`

#### `getActiveTabContent(): Promise<undefined | SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabContentHarness>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getGroup(filters: SkyVerticalTabsetGroupHarnessFilters): Promise<undefined | SkyVerticalTabsetGroupHarness>`

Gets a specific vertical tabset group based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

The filter criteria.

#### Returns

`Promise<undefined | SkyVerticalTabsetGroupHarness>`

#### `getGroups(filters?: SkyVerticalTabsetGroupHarnessFilters): Promise<SkyVerticalTabsetGroupHarness[]>`

Gets an array of vertical tabset groups based on the filter criteria. If no filter is provided, returns all vertical tabset groups.

#### Parameters

##### `filters?: SkyVerticalTabsetGroupHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabsetGroupHarness[]>`

#### `getShowTabsText(): Promise<undefined | string>`

Gets the text in the show tabs button in mobile view.

#### Returns

`Promise<undefined | string>`

#### `getTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab button based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isTabsVisible(): Promise<boolean>`

Whether the tabs are visible. In mobile view, vertical tabsets collapse to just the content pane with a button to show the tabs.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetHarness.with(filters: SkyVerticalTabsetHarnessFilters): HarnessPredicate<SkyVerticalTabsetHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetHarness>`

 SkyVerticalTabsetHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

    interface SkyVerticalTabsetHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyVerticalTabsetGroupHarness
------------------------------

Type: Class

`import { SkyVerticalTabsetGroupHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tabset group in tests.

### Methods

#### `click(): Promise<void>`

Clicks the group button to toggle its expanded state.

#### Returns

`Promise<void>`

#### `getGroupHeading(): Promise<string>`

Gets the group heading text.

#### Returns

`Promise<string>`

#### `getVerticalTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getVerticalTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isActive(): Promise<boolean>`

Whether a tab under this group is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the group is disabled.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the group is expanded.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetGroupHarness.with(filters: SkyVerticalTabsetGroupHarnessFilters): HarnessPredicate<SkyVerticalTabsetGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetGroupHarness>`

 SkyVerticalTabsetGroupHarnessFilters
-------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetGroupHarness` instances.

    interface SkyVerticalTabsetGroupHarnessFilters {
      dataSkyId?: string | RegExp;
      groupHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `groupHeading?: string`

Find tabset groups whose heading matches the given value.

 SkyVerticalTabButtonHarness
----------------------------

Type: Class

`import { SkyVerticalTabButtonHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab button in tests.

### Methods

#### `click(): Promise<void>`

Clicks the tab button to activate the tab.

#### Returns

`Promise<void>`

#### `getTabContent(): Promise<SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for this tab.

#### Returns

`Promise<SkyVerticalTabContentHarness>`

#### `getTabHeaderCount(): Promise<number>`

Gets the tab header count.

#### Returns

`Promise<number>`

#### `getTabHeading(): Promise<string>`

Gets the tab heading text.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the tab is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the tab is disabled.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabButtonHarness.with(filters: SkyVerticalTabButtonHarnessFilters): HarnessPredicate<SkyVerticalTabButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabButtonHarness>`

 SkyVerticalTabButtonHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabButtonHarness` instances.

    interface SkyVerticalTabButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      tabHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `tabHeading?: string`

Find a tab whose heading matches the given value.

 SkyVerticalTabContentHarness
-----------------------------

Type: Class

`import { SkyVerticalTabContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab content in tests.

### Methods

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

#### `SkyVerticalTabContentHarness.with(filters: SkyVerticalTabContentHarnessFilters): HarnessPredicate<SkyVerticalTabContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabContentHarness>`

 SkyVerticalTabContentHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabContentHarness` instances.

    interface SkyVerticalTabContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                  Skip to Main Content

 Vertical tabs
=============

Vertical tabs divide and categorize content on pages with a large number of categories.

 Usage
------

### Use when

Use vertical tabs when you expect horizontal tabs to exceed the available horizontal space because of the number of tabs or the length of tab labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-1.ab5393b2909b93f5cd5ad333976989d4.png)

Do use vertical tabs for a large number of tabs.

Use collapsible groups to organize vertical tabs that fit naturally into multiple categories.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-2.5c334f311d72443e51f3cbee081a5165.png)

Do use collapsible groups to organize vertical tabs into categories.

### Don't use when

Don't use vertical tabs when [horizontal tabs](/skyux/components/tabs.md) are appropriate. If the expected number of tabs is small and grouping is not necessary, use horizontal tabs instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-3.4c18c0e33181bf48fe71817e8d1c0584.png)

Don't use vertical tabs when you have enough space for horizontal tabs.

Don't use vertical tabs as containers for other tabs. Change the workflow instead of nesting multiple sets of tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-4.89f91dc11851633a2c4bdfb9d8f052cf.png)

Don't nest tabs within vertical tabs.

Don't use vertical tabs when the workflow requires users to view and perform actions on each tab. Use [split views](/skyux/components/split-view.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-5.eecad7fcf0cae57e34af6bd96848292e.png)

Don't use vertical tabs when users must interact with each tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-6.4f3dff14b4c1fc472dfdf168db985996.png)

Do use split views to display lists of items that users must work through.

Don't use vertical tabs in modals. Use [sectioned forms](/skyux/components/sectioned-form.md) instead. The two approaches look similar, but sectioned forms have additional features, such as displaying validation errors in form sections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-7.c424c6cb2a74d31dadab66066035a778.png)

Don't use vertical tabs in modals.

 Anatomy
--------

1

Vertical tabset

2

Unselected tab

3

Tab label

4

Selected tab

5

Tabset border

6

Selected tab group (optional)

7

Tab group label (optional)

8

Unselected tab group (optional)

9

Expand/collapse icon (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tab-anatomy.d88df03d2b5b866fbec8d934524b282d.png)

 Options
--------

### Collapsible groups

You can organize vertical tabs into collapsible groups when the categories help users.

 Behavior and states
--------------------

### States

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected.939f5d5a6b0d11a40ab9f39a45130095.png)

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected.fc25d03952a0b1708c66dd4f7dacbff6.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-disabled.d1eeb1d2046474c9013692e860e3a6ce.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-hover.a00f3c73310f0bd4419bad2557e7b936.png)

Group with selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected-group.2bf119997f3fb7adc57fde1dd459f7ba.png)

Group without selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected-group.18c6d9d74f8e54fc99af7d0f929c0524.png)

 Layout
-------

Vertical tabs are always the bottom-most content in their containers. Don't include additional content after vertical tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-layout-1.0747aee525204c91557b6ac9aa39d131.png)

Don't include content after vertical tabs.

 Related information
--------------------

### Components

*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/vertical-tabset/vertical-tabset.module.ts#L41) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkyVerticalTabsetModule
------------------------

Type: Module

`import { SkyVerticalTabsetModule } from '@skyux/tabs';`

 SkyVerticalTabsetComponent
---------------------------

Type: Component

Selector: `sky-vertical-tabset`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tablist` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tablist`.

The ARIA role for the vertical tabset [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tabset functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tablist"`

#### `maintainTabContent: boolean | undefined`

Whether the vertical tabset loads tab content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `showTabsText: string | undefined`

The text to display on the show tabs button on mobile devices.

### Outputs

#### `activeChange: EventEmitter<number>`

Fires when the active tab changes. Emits the index of the active tab. The index is based on the tab's position when it loads.

 SkyVerticalTabComponent
------------------------

Type: Component

Selector: `sky-vertical-tab`

### Inputs

#### `tabHeading: string | undefined`

Required

The tab header.

#### `active: boolean`

Whether the tab is active when the tabset loads.

Default: `false`

#### `ariaControls: string | undefined`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The HTML element ID of the element that contains the content that the vertical tab displays, which corresponds to the `tabId`. This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure). For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tab` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tab`.

The ARIA role for the vertical tab [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tab functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tab"`

#### `disabled: boolean | undefined`

Whether to disable the tab.

Default: `false`

#### `tabHeaderCount: number | undefined`

Displays an item count alongside the tab header to indicate how many list items the tab contains.

#### `tabId: string`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The ID for the tab.

 SkyVerticalTabsetGroupComponent
--------------------------------

Type: Component

Selector: `sky-vertical-tabset-group`

### Inputs

#### `disabled: boolean | undefined`

Whether to disable the ability to expand and collapse the group.

Default: `false`

#### `groupHeading: string | undefined`

The header for the collapsible group of tabs.

#### `open: boolean | undefined`

Whether the collapsible group is expanded.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyVerticalTabsetHarness
-------------------------

Type: Class

`import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';`

Harness for interacting with the vertical tabset component in tests.

### Methods

#### `clickShowTabsButton(): Promise<void>`

Click the show tabs button in mobile view.

#### Returns

`Promise<void>`

#### `getActiveTab(): Promise<undefined | SkyVerticalTabButtonHarness>`

Gets the `SkyVerticalTabButtonHarness` of the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabButtonHarness>`

#### `getActiveTabContent(): Promise<undefined | SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabContentHarness>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getGroup(filters: SkyVerticalTabsetGroupHarnessFilters): Promise<undefined | SkyVerticalTabsetGroupHarness>`

Gets a specific vertical tabset group based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

The filter criteria.

#### Returns

`Promise<undefined | SkyVerticalTabsetGroupHarness>`

#### `getGroups(filters?: SkyVerticalTabsetGroupHarnessFilters): Promise<SkyVerticalTabsetGroupHarness[]>`

Gets an array of vertical tabset groups based on the filter criteria. If no filter is provided, returns all vertical tabset groups.

#### Parameters

##### `filters?: SkyVerticalTabsetGroupHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabsetGroupHarness[]>`

#### `getShowTabsText(): Promise<undefined | string>`

Gets the text in the show tabs button in mobile view.

#### Returns

`Promise<undefined | string>`

#### `getTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab button based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isTabsVisible(): Promise<boolean>`

Whether the tabs are visible. In mobile view, vertical tabsets collapse to just the content pane with a button to show the tabs.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetHarness.with(filters: SkyVerticalTabsetHarnessFilters): HarnessPredicate<SkyVerticalTabsetHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetHarness>`

 SkyVerticalTabsetHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

    interface SkyVerticalTabsetHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyVerticalTabsetGroupHarness
------------------------------

Type: Class

`import { SkyVerticalTabsetGroupHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tabset group in tests.

### Methods

#### `click(): Promise<void>`

Clicks the group button to toggle its expanded state.

#### Returns

`Promise<void>`

#### `getGroupHeading(): Promise<string>`

Gets the group heading text.

#### Returns

`Promise<string>`

#### `getVerticalTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getVerticalTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isActive(): Promise<boolean>`

Whether a tab under this group is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the group is disabled.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the group is expanded.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetGroupHarness.with(filters: SkyVerticalTabsetGroupHarnessFilters): HarnessPredicate<SkyVerticalTabsetGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetGroupHarness>`

 SkyVerticalTabsetGroupHarnessFilters
-------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetGroupHarness` instances.

    interface SkyVerticalTabsetGroupHarnessFilters {
      dataSkyId?: string | RegExp;
      groupHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `groupHeading?: string`

Find tabset groups whose heading matches the given value.

 SkyVerticalTabButtonHarness
----------------------------

Type: Class

`import { SkyVerticalTabButtonHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab button in tests.

### Methods

#### `click(): Promise<void>`

Clicks the tab button to activate the tab.

#### Returns

`Promise<void>`

#### `getTabContent(): Promise<SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for this tab.

#### Returns

`Promise<SkyVerticalTabContentHarness>`

#### `getTabHeaderCount(): Promise<number>`

Gets the tab header count.

#### Returns

`Promise<number>`

#### `getTabHeading(): Promise<string>`

Gets the tab heading text.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the tab is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the tab is disabled.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabButtonHarness.with(filters: SkyVerticalTabButtonHarnessFilters): HarnessPredicate<SkyVerticalTabButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabButtonHarness>`

 SkyVerticalTabButtonHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabButtonHarness` instances.

    interface SkyVerticalTabButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      tabHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `tabHeading?: string`

Find a tab whose heading matches the given value.

 SkyVerticalTabContentHarness
-----------------------------

Type: Class

`import { SkyVerticalTabContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab content in tests.

### Methods

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

#### `SkyVerticalTabContentHarness.with(filters: SkyVerticalTabContentHarnessFilters): HarnessPredicate<SkyVerticalTabContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabContentHarness>`

 SkyVerticalTabContentHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabContentHarness` instances.

    interface SkyVerticalTabContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Testing

                  Skip to Main Content

 Vertical tabs
=============

Vertical tabs divide and categorize content on pages with a large number of categories.

 Usage
------

### Use when

Use vertical tabs when you expect horizontal tabs to exceed the available horizontal space because of the number of tabs or the length of tab labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-1.ab5393b2909b93f5cd5ad333976989d4.png)

Do use vertical tabs for a large number of tabs.

Use collapsible groups to organize vertical tabs that fit naturally into multiple categories.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-2.5c334f311d72443e51f3cbee081a5165.png)

Do use collapsible groups to organize vertical tabs into categories.

### Don't use when

Don't use vertical tabs when [horizontal tabs](/skyux/components/tabs.md) are appropriate. If the expected number of tabs is small and grouping is not necessary, use horizontal tabs instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-3.4c18c0e33181bf48fe71817e8d1c0584.png)

Don't use vertical tabs when you have enough space for horizontal tabs.

Don't use vertical tabs as containers for other tabs. Change the workflow instead of nesting multiple sets of tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-4.89f91dc11851633a2c4bdfb9d8f052cf.png)

Don't nest tabs within vertical tabs.

Don't use vertical tabs when the workflow requires users to view and perform actions on each tab. Use [split views](/skyux/components/split-view.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-5.eecad7fcf0cae57e34af6bd96848292e.png)

Don't use vertical tabs when users must interact with each tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-6.4f3dff14b4c1fc472dfdf168db985996.png)

Do use split views to display lists of items that users must work through.

Don't use vertical tabs in modals. Use [sectioned forms](/skyux/components/sectioned-form.md) instead. The two approaches look similar, but sectioned forms have additional features, such as displaying validation errors in form sections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-usage-7.c424c6cb2a74d31dadab66066035a778.png)

Don't use vertical tabs in modals.

 Anatomy
--------

1

Vertical tabset

2

Unselected tab

3

Tab label

4

Selected tab

5

Tabset border

6

Selected tab group (optional)

7

Tab group label (optional)

8

Unselected tab group (optional)

9

Expand/collapse icon (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tab-anatomy.d88df03d2b5b866fbec8d934524b282d.png)

 Options
--------

### Collapsible groups

You can organize vertical tabs into collapsible groups when the categories help users.

 Behavior and states
--------------------

### States

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected.939f5d5a6b0d11a40ab9f39a45130095.png)

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected.fc25d03952a0b1708c66dd4f7dacbff6.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-disabled.d1eeb1d2046474c9013692e860e3a6ce.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-hover.a00f3c73310f0bd4419bad2557e7b936.png)

Group with selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-selected-group.2bf119997f3fb7adc57fde1dd459f7ba.png)

Group without selected tab

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-state-unselected-group.18c6d9d74f8e54fc99af7d0f929c0524.png)

 Layout
-------

Vertical tabs are always the bottom-most content in their containers. Don't include additional content after vertical tabs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/vertical-tabs/vertical-tabs-layout-1.0747aee525204c91557b6ac9aa39d131.png)

Don't include content after vertical tabs.

 Related information
--------------------

### Components

*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Split view](/skyux/components/split-view.md)
*   [Tabs](/skyux/components/tabs.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/vertical-tabset/vertical-tabset.module.ts#L41) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkyVerticalTabsetModule
------------------------

Type: Module

`import { SkyVerticalTabsetModule } from '@skyux/tabs';`

 SkyVerticalTabsetComponent
---------------------------

Type: Component

Selector: `sky-vertical-tabset`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the tabset does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tablist` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tablist`.

The ARIA role for the vertical tabset [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tabset functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tablist"`

#### `maintainTabContent: boolean | undefined`

Whether the vertical tabset loads tab content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `showTabsText: string | undefined`

The text to display on the show tabs button on mobile devices.

### Outputs

#### `activeChange: EventEmitter<number>`

Fires when the active tab changes. Emits the index of the active tab. The index is based on the tab's position when it loads.

 SkyVerticalTabComponent
------------------------

Type: Component

Selector: `sky-vertical-tab`

### Inputs

#### `tabHeading: string | undefined`

Required

The tab header.

#### `active: boolean`

Whether the tab is active when the tabset loads.

Default: `false`

#### `ariaControls: string | undefined`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The HTML element ID of the element that contains the content that the vertical tab displays, which corresponds to the `tabId`. This property [supports accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure). For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).

#### `ariaRole: string`

Warning: **Deprecated.** Any other value than `tab` could lead to a poor user experience for users with assistive technology. In the next major version, this property will be automatically set to `tab`.

The ARIA role for the vertical tab [to support accessibility](/skyux/learn/accessibility.md) by indicating how the tab functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

Default: `"tab"`

#### `disabled: boolean | undefined`

Whether to disable the tab.

Default: `false`

#### `tabHeaderCount: number | undefined`

Displays an item count alongside the tab header to indicate how many list items the tab contains.

#### `tabId: string`

Warning: **Deprecated.** Now that the vertical tabs provide aria labels automatically, this input is no longer necessary.

The ID for the tab.

 SkyVerticalTabsetGroupComponent
--------------------------------

Type: Component

Selector: `sky-vertical-tabset-group`

### Inputs

#### `disabled: boolean | undefined`

Whether to disable the ability to expand and collapse the group.

Default: `false`

#### `groupHeading: string | undefined`

The header for the collapsible group of tabs.

#### `open: boolean | undefined`

Whether the collapsible group is expanded.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyVerticalTabsetHarness
-------------------------

Type: Class

`import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';`

Harness for interacting with the vertical tabset component in tests.

### Methods

#### `clickShowTabsButton(): Promise<void>`

Click the show tabs button in mobile view.

#### Returns

`Promise<void>`

#### `getActiveTab(): Promise<undefined | SkyVerticalTabButtonHarness>`

Gets the `SkyVerticalTabButtonHarness` of the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabButtonHarness>`

#### `getActiveTabContent(): Promise<undefined | SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for the currently active tab.

#### Returns

`Promise<undefined | SkyVerticalTabContentHarness>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getGroup(filters: SkyVerticalTabsetGroupHarnessFilters): Promise<undefined | SkyVerticalTabsetGroupHarness>`

Gets a specific vertical tabset group based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

The filter criteria.

#### Returns

`Promise<undefined | SkyVerticalTabsetGroupHarness>`

#### `getGroups(filters?: SkyVerticalTabsetGroupHarnessFilters): Promise<SkyVerticalTabsetGroupHarness[]>`

Gets an array of vertical tabset groups based on the filter criteria. If no filter is provided, returns all vertical tabset groups.

#### Parameters

##### `filters?: SkyVerticalTabsetGroupHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabsetGroupHarness[]>`

#### `getShowTabsText(): Promise<undefined | string>`

Gets the text in the show tabs button in mobile view.

#### Returns

`Promise<undefined | string>`

#### `getTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab button based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isTabsVisible(): Promise<boolean>`

Whether the tabs are visible. In mobile view, vertical tabsets collapse to just the content pane with a button to show the tabs.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetHarness.with(filters: SkyVerticalTabsetHarnessFilters): HarnessPredicate<SkyVerticalTabsetHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetHarness>`

 SkyVerticalTabsetHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

    interface SkyVerticalTabsetHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyVerticalTabsetGroupHarness
------------------------------

Type: Class

`import { SkyVerticalTabsetGroupHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tabset group in tests.

### Methods

#### `click(): Promise<void>`

Clicks the group button to toggle its expanded state.

#### Returns

`Promise<void>`

#### `getGroupHeading(): Promise<string>`

Gets the group heading text.

#### Returns

`Promise<string>`

#### `getVerticalTab(filters: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness>`

Gets a specific vertical tab based on the filter criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness>`

#### `getVerticalTabs(filters?: SkyVerticalTabButtonHarnessFilters): Promise<SkyVerticalTabButtonHarness[]>`

Gets an array of vertical tab buttons based on the filter criteria. If no filter is provided, returns all vertical tab buttons.

#### Parameters

##### `filters?: SkyVerticalTabButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyVerticalTabButtonHarness[]>`

#### `isActive(): Promise<boolean>`

Whether a tab under this group is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the group is disabled.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the group is expanded.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabsetGroupHarness.with(filters: SkyVerticalTabsetGroupHarnessFilters): HarnessPredicate<SkyVerticalTabsetGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabsetGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabsetGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabsetGroupHarness>`

 SkyVerticalTabsetGroupHarnessFilters
-------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabsetGroupHarness` instances.

    interface SkyVerticalTabsetGroupHarnessFilters {
      dataSkyId?: string | RegExp;
      groupHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `groupHeading?: string`

Find tabset groups whose heading matches the given value.

 SkyVerticalTabButtonHarness
----------------------------

Type: Class

`import { SkyVerticalTabButtonHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab button in tests.

### Methods

#### `click(): Promise<void>`

Clicks the tab button to activate the tab.

#### Returns

`Promise<void>`

#### `getTabContent(): Promise<SkyVerticalTabContentHarness>`

Gets the `SkyVerticalTabContentHarness` for this tab.

#### Returns

`Promise<SkyVerticalTabContentHarness>`

#### `getTabHeaderCount(): Promise<number>`

Gets the tab header count.

#### Returns

`Promise<number>`

#### `getTabHeading(): Promise<string>`

Gets the tab heading text.

#### Returns

`Promise<string>`

#### `isActive(): Promise<boolean>`

Whether the tab is active.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the tab is disabled.

#### Returns

`Promise<boolean>`

#### `SkyVerticalTabButtonHarness.with(filters: SkyVerticalTabButtonHarnessFilters): HarnessPredicate<SkyVerticalTabButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabButtonHarness>`

 SkyVerticalTabButtonHarnessFilters
-----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabButtonHarness` instances.

    interface SkyVerticalTabButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      tabHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `tabHeading?: string`

Find a tab whose heading matches the given value.

 SkyVerticalTabContentHarness
-----------------------------

Type: Class

`import { SkyVerticalTabContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a vertical tab content in tests.

### Methods

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

#### `SkyVerticalTabContentHarness.with(filters: SkyVerticalTabContentHarnessFilters): HarnessPredicate<SkyVerticalTabContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyVerticalTabContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyVerticalTabContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyVerticalTabContentHarness>`

 SkyVerticalTabContentHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyVerticalTabContentHarness` instances.

    interface SkyVerticalTabContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
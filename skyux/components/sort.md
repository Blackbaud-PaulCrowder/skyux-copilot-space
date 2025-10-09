                      

 Sort
====

The sort button and menu let users select sorting criteria.

 Usage
------

### Use when

Use to sort a list of items when there are templated columns in a list. This provides a way for users to sort templated columns because there are no corresponding column headings.

Use to sort a list of items when the list includes other views in addition to the data grid (e.g., repeater). This allows users to sort in these other views using the sort menu.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/sort/sort-multiple-view-sort.b7e9a8d84bf47c2056bc8eee44b8b1b9.png)

Do use a sort button when there are other views of the data, in addition to a data grid, to support sorting in those views (without column headers).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/sort/sort-templated-sort.4f5b671e1bd43bcc34b1293f037edd54.png)

Do use a sort button when there are templated columns to provide sort options for multiple properties within a single templated column (e.g., First name and last name).

### Don't use when

Do not include an additional sort button in the toolbar for a list when only data grid view is available. Column headers provide sorting in this case.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/sort/sort-double-sort.86c7a71865afdbd649cd0c88321a51c6.png)

Don't use a sort button if the list only uses data grid view and not templated columns. Rely on column headers for sorting.

 Anatomy
--------

1

Sort button

2

Sort by menu

3

Selected menu option

4

Menu option

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/sort/sort-anatomy.0bb0172277fbc4eaeaf35ebca2b57957.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Repeater](/skyux/components/repeater.md)
*   [Toolbar](/skyux/components/toolbar.md)

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/sort/sort.module.ts#L30) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkySortModule
--------------

Type: Module

`import { SkySortModule } from '@skyux/lists';`

 SkySortComponent
-----------------

Type: Component

Selector: `sky-sort`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the sort button. This sets the sort button's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Sort constituents." Context is especially important when multiple filter buttons are in close proximity. In toolbars, sort buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Sort <listDescriptor>." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `showButtonText: boolean | undefined`

Whether to display a "Sort" label beside the icon on the sort button.

Default: `false`

 SkySortItemComponent
---------------------

Type: Component

Selector: `sky-sort-item`

### Inputs

#### `active: boolean | undefined`

Whether the sorting option is active.

### Outputs

#### `itemSelect: EventEmitter<any>`

Fires when a sort item is selected.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySortHarness
---------------

Type: Class

`import { SkySortHarness } from '@skyux/lists/testing';`

Harness for interacting with a sort component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the sort component.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label value.

#### Returns

`Promise<null | string>`

#### `getButtonText(): Promise<string>`

Gets the text that appears on the sort button.

#### Returns

`Promise<string>`

#### `getItem(filters: SkySortItemHarnessFilters): Promise<SkySortItemHarness>`

Gets a specific sort item based on the filter criteria.

#### Parameters

##### `filters: SkySortItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySortItemHarness>`

#### `getItems(filters?: SkySortItemHarnessFilters): Promise<SkySortItemHarness[]>`

Gets an array of sort items based on the filter criteria. If no filter is provided, returns all sort items.

#### Parameters

##### `filters?: SkySortItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySortItemHarness[]>`

#### `SkySortHarness.with(filters: SkySortHarnessFilters): HarnessPredicate<SkySortHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySortHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySortHarnessFilters`

#### Returns

`HarnessPredicate<SkySortHarness>`

 SkySortHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySortHarness` instances.

    interface SkySortHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySortItemHarness
-------------------

Type: Class

`import { SkySortItemHarness } from '@skyux/lists/testing';`

Harness for interacting with a sort item component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the sort item.

#### Returns

`Promise<void>`

#### `getText(): Promise<null | string>`

Gets the sort item text.

#### Returns

`Promise<null | string>`

#### `isActive(): Promise<boolean>`

Whether the sort item is active.

#### Returns

`Promise<boolean>`

#### `SkySortItemHarness.with(filters: SkySortItemHarnessFilters): HarnessPredicate<SkySortItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySortItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySortItemHarnessFilters`

#### Returns

`HarnessPredicate<SkySortItemHarness>`

 SkySortItemHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySortItemHarness` instances.

    interface SkySortItemHarnessFilters {
      text?: string;
    }

### Properties

#### `text?: string`

Only find instances whose text content matches the given value.
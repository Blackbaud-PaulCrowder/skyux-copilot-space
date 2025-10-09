                    

 Toolbar
=======

The toolbar component displays actions to manipulate a list or to manipulate the individual items in the list.

 Usage
------

### Use when

Use list toolbars to display actions that manipulate the contents of lists of records. Place frequently used actions directly in the toolbar, and place less-frequently used actions in the more actions menu. When multiple views are available, dock the view switcher on the right.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-usage-list.e71a0460a365e27f35cb77899e222bb7.png)

Do use toolbars to display actions that manipulate list items.

Use toolbars to display actions that manipulate lists within containers, such as [boxes](/skyux/components/box.md) or [modals](/skyux/components/modal.md). Only place the most important actions directly in the toolbar because containers have limited horizontal real estate. Place all other actions in the more actions [dropdown](/skyux/components/dropdown.md).

For guidance on how to incorporate filters into lists within containers, see [filter lists guidelines](/skyux/design/guidelines/filtering-lists.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-usage-box.701e6cf04ebd428943e3cc3ec3400db7.png)

Do use toolbars to display actions that manipulate lists in containers, such as boxes.

### Don't use when

Don't use toolbars on [record page](/skyux/design/guidelines/page-layouts/record-page.md) headers to display page actions. Instead, place page actions directly below the record details.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-usage-dont-record.6aee51ab4e5bd53de701c5a52b877032.png)

Do not use toolbars on record pages.

Don't use toolbars in [action hub](/skyux/design/guidelines/page-layouts/action-hub.md) headers to display actions related to action hub content. Instead, place common action [buttons](/skyux/components/button.md) directly on the page below the page title.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-usage-dont-action-hub.628470fa20761dc882baa371f3c0aaa7.png)

Do not use toolbars on action hub pages.

 Options
--------

Only include toolbar options that are relevant to a particular list, and organize them consistently in their designated locations.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/anatomy.1a7bcaf736eaeae3761f04f37e3b9456.png)

### Standard toolbar actions

Place standard actions to the far left of the toolbar, and organize them from left to right based on the order in this section.

Don't include [primary action buttons](/skyux/components/button.md) in toolbars.

Add button

New

New

Text

New or Add

Icon

add

Dropdown

Optional. Allows users to add more than one type of item.

Notes

Use the "Add" label instead of "New" when an action creates an association between existing items.

Edit button

Edit

Edit

Text

Edit

Icon

edit

Dropdown

Optional. Allows users to edit multiple types of records in a content container.

Save button

Save

Save

Text

Save

Icon

save

Dropdown

Optional. Allows users to select multiple choices for how to save a list, such as "Save" and "Save as."

Sort button

Sort

Sort

Text

Sort

Icon

sort

Dropdown

Optional. Uses the SKY UX sort component to let users select a field to order rows in certain scenarios, such as templated columns and repeaters.

Columns button

Columns

Text

Columns

Icon

columns

Dropdown

None

Notes

Only visible when viewing a list as a grid.

Share button

Share

Text

Share

Icon

share

Dropdown

None

Export button

Export

Export

Export

Export

Text

Export

Icon

file, pdf-file, xls-file, doc-file

Dropdown

Optional. Allows users to select from multiple export options.

Notes

For multiple export options, use the generic file icon and a dropdown. For a single export option, use the icon for the file type that the option creates.

### More actions

Place less important or less-frequently used actions in a more actions menu. And when horizontal space in a toolbar is insufficient for all actions, collapse standard actions into the more actions menu.

More button

More

Text

More

Icon

ellipsis

Dropdown

Yes

Notes

In general, only use the more actions button for multiple actions. For a single action, display the button directly in the toolbar. However, if an action is potentially costly, such as a delete action, you can place that lone action in the dropdown to prevent users from accidentally selecting it.

### Find in this list

Place the search component to the right of the standard toolbar actions and the more actions button. Align the search field with the action buttons so that in large monitor resolutions, it appears on the left side of the screen.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-search-field.379e19a4dc3c6784852b023e9b584fe6.png)

Text

Find in this list

Notes

The search component has the same interactions and highlights in the toolbar as in other contexts.

### Items related to views

The view section appears on the right side of the toolbar. Reserve it for items that substantially change or affect the view of the rest of the content container. The items largely depend on the purpose of the toolbar. View section items appear from left to right in the following order when present in a toolbar:

Simple filters

Include inactive

Label

All volunteersSummer volunteersAll-year volunteers

Used in

Lists within containers

Notes

For lists in containers with no more than two simple filters, the filters can appear in the view section.

  

Expand/Collapse All

Used in

Tree views and lists with expandable repeater views

Icon

double-chevron-down, double-chevron-up

Notes

Use expand/collapse all buttons to control multiple rows in a repeater list or nodes in a tree view.

  

View switcher

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-view-switcher.dec8b3825a3862ecadf47f1f5cbe5054.png)

Used in

Lists

Icon

table, bullet-list, map-marker

Notes

The view switcher changes the component that displays items in a list. It uses the styling from icon-based checkboxes to indicate the current view.

 Behavior and states
--------------------

### Toolbar action wrapping

Do not extend the standard actions and more actions menu beyond 50 percent of the toolbar.

If the standard actions extend beyond 50 percent of the toolbar, create a more actions menu for at least two of the rightmost actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-dont-missing-more-menu.2d29cd08faec5f2fbc9c2cf42ade2adb.png)

Don't use toolbars with too many visible actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-with-more-menu.ff146255141a25b58292f3d1f1c1cc70.png)

Do move the rightmost actions into the more actions menu.

### Small form factors

On small screens, action buttons switch to icon-only buttons, the search field collapses into a search icon, and the view switcher collapses into a single icon. Buttons without icons go in the more actions menu, and the more actions button, view switcher, and any other buttons with dropdowns display their options when selected.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/toolbar-small-form-factor.a96f29a3ef8b4e94d40a4ce9ef4b0d56.png)

 Layout
-------

When two toolbars are stacked, place a border separator between them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/toolbar/double-toolbars-modern.c668ae8c515c08c7ad820e11b7e2fff0.png)

Do include a border separator between the toolbars.

 Related information
--------------------

### Components

*   [Box](/skyux/components/box.md)
*   [Buttons](/skyux/components/button.md)
*   [Data manager](/skyux/components/data-manager.md)
*   [Search](/skyux/components/search.md)

### Guidelines

*   [List page](/skyux/design/guidelines/page-layouts/list-page.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Terminology](/skyux/design/guidelines/terminology.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/toolbar/toolbar.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyToolbarModule
-----------------

Type: Module

`import { SkyToolbarModule } from '@skyux/layout';`

 SkyToolbarComponent
--------------------

Type: Component

Selector: `sky-toolbar`

Displays actions for lists, records, and tiles.

### Inputs

#### `listDescriptor: string | undefined`

A descriptor for the items that the toolbar manipulates. Use a plural term. The descriptor helps set the toolbar's `aria-label` attributes for search inputs, sort buttons, and filter buttons to provide text equivalents for screen readers [to support accessibility](/skyux/components/checkbox#accessibility.md). For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

 SkyToolbarSectionComponent
---------------------------

Type: Component

Selector: `sky-toolbar-section`

Specifies a section to group items within the toolbar. The section displays items in a separate horizontal row.

 SkyToolbarItemComponent
------------------------

Type: Component

Selector: `sky-toolbar-item`

Specifies a container for an item in the toolbar.

 SkyToolbarViewActionsComponent
-------------------------------

Type: Component

Selector: `sky-toolbar-view-actions`

Adds a section on the right side of the toolbar for items that substantially alter the view of the content container. This includes simple filters and view switchers.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyToolbarHarness
------------------

Type: Class

`import { SkyToolbarHarness } from '@skyux/layout/testing';`

Harness for interacting with a toolbar component in tests.

### Methods

#### `getItem(filter: SkyToolbarItemHarnessFilters): Promise<SkyToolbarItemHarness>`

Gets a specific toolbar item based on the filter criteria.

#### Parameters

##### `filter: SkyToolbarItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyToolbarItemHarness>`

#### `getItems(filters?: SkyToolbarItemHarnessFilters): Promise<SkyToolbarItemHarness[]>`

Gets an array of toolbar items based on the filter criteria. If no filter is provided, returns all toolbar items.

#### Parameters

##### `filters?: SkyToolbarItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyToolbarItemHarness[]>`

#### `getSection(filter: SkyToolbarSectionHarnessFilters): Promise<SkyToolbarSectionHarness>`

Gets a specific toolbar section based on the filter criteria.

#### Parameters

##### `filter: SkyToolbarSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyToolbarSectionHarness>`

#### `getSections(filters?: SkyToolbarSectionHarnessFilters): Promise<SkyToolbarSectionHarness[]>`

Gets an array of toolbar sections based on the filter criteria. If no filter is provided, returns all toolbar sections.

#### Parameters

##### `filters?: SkyToolbarSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyToolbarSectionHarness[]>`

#### `getViewActions(): Promise<SkyToolbarViewActionsHarness>`

Gets the harness to interact with the toolbar's view actions.

#### Returns

`Promise<SkyToolbarViewActionsHarness>`

#### `SkyToolbarHarness.with(filters: SkyToolbarHarnessFilters): HarnessPredicate<SkyToolbarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyToolbarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyToolbarHarnessFilters`

#### Returns

`HarnessPredicate<SkyToolbarHarness>`

 SkyToolbarHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyToolbarHarness` instances.

    interface SkyToolbarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyToolbarSectionHarness
-------------------------

Type: Class

`import { SkyToolbarSectionHarness } from '@skyux/layout/testing';`

Harness to interact with a toolbar section component in tests.

### Methods

#### `getItem(filter: SkyToolbarItemHarnessFilters): Promise<SkyToolbarItemHarness>`

Gets a specific toolbar item based on the filter criteria.

#### Parameters

##### `filter: SkyToolbarItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyToolbarItemHarness>`

#### `getItems(filters?: SkyToolbarItemHarnessFilters): Promise<SkyToolbarItemHarness[]>`

Gets an array of toolbar items based on the filter criteria. If no filter is provided, returns all toolbar items.

#### Parameters

##### `filters?: SkyToolbarItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyToolbarItemHarness[]>`

#### `getViewActions(): Promise<SkyToolbarViewActionsHarness>`

Gets the harness to interact with the toolbar's view actions.

#### Returns

`Promise<SkyToolbarViewActionsHarness>`

#### `SkyToolbarSectionHarness.with(filters: SkyToolbarSectionHarnessFilters): HarnessPredicate<SkyToolbarSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyToolbarSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyToolbarSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkyToolbarSectionHarness>`

 SkyToolbarSectionHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyToolbarSectionHarness` instances.

    interface SkyToolbarSectionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyToolbarItemHarness
----------------------

Type: Class

`import { SkyToolbarItemHarness } from '@skyux/layout/testing';`

Harness to interact with a toolbar item component in tests.

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

#### `SkyToolbarItemHarness.with(filters: SkyToolbarItemHarnessFilters): HarnessPredicate<SkyToolbarItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyToolbarItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyToolbarItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyToolbarItemHarness>`

 SkyToolbarItemHarnessFilters
-----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyToolbarItemHarness` instances.

    interface SkyToolbarItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyToolbarViewActionsHarness
-----------------------------

Type: Class

`import { SkyToolbarViewActionsHarness } from '@skyux/layout/testing';`

Harness to interact with a toolbar view actions component in tests.

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
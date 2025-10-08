# Design

                     Skip to Main Content

 List toolbar (deprecated)
=========================

The list toolbar component displays a toolbar for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

Lists and their features are deprecated. We will remove them in a future major version. We recommend using [data manager](/skyux/components/data-manager.md) instead.

 Usage
------

### Use when

Do use the list toolbar above a list of records to display actions that manipulate the contents of the list. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. When multiple views of the list are available, the view switcher is docked on the right side of the toolbar.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder/img/guidelines/list-toolbar/list-toolbar-context.ada0030a9715e75351225fb7b987a912.png)

Do use list toolbars to display actions that manipulate list items.

 Options
--------

### Composition

For more information about how to arrange content in a list toolbar, see the [toolbar design guidelines](/skyux/components/toolbar.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder/img/guidelines/list-toolbar/toolbar-anatomy.1a7bcaf736eaeae3761f04f37e3b9456.png)

### Sorting

If you use the toolbar with a grid view, you have two options to let users sort the list:

*   The sort button in the toolbar
*   Clickable column headers

Don't use both sorting options on the same list because it can confuse users about which option is applied.

 Related information
--------------------

### Components

*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)
*   [List view grid](/skyux/components/list-view-grid.md)
*   [Search](/skyux/components/search.md)
*   [Toolbar](/skyux/components/toolbar.md)

 Installation
-------------

NPM package

`@skyux/list-builder`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder/src/lib/modules/list-toolbar/list-secondary-actions/list-secondary-actions.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder`Copy None found.

 SkyListSecondaryActionsModule
------------------------------

Type: Module

`import { SkyListSecondaryActionsModule } from '@skyux/list-builder';`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

 SkyListToolbarComponent
------------------------

Type: Component

Selector: `sky-list-toolbar`

Displays a toolbar for a SKY UX-themed list of data.

### Inputs

#### `placeholder: string`

Placeholder text for the search bar that the list toolbar creates with a [search component](/skyux/components/search.md).

Default: `"Find in this list"`

#### `searchEnabled: boolean | Observable<boolean>`

Whether to enable the search bar.

Default: `true`

#### `searchText: string | Observable<string>`

The text string to search with.

#### `sortSelectorEnabled: boolean | Observable<boolean>`

Whether to enable the sort selector.

Default: `false`

#### `toolbarType: string`

Display the search bar in the standard position or in a separate section. To highlight the search bar in a section above all other toolbar items, set this property to `search`.

Default: `"standard"`

 SkyListSecondaryActionsComponent
---------------------------------

Type: Component

Selector: `sky-list-secondary-actions`

Adds a dropdown to the list toolbar for secondary actions. If the dropdown does not include actions, the secondary actions dropdown is hidden.

 SkyListSecondaryActionComponent
--------------------------------

Type: Component

Selector: `sky-list-secondary-action`

Adds actions to the secondary actions dropdown in the list toolbar.

 SkyListToolbarItemComponent
----------------------------

Type: Component

Selector: `sky-list-toolbar-item`

Defines a toolbar item for the list toolbar.

### Inputs

#### `id: string`

The ID of the item.

#### `index: number`

The index of the item at the given item location.

Default: `-1`

#### `location: string`

The toolbar location of the item. The valid options are `"left"`, `"center"`, and `"right"`.

Default: `"left"`

 SkyListToolbarSearchActionsComponent
-------------------------------------

Type: Component

Selector: `sky-list-toolbar-search-actions`

Displays custom actions in the toolbar beside to the search bar.

 SkyListToolbarSortComponent
----------------------------

Type: Component

Selector: `sky-list-toolbar-sort`

Adds a sort dropdown to the list toolbar.

### Inputs

#### `field: string`

Required

The data field to sort the list on.

#### `label: string`

Required

The label for a sort option.

#### `type: string`

Required

The data type of the data field to sort the list on.

#### `descending: boolean`

Whether to sort data in descending order.

Default: `false`

 SkyListToolbarViewActionsComponent
-----------------------------------

Type: Component

Selector: `sky-list-toolbar-view-actions`

Adds a section on the right side of the toolbar for items that substantially change or affect the view of the list. This includes simple filters and view switchers. If the view section includes more than one item, simple filters appear on the left and view switchers appear on the right.

# Development

                     Skip to Main Content

 List toolbar (deprecated)
=========================

The list toolbar component displays a toolbar for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

Lists and their features are deprecated. We will remove them in a future major version. We recommend using [data manager](/skyux/components/data-manager.md) instead.

 Usage
------

### Use when

Do use the list toolbar above a list of records to display actions that manipulate the contents of the list. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. When multiple views of the list are available, the view switcher is docked on the right side of the toolbar.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder/img/guidelines/list-toolbar/list-toolbar-context.ada0030a9715e75351225fb7b987a912.png)

Do use list toolbars to display actions that manipulate list items.

 Options
--------

### Composition

For more information about how to arrange content in a list toolbar, see the [toolbar design guidelines](/skyux/components/toolbar.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/list-builder/img/guidelines/list-toolbar/toolbar-anatomy.1a7bcaf736eaeae3761f04f37e3b9456.png)

### Sorting

If you use the toolbar with a grid view, you have two options to let users sort the list:

*   The sort button in the toolbar
*   Clickable column headers

Don't use both sorting options on the same list because it can confuse users about which option is applied.

 Related information
--------------------

### Components

*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)
*   [List view grid](/skyux/components/list-view-grid.md)
*   [Search](/skyux/components/search.md)
*   [Toolbar](/skyux/components/toolbar.md)

 Installation
-------------

NPM package

`@skyux/list-builder`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder/src/lib/modules/list-toolbar/list-secondary-actions/list-secondary-actions.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder`Copy None found.

 SkyListSecondaryActionsModule
------------------------------

Type: Module

`import { SkyListSecondaryActionsModule } from '@skyux/list-builder';`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

 SkyListToolbarComponent
------------------------

Type: Component

Selector: `sky-list-toolbar`

Displays a toolbar for a SKY UX-themed list of data.

### Inputs

#### `placeholder: string`

Placeholder text for the search bar that the list toolbar creates with a [search component](/skyux/components/search.md).

Default: `"Find in this list"`

#### `searchEnabled: boolean | Observable<boolean>`

Whether to enable the search bar.

Default: `true`

#### `searchText: string | Observable<string>`

The text string to search with.

#### `sortSelectorEnabled: boolean | Observable<boolean>`

Whether to enable the sort selector.

Default: `false`

#### `toolbarType: string`

Display the search bar in the standard position or in a separate section. To highlight the search bar in a section above all other toolbar items, set this property to `search`.

Default: `"standard"`

 SkyListSecondaryActionsComponent
---------------------------------

Type: Component

Selector: `sky-list-secondary-actions`

Adds a dropdown to the list toolbar for secondary actions. If the dropdown does not include actions, the secondary actions dropdown is hidden.

 SkyListSecondaryActionComponent
--------------------------------

Type: Component

Selector: `sky-list-secondary-action`

Adds actions to the secondary actions dropdown in the list toolbar.

 SkyListToolbarItemComponent
----------------------------

Type: Component

Selector: `sky-list-toolbar-item`

Defines a toolbar item for the list toolbar.

### Inputs

#### `id: string`

The ID of the item.

#### `index: number`

The index of the item at the given item location.

Default: `-1`

#### `location: string`

The toolbar location of the item. The valid options are `"left"`, `"center"`, and `"right"`.

Default: `"left"`

 SkyListToolbarSearchActionsComponent
-------------------------------------

Type: Component

Selector: `sky-list-toolbar-search-actions`

Displays custom actions in the toolbar beside to the search bar.

 SkyListToolbarSortComponent
----------------------------

Type: Component

Selector: `sky-list-toolbar-sort`

Adds a sort dropdown to the list toolbar.

### Inputs

#### `field: string`

Required

The data field to sort the list on.

#### `label: string`

Required

The label for a sort option.

#### `type: string`

Required

The data type of the data field to sort the list on.

#### `descending: boolean`

Whether to sort data in descending order.

Default: `false`

 SkyListToolbarViewActionsComponent
-----------------------------------

Type: Component

Selector: `sky-list-toolbar-view-actions`

Adds a section on the right side of the toolbar for items that substantially change or affect the view of the list. This includes simple filters and view switchers. If the view section includes more than one item, simple filters appear on the left and view switchers appear on the right.
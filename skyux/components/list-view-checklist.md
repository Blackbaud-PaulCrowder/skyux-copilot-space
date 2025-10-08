# Design

                   Skip to Main Content

 List view checklist (deprecated)
================================

The list view checklist displays a checklist within a [SKY UX-themed list of data](/skyux/components/list-overview.md) and enables consumers to define a custom search function for the data.

List view checklist and its features are deprecated. We will remove it in a future major version. We recommend using [selection modal](/skyux/components/selection-modal.md) instead.

 Related information
--------------------

### Components

*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view grid](/skyux/components/list-view-grid.md)

 Installation
-------------

NPM package

`@skyux/list-builder-view-checklist`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder-view-checklist) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder-view-checklist/src/lib/modules/list-view-checklist/list-view-checklist.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder-view-checklist`Copy None found.

 SkyListViewChecklistModule
---------------------------

Type: Module

`import { SkyListViewChecklistModule } from '@skyux/list-builder-view-checklist';`

Warning: **Deprecated.** List builder view checklist and its features are deprecated. Use repeater instead. For more information, see [https://developer.blackbaud.com/skyux/components/repeater](/skyux/components/repeater.md).

 SkyListViewChecklistComponent
------------------------------

Type: Component

Selector: `sky-list-view-checklist`

Warning: **Deprecated.** List builder view checklist and its features are deprecated. Use repeater instead. For more information, see [https://developer.blackbaud.com/skyux/components/repeater](/skyux/components/repeater.md).

### Inputs

#### `name: string`

Required

The name of the view.

#### `description: string`

The name of the description field selector.

Default: `"description"`

#### `label: string`

The name of the label field selector.

Default: `"label"`

#### `search: (data: any, searchText: string) => boolean`

The search function to apply on the view data. The default function searches view data on label, description, and category if field selectors are defined for the given field.

Default: `default search function`

#### `selectMode: string`

How many items users can select. `"single"` allows users to select one item in the checklist, while `"multiple"` allows users to select multiple items in the checklist.

Default: `"multiple"`

#### `showOnlySelected: boolean`

Whether to display selected items only.

Default: `false`

 SkyListViewChecklistItemComponent
----------------------------------

Type: Component

Selector: `sky-list-view-checklist-item`

### Inputs

#### `item: ListViewChecklistItemModel`

 ChecklistStateAction
---------------------

Type: Type alias

    type ChecklistStateAction = ListViewChecklistItemsLoadAction

 ChecklistStateModel
--------------------

Type: Class

### Properties

#### `items: AsyncList<ListViewChecklistItemModel>`

 ChecklistStateDispatcher
-------------------------

Type: Service

 ChecklistStateOrchestrator
---------------------------

Type: Class

### Methods

#### `register(action: any, callback: (state: T, action: ListViewChecklistItemsLoadAction, initialState?: any) => any): StateOrchestrator<T, ListViewChecklistItemsLoadAction>`

#### Parameters

##### `action: any`

##### `callback: (state: T, action: ListViewChecklistItemsLoadAction, initialState?: any) => any`

#### Returns

`StateOrchestrator<T, ListViewChecklistItemsLoadAction>`

#### `scan(initialState: T, actions: Observable<ListViewChecklistItemsLoadAction>): Observable<any>`

#### Parameters

##### `initialState: T`

##### `actions: Observable<ListViewChecklistItemsLoadAction>`

#### Returns

`Observable<any>`

 ChecklistState
---------------

Type: Service

### Methods

#### `begin(): void`

#### Returns

`void`

#### `register(stateKey: string, orchestrator: any): StateNode<ChecklistStateModel>`

#### Parameters

##### `stateKey: string`

##### `orchestrator: any`

#### Returns

`StateNode<ChecklistStateModel>`

#### `reset(): void`

#### Returns

`void`

 ListViewChecklistItemModel
---------------------------

Type: Class

### Properties

#### `description: string`

#### `id: string`

#### `label: string`

 ListViewChecklistItemsOrchestrator
-----------------------------------

Type: Class

### Methods

#### `register(action: any, callback: (state: AsyncList, action: ListViewChecklistItemsLoadAction, initialState?: any) => any): StateOrchestrator<AsyncList<ListViewChecklistItemModel>, ListViewChecklistItemsLoadAction>`

#### Parameters

##### `action: any`

##### `callback: (state: AsyncList, action: ListViewChecklistItemsLoadAction, initialState?: any) => any`

#### Returns

`StateOrchestrator<AsyncList<ListViewChecklistItemModel>, ListViewChecklistItemsLoadAction>`

#### `scan(initialState: AsyncList, actions: Observable<ListViewChecklistItemsLoadAction>): Observable<any>`

#### Parameters

##### `initialState: AsyncList`

##### `actions: Observable<ListViewChecklistItemsLoadAction>`

#### Returns

`Observable<any>`

 ListViewChecklistItemsLoadAction
---------------------------------

Type: Class

### Properties

#### `dataChanged: boolean`

Default: `true`

#### `itemCount: number`

Default: `items.length`

#### `items: ListViewChecklistItemModel[]`

Default: `[]`

#### `refresh: boolean`

Default: `false`

# Development

                   Skip to Main Content

 List view checklist (deprecated)
================================

The list view checklist displays a checklist within a [SKY UX-themed list of data](/skyux/components/list-overview.md) and enables consumers to define a custom search function for the data.

List view checklist and its features are deprecated. We will remove it in a future major version. We recommend using [selection modal](/skyux/components/selection-modal.md) instead.

 Related information
--------------------

### Components

*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List paging](/skyux/components/list-paging.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view grid](/skyux/components/list-view-grid.md)

 Installation
-------------

NPM package

`@skyux/list-builder-view-checklist`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder-view-checklist) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder-view-checklist/src/lib/modules/list-view-checklist/list-view-checklist.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder-view-checklist`Copy None found.

 SkyListViewChecklistModule
---------------------------

Type: Module

`import { SkyListViewChecklistModule } from '@skyux/list-builder-view-checklist';`

Warning: **Deprecated.** List builder view checklist and its features are deprecated. Use repeater instead. For more information, see [https://developer.blackbaud.com/skyux/components/repeater](/skyux/components/repeater.md).

 SkyListViewChecklistComponent
------------------------------

Type: Component

Selector: `sky-list-view-checklist`

Warning: **Deprecated.** List builder view checklist and its features are deprecated. Use repeater instead. For more information, see [https://developer.blackbaud.com/skyux/components/repeater](/skyux/components/repeater.md).

### Inputs

#### `name: string`

Required

The name of the view.

#### `description: string`

The name of the description field selector.

Default: `"description"`

#### `label: string`

The name of the label field selector.

Default: `"label"`

#### `search: (data: any, searchText: string) => boolean`

The search function to apply on the view data. The default function searches view data on label, description, and category if field selectors are defined for the given field.

Default: `default search function`

#### `selectMode: string`

How many items users can select. `"single"` allows users to select one item in the checklist, while `"multiple"` allows users to select multiple items in the checklist.

Default: `"multiple"`

#### `showOnlySelected: boolean`

Whether to display selected items only.

Default: `false`

 SkyListViewChecklistItemComponent
----------------------------------

Type: Component

Selector: `sky-list-view-checklist-item`

### Inputs

#### `item: ListViewChecklistItemModel`

 ChecklistStateAction
---------------------

Type: Type alias

    type ChecklistStateAction = ListViewChecklistItemsLoadAction

 ChecklistStateModel
--------------------

Type: Class

### Properties

#### `items: AsyncList<ListViewChecklistItemModel>`

 ChecklistStateDispatcher
-------------------------

Type: Service

 ChecklistStateOrchestrator
---------------------------

Type: Class

### Methods

#### `register(action: any, callback: (state: T, action: ListViewChecklistItemsLoadAction, initialState?: any) => any): StateOrchestrator<T, ListViewChecklistItemsLoadAction>`

#### Parameters

##### `action: any`

##### `callback: (state: T, action: ListViewChecklistItemsLoadAction, initialState?: any) => any`

#### Returns

`StateOrchestrator<T, ListViewChecklistItemsLoadAction>`

#### `scan(initialState: T, actions: Observable<ListViewChecklistItemsLoadAction>): Observable<any>`

#### Parameters

##### `initialState: T`

##### `actions: Observable<ListViewChecklistItemsLoadAction>`

#### Returns

`Observable<any>`

 ChecklistState
---------------

Type: Service

### Methods

#### `begin(): void`

#### Returns

`void`

#### `register(stateKey: string, orchestrator: any): StateNode<ChecklistStateModel>`

#### Parameters

##### `stateKey: string`

##### `orchestrator: any`

#### Returns

`StateNode<ChecklistStateModel>`

#### `reset(): void`

#### Returns

`void`

 ListViewChecklistItemModel
---------------------------

Type: Class

### Properties

#### `description: string`

#### `id: string`

#### `label: string`

 ListViewChecklistItemsOrchestrator
-----------------------------------

Type: Class

### Methods

#### `register(action: any, callback: (state: AsyncList, action: ListViewChecklistItemsLoadAction, initialState?: any) => any): StateOrchestrator<AsyncList<ListViewChecklistItemModel>, ListViewChecklistItemsLoadAction>`

#### Parameters

##### `action: any`

##### `callback: (state: AsyncList, action: ListViewChecklistItemsLoadAction, initialState?: any) => any`

#### Returns

`StateOrchestrator<AsyncList<ListViewChecklistItemModel>, ListViewChecklistItemsLoadAction>`

#### `scan(initialState: AsyncList, actions: Observable<ListViewChecklistItemsLoadAction>): Observable<any>`

#### Parameters

##### `initialState: AsyncList`

##### `actions: Observable<ListViewChecklistItemsLoadAction>`

#### Returns

`Observable<any>`

 ListViewChecklistItemsLoadAction
---------------------------------

Type: Class

### Properties

#### `dataChanged: boolean`

Default: `true`

#### `itemCount: number`

Default: `items.length`

#### `items: ListViewChecklistItemModel[]`

Default: `[]`

#### `refresh: boolean`

Default: `false`
                      

 Split view
==========

A split view displays a workspace beside a list to let users view details and take actions for the selected item.

 Usage
------

### Use when

Use split views when users need to work through a list of items with the intent of taking action on each item.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-usage.afb3ab9003e792c00e0722cbc9926601.png)

Do use split views when users take the same action for each item in the list.

### Don't use when

Don't use split views when users are likely to interact with a small number of items in the list. Use regular lists instead, and follow the [flyout guidelines](/skyux/components/flyout#ux-guidelines.md) to determine whether to use flyouts or navigate to selected records.

 Anatomy
--------

### Large viewport

1

List panel

2

Workspace panel

3

Summary action bar  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-anatomy-desktop.16936f42d8425cb0da26dc195f9d2bac.png)

### Small viewport

1

List panel

2

Responsive header bar

3

Workspace panel

4

Summary action bar  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-anatomy-mobile.3895c8eb86059e0016d50573fe8f777f.png)

 Options
--------

### List type

[Repeaters](/skyux/components/repeater.md) are the most common list type because they enable flexible content layouts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-usage.afb3ab9003e792c00e0722cbc9926601.png)

[Tree views](/skyux/components/angular-tree.md) can be used when items are hierarchical. If items at different levels have different types, you can use multiple views in the workspace panel.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-options-list-type-tree.3a6d859ce8728dc3d2c36b5e80b213af.png)

We recommend against using [grids](/skyux/components/grid.md) if possible. They do not scale well at the typically small width of the list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-options-list-type-grid.739474e419ae9663ebf38a231d8a5faf.png)

Use caution with grids because they do not perform well at narrow widths.

### List manipulation

If users need to search for specific items in the list or show and hide items with certain statuses, include a search input or status checkbox filter in the list panel.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-options-search-toggle.57e4d92e34dcad071de3a2c264419196.png)

When possible, pre-filter the list to relevant items and pre-sort it to the expected useful order. If you can't predict how users will use the list, include a [toolbar](/skyux/components/toolbar.md) to let them add items or filter, sort, and search the list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-options-toolbar.5db281b0ab420f5e5d03c259bfecdc01.png)

Use caution when using a full toolbar with a split view. Automatically filter and sort the list when possible.

 Behavior and states
--------------------

### Automatically advance to the next item

If users are likely to work through the list sequentially, remove the selected item and automatically advance to the next item after users invoke the primary action in the workspace.

### Place focus in the workspace

When users select an item in the list, place focus on the first focusable element in the workspace so that users can start working immediately.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-behavior-focus.40ba0bd3b0a2551038a779ac8cbd71e2.png)

### Change panel width

Users can change the panel widths using drag-and-drop or keyboard interactions. If the list content is wider than the panel, a horizontal scrollbar appears.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-behavior-resize.e29d57c2edbdb8810598eb5ab46e1ceb.png)

### Responsiveness

In smaller viewports, the split view automatically switches from a side-by-side view to a panel-switching interaction where users switch between the list and the workspace.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-behavior-responsive.954b906f00b8173adf28e9118eeb9bac.png)

 Content
--------

### List item

Use up to three pieces of data to identify the item. If additional content is needed to uniquely identify the item, put it in the workspace view instead of overloading the list item.

 Layout
-------

A split view should be the last item on a page. Do not place additional content below it.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/split-view/split-view-layout-last-item.98ca0a4b1e52bb8d79d1aeb6a85623ca.png)

Don't place content below the split view.

 Related information
--------------------

### Components

*   [Repeater](/skyux/components/repeater.md)
*   [Summary action bar](/skyux/components/summary-action-bar.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

 Installation
-------------

NPM package

`@skyux/split-view`[View in NPM](https://www.npmjs.com/package/@skyux/split-view) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/split-view/src/lib/modules/split-view/split-view.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/split-view`Copy None found.

 SkySplitViewModule
-------------------

Type: Module

`import { SkySplitViewModule } from '@skyux/split-view';`

 SkySplitViewComponent
----------------------

Type: Component

Selector: `sky-split-view`

Displays a list alongside a workspace where users can view details for selected items and take actions.

### Inputs

#### `backButtonText: string`

The label for the button that appears in the workspace header in responsive mode. The button returns users to the list.

Default: `"Back to list"`

#### `bindHeightToWindow: boolean`

Warning: **Deprecated.** We recommend using the `dock` input instead. An example of this can be found in the developer code examples.

Whether the split view's height is bound to the window height.

Default: `false`

#### `dock: SkySplitViewDockType`

How the split view docks to its container. Use `fill` to dock the split view to the container's size where the container is a `sky-page` component with its `layout` input set to `fit`, or where the container is another element with a relative or absolute position and a fixed size.

Default: `"none"`

#### `messageStream: Subject<SkySplitViewMessage>`

The observable that sends commands to the split view component. The commands should respect the `SkySplitViewMessage` type.

 SkySplitViewDrawerComponent
----------------------------

Type: Component

Selector: `sky-split-view-drawer`

Specifies the content to display in the split view's list panel.

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the list panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `width: number | undefined`

Sets the list panel's width in pixels.

Default: `320`

 SkySplitViewWorkspaceComponent
-------------------------------

Type: Component

Selector: `sky-split-view-workspace`

Contains the content, footer, and header to display in the split view's workspace panel.

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the workspace panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

 SkySplitViewWorkspaceContentComponent
--------------------------------------

Type: Component

Selector: `sky-split-view-workspace-content`

Specifies the content to display in the split view's workspace panel.

 SkySplitViewWorkspaceFooterComponent
-------------------------------------

Type: Component

Selector: `sky-split-view-workspace-footer`

Specifies the footer to display in the split view's workspace panel. This component is often used with a summary action bar.

 SkySplitViewDockType
---------------------

Type: Type alias

    type SkySplitViewDockType = "none" | "fill"

 SkySplitViewMessage
--------------------

Type: Interface

    interface SkySplitViewMessage {
      type?: FocusWorkspace;
    }

### Properties

#### `type?: FocusWorkspace`

Sets the `SkySplitViewMessageType`.

 SkySplitViewMessageType
------------------------

Type: Enumeration

    enum SkySplitViewMessageType {
      FocusWorkspace = 0,
    }

### Properties

#### `SkySplitViewMessageType.FocusWorkspace`

Places focus on the first focusable element in the workspace.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySplitViewHarness
--------------------

Type: Class

`import { SkySplitViewHarness } from '@skyux/split-view/testing';`

Harness for interacting with a split view component in tests.

### Methods

#### `getBackButtonText(): Promise<string>`

Gets the text for the button that appears in the workspace header in responsive mode.

#### Returns

`Promise<string>`

#### `getDockType(): Promise<SkySplitViewDockType>`

Gets the type of dock style on the split view.

#### Returns

`Promise<SkySplitViewDockType>`

#### `getDrawer(): Promise<SkySplitViewDrawerHarness>`

Gets a '[SkySplitViewDrawerHarness](/skyux/components/split-view?docs-active-tab=design#class_sky-split-view-drawer-harness.md)\`.

#### Returns

`Promise<SkySplitViewDrawerHarness>`

#### `getDrawerIsVisible(): Promise<boolean>`

Whether the drawer component is visible

#### Returns

`Promise<boolean>`

#### `getWorkspace(): Promise<SkySplitViewWorkspaceHarness>`

Gets a `SkySplitViewWorkspaceHarness`.

#### Returns

`Promise<SkySplitViewWorkspaceHarness>`

#### `getWorkspaceIsVisible(): Promise<boolean>`

Whether the workspace component is visible.

#### Returns

`Promise<boolean>`

#### `openDrawer(): Promise<void>`

Opens the drawer component when in responsive mode.

#### Returns

`Promise<void>`

#### `SkySplitViewHarness.with(filters: SkySplitViewHarnessFilters): HarnessPredicate<SkySplitViewHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySplitViewHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySplitViewHarnessFilters`

#### Returns

`HarnessPredicate<SkySplitViewHarness>`

 SkySplitViewHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkySplitViewHarness](/skyux/components/split-view?docs-active-tab=design#class_sky-split-view-harness.md) instances.

    interface SkySplitViewHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySplitViewDrawerHarness
--------------------------

Type: Class

`import { SkySplitViewDrawerHarness } from '@skyux/split-view/testing';`

Harness to interact with the split view drawer component in tests.

### Methods

#### `getAriaLabel(): Promise<null | string>`

The aria-label property of the split view drawer

#### Returns

`Promise<null | string>`

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

 SkySplitViewWorkspaceHarness
-----------------------------

Type: Class

`import { SkySplitViewWorkspaceHarness } from '@skyux/split-view/testing';`

Harness to interact with the split view workspace component in tests.

### Methods

#### `getAriaLabel(): Promise<null | string>`

The aria-label property of the split view workspace

#### Returns

`Promise<null | string>`

#### `getContent(): Promise<SkySplitViewWorkspaceContentHarness>`

Gets the workspace content component.

#### Returns

`Promise<SkySplitViewWorkspaceContentHarness>`

#### `getFooter(): Promise<SkySplitViewWorkspaceFooterHarness>`

Gets the workspace footer component.

#### Returns

`Promise<SkySplitViewWorkspaceFooterHarness>`

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

 SkySplitViewWorkspaceContentHarness
------------------------------------

Type: Class

`import { SkySplitViewWorkspaceContentHarness } from '@skyux/split-view/testing';`

Harness to interact with the split view workspace content component in tests.

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

 SkySplitViewWorkspaceFooterHarness
-----------------------------------

Type: Class

`import { SkySplitViewWorkspaceFooterHarness } from '@skyux/split-view/testing';`

Harness to interact with the split view workspace footer component in tests.

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
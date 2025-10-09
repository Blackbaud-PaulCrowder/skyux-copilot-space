                  

 Tile
====

Tiles create flexible containers to display content or features from external sources inside SKY UX applications.

 Usage
------

### Use when

Use tiles to display content or features from external sources on the Add-ins tab of [record pages](/skyux/design/guidelines/page-layouts/record-page.md) . As extension points in the SKY Add-ins framework, tiles are the primary container for external content in SKY UX applications. You can use a tile dashboard to automatically size and arrange tiles and to let users reorder or collapse/expand tiles to meet their specific needs.

For more information, see the [SKY Add-ins documentation for tiles](https://developer.blackbaud.com/skyapi/docs/addins/get-started/skyux-tile) .

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tiles-usage-1.8cfebaaf2bd0bb54cdd108b801a9fb21.png)

Do use tiles to display content from external sources.

### Don't use when

Don't use tiles to organize native Blackbaud content and features or to define content categories within SKY UX applications. On [record pages](/skyux/design/guidelines/page-layouts/record-page.md) use [boxes](/skyux/components/box.md) within [fluid grids](/skyux/components/fluid-grid.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tiles-usage-2.ff05c732fb3fe7b9df437da0a0ffa212.png)

Don't use tiles to organize native Blackbaud content and features.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tiles-usage-3.a7cb204592d8a4084b52e549f7814b78.png)

Do use boxes to organize page content into categories.

Don't use tiles to organize content within modals. For complex forms, use [sectioned forms](/skyux/components/sectioned-form.md) or [other form containers](/skyux/design/guidelines/form-design.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tile-usage-4.97ec40dffe9483926bd8c97815b2f41e.png)

Don't use tiles to divide modal content into sections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tile-usage-5.c75e59139d4a170693363c57b857eeb2.png)

Do use sectioned forms if you need to organize modal content into categories.

 Anatomy
--------

1

Header

2

Title

3

Expand/collapse button

4

Drag handle

5

Content area

6

Help inline button (optional)

7

Settings button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/tiles/img/guidelines/tile-anatomy.79a477dc1287559bfee27684908bdd93.png)

 Options
--------

### Help inline button

When you need to supplement a tile with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the title to invoke contextual user assistance.

### Settings button

Show the settings button on a tile when users need to access add-in settings, authentication for connected services, or other configuration options. This button can launch whatever pattern is appropriate, such as opening a modal or a separate browser tab.

 Content
--------

### Empty state

For tiles that are not populated, use [empty-state help](/skyux/design/guidelines/user-assistance#empty-state-help.md) to explain how to use the tile.

 Related information
--------------------

### Components

*   [Box](/skyux/components/box.md)
*   [Help inline button](/skyux/components/help-inline.md)

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/tiles`[View in NPM](https://www.npmjs.com/package/@skyux/tiles) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tiles/src/lib/modules/tiles/tiles.module.ts#L16) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tiles`Copy None found.

 SkyTilesModule
---------------

Type: Module

`import { SkyTilesModule } from '@skyux/tiles';`

 SkyTileComponent
-----------------

Type: Component

Selector: `sky-tile`

Provides a common look-and-feel for tab content.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `tileName`, a [help inline](/skyux/components/help-inline.md) button is added to the tile header. Clicking the button invokes global help as configured by the application. This property only applies when `tileName` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `tileName`, a [help inline](/skyux/components/help-inline.md) button is added to the tile header. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `tileName` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `showHelp: boolean`

Warning: **Deprecated.** Set the `helpKey` or `helpPopoverContent` inputs instead.

Whether to display a help button in the tile header. To display the button, you must also listen for the `helpClick` event.

Default: `true`

#### `showSettings: boolean`

Whether to display a settings button in the tile header. To display the button, you must also listen for the `settingsClick` event.

Default: `true`

#### `tileName: string | undefined`

The human-readable name for the tile that is available to the tile controls for multiple purposes, such as accessibility and instrumentation. The component uses the name to construct ARIA labels for the help, expand/collapse, settings, and drag handle buttons to [support accessibility](/skyux/learn/accessibility.md). For example, if the tile name is "Constituents," the help input's `aria-label` is "Constituents help" and the drag handle's `aria-label` is "Move Constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

### Outputs

#### `helpClick: EventEmitter<any>`

Warning: **Deprecated.** Set the `helpKey` or `helpPopoverContent` inputs instead.

Fires when users select the help button in the tile header. The help button only appears when the `showHelp` property is set to `true`.

#### `isCollapsedChange: EventEmitter<boolean>`

Fires when the tile's collapsed state changes. Returns `true` when the tile collapses and `false` when it expands.

#### `settingsClick: EventEmitter<any>`

Fires when users select the settings button in the tile header. The settings button only appears when the `showSettings` property is set to `true`.

 SkyTileTitleComponent
----------------------

Type: Component

Selector: `sky-tile-title`

Specifies content to display in the tile's title.

 SkyTileSummaryComponent
------------------------

Type: Component

Selector: `sky-tile-summary`

Specifies content to display in the tile's summary.

 SkyTileContentComponent
------------------------

Type: Component

Selector: `sky-tile-content`

Specifies content to display in the tile's body.

 SkyTileContentSectionComponent
-------------------------------

Type: Component

Selector: `sky-tile-content-section`

Specifies content to display inside a padded section of a [SkyTileContentComponent](/skyux/components/tile?docs-active-tab=design#class_sky-tile-content-component.md).

 SkyTileDashboardComponent
--------------------------

Type: Component

Selector: `sky-tile-dashboard`

Specifies a container to group multiple tiles.

### Inputs

#### `config: SkyTileDashboardConfig | undefined`

Required

Populates the tile dashboard based on the `SkyTileDashboardConfig` object.

#### `messageStream: Subject<SkyTileDashboardMessage>`

The observable to send commands to the tile dashboard. The commands must respect the `SkyTileDashboardMessage` type.

#### `settingsKey: string | undefined`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the layout and collapsed state of tile dashboards. The UI Config Service relies on `id` values from the `config` property to maintain user settings. For more information about the UI Config Service, see the [sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

### Outputs

#### `configChange: EventEmitter<SkyTileDashboardConfig>`

Fires when the tile dashboard changes state and emits a [SkyTileDashboardConfig](/skyux/components/tile?docs-active-tab=design#interface_sky-tile-dashboard-config.md) object. This occurs when tiles collapse or expand and when users drag and drop tiles to rearrange them.

 SkyTileDashboardService
------------------------

Type: Service

### Properties

#### `dashboardInitialized: EventEmitter<void>`

Fires when the tile dashboard's initialization is complete.

### Methods

#### `addTileComponent(tile: SkyTileDashboardConfigLayoutTile, component: ComponentRef<any>): void`

Adds a new tile to the tile dashboard.

#### Parameters

##### `tile: SkyTileDashboardConfigLayoutTile`

Specifies the tile configuration.

##### `component: ComponentRef<any>`

Specifies the tile component to add.

#### Returns

`void`

#### `setAllTilesCollapsed(isCollapsed: boolean): void`

Sets the collapsed state of all tiles.

#### Parameters

##### `isCollapsed: boolean`

Indicates whether tiles are collapsed.

#### Returns

`void`

#### `setTileCollapsed(tile: SkyTileComponent | undefined, isCollapsed: boolean): void`

Sets the collapsed state of a specified tile.

#### Parameters

##### `tile: SkyTileComponent | undefined`

Specifies the tile component.

##### `isCollapsed: boolean`

Indicates whether the tile is collapsed.

#### Returns

`void`

#### `tileIsCollapsed(tile: SkyTileComponent): boolean`

Checks whether a specified tile is collapsed.

#### Parameters

##### `tile: SkyTileComponent`

Specifies the tile component to check.

#### Returns

`boolean`

 SkyTileDashboardConfig
-----------------------

Type: Interface

    interface SkyTileDashboardConfig {
      layout: SkyTileDashboardConfigLayout;
      movedTile?: SkyTileDashboardConfigReorderData;
      tiles: SkyTileDashboardConfigTile[];
    }

### Properties

#### `layout: SkyTileDashboardConfigLayout`

A `SkyTileDashboardConfigLayout` object that describes the tile dashboard's layout.

#### `movedTile?: SkyTileDashboardConfigReorderData`

A `SkyTileDashboardConfigReorderData` object that describes how to move a tile within the dashboard.

#### `tiles: SkyTileDashboardConfigTile[]`

An array of [SkyTileDashboardConfigTile](/skyux/components/tile?docs-active-tab=design#interface_sky-tile-dashboard-config-tile.md) objects that specifies the tiles to include in the dashboard.

 SkyTileDashboardConfigLayout
-----------------------------

Type: Interface

    interface SkyTileDashboardConfigLayout {
      multiColumn: SkyTileDashboardConfigLayoutColumn[];
      singleColumn: SkyTileDashboardConfigLayoutColumn;
    }

### Properties

#### `multiColumn: SkyTileDashboardConfigLayoutColumn[]`

An array of `SkyTileDashboardConfigLayoutColumn` objects that describes how to display tiles in multiple columns on larger screens.

#### `singleColumn: SkyTileDashboardConfigLayoutColumn`

A `SkyTileDashboardConfigLayoutColumn` object that describes how to display tiles in a single column on small screens.

 SkyTileDashboardConfigLayoutColumn
-----------------------------------

Type: Interface

    interface SkyTileDashboardConfigLayoutColumn {
      tiles: SkyTileDashboardConfigLayoutTile[];
    }

### Properties

#### `tiles: SkyTileDashboardConfigLayoutTile[]`

An array of `SkyTileDashboardConfigTile` objects that specifies the tiles to include in the dashboard.

 SkyTileDashboardConfigLayoutTile
---------------------------------

Type: Interface

    interface SkyTileDashboardConfigLayoutTile {
      id: string;
      isCollapsed: boolean;
    }

### Properties

#### `id: string`

The ID of a tile to display in the dashboard.

#### `isCollapsed: boolean`

Whether the tile is in a collapsed state.

 SkyTileDashboardConfigTile
---------------------------

Type: Interface

    interface SkyTileDashboardConfigTile {
      componentType: any;
      id: string;
      providers?: any[];
    }

### Properties

#### `componentType: any`

The class type of the tile component.

#### `id: string`

The ID of the tile.

#### `providers?: any[]`

The array of data providers that can be passed to the tile.

 SkyTileDashboardConfigReorderData
----------------------------------

Type: Interface

    interface SkyTileDashboardConfigReorderData {
      column: number;
      position: number;
      tileDescription: string;
    }

### Properties

#### `column: number`

The column for the tile.

#### `position: number`

The position of the tile within the column.

#### `tileDescription: string`

The description of the tile.

 SkyTileDashboardMessage
------------------------

Type: Interface

Specifies the messages to be sent to the tile dashboard component.

    interface SkyTileDashboardMessage {
      type?: SkyTileDashboardMessageType;
    }

### Properties

#### `type?: SkyTileDashboardMessageType`

The type of message to send.

 SkyTileDashboardMessageType
----------------------------

Type: Enumeration

The type of message to send to the tile dashboard component.

    enum SkyTileDashboardMessageType {
      CollapseAll = 1,
      ExpandAll = 0,
    }

### Properties

#### `SkyTileDashboardMessageType.CollapseAll`

Collapses all tiles within the tile dashboard.

#### `SkyTileDashboardMessageType.ExpandAll`

Expands all tiles within the tile dashboard.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTileHarness
---------------

Type: Class

`import { SkyTileHarness } from '@skyux/tiles/testing';`

Harness to interact with a tile component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `clickSettingsButton(): Promise<void>`

Clicks the settings button.

#### Returns

`Promise<void>`

#### `collapse(): Promise<void>`

Collapses the tile, or does nothing if already collapsed.

#### Returns

`Promise<void>`

#### `expand(): Promise<void>`

Expands the tile, or does nothing if already expanded.

#### Returns

`Promise<void>`

#### `getContent(): Promise<SkyTileContentHarness>`

Gets a harness for the tile content.

#### Returns

`Promise<SkyTileContentHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getSummaryText(): Promise<string>`

Gets the tile summary text.

#### Returns

`Promise<string>`

#### `getTitleText(): Promise<string>`

Gets the tile title text.

#### Returns

`Promise<string>`

#### `isExpanded(): Promise<boolean>`

Whether the tile is expanded.

#### Returns

`Promise<boolean>`

#### `SkyTileHarness.with(filters: SkyTileHarnessFilters): HarnessPredicate<SkyTileHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTileHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTileHarnessFilters`

#### Returns

`HarnessPredicate<SkyTileHarness>`

 SkyTileHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTileHarness` instances.

    interface SkyTileHarnessFilters {
      dataSkyId?: string | RegExp;
      titleText?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `titleText?: string | RegExp`

Only find instances whose title matches the given value.

 SkyTileContentHarness
----------------------

Type: Class

`import { SkyTileContentHarness } from '@skyux/tiles/testing';`

Harness to interact with a tile content component in tests.

### Methods

#### `getSection(filter: SkyTileContentSectionHarnessFilters): Promise<SkyTileContentSectionHarness>`

Gets a specific tile content section based on the filter criteria.

#### Parameters

##### `filter: SkyTileContentSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTileContentSectionHarness>`

#### `getSections(filters?: SkyTileContentSectionHarnessFilters): Promise<SkyTileContentSectionHarness[]>`

Gets an array of tile content sections based on the filter criteria. If no filter is provided, returns all tile content sections.

#### Parameters

##### `filters?: SkyTileContentSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTileContentSectionHarness[]>`

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

 SkyTileContentSectionHarness
-----------------------------

Type: Class

`import { SkyTileContentSectionHarness } from '@skyux/tiles/testing';`

Harness to interact with a tile content section component in tests.

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

#### `SkyTileContentSectionHarness.with(filters: SkyTileContentSectionHarnessFilters): HarnessPredicate<SkyTileContentSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTileContentSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTileContentSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkyTileContentSectionHarness>`

 SkyTileContentSectionHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTileContentSectionHarness` instances.

    interface SkyTileContentSectionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTileDashboardHarness
------------------------

Type: Class

`import { SkyTileDashboardHarness } from '@skyux/tiles/testing';`

Harness to interact with a tile dashboard component in tests.

### Methods

#### `getTile(filter: SkyTileHarnessFilters): Promise<SkyTileHarness>`

Gets a specific tile based on the filter criteria.

#### Parameters

##### `filter: SkyTileHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTileHarness>`

#### `getTiles(filters?: SkyTileHarnessFilters): Promise<SkyTileHarness[]>`

Gets an array of tiles based on the filter criteria. If no filter is provided, returns all tiles.

#### Parameters

##### `filters?: SkyTileHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTileHarness[]>`

#### `isMultiColumn(): Promise<boolean>`

Whether or not the dashboard is in multi-column mode.

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

#### `SkyTileDashboardHarness.with(filters: SkyTileDashboardHarnessFilters): HarnessPredicate<SkyTileDashboardHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTileDashboardHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTileDashboardHarnessFilters`

#### Returns

`HarnessPredicate<SkyTileDashboardHarness>`

 SkyTileDashboardHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTileDashboardHarness` instances.

    interface SkyTileDashboardHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
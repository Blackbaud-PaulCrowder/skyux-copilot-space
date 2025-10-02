---
component: 'tile'
type: 'api-documentation'
description: 'API documentation for the tile component including components, interfaces, and types.'
---

# Tile API Documentation

## Components and Directives

#### TilesBasicExampleComponent

**Selector:** `app-tiles-basic-example`

**Package:** `@skyux/code-examples`

#### SkyTileContentSectionComponent

Specifies content to display inside a padded section of a SkyTileContentComponent.

**Selector:** `sky-tile-content-section`

**Package:** `@skyux/tiles`

#### SkyTileContentComponent

Specifies content to display in the tile's body.

**Selector:** `sky-tile-content`

**Package:** `@skyux/tiles`

#### SkyTileDashboardColumnComponent

**Selector:** `sky-tile-dashboard-column`

**Package:** `@skyux/tiles`

#### SkyTileDashboardComponent

Specifies a container to group multiple tiles.

**Selector:** `sky-tile-dashboard`

**Package:** `@skyux/tiles`

**Inputs:**

- `messageStream`: `Subject<SkyTileDashboardMessage>` - The observable to send commands to the tile dashboard. The commands must respect the
`SkyTileDashboardMessage` type.
- `settingsKey`: `string | undefined` - The unique key for the UI Config Service to retrieve stored settings
from a database. The UI Config Service saves configuration settings for users
to preserve the layout and collapsed state of tile dashboards. The UI Config Service relies on `id` values from the `config` property to maintain user settings. For more information
about the UI Config Service, see the
[sticky settings documentation](https://developer.blackbaud.com/skyux/learn/develop/sticky-settings).
- `config`: `SkyTileDashboardConfig | undefined` - Populates the tile dashboard based on the `SkyTileDashboardConfig` object.

**Outputs:**

- `configChange`: `EventEmitter<SkyTileDashboardConfig>` - Fires when the tile dashboard changes state and emits a SkyTileDashboardConfig
object. This occurs when tiles collapse or expand and when users drag and drop
tiles to rearrange them.

#### SkyTileSummaryComponent

Specifies content to display in the tile's summary.

**Selector:** `sky-tile-summary`

**Package:** `@skyux/tiles`

#### SkyTileTitleComponent

Specifies content to display in the tile's title.

**Selector:** `sky-tile-title`

**Package:** `@skyux/tiles`

#### SkyTileComponent

Provides a common look-and-feel for tab content.

**Selector:** `sky-tile`

**Package:** `@skyux/tiles`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `tileName`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
added to the tile header. Clicking the button invokes global help as configured by the application.
This property only applies when `tileName` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `tileName`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the tile header. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `tileName` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `showHelp`: `boolean` - Whether to display a help button in the tile header. To display the
button, you must also listen for the `helpClick` event. (default: true)
- `showSettings`: `boolean` - Whether to display a settings button in the tile header. To display the
button, you must also listen for the `settingsClick` event. (default: true)
- `tileName`: `string | undefined` - The human-readable name for the tile that is available to the tile controls for multiple purposes, such as accessibility and instrumentation. The component uses the name to construct ARIA labels for the help, expand/collapse, settings, and drag handle buttons to [support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For example, if the tile name is "Constituents," the help input's `aria-label` is "Constituents help" and the drag handle's `aria-label` is "Move Constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

**Outputs:**

- `helpClick`: `EventEmitter<any>` - Fires when users select the help button in the tile header. The help
button only appears when the `showHelp` property is set to `true`.
- `isCollapsedChange`: `EventEmitter<boolean>` - Fires when the tile's collapsed state changes. Returns `true` when the tile
collapses and `false` when it expands.
- `settingsClick`: `EventEmitter<any>` - Fires when users select the settings button in the tile header. The settings
button only appears when the `showSettings` property is set to `true`.
---
component: 'tile'
description: 'Design guidelines, API documentation, and usage instructions for the tile component extracted from SKY UX documentation.'
---

# Tile Component Guidelines

## Component Overview
Tiles create flexible containers to display content or features from external sources inside SKY UX applications.

## Usage

### ✅ Use when

Use tiles to display content or features from external sources on the Add-ins tab of record pages . As extension points in the SKY Add-ins framework, tiles are the primary container for external content in SKY UX applications. You can use a tile dashboard to automatically size and arrange tiles and to let users reorder or collapse/expand tiles to meet their specific needs.

For more information, see the SKY Add-ins documentation for tiles .

### ❌ Don't use when

Don't use tiles to organize native Blackbaud content and features or to define content categories within SKY UX applications. On record pages use boxes within fluid grids instead.

Don't use tiles to organize content within modals. For complex forms, use sectioned forms or other form containers instead.

## Anatomy

- Header
- Title
- Expand/collapse button
- Drag handle
- Content area
- Help inline button
- Settings button

## Options

### Help inline button

When you need to supplement a tile with additional information but don't require persistent inline help, you can place a help inline button beside the title to invoke contextual user assistance.

### Settings button

Show the settings button on a tile when users need to access add-in settings, authentication for connected services, or other configuration options. This button can launch whatever pattern is appropriate, such as opening a modal or a separate browser tab.

## Content

### Empty state

For tiles that are not populated, use empty-state help to explain how to use the tile.

## Related information

### Components

- Box
- Help inline button

### Guidelines

- Content containers
- Page design

## API Documentation

### Components and Directives

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

#### SkyTileContentModule

**Package:** `@skyux/tiles`

#### SkyTileDashboardColumnComponent

**Selector:** `sky-tile-dashboard-column`

**Package:** `@skyux/tiles`

#### SkyTileDashboardColumnModule

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfigLayoutColumn

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfigLayoutTile

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfigLayout

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfigReorderData

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfigTile

**Package:** `@skyux/tiles`

#### SkyTileDashboardConfig

**Package:** `@skyux/tiles`

#### SkyTileDashboardMessageType

The type of message to send to the tile dashboard component.

**Package:** `@skyux/tiles`

#### SkyTileDashboardMessage

Specifies the messages to be sent to the tile dashboard component.

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
- `config`: `SkyTileDashboardConfig | undefined` - Populates the tile dashboard based on the `SkyTileDashboardConfig` object. **[Required]**

**Outputs:**

- `configChange`: `EventEmitter<SkyTileDashboardConfig>` - Fires when the tile dashboard changes state and emits a SkyTileDashboardConfig
object. This occurs when tiles collapse or expand and when users drag and drop
tiles to rearrange them.

#### SkyTileDashboardModule

**Package:** `@skyux/tiles`

#### SkyTileDashboardService

**Package:** `@skyux/tiles`

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

#### SkyTileModule

**Package:** `@skyux/tiles`

#### SkyTilesModule

**Package:** `@skyux/tiles`

#### SkyTileContentHarness

Harness to interact with a tile content component in tests.

**Package:** `@skyux/tiles/testing`

#### SkyTileContentSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileContentSectionHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyTileContentSectionHarness

Harness to interact with a tile content section component in tests.

**Package:** `@skyux/tiles/testing`

#### SkyTileDashboardHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileDashboardHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyTileDashboardHarness

Harness to interact with a tile dashboard component in tests.

**Package:** `@skyux/tiles/testing`

#### SkyTileHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyTileHarness

Harness to interact with a tile component in tests.

**Package:** `@skyux/tiles/testing`

### Code Examples

#### Home page with blocks layout, using tile dashboard and recently accessed links

**Selector:** `app-pages-page-home-page-blocks-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyPageModule, SkyRecentLink } from '@skyux/pages';

import { HomePageContentComponent } from './home-page-content.component';

/**
 * @title Home page with blocks layout, using tile dashboard and recently accessed links
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-home-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [HomePageContentComponent, SkyIconModule, SkyPageModule],
})
export class PagesPageHomePageBlocksLayoutExampleComponent {
  protected readonly recentLinks: SkyRecentLink[] = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

**Template:**

```html
<sky-page layout="blocks">
  <sky-page-header pageTitle="Home">
    <sky-page-header-actions>
      <button type="button" class="sky-btn sky-btn-default">
        <sky-icon iconName="add" /> New
      </button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-home-page-content />
  </sky-page-content>

  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Resources">
      <sky-link-list-item>
        <a href="#">Help</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Support</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Training</a>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

```

#### Tile dashboard with basic setup

**Selector:** `app-tiles-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyTileDashboardConfig, SkyTilesModule } from '@skyux/tiles';

import { Tile1Component } from './tile1.component';
import { Tile2Component } from './tile2.component';

/**
 * @title Tile dashboard with basic setup
 */
@Component({
  selector: 'app-tiles-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyTilesModule],
})
export class TilesBasicExampleComponent {
  protected dashboardConfig: SkyTileDashboardConfig = {
    tiles: [
      {
        id: 'tile1',
        componentType: Tile1Component,
      },
      {
        id: 'tile2',
        componentType: Tile2Component,
      },
    ],
    layout: {
      singleColumn: {
        tiles: [
          {
            id: 'tile2',
            isCollapsed: false,
          },
          {
            id: 'tile1',
            isCollapsed: true,
          },
        ],
      },
      multiColumn: [
        {
          tiles: [
            {
              id: 'tile1',
              isCollapsed: true,
            },
          ],
        },
        {
          tiles: [
            {
              id: 'tile2',
              isCollapsed: false,
            },
          ],
        },
      ],
    },
  };
}

```

**Template:**

```html
<sky-tile-dashboard
  data-sky-id="basic-dashboard"
  [(config)]="dashboardConfig"
/>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
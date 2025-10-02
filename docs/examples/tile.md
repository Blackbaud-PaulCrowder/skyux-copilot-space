---
component: 'tile'
type: 'code-examples'
description: 'Code examples for the tile component.'
---

# Tile Code Examples

## Tile dashboard with basic setup

**Component:** TilesBasicExampleComponent

**Selector:** `app-tiles-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { By } from '@angular/platform-browser';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyMediaQueryTestingController,
  provideSkyMediaQueryTesting,
} from '@skyux/core/testing';
import { SkyTileDashboardHarness } from '@skyux/tiles/testing';

import { TilesBasicExampleComponent } from './example.component';

describe('Tile dashboard example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    tileDashboardHarness: SkyTileDashboardHarness;
    mediaQueryController: SkyMediaQueryTestingController;
    fixture: ComponentFixture<TilesBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [TilesBasicExampleComponent, NoopAnimationsModule],
      providers: [provideSkyMediaQueryTesting()],
    }).compileComponents();

    const mediaQueryController = TestBed.inject(SkyMediaQueryTestingController);

    const fixture = TestBed.createComponent(TilesBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const tileDashboardHarness: SkyTileDashboardHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyTileDashboardHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyTileDashboardHarness);

    return { tileDashboardHarness, mediaQueryController, fixture };
  }

  it('should set up the tile dashboard', async () => {
    const { tileDashboardHarness, mediaQueryController, fixture } =
      await setupTest();

    mediaQueryController.setBreakpoint('lg');

    await expectAsync(tileDashboardHarness.isMultiColumn()).toBeResolvedTo(
      true,
    );

    const tileHarness = await tileDashboardHarness.getTile({
      dataSkyId: 'tile-1',
    });

    await expectAsync(tileHarness.isExpanded()).toBeResolvedTo(false);
    await tileHarness.expand();
    await expectAsync(tileHarness.isExpanded()).toBeResolvedTo(true);

    const tile1Component = fixture.debugElement.query(By.css('div.tile1'));
    const settingsSpy = spyOn(
      tile1Component.componentInstance,
      'tileSettingsClick',
    );
    await tileHarness.clickSettingsButton();

    expect(settingsSpy).toHaveBeenCalled();

    const tileContentHarness = await tileHarness.getContent();

    const tileContentSectionHarness = await tileContentHarness.getSection({
      dataSkyId: 'section-1',
    });

    await expectAsync(
      (await tileContentSectionHarness.host()).text(),
    ).toBeResolvedTo('Section 1');
  });
});

```

#### example.component.ts

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

#### tile1.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTilesModule } from '@skyux/tiles';

@Component({
  // eslint-disable-next-line @angular-eslint/component-selector
  selector: 'div.tile1',
  templateUrl: './tile1.component.html',
  imports: [SkyTilesModule],
})
export class Tile1Component {
  public tileSettingsClick(): void {
    alert('tile settings clicked');
  }
}

```

#### tile2.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTilesModule } from '@skyux/tiles';

@Component({
  // eslint-disable-next-line @angular-eslint/component-selector
  selector: 'div.tile2',
  templateUrl: './tile2.component.html',
  imports: [SkyTilesModule],
})
export class Tile2Component {}

```

#### example.component.html

```html
<sky-tile-dashboard
  data-sky-id="basic-dashboard"
  [(config)]="dashboardConfig"
/>

```

#### tile1.component.html

```html
<sky-tile
  data-sky-id="tile-1"
  helpPopoverContent="Sample help information for tile 1."
  helpPopoverTitle="Sample help content"
  tileName="Tile 1"
  (settingsClick)="tileSettingsClick()"
>
  <sky-tile-title> Tile 1 </sky-tile-title>
  <sky-tile-summary> $123.4m </sky-tile-summary>
  <sky-tile-content>
    <sky-tile-content-section data-sky-id="section-1">
      Section 1
    </sky-tile-content-section>
    <sky-tile-content-section> Section 2 </sky-tile-content-section>
    <sky-tile-content-section> Section 3 </sky-tile-content-section>
  </sky-tile-content>
</sky-tile>

```

#### tile2.component.html

```html
<sky-tile helpKey="tile-2-help" tileName="Tile 2" [attr.data-sky-id]="'tile-2'">
  <sky-tile-title> Tile 2 </sky-tile-title>
  <sky-tile-content>
    <sky-tile-content-section> Section 1 </sky-tile-content-section>
    <sky-tile-content-section> Section 2 </sky-tile-content-section>
    <sky-tile-content-section> Section 3 </sky-tile-content-section>
  </sky-tile-content>
</sky-tile>

```

---
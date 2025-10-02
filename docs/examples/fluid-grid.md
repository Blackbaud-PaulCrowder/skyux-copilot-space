---
component: 'fluid-grid'
type: 'code-examples'
description: 'Code examples for the fluid-grid component.'
---

# Fluid Grid Code Examples

## Fluid grid with basic setup

**Component:** LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyColumnHarness,
  SkyFluidGridHarness,
  SkyRowHarness,
} from '@skyux/layout/testing';

import { LayoutFluidGridExampleComponent } from './example.component';

describe('Basic fluid grid', () => {
  async function setupTest(): Promise<{
    fluidGridHarness: SkyFluidGridHarness;
    fixture: ComponentFixture<LayoutFluidGridExampleComponent>;
    loader: HarnessLoader;
  }> {
    const fixture = TestBed.createComponent(LayoutFluidGridExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const fluidGridHarness = await loader.getHarness(
      SkyFluidGridHarness.with({
        dataSkyId: 'fluid-grid',
      }),
    );

    return { fluidGridHarness, fixture, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LayoutFluidGridExampleComponent],
    });
  });

  it('should display the correct fluid grid', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    const rows = await fluidGridHarness.getRows();

    expect(rows.length).toEqual(12);
  });

  it('should indicate the grid has margins', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(fluidGridHarness.hasMargin()).toBeResolvedTo(true);

    fixture.componentInstance.disableMargin = true;
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.hasMargin()).toBeResolvedTo(false);
  });

  it('should get the gutter size', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo('large');

    fixture.componentInstance.gutterSize = 'medium';
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo(
      'medium',
    );

    fixture.componentInstance.gutterSize = 'small';
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo('small');
  });

  it('should get the correct row harness', async () => {
    const { fixture, loader } = await setupTest();
    const rowHarness = await loader.getHarness(
      SkyRowHarness.with({ dataSkyId: 'test-row' }),
    );

    fixture.detectChanges();

    const columns = await rowHarness.getColumns();

    expect(columns.length).toEqual(12);
    await expectAsync(rowHarness.getColumnOrder()).toBeResolvedTo('normal');
  });

  it('should get the row direction from the row harness', async () => {
    const { fixture, loader } = await setupTest();
    const rowHarness = await loader.getHarness(
      SkyRowHarness.with({ dataSkyId: 'reverse-row' }),
    );

    fixture.detectChanges();

    await expectAsync(rowHarness.getColumnOrder()).toBeResolvedTo('reverse');
  });

  it('should get the correct column harness', async () => {
    const { fixture, loader } = await setupTest();
    const columnHarness = await loader.getHarness(
      SkyColumnHarness.with({ dataSkyId: 'test-column' }),
    );

    fixture.detectChanges();

    await expectAsync(columnHarness.getXSmallSize()).toBeResolvedTo(12);
    await expectAsync(columnHarness.getLargeSize()).toBeResolvedTo(1);
  });

  it('should get the column sizes from the column harness', async () => {
    const { fixture, loader } = await setupTest();
    const columnHarness = await loader.getHarness(
      SkyColumnHarness.with({ dataSkyId: 'dynamic-column' }),
    );

    fixture.detectChanges();

    await expectAsync(columnHarness.getXSmallSize()).toBeResolvedTo(6);
    await expectAsync(columnHarness.getSmallSize()).toBeResolvedTo(8);
    await expectAsync(columnHarness.getMediumSize()).toBeResolvedTo(9);
    await expectAsync(columnHarness.getLargeSize()).toBeResolvedTo(10);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyFluidGridGutterSizeType, SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Fluid grid with basic setup
 */
@Component({
  selector: 'app-layout-fluid-grid-example',
  templateUrl: './example.component.html',
  styles: [
    `
      .highlight-columns .sky-column {
        background-color: #97eced;
        border: 1px solid #56e0e1;
        overflow-wrap: break-word;
      }
    `,
  ],
  imports: [SkyFluidGridModule],
})
export class LayoutFluidGridExampleComponent {
  public gutterSize: SkyFluidGridGutterSizeType | undefined;
  public disableMargin = false;
}

```

#### example.component.html

```html
<div class="highlight-columns">
  <sky-fluid-grid
    data-sky-id="fluid-grid"
    [disableMargin]="disableMargin"
    [gutterSize]="gutterSize"
  >
    <sky-row data-sky-id="test-row">
      <sky-column data-sky-id="test-column" [screenSmall]="1">
        [screenSmall]="1"
      </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="5"> [screenSmall]="5" </sky-column>
      <sky-column [screenSmall]="7"> [screenSmall]="7" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="8"> [screenSmall]="8" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="9"> [screenSmall]="9" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="10"> [screenSmall]="10" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="11"> [screenSmall]="11" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column
        data-sky-id="dynamic-column"
        [screenXSmall]="6"
        [screenSmall]="8"
        [screenMedium]="9"
        [screenLarge]="10"
      >
        [screenXSmall]="6" [screenSmall]="8" [screenMedium]="9"
        [screenLarge]="10"
      </sky-column>
      <sky-column
        [screenXSmall]="6"
        [screenSmall]="4"
        [screenMedium]="3"
        [screenLarge]="2"
      >
        [screenXSmall]="6" [screenSmall]="4" [screenMedium]="3"
        [screenLarge]="2"
      </sky-column>
    </sky-row>

    <sky-row data-sky-id="reverse-row" [reverseColumnOrder]="true">
      <sky-column [screenSmall]="4"> First column </sky-column>
      <sky-column [screenSmall]="4"> Second column </sky-column>
      <sky-column [screenSmall]="4"> Third column </sky-column>
    </sky-row>
  </sky-fluid-grid>
</div>

```

---
---
component: 'toolbar'
type: 'code-examples'
description: 'Code examples for the toolbar component.'
---

# Toolbar Code Examples

## Toolbar with basic setup

**Component:** LayoutToolbarBasicExampleComponent

**Selector:** `app-layout-toolbar-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyToolbarHarness } from '@skyux/layout/testing';

import { LayoutToolbarBasicExampleComponent } from './example.component';

describe('Basic toolbar example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    toolbarHarness: SkyToolbarHarness;
    fixture: ComponentFixture<LayoutToolbarBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutToolbarBasicExampleComponent],
    }).compileComponents();

    const fixture = TestBed.createComponent(LayoutToolbarBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const toolbarHarness: SkyToolbarHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyToolbarHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyToolbarHarness);

    return { toolbarHarness, fixture };
  }

  it('should set up the toolbar', async () => {
    const { toolbarHarness, fixture } = await setupTest();

    const toolbarItem1 = await toolbarHarness.getItem({
      dataSkyId: 'toolbar-item-1',
    });
    const toolbarButton = await toolbarItem1.querySelector('button');

    const viewActionsHarness = await toolbarHarness.getViewActions();
    const expandButton = (
      await viewActionsHarness.querySelectorAll('button')
    )[0];

    const clickSpy = spyOn(fixture.componentInstance, 'onButtonClicked');
    await toolbarButton.click();
    await expandButton.click();
    expect(clickSpy).toHaveBeenCalledTimes(2);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyToolbarModule } from '@skyux/layout';

/**
 * @title Toolbar with basic setup
 */
@Component({
  selector: 'app-layout-toolbar-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule, SkyToolbarModule],
})
export class LayoutToolbarBasicExampleComponent {
  public onButtonClicked(buttonText: string): void {
    alert(buttonText + ' clicked!');
  }
}

```

#### example.component.html

```html
<sky-toolbar data-sky-id="basic-toolbar">
  <sky-toolbar-item data-sky-id="toolbar-item-1">
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="onButtonClicked('Button 1')"
    >
      Button 1
    </button>
  </sky-toolbar-item>
  <sky-toolbar-item data-sky-id="toolbar-item-2">
    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="onButtonClicked('Button 2')"
    >
      Button 2
    </button>
  </sky-toolbar-item>
  <sky-toolbar-view-actions>
    <button
      class="sky-btn sky-btn-default sky-btn-icon"
      title="Sort descending"
      type="button"
      (click)="onButtonClicked('Expand')"
    >
      <sky-icon iconName="chevron-double-down" />
    </button>
    <button
      class="sky-btn sky-btn-default sky-btn-icon"
      title="Sort ascending"
      type="button"
      (click)="onButtonClicked('Collapse')"
    >
      <sky-icon iconName="chevron-double-up" />
    </button>
  </sky-toolbar-view-actions>
</sky-toolbar>

```

---

## Toolbar with sections

**Component:** LayoutToolbarSectionedExampleComponent

**Selector:** `app-layout-toolbar-sectioned-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyToolbarHarness } from '@skyux/layout/testing';

import { LayoutToolbarSectionedExampleComponent } from './example.component';

describe('Sectioned toolbar example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    toolbarHarness: SkyToolbarHarness;
    fixture: ComponentFixture<LayoutToolbarSectionedExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutToolbarSectionedExampleComponent],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutToolbarSectionedExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const toolbarHarness: SkyToolbarHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyToolbarHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyToolbarHarness);

    return { toolbarHarness, fixture };
  }

  it('should set up the toolbar', async () => {
    const { toolbarHarness, fixture } = await setupTest();

    const toolbarSectionHarness = await toolbarHarness.getSection({
      dataSkyId: 'top-section',
    });

    const toolbarItem1 = await toolbarSectionHarness.getItem({
      dataSkyId: 'toolbar-item-1',
    });
    const toolbarButton = await toolbarItem1.querySelector('button');

    const viewActionsHarness = await toolbarSectionHarness.getViewActions();
    const expandButton = (
      await viewActionsHarness.querySelectorAll('button')
    )[0];

    const clickSpy = spyOn(fixture.componentInstance, 'onButtonClicked');
    await toolbarButton.click();
    await expandButton.click();
    expect(clickSpy).toHaveBeenCalledTimes(2);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyToolbarModule } from '@skyux/layout';

/**
 * @title Toolbar with sections
 */
@Component({
  selector: 'app-layout-toolbar-sectioned-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule, SkyToolbarModule],
})
export class LayoutToolbarSectionedExampleComponent {
  public onButtonClicked(buttonText: string): void {
    alert(buttonText + ' clicked!');
  }
}

```

#### example.component.html

```html
<sky-toolbar data-sky-id="sectioned-toolbar">
  <sky-toolbar-section data-sky-id="top-section">
    <sky-toolbar-item data-sky-id="toolbar-item-1">
      <button
        class="sky-btn sky-btn-primary"
        type="button"
        (click)="onButtonClicked('Button 1')"
      >
        Button 1
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item data-sky-id="toolbar-item-2">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Button 2')"
      >
        Button 2
      </button>
    </sky-toolbar-item>
    <sky-toolbar-view-actions>
      <button
        class="sky-btn sky-btn-default sky-btn-icon"
        title="Sort descending"
        type="button"
        (click)="onButtonClicked('Expand')"
      >
        <sky-icon iconName="chevron-double-down" />
      </button>
      <button
        class="sky-btn sky-btn-default sky-btn-icon"
        title="Sort ascending"
        type="button"
        (click)="onButtonClicked('Collapse')"
      >
        <sky-icon iconName="chevron-double-up" />
      </button>
    </sky-toolbar-view-actions>
  </sky-toolbar-section>
  <sky-toolbar-section data-sky-id="bottom-section">
    <sky-toolbar-item data-sky-id="sort-button">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Sort')"
      >
        <sky-icon iconName="arrow-sort" /> Sort
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item data-sky-id="filter-button">
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="onButtonClicked('Filter')"
      >
        <sky-icon iconName="filter" /> Filter
      </button>
    </sky-toolbar-item>
  </sky-toolbar-section>
</sky-toolbar>

```

---
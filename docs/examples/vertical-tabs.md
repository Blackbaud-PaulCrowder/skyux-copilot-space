---
component: 'vertical-tabs'
type: 'code-examples'
description: 'Code examples for the vertical-tabs component.'
---

# Vertical Tabs Code Examples

## Vertical tabs with basic setup

**Component:** TabsVerticalTabsBasicExampleComponent

**Selector:** `app-tabs-vertical-tabs-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsBasicExampleComponent } from './example.component';

describe('Basic vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set up vertical tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-basic' });

    const allTabs = await harness.getTabs();
    expect(allTabs.length).toBe(3);

    const activeTab = await harness.getActiveTab();
    expect(await activeTab?.getTabHeading()).toBe('Tab 2');
    const activeTabContent = await activeTab?.getTabContent();
    expect(await activeTabContent?.isVisible()).toBeTrue();

    const disabledTab = await harness.getTab({ tabHeading: 'Tab 3' });
    expect(await disabledTab?.isDisabled()).toBeTrue();
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

/**
 * @title Vertical tabs with basic setup
 */
@Component({
  selector: 'app-tabs-vertical-tabs-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsBasicExampleComponent {}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-basic">
  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 content </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 2" [active]="true">
    Tab 2 content
  </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

---

## Vertical tabs with grouped tabs

**Component:** TabsVerticalTabsGroupedExampleComponent

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsGroupedExampleComponent } from './example.component';

describe('Group vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsGroupedExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsGroupedExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsGroupedExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set up vertical tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-group' });

    const allTabs = await harness.getTabs();
    expect(allTabs.length).toBe(4);

    const groups = await harness.getGroups();
    expect(groups.length).toBe(3);

    const disabledGroup = await harness.getGroup({
      groupHeading: 'Disabled',
    });
    await expectAsync(disabledGroup?.isDisabled()).toBeResolvedTo(true);

    const group1Tab2 = await harness.getTab({ tabHeading: 'Group 1 — Tab 2' });
    await expectAsync(group1Tab2.getTabHeaderCount()).toBeResolvedTo(7);
  });

  it('should have active tab as the first tab in group 2', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-group' });

    // Two ways to get a tab inside a group
    // Through tabset harness
    const activeTab = await harness.getActiveTab();

    // Through group harness
    const group2 = await harness.getGroup({ groupHeading: 'Group 2' });
    await expectAsync(group2?.isActive()).toBeResolvedTo(true);

    const tab1 = await group2?.getVerticalTab({
      tabHeading: 'Group 2 — Tab 1',
    });

    const check =
      (await activeTab?.getTabHeading()) === (await tab1?.getTabHeading());
    expect(check).toBe(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-grouped-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsGroupedExampleComponent {
  protected groups: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: false,
      isDisabled: false,
      subTabs: [
        { tabHeading: 'Group 1 — Tab 1', content: 'Group 1 — Tab 1 Content' },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
          tabHeaderCount: 7,
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: true,
      isDisabled: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 2 — Tab 2 — Disabled',
          content: 'Group 2 — Tab 2 Content',
          disabled: true,
        },
      ],
    },
    {
      heading: 'Disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [],
    },
  ];
}

```

#### group.ts

```typescript
export interface TabGroup {
  heading: string;
  isOpen: boolean;
  isDisabled: boolean;
  subTabs: {
    tabHeading: string;
    content: string;
    tabHeaderCount?: number;
    active?: boolean;
    disabled?: boolean;
  }[];
}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-group" showTabsText="Tab list">
  @for (group of groups; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab
          [active]="tab.active"
          [tabHeading]="tab.tabHeading"
          [tabHeaderCount]="tab.tabHeaderCount"
          [disabled]="tab.disabled"
        >
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }
</sky-vertical-tabset>

```

---

## Vertical tabs with grouped and ungrouped tabs

**Component:** TabsVerticalTabsMixedExampleComponent

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsMixedExampleComponent } from './example.component';

describe('Mixed vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsMixedExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsMixedExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsMixedExampleComponent, NoopAnimationsModule],
    });
  });

  it('should show grouped and ungrouped tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-mixed' });

    // Test grouped tabs
    const group1 = await harness.getGroup({ groupHeading: 'Group 1' });
    expect(group1).toBeTruthy();
    expect(await group1?.isOpen()).toBe(true);

    const group2 = await harness.getGroup({ groupHeading: 'Group 2' });
    expect(group2).toBeTruthy();
    expect(await group2?.isOpen()).toBe(false);

    // Test ungrouped tabs
    const tab1 = await harness.getTab({ tabHeading: 'Tab 1' });
    expect(tab1).toBeTruthy();

    const tab2 = await harness.getTab({ tabHeading: 'Tab 2' });
    expect(tab2).toBeTruthy();
    expect(await tab2?.getTabHeaderCount()).toBe(3);

    const tab3 = await harness.getTab({ tabHeading: 'Tab 3' });
    expect(tab3).toBeTruthy();
    expect(await tab3?.isDisabled()).toBe(true);
  });

  it('should have the group 1 tab 1 active by default', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-mixed' });

    const group1Tab1 = await harness.getTab({ tabHeading: 'Group 1 — Tab 1' });
    expect(group1Tab1).toBeTruthy();
    expect(await group1Tab1?.isActive()).toBe(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped and ungrouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-mixed-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsMixedExampleComponent {
  protected groupedTabs: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: true,
      subTabs: [
        {
          tabHeading: 'Group 1 — Tab 1',
          content: 'Group 1 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 2 — Tab 2',
          content: 'Group 2 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 3 - disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [
        {
          tabHeading: 'Group 3 — Tab 1',
          content: 'Group 3 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 3 — Tab 2',
          content: 'Group 3 — Tab 2 Content',
        },
      ],
    },
  ];
}

```

#### group.ts

```typescript
export interface TabGroup {
  heading: string;
  isOpen: boolean;
  isDisabled?: boolean;
  subTabs: {
    tabHeading: string;
    content: string;
    tabHeaderCount?: number;
    active?: boolean;
    disabled?: boolean;
  }[];
}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-mixed" showTabsText="Tab list">
  @for (group of groupedTabs; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab [active]="tab.active" [tabHeading]="tab.tabHeading">
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }

  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 Content </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 2" [tabHeaderCount]="3">
    Tab 2 Content
  </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 Content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

---
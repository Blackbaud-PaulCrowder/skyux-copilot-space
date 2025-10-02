---
component: 'list'
type: 'code-examples'
description: 'Code examples for the list component.'
---

# List Code Examples

## Definition list with basic setup

**Component:** LayoutDefinitionListBasicExampleComponent

**Selector:** `app-layout-definition-list-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDefinitionListModule } from '@skyux/layout';

/**
 * @title Definition list with basic setup
 */
@Component({
  selector: 'app-layout-definition-list-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDefinitionListModule],
})
export class LayoutDefinitionListBasicExampleComponent {
  protected items: { label: string; value?: string }[] = [
    {
      label: 'Field 1',
      value: 'Field 1 value',
    },
    {
      label: 'Field 2',
      value: 'Field 2 value',
    },
    {
      label: 'Field 3',
      value: undefined,
    },
    {
      label: 'Field 4',
      value: 'Field 4 value',
    },
  ];
}

```

#### example.component.html

```html
<sky-definition-list>
  <sky-definition-list-heading>
    Definition list heading
  </sky-definition-list-heading>
  @for (item of items; track item) {
    <sky-definition-list-content>
      <sky-definition-list-label>
        {{ item.label }}
      </sky-definition-list-label>
      <sky-definition-list-value>
        {{ item.value }}
      </sky-definition-list-value>
    </sky-definition-list-content>
  }
</sky-definition-list>

```

---

## Description list with help key

**Component:** LayoutDescriptionListHelpKeyExampleComponent

**Selector:** `app-layout-description-list-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyDescriptionListHarness } from '@skyux/layout/testing';

import { LayoutDescriptionListHelpKeyExampleComponent } from './example.component';

describe('Help key description list', () => {
  async function setupTest(): Promise<{
    descriptionListHarness: SkyDescriptionListHarness;
    fixture: ComponentFixture<LayoutDescriptionListHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        LayoutDescriptionListHelpKeyExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutDescriptionListHelpKeyExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const helpController = TestBed.inject(SkyHelpTestingController);

    const descriptionListHarness: SkyDescriptionListHarness =
      await loader.getHarness(SkyDescriptionListHarness);

    return { descriptionListHarness, fixture, helpController };
  }

  it('should set up the component', async () => {
    const { descriptionListHarness, fixture, helpController } =
      await setupTest();

    await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
      'horizontal',
    );

    const content = await descriptionListHarness.getContent();

    expect(content.length).toBe(4);

    await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
    await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
      'Humanities and Social Sciences',
    );

    await content[0].clickHelpInline();
    fixture.detectChanges();
    await fixture.whenStable();

    helpController.expectCurrentHelpKey('college-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Description list with help key
 */
@Component({
  selector: 'app-layout-description-list-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListHelpKeyExampleComponent {
  protected items: { term: string; description: string; helpKey?: string }[] = [
    {
      term: 'College',
      description: 'Humanities and Social Sciences',
      helpKey: 'college-help',
    },
    {
      term: 'Department',
      description: 'Anthropology',
    },
    {
      term: 'Advisor',
      description: 'Cathy Green',
    },
    {
      term: 'Class year',
      description: '2024',
    },
  ];
}

```

#### example.component.html

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpKey]="item.helpKey">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

---

## Horizontal mode

**Component:** LayoutDescriptionListHorizontalExampleComponent

**Selector:** `app-layout-description-list-horizontal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyHelpTestingModule } from '@skyux/core/testing';
import { SkyDescriptionListHarness } from '@skyux/layout/testing';

import { LayoutDescriptionListHorizontalExampleComponent } from './example.component';

describe('Horizontal description list', () => {
  async function setupTest(): Promise<{
    descriptionListHarness: SkyDescriptionListHarness;
    fixture: ComponentFixture<LayoutDescriptionListHorizontalExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        LayoutDescriptionListHorizontalExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutDescriptionListHorizontalExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const descriptionListHarness: SkyDescriptionListHarness =
      await loader.getHarness(SkyDescriptionListHarness);

    return { descriptionListHarness, fixture };
  }

  it('should set up the component', async () => {
    const { descriptionListHarness, fixture } = await setupTest();

    await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
      'horizontal',
    );

    const content = await descriptionListHarness.getContent();

    expect(content.length).toBe(4);

    await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
    await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
      'Humanities and Social Sciences',
    );

    await content[2].clickHelpInline();
    fixture.detectChanges();
    await fixture.whenStable();
    await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
      'The faculty member who advises the student.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Horizontal mode
 */
@Component({
  selector: 'app-layout-description-list-horizontal-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListHorizontalExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];
}

```

#### example.component.html

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

---

## Description list with inline help

**Component:** LayoutDescriptionListInlineHelpExampleComponent

**Selector:** `app-layout-description-list-inline-help-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyHelpTestingModule } from '@skyux/core/testing';
import { SkyDescriptionListHarness } from '@skyux/layout/testing';

import { LayoutDescriptionListInlineHelpExampleComponent } from './example.component';

describe('Horizontal description list', () => {
  async function setupTest(): Promise<{
    descriptionListHarness: SkyDescriptionListHarness;
    fixture: ComponentFixture<LayoutDescriptionListInlineHelpExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        LayoutDescriptionListInlineHelpExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutDescriptionListInlineHelpExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const descriptionListHarness: SkyDescriptionListHarness =
      await loader.getHarness(SkyDescriptionListHarness);

    return { descriptionListHarness, fixture };
  }

  it('should set up the component', async () => {
    const { descriptionListHarness, fixture } = await setupTest();

    await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
      'horizontal',
    );

    const content = await descriptionListHarness.getContent();

    expect(content.length).toBe(4);

    await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
    await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
      'Humanities and Social Sciences',
    );

    await content[2].clickHelpInline();
    fixture.detectChanges();
    await fixture.whenStable();
    await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
      'The faculty member who advises the student.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Description list with inline help
 */
@Component({
  selector: 'app-layout-description-list-inline-help-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule, SkyHelpInlineModule],
})
export class LayoutDescriptionListInlineHelpExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];

  protected onActionClick(): void {
    alert('Help inline button clicked!');
  }
}

```

#### example.component.html

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
        <sky-help-inline
          ariaLabel="Information about {{ item.term }}"
          class="sky-control-help"
          (actionClick)="onActionClick()"
        />
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

---

## Long-description mode

**Component:** LayoutDescriptionListLongDescriptionExampleComponent

**Selector:** `app-layout-description-list-long-description-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyHelpTestingModule } from '@skyux/core/testing';
import { SkyDescriptionListHarness } from '@skyux/layout/testing';

import { LayoutDescriptionListLongDescriptionExampleComponent } from './example.component';

describe('Long description list', () => {
  async function setupTest(): Promise<{
    descriptionListHarness: SkyDescriptionListHarness;
    fixture: ComponentFixture<LayoutDescriptionListLongDescriptionExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        LayoutDescriptionListLongDescriptionExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutDescriptionListLongDescriptionExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const descriptionListHarness: SkyDescriptionListHarness =
      await loader.getHarness(SkyDescriptionListHarness);

    return { descriptionListHarness, fixture };
  }

  it('should set up the component', async () => {
    const { descriptionListHarness } = await setupTest();

    await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
      'longDescription',
    );

    const content = await descriptionListHarness.getContent();

    expect(content.length).toBe(3);

    await expectAsync(content[0].getTermText()).toBeResolvedTo(
      'Good Health and Well-being',
    );
    await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
      'Ensure healthy lives and promote well-being for all at all ages.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Long-description mode
 */
@Component({
  selector: 'app-layout-description-list-long-description-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListLongDescriptionExampleComponent {
  protected items: { term: string; description: string }[] = [
    {
      term: 'Good Health and Well-being',
      description:
        'Ensure healthy lives and promote well-being for all at all ages.',
    },
    {
      term: 'Quality Education',
      description:
        'Ensure inclusive and equitable quality education and promote lifelong learning opportunities for all.',
    },
    {
      term: 'Gender Equity',
      description: 'Achieve gender equality and empower all women and girls.',
    },
  ];
}

```

#### example.component.html

```html
<sky-description-list mode="longDescription">
  @for (item of items; track item) {
    <sky-description-list-content>
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

---

## Vertical mode

**Component:** LayoutDescriptionListVerticalExampleComponent

**Selector:** `app-layout-description-list-vertical-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyHelpTestingModule } from '@skyux/core/testing';
import { SkyDescriptionListHarness } from '@skyux/layout/testing';

import { LayoutDescriptionListVerticalExampleComponent } from './example.component';

describe('Vertical description list', () => {
  async function setupTest(): Promise<{
    descriptionListHarness: SkyDescriptionListHarness;
    fixture: ComponentFixture<LayoutDescriptionListVerticalExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        LayoutDescriptionListVerticalExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutDescriptionListVerticalExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const descriptionListHarness: SkyDescriptionListHarness =
      await loader.getHarness(SkyDescriptionListHarness);

    return { descriptionListHarness, fixture };
  }

  it('should set up the component', async () => {
    const { descriptionListHarness, fixture } = await setupTest();

    await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
      'vertical',
    );

    const content = await descriptionListHarness.getContent();

    expect(content.length).toBe(4);

    await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
    await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
      'Humanities and Social Sciences',
    );

    await content[2].clickHelpInline();
    fixture.detectChanges();
    await fixture.whenStable();
    await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
      'The faculty member who advises the student.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Vertical mode
 */
@Component({
  selector: 'app-layout-description-list-vertical-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListVerticalExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];
}

```

#### example.component.html

```html
<sky-description-list mode="vertical">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

---

## Expandable inline filter

**Component:** ListsFilterInlineExampleComponent

**Selector:** `app-lists-filter-inline-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyCheckboxHarness } from '@skyux/forms/testing';
import {
  SkyFilterButtonHarness,
  SkyFilterInlineHarness,
} from '@skyux/lists/testing';

import { ListsFilterInlineExampleComponent } from './example.component';

describe('Filter inline example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    filterButtonHarness: SkyFilterButtonHarness;
    fixture: ComponentFixture<ListsFilterInlineExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsFilterInlineExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsFilterInlineExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const filterButtonHarness: SkyFilterButtonHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyFilterButtonHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyFilterButtonHarness);

    return { filterButtonHarness, fixture, loader };
  }

  it('should set up the component', async () => {
    const { filterButtonHarness, fixture, loader } = await setupTest({
      dataSkyId: 'my-filter-button',
    });

    await filterButtonHarness.clickFilterButton();
    fixture.detectChanges();
    await fixture.whenStable();

    const filterInlineHarness = await loader.getHarness(
      SkyFilterInlineHarness.with({ dataSkyId: 'filter-inline' }),
    );

    const itemHarness = await filterInlineHarness.getItem({
      dataSkyId: 'hide-orange-filter',
    });
    const orangeCheck = await itemHarness.queryHarness(SkyCheckboxHarness);
    await orangeCheck.check();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(filterButtonHarness.isActive()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';

interface Filter {
  name: string;
  value: string | boolean;
}

interface Fruit {
  name: string;
  type: string;
  color: string;
}

/**
 * @title Expandable inline filter
 */
@Component({
  selector: 'app-lists-filter-inline-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyCheckboxModule,
    SkyIdModule,
    SkyFilterModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkyToolbarModule,
  ],
})
export class ListsFilterInlineExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected filtersActive = false;
  protected fruitType = 'any';
  protected hideOrange = false;

  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected filterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected fruitTypeChange(newValue: string): void {
    this.fruitType = newValue;
    this.#setFilterActiveState();
  }

  protected hideOrangeChange(newValue: boolean): void {
    this.hideOrange = newValue;
    this.#setFilterActiveState();
  }

  #setFilterActiveState(): void {
    this.appliedFilters = [];

    if (this.fruitType !== 'any') {
      this.appliedFilters.push({
        name: 'fruitType',
        value: this.fruitType,
      });
    }

    if (this.hideOrange) {
      this.appliedFilters.push({
        name: 'hideOrange',
        value: true,
      });
    }

    this.filtersActive = this.appliedFilters.length > 0;
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [active]="filtersActive"
        [ariaControls]="inlineFilters.id"
        [ariaExpanded]="showInlineFilters"
        [showButtonText]="true"
        (filterButtonClick)="filterButtonClicked()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
</sky-toolbar>

<div #inlineFilters skyId [hidden]="!showInlineFilters">
  <sky-filter-inline data-sky-id="filter-inline">
    <sky-filter-inline-item data-sky-id="fruit-filter">
      <sky-input-box labelText="Fruit type">
        <select [ngModel]="fruitType" (ngModelChange)="fruitTypeChange($event)">
          <option value="any">Any fruit</option>
          <option value="citrus">Citrus</option>
          <option value="berry">Berry</option>
        </select>
      </sky-input-box>
    </sky-filter-inline-item>
    <sky-filter-inline-item data-sky-id="hide-orange-filter">
      <sky-checkbox
        labelText="Hide orange fruits"
        [ngModel]="hideOrange"
        (ngModelChange)="hideOrangeChange($event)"
      />
    </sky-filter-inline-item>
  </sky-filter-inline>
</div>

<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

---

## Modal filter

**Component:** ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyFilterButtonHarness,
  SkyFilterSummaryHarness,
} from '@skyux/lists/testing';
import {
  SkyModalTestingController,
  SkyModalTestingModule,
} from '@skyux/modals/testing';

import { ListsFilterModalExampleComponent } from './example.component';
import { Filter } from './filter';
import { FilterModalComponent } from './filter-modal.component';

describe('Filter modal example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    filterButtonHarness: SkyFilterButtonHarness;
    fixture: ComponentFixture<ListsFilterModalExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        ListsFilterModalExampleComponent,
        SkyModalTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsFilterModalExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const filterButtonHarness: SkyFilterButtonHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyFilterButtonHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyFilterButtonHarness);

    return { filterButtonHarness, fixture, loader };
  }

  it('should set up the component', async () => {
    const { filterButtonHarness, fixture, loader } = await setupTest({
      dataSkyId: 'my-filter-button',
    });

    const modalController = TestBed.inject(SkyModalTestingController);

    await filterButtonHarness.clickFilterButton();
    fixture.detectChanges();
    await fixture.whenStable();

    const saveData: Filter[] = [
      {
        name: 'fruitType',
        value: 'citrus',
        label: 'citrus',
      },
      {
        name: 'hideOrange',
        value: true,
        label: 'hide orange fruits',
      },
    ];
    modalController.expectCount(1);
    modalController.expectOpen(FilterModalComponent);
    modalController.closeTopModal({ data: saveData, reason: 'save' });

    const filterSummaryHarness = await loader.getHarness(
      SkyFilterSummaryHarness.with({ dataSkyId: 'filter-summary' }),
    );

    let filterSummaryItemHarnesses = await filterSummaryHarness.getItems();

    expect(filterSummaryItemHarnesses.length).toBe(2);

    await filterSummaryItemHarnesses[0].dismiss();

    filterSummaryItemHarnesses = await filterSummaryHarness.getItems();

    expect(filterSummaryItemHarnesses.length).toBe(1);
  });
});

```

#### example.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';
import { FilterModalComponent } from './filter-modal.component';
import { Fruit } from './fruit';

/**
 * @title Modal filter
 */
@Component({
  selector: 'app-lists-filter-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyFilterModule, SkyRepeaterModule, SkyToolbarModule],
})
export class ListsFilterModalExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected onDismiss(index: number): void {
    this.appliedFilters.splice(index, 1);
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  protected onInlineFilterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected onModalFilterButtonClick(): void {
    const modalInstance = this.#modalSvc.open(FilterModalComponent, [
      {
        provide: FilterModalContext,
        useValue: {
          appliedFilters: this.appliedFilters,
        },
      },
    ]);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'save') {
        this.appliedFilters = (result.data as Filter[]).slice();
        this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
        this.#changeDetectorRef.markForCheck();
      }
    });
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }
}

```

#### filter-modal-context.ts

```typescript
import { Filter } from './filter';

export class FilterModalContext {
  public appliedFilters: Filter[] = [];
}

```

#### filter-modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';

@Component({
  selector: 'app-filter-modal',
  templateUrl: './filter-modal.component.html',
  imports: [FormsModule, SkyCheckboxModule, SkyInputBoxModule, SkyModalModule],
})
export class FilterModalComponent {
  protected hideOrange = false;
  protected fruitType = 'any';

  protected readonly context = inject(FilterModalContext);
  protected readonly instance = inject(SkyModalInstance);

  constructor() {
    if (this.context.appliedFilters.length > 0) {
      this.#setFormFilters(this.context.appliedFilters);
    } else {
      this.clearAllFilters();
    }
  }

  protected applyFilters(): void {
    const result = this.#getAppliedFiltersArray();
    this.instance.save(result);
  }

  protected cancel(): void {
    this.instance.cancel();
  }

  protected clearAllFilters(): void {
    this.hideOrange = false;
    this.fruitType = 'any';
  }

  #getAppliedFiltersArray(): Filter[] {
    const appliedFilters: Filter[] = [];

    if (this.fruitType !== 'any') {
      appliedFilters.push({
        name: 'fruitType',
        value: this.fruitType,
        label: this.fruitType,
      });
    }

    if (this.hideOrange) {
      appliedFilters.push({
        name: 'hideOrange',
        value: true,
        label: 'hide orange fruits',
      });
    }

    return appliedFilters;
  }

  #setFormFilters(appliedFilters: Filter[]): void {
    for (const appliedFilter of appliedFilters) {
      if (appliedFilter.name === 'fruitType') {
        this.fruitType = `${appliedFilter.value}`;
      }

      if (appliedFilter.name === 'hideOrange') {
        this.hideOrange = !!appliedFilter.value;
      }
    }
  }
}

```

#### filter.ts

```typescript
export interface Filter {
  name: string;
  value: string | boolean;
  label: string;
}

```

#### fruit.ts

```typescript
export interface Fruit {
  name: string;
  type: string;
  color: string;
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [showButtonText]="true"
        (filterButtonClick)="onModalFilterButtonClick()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
  @if (appliedFilters && appliedFilters.length > 0) {
    <sky-toolbar-section>
      <sky-filter-summary data-sky-id="filter-summary">
        @for (item of appliedFilters; track item; let i = $index) {
          <sky-filter-summary-item (dismiss)="onDismiss(i)">
            {{ item.label }}
          </sky-filter-summary-item>
        }
      </sky-filter-summary>
    </sky-toolbar-section>
  }
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### filter-modal.component.html

```html
<sky-modal headingText="Filter food preferences">
  <sky-modal-content>
    <sky-input-box labelText="Fruit type" stacked="true">
      <select [(ngModel)]="fruitType">
        <option value="any">Any fruit</option>
        <option value="citrus">Citrus</option>
        <option value="berry">Berry</option>
      </select>
    </sky-input-box>
    <sky-checkbox labelText="Hide orange fruits" [(ngModel)]="hideOrange" />
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="applyFilters()"
    >
      Apply
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="clearAllFilters()"
    >
      Clear
    </button>
    <button class="sky-btn sky-btn-link" type="button" (click)="cancel()">
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

---

## Infinite scroll with repeater

**Component:** ListsInfiniteScrollRepeaterExampleComponent

**Selector:** `app-lists-infinite-scroll-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';

import { ListsInfiniteScrollRepeaterExampleComponent } from './example.component';

describe('Infinite scroll example', () => {
  async function setupTest(): Promise<{
    infiniteScrollHarness: SkyInfiniteScrollHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        ListsInfiniteScrollRepeaterExampleComponent,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      ListsInfiniteScrollRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const infiniteScrollHarness: SkyInfiniteScrollHarness =
      await loader.getHarness(SkyInfiniteScrollHarness);

    return { infiniteScrollHarness };
  }

  it('should set up the component', async () => {
    const { infiniteScrollHarness } = await setupTest();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);

    await infiniteScrollHarness.loadMore();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);

    await infiniteScrollHarness.loadMore();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(false);

    await expectAsync(infiniteScrollHarness.loadMore()).toBeRejectedWithError(
      'Unable to click the "Load more" button because the infinite scroll is not enabled.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnInit } from '@angular/core';
import { SkyInfiniteScrollModule, SkyRepeaterModule } from '@skyux/lists';

import { InfiniteScrollDemoItem } from './item';

let nextId = 0;

/**
 * @title Infinite scroll with repeater
 */
@Component({
  selector: 'app-lists-infinite-scroll-repeater-example',
  styles: `
    .wrapper {
      overflow-y: auto;
      max-height: 500px;
      position: relative;
    }
  `,
  templateUrl: './example.component.html',
  imports: [SkyInfiniteScrollModule, SkyRepeaterModule],
})
export class ListsInfiniteScrollRepeaterExampleComponent implements OnInit {
  protected items: InfiniteScrollDemoItem[] = [];
  protected itemsHaveMore = true;

  public ngOnInit(): void {
    void this.#addData();
  }

  protected onScrollEnd(): void {
    if (this.itemsHaveMore) {
      void this.#addData();
    }
  }

  async #addData(): Promise<void> {
    const result = await this.#mockRemote();
    this.items = this.items.concat(result.data);
    this.itemsHaveMore = result.hasMore;
  }

  #mockRemote(): Promise<{
    data: InfiniteScrollDemoItem[];
    hasMore: boolean;
  }> {
    const data: InfiniteScrollDemoItem[] = [];

    for (let i = 0; i < 20; i++) {
      data.push({
        name: `Item #${++nextId}`,
      });
    }

    // Simulate async request.
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve({
          data,
          hasMore: nextId < 50,
        });
      }, 1000);
    });
  }
}

```

#### item.ts

```typescript
export interface InfiniteScrollDemoItem {
  name: string;
}

```

#### example.component.html

```html
<div class="wrapper">
  <sky-repeater>
    @for (item of items; track item) {
      <sky-repeater-item>
        <sky-repeater-item-title>
          {{ item.name }}
        </sky-repeater-item-title>
      </sky-repeater-item>
    }
  </sky-repeater>
  <sky-infinite-scroll [enabled]="itemsHaveMore" (scrollEnd)="onScrollEnd()" />
</div>

```

---

## Paging with basic setup

**Component:** ListsPagingBasicExampleComponent

**Selector:** `app-lists-paging-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPagingModule } from '@skyux/lists';

/**
 * @title Paging with basic setup
 */
@Component({
  selector: 'app-lists-paging-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyPagingModule],
})
export class ListsPagingBasicExampleComponent {
  protected currentPage = 1;
}

```

#### example.component.html

```html
<sky-paging
  [itemCount]="8"
  [maxPages]="3"
  [pageSize]="2"
  [(currentPage)]="currentPage"
/>

<p>The current page is {{ currentPage }}.</p>

```

---

## Paging with content wrapper

**Component:** ListsPagingWithContentExampleComponent

**Selector:** `app-lists-paging-with-content-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### demo-data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, delay, of } from 'rxjs';

import { DemoData } from './demo-data';

const people = [
  {
    name: 'Abed',
    formal: 'Mr. Nadir',
  },
  {
    name: 'Alex',
    formal: 'Mr. Osbourne',
  },
  {
    name: 'Ben',
    formal: 'Mr. Chang',
  },
  {
    name: 'Britta',
    formal: 'Ms. Perry',
  },
  {
    name: 'Buzz',
    formal: 'Mr. Hickey',
  },
  {
    name: 'Craig',
    formal: 'Mr. Pelton',
  },
  {
    name: 'Elroy',
    formal: 'Mr. Patashnik',
  },
  {
    name: 'Garrett',
    formal: 'Mr. Lambert',
  },
  {
    name: 'Ian',
    formal: 'Mr. Duncan',
  },
  {
    name: 'Jeff',
    formal: 'Mr. Winger',
  },
  {
    name: 'Leonard',
    formal: 'Mr. Rodriguez',
  },
  {
    name: 'Neil',
    formal: 'Mr. Neil',
  },
  {
    name: 'Pierce',
    formal: 'Mr. Hawthorne',
  },
  {
    name: 'Preston',
    formal: 'Mr. Koogler',
  },
  {
    name: 'Rachel',
    formal: 'Ms. Rachel',
  },
  {
    name: 'Shirley',
    formal: 'Ms. Bennett',
  },
  {
    name: 'Todd',
    formal: 'Mr. Jacobson',
  },
  {
    name: 'Troy',
    formal: 'Mr. Barnes',
  },
  {
    name: 'Vaughn',
    formal: 'Mr. Miller',
  },
  {
    name: 'Vicki',
    formal: 'Ms. Jenkins',
  },
];

@Injectable({
  providedIn: 'root',
})
export class DemoDataService {
  public getPagedData(
    pageNumber: number,
    itemCount: number,
  ): Observable<DemoData> {
    const startIndex = (pageNumber - 1) * itemCount;

    return of({
      people: people.slice(startIndex, startIndex + itemCount),
      totalCount: people.length,
    }).pipe(
      // Simulate network latency.
      delay(1000),
    );
  }
}

```

#### demo-data.ts

```typescript
import { Person } from './person';

export interface DemoData {
  people: Person[];
  totalCount: number;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyPagingHarness, SkyRepeaterHarness } from '@skyux/lists/testing';

import { ListsPagingWithContentExampleComponent } from './example.component';

describe('Paging example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    pagingHarness: SkyPagingHarness;
    fixture: ComponentFixture<ListsPagingWithContentExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsPagingWithContentExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      ListsPagingWithContentExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const pagingHarness: SkyPagingHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyPagingHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyPagingHarness);

    return { pagingHarness, fixture };
  }

  it('should set up the paging content', async () => {
    const { pagingHarness, fixture } = await setupTest({
      dataSkyId: 'my-paging-content',
    });

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(1);

    const contentHarness = await (
      await pagingHarness.getPagingContent()
    ).queryHarness(SkyRepeaterHarness);

    let items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Abed');

    await pagingHarness.clickPageButton(3);

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(3);

    items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Leonard');

    await pagingHarness.clickNextButton();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(4);

    items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Shirley');

    await expectAsync(pagingHarness.clickNextButton()).toBeRejectedWithError(
      'Could not click the next button because it is disabled.',
    );

    await expectAsync(pagingHarness.clickPageButton(1)).toBeRejectedWithError(
      'Could not find page button 1.',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';
import {
  SkyPagingContentChangeArgs,
  SkyPagingModule,
  SkyRepeaterModule,
} from '@skyux/lists';

import { Subject, shareReplay, switchMap, tap } from 'rxjs';

import { DemoDataService } from './demo-data.service';

/**
 * @title Paging with content wrapper
 */
@Component({
  selector: 'app-lists-paging-with-content-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    SkyDescriptionListModule,
    SkyPagingModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class ListsPagingWithContentExampleComponent {
  #demoDataSvc = inject(DemoDataService);

  protected currentPage = 1;
  protected pageSize = 5;
  protected contentChange = new Subject<SkyPagingContentChangeArgs>();

  protected pagedData = this.contentChange.pipe(
    switchMap((args) =>
      this.#demoDataSvc.getPagedData(args.currentPage, this.pageSize).pipe(
        tap(() => {
          args.loadingComplete();
        }),
      ),
    ),
    shareReplay(1),
  );
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
  formal: string;
}

```

#### example.component.html

```html
<sky-paging
  data-sky-id="my-paging-content"
  [itemCount]="(pagedData | async)?.totalCount ?? 0"
  [maxPages]="3"
  [pageSize]="pageSize"
  [(currentPage)]="currentPage"
  (contentChange)="contentChange.next($event)"
>
  <sky-paging-content>
    <sky-repeater>
      @for (person of (pagedData | async)?.people; track person) {
        <sky-repeater-item>
          <sky-repeater-item-title>
            {{ person.name }}
          </sky-repeater-item-title>
          <sky-repeater-item-content>
            <sky-description-list>
              <sky-description-list-content>
                <sky-description-list-term>
                  Formal name
                </sky-description-list-term>
                <sky-description-list-description>
                  {{ person.formal }}
                </sky-description-list-description>
              </sky-description-list-content>
            </sky-description-list>
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  </sky-paging-content>
</sky-paging>

```

---

## Repeater with drag and drop, removable items

**Component:** ListsRepeaterAddRemoveExampleComponent

**Selector:** `app-lists-repeater-add-remove-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyRepeaterHarness } from '@skyux/lists/testing';

import { ListsRepeaterAddRemoveExampleComponent } from './example.component';

describe('Repeater add remove example', () => {
  async function setupTest(): Promise<{
    el: HTMLElement;
    fixture: ComponentFixture<ListsRepeaterAddRemoveExampleComponent>;
    repeaterHarness: SkyRepeaterHarness;
  }> {
    const fixture = TestBed.createComponent(
      ListsRepeaterAddRemoveExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const repeaterHarness = await loader.getHarness(
      SkyRepeaterHarness.with({ dataSkyId: 'repeater-example' }),
    );

    const el = fixture.nativeElement as HTMLElement;

    return { el, fixture, repeaterHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ListsRepeaterAddRemoveExampleComponent, NoopAnimationsModule],
    });
  });

  it('should allow items to be expanded and collapsed', async () => {
    const { repeaterHarness } = await setupTest();

    const repeaterItems = await repeaterHarness.getRepeaterItems();

    let first = true;

    for (const item of repeaterItems) {
      await expectAsync(item.isCollapsible()).toBeResolvedTo(true);

      // in single expand mode, the first item is expanded by default
      await expectAsync(item.isExpanded()).toBeResolvedTo(first ? true : false);

      first = false;

      await item.collapse();
      await expectAsync(item.isExpanded()).toBeResolvedTo(false);

      await item.expand();
      await expectAsync(item.isExpanded()).toBeResolvedTo(true);
    }
  });

  it('should allow items to be reordered', async () => {
    const { repeaterHarness } = await setupTest();

    const expectedContent = [
      {
        title: 'Call Robert Hernandez  Completed',
        body: 'Robert recently gave a very generous gift. We should call him to thank him.',
      },
      {
        title: 'Send invitation to Spring Ball  Past due',
        body: "The Spring Ball is coming up soon. Let's get those invitations out!",
      },
      {
        title: 'Assign prospects  Due tomorrow',
        body: 'There are 14 new prospects who are not assigned to fundraisers.',
      },
      {
        title: 'Process gift receipts  Due next week',
        body: 'There are 28 recent gifts that are not receipted.',
      },
    ];

    let repeaterItems = await repeaterHarness.getRepeaterItems();

    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(expectedContent.length);

    for (const item of repeaterItems) {
      await expectAsync(item.isReorderable()).toBeResolvedTo(true);
    }

    await expectAsync(repeaterItems[1].getTitleText()).toBeResolvedTo(
      expectedContent[1].title,
    );

    await repeaterItems[1].sendToTop();
    repeaterItems = await repeaterHarness.getRepeaterItems();

    await expectAsync(repeaterItems[1].getTitleText()).toBeResolvedTo(
      expectedContent[0].title,
    );
  });

  it('should allow items to be added and removed', async () => {
    const { repeaterHarness, el, fixture } = await setupTest();

    let repeaterItems = await repeaterHarness.getRepeaterItems();

    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(4);

    for (const item of repeaterItems) {
      await expectAsync(item.isSelectable()).toBeResolvedTo(true);
    }

    const addButton = el.querySelector<HTMLButtonElement>(
      '[data-sky-id="add-button"]',
    );

    const removeButton = el.querySelector<HTMLButtonElement>(
      '[data-sky-id="remove-button"]',
    );

    addButton?.click();
    fixture.detectChanges();

    repeaterItems = await repeaterHarness.getRepeaterItems();
    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(5);

    await expectAsync(repeaterItems[0].isSelected()).toBeResolvedTo(false);
    await repeaterItems[0].select();

    await expectAsync(repeaterItems[0].isSelected()).toBeResolvedTo(true);
    await expectAsync(repeaterItems[1].isSelected()).toBeResolvedTo(false);

    await repeaterItems[1].select();
    await expectAsync(repeaterItems[1].isSelected()).toBeResolvedTo(true);

    removeButton?.click();
    fixture.detectChanges();

    repeaterItems = await repeaterHarness.getRepeaterItems();
    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

import { Item } from './item';

let nextId = 0;

/**
 * @title Repeater with drag and drop, removable items
 */
@Component({
  selector: 'app-lists-repeater-add-remove-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyDropdownModule, SkyRepeaterModule],
})
export class ListsRepeaterAddRemoveExampleComponent {
  protected items: Item[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call him to thank him.',
      status: 'Completed',
      isSelected: false,
    },
    {
      title: 'Send invitation to Spring Ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      status: 'Past due',
      isSelected: false,
    },
    {
      title: 'Assign prospects',
      note: 'There are 14 new prospects who are not assigned to fundraisers.',
      status: 'Due tomorrow',
      isSelected: false,
    },
    {
      title: 'Process gift receipts',
      note: 'There are 28 recent gifts that are not receipted.',
      status: 'Due next week',
      isSelected: false,
    },
  ];

  protected addItem(): void {
    this.items.push({
      title: 'New reminder ' + ++nextId,
      note: 'This is a new reminder',
      status: 'Active',
      isSelected: false,
    });
  }

  protected changeItems(tags: Item[]): void {
    console.log('Tags in order ', tags);
  }

  protected onActionClicked(buttonText: string): void {
    alert(buttonText + ' was clicked!');
  }

  protected removeItems(): void {
    this.items = this.items.filter((item) => !item.isSelected);
  }
}

```

#### item.ts

```typescript
export interface Item {
  title: string;
  note: string;
  status: string;
  isSelected: boolean;
}

```

#### example.component.html

```html
<div class="sky-margin-stacked-lg">
  <sky-repeater
    data-sky-id="repeater-example"
    [expandMode]="'single'"
    [reorderable]="true"
    (orderChange)="changeItems($event)"
  >
    @for (item of items; track item) {
      <sky-repeater-item
        [selectable]="true"
        [tag]="item.note"
        [(isSelected)]="item.isSelected"
      >
        <sky-repeater-item-title class="example-repeater-flex">
          <div class="example-repeater-item-title">
            {{ item.title }}
          </div>
          <div>
            {{ item.status }}
          </div>
        </sky-repeater-item-title>
        <sky-repeater-item-context-menu>
          <sky-dropdown buttonType="context-menu">
            <sky-dropdown-menu>
              <sky-dropdown-item>
                <button type="button" (click)="onActionClicked('Action 1')">
                  Action 1
                </button>
              </sky-dropdown-item>
              <sky-dropdown-item>
                <button type="button" (click)="onActionClicked('Action 2')">
                  Action 2
                </button>
              </sky-dropdown-item>
            </sky-dropdown-menu>
          </sky-dropdown>
        </sky-repeater-item-context-menu>
        <sky-repeater-item-content>
          {{ item.note }}
        </sky-repeater-item-content>
      </sky-repeater-item>
    }
  </sky-repeater>
</div>

<button
  data-sky-id="add-button"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="addItem()"
>
  Add item
</button>

<button
  data-sky-id="remove-button"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="removeItems()"
>
  Remove selected items
</button>

```

#### example.component.scss

```css
.example-repeater-flex {
  display: flex;
  flex-wrap: wrap;

  .example-repeater-item-title {
    flex-grow: 1;
  }
}

```

---

## Repeater with basic setup

**Component:** ListsRepeaterBasicExampleComponent

**Selector:** `app-lists-repeater-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyRepeaterHarness,
  SkyRepeaterItemHarness,
} from '@skyux/lists/testing';

import { ListsRepeaterBasicExampleComponent } from './example.component';

describe('Repeater basic example', () => {
  async function setupTest(): Promise<{
    repeaterHarness: SkyRepeaterHarness | null;
    repeaterItems: SkyRepeaterItemHarness[] | null;
    fixture: ComponentFixture<ListsRepeaterBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(ListsRepeaterBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const repeaterHarness = await loader.getHarness(
      SkyRepeaterHarness.with({ dataSkyId: 'repeater-example' }),
    );

    const repeaterItems = await repeaterHarness.getRepeaterItems();

    return { repeaterHarness, repeaterItems, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ListsRepeaterBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should display the repeater item contents', async () => {
    const { repeaterItems } = await setupTest();

    const expectedContent = [
      {
        title: 'Call Robert Hernandez  Completed',
        body: 'Robert recently gave a very generous gift. We should call him to thank him.',
      },
      {
        title: 'Send invitation to Spring Ball  Past due',
        body: "The Spring Ball is coming up soon. Let's get those invitations out!",
      },
      {
        title: 'Assign prospects  Due tomorrow',
        body: 'There are 14 new prospects who are not assigned to fundraisers.',
      },
      {
        title: 'Process gift receipts  Due next week',
        body: 'There are 28 recent gifts that are not receipted.',
      },
      {
        title: '',
        body: 'Three other tasks were not displayed',
      },
    ];

    expect(repeaterItems?.length).toBe(expectedContent.length);

    if (repeaterItems) {
      for (let i = 0; i < repeaterItems.length; i++) {
        await expectAsync(repeaterItems[i].getTitleText()).toBeResolvedTo(
          expectedContent[i].title,
        );
        await expectAsync(repeaterItems[i].getContentText()).toBeResolvedTo(
          expectedContent[i].body,
        );
      }
    }
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Repeater with basic setup
 */
@Component({
  selector: 'app-lists-repeater-basic-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyDropdownModule, SkyRepeaterModule],
})
export class ListsRepeaterBasicExampleComponent {
  protected items: {
    note: string;
    status?: string;
    title?: string;
    accessibilityLabel?: string;
  }[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call him to thank him.',
      status: 'Completed',
    },
    {
      title: 'Send invitation to Spring Ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      status: 'Past due',
    },
    {
      title: 'Assign prospects',
      note: 'There are 14 new prospects who are not assigned to fundraisers.',
      status: 'Due tomorrow',
    },
    {
      title: 'Process gift receipts',
      note: 'There are 28 recent gifts that are not receipted.',
      status: 'Due next week',
    },
    {
      note: 'Three other tasks were not displayed',
      accessibilityLabel: 'Other tasks',
    },
  ];

  protected onActionClicked(buttonText: string): void {
    alert(buttonText + ' was clicked!');
  }
}

```

#### example.component.html

```html
<sky-repeater data-sky-id="repeater-example">
  @for (item of items; track item) {
    <sky-repeater-item [itemName]="item.accessibilityLabel">
      @if (item.title) {
        <sky-repeater-item-title class="example-repeater-flex">
          <div class="example-repeater-item-title">
            {{ item.title }}
          </div>
          <div>
            {{ item.status }}
          </div>
        </sky-repeater-item-title>
      }
      <sky-repeater-item-context-menu>
        <sky-dropdown buttonType="context-menu">
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Action 1 for ' + (item.title ?? item.accessibilityLabel)
                "
                (click)="onActionClicked('Action 1')"
              >
                Action 1
              </button>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Action 2 for ' + (item.title ?? item.accessibilityLabel)
                "
                (click)="onActionClicked('Action 2')"
              >
                Action 2
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### example.component.scss

```css
.example-repeater-flex {
  display: flex;
  flex-wrap: wrap;

  .example-repeater-item-title {
    flex-grow: 1;
  }
}

```

---

## Repeater with inline form

**Component:** ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
} from '@skyux/inline-form';
import { SkyRepeaterModule } from '@skyux/lists';

interface DemoForm {
  id: FormControl<string>;
  note: FormControl<string>;
  title: FormControl<string>;
}

interface Item {
  id: string;
  title: string | undefined;
  note: string | undefined;
}

/**
 * @title Repeater with inline form
 */
@Component({
  selector: 'app-lists-repeater-inline-form-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
  ],
})
export class ListsRepeaterInlineFormExampleComponent {
  protected activeInlineFormId: string | undefined;
  protected formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected items: Item[] = [
    {
      id: '1',
      title: '2019 Spring Gala',
      note: 'Gala for friends and family',
    },
    {
      id: '2',
      title: '2019 Special Winter Event',
      note: 'A special event',
    },
    {
      id: '3',
      title: '2019 Donor Appreciation Event',
      note: 'Event for all donors and families',
    },
    {
      id: '4',
      title: '2020 Spring Gala',
      note: 'Gala for friends and family',
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: new FormControl('', { nonNullable: true }),
      title: new FormControl('', { nonNullable: true }),
      note: new FormControl('', { nonNullable: true }),
    });
  }

  protected showInlineForm(item: Item): void {
    this.activeInlineFormId = item.id;
    this.formGroup.patchValue({
      note: item.note,
      title: item.title,
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      const found = this.items.find(
        (item) => item.id === this.activeInlineFormId,
      );
      if (found) {
        found.note = this.formGroup.value.note;
        found.title = this.formGroup.value.title;
      }
    }

    this.formGroup.patchValue({
      note: undefined,
      title: undefined,
    });

    // Close the active form.
    this.activeInlineFormId = undefined;
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of items; track item) {
    <sky-repeater-item
      [inlineFormConfig]="inlineFormConfig"
      [inlineFormTemplate]="inlineFormTemplate"
      [showInlineForm]="activeInlineFormId === item.id"
      (inlineFormClose)="onInlineFormClose($event)"
    >
      <sky-repeater-item-title>
        <div class="sky-font-emphasized">
          {{ item.title }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-context-menu>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="showInlineForm(item)"
        >
          <sky-icon iconName="edit" />
        </button>
      </sky-repeater-item-context-menu>

      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

<ng-template #inlineFormTemplate>
  <form novalidate [formGroup]="formGroup">
    <sky-input-box labelText="Title" stacked="true">
      <input formControlName="title" type="text" />
    </sky-input-box>
    <sky-input-box labelText="Note">
      <input formControlName="note" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Sort with basic setup

**Component:** ListsSortBasicExampleComponent

**Selector:** `app-lists-sort-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySortHarness } from '@skyux/lists/testing';

import { ListsSortBasicExampleComponent } from './example.component';

describe('Sort demo', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    sortHarness: SkySortHarness;
    fixture: ComponentFixture<ListsSortBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsSortBasicExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsSortBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const sortHarness: SkySortHarness = options.dataSkyId
      ? await loader.getHarness(
          SkySortHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkySortHarness);

    return { sortHarness, fixture };
  }

  it('should set up the component', async () => {
    const { sortHarness } = await setupTest();

    await sortHarness.click();

    const items = await sortHarness.getItems();

    await expectAsync(items[0].isActive()).toBeResolvedTo(false);
    await expectAsync(items[1].getText()).toBeResolvedTo('Assigned to (Z - A)');
    await expectAsync(items[2].isActive()).toBeResolvedTo(true);

    await items[3].click();

    await expectAsync(items[3].isActive()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnInit } from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyRepeaterModule, SkySortModule } from '@skyux/lists';

interface Item {
  title: string;
  note: string;
  assignee: string;
  date: Date;
}

interface SortOption {
  id: number;
  label: string;
  name: keyof Item;
  descending: boolean;
}

/**
 * @title Sort with basic setup
 */
@Component({
  selector: 'app-lists-sort-basic-example',
  styles: `
    .item-wrapper {
      display: flex;
      justify-content: space-between;
    }
  `,
  templateUrl: './example.component.html',
  imports: [CommonModule, SkyRepeaterModule, SkySortModule, SkyToolbarModule],
})
export class ListsSortBasicExampleComponent implements OnInit {
  protected initialState = 3;

  protected sortedItems: Item[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call to thank him.',
      assignee: 'Debby Fowler',
      date: new Date('12/22/2015'),
    },
    {
      title: 'Send invitation to ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      assignee: 'Debby Fowler',
      date: new Date('1/1/2016'),
    },
    {
      title: 'Clean up desk',
      note: 'File and organize papers.',
      assignee: 'Tim Howard',
      date: new Date('2/2/2016'),
    },
    {
      title: 'Investigate leads',
      note: 'Check out leads for important charity event funding.',
      assignee: 'Larry Williams',
      date: new Date('4/5/2016'),
    },
    {
      title: 'Send thank you note',
      note: 'Send a thank you note to Timothy for his donation.',
      assignee: 'Catherine Hooper',
      date: new Date('11/11/2015'),
    },
  ];

  protected sortOptions: SortOption[] = [
    {
      id: 1,
      label: 'Assigned to (A - Z)',
      name: 'assignee',
      descending: false,
    },
    {
      id: 2,
      label: 'Assigned to (Z - A)',
      name: 'assignee',
      descending: true,
    },
    {
      id: 3,
      label: 'Date created (newest first)',
      name: 'date',
      descending: true,
    },
    {
      id: 4,
      label: 'Date created (oldest first)',
      name: 'date',
      descending: false,
    },
    {
      id: 5,
      label: 'Note title (A - Z)',
      name: 'title',
      descending: false,
    },
    {
      id: 6,
      label: 'Note title (Z - A)',
      name: 'title',
      descending: true,
    },
  ];

  public ngOnInit(): void {
    this.sortItems(this.sortOptions[2]);
  }

  protected sortItems(option: SortOption): void {
    this.sortedItems = this.sortedItems.sort((a, b) => {
      const descending = option.descending ? -1 : 1;
      const sortProperty: keyof typeof a = option.name;

      if (a[sortProperty] > b[sortProperty]) {
        return descending;
      } else if (a[sortProperty] < b[sortProperty]) {
        return -1 * descending;
      } else {
        return 0;
      }
    });
  }
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-item>
    <sky-sort [showButtonText]="true">
      @for (item of sortOptions; track item) {
        <sky-sort-item
          [active]="initialState === item.id"
          (itemSelect)="sortItems(item)"
        >
          {{ item.label }}
        </sky-sort-item>
      }
    </sky-sort>
  </sky-toolbar-item>
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of sortedItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.title }}
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        <div class="item-wrapper">
          <div>Assigned to {{ item.assignee }}</div>
          <div>Created {{ item.date | date }}</div>
        </div>
        <div>
          {{ item.note }}
        </div>
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

---

## List page with list layout using data manager

**Component:** PagesPageListPageListLayoutExampleComponent

**Selector:** `app-pages-page-list-page-list-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### dashboards-grid-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Item } from './item';

@Component({
  selector: 'app-dashboards-grid-context-menu',
  templateUrl: './dashboards-grid-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class DashboardGridContextMenuComponent
  implements ICellRendererAngularComp
{
  protected dashboardName = '';

  public agInit(params: ICellRendererParams<Item>): void {
    this.dashboardName = params.data?.dashboard ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageListPageListLayoutExampleComponent } from './example.component';

describe('List page list layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageListPageListLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageListPageListLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageListPageListLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    });
  });

  it('should have a list layout', async () => {
    const { pageHarness } = await setupTest();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('list');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Dashboards',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with list layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-list-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageListLayoutExampleComponent {}

```

#### item.ts

```typescript
export interface Item {
  dashboard: string;
  name: string;
  lastUpdated: string;
}

```

#### list-page-content.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { DashboardGridContextMenuComponent } from './dashboards-grid-context-menu.component';
import { Item } from './item';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-list-page-content',
  templateUrl: './list-page-content.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyIconModule,
    SkyKeyInfoModule,
  ],
})
export class ListPageContentComponent implements OnInit {
  protected items: Item[] = [
    {
      dashboard: 'Cash Flow Tracker',
      name: 'Kanesha Hutto',
      lastUpdated: '06/21/2023',
    },
    {
      dashboard: 'Accounts Receivable Dashboard',
      name: 'Kristeen Lunsford',
      lastUpdated: '06/30/2023',
    },
    {
      dashboard: 'Accounts Payable Dashboard',
      name: 'Darcel Lenz',
      lastUpdated: '04/20/2023',
    },
    {
      dashboard: 'Budget vs. Actual',
      name: 'Barbara Durr',
      lastUpdated: '12/04/2023',
    },
    {
      dashboard: 'Balance Sheet - New',
      name: 'Ilene Woo',
      lastUpdated: '12/20/2023',
    },
    {
      dashboard: 'Debt Management',
      name: 'Tonja Sanderson',
      lastUpdated: '09/10/2023',
    },
  ];

  protected gridOptions: GridOptions;

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: DashboardGridContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'dashboard',
      field: 'dashboard',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Created By',
    },
    {
      colId: 'lastUpdated',
      field: 'lastUpdated',
      headerName: 'Last Updated',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
  };

  readonly #dataManagerService = inject(SkyDataManagerService);
  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'dashboard',
              'name',
              'lastUpdated',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### dashboards-grid-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + dashboardName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + dashboardName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Copy ' + dashboardName">
        Copy
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + dashboardName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="list" helpKey="example-help">
  <sky-page-header pageTitle="Dashboards" />
  <sky-page-content>
    <app-list-page-content />
  </sky-page-content>
</sky-page>

```

#### list-page-content.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New dashboard"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info class="sky-padding-horizontal-sm" layout="horizontal">
      <sky-key-info-value class="sky-font-display-4">
        {{ items.length }}
      </sky-key-info-value>
      <sky-key-info-label> Dashboards </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

---

## List page with tabs layout using data manager

**Component:** PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### contact-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Contact } from './contact';

@Component({
  selector: 'app-contacts-grid-context-menu',
  templateUrl: './contact-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class ContactContextMenuComponent implements ICellRendererAngularComp {
  protected contactName = '';

  public agInit(params: ICellRendererParams<Contact>): void {
    this.contactName = params.data?.name ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### contact.ts

```typescript
export interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageListPageTabsLayoutExampleComponent } from './example.component';

describe('List page tabs layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageListPageTabsLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageListPageTabsLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageListPageTabsLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a tabs layout', async () => {
    const { pageHarness } = await setupTest();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Contacts',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageTabsLayoutExampleComponent {}

```

#### list-page-contacts-grid.component.ts

```typescript
import { Component, Input, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { ContactContextMenuComponent } from './contact-context-menu.component';

ModuleRegistry.registerModules([AllCommunityModule]);

interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

@Component({
  selector: 'app-list-page-contacts-grid',
  templateUrl: './list-page-contacts-grid.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyIconModule,
    SkyKeyInfoModule,
  ],
})
export class ListPageContactsGridComponent implements OnInit {
  @Input()
  public contacts: Contact[] = [];

  protected gridOptions: GridOptions;

  #dataManagerService = inject(SkyDataManagerService);
  #agGridSvc = inject(SkyAgGridService);

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: ContactContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'organization',
      field: 'organization',
      headerName: 'Organization',
    },
    {
      colId: 'emailAddress',
      field: 'emailAddress',
      headerName: 'Email Address',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
    columnPickerEnabled: true,
    columnOptions: [
      { id: 'contextMenu', label: 'Context menu', alwaysDisplayed: true },
      { id: 'name', label: 'Name' },
      { id: 'organization', label: 'Organization' },
      { id: 'emailAddress', label: 'Email Address' },
    ],
  };

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'name',
              'organization',
              'emailAddress',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### list-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

import { Contact } from './contact';
import { ListPageContactsGridComponent } from './list-page-contacts-grid.component';

@Component({
  selector: 'app-list-page-content',
  templateUrl: './list-page-content.component.html',
  imports: [ListPageContactsGridComponent, SkyTabsModule],
})
export class ListPageContentComponent {
  protected activeTabIndex: SkyTabIndex = 0;

  protected myContacts: Contact[] = [
    {
      name: 'Wonda Lumpkin',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'wlumpkin@yahoo.com',
    },
    {
      name: 'Eliza Vanhorn',
      organization: 'Summit School of the Arts',
      emailAddress: 'evanhorn@outlook.com',
    },
    {
      name: 'Ed Sipes',
      organization: 'Reflections Middle School',
      emailAddress: 'esipes@yahoo.com',
    },
    {
      name: 'Elwood Farris',
      organization: 'Sandy Lagoon College',
      emailAddress: 'elfarris@gmail.com',
    },
    {
      name: 'Cristen Sizemore',
      organization: 'Grafton Vision Health',
      emailAddress: 'cristen.sizemore@aol.com',
    },
    {
      name: 'Latrice Ashmore',
      organization: 'Food Bank of Rapid City',
      emailAddress: 'lashmore@gmail.com',
    },
  ];

  protected allContacts = [
    ...this.myContacts,
    {
      name: 'Kanesha Hutto',
      organization: 'Los Angeles College of the Arts',
      emailAddress: 'khutto@yahoo.com',
    },
    {
      name: 'Kristeen Lunsford',
      organization: 'Food Bank of Los Angeles',
      emailAddress: 'kristeen.lunsford@yahoo.com',
    },
    {
      name: 'Barbara Durr',
      organization: 'Riverfront Middle School',
      emailAddress: 'bdurr@gmail.com',
    },
    {
      name: 'Ilene Woo',
      organization: 'Rapid City High School',
      emailAddress: 'ilene.woo@aol.com',
    },
    {
      name: 'Darcel Lenz',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'dlenz@yahoo.com',
    },
  ];
}

```

#### contact-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + contactName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + contactName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + contactName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="tabs" helpKey="example-help">
  <sky-page-header pageTitle="Contacts" />
  <sky-page-content>
    <app-list-page-content />
  </sky-page-content>
</sky-page>

```

#### list-page-contacts-grid.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New contact"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
      <sky-key-info-value class="sky-font-display-4">
        {{ contacts.length }}
      </sky-key-info-value>
      <sky-key-info-label> Contacts </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="contacts" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

#### list-page-content.component.html

```html
<sky-tabset [(active)]="activeTabIndex">
  <sky-tab tabHeading="My contacts" layout="list">
    @if (activeTabIndex === 0) {
      <app-list-page-contacts-grid [contacts]="myContacts" />
    }
  </sky-tab>
  <sky-tab tabHeading="All contacts" layout="list">
    @if (activeTabIndex === 1) {
      <app-list-page-contacts-grid [contacts]="allContacts" />
    }
  </sky-tab>
</sky-tabset>

```

---
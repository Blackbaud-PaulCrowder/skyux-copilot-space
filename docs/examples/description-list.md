---
component: 'description-list'
type: 'code-examples'
description: 'Code examples for the description-list component.'
---

# Description List Code Examples

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
---
component: 'key-info'
type: 'code-examples'
description: 'Code examples for the key-info component.'
---

# Key Info Code Examples

## Key info with basic setup

**Component:** IndicatorsKeyInfoBasicExampleComponent

**Selector:** `app-indicators-key-info-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideNoopAnimations } from '@angular/platform-browser/animations';
import { SkyHelpInlineHarness } from '@skyux/help-inline/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';

import { IndicatorsKeyInfoBasicExampleComponent } from './example.component';

describe('Basic key info', () => {
  async function setupTest(options?: { value?: number }): Promise<{
    keyInfoHarness: SkyKeyInfoHarness;
    helpInlineHarness: SkyHelpInlineHarness;
    fixture: ComponentFixture<IndicatorsKeyInfoBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsKeyInfoBasicExampleComponent,
    );

    if (options?.value !== undefined) {
      fixture.componentInstance.value = options.value;
    }

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const keyInfoHarness = await loader.getHarness(
      SkyKeyInfoHarness.with({ dataSkyId: 'key-info-example' }),
    );
    const helpInlineHarness = await loader.getHarness(SkyHelpInlineHarness);

    return { keyInfoHarness, helpInlineHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsKeyInfoBasicExampleComponent],
      providers: [provideNoopAnimations()],
    });
  });

  it('should display a vertical key info', async () => {
    const { keyInfoHarness } = await setupTest({ value: 101 });

    await expectAsync(keyInfoHarness.getLayout()).toBeResolvedTo('vertical');
    await expectAsync(keyInfoHarness.getValueText()).toBeResolvedTo('101');
    await expectAsync(keyInfoHarness.getLabelText()).toBeResolvedTo(
      'New members',
    );
  });

  it('should display a horizontal key info', async () => {
    const { keyInfoHarness } = await setupTest({ value: 50 });

    await expectAsync(keyInfoHarness.getLayout()).toBeResolvedTo('horizontal');
    await expectAsync(keyInfoHarness.getValueText()).toBeResolvedTo('50');
    await expectAsync(keyInfoHarness.getLabelText()).toBeResolvedTo(
      'New members',
    );
  });

  it('should include inline help', async () => {
    const { helpInlineHarness } = await setupTest({ value: 50 });

    await expectAsync(helpInlineHarness.getAriaExpanded()).toBeResolvedTo(
      false,
    );
    await helpInlineHarness.click();
    await expectAsync(helpInlineHarness.getAriaExpanded()).toBeResolvedTo(true);
    expect(await helpInlineHarness.getPopoverContent()).toContain(
      'help content can add clarity',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, Input } from '@angular/core';
import { SkyKeyInfoLayoutType, SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Key info with basic setup
 */
@Component({
  selector: 'app-indicators-key-info-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule],
})
export class IndicatorsKeyInfoBasicExampleComponent {
  @Input()
  public set value(value: number | undefined) {
    this.#_value = value;

    this.layout =
      this.#_value && this.#_value >= 100 ? 'vertical' : 'horizontal';
  }

  public get value(): number | undefined {
    return this.#_value;
  }

  protected layout: SkyKeyInfoLayoutType = 'vertical';

  #_value: number | undefined = 575;
}

```

#### example.component.html

```html
<sky-key-info
  data-sky-id="key-info-example"
  helpPopoverTitle="Help"
  [layout]="layout"
  [helpPopoverContent]="helpContent"
>
  <sky-key-info-value class="sky-font-display-3">
    {{ value }}
  </sky-key-info-value>
  <sky-key-info-label> New members </sky-key-info-label>
</sky-key-info>
<ng-template #helpContent>
  This help content can add clarity and provide next steps.
</ng-template>

```

---

## Key info with help key

**Component:** IndicatorsKeyInfoHelpKeyExampleComponent

**Selector:** `app-indicators-key-info-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideNoopAnimations } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyHelpInlineHarness } from '@skyux/help-inline/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';

import { IndicatorsKeyInfoHelpKeyExampleComponent } from './example.component';

describe('Basic key info', () => {
  async function setupTest(options?: { value?: number }): Promise<{
    keyInfoHarness: SkyKeyInfoHarness;
    helpInlineHarness: SkyHelpInlineHarness;
    fixture: ComponentFixture<IndicatorsKeyInfoHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsKeyInfoHelpKeyExampleComponent,
    );

    if (options?.value !== undefined) {
      fixture.componentInstance.value = options.value;
    }

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const keyInfoHarness = await loader.getHarness(
      SkyKeyInfoHarness.with({ dataSkyId: 'key-info-example' }),
    );
    const helpInlineHarness = await loader.getHarness(SkyHelpInlineHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { keyInfoHarness, helpInlineHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsKeyInfoHelpKeyExampleComponent, SkyHelpTestingModule],
      providers: [provideNoopAnimations()],
    });
  });

  it('should display a vertical key info', async () => {
    const { keyInfoHarness } = await setupTest({ value: 101 });

    await expectAsync(keyInfoHarness.getLayout()).toBeResolvedTo('vertical');
    await expectAsync(keyInfoHarness.getValueText()).toBeResolvedTo('101');
    await expectAsync(keyInfoHarness.getLabelText()).toBeResolvedTo(
      'New members',
    );
  });

  it('should display a horizontal key info', async () => {
    const { keyInfoHarness } = await setupTest({ value: 50 });

    await expectAsync(keyInfoHarness.getLayout()).toBeResolvedTo('horizontal');
    await expectAsync(keyInfoHarness.getValueText()).toBeResolvedTo('50');
    await expectAsync(keyInfoHarness.getLabelText()).toBeResolvedTo(
      'New members',
    );
  });

  it('should have the correct help key', async () => {
    const { helpInlineHarness, helpController } = await setupTest({
      value: 50,
    });

    await helpInlineHarness.click();

    helpController.expectCurrentHelpKey('new-member-help');
  });
});

```

#### example.component.ts

```typescript
import { Component, Input } from '@angular/core';
import { SkyKeyInfoLayoutType, SkyKeyInfoModule } from '@skyux/indicators';

/**
 * @title Key info with help key
 */
@Component({
  selector: 'app-indicators-key-info-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyKeyInfoModule],
})
export class IndicatorsKeyInfoHelpKeyExampleComponent {
  @Input()
  public set value(value: number | undefined) {
    this.#_value = value;

    this.layout =
      this.#_value && this.#_value >= 100 ? 'vertical' : 'horizontal';
  }

  public get value(): number | undefined {
    return this.#_value;
  }

  protected layout: SkyKeyInfoLayoutType = 'vertical';

  #_value: number | undefined = 575;
}

```

#### example.component.html

```html
<sky-key-info
  data-sky-id="key-info-example"
  helpKey="new-member-help"
  [layout]="layout"
>
  <sky-key-info-value class="sky-font-display-3">
    {{ value }}
  </sky-key-info-value>
  <sky-key-info-label> New members </sky-key-info-label>
</sky-key-info>

```

---
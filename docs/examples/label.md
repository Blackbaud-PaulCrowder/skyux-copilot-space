---
component: 'label'
type: 'code-examples'
description: 'Code examples for the label component.'
---

# Label Code Examples

## Label with basic setup

**Component:** IndicatorsLabelBasicExampleComponent

**Selector:** `app-indicators-label-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyLabelHarness } from '@skyux/indicators/testing';

import { IndicatorsLabelBasicExampleComponent } from './example.component';

describe('Basic label', () => {
  async function setupTest(options?: {
    daysUntilDue?: number;
    submitted?: boolean;
  }): Promise<{
    labelHarness: SkyLabelHarness;
    fixture: ComponentFixture<IndicatorsLabelBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsLabelBasicExampleComponent,
    );

    if (options?.daysUntilDue !== undefined) {
      fixture.componentInstance.daysUntilDue = options.daysUntilDue;
    }

    if (options?.submitted !== undefined) {
      fixture.componentInstance.submitted = options.submitted;
    }

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const labelHarness = await loader.getHarness(
      SkyLabelHarness.with({ dataSkyId: 'label-example' }),
    );

    return { labelHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsLabelBasicExampleComponent],
    });
  });

  it('should show an info label when submitted is false and there is more than a week until due', async () => {
    const { labelHarness, fixture } = await setupTest({ daysUntilDue: 8 });
    fixture.detectChanges();

    await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('info');
    await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
      'attention',
    );
    await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Incomplete');
  });

  it('should show a warning label when submitted is false and there is less than a week until due', async () => {
    const { labelHarness, fixture } = await setupTest({ daysUntilDue: 6 });
    fixture.detectChanges();

    await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('warning');
    await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
      'important-warning',
    );
    await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Due soon');
  });

  it('should show a danger label when submitted is false and it is past due', async () => {
    const { labelHarness, fixture } = await setupTest({ daysUntilDue: -1 });
    fixture.detectChanges();

    await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('danger');
    await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
      'danger',
    );
    await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Overdue');
  });

  it('should show a success label when submitted is true', async () => {
    const { labelHarness, fixture } = await setupTest({ submitted: true });
    fixture.detectChanges();

    await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('success');
    await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
      'completed',
    );
    await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Submitted');
  });
});

```

#### example.component.ts

```typescript
import { Component, Input } from '@angular/core';
import {
  SkyIndicatorDescriptionType,
  SkyLabelModule,
  SkyLabelType,
} from '@skyux/indicators';

/**
 * @title Label with basic setup
 */
@Component({
  selector: 'app-indicators-label-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyLabelModule],
})
export class IndicatorsLabelBasicExampleComponent {
  @Input()
  public get daysUntilDue(): number {
    return this.#_daysUntilDue;
  }

  public set daysUntilDue(days: number) {
    this.#_daysUntilDue = days;
    this.#updateLabelProperties(this.submitted, days);
  }

  @Input()
  public get submitted(): boolean {
    return this.#_submitted;
  }

  public set submitted(submitted: boolean) {
    this.#_submitted = submitted;
    this.#updateLabelProperties(submitted, this.daysUntilDue);
  }

  protected descriptionType: SkyIndicatorDescriptionType = 'attention';
  protected labelText = 'Incomplete';
  protected labelType: SkyLabelType = 'info';

  #_daysUntilDue = 14;
  #_submitted = false;

  #updateLabelProperties(submitted: boolean, days: number): void {
    if (submitted) {
      this.labelType = 'success';
      this.descriptionType = 'completed';
      this.labelText = 'Submitted';
    } else if (days <= 0) {
      this.labelType = 'danger';
      this.descriptionType = 'danger';
      this.labelText = 'Overdue';
    } else if (days <= 7) {
      this.labelType = 'warning';
      this.descriptionType = 'important-warning';
      this.labelText = 'Due soon';
    } else {
      this.labelType = 'info';
      this.descriptionType = 'attention';
      this.labelText = 'Incomplete';
    }
  }
}

```

#### example.component.html

```html
<sky-label
  data-sky-id="label-example"
  [descriptionType]="descriptionType"
  [labelType]="labelType"
>
  {{ labelText }}
</sky-label>

```

---
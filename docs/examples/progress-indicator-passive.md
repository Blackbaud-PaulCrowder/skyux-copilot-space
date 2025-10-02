---
component: 'progress-indicator-passive'
type: 'code-examples'
description: 'Code examples for the progress-indicator-passive component.'
---

# Progress Indicator Passive Code Examples

## Passive progress indicator

**Component:** ProgressIndicatorPassiveIndicatorBasicExampleComponent

**Selector:** `app-progress-indicator-passive-indicator-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyProgressIndicatorHarness } from '@skyux/progress-indicator/testing';

import { ProgressIndicatorPassiveIndicatorBasicExampleComponent } from './example.component';

describe('Basic passive progress indicator example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyProgressIndicatorHarness;
    fixture: ComponentFixture<ProgressIndicatorPassiveIndicatorBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ProgressIndicatorPassiveIndicatorBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyProgressIndicatorHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  it('should have the initial progress set', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'example-progress-indicator',
    });

    await expectAsync(harness.isPassive()).toBeResolvedTo(true);
    expect((await harness.getItems()).length).toBe(3);

    const finishedStep = harness.getItem({ dataSkyId: 'finished-step' });
    await expectAsync((await finishedStep).getTitle()).toBeResolvedTo(
      'Finished step',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyProgressIndicatorModule } from '@skyux/progress-indicator';

/**
 * @title Passive progress indicator
 */
@Component({
  selector: 'app-progress-indicator-passive-indicator-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyProgressIndicatorModule],
})
export class ProgressIndicatorPassiveIndicatorBasicExampleComponent {}

```

#### example.component.html

```html
<sky-progress-indicator
  data-sky-id="example-progress-indicator"
  [isPassive]="true"
  [startingIndex]="1"
>
  <sky-progress-indicator-item
    data-sky-id="finished-step"
    helpPopoverContent="Example help content for finished step"
    helpPopoverTitle="Start here"
    title="Finished step"
    >Optional details about this step
  </sky-progress-indicator-item>
  <sky-progress-indicator-item
    helpPopoverContent="Example help content for current step"
    title="Current step"
  />
  <sky-progress-indicator-item title="HIDDEN TITLE" />
</sky-progress-indicator>

```

---
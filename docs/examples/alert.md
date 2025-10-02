---
component: 'alert'
type: 'code-examples'
description: 'Code examples for the alert component.'
---

# Alert Code Examples

## Alert with basic setup

**Component:** IndicatorsAlertBasicExampleComponent

**Selector:** `app-indicators-alert-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyAlertHarness } from '@skyux/indicators/testing';

import { IndicatorsAlertBasicExampleComponent } from './example.component';

describe('Basic alert', () => {
  async function setupTest(options?: { days?: number }): Promise<{
    alertHarness: SkyAlertHarness;
    fixture: ComponentFixture<IndicatorsAlertBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsAlertBasicExampleComponent,
    );

    if (options?.days !== undefined) {
      fixture.componentInstance.days = options.days;
    }

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const alertHarness = await loader.getHarness(
      SkyAlertHarness.with({ dataSkyId: 'alert-example' }),
    );

    return { alertHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsAlertBasicExampleComponent],
    });
  });

  it('should show the expected alert when the number of days is 8 or more', async () => {
    const { alertHarness, fixture } = await setupTest({ days: 8 });
    fixture.detectChanges();

    await expectAsync(alertHarness.getAlertType()).toBeResolvedTo('warning');
    await expectAsync(alertHarness.getText()).toBeResolvedTo(
      'Your password expires in 8 day(s)!',
    );
    await expectAsync(alertHarness.isCloseable()).toBeResolvedTo(true);
  });

  it('should show the expected alert when the number of days is 7 or fewer', async () => {
    const { alertHarness, fixture } = await setupTest({ days: 7 });
    fixture.detectChanges();

    await expectAsync(alertHarness.getAlertType()).toBeResolvedTo('danger');
    await expectAsync(alertHarness.getText()).toBeResolvedTo(
      'Your password expires in 7 day(s)!',
    );
    await expectAsync(alertHarness.isCloseable()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { ChangeDetectionStrategy, Component, Input } from '@angular/core';
import { SkyAlertModule } from '@skyux/indicators';

/**
 * @title Alert with basic setup
 */
@Component({
  selector: 'app-indicators-alert-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyAlertModule],
})
export class IndicatorsAlertBasicExampleComponent {
  @Input()
  public days = 9;

  protected onClosedChange(event: boolean): void {
    alert(`Alert closed with: ${event}`);
  }
}

```

#### example.component.html

```html
<sky-alert
  data-sky-id="alert-example"
  [alertType]="days < 8 ? 'danger' : 'warning'"
  [closeable]="days >= 8"
  [descriptionType]="days < 8 ? 'danger' : 'important-warning'"
  (closedChange)="onClosedChange($event)"
>
  Your password expires in {{ days }} day(s)!
</sky-alert>

```

---
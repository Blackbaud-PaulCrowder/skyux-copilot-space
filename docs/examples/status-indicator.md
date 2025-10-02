---
component: 'status-indicator'
type: 'code-examples'
description: 'Code examples for the status-indicator component.'
---

# Status Indicator Code Examples

## Status indicator with basic setup

**Component:** IndicatorsStatusIndicatorBasicExampleComponent

**Selector:** `app-indicators-status-indicator-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import {
  SkyIndicatorDescriptionType,
  SkyIndicatorIconType,
} from '@skyux/indicators';
import { SkyStatusIndicatorHarness } from '@skyux/indicators/testing';

import { IndicatorsStatusIndicatorBasicExampleComponent } from './example.component';

describe('Status indicator basic example', () => {
  async function setupTest(): Promise<HarnessLoader> {
    const fixture = TestBed.createComponent(
      IndicatorsStatusIndicatorBasicExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    fixture.detectChanges();
    await fixture.whenStable();

    return loader;
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsStatusIndicatorBasicExampleComponent],
    });
  });

  it('should use the expected text and description type for each status indicator', async () => {
    const loader = await setupTest();

    async function validate(
      dataSkyIdSuffix: string,
      expectedIndicatorType: SkyIndicatorIconType,
      expectedDescriptionType: SkyIndicatorDescriptionType,
      expectedText: string,
      expectedCustomDescription?: string,
    ): Promise<void> {
      const harness = await loader.getHarness(
        SkyStatusIndicatorHarness.with({
          dataSkyId: `status-indicator-${dataSkyIdSuffix}`,
        }),
      );

      await expectAsync(harness.getDescriptionType()).toBeResolvedTo(
        expectedDescriptionType,
      );

      await expectAsync(harness.getIndicatorType()).toBeResolvedTo(
        expectedIndicatorType,
      );

      await expectAsync(harness.getText()).toBeResolvedTo(expectedText);

      if (expectedCustomDescription !== undefined) {
        await expectAsync(harness.getCustomDescription()).toBeResolvedTo(
          expectedCustomDescription,
        );
      }
    }

    await validate('error', 'danger', 'error', 'Danger status indicator');

    await validate(
      'important-info',
      'info',
      'important-info',
      'Info status indicator',
    );

    await validate(
      'completed',
      'success',
      'completed',
      'Success status indicator',
    );

    await validate('warning', 'warning', 'warning', 'Warning status indicator');

    await validate(
      'custom',
      'warning',
      'custom',
      'Warning status indicator with custom screen reader description',
      'Custom warning',
    );

    await validate(
      'error-with-help',
      'danger',
      'error',
      'Danger status indicator with help',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Status indicator with basic setup
 */
@Component({
  selector: 'app-indicators-status-indicator-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyStatusIndicatorModule],
})
export class IndicatorsStatusIndicatorBasicExampleComponent {}

```

#### example.component.html

```html
<sky-status-indicator
  data-sky-id="status-indicator-error"
  descriptionType="error"
  indicatorType="danger"
>
  Danger status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-important-info"
  descriptionType="important-info"
  indicatorType="info"
>
  Info status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-completed"
  descriptionType="completed"
  indicatorType="success"
>
  Success status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-warning"
  descriptionType="warning"
  indicatorType="warning"
>
  Warning status indicator
</sky-status-indicator>

<sky-status-indicator
  customDescription="Custom warning"
  data-sky-id="status-indicator-custom"
  descriptionType="custom"
  indicatorType="warning"
>
  Warning status indicator with custom screen reader description
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-error-with-help"
  descriptionType="error"
  indicatorType="danger"
  helpPopoverContent="
    This contextual help can provide more information about
    the status as well as possible next steps."
>
  Danger status indicator with help
</sky-status-indicator>

```

---

## Status indicator with help key

**Component:** IndicatorsStatusIndicatorHelpKeyExampleComponent

**Selector:** `app-indicators-status-indicator-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import {
  SkyIndicatorDescriptionType,
  SkyIndicatorIconType,
} from '@skyux/indicators';
import { SkyStatusIndicatorHarness } from '@skyux/indicators/testing';

import { IndicatorsStatusIndicatorHelpKeyExampleComponent } from './example.component';

describe('Status indicator basic example', () => {
  async function setupTest(): Promise<HarnessLoader> {
    const fixture = TestBed.createComponent(
      IndicatorsStatusIndicatorHelpKeyExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    fixture.detectChanges();
    await fixture.whenStable();

    return loader;
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        IndicatorsStatusIndicatorHelpKeyExampleComponent,
        SkyHelpTestingModule,
      ],
    });
  });

  it('should use the expected text and description type for each status indicator', async () => {
    const loader = await setupTest();

    async function validate(
      dataSkyIdSuffix: string,
      expectedIndicatorType: SkyIndicatorIconType,
      expectedDescriptionType: SkyIndicatorDescriptionType,
      expectedText: string,
      expectedCustomDescription?: string,
    ): Promise<void> {
      const harness = await loader.getHarness(
        SkyStatusIndicatorHarness.with({
          dataSkyId: `status-indicator-${dataSkyIdSuffix}`,
        }),
      );

      await expectAsync(harness.getDescriptionType()).toBeResolvedTo(
        expectedDescriptionType,
      );

      await expectAsync(harness.getIndicatorType()).toBeResolvedTo(
        expectedIndicatorType,
      );

      await expectAsync(harness.getText()).toBeResolvedTo(expectedText);

      if (expectedCustomDescription !== undefined) {
        await expectAsync(harness.getCustomDescription()).toBeResolvedTo(
          expectedCustomDescription,
        );
      }
    }

    await validate('error', 'danger', 'error', 'Danger status indicator');

    await validate(
      'important-info',
      'info',
      'important-info',
      'Info status indicator',
    );

    await validate(
      'completed',
      'success',
      'completed',
      'Success status indicator',
    );

    await validate('warning', 'warning', 'warning', 'Warning status indicator');

    await validate(
      'custom',
      'warning',
      'custom',
      'Warning status indicator with custom screen reader description',
      'Custom warning',
    );

    await validate(
      'error-with-help-key',
      'danger',
      'error',
      'Danger status indicator with help key',
    );
  });

  it('should have the correct help key', async () => {
    const loader = await setupTest();
    const harness = await loader.getHarness(
      SkyStatusIndicatorHarness.with({
        dataSkyId: 'status-indicator-error-with-help-key',
      }),
    );
    const helpController = TestBed.inject(SkyHelpTestingController);

    await harness.clickHelpInline();

    helpController.expectCurrentHelpKey('danger-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Status indicator with help key
 */
@Component({
  selector: 'app-indicators-status-indicator-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyStatusIndicatorModule],
})
export class IndicatorsStatusIndicatorHelpKeyExampleComponent {}

```

#### example.component.html

```html
<sky-status-indicator
  data-sky-id="status-indicator-error"
  descriptionType="error"
  indicatorType="danger"
>
  Danger status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-important-info"
  descriptionType="important-info"
  indicatorType="info"
>
  Info status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-completed"
  descriptionType="completed"
  indicatorType="success"
>
  Success status indicator
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-warning"
  descriptionType="warning"
  indicatorType="warning"
>
  Warning status indicator
</sky-status-indicator>

<sky-status-indicator
  customDescription="Custom warning"
  data-sky-id="status-indicator-custom"
  descriptionType="custom"
  indicatorType="warning"
>
  Warning status indicator with custom screen reader description
</sky-status-indicator>

<sky-status-indicator
  data-sky-id="status-indicator-error-with-help-key"
  descriptionType="error"
  indicatorType="danger"
  helpKey="danger-help"
>
  Danger status indicator with help key
</sky-status-indicator>

```

---
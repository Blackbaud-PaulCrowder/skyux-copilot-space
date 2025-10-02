---
component: 'character-count'
type: 'code-examples'
description: 'Code examples for the character-count component.'
---

# Character Count Code Examples

## Character count with basic setup

**Component:** FormsCharacterCountExampleComponent

**Selector:** `app-forms-character-count-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';
import { SkyStatusIndicatorHarness } from '@skyux/indicators/testing';

import { FormsCharacterCountExampleComponent } from './example.component';

describe('Character count example', () => {
  async function setupTest(): Promise<{
    harness: SkyCharacterCounterIndicatorHarness;
    loader: HarnessLoader;
  }> {
    const fixture = TestBed.createComponent(
      FormsCharacterCountExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyCharacterCounterIndicatorHarness.with({
        dataSkyId: 'description-indicator',
      }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsCharacterCountExampleComponent],
    });
  });

  it('should allow a maximum of 50 characters', async () => {
    const { harness, loader } = await setupTest();

    // Validate initial state.
    await expectAsync(harness.getCharacterCountLimit()).toBeResolvedTo(50);
    await expectAsync(harness.getCharacterCount()).toBeResolvedTo(46);
    await expectAsync(harness.isOverLimit()).toBeResolvedTo(false);

    // Update the value to exceed the limit and validate.
    const inputEl =
      document.querySelector<HTMLInputElement>('.description-input');

    if (inputEl) {
      inputEl.value += ' scholarship fund';
      inputEl.dispatchEvent(new Event('input'));
    }

    await expectAsync(harness.getCharacterCount()).toBeResolvedTo(63);
    await expectAsync(harness.isOverLimit()).toBeResolvedTo(true);

    // Validate that the status indicator error displayed when limit was exceeded.
    const statusIndicator = await loader.getHarness(
      SkyStatusIndicatorHarness.with({
        dataSkyId: 'description-status-indicator-over-limit',
      }),
    );

    await expectAsync(statusIndicator.getDescriptionType()).toBeResolvedTo(
      'error',
    );
    await expectAsync(statusIndicator.getIndicatorType()).toBeResolvedTo(
      'danger',
    );
    await expectAsync(statusIndicator.getText()).toBeResolvedTo(
      'Limit Transaction description to 50 characters.',
    );
  });
});

```

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
import { SkyIdModule } from '@skyux/core';
import { SkyCharacterCounterModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Character count with basic setup
 */
@Component({
  selector: 'app-forms-character-count-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCharacterCounterModule,
    SkyIdModule,
    SkyInputBoxModule,
    SkyStatusIndicatorModule,
  ],
})
export class FormsCharacterCountExampleComponent {
  protected description: FormControl;
  protected formGroup: FormGroup;
  protected maxDescriptionCharacterCount = 50;

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.description = this.#formBuilder.control(
      'Boys and Girls Club of South Carolina donation',
    );

    this.formGroup = this.#formBuilder.group({
      description: this.description,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box stacked="true" labelText="Transaction description">
    <sky-character-counter-indicator
      #descriptionIndicator
      data-sky-id="description-indicator"
    />

    <input
      #descriptionInput="skyId"
      class="sky-form-control description-input"
      formControlName="description"
      skyCharacterCounter
      skyId
      type="text"
      [attr.aria-describedby]="characterCountError.id"
      [skyCharacterCounterIndicator]="descriptionIndicator"
      [skyCharacterCounterLimit]="maxDescriptionCharacterCount"
    />

    <span #characterCountError="skyId" class="sky-error-indicator" skyId>
      @if (description.errors?.['skyCharacterCounter']) {
        <sky-status-indicator
          data-sky-id="description-status-indicator-over-limit"
          descriptionType="error"
          indicatorType="danger"
        >
          Limit Transaction description to
          {{ maxDescriptionCharacterCount }} characters.
        </sky-status-indicator>
      }
    </span>
  </sky-input-box>
</form>

```

---
---
component: 'progress-indicator-wizard'
type: 'code-examples'
description: 'Code examples for the progress-indicator-wizard component.'
---

# Progress Indicator Wizard Code Examples

## Wizard (progress indicator)

**Component:** ProgressIndicatorWizardBasicExampleComponent

**Selector:** `app-progress-indicator-wizard-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard (progress indicator)
 */
@Component({
  standalone: true,
  selector: 'app-progress-indicator-wizard-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class ProgressIndicatorWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent);
  }
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormBuilder, FormGroup, ReactiveFormsModule } from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
import {
  SkyProgressIndicatorActionClickArgs,
  SkyProgressIndicatorChange,
  SkyProgressIndicatorDisplayModeType,
  SkyProgressIndicatorModule,
} from '@skyux/progress-indicator';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyProgressIndicatorModule,
  ],
})
export class ModalComponent {
  protected activeIndex: number | undefined = 0;
  protected displayMode: SkyProgressIndicatorDisplayModeType = 'horizontal';
  protected formGroup: FormGroup;
  protected title = 'Wizard example';

  protected get requirementsMet(): boolean {
    switch (this.activeIndex) {
      case 0:
        return !!this.formGroup.get('requiredValue1')?.value;
      case 1:
        return !!this.formGroup.get('requiredValue2')?.value;
      default:
        return false;
    }
  }

  protected readonly instance = inject(SkyModalInstance);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      requiredValue1: undefined,
      requiredValue2: undefined,
    });
  }

  protected onCancelClick(): void {
    this.instance.cancel();
  }

  protected onSaveClick(args: SkyProgressIndicatorActionClickArgs): void {
    args.progressHandler.advance();
    this.instance.save();
  }

  protected updateIndex(changes: SkyProgressIndicatorChange): void {
    this.activeIndex = changes.activeIndex;
  }
}

```

#### example.component.html

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openWizard()">
  Open wizard
</button>

```

#### modal.component.html

```html
<sky-modal [headingText]="title">
  <sky-modal-content>
    <form [formGroup]="formGroup">
      <sky-progress-indicator
        #wizardDemo
        [displayMode]="displayMode"
        (progressChanges)="updateIndex($event)"
      >
        <sky-progress-indicator-item title="First step">
          <sky-input-box labelText="Enter text to continue">
            <input type="text" formControlName="requiredValue1" />
          </sky-input-box>
        </sky-progress-indicator-item>

        <sky-progress-indicator-item title="Second step">
          <div>
            <sky-checkbox
              formControlName="requiredValue2"
              labelText="Select to continue"
            />
          </div>
        </sky-progress-indicator-item>

        <sky-progress-indicator-item title="Third step">
          <div>Additional content or tasks go here.</div>
        </sky-progress-indicator-item>
      </sky-progress-indicator>
    </form>
  </sky-modal-content>
  <sky-modal-footer>
    <sky-progress-indicator-nav-button
      buttonType="previous"
      [progressIndicator]="wizardDemo"
    />
    <sky-progress-indicator-nav-button
      buttonType="next"
      [disabled]="!requirementsMet"
      [progressIndicator]="wizardDemo"
    />
    <sky-progress-indicator-nav-button
      buttonType="finish"
      buttonText="Finish"
      [progressIndicator]="wizardDemo"
      (actionClick)="onSaveClick($event)"
    />
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="onCancelClick()"
    >
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

---
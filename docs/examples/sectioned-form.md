---
component: 'sectioned-form'
type: 'code-examples'
description: 'Code examples for the sectioned-form component.'
---

# Sectioned Form Code Examples

## Sectioned form inside modal

**Component:** TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### address-form.component.ts

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-address-form',
  template: `<div>Address form</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class AddressFormComponent {}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkySectionedFormHarness } from '@skyux/tabs/testing';

import { TabsSectionedFormModalExampleComponent } from './example.component';

describe('Sectioned form in a modal example', () => {
  async function setupTest(): Promise<{
    sectionedFormHarness: SkySectionedFormHarness;
    fixture: ComponentFixture<TabsSectionedFormModalExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [TabsSectionedFormModalExampleComponent, NoopAnimationsModule],
    }).compileComponents();
    const fixture = TestBed.createComponent(
      TabsSectionedFormModalExampleComponent,
    );
    fixture.componentInstance.openModal();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const sectionedFormHarness: SkySectionedFormHarness =
      await loader.getHarness(
        SkySectionedFormHarness.with({ dataSkyId: 'modal-sectioned-form' }),
      );

    return { sectionedFormHarness, fixture };
  }

  it('should set up the sectioned form', async () => {
    const { sectionedFormHarness } = await setupTest();
    let activeSection = await sectionedFormHarness.getActiveSection();
    await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
      'Addresses',
    );
    await expectAsync(activeSection?.getSectionItemCount()).toBeResolvedTo(2);

    await (
      await sectionedFormHarness.getSection({
        sectionHeading: 'Basic information',
      })
    ).click();

    await expectAsync(activeSection?.isActive()).toBeResolvedTo(false);

    activeSection = await sectionedFormHarness.getActiveSection();
    await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
      'Basic information',
    );

    const activeContent = await sectionedFormHarness.getActiveSectionContent();

    const idField = await (
      await activeContent?.queryHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'id-field' }),
      )
    )?.querySelector('input');

    await expectAsync(idField?.getProperty('value')).toBeResolvedTo('5324901');
  });
});

```

#### example.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Sectioned form inside modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-sectioned-form-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class TabsSectionedFormModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  public openModal(): void {
    const modalInstance = this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel') {
        console.log(`Modal cancelled`);
      } else if (result.reason === 'save') {
        console.log(`Modal saved`);
      }
    });
  }
}

```

#### information-form.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnInit,
  inject,
} from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkySectionedFormService } from '@skyux/tabs';

@Component({
  selector: 'app-information-form',
  templateUrl: './information-form.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyFluidGridModule,
    SkyStatusIndicatorModule,
  ],
})
export class InformationFormComponent implements OnInit {
  protected id = '5324901';
  protected formGroup: FormGroup<{
    name: FormControl<string>;
    nameRequired: FormControl<boolean>;
    id: FormControl<string>;
  }>;
  protected name = '';
  protected nameRequired = false;

  readonly #sectionedFormSvc = inject(SkySectionedFormService);
  readonly #changeDetector = inject(ChangeDetectorRef);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      name: new FormControl(this.name, { nonNullable: true }),
      nameRequired: new FormControl(this.nameRequired, { nonNullable: true }),
      id: new FormControl(this.id, {
        nonNullable: true,
        validators: [Validators.pattern('^[0-9]+$')],
      }),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe((changes) => {
      this.id = changes.id ?? '';
      this.name = changes.name ?? '';
      this.nameRequired = !!changes.nameRequired;
      this.#checkValidity();
    });

    this.#changeDetector.markForCheck();
  }

  #checkValidity(): void {
    if (this.nameRequired) {
      this.formGroup.get('name')?.setValidators([Validators.required]);
      this.#sectionedFormSvc.requiredFieldChanged(true);
    } else {
      this.formGroup.get('name')?.setValidators([]);
      this.#sectionedFormSvc.requiredFieldChanged(false);
    }

    if (!this.formGroup.get('name')?.value && this.nameRequired) {
      this.#sectionedFormSvc.invalidFieldChanged(true);
    } else {
      this.#sectionedFormSvc.invalidFieldChanged(false);
    }
  }
}

```

#### modal.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
import {
  SkySectionedFormMessage,
  SkySectionedFormMessageType,
  SkySectionedFormModule,
} from '@skyux/tabs';

import { Subject } from 'rxjs';

import { AddressFormComponent } from './address-form.component';
import { InformationFormComponent } from './information-form.component';
import { PhoneFormComponent } from './phone-form.component';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [
    AddressFormComponent,
    InformationFormComponent,
    PhoneFormComponent,
    SkyIconModule,
    SkyModalModule,
    SkySectionedFormModule,
  ],
})
export class ModalComponent {
  protected activeIndexDisplay: number | undefined;
  protected activeTab = true;
  protected sectionedFormController = new Subject<SkySectionedFormMessage>();
  protected tabsHidden = false;

  protected readonly modalInstance = inject(SkyModalInstance);
  readonly #changeDetector = inject(ChangeDetectorRef);

  protected onIndexChanged(newIndex: number): void {
    this.activeIndexDisplay = newIndex;
    this.#changeDetector.markForCheck();
  }

  protected onTabsVisibleChanged(visible: boolean): void {
    this.tabsHidden = !visible;
  }

  protected showTabs(): void {
    this.sectionedFormController.next({
      type: SkySectionedFormMessageType.ShowTabs,
    });
  }
}

```

#### phone-form.component.ts

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-phone-form',
  template: `<div>Phone form</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class PhoneFormComponent {}

```

#### example.component.html

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
  Open sectioned form
</button>

```

#### information-form.component.html

```html
<form novalidate [formGroup]="formGroup">
  <sky-fluid-grid gutterSize="small" [disableMargin]="true">
    <sky-row>
      <sky-column [screenXSmall]="6">
        <sky-input-box data-sky-id="name-field" labelText="Name" stacked="true">
          <input formControlName="name" type="text" />
        </sky-input-box>
      </sky-column>
      <sky-column [screenXSmall]="6">
        <sky-input-box data-sky-id="id-field" labelText="ID" stacked="true">
          <input formControlName="id" type="text" />
          <span class="sky-error-indicator">
            @if (formGroup.get('id')?.invalid) {
              <sky-status-indicator
                indicatorType="danger"
                descriptionType="error"
              >
                Enter a valid value.
              </sky-status-indicator>
            }
          </span>
        </sky-input-box>
      </sky-column>
    </sky-row>
  </sky-fluid-grid>
</form>

```

#### modal.component.html

```html
<sky-modal [headingText]="'Sectioned form — Index: ' + activeIndexDisplay">
  <sky-modal-content>
    <sky-sectioned-form
      data-sky-id="modal-sectioned-form"
      [messageStream]="sectionedFormController"
      (indexChanged)="onIndexChanged($event)"
      (tabsVisibleChanged)="onTabsVisibleChanged($event)"
    >
      <sky-sectioned-form-section heading="Basic information">
        <app-information-form />
      </sky-sectioned-form-section>
      <sky-sectioned-form-section
        heading="Addresses"
        [itemCount]="2"
        [active]="activeTab"
      >
        <app-address-form />
      </sky-sectioned-form-section>
      <sky-sectioned-form-section heading="Phone numbers" [itemCount]="3">
        <app-phone-form />
      </sky-sectioned-form-section>
    </sky-sectioned-form>
  </sky-modal-content>
  <sky-modal-footer>
    @if (tabsHidden) {
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="showTabs()"
      >
        <sky-icon iconName="chevron-left" />
        Show sections
      </button>
    }
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="modalInstance.save()"
    >
      Save
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="modalInstance.cancel()"
    >
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

---
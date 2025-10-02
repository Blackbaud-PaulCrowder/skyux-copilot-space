---
component: 'tabs-wizard'
type: 'code-examples'
description: 'Code examples for the tabs-wizard component.'
---

# Tabs Wizard Code Examples

## Wizard in a modal

**Component:** TabsWizardBasicExampleComponent

**Selector:** `app-tabs-wizard-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard in a modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-wizard-basic-example',
  templateUrl: './example.component.html',
})
export class TabsWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  #modalSize = 'large';

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent, { size: this.#modalSize });
  }
}

```

#### modal.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyModalInstance } from '@skyux/modals';
import {
  SkyTabsetHarness,
  SkyTabsetNavButtonHarness,
} from '@skyux/tabs/testing';

import { ModalComponent } from './modal.component';

describe('Wizard tabset demo', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<ModalComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([]), SkyModalInstance],
      imports: [ModalComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ModalComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );
    return { harness, fixture, loader };
  }

  it('should set up the tabset wizard', async () => {
    const { harness, loader } = await setupTest({
      dataSkyId: 'sign-up-wizard',
    });

    // You can get all tab button harnesses from the tabset harness.
    const tabs = await harness.getTabButtonHarnesses();
    expect(tabs.length).toBe(3);
    await expectAsync(tabs[1].isDisabled()).toBeResolvedTo(true);

    // You can get the tab button harness from its `tabHeading`
    const tab2 = await harness.getTabButtonHarness({
      tabHeading: '2. Contact Information',
    });
    await expectAsync(tab2.isActive()).toBeResolvedTo(false);

    // You can get the active tab button's harness.
    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo(
      '1. Biographical Details',
    );

    // You can get the tabset nav button harnesses by their `buttonType`.
    const previousButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({
        buttonType: 'previous',
      }),
    );
    const nextButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({
        buttonType: 'next',
      }),
    );

    await expectAsync(previousButton.isDisabled()).toBeResolvedTo(true);
    await expectAsync(nextButton.isDisabled()).toBeResolvedTo(true);
  });

  it('should enable the second step once the first step is complete', async () => {
    const { harness, loader, fixture } = await setupTest({
      dataSkyId: 'sign-up-wizard',
    });

    const tab1Harness = await harness.getActiveTabButton();

    // You can query the tab content harness' internal harnesses.
    const inputHarnesses = await (
      await tab1Harness?.getTabContentHarness()
    )?.queryHarnesses(SkyInputBoxHarness);
    expect(inputHarnesses?.length).toBe(3);

    fixture.componentInstance.formGroup.get('firstName')?.setValue('John');
    fixture.componentInstance.formGroup.get('lastName')?.setValue('Doe');
    fixture.detectChanges();

    // If changes in the test causes the tabset to swap to dropdown mode
    // open the dropdown to access tab button harnesses
    if ((await harness.getMode()) === 'dropdown') {
      await harness.clickDropdownTab();
    }

    const tab2 = await harness.getTabButtonHarness({
      tabHeading: '2. Contact Information',
    });
    expect(await tab2.isDisabled()).toBe(false);

    const nextButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({ buttonType: 'next' }),
    );
    expect(await nextButton.isDisabled()).toBe(false);

    await nextButton.click();
    await expectAsync(tab2.isActive()).toBeResolvedTo(true);
  });
});

```

#### modal.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
import { SkyPhoneFieldModule } from '@skyux/phone-field';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyPhoneFieldModule,
    SkyTabsModule,
  ],
})
export class ModalComponent implements OnInit {
  protected activeIndex: SkyTabIndex = 0;
  public formGroup: FormGroup;
  protected isSaveDisabled = true;
  protected isStep2Disabled = true;
  protected isStep3Disabled = true;
  protected title = 'New Member Sign-up';

  readonly #instance = inject(SkyModalInstance);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      firstName: new FormControl('', Validators.required),
      middleName: new FormControl(''),
      lastName: new FormControl('', Validators.required),
      phoneNumber: new FormControl('', Validators.required),
      email: new FormControl('', Validators.required),
      termsAccepted: new FormControl(false),
      mailingList: new FormControl(false),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe(() => {
      this.#checkRequirementsMet();
    });
  }

  protected onCancelClick(): void {
    this.#instance.cancel();
  }

  protected onSave(): void {
    this.#instance.save();
  }

  #checkRequirementsMet(): void {
    this.isStep2Disabled = !(
      this.formGroup?.get('firstName')?.value &&
      this.formGroup?.get('lastName')?.value
    );

    this.isStep3Disabled = !(
      this.formGroup?.get('phoneNumber')?.value &&
      this.formGroup?.get('phoneNumber')?.valid &&
      this.formGroup?.get('email')?.value
    );

    this.isSaveDisabled = !this.formGroup?.get('termsAccepted')?.value;
  }
}

```

#### example.component.html

```html
<button type="button" class="sky-btn sky-btn-default" (click)="openWizard()">
  Open Wizard
</button>

```

#### modal.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="onSave()">
  <sky-modal [headingText]="title">
    <sky-modal-content>
      <sky-tabset
        #wizardDemo
        ariaLabel="Sign-up steps"
        data-sky-id="sign-up-wizard"
        tabStyle="wizard"
        [(active)]="activeIndex"
      >
        <sky-tab tabHeading="1. Biographical Details">
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="First name" [stacked]="true">
                  <input type="text" formControlName="firstName" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="Middle name" [stacked]="true">
                  <input type="text" formControlName="middleName" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="Last name">
                  <input type="text" formControlName="lastName" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
        <sky-tab
          tabHeading="2. Contact Information"
          [disabled]="isStep2Disabled"
        >
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12" [screenMedium]="6">
                <sky-input-box labelText="Phone Number" [stacked]="true">
                  <sky-phone-field defaultCountry="us">
                    <input formControlName="phoneNumber" skyPhoneFieldInput />
                  </sky-phone-field>
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="6">
                <sky-input-box labelText="Email">
                  <input type="email" formControlName="email" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
        <sky-tab tabHeading="3. More Information" [disabled]="isStep3Disabled">
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12">
                <sky-checkbox
                  formControlName="termsAccepted"
                  labelText="Accept terms and conditions"
                  required
                />
              </sky-column>
              <sky-column [screenSmall]="12">
                <sky-checkbox
                  formControlName="mailingList"
                  labelText="Sign up for our email newsletter"
                />
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
      </sky-tabset>
    </sky-modal-content>
    <sky-modal-footer>
      <sky-tabset-nav-button buttonType="previous" [tabset]="wizardDemo" />
      <sky-tabset-nav-button buttonType="next" [tabset]="wizardDemo" />
      <sky-tabset-nav-button
        buttonType="finish"
        [tabset]="wizardDemo"
        [disabled]="isSaveDisabled"
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
</form>

```

---
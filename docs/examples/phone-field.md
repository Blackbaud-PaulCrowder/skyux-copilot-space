---
component: 'phone-field'
type: 'code-examples'
description: 'Code examples for the phone-field component.'
---

# Phone Field Code Examples

## Phone field with basic setup

**Component:** PhoneFieldBasicExampleComponent

**Selector:** `app-phone-field-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyPhoneFieldCountry } from '@skyux/phone-field';
import { SkyPhoneFieldHarness } from '@skyux/phone-field/testing';

import { PhoneFieldBasicExampleComponent } from './example.component';

const COUNTRY_AU: SkyPhoneFieldCountry = {
  name: 'Australia',
  iso2: 'au',
  dialCode: '+61',
};

const DATA_SKY_ID = 'my-phone-field';
const VALID_AU_NUMBER = '0212345678';
const VALID_US_NUMBER = '8675555309';

describe('Basic phone field example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyPhoneFieldHarness;
    fixture: ComponentFixture<PhoneFieldBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(PhoneFieldBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
      )
    ).queryHarness(SkyPhoneFieldHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [PhoneFieldBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set up phone field input and clear value', async () => {
    const { harness } = await setupTest({
      dataSkyId: DATA_SKY_ID,
    });

    // First, set a value on the phoneField.
    const inputHarness = await harness.getControl();
    await inputHarness.focus();
    await inputHarness.setValue(VALID_US_NUMBER);

    await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_US_NUMBER);

    // Now, clear the value.
    await inputHarness.clear();
    await expectAsync(inputHarness.getValue()).toBeResolvedTo('');
  });

  it('should use selected country', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: DATA_SKY_ID,
    });

    const inputHarness = await harness.getControl();
    await inputHarness.focus();
    // enter a valid phone number for the default country
    await inputHarness.setValue(VALID_US_NUMBER);

    // expect the model to use the proper dial code and format
    await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_US_NUMBER);
    expect(fixture.componentInstance.phoneControl.value).toEqual(
      '(867) 555-5309',
    );

    if (COUNTRY_AU.name) {
      // change the country
      await harness.selectCountry(COUNTRY_AU.name);
    }

    const countryName: string | null = await harness.getSelectedCountryName();

    const countryIos2: string | null = await harness.getSelectedCountryIso2();

    fixture.detectChanges();
    await fixture.whenStable();

    if (COUNTRY_AU.name && countryName) {
      expect(countryName).toBe(COUNTRY_AU.name);
    }
    if (COUNTRY_AU.iso2 && countryIos2) {
      expect(countryIos2).toBe(COUNTRY_AU.iso2);
    }

    // enter a valid phone number for the new country
    await inputHarness.setValue(VALID_AU_NUMBER);

    // expect the model to use the proper dial code and format
    await expectAsync(inputHarness.getValue()).toBeResolvedTo(VALID_AU_NUMBER);
    expect(fixture.componentInstance.phoneControl.value).toEqual(
      '+61 2 1234 5678',
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
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyPhoneFieldModule } from '@skyux/phone-field';

/**
 * @title Phone field with basic setup
 */
@Component({
  selector: 'app-phone-field-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyPhoneFieldModule,
  ],
})
export class PhoneFieldBasicExampleComponent {
  public phoneForm: FormGroup;
  public phoneControl: FormControl;

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.phoneControl = this.#formBuilder.control(undefined, {
      validators: Validators.required,
    });
    this.phoneForm = this.#formBuilder.group({
      phoneControl: this.phoneControl,
    });
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form class="phone-field-example" [formGroup]="phoneForm">
    <sky-input-box
      data-sky-id="my-phone-field"
      helpPopoverTitle="How we use your phone number"
      hintText="Enter the phone number where you can be reached before 5 p.m., Monday through Friday."
      labelText="Phone number"
      [helpPopoverContent]="inlineHelpPopover"
    >
      <sky-phone-field [defaultCountry]="'us'">
        <input formControlName="phoneControl" skyPhoneFieldInput />
      </sky-phone-field>
    </sky-input-box>
  </form>
</div>

<ng-template #inlineHelpPopover>
  We use this number for calls and text about your student. We won't use it for
  other purposes.
  <br />
  <br />
  For more information, see our <a>privacy policy</a>.
</ng-template>

```

---
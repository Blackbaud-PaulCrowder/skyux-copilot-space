---
component: 'field-group'
type: 'code-examples'
description: 'Code examples for the field-group component.'
---

# Field Group Code Examples

## Field group with basic setup

**Component:** FormsFieldGroupBasicExampleComponent

**Selector:** `app-forms-field-group-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Field group with basic setup
 */
@Component({
  selector: 'app-forms-field-group-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyFieldGroupModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
  ],
})
export class FormsFieldGroupBasicExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected helpPopoverContent =
    'We use your address to validate your application with regulatory agencies and to send correspondence related to your application.';

  protected states = [
    'AK',
    'AZ',
    'AL',
    'AR',
    'CA',
    'CO',
    'CT',
    'DE',
    'DC',
    'FL',
    'GA',
    'HI',
    'ID',
    'IL',
    'IN',
    'IA',
    'KS',
    'KY',
    'LA',
    'ME',
    'MD',
    'MA',
    'MI',
    'MN',
    'MS',
    'MO',
    'MT',
    'NE',
    'NV',
    'NH',
    'NJ',
    'NM',
    'NY',
    'NC',
    'ND',
    'OH',
    'OK',
    'OR',
    'PA',
    'RI',
    'SC',
    'SD',
    'TN',
    'TX',
    'UT',
    'VT',
    'VA',
    'WA',
    'WV',
    'WI',
    'WY',
  ];

  constructor() {
    this.formGroup = this.#formBuilder.group({
      streetAddress: this.#formBuilder.control(undefined),
      city: this.#formBuilder.control(undefined),
      state: this.#formBuilder.control(undefined),
      zipCode: this.#formBuilder.control(undefined),
    });
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-field-group
      headingText="Address"
      hintText="We use this address for your end-of-year statement."
      [headingStyle]="4"
      [helpPopoverContent]="helpPopoverContent"
    >
      <sky-fluid-grid gutterSize="small" [disableMargin]="true">
        <sky-row>
          <sky-column [screenXSmall]="12">
            <sky-input-box labelText="Street address" stacked="true">
              <input
                formControlName="streetAddress"
                spellcheck="false"
                type="text"
              />
            </sky-input-box>
          </sky-column>
        </sky-row>
        <sky-row>
          <sky-column [screenSmall]="5">
            <sky-input-box labelText="City" stacked="true">
              <input formControlName="city" spellcheck="false" type="text" />
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="5" [screenXSmall]="8">
            <sky-input-box labelText="State" stacked="true">
              <select formControlName="state">
                <option [attr.value]="undefined"></option>
                @for (state of states; track state) {
                  <option value="state">
                    {{ state }}
                  </option>
                }
              </select>
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="2" [screenXSmall]="4">
            <sky-input-box labelText="Zip code">
              <input formControlName="zipCode" maxlength="5" type="text" />
            </sky-input-box>
          </sky-column>
        </sky-row>
      </sky-fluid-grid>
    </sky-field-group>
  </form>
</div>

```

---

## Field group with help key

**Component:** FormsFieldGroupHelpKeyExampleComponent

**Selector:** `app-forms-field-group-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyFieldGroupHarness } from '@skyux/forms/testing';

import { FormsFieldGroupHelpKeyExampleComponent } from './example.component';

describe('Field group', () => {
  async function setupTest(): Promise<{
    fieldGroupHarness: SkyFieldGroupHarness;
    fixture: ComponentFixture<FormsFieldGroupHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      FormsFieldGroupHelpKeyExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const fieldGroupHarness = await loader.getHarness(SkyFieldGroupHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { fieldGroupHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsFieldGroupHelpKeyExampleComponent, SkyHelpTestingModule],
    });
  });

  it('should have the correct help key', async () => {
    const { fieldGroupHarness, helpController } = await setupTest();

    await fieldGroupHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('address-help');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Field group with help key
 */
@Component({
  selector: 'app-forms-field-group-help-key-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyFieldGroupModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
  ],
})
export class FormsFieldGroupHelpKeyExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected states = [
    'AK',
    'AZ',
    'AL',
    'AR',
    'CA',
    'CO',
    'CT',
    'DE',
    'DC',
    'FL',
    'GA',
    'HI',
    'ID',
    'IL',
    'IN',
    'IA',
    'KS',
    'KY',
    'LA',
    'ME',
    'MD',
    'MA',
    'MI',
    'MN',
    'MS',
    'MO',
    'MT',
    'NE',
    'NV',
    'NH',
    'NJ',
    'NM',
    'NY',
    'NC',
    'ND',
    'OH',
    'OK',
    'OR',
    'PA',
    'RI',
    'SC',
    'SD',
    'TN',
    'TX',
    'UT',
    'VT',
    'VA',
    'WA',
    'WV',
    'WI',
    'WY',
  ];

  constructor() {
    this.formGroup = this.#formBuilder.group({
      streetAddress: this.#formBuilder.control(undefined),
      city: this.#formBuilder.control(undefined),
      state: this.#formBuilder.control(undefined),
      zipCode: this.#formBuilder.control(undefined),
    });
  }
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-field-group
      headingText="Address"
      helpKey="address-help"
      hintText="We use this address for your end-of-year statement."
      [headingStyle]="4"
    >
      <sky-fluid-grid gutterSize="small" [disableMargin]="true">
        <sky-row>
          <sky-column [screenXSmall]="12">
            <sky-input-box labelText="Street address" stacked="true">
              <input
                formControlName="streetAddress"
                spellcheck="false"
                type="text"
              />
            </sky-input-box>
          </sky-column>
        </sky-row>
        <sky-row>
          <sky-column [screenSmall]="5">
            <sky-input-box labelText="City" stacked="true">
              <input formControlName="city" spellcheck="false" type="text" />
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="5" [screenXSmall]="8">
            <sky-input-box labelText="State" stacked="true">
              <select formControlName="state">
                <option [attr.value]="undefined"></option>
                @for (state of states; track state) {
                  <option value="state">
                    {{ state }}
                  </option>
                }
              </select>
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="2" [screenXSmall]="4">
            <sky-input-box labelText="Zip code">
              <input formControlName="zipCode" maxlength="5" type="text" />
            </sky-input-box>
          </sky-column>
        </sky-row>
      </sky-fluid-grid>
    </sky-field-group>
  </form>
</div>

```

---
---
component: 'country-field'
type: 'code-examples'
description: 'Code examples for the country-field component.'
---

# Country Field Code Examples

## Country field with basic setup

**Component:** LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyCountryFieldHarness } from '@skyux/lookup/testing';

import { LookupCountryFieldBasicExampleComponent } from './example.component';

describe('Basic country field example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyCountryFieldHarness;
    fixture: ComponentFixture<LookupCountryFieldBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupCountryFieldBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
      )
    ).queryHarness(SkyCountryFieldHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LookupCountryFieldBasicExampleComponent],
    });
  });

  it('should set up country field input', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'country-field',
    });

    await harness.focus();
    await harness.enterText('ger');

    const searchResultsText = await harness.getSearchResultsText();

    expect(searchResultsText.length).toBe(4);

    await harness.clear();
    await harness.enterText('can');

    const searchResults = await harness.getSearchResults();
    await expectAsync(searchResults[1].getText()).toBeResolvedTo('Canada');

    await searchResults[1].select();
    const value = fixture.componentInstance.countryForm.get('country')?.value;
    expect(value?.name).toBe('Canada');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyCountryFieldCountry, SkyCountryFieldModule } from '@skyux/lookup';

interface DemoForm {
  country: FormControl<SkyCountryFieldCountry | undefined>;
}

function validateCountry(
  control: AbstractControl<SkyCountryFieldCountry | undefined>,
): ValidationErrors | null {
  return control.value?.name === 'Mexico' ? { invalidCountry: true } : null;
}

/**
 * @title Country field with basic setup
 */
@Component({
  selector: 'app-lookup-country-field-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCountryFieldModule,
    SkyInputBoxModule,
  ],
})
export class LookupCountryFieldBasicExampleComponent {
  protected countryControl: FormControl<SkyCountryFieldCountry | undefined>;
  public countryForm: FormGroup<DemoForm>;

  protected helpPopoverContent =
    'We use the country to validate your passport within 10 business days. You can update it at any time.';

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.countryControl = new FormControl(
      {
        name: 'Australia',
        iso2: 'au',
      },
      {
        nonNullable: true,
        validators: [validateCountry, Validators.required],
      },
    );

    this.countryForm = this.#formBuilder.group({
      country: this.countryControl,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="countryForm">
  <sky-input-box
    data-sky-id="country-field"
    hintText="If you have multiple countries, choose your primary country."
    labelText="Country"
    [helpPopoverContent]="helpPopoverContent"
  >
    <sky-country-field formControlName="country" />
    @if (countryControl.errors?.['invalidCountry']) {
      <sky-form-error
        errorName="invalidCountry"
        errorText="This country is no longer available for the date you selected."
      />
    }
  </sky-input-box>
</form>

```

---
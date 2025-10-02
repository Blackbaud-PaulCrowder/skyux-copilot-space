---
component: 'input-box'
type: 'code-examples'
description: 'Code examples for the input-box component.'
---

# Input Box Code Examples

## Input box

**Component:** FormsInputBoxBasicExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { FormsInputBoxBasicExampleComponent } from './example.component';

describe('Basic input box example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    fixture: ComponentFixture<FormsInputBoxBasicExampleComponent>;
    inputBoxHarness: SkyInputBoxHarness;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(FormsInputBoxBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpController = TestBed.inject(SkyHelpTestingController);

    const inputBoxHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { fixture, inputBoxHarness, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        NoopAnimationsModule,
        FormsInputBoxBasicExampleComponent,
        SkyHelpTestingModule,
      ],
    });
  });

  describe('first name field', () => {
    it('should have the expected label text and stacked values', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-first-name',
      });

      fixture.detectChanges();

      await expectAsync(inputBoxHarness.getLabelText()).toBeResolvedTo(
        'First name',
      );

      await expectAsync(inputBoxHarness.getStacked()).toBeResolvedTo(true);
    });

    it('should have the correct help key', async () => {
      const { fixture, inputBoxHarness, helpController } = await setupTest({
        dataSkyId: 'input-box-first-name',
      });

      fixture.detectChanges();

      await inputBoxHarness.clickHelpInline();

      helpController.expectCurrentHelpKey('first-name-help');
    });
  });

  describe('last name field', () => {
    it('should have last name required', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-last-name',
      });

      fixture.detectChanges();

      const inputEl = await inputBoxHarness.querySelector(
        '.last-name-input-box',
      );

      await inputEl.setInputValue('');
      await inputEl.blur();

      await expectAsync(inputBoxHarness.hasRequiredError()).toBeResolvedTo(
        true,
      );
    });
  });

  describe('bio field', () => {
    it('should have a character limit of 250', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-bio',
      });

      fixture.detectChanges();

      const characterCounter = await inputBoxHarness.getCharacterCounter();

      await expectAsync(characterCounter.getCharacterCount()).toBeResolvedTo(0);
      await expectAsync(
        characterCounter.getCharacterCountLimit(),
      ).toBeResolvedTo(250);
    });

    it('should show hint text', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-bio',
      });

      fixture.detectChanges();

      await expectAsync(inputBoxHarness.getHintText()).toBeResolvedTo(
        `A brief description of the member's background, such as hometown, school, hobbies, etc.`,
      );
    });
  });

  describe('email field', () => {
    it('should show a help popover with the expected text', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-email',
      });

      fixture.detectChanges();

      await inputBoxHarness.clickHelpInline();

      await expectAsync(inputBoxHarness.getHelpPopoverTitle()).toBeResolvedTo(
        'Privacy notice',
      );

      await expectAsync(inputBoxHarness.getHelpPopoverContent()).toBeResolvedTo(
        `We do not share this information with any third parties.`,
      );
    });
  });

  describe('favorite color field', () => {
    it('should not allow invalid color to be selected', async () => {
      const { fixture, inputBoxHarness } = await setupTest({
        dataSkyId: 'input-box-favorite-color',
      });

      fixture.detectChanges();

      const selectEl = await inputBoxHarness.querySelector('select');

      // Select the "invalid" option.
      await selectEl.selectOptions(7);

      await expectAsync(
        inputBoxHarness.hasCustomFormError('invalid'),
      ).toBeResolvedTo(true);
    });
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
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyDatepickerModule } from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkyValidators } from '@skyux/validation';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDatepickerModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
    SkyStatusIndicatorModule,
  ],
})
export class FormsInputBoxBasicExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    firstName: new FormControl(''),
    lastName: new FormControl('', Validators.required),
    bio: new FormControl(''),
    email: new FormControl('', [Validators.required, SkyValidators.email]),
    dob: new FormControl('', Validators.required),
    favoriteColor: this.favoriteColor,
  });
}

```

#### example.component.html

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-fluid-grid gutterSize="small" [disableMargin]="false">
      <sky-row>
        <sky-column [screenSmall]="12">
          <h2>New member form</h2>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-first-name"
            helpKey="first-name-help"
            labelText="First name"
            stacked="true"
          >
            <input formControlName="firstName" spellcheck="false" type="text" />
          </sky-input-box>
        </sky-column>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-last-name"
            labelText="Last name"
            stacked="true"
          >
            <input
              class="last-name-input-box"
              formControlName="lastName"
              spellcheck="false"
              type="text"
            />
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12">
          <sky-input-box
            characterLimit="250"
            data-sky-id="input-box-bio"
            hintText="A brief description of the member's background, such as hometown, school, hobbies, etc."
            labelText="Bio"
            stacked="true"
          >
            <textarea formControlName="bio"></textarea>
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-email"
            labelText="Email address"
            stacked="true"
            helpPopoverContent="We do not share this information with any third parties."
            helpPopoverTitle="Privacy notice"
          >
            <input formControlName="email" type="text" />
          </sky-input-box>
        </sky-column>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box labelText="Date of birth" stacked="true">
            <sky-datepicker>
              <input formControlName="dob" skyDatepickerInput />
            </sky-datepicker>
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12">
          <sky-input-box
            data-sky-id="input-box-favorite-color"
            labelText="Favorite color"
          >
            <select
              class="input-box-favorite-color-select"
              formControlName="favoriteColor"
            >
              <option value="none">None</option>
              <option value="red">Red</option>
              <option value="orange">Orange</option>
              <option value="yellow">Yellow</option>
              <option value="green">Green</option>
              <option value="blue">Blue</option>
              <option value="purple">Purple</option>
              <option value="invalid">Invalid Color</option>
            </select>
            <!-- Custom form error not handled by input box. -->
            @if (favoriteColor.errors?.['invalid']) {
              <sky-form-error
                errorName="invalid"
                errorText="Invalid Color is not a color"
              />
            }
          </sky-input-box>
        </sky-column>
      </sky-row>
    </sky-fluid-grid>
  </form>
</div>

```

---

## Input box with custom errors

**Component:** FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';

import { FormsInputBoxWithCustomFormErrorsExampleComponent } from './example.component';

describe('Input box with custom form errors example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    fixture: ComponentFixture<FormsInputBoxWithCustomFormErrorsExampleComponent>;
    inputBoxHarness: SkyInputBoxHarness;
  }> {
    const fixture = TestBed.createComponent(
      FormsInputBoxWithCustomFormErrorsExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const inputBoxHarness = await loader.getHarness(
      SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { fixture, inputBoxHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsInputBoxWithCustomFormErrorsExampleComponent],
    });
  });

  it('should not allow invalid color to be selected', async () => {
    const { fixture, inputBoxHarness } = await setupTest({
      dataSkyId: 'input-box-favorite-color',
    });

    fixture.detectChanges();

    const selectEl = await inputBoxHarness.querySelector('select');

    // Select the "invalid" option.
    await selectEl.selectOptions(7);

    await expectAsync(
      inputBoxHarness.hasCustomFormError('invalid'),
    ).toBeResolvedTo(true);
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
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box with custom errors
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class FormsInputBoxWithCustomFormErrorsExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    favoriteColor: this.favoriteColor,
  });
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box
    data-sky-id="input-box-favorite-color"
    labelText="Favorite color"
  >
    <select formControlName="favoriteColor">
      <option value="none">None</option>
      <option value="red">Red</option>
      <option value="orange">Orange</option>
      <option value="yellow">Yellow</option>
      <option value="green">Green</option>
      <option value="blue">Blue</option>
      <option value="purple">Purple</option>
      <option value="invalid">Invalid Color</option>
    </select>
    @if (favoriteColor.errors?.['invalid']) {
      <sky-form-error
        errorName="invalid"
        errorText="The color Invalid Color is not a color"
      />
    }
  </sky-input-box>
</form>

```

---
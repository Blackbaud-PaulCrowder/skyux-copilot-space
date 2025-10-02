---
component: 'box'
type: 'code-examples'
description: 'Code examples for the box component.'
---

# Box Code Examples

## Standard checkboxes

**Component:** FormsCheckboxBasicExampleComponent

**Selector:** `app-forms-checkbox-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyCheckboxGroupHarness,
  SkyCheckboxHarness,
} from '@skyux/forms/testing';

import { FormsCheckboxBasicExampleComponent } from './example.component';

describe('Basic checkbox group example', () => {
  async function setupCheckboxGroupTest(options: {
    dataSkyId: string;
  }): Promise<SkyCheckboxGroupHarness> {
    const fixture = TestBed.createComponent(FormsCheckboxBasicExampleComponent);

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyCheckboxGroupHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return harness;
  }

  async function setupCheckboxTest(options: {
    dataSkyId: string;
  }): Promise<SkyCheckboxHarness> {
    const fixture = TestBed.createComponent(FormsCheckboxBasicExampleComponent);

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyCheckboxHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return harness;
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, FormsCheckboxBasicExampleComponent],
    });
  });

  it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
    const harness = await setupCheckboxGroupTest({
      dataSkyId: 'checkbox-group',
    });

    const checkboxButtons = await harness.getCheckboxes();

    await expectAsync(harness.getHeadingText()).toBeResolvedTo(
      'Contact method',
    );
    await expectAsync(harness.getHeadingLevel()).toBeResolvedTo(undefined);
    await expectAsync(harness.getHeadingStyle()).toBeResolvedTo(5);
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Please select at least one phone-based method.',
    );

    await expectAsync(checkboxButtons[0].getLabelText()).toBeResolvedTo(
      'Email',
    );
    await expectAsync(checkboxButtons[0].getHintText()).toBeResolvedTo('');

    await expectAsync(checkboxButtons[1].getLabelText()).toBeResolvedTo(
      'Phone',
    );
    await expectAsync(checkboxButtons[1].getHintText()).toBeResolvedTo('');

    await expectAsync(checkboxButtons[2].getLabelText()).toBeResolvedTo('Text');
    await expectAsync(checkboxButtons[2].getHintText()).toBeResolvedTo('');
  });

  it('should display an error message when there is a custom validation error', async () => {
    const harness = await setupCheckboxGroupTest({
      dataSkyId: 'checkbox-group',
    });

    const checkboxHarness = (await harness.getCheckboxes())[0];

    await checkboxHarness.check();

    await expectAsync(harness.hasError('emailOnly')).toBeResolvedTo(true);
  });

  it('should show a help popover with the expected text', async () => {
    const harness = await setupCheckboxGroupTest({
      dataSkyId: 'checkbox-group',
    });

    await harness.clickHelpInline();

    const helpPopoverContent = await harness.getHelpPopoverContent();
    expect(helpPopoverContent).toBe(
      `We use your contact info to keep you informed on current events. We will not sell your information.`,
    );
  });

  it('should check and uncheck checkboxes in display errors if they are required', async () => {
    const harness = await setupCheckboxTest({ dataSkyId: 'single-checkbox' });

    await expectAsync(harness.isStacked()).toBeResolvedTo(true);

    await expectAsync(harness.isChecked()).toBeResolvedTo(false);
    await harness.check();
    await expectAsync(harness.isChecked()).toBeResolvedTo(true);
    await harness.uncheck();
    await harness.blur();
    await expectAsync(harness.hasRequiredError()).toBeResolvedTo(true);
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
} from '@angular/forms';
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Standard checkboxes
 */
@Component({
  selector: 'app-forms-checkbox-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxBasicExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected contactMethod: FormGroup;

  constructor() {
    this.contactMethod = this.#formBuilder.group({
      email: new FormControl(false),
      phone: new FormControl(false),
      text: new FormControl(false),
    });

    this.formGroup = this.#formBuilder.group({
      contactMethod: this.contactMethod,
      terms: new FormControl(false),
    });

    this.contactMethod.setValidators(
      (control: AbstractControl): ValidationErrors | null => {
        const group = control as FormGroup;
        const email = group.controls['email'];
        const phone = group.controls['phone'];
        const text = group.controls['text'];

        if (email.value && !phone.value && !text.value) {
          return { emailOnly: true };
        } else {
          return null;
        }
      },
    );
  }

  protected onSubmit(): void {
    this.formGroup.markAllAsTouched();

    console.log(this.formGroup.value);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    data-sky-id="checkbox-group"
    headingText="Contact method"
    headingStyle="5"
    helpPopoverContent="We use your contact info to keep you informed on current events. We will not sell your information."
    hintText="Please select at least one phone-based method."
    [formGroup]="contactMethod"
    [required]="true"
    [stacked]="true"
  >
    <sky-checkbox formControlName="email" labelText="Email" />
    <sky-checkbox formControlName="phone" labelText="Phone" />
    <sky-checkbox formControlName="text" labelText="Text" />
    @if (contactMethod.errors?.['emailOnly']) {
      <sky-form-error
        errorName="emailOnly"
        errorText="Email cannot be the only contact method."
      />
    }
  </sky-checkbox-group>
  <sky-checkbox
    data-sky-id="single-checkbox"
    formControlName="terms"
    labelText="I agree to the terms and conditions"
    [required]="true"
    [stacked]="true"
  />
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

---

## Checkboxes with help key

**Component:** FormsCheckboxHelpKeyExampleComponent

**Selector:** `app-forms-checkbox-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import {
  SkyCheckboxGroupHarness,
  SkyCheckboxHarness,
} from '@skyux/forms/testing';

import { FormsCheckboxHelpKeyExampleComponent } from './example.component';

describe('Basic checkbox group example', () => {
  async function setupCheckboxGroupTest(options: {
    dataSkyId: string;
  }): Promise<{
    checkboxGroupHarness: SkyCheckboxGroupHarness;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      FormsCheckboxHelpKeyExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const checkboxGroupHarness = await loader.getHarness(
      SkyCheckboxGroupHarness.with({ dataSkyId: options.dataSkyId }),
    );

    const helpController = TestBed.inject(SkyHelpTestingController);

    fixture.detectChanges();
    await fixture.whenStable();

    return { checkboxGroupHarness, helpController };
  }

  async function setupCheckboxTest(options: { dataSkyId: string }): Promise<{
    checkboxHarness: SkyCheckboxHarness;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      FormsCheckboxHelpKeyExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const checkboxHarness = await loader.getHarness(
      SkyCheckboxHarness.with({ dataSkyId: options.dataSkyId }),
    );

    const helpController = TestBed.inject(SkyHelpTestingController);

    fixture.detectChanges();
    await fixture.whenStable();

    return { checkboxHarness, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        NoopAnimationsModule,
        FormsCheckboxHelpKeyExampleComponent,
        SkyHelpTestingModule,
      ],
    });
  });

  it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
    const { checkboxGroupHarness } = await setupCheckboxGroupTest({
      dataSkyId: 'checkbox-group',
    });

    const checkboxButtons = await checkboxGroupHarness.getCheckboxes();

    await expectAsync(checkboxGroupHarness.getHeadingText()).toBeResolvedTo(
      'Contact method',
    );
    await expectAsync(checkboxGroupHarness.getHeadingLevel()).toBeResolvedTo(
      undefined,
    );
    await expectAsync(checkboxGroupHarness.getHeadingStyle()).toBeResolvedTo(5);
    await expectAsync(checkboxGroupHarness.getHintText()).toBeResolvedTo(
      'Please select at least one phone-based method.',
    );

    await expectAsync(checkboxButtons[0].getLabelText()).toBeResolvedTo(
      'Email',
    );
    await expectAsync(checkboxButtons[0].getHintText()).toBeResolvedTo('');

    await expectAsync(checkboxButtons[1].getLabelText()).toBeResolvedTo(
      'Phone',
    );
    await expectAsync(checkboxButtons[1].getHintText()).toBeResolvedTo('');

    await expectAsync(checkboxButtons[2].getLabelText()).toBeResolvedTo('Text');
    await expectAsync(checkboxButtons[2].getHintText()).toBeResolvedTo('');
  });

  it('should display an error message when there is a custom validation error', async () => {
    const { checkboxGroupHarness } = await setupCheckboxGroupTest({
      dataSkyId: 'checkbox-group',
    });

    const checkboxHarness = (await checkboxGroupHarness.getCheckboxes())[0];

    await checkboxHarness.check();

    await expectAsync(
      checkboxGroupHarness.hasError('emailOnly'),
    ).toBeResolvedTo(true);
  });

  it('should have the correct help key for checkbox groups', async () => {
    const { checkboxGroupHarness, helpController } =
      await setupCheckboxGroupTest({
        dataSkyId: 'checkbox-group',
      });

    await checkboxGroupHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('contact-help');
  });

  it('should check and uncheck checkboxes in display errors if they are required', async () => {
    const { checkboxHarness } = await setupCheckboxTest({
      dataSkyId: 'single-checkbox',
    });

    await expectAsync(checkboxHarness.isStacked()).toBeResolvedTo(true);

    await expectAsync(checkboxHarness.isChecked()).toBeResolvedTo(false);
    await checkboxHarness.check();
    await expectAsync(checkboxHarness.isChecked()).toBeResolvedTo(true);
    await checkboxHarness.uncheck();
    await checkboxHarness.blur();
    await expectAsync(checkboxHarness.hasRequiredError()).toBeResolvedTo(true);
  });

  it('should have the correct help key for checkboxes', async () => {
    const { checkboxHarness, helpController } = await setupCheckboxTest({
      dataSkyId: 'single-checkbox',
    });

    await checkboxHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('terms-help');
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
} from '@angular/forms';
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Checkboxes with help key
 */
@Component({
  selector: 'app-forms-checkbox-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxHelpKeyExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected contactMethod: FormGroup;

  constructor() {
    this.contactMethod = this.#formBuilder.group({
      email: new FormControl(false),
      phone: new FormControl(false),
      text: new FormControl(false),
    });

    this.formGroup = this.#formBuilder.group({
      contactMethod: this.contactMethod,
      terms: new FormControl(false),
    });

    this.contactMethod.setValidators(
      (control: AbstractControl): ValidationErrors | null => {
        const group = control as FormGroup;
        const email = group.controls['email'];
        const phone = group.controls['phone'];
        const text = group.controls['text'];

        if (email.value && !phone.value && !text.value) {
          return { emailOnly: true };
        } else {
          return null;
        }
      },
    );
  }

  protected onSubmit(): void {
    this.formGroup.markAllAsTouched();

    console.log(this.formGroup.value);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    data-sky-id="checkbox-group"
    headingText="Contact method"
    headingStyle="5"
    helpKey="contact-help"
    hintText="Please select at least one phone-based method."
    [formGroup]="contactMethod"
    [required]="true"
    [stacked]="true"
  >
    <sky-checkbox formControlName="email" labelText="Email" />
    <sky-checkbox formControlName="phone" labelText="Phone" />
    <sky-checkbox formControlName="text" labelText="Text" />
    @if (contactMethod.errors?.['emailOnly']) {
      <sky-form-error
        errorName="emailOnly"
        errorText="Email cannot be the only contact method."
      />
    }
  </sky-checkbox-group>
  <sky-checkbox
    data-sky-id="single-checkbox"
    formControlName="terms"
    helpKey="terms-help"
    labelText="I agree to the terms and conditions"
    [required]="true"
    [stacked]="true"
  />
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

---

## Icon checkbox group

**Component:** FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Import Path:** `@skyux/code-examples`

### Code Files

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
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Icon checkbox group
 */
@Component({
  selector: 'app-forms-checkbox-icon-group-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxIconGroupExampleComponent {
  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      bold: new FormControl(false),
      italic: new FormControl(false),
      underline: new FormControl(false),
    });
  }

  public onSubmit(): void {
    console.log(this.formGroup.value);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    headingText="Text formatting"
    [formGroup]="formGroup"
    [headingHidden]="true"
    [stacked]="true"
  >
    <sky-checkbox
      formControlName="bold"
      iconName="text-bold"
      labelHidden="true"
      labelText="Bold"
    />
    <sky-checkbox
      formControlName="italic"
      iconName="text-italic"
      labelHidden="true"
      labelText="Italic"
    />
    <sky-checkbox
      formControlName="underline"
      iconName="text-underline"
      labelHidden="true"
      labelText="Underline"
    />
  </sky-checkbox-group>
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

---

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

## Selection boxes with checkboxes

**Component:** FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyIdService } from '@skyux/core';
import { SkySelectionBoxGridHarness } from '@skyux/forms/testing';

import { FormsSelectionBoxCheckboxExampleComponent } from './example.component';

let index: number;

async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
  selectionBoxGridHarness: SkySelectionBoxGridHarness;
}> {
  await TestBed.configureTestingModule({
    imports: [FormsSelectionBoxCheckboxExampleComponent, NoopAnimationsModule],
  }).compileComponents();

  index = 0;
  spyOn(TestBed.inject(SkyIdService), 'generateId').and.callFake(
    () => `MOCK_ID_${++index}`,
  );

  const fixture = TestBed.createComponent(
    FormsSelectionBoxCheckboxExampleComponent,
  );
  const loader = TestbedHarnessEnvironment.loader(fixture);

  const selectionBoxGridHarness: SkySelectionBoxGridHarness = options.dataSkyId
    ? await loader.getHarness(
        SkySelectionBoxGridHarness.with({
          dataSkyId: options.dataSkyId,
        }),
      )
    : await loader.getHarness(SkySelectionBoxGridHarness);

  return { selectionBoxGridHarness };
}

describe('Selection box checkbox example', () => {
  it('should set up the component', async () => {
    const { selectionBoxGridHarness } = await setupTest();

    const selectionBoxHarnesses =
      await selectionBoxGridHarness.getSelectionBoxes();

    expect(selectionBoxHarnesses.length).toBe(3);

    await expectAsync(selectionBoxHarnesses[0].getHeaderText()).toBeResolvedTo(
      'Save time and effort',
    );
    await expectAsync(
      selectionBoxHarnesses[1].getDescriptionText(),
    ).toBeResolvedTo(
      'Encourage supporters to interact with your organization.',
    );
    await expectAsync(
      (await selectionBoxHarnesses[2].getIcon())?.getIconName(),
    ).toBeResolvedTo('people-team');

    await (await selectionBoxHarnesses[0].getControl()).check();
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormArray,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCheckboxModule, SkySelectionBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Selection boxes with checkboxes
 */
@Component({
  selector: 'app-forms-selection-box-checkbox-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyIconModule,
    SkyIdModule,
    SkySelectionBoxModule,
  ],
})
export class FormsSelectionBoxCheckboxExampleComponent {
  protected checkboxControls: FormControl[] | undefined;

  protected selectionBoxes: {
    description: string;
    iconName: string;
    name: string;
    selected?: boolean;
  }[] = [
    {
      name: 'Save time and effort',
      iconName: 'clock',
      description:
        'Automate mundane tasks and spend more time on the things that matter.',
    },
    {
      name: 'Boost engagement',
      iconName: 'person',
      description: 'Encourage supporters to interact with your organization.',
    },
    {
      name: 'Build relationships',
      iconName: 'people-team',
      description:
        'Connect to supporters on a personal level and maintain accurate data.',
    },
  ];

  protected formGroup: FormGroup;

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    const checkboxArray = this.#buildCheckboxes();
    this.checkboxControls = checkboxArray.controls as FormControl[];

    this.formGroup = this.#formBuilder.group({
      checkboxes: checkboxArray,
    });
  }

  #buildCheckboxes(): FormArray {
    const checkboxArray = this.selectionBoxes.map((checkbox) =>
      this.#formBuilder.control(checkbox.selected),
    );

    return this.#formBuilder.array(checkboxArray);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-selection-box-grid>
    @for (control of checkboxControls; track control; let i = $index) {
      <sky-selection-box [control]="checkbox">
        <sky-icon [iconName]="selectionBoxes[i].iconName" />
        <sky-selection-box-header #checkboxHeaderId="skyId" skyId>
          {{ selectionBoxes[i].name }}
        </sky-selection-box-header>
        <sky-selection-box-description>
          {{ selectionBoxes[i].description }}
        </sky-selection-box-description>
        <sky-checkbox
          #checkbox
          [formControl]="control"
          [labelledBy]="checkboxHeaderId.id"
        />
      </sky-selection-box>
    }
  </sky-selection-box-grid>
</form>

```

---

## Selection boxes with radio buttons

**Component:** FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyIdService } from '@skyux/core';
import { SkySelectionBoxGridHarness } from '@skyux/forms/testing';

import { FormsSelectionBoxRadioExampleComponent } from './example.component';

let index: number;

async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
  selectionBoxGridHarness: SkySelectionBoxGridHarness;
}> {
  await TestBed.configureTestingModule({
    imports: [FormsSelectionBoxRadioExampleComponent, NoopAnimationsModule],
  }).compileComponents();

  spyOn(TestBed.inject(SkyIdService), 'generateId').and.callFake(
    () => `MOCK_ID_${++index}`,
  );

  index = 0;
  const fixture = TestBed.createComponent(
    FormsSelectionBoxRadioExampleComponent,
  );
  const loader = TestbedHarnessEnvironment.loader(fixture);

  const selectionBoxGridHarness: SkySelectionBoxGridHarness = options.dataSkyId
    ? await loader.getHarness(
        SkySelectionBoxGridHarness.with({
          dataSkyId: options.dataSkyId,
        }),
      )
    : await loader.getHarness(SkySelectionBoxGridHarness);

  return { selectionBoxGridHarness };
}

describe('Selection box radio example', () => {
  it('should set up the component', async () => {
    const { selectionBoxGridHarness } = await setupTest();

    const selectionBoxHarnesses =
      await selectionBoxGridHarness.getSelectionBoxes();

    expect(selectionBoxHarnesses.length).toBe(3);

    await expectAsync(selectionBoxHarnesses[0].getHeaderText()).toBeResolvedTo(
      'Save time and effort',
    );
    await expectAsync(
      selectionBoxHarnesses[1].getDescriptionText(),
    ).toBeResolvedTo(
      'Encourage supporters to interact with your organization.',
    );
    await expectAsync(
      (await selectionBoxHarnesses[2].getIcon())?.getIconName(),
    ).toBeResolvedTo('people-team');

    await (await selectionBoxHarnesses[0].getControl()).check();
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
import { SkyIdModule } from '@skyux/core';
import { SkyRadioModule, SkySelectionBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Selection boxes with radio buttons
 */
@Component({
  selector: 'app-forms-selection-box-radio-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyIdModule,
    SkyRadioModule,
    SkySelectionBoxModule,
  ],
})
export class FormsSelectionBoxRadioExampleComponent {
  protected items: Record<string, string>[] = [
    {
      name: 'Save time and effort',
      iconName: 'clock',
      description:
        'Automate mundane tasks and spend more time on the things that matter.',
      value: 'clock',
    },
    {
      name: 'Boost engagement',
      iconName: 'person',
      description: 'Encourage supporters to interact with your organization.',
      value: 'engagement',
    },
    {
      name: 'Build relationships',
      iconName: 'people-team',
      description:
        'Connect to supporters on a personal level and maintain accurate data.',
      value: 'relationships',
    },
  ];

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      myOption: this.items[2]['value'],
    });
  }
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <sky-radio-group ariaLabel="Demo options" formControlName="myOption">
    <sky-selection-box-grid>
      @for (item of items; track item) {
        <sky-selection-box [control]="radio">
          <sky-icon [iconName]="item['iconName']" />
          <sky-selection-box-header #radioHeaderId="skyId" skyId>
            {{ item['name'] }}
          </sky-selection-box-header>
          <sky-selection-box-description>
            {{ item['description'] }}
          </sky-selection-box-description>
          <sky-radio
            #radio
            [labelledBy]="radioHeaderId.id"
            [value]="item['value']"
          />
        </sky-selection-box>
      }
    </sky-selection-box-grid>
  </sky-radio-group>
</form>

```

---

## Box with header, content, and controls

**Component:** LayoutBoxBasicExampleComponent

**Selector:** `app-layout-box-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyBoxHarness } from '@skyux/layout/testing';

import { LayoutBoxBasicExampleComponent } from './example.component';

describe('Basic box', () => {
  async function setupTest(): Promise<{
    boxHarness: SkyBoxHarness;
    fixture: ComponentFixture<LayoutBoxBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LayoutBoxBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const boxHarness = await loader.getHarness(
      SkyBoxHarness.with({
        dataSkyId: 'box-example',
      }),
    );

    return { boxHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LayoutBoxBasicExampleComponent],
    });
  });

  it('should display the correct box', async () => {
    const { boxHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(boxHarness.getAriaLabel()).toBeResolvedTo('Box header');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyBoxModule } from '@skyux/layout';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Box with header, content, and controls
 */
@Component({
  selector: 'app-layout-box-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyBoxModule, SkyDropdownModule],
})
export class LayoutBoxBasicExampleComponent {}

```

#### example.component.html

```html
<sky-box
  data-sky-id="box-example"
  headingText="Box header"
  helpPopoverContent="Example help content for box"
>
  <sky-box-controls>
    <sky-dropdown buttonType="context-menu" label="Box example context menu">
      <sky-dropdown-menu>
        <sky-dropdown-item>
          <button type="button">Action 1</button>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <button type="button">Action 2</button>
        </sky-dropdown-item>
      </sky-dropdown-menu>
    </sky-dropdown>
  </sky-box-controls>
  <sky-box-content>
    <p>Box content</p>
  </sky-box-content>
</sky-box>

```

---

## Box with help key

**Component:** LayoutBoxHelpKeyExampleComponent

**Selector:** `app-layout-box-help-key-example`

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
import { SkyBoxHarness } from '@skyux/layout/testing';

import { LayoutBoxHelpKeyExampleComponent } from './example.component';

describe('Basic box', () => {
  async function setupTest(): Promise<{
    boxHarness: SkyBoxHarness;
    fixture: ComponentFixture<LayoutBoxHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(LayoutBoxHelpKeyExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const boxHarness = await loader.getHarness(
      SkyBoxHarness.with({
        dataSkyId: 'box-example',
      }),
    );

    const helpController = TestBed.inject(SkyHelpTestingController);

    return { boxHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LayoutBoxHelpKeyExampleComponent, SkyHelpTestingModule],
    });
  });

  it('should display the correct box', async () => {
    const { boxHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(boxHarness.getAriaLabel()).toBeResolvedTo('Box header');
  });

  it('should have the correct help key', async () => {
    const { boxHarness, helpController } = await setupTest();

    await boxHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('box-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyBoxModule } from '@skyux/layout';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Box with help key
 */
@Component({
  selector: 'app-layout-box-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyBoxModule, SkyDropdownModule],
})
export class LayoutBoxHelpKeyExampleComponent {}

```

#### example.component.html

```html
<sky-box data-sky-id="box-example" headingText="Box header" helpKey="box-help">
  <sky-box-controls>
    <sky-dropdown buttonType="context-menu" label="Box example context menu">
      <sky-dropdown-menu>
        <sky-dropdown-item>
          <button type="button">Action 1</button>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <button type="button">Action 2</button>
        </sky-dropdown-item>
      </sky-dropdown-menu>
    </sky-dropdown>
  </sky-box-controls>
  <sky-box-content>
    <p>Box content</p>
  </sky-box-content>
</sky-box>

```

---
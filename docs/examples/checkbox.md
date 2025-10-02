---
component: 'checkbox'
type: 'code-examples'
description: 'Code examples for the checkbox component.'
---

# Checkbox Code Examples

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
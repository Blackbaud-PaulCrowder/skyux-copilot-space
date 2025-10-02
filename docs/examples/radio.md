---
component: 'radio'
type: 'code-examples'
description: 'Code examples for the radio component.'
---

# Radio Code Examples

## Radio group with help key

**Component:** FormsRadioHelpKeyExampleComponent

**Selector:** `app-forms-radio-help-key-example`

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
import { SkyRadioGroupHarness } from '@skyux/forms/testing';

import { FormsRadioHelpKeyExampleComponent } from './example.component';

describe('Basic radio group example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    radioGroupHarness: SkyRadioGroupHarness;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(FormsRadioHelpKeyExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpController = TestBed.inject(SkyHelpTestingController);

    const radioGroupHarness = await loader.getHarness(
      SkyRadioGroupHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { radioGroupHarness, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        NoopAnimationsModule,
        FormsRadioHelpKeyExampleComponent,
        SkyHelpTestingModule,
      ],
    });
  });

  it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
    const { radioGroupHarness } = await setupTest({ dataSkyId: 'radio-group' });

    const radioButtons = await radioGroupHarness.getRadioButtons();

    await expectAsync(radioGroupHarness.getHeadingText()).toBeResolvedTo(
      'Payment method',
    );
    await expectAsync(radioGroupHarness.getHeadingLevel()).toBeResolvedTo(4);
    await expectAsync(radioGroupHarness.getHeadingStyle()).toBeResolvedTo(4);
    await expectAsync(radioGroupHarness.getHintText()).toBeResolvedTo(
      'Card methods require proof of identification.',
    );

    await expectAsync(radioButtons[0].getLabelText()).toBeResolvedTo('Cash');
    await expectAsync(radioButtons[0].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[1].getLabelText()).toBeResolvedTo('Check');
    await expectAsync(radioButtons[1].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[2].getLabelText()).toBeResolvedTo(
      'Apple pay',
    );
    await expectAsync(radioButtons[2].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[3].getLabelText()).toBeResolvedTo('Credit');
    await expectAsync(radioButtons[3].getHintText()).toBeResolvedTo(
      'A 2% late fee is applied to payments made after the due date.',
    );

    await expectAsync(radioButtons[4].getLabelText()).toBeResolvedTo('Debit');
    await expectAsync(radioButtons[4].getHintText()).toBeResolvedTo('');
  });

  it('should display an error message when there is a custom validation error', async () => {
    const { radioGroupHarness } = await setupTest({ dataSkyId: 'radio-group' });

    const radioHarness = (await radioGroupHarness.getRadioButtons())[1];

    await radioHarness.check();

    await expectAsync(
      radioGroupHarness.hasError('processingIssue'),
    ).toBeResolvedTo(true);
  });

  it('should have the correct help key for radio group', async () => {
    const { radioGroupHarness, helpController } = await setupTest({
      dataSkyId: 'radio-group',
    });

    await radioGroupHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('payment-help');
  });

  it('should have the correct help key for radio', async () => {
    const { radioGroupHarness, helpController } = await setupTest({
      dataSkyId: 'radio-group',
    });
    const radioHarness = (await radioGroupHarness.getRadioButtons())[0];

    await radioHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('cash-help');
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
import { SkyRadioModule } from '@skyux/forms';

interface DemoForm {
  paymentMethod: FormControl<string | null>;
}

interface Item {
  name: string;
  value: string;
  disabled?: boolean;
  hintText?: string;
  helpKey?: string;
}

function validatePaymentMethod(
  control: AbstractControl,
): ValidationErrors | null {
  return control.value === 'check' ? { processingIssue: true } : null;
}

/**
 * @title Radio group with help key
 */
@Component({
  selector: 'app-forms-radio-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioHelpKeyExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected hintText = 'Card methods require proof of identification.';
  protected paymentMethod: FormControl<string | null>;

  protected paymentOptions: Item[] = [
    {
      name: 'Cash',
      value: 'cash',
      helpKey: 'cash-help',
    },
    { name: 'Check', value: 'check' },
    { name: 'Apple pay', value: 'apple', disabled: true },
    {
      name: 'Credit',
      value: 'credit',
      hintText: 'A 2% late fee is applied to payments made after the due date.',
    },
    { name: 'Debit', value: 'debit' },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.paymentMethod = this.#formBuilder.control(
      this.paymentOptions[0].name,
      {
        validators: [validatePaymentMethod],
      },
    );

    this.formGroup = this.#formBuilder.group({
      paymentMethod: this.paymentMethod,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    data-sky-id="radio-group"
    formControlName="paymentMethod"
    headingLevel="4"
    headingText="Payment method"
    helpKey="payment-help"
    [hintText]="hintText"
  >
    @for (option of paymentOptions; track option) {
      <sky-radio
        [disabled]="option.disabled"
        [value]="option.value"
        [labelText]="option.name"
        [helpKey]="option.helpKey"
        [hintText]="option.hintText"
      />
    }
    @if (paymentMethod.errors?.['processingIssue']) {
      <sky-form-error
        errorName="processingIssue"
        errorText="An error occurred with this payment method. Please contact us to resolve."
      />
    }
  </sky-radio-group>
</form>

```

---

## Radio group with icons

**Component:** FormsRadioIconExampleComponent

**Selector:** `app-forms-radio-icon-example`

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
import { SkyRadioModule } from '@skyux/forms';

interface Item {
  iconName: string;
  label: string;
  name: string;
}

/**
 * @title Radio group with icons
 */
@Component({
  selector: 'app-forms-radio-icon-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioIconExampleComponent {
  protected formGroup: FormGroup;

  protected views: Item[] = [
    { iconName: 'table', label: 'Table', name: 'table' },
    { iconName: 'text-number-list-ltr', label: 'List', name: 'list' },
    { iconName: 'location', label: 'Map', name: 'map' },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      myView: this.views[0].name,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    class="sky-switch-icon-group"
    formControlName="myView"
    headingHidden="true"
    headingText="View"
  >
    @for (view of views; track view) {
      <sky-radio
        [labelHidden]="true"
        [iconName]="view.iconName"
        [labelText]="view.label"
        [value]="view.name"
      />
    }
  </sky-radio-group>
</form>

```

---

## Radio group with standard setup

**Component:** FormsRadioStandardExampleComponent

**Selector:** `app-forms-radio-standard-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyRadioGroupHarness } from '@skyux/forms/testing';

import { FormsRadioStandardExampleComponent } from './example.component';

describe('Basic radio group example', () => {
  async function setupTest(options: {
    dataSkyId: string;
  }): Promise<SkyRadioGroupHarness> {
    const fixture = TestBed.createComponent(FormsRadioStandardExampleComponent);

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyRadioGroupHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return harness;
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, FormsRadioStandardExampleComponent],
    });
  });

  it('should have the appropriate heading text/level/style, label text, and hint text', async () => {
    const harness = await setupTest({ dataSkyId: 'radio-group' });

    const radioButtons = await harness.getRadioButtons();

    await expectAsync(harness.getHeadingText()).toBeResolvedTo(
      'Payment method',
    );
    await expectAsync(harness.getHeadingLevel()).toBeResolvedTo(4);
    await expectAsync(harness.getHeadingStyle()).toBeResolvedTo(4);
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Card methods require proof of identification.',
    );

    await expectAsync(radioButtons[0].getLabelText()).toBeResolvedTo('Cash');
    await expectAsync(radioButtons[0].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[1].getLabelText()).toBeResolvedTo('Check');
    await expectAsync(radioButtons[1].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[2].getLabelText()).toBeResolvedTo(
      'Apple pay',
    );
    await expectAsync(radioButtons[2].getHintText()).toBeResolvedTo('');

    await expectAsync(radioButtons[3].getLabelText()).toBeResolvedTo('Credit');
    await expectAsync(radioButtons[3].getHintText()).toBeResolvedTo(
      'A 2% late fee is applied to payments made after the due date.',
    );

    await expectAsync(radioButtons[4].getLabelText()).toBeResolvedTo('Debit');
    await expectAsync(radioButtons[4].getHintText()).toBeResolvedTo('');
  });

  it('should display an error message when there is a custom validation error', async () => {
    const harness = await setupTest({ dataSkyId: 'radio-group' });

    const radioHarness = (await harness.getRadioButtons())[1];

    await radioHarness.check();

    await expectAsync(harness.hasError('processingIssue')).toBeResolvedTo(true);
  });

  it('should show a help popover with the expected text', async () => {
    const harness = await setupTest({
      dataSkyId: 'radio-group',
    });

    await harness.clickHelpInline();

    const helpPopoverTitle = await harness.getHelpPopoverTitle();
    expect(helpPopoverTitle).toBe('Are there fees?');

    const helpPopoverContent = await harness.getHelpPopoverContent();
    expect(helpPopoverContent).toBe(
      `We don't charge fees for any payment method. The only exception is when credit card payments are late, which incurs a 2% fee.`,
    );
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
import { SkyRadioModule } from '@skyux/forms';

interface DemoForm {
  paymentMethod: FormControl<string | null>;
}

interface Item {
  name: string;
  value: string;
  disabled?: boolean;
  hintText?: string;
  helpContent?: string;
}

function validatePaymentMethod(
  control: AbstractControl,
): ValidationErrors | null {
  return control.value === 'check' ? { processingIssue: true } : null;
}

/**
 * @title Radio group with standard setup
 */
@Component({
  selector: 'app-forms-radio-standard-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioStandardExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected helpPopoverContent =
    "We don't charge fees for any payment method. The only exception is when credit card payments are late, which incurs a 2% fee.";
  protected helpPopoverTitle = 'Are there fees?';
  protected hintText = 'Card methods require proof of identification.';
  protected paymentMethod: FormControl<string | null>;

  protected paymentOptions: Item[] = [
    {
      name: 'Cash',
      value: 'cash',
      helpContent:
        'We accept cash at any of our locations and affiliated partners.',
    },
    { name: 'Check', value: 'check' },
    { name: 'Apple pay', value: 'apple', disabled: true },
    {
      name: 'Credit',
      value: 'credit',
      hintText: 'A 2% late fee is applied to payments made after the due date.',
    },
    { name: 'Debit', value: 'debit' },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.paymentMethod = this.#formBuilder.control(
      this.paymentOptions[0].name,
      {
        validators: [validatePaymentMethod],
      },
    );

    this.formGroup = this.#formBuilder.group({
      paymentMethod: this.paymentMethod,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    data-sky-id="radio-group"
    formControlName="paymentMethod"
    headingLevel="4"
    headingText="Payment method"
    [helpPopoverContent]="helpPopoverContent"
    [helpPopoverTitle]="helpPopoverTitle"
    [hintText]="hintText"
  >
    @for (option of paymentOptions; track option) {
      <sky-radio
        [disabled]="option.disabled"
        [value]="option.value"
        [labelText]="option.name"
        [helpPopoverContent]="option.helpContent"
        [hintText]="option.hintText"
      />
    }
    @if (paymentMethod.errors?.['processingIssue']) {
      <sky-form-error
        errorName="processingIssue"
        errorText="An error occurred with this payment method. Please contact us to resolve."
      />
    }
  </sky-radio-group>
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
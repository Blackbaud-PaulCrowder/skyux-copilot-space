---
component: 'colorpicker'
type: 'code-examples'
description: 'Code examples for the colorpicker component.'
---

# Colorpicker Code Examples

## Basic example

**Component:** ColorpickerBasicExampleComponent

**Selector:** `app-colorpicker-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyColorpickerHarness } from '@skyux/colorpicker/testing';

import { ColorpickerBasicExampleComponent } from './example.component';

describe('Basic colorpicker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyColorpickerHarness;
    fixture: ComponentFixture<ColorpickerBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(ColorpickerBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyColorpickerHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ColorpickerBasicExampleComponent],
    });
  });

  it('should have the initial values set', async () => {
    const { harness } = await setupTest({ dataSkyId: 'favorite-color' });

    await expectAsync(harness.getLabelText()).toBeResolvedTo(
      'What is your favorite color?',
    );
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Pick a color with at least 80% opacity.',
    );
  });

  it('should throw an error if a low opacity color is selected', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'favorite-color',
    });

    await harness.clickColorpickerButton();
    await expectAsync(harness.isColorpickerOpen()).toBeResolvedTo(true);

    const dropdown = await harness.getColorpickerDropdown();

    await dropdown.setAlphaValue('.2');
    await dropdown.clickApplyButton();
    fixture.detectChanges();

    await expectAsync(harness.hasError('opaque')).toBeResolvedTo(true);
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
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyColorpickerModule, SkyColorpickerOutput } from '@skyux/colorpicker';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Basic example
 */
@Component({
  selector: 'app-colorpicker-basic-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerBasicExampleComponent {
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;

  protected swatches: string[] = [
    '#BD4040',
    '#617FC2',
    '#60AC68',
    '#3486BA',
    '#E87134',
    '#DA9C9C',
  ];

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected onSelectedColorChanged(args: SkyColorpickerOutput): void {
    console.log('Reactive form color changed:', args);
  }

  protected submit(): void {
    const controlValue = this.favoriteColor.value;
    const favoriteColor = isColorpickerOutput(controlValue)
      ? controlValue.hex
      : controlValue;

    alert('Your favorite color is: \n' + favoriteColor);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="submit()">
  <sky-colorpicker
    #colorPicker
    data-sky-id="favorite-color"
    labelText="What is your favorite color?"
    hintText="Pick a color with at least 80% opacity."
    [stacked]="true"
    (selectedColorChanged)="onSelectedColorChanged($event)"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [presetColors]="swatches"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>

  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

---

## Colorpicker with help key

**Component:** ColorpickerHelpKeyExampleComponent

**Selector:** `app-colorpicker-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyColorpickerHarness } from '@skyux/colorpicker/testing';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';

import { ColorpickerHelpKeyExampleComponent } from './example.component';

describe('Basic colorpicker example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyColorpickerHarness;
    fixture: ComponentFixture<ColorpickerHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(ColorpickerHelpKeyExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpController = TestBed.inject(SkyHelpTestingController);

    const harness = await loader.getHarness(
      SkyColorpickerHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ColorpickerHelpKeyExampleComponent, SkyHelpTestingModule],
    });
  });

  it('should have the initial values set', async () => {
    const { harness } = await setupTest({ dataSkyId: 'favorite-color' });

    await expectAsync(harness.getLabelText()).toBeResolvedTo(
      'What is your favorite color?',
    );
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Pick a color with at least 80% opacity.',
    );
  });

  it('should throw an error if a low opacity color is selected', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'favorite-color',
    });

    await harness.clickColorpickerButton();
    await expectAsync(harness.isColorpickerOpen()).toBeResolvedTo(true);

    const dropdown = await harness.getColorpickerDropdown();

    await dropdown.setAlphaValue('.2');
    await dropdown.clickApplyButton();
    fixture.detectChanges();

    await expectAsync(harness.hasError('opaque')).toBeResolvedTo(true);
  });

  it('should have the correct help key', async () => {
    const { harness, helpController } = await setupTest({
      dataSkyId: 'favorite-color',
    });

    await harness.clickHelpInline();

    helpController.expectCurrentHelpKey('color-help');
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
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyColorpickerModule, SkyColorpickerOutput } from '@skyux/colorpicker';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Colorpicker with help key
 */
@Component({
  selector: 'app-colorpicker-help-key-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerHelpKeyExampleComponent {
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;

  protected swatches: string[] = [
    '#BD4040',
    '#617FC2',
    '#60AC68',
    '#3486BA',
    '#E87134',
    '#DA9C9C',
  ];

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected onSelectedColorChanged(args: SkyColorpickerOutput): void {
    console.log('Reactive form color changed:', args);
  }

  protected submit(): void {
    const controlValue = this.favoriteColor.value;
    const favoriteColor = isColorpickerOutput(controlValue)
      ? controlValue.hex
      : controlValue;

    alert('Your favorite color is: \n' + favoriteColor);
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="submit()">
  <sky-colorpicker
    #colorPicker
    data-sky-id="favorite-color"
    labelText="What is your favorite color?"
    helpKey="color-help"
    hintText="Pick a color with at least 80% opacity."
    [stacked]="true"
    (selectedColorChanged)="onSelectedColorChanged($event)"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [presetColors]="swatches"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>

  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

---

## Interact with a colorpicker programmatically

**Component:** ColorpickerProgrammaticExampleComponent

**Selector:** `app-colorpicker-programmatic-example`

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
  ValidationErrors,
} from '@angular/forms';
import {
  SkyColorpickerMessage,
  SkyColorpickerMessageType,
  SkyColorpickerModule,
  SkyColorpickerOutput,
} from '@skyux/colorpicker';

import { Subject } from 'rxjs';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Interact with a colorpicker programmatically
 */
@Component({
  selector: 'app-colorpicker-programmatic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerProgrammaticExampleComponent {
  protected colorpickerController = new Subject<SkyColorpickerMessage>();
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;
  protected showResetButton = false;

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected openColorpicker(): void {
    this.#sendMessage(SkyColorpickerMessageType.Open);
  }

  protected resetColorpicker(): void {
    this.#sendMessage(SkyColorpickerMessageType.Reset);
  }

  protected toggleResetButton(): void {
    this.#sendMessage(SkyColorpickerMessageType.ToggleResetButton);
  }

  #sendMessage(type: SkyColorpickerMessageType): void {
    this.colorpickerController.next({ type });
  }
}

```

#### example.component.html

```html
<form class="sky-margin-stacked-xxl" [formGroup]="formGroup">
  <sky-colorpicker
    #colorPicker
    labelText="What is your favorite color?"
    hintText="Pick a color with at least 80% opacity."
    [messageStream]="colorpickerController"
    [showResetButton]="showResetButton"
    [stacked]="true"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>
</form>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openColorpicker()"
>
  Open colorpicker
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="resetColorpicker()"
>
  Reset colorpicker
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="toggleResetButton()"
>
  Toggle reset button
</button>

```

---
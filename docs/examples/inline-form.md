---
component: 'inline-form'
type: 'code-examples'
description: 'Code examples for the inline-form component.'
---

# Inline Form Code Examples

## Inline form with basic setup

**Component:** InlineFormBasicExampleComponent

**Selector:** `app-inline-form-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineFormHarness } from '@skyux/inline-form/testing';

import { InlineFormBasicExampleComponent } from './example.component';

describe('Inline form basic demo', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyInlineFormHarness;
    fixture: ComponentFixture<InlineFormBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [InlineFormBasicExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(InlineFormBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness = await loader.getHarness(
      SkyInlineFormHarness.with({ dataSkyId: options.dataSkyId }),
    );
    return { harness, fixture };
  }

  it('should change the first name', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'first-name',
    });

    // You can query components inside the inline form when closed.
    const editButton = await harness.querySelector('button.sky-btn');
    await editButton.click();

    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(true);

    // You can query inline form buttons when the form is open.
    const buttons = await harness.getButtons();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Jane',
    );
    await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
    await expectAsync(buttons[1].getStyleType()).toBeResolvedTo('link');

    // You can query components from the inline form template when the form is open.
    const inputHarness = await (
      await harness.getTemplate()
    ).querySelector('input');

    await inputHarness.sendKeys('t');
    await inputHarness.blur();
    fixture.detectChanges();

    await buttons[0].click();
    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(false);

    await editButton.click();
    fixture.detectChanges();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Janet',
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
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
  SkyInlineFormModule,
} from '@skyux/inline-form';

interface DemoForm {
  firstName: FormControl<string>;
}

/**
 * @title Inline form with basic setup
 */
@Component({
  selector: 'app-inline-form-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInlineFormModule,
    SkyInputBoxModule,
  ],
})
export class InlineFormBasicExampleComponent {
  protected firstName = 'Jane';
  public formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected showForm = false;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      firstName: new FormControl<string>('', { nonNullable: true }),
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      this.firstName = this.formGroup.value.firstName ?? '';
    }

    this.showForm = false;
    this.formGroup.patchValue({
      firstName: undefined,
    });
  }

  protected onInlineFormOpen(): void {
    this.showForm = true;
    this.formGroup.patchValue({
      firstName: this.firstName,
    });
  }
}

```

#### example.component.html

```html
<sky-inline-form
  data-sky-id="first-name"
  [config]="inlineFormConfig"
  [showForm]="showForm"
  [template]="inlineFormTemplate"
  (close)="onInlineFormClose($event)"
>
  <table>
    <tr>
      <th>First name:</th>
      <td>
        {{ firstName }}
      </td>
      <td>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="onInlineFormOpen()"
        >
          <sky-icon iconName="edit" />
        </button>
      </td>
    </tr>
  </table>
</sky-inline-form>

<ng-template #inlineFormTemplate>
  <form [formGroup]="formGroup">
    <sky-input-box labelText="First name">
      <input formControlName="firstName" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Inline form with custom buttons

**Component:** InlineFormCustomButtonsExampleComponent

**Selector:** `app-inline-form-custom-buttons-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineFormHarness } from '@skyux/inline-form/testing';

import { InlineFormCustomButtonsExampleComponent } from './example.component';

describe('Inline form custom button demo', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyInlineFormHarness;
    fixture: ComponentFixture<InlineFormCustomButtonsExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [InlineFormCustomButtonsExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      InlineFormCustomButtonsExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness = await loader.getHarness(
      SkyInlineFormHarness.with({ dataSkyId: options.dataSkyId }),
    );
    return { harness, fixture };
  }

  it('should change the first name', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'first-name',
    });

    // You can query components inside the inline form when closed.
    const editButton = await harness.querySelector('button.sky-btn');
    await editButton.click();

    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(true);

    // You can query inline form buttons when the form is open.
    const buttons = await harness.getButtons();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Jane',
    );
    await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
    await expectAsync(buttons[1].getStyleType()).toBeResolvedTo('default');

    // You can query components from the inline form template when the form is open.
    const inputHarness = await (
      await harness.getTemplate()
    ).querySelector('input');

    await inputHarness.sendKeys('t');
    await inputHarness.blur();
    fixture.detectChanges();

    await buttons[0].click();
    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(false);

    await editButton.click();
    fixture.detectChanges();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Janet',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
  SkyInlineFormModule,
} from '@skyux/inline-form';

interface DemoForm {
  firstName: FormControl<string>;
}

/**
 * @title Inline form with custom buttons
 */
@Component({
  selector: 'app-inline-form-custom-buttons-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInlineFormModule,
    SkyInputBoxModule,
  ],
})
export class InlineFormCustomButtonsExampleComponent implements OnInit {
  protected firstName = 'Jane';
  public formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.Custom,
    buttons: [
      {
        action: 'save',
        text: 'Save',
        styleType: 'primary',
      },
      {
        action: 'clear',
        text: 'Clear',
        styleType: 'default',
      },
      {
        action: 'reset',
        text: 'Reset',
        styleType: 'default',
      },
      {
        action: 'cancel',
        text: 'Cancel',
        styleType: 'link',
      },
    ],
  };

  protected showForm = false;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      firstName: new FormControl<string>('', { nonNullable: true }),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe(() => {
      if (
        this.inlineFormConfig.buttons &&
        this.inlineFormConfig.buttons[0].disabled !== this.formGroup.invalid
      ) {
        this.inlineFormConfig.buttons[0].disabled = this.formGroup.invalid;
        this.inlineFormConfig = { ...{}, ...this.inlineFormConfig };
      }
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    switch (args.reason) {
      case 'save':
        this.firstName = this.formGroup.value.firstName ?? '';
        this.showForm = false;
        break;

      case 'clear':
        this.formGroup.patchValue({ firstName: '' });
        break;

      case 'reset':
        this.formGroup.setValue({ firstName: this.firstName });
        break;

      default:
        this.showForm = false;
        break;
    }
  }

  protected onInlineFormOpen(): void {
    this.showForm = true;
    this.formGroup.patchValue({
      firstName: this.firstName,
    });
  }
}

```

#### example.component.html

```html
<sky-inline-form
  data-sky-id="first-name"
  [config]="inlineFormConfig"
  [showForm]="showForm"
  [template]="inlineFormTemplate"
  (close)="onInlineFormClose($event)"
>
  <table>
    <tr>
      <th>First name:</th>
      <td>
        {{ firstName }}
      </td>
      <td>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="onInlineFormOpen()"
        >
          <sky-icon iconName="edit" />
        </button>
      </td>
    </tr>
  </table>
</sky-inline-form>

<ng-template #inlineFormTemplate>
  <form [formGroup]="formGroup">
    <sky-input-box labelText="First name">
      <input formControlName="firstName" required type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Inline form with repeater

**Component:** InlineFormRepeatersExampleComponent

**Selector:** `app-inline-form-repeaters-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineFormHarness } from '@skyux/inline-form/testing';
import { SkyRepeaterHarness } from '@skyux/lists/testing';

import { InlineFormRepeatersExampleComponent } from './example.component';

describe('Inline form with repeater demo', () => {
  async function setupTest(options: { itemId: number }): Promise<{
    repeaterHarness: SkyRepeaterHarness;
    inlineFormHarness: SkyInlineFormHarness;
    fixture: ComponentFixture<InlineFormRepeatersExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [InlineFormRepeatersExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      InlineFormRepeatersExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const repeaterHarness = await loader.getHarness(SkyRepeaterHarness);
    const item = await repeaterHarness.getRepeaterItems();
    const inlineFormHarness =
      await item[options.itemId].queryHarness(SkyInlineFormHarness);

    return { repeaterHarness, inlineFormHarness, fixture };
  }

  it('should set up the spring gala item inline form', async () => {
    const { inlineFormHarness } = await setupTest({
      itemId: 1,
    });
    const editButton = await inlineFormHarness?.querySelector('button.sky-btn');
    await editButton?.click();
    await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(true);

    // You can query inline form buttons when the form is open.
    const buttons = await inlineFormHarness?.getButtons();
    await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
    const cancelButton = buttons[1];

    await cancelButton.click();
    await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(
      false,
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
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
} from '@skyux/inline-form';
import { SkyRepeaterModule } from '@skyux/lists';

interface DemoForm {
  id: FormControl<string>;
  note: FormControl<string>;
  title: FormControl<string>;
}

interface Item {
  id: string;
  title: string | undefined;
  note: string | undefined;
}

/**
 * @title Inline form with repeater
 */
@Component({
  selector: 'app-inline-form-repeaters-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
  ],
})
export class InlineFormRepeatersExampleComponent {
  protected activeInlineFormId: string | undefined;
  protected formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected items: Item[] = [
    {
      id: '1',
      title: '2019 Spring Gala',
      note: 'Gala for friends and family',
    },
    {
      id: '2',
      title: '2019 Special Winter Event',
      note: 'A special event',
    },
    {
      id: '3',
      title: '2019 Donor Appreciation Event',
      note: 'Event for all donors and families',
    },
    {
      id: '4',
      title: '2020 Spring Gala',
      note: 'Gala for friends and family',
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: new FormControl('', { nonNullable: true }),
      title: new FormControl('', { nonNullable: true }),
      note: new FormControl('', { nonNullable: true }),
    });
  }

  protected showInlineForm(item: Item): void {
    this.activeInlineFormId = item.id;
    this.formGroup.patchValue({
      note: item.note,
      title: item.title,
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      const found = this.items.find(
        (item) => item.id === this.activeInlineFormId,
      );

      if (found) {
        found.note = this.formGroup.value.note;
        found.title = this.formGroup.value.title;
      }
    }

    this.formGroup.patchValue({
      note: undefined,
      title: undefined,
    });

    // Close the active form.
    this.activeInlineFormId = undefined;
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of items; track item) {
    <sky-repeater-item
      [inlineFormConfig]="inlineFormConfig"
      [inlineFormTemplate]="inlineFormTemplate"
      [showInlineForm]="activeInlineFormId === item.id"
      (inlineFormClose)="onInlineFormClose($event)"
    >
      <sky-repeater-item-title>
        <div class="sky-font-emphasized">
          {{ item.title }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-context-menu>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="showInlineForm(item)"
        >
          <sky-icon iconName="edit" />
        </button>
      </sky-repeater-item-context-menu>

      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

<ng-template #inlineFormTemplate>
  <form novalidate [formGroup]="formGroup">
    <sky-input-box labelTex="Title" stacked="true">
      <input formControlName="title" type="text" />
    </sky-input-box>
    <sky-input-box labelText="Note">
      <input formControlName="note" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Repeater with inline form

**Component:** ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

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
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
} from '@skyux/inline-form';
import { SkyRepeaterModule } from '@skyux/lists';

interface DemoForm {
  id: FormControl<string>;
  note: FormControl<string>;
  title: FormControl<string>;
}

interface Item {
  id: string;
  title: string | undefined;
  note: string | undefined;
}

/**
 * @title Repeater with inline form
 */
@Component({
  selector: 'app-lists-repeater-inline-form-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
  ],
})
export class ListsRepeaterInlineFormExampleComponent {
  protected activeInlineFormId: string | undefined;
  protected formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected items: Item[] = [
    {
      id: '1',
      title: '2019 Spring Gala',
      note: 'Gala for friends and family',
    },
    {
      id: '2',
      title: '2019 Special Winter Event',
      note: 'A special event',
    },
    {
      id: '3',
      title: '2019 Donor Appreciation Event',
      note: 'Event for all donors and families',
    },
    {
      id: '4',
      title: '2020 Spring Gala',
      note: 'Gala for friends and family',
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: new FormControl('', { nonNullable: true }),
      title: new FormControl('', { nonNullable: true }),
      note: new FormControl('', { nonNullable: true }),
    });
  }

  protected showInlineForm(item: Item): void {
    this.activeInlineFormId = item.id;
    this.formGroup.patchValue({
      note: item.note,
      title: item.title,
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      const found = this.items.find(
        (item) => item.id === this.activeInlineFormId,
      );
      if (found) {
        found.note = this.formGroup.value.note;
        found.title = this.formGroup.value.title;
      }
    }

    this.formGroup.patchValue({
      note: undefined,
      title: undefined,
    });

    // Close the active form.
    this.activeInlineFormId = undefined;
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of items; track item) {
    <sky-repeater-item
      [inlineFormConfig]="inlineFormConfig"
      [inlineFormTemplate]="inlineFormTemplate"
      [showInlineForm]="activeInlineFormId === item.id"
      (inlineFormClose)="onInlineFormClose($event)"
    >
      <sky-repeater-item-title>
        <div class="sky-font-emphasized">
          {{ item.title }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-context-menu>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="showInlineForm(item)"
        >
          <sky-icon iconName="edit" />
        </button>
      </sky-repeater-item-context-menu>

      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

<ng-template #inlineFormTemplate>
  <form novalidate [formGroup]="formGroup">
    <sky-input-box labelText="Title" stacked="true">
      <input formControlName="title" type="text" />
    </sky-input-box>
    <sky-input-box labelText="Note">
      <input formControlName="note" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---
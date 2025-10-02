---
component: 'icon'
type: 'code-examples'
description: 'Code examples for the icon component.'
---

# Icon Code Examples

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

## Icon with basic setup

**Component:** IconBasicExampleComponent

**Selector:** `app-icon-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyIconHarness } from '@skyux/icon/testing';

import { IconBasicExampleComponent } from './example.component';

describe('Basic icon', () => {
  async function setupTest(): Promise<{
    iconHarness: SkyIconHarness;
    fixture: ComponentFixture<IconBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(IconBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const iconHarness = await loader.getHarness(
      SkyIconHarness.with({
        dataSkyId: 'icon-example',
      }),
    );

    return { iconHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IconBasicExampleComponent],
    });
  });

  it('should display the correct icon', async () => {
    const { iconHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(iconHarness.getIconName()).toBeResolvedTo('calendar-ltr');
    await expectAsync(iconHarness.getVariant()).toBeResolvedTo('solid');
    await expectAsync(iconHarness.getIconSize()).toBeResolvedTo('xl');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Icon with basic setup
 */
@Component({
  selector: 'app-icon-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule],
})
export class IconBasicExampleComponent {}

```

#### example.component.html

```html
<sky-icon iconName="calendar-ltr" iconSize="xxxs" />
<sky-icon iconName="calendar-ltr" iconSize="xxs" />
<sky-icon iconName="calendar-ltr" iconSize="xs" />
<sky-icon iconName="calendar-ltr" iconSize="s" />
<sky-icon iconName="calendar-ltr" />
<sky-icon iconName="calendar-ltr" iconSize="l" />
<sky-icon iconName="calendar-ltr" iconSize="xl" />
<sky-icon iconName="calendar-ltr" iconSize="xxl" />
<sky-icon iconName="calendar-ltr" iconSize="xxxl" />
<sky-icon
  data-sky-id="icon-example"
  iconName="calendar-ltr"
  variant="solid"
  iconSize="xl"
/>

<div>
  <sky-icon iconName="navigation" iconSize="xl" />
</div>

<div>
  <sky-icon iconName="chevron-down" iconSize="xl" />
</div>

```

---

## Icons in buttons

**Component:** IconIconButtonExampleComponent

**Selector:** `app-icon-icon-button-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyIconHarness } from '@skyux/icon/testing';

import { IconIconButtonExampleComponent } from './example.component';

describe('Icon button', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    iconHarness: SkyIconHarness;
    fixture: ComponentFixture<IconIconButtonExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(IconIconButtonExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const iconHarness = await loader.getHarness(
      SkyIconHarness.with({
        dataSkyId: options?.dataSkyId,
      }),
    );

    return { iconHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IconIconButtonExampleComponent],
    });
  });

  it('should display the icon in the text icon button', async () => {
    const { iconHarness, fixture } = await setupTest({
      dataSkyId: 'text-button-icon',
    });

    fixture.detectChanges();

    await expectAsync(iconHarness.getIconName()).toBeResolvedTo('save');
  });

  it('should display the icon in the icon only button', async () => {
    const { iconHarness, fixture } = await setupTest({
      dataSkyId: 'button-icon',
    });

    fixture.detectChanges();

    await expectAsync(iconHarness.getIconName()).toBeResolvedTo('edit');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Icons in buttons
 */
@Component({
  selector: 'app-icon-icon-button-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule],
})
export class IconIconButtonExampleComponent {
  protected textButtonClick(): void {
    alert('Text with icon button clicked');
  }

  protected iconOnlyButtonClick(): void {
    alert('Icon only button clicked');
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="textButtonClick()"
>
  <sky-icon data-sky-id="text-button-icon" iconName="save" />
  Save
</button>

<button
  class="sky-btn sky-btn-icon-borderless"
  type="button"
  (click)="iconOnlyButtonClick()"
>
  <sky-icon data-sky-id="button-icon" iconName="edit" />
</button>

```

---
---
component: 'selection-box'
type: 'code-examples'
description: 'Code examples for the selection-box component.'
---

# Selection Box Code Examples

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
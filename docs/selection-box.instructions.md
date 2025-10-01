---
component: 'selection-box'
description: 'Design guidelines, API documentation, and usage instructions for the selection-box component extracted from SKY UX documentation.'
---

# Selection Box Component Guidelines

## Component Overview
Selection boxes present users with a choice to make or a question to answer before proceeding with a one-time process.

## Usage

### ✅ Use when

Use selection boxes when users must make a choice or answer a standalone question before proceeding with a one-time process such as a setup or configuration task. Selection boxes represent the only decision on a page.

**✅ Do use selection boxes to present standalone options during a one-time process such as onboarding.**

Use selection boxes when options are abstract or potentially unfamiliar to users. Use icons and descriptions to provide additional insight.

**✅ Do use selection boxes to present options or categories that are unfamiliar to users.**

### ❌ Don't use when

Don't use selection boxes for repeatable tasks such as data entry. Use other selection controls, such as checkboxes or radio buttons, instead.

Don't use selection boxes for fewer than 3 options or more than 12 options. Use other selection controls instead.

**❌ Don't use selection boxes in tasks or workflows that users complete repeatedly.**

Don't use selection boxes for fewer than 3 options or more than 12 options. Use other selection controls instead.

## Anatomy

- Box
- Checkbox or radio button
- Header
- Icon
- Description

## Options

### Icons

Use icons to add meaning and help users distinguish between options.

- Don't use icons if they don't add useful information.
- Don't reuse icons within a group of selection boxes.
- Don't use icons with some selection boxes in a group but not others.
- Don't use selection boxes with titles only. If neither icons nor descriptions are necessary, use other selection controls instead.

### Descriptions

Use descriptions to add meaning and help users distinguish between options.

- Don't use descriptions if they don't add useful information.
- Don't use descriptions with some selection boxes in a group but not others.
- Don't use selection boxes with titles only. If neither icons nor descriptions are necessary, use other selection controls instead.

## Behavior and states

### Responsiveness

On smaller viewports, selection boxes hide their icons and use smaller typography and tighter spacing.

## Content

## Layout

Selection boxes are center-aligned within a container based on the number of options and the container's width. Don't use other layouts with selection boxes.

**✅ Do center-align selection boxes and use matching heights.**

## Related information

### Components

- Checkbox
- Icon
- Radio button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Package:** `@skyux/code-examples`

#### SkySelectionBoxDescriptionComponent

Specifies the description to display in a selection box.

**Selector:** `sky-selection-box-description`

**Package:** `@skyux/forms`

#### SkySelectionBoxGridComponent

Creates a grid layout for an array of selection boxes.

**Selector:** `sky-selection-box-grid`

**Package:** `@skyux/forms`

**Inputs:**

- `alignItems`: `SkySelectionBoxGridAlignItemsType` - How to display the selection boxes in the grid. (default: 'center')

#### SkySelectionBoxHeaderComponent

Specifies the header to display in a selection box.

**Selector:** `sky-selection-box-header`

**Package:** `@skyux/forms`

#### SkySelectionBoxComponent

Creates a button to present users with a choice or question before proceeding with a one-time process.

**Selector:** `sky-selection-box`

**Package:** `@skyux/forms`

**Inputs:**

- `control`: `SkyCheckboxComponent | SkyRadioComponent | undefined` - The radio button or checkbox to display in the selection box. **[Required]**

#### SkySelectionBoxModule

**Package:** `@skyux/forms`

#### SkySelectionBoxGridAlignItemsType

**Package:** `@skyux/forms`

#### SkySelectionBoxGridAlignItems

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkySelectionBoxGridHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxGridHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxGridHarness

Harness for interacting with a selection box grid component in tests.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxHarness

Harness to interact with a selection box component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Selection boxes with checkboxes

**Selector:** `app-forms-selection-box-checkbox-example`

**TypeScript:**

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

**Template:**

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

#### Selection boxes with radio buttons

**Selector:** `app-forms-selection-box-radio-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
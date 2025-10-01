---
component: 'inline-form'
description: 'Design guidelines, API documentation, and usage instructions for the inline-form component extracted from SKY UX documentation.'
---

# Inline Form Component Guidelines

## Component Overview
Inline forms render in context in the current view instead of in a separate modal. It is most commonly used in grids and repeaters.

## Usage

### ✅ Use when

Use inline forms when the add or edit form is simple in terms of the number of fields and the complexity of the input controls.

Use inline forms when the surrounding content will not distract users from the add or edit task.

Use inline forms when users are highly likely to add multiple records in succession.

Use inline forms to add or edit a subsection within a larger modal form.

Use inline forms when users can abandon the task while the add or edit form is open.

For more details on adding and editing data, see managing data guidelines

### ❌ Don't use when

Don't use inline forms when the add or edit form requires a large amount of page morphing or users must scroll to complete the form.

Don't use inline forms within a paginated or infinite scroll list of items.

Don't use inline forms when users must finish the add or edit form before doing anything else.

## Anatomy

### Edit form

When users click the Edit button, the inline form replaces the view-only content.

### Primary buttons

The primary action on the inline form should be Save or Done.

Use Save if the inline form saves data to the database immediately.

Use Done if the inline form does not save data to the database immediately because it is part of a larger form.

### Guidelines

- Form design
- Manage data

- Edit button
- Inline form
- Form field
- Form action buttons

## Behavior and states

### Edit form

When users click the Edit button, the inline form replaces the view-only content.

## Content

### Primary buttons

The primary action on the inline form should be Save or Done.

Use Save if the inline form saves data to the database immediately.

Use Done if the inline form does not save data to the database immediately because it is part of a larger form.

## Related information

### Guidelines

- Form design
- Manage data

## API Documentation

### Components and Directives

#### InlineFormBasicExampleComponent

**Selector:** `app-inline-form-basic-example`

**Package:** `@skyux/code-examples`

#### InlineFormCustomButtonsExampleComponent

**Selector:** `app-inline-form-custom-buttons-example`

**Package:** `@skyux/code-examples`

#### InlineFormRepeatersExampleComponent

**Selector:** `app-inline-form-repeaters-example`

**Package:** `@skyux/code-examples`

#### ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Package:** `@skyux/code-examples`

#### SkyInlineFormComponent

Renders form content in the current view instead of a separate modal.

**Selector:** `sky-inline-form`

**Package:** `@skyux/inline-form`

**Inputs:**

- `template`: `TemplateRef<unknown> | undefined` - The template to instantiate the inline form. **[Required]**
- `config`: `SkyInlineFormConfig | undefined` - Configuration options for the buttons to display with the inline form. **[Required]**
- `showForm`: `boolean | undefined` - Whether to display the inline form. Users can toggle between displaying
and hiding the inline form. (default: false)

**Outputs:**

- `close`: `EventEmitter<SkyInlineFormCloseArgs>` - Fires when users close the inline form.

#### SkyInlineFormModule

**Package:** `@skyux/inline-form`

#### SkyInlineFormButtonAction

**Package:** `@skyux/inline-form`

#### SkyInlineFormButtonConfig

Specifies configuration options for the inline form's buttons when `buttonLayout` is set to `Custom`.

**Package:** `@skyux/inline-form`

#### SkyInlineFormButtonLayout

**Package:** `@skyux/inline-form`

#### SkyInlineFormCloseArgs

**Package:** `@skyux/inline-form`

#### SkyInlineFormConfig

Specifies configuration options for the buttons to display with the inline form.

**Package:** `@skyux/inline-form`

#### SkyInlineFormButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineFormButtonHarness` instances.

**Package:** `@skyux/inline-form/testing`

#### SkyInlineFormButtonHarness

Harness to interact with inline form button component in tests.

**Package:** `@skyux/inline-form/testing`

#### SkyInlineFormHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineFormHarness` instances.

**Package:** `@skyux/inline-form/testing`

#### SkyInlineFormHarness

Harness to interact with inline form components in tests.

**Package:** `@skyux/inline-form/testing`

#### SkyInlineFormTemplateHarness

Harness to interact with inline form template components in tests.

**Package:** `@skyux/inline-form/testing`

### Code Examples

#### Inline form with basic setup

**Selector:** `app-inline-form-basic-example`

**TypeScript:**

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

**Template:**

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

#### Inline form with custom buttons

**Selector:** `app-inline-form-custom-buttons-example`

**TypeScript:**

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

**Template:**

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

#### Inline form with repeater

**Selector:** `app-inline-form-repeaters-example`

**TypeScript:**

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

**Template:**

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

#### Repeater with inline form

**Selector:** `app-lists-repeater-inline-form-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
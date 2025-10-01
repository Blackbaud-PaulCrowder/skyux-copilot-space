---
component: 'checkbox'
description: 'Design guidelines, API documentation, and usage instructions for the checkbox component extracted from SKY UX documentation.'
---

# Checkbox Component Guidelines

## Component Overview
Checkboxes let users select multiple items from a short list of items.

## Usage

### ✅ Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

**✅ Do use a checkbox when users must make a single yes/no decision.**

Use checkbox groups when users must make multiple, related yes/no decisions.

**✅ Do use a checkbox group for multiple, related checkboxes.**

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

**✅ Do use icon checkboxes when icons clearly communicate the options.**

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

**✅ Do use checkboxes to enable conditional inputs as part of a task.**

### ❌ Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different selection input, such as a lookup field, instead.

**❌ Don't use a checkbox group for a homogenous list of more than 5 items.**

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

**✅ Do use checkbox groups for more than 5 checkboxes when the choices represent distinct decisions.**

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use toggle switch instead.

**❌ Don't use checkboxes to alternate between two states when changes take effect immediately.**

Don't use a checkbox group for a lone checkbox in a form or field group.

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

**❌ Don't use a checkbox group for a lone checkbox.**

## Anatomy

### Individual checkbox

### Checkbox group

### Icon checkbox

- Checkbox
- Label
- Required field marker
- Help inline button
- Hint text

## Options

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use headingLevel to specify a semantic heading level in the document structure and headingStyle to set the heading font style. For example, use a label as a heading to indicate that a checkbox group is a form section just like other field groups. Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

**Checkbox group labels can be turned into HTML headings.**

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

- Constraints or requirements on a checkbox group
- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use stacked to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the checkbox group:

- Is the last input inside a field group
- Is the last input on a form

Also use stacked when an individual checkbox is immediately followed by another form input. However, don't use stacked when the checkbox is followed by one or more conditional fields. Use sky-margin-stacked-sm instead for closely related fields.

If a checkbox group uses headingLevel, use stacked when the checkbox group is followed by a field group or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

## Content

## Layout

Don't wrap a checkbox group inside a field group component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's headingLevel and headingStyle to 3 to use the label as an h3 heading with a sky-font-heading-3 visual style. An additional heading from a field group would be unnecessary and confusing.

**❌ Don't use a field group with a lone checkbox group.**

## Accessibility

## Related information

### Components

- Field group
- Lookup
- Modal
- Radio button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsCheckboxBasicExampleComponent

**Selector:** `app-forms-checkbox-basic-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxHelpKeyExampleComponent

**Selector:** `app-forms-checkbox-help-key-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### SkyCheckboxChange

Fires when users select or deselect the checkbox.

**Package:** `@skyux/forms`

#### SkyCheckboxGroupHeadingLevel

**Package:** `@skyux/forms`

#### SkyCheckboxGroupHeadingStyle

**Package:** `@skyux/forms`

#### SkyCheckboxGroupComponent

Organizes checkboxes into a group.

**Selector:** `sky-checkbox-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingText`: `string` - The text to display as the checkbox group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox group fieldset legend. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `required`: `boolean` - Whether the checkbox group is required. (default: false)
- `headingLevel`: `SkyCheckboxGroupHeadingLevel | undefined` - The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.
- `headingStyle`: `SkyCheckboxGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 4)
- `stacked`: `boolean` - Whether the checkbox group is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox group.

#### SkyCheckboxLabelComponent

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-checkbox-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyCheckboxComponent

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value
is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

**Selector:** `sky-checkbox`

**Package:** `@skyux/forms`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `iconName`: `string | undefined` - The SVG icon to display in place of the checkbox. To group icon checkboxes
like in the demo, place the checkboxes within a `sky-checkbox-group`.
- `labelHidden`: `boolean` - Indicates whether to hide the `labelText`. (default: false)
- `labelText`: `string | undefined` - The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only.
Specifying `labelText` also enables automatic error message handling for checkbox.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete. (default: false)
- `stacked`: `boolean` - Whether the checkbox is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group,
set `stacked` on the checkbox group component instead. (default: false)
- `tabindex`: `number | undefined` - The index for the checkbox. If not defined, the index is set to the position of the
checkbox on load. (default: 0)
- `checkboxType`: `string` - The background color type after users select a checkbox where the
`icon` property displays an icon in place of the checkbox. The valid options correspond to
[the label component's](https://developer.blackbaud.com/skyux/components/label)
label types. `"info"` creates a blue background, `"success"` creates a green
background, `"warning"` creates an orange background, and `"danger"` creates a red background. (default: "info")
- `checked`: `boolean` - Whether the checkbox is selected.
- `disabled`: `boolean` - Whether the checkbox is disabled.
- `id`: `string | undefined` - The ID for the checkbox.
If a value is not provided, an autogenerated ID is used.
- `indeterminate`: `boolean` - Whether the checkbox is in the indeterminate state. This has no visual effect for icon checkboxes.
- `label`: `string | undefined` - The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility)
when the checkbox does not include a visible label. You must set this property for icon
checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels the
checkbox. This sets the checkbox's `aria-labelledby` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
If the checkbox does not include a visible label, use `label` instead.
- `name`: `string` - The name for the checkbox.
If a value is not provided, an autogenerated ID is used.

**Outputs:**

- `change`: `EventEmitter<SkyCheckboxChange>` - Fires when the selected value changes.
- `checkedChange`: `Observable<boolean>` - Fires when users select or deselect the checkbox.
- `disabledChange`: `Observable<boolean>` - Fires when the selected value changes.
- `indeterminateChange`: `Observable<boolean>` - Fires when the indeterminate state changes.

#### SkyCheckboxModule

**Package:** `@skyux/forms`

#### SkyCheckboxFixture

Allows interaction with a SKY UX checkbox component.

**Package:** `@skyux/forms/testing`

⚠️ **This component is deprecated.**

#### SkyCheckboxGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxGroupHarness

Harness for interacting with a checkbox group component in tests.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxHarness

Harness for interacting with a checkbox component in tests.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxLabelHarness

Harness for interacting with a checkbox label component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Standard checkboxes

**Selector:** `app-forms-checkbox-basic-example`

**TypeScript:**

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

**Template:**

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

#### Checkboxes with help key

**Selector:** `app-forms-checkbox-help-key-example`

**TypeScript:**

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

**Template:**

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

#### Icon checkbox group

**Selector:** `app-forms-checkbox-icon-group-example`

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
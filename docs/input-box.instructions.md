---
component: 'input-box'
description: 'Design guidelines, API documentation, and usage instructions for the input-box component extracted from SKY UX documentation.'
---

# Input Box Component Guidelines

## Component Overview
Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

**✅ Do use input boxes to style data entry elements.**

Use input boxes when forms include native HTML elements for text and selection, such as <input>, <select>, and <textarea>. To determine whether to use the HTML <select> element or a SKY UX component, see the form design guidelines.

**✅ Do use input boxes to style HTML elements.**

Use input boxes when forms include SKY UX components, such as country fields, datepickers, lookup fields, phone fields, and timepickers.

**✅ Do use input boxes to style SKY UX components.**

## Anatomy

- Label
- Input field
- Required field marker
- Help inline button
- Hint text

## Options

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

**✅ Do use hint text to explain how to enter data.**

### Character count

When users are likely to exceed a character limit, use a character count indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

**✅ Do use character count indicators on input fields when users may realistically exceed character limits.**

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the form input:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Suggested text

## Behavior and states

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the error-handling guidelines.

## Content

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

**❌ Don't use full sentences or questions for input labels.**

## Layout

Input boxes are most common inside modals and follow form design guidelines. For two-column or three-column layouts, use fluid grid's small gutters spacing option to apply vertical and horizontal padding evenly.

## Related information

### Components

- Character count
- Country field
- Datepicker
- Field group
- Fluid grid
- Help inline button
- Lookup
- Modal
- Phone field
- Timepicker

### Guidelines

- Error handling
- Form design
- Spacing

## API Documentation

### Components and Directives

#### FormsInputBoxBasicExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### SkyInputBoxControlDirective

**Selector:** `input:not([skyId]):not(.sky-form-control),select:not([skyId]):not(.sky-form-control),textarea:not([skyId]):not(.sky-form-control)`

**Package:** `@skyux/forms`

**Inputs:**

- `autocomplete`: `string | undefined`

#### SkyInputBoxHintTextPipe

**Package:** `@skyux/forms`

#### SkyInputBoxHostService

**Package:** `@skyux/forms`

#### SkyInputBoxPopulateArgs

**Package:** `@skyux/forms`

#### SkyInputBoxComponent

A wrapper component that provides styling and accessibility to form elements.

**Selector:** `sky-input-box`

**Package:** `@skyux/forms`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to visually highlight the input box as disabled. To disable the input box's
input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled`
property. If the input element is mapped to an Angular form control
(e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically;
if the input element is not associated with an Angular form control, the `disabled`
property on the input box must be set to `true` to visually indicate
the disabled state on the input box. (default: false)
- `hasErrors`: `boolean | undefined` - Whether to visually highlight the input box in an error state. If not specified, the input box
displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error. (default: undefined)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the input box label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the input box label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `labelText`: `string | undefined` - The text to display as the input's label and in known validation error messages. The label
will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX
component included in the input box.
- `characterLimit`: `number | undefined` - The maximum number of characters allowed in the input. A [SKY UX character count](https://developer.blackbaud.com/skyux/components/character-count)
will be placed on the input element with the appropriate validator.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `BooleanInput` - Whether the input box is stacked on another input box. When specified, the appropriate
vertical spacing is automatically added to the input box.

#### SkyInputBoxModule

**Package:** `@skyux/forms`

#### SkyInputBoxHarnessFilters

A set of criteria that can be used to filter a list of SkyInputBoxHarness instances.

**Package:** `@skyux/forms/testing`

#### SkyInputBoxHarness

Harness for interacting with an input box component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Input box

**Selector:** `app-forms-input-box-basic-example`

**TypeScript:**

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

**Template:**

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

#### Input box with custom errors

**Selector:** `app-forms-input-box-basic-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
---
component: 'email-validation'
description: 'Design guidelines, API documentation, and usage instructions for the email-validation component extracted from SKY UX documentation.'
---

# Email Validation Component Guidelines

## Component Overview
The email validation module validates the format of email addresses in input fields.

## Usage

### ✅ Use when

Use email validation when users must enter valid email addresses.

### ❌ Don't use when

Don't use email validation when users can enter multiple types of data in an input field.

## Anatomy

- Input field
- Status indicator (danger)

## Behavior and states

## Content

## Related information

### Components

- Status indicator
- URL validation

### Guidelines

- Error handling
- Form design

## API Documentation

### Components and Directives

#### ValidationEmailValidationControlValidatorExampleComponent

**Selector:** `app-validation-email-validation-control-validator-example`

**Package:** `@skyux/code-examples`

#### ValidationEmailValidationDirectiveExampleComponent

**Selector:** `app-validation-email-validation-directive-example`

**Package:** `@skyux/code-examples`

#### SkyEmailValidationDirective

Adds email address validation to an input element. The directive uses `NgModel` to bind data.

**Selector:** `[skyEmailValidation]`

**Package:** `@skyux/validation`

#### SkyEmailValidationModule

**Package:** `@skyux/validation`

### Code Examples

#### Email validation on reactive form controls

**Selector:** `app-validation-email-validation-control-validator-example`

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
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyValidators } from '@skyux/validation';

/**
 * @title Email validation on reactive form controls
 */
@Component({
  selector: 'app-validation-email-validation-control-validator-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class ValidationEmailValidationControlValidatorExampleComponent {
  protected get emailControl(): AbstractControl | null {
    return this.formGroup.get('email');
  }

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      email: new FormControl(undefined, [
        Validators.required,
        SkyValidators.email,
      ]),
    });
  }
}

```

**Template:**

```html
<form novalidate [formGroup]="formGroup">
  <div>
    <sky-input-box stacked="true" labelText="Email address">
      <input formControlName="email" type="text" />
    </sky-input-box>
  </div>
</form>

```

#### Email validation using input directive

**Selector:** `app-validation-email-validation-directive-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyEmailValidationModule } from '@skyux/validation';

/**
 * @title Email validation using input directive
 */
@Component({
  selector: 'app-validation-email-validation-directive-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyEmailValidationModule,
    SkyInputBoxModule,
  ],
})
export class ValidationEmailValidationDirectiveExampleComponent {
  protected exampleModel: {
    emailAddress?: string;
  } = {};
}

```

**Template:**

```html
<form novalidate>
  <div>
    <sky-input-box stacked="true" labelText="Email address">
      <input
        class="sky-form-control"
        name="emailAddress"
        skyEmailValidation
        type="text"
        [(ngModel)]="exampleModel.emailAddress"
      />
    </sky-input-box>
  </div>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
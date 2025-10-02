---
component: 'email-validation'
type: 'code-examples'
description: 'Code examples for the email-validation component.'
---

# Email Validation Code Examples

## Email validation on reactive form controls

**Component:** ValidationEmailValidationControlValidatorExampleComponent

**Selector:** `app-validation-email-validation-control-validator-example`

**Import Path:** `@skyux/code-examples`

### Code Files

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

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <div>
    <sky-input-box stacked="true" labelText="Email address">
      <input formControlName="email" type="text" />
    </sky-input-box>
  </div>
</form>

```

---

## Email validation using input directive

**Component:** ValidationEmailValidationDirectiveExampleComponent

**Selector:** `app-validation-email-validation-directive-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---
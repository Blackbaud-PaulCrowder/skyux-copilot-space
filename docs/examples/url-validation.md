---
component: 'url-validation'
type: 'code-examples'
description: 'Code examples for the url-validation component.'
---

# Url Validation Code Examples

## URL validation on reactive form controls

**Component:** ValidationUrlValidationControlValidatorExampleComponent

**Selector:** `app-validation-url-validation-control-validator-example`

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
 * @title URL validation on reactive form controls
 */
@Component({
  selector: 'app-validation-url-validation-control-validator-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class ValidationUrlValidationControlValidatorExampleComponent {
  protected get urlControl(): AbstractControl | null {
    return this.formGroup.get('url');
  }

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      url: new FormControl(undefined, [
        Validators.required,
        SkyValidators.url({
          rulesetVersion: 2,
        }),
      ]),
    });
  }
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <div>
    <sky-input-box stacked="true" labelText="URL">
      <input formControlName="url" type="text" />
    </sky-input-box>
  </div>
</form>

```

---

## URL validation using input directive

**Component:** ValidationUrlValidationDirectiveExampleComponent

**Selector:** `app-validation-url-validation-directive-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import {
  SkyUrlValidationModule,
  SkyUrlValidationOptions,
} from '@skyux/validation';

/**
 * @title URL validation using input directive
 */
@Component({
  selector: 'app-validation-url-validation-directive-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyUrlValidationModule,
  ],
})
export class ValidationUrlValidationDirectiveExampleComponent {
  protected exampleModel: {
    url?: string;
  } = {};

  protected skyUrlValidationOptions: SkyUrlValidationOptions = {
    rulesetVersion: 2,
  };
}

```

#### example.component.html

```html
<form novalidate>
  <div>
    <sky-input-box stacked="true" labelText="URL">
      <input
        name="url"
        [skyUrlValidation]="skyUrlValidationOptions"
        [(ngModel)]="exampleModel.url"
      />
    </sky-input-box>
  </div>
</form>

```

---
---
component: 'url-validation'
description: 'Design guidelines, API documentation, and usage instructions for the url-validation component extracted from SKY UX documentation.'
---

# Url Validation Component Guidelines

## Component Overview
The URL validation module validates the format of URLs in input fields.

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ValidationUrlValidationControlValidatorExampleComponent

**Selector:** `app-validation-url-validation-control-validator-example`

**Package:** `@skyux/code-examples`

#### ValidationUrlValidationDirectiveExampleComponent

**Selector:** `app-validation-url-validation-directive-example`

**Package:** `@skyux/code-examples`

#### SkyUrlValidationOptions

Specifies options for the URL validator component.

**Package:** `@skyux/validation`

#### SkyUrlValidationDirective

Adds URL validation to an input element. The directive uses `NgModel` to bind data.

**Selector:** `[skyUrlValidation]`

**Package:** `@skyux/validation`

**Inputs:**

- `skyUrlValidation`: `SkyUrlValidationOptions | undefined` - Configuration options for the URL validation component.

#### SkyUrlValidationModule

**Package:** `@skyux/validation`

### Code Examples

#### URL validation on reactive form controls

**Selector:** `app-validation-url-validation-control-validator-example`

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

**Template:**

```html
<form novalidate [formGroup]="formGroup">
  <div>
    <sky-input-box stacked="true" labelText="URL">
      <input formControlName="url" type="text" />
    </sky-input-box>
  </div>
</form>

```

#### URL validation using input directive

**Selector:** `app-validation-url-validation-directive-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
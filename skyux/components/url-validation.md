# Design

                 Skip to Main Content

 URL validation
==============

The URL validation module validates the format of URLs in input fields.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/validation`[View in NPM](https://www.npmjs.com/package/@skyux/validation) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/validation/src/lib/modules/url-validation/url-validation.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/validation`Copy None found.

 SkyUrlValidationModule
-----------------------

Type: Module

`import { SkyUrlValidationModule } from '@skyux/validation';`

 SkyUrlValidationDirective
--------------------------

Type: Directive

Selector: `[skyUrlValidation]`

Adds URL validation to an input element. The directive uses `NgModel` to bind data.

### Inputs

#### `skyUrlValidation: SkyUrlValidationOptions | undefined`

Configuration options for the URL validation component.

 SkyUrlValidationOptions
------------------------

Type: Interface

Specifies options for the URL validator component.

    interface SkyUrlValidationOptions {
      rulesetVersion: 1 | 2;
    }

### Properties

#### `rulesetVersion: 1 | 2`

The ruleset for URL validation. Ruleset 1 uses a regular expression, and ruleset 2 uses the third-party [validator.js library](https://github.com/validatorjs/validator.js).

 SkyValidators
--------------

Type: Class

### Methods

#### `SkyValidators.email(control: AbstractControl): null | ValidationErrors`

Validates email addresses in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid email addresses, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `control: AbstractControl`

#### Returns

`null | ValidationErrors`

#### `SkyValidators.url(abstractControl: AbstractControl): null | ValidationErrors`

Validates URLs in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid URLs, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `abstractControl: AbstractControl`

#### Returns

`null | ValidationErrors`

# Development

                 Skip to Main Content

 URL validation
==============

The URL validation module validates the format of URLs in input fields.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/validation`[View in NPM](https://www.npmjs.com/package/@skyux/validation) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/validation/src/lib/modules/url-validation/url-validation.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/validation`Copy None found.

 SkyUrlValidationModule
-----------------------

Type: Module

`import { SkyUrlValidationModule } from '@skyux/validation';`

 SkyUrlValidationDirective
--------------------------

Type: Directive

Selector: `[skyUrlValidation]`

Adds URL validation to an input element. The directive uses `NgModel` to bind data.

### Inputs

#### `skyUrlValidation: SkyUrlValidationOptions | undefined`

Configuration options for the URL validation component.

 SkyUrlValidationOptions
------------------------

Type: Interface

Specifies options for the URL validator component.

    interface SkyUrlValidationOptions {
      rulesetVersion: 1 | 2;
    }

### Properties

#### `rulesetVersion: 1 | 2`

The ruleset for URL validation. Ruleset 1 uses a regular expression, and ruleset 2 uses the third-party [validator.js library](https://github.com/validatorjs/validator.js).

 SkyValidators
--------------

Type: Class

### Methods

#### `SkyValidators.email(control: AbstractControl): null | ValidationErrors`

Validates email addresses in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid email addresses, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `control: AbstractControl`

#### Returns

`null | ValidationErrors`

#### `SkyValidators.url(abstractControl: AbstractControl): null | ValidationErrors`

Validates URLs in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid URLs, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `abstractControl: AbstractControl`

#### Returns

`null | ValidationErrors`

# Examples

                    Skip to Main Content

 URL validation
==============

The URL validation module validates the format of URLs in input fields.Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/validation`[View in NPM](https://www.npmjs.com/package/@skyux/validation) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/validation/src/lib/modules/url-validation/url-validation.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/validation`Copy None found.

 SkyUrlValidationModule
-----------------------

Type: Module

`import { SkyUrlValidationModule } from '@skyux/validation';`

 SkyUrlValidationDirective
--------------------------

Type: Directive

Selector: `[skyUrlValidation]`

Adds URL validation to an input element. The directive uses `NgModel` to bind data.

### Inputs

#### `skyUrlValidation: SkyUrlValidationOptions | undefined`

Configuration options for the URL validation component.

 SkyUrlValidationOptions
------------------------

Type: Interface

Specifies options for the URL validator component.

    interface SkyUrlValidationOptions {
      rulesetVersion: 1 | 2;
    }

### Properties

#### `rulesetVersion: 1 | 2`

The ruleset for URL validation. Ruleset 1 uses a regular expression, and ruleset 2 uses the third-party [validator.js library](https://github.com/validatorjs/validator.js).

 SkyValidators
--------------

Type: Class

### Methods

#### `SkyValidators.email(control: AbstractControl): null | ValidationErrors`

Validates email addresses in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid email addresses, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `control: AbstractControl`

#### Returns

`null | ValidationErrors`

#### `SkyValidators.url(abstractControl: AbstractControl): null | ValidationErrors`

Validates URLs in reactive forms. Add this validator directly to the form control model in the component class. If users enter values that are not valid URLs, the validator throws an error. Since this is a sync validator, it returns a set of validation errors or `null` immediately when users enter values.

#### Parameters

##### `abstractControl: AbstractControl`

#### Returns

`null | ValidationErrors`

### URL validation using input directive

Edit in StackBlitz

URL

Show code

Copy

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

Copy

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
### URL validation on reactive form controls

Edit in StackBlitz

URL

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <div>
        <sky-input-box stacked="true" labelText="URL">
          <input formControlName="url" type="text" />
        </sky-input-box>
      </div>
    </form>

Copy

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
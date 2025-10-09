                

 Email validation
================

The email validation module validates the format of email addresses in input fields.

 Usage
------

### Use when

Use email validation when users must enter valid email addresses.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/email-validation/email-validation-usage1-modern.e5b1cc69c5833ca71b279d1bf1a714ea.png)

Do validate email addresses that users will store as data.

### Don't use when

Don't use email validation when users can enter multiple types of data in an input field.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/email-validation/email-validation-usage-2-modern.d1d87487aa583cdde25e42459f83ffb7.png)

Don't validate email addresses in search fields or filters.

 Anatomy
--------

1

Input field

2

[Status indicator](/skyux/components/status-indicator.md) (danger)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/email-validation/email-validation-anatomy-modern.e1a51c14e0ab5d637b702f81d37e3e7f.png)

 Behavior and states
--------------------

You apply the email validation directive to an input field. The directive triggers the normal and error states, but the input field defines styles and the appearance of those states.

The directive applies its logic when the input field loses focus. It does not trigger error states while users type. After the field enters an error state, it remains in that state until the content matches a valid email address format.

 Content
--------

Use a succinct error message, and explain that users need to use a valid email address format.

 Related information
--------------------

### Components

*   [Status indicator](/skyux/components/status-indicator.md)
*   [URL validation](/skyux/components/url-validation.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/validation`[View in NPM](https://www.npmjs.com/package/@skyux/validation) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/validation/src/lib/modules/email-validation/email-validation.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/validation`Copy None found.

 SkyEmailValidationModule
-------------------------

Type: Module

`import { SkyEmailValidationModule } from '@skyux/validation';`

 SkyEmailValidationDirective
----------------------------

Type: Directive

Selector: `[skyEmailValidation]`

Adds email address validation to an input element. The directive uses `NgModel` to bind data.

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
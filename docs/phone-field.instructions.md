---
component: 'phone-field'
description: 'Design guidelines, API documentation, and usage instructions for the phone-field component extracted from SKY UX documentation.'
---

# Phone Field Component Guidelines

## Component Overview
The phone field module creates a button, search input, and text input for entering and validating international phone numbers. Phone fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use phone fields to validate phone numbers against the correct format for the selected country.

**✅ Do use phone fields to validate phone numbers.**

## Anatomy

### Phone field

### Country selector

- Country selector button
- Label
- Input field
- Default hint text
- Required field marker
- Help inline button
- Additional hint text

## Options

### Default country

By default, the country selector is set to the United States, but you can specify a different default value. You can also set the default dynamically. For example, you can set the default value using location detection.

### Required field marker

When a phone field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a phone field label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a phone field, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the phone field
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a phone field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the phone field from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the phone field:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Country selection

The selected country determines the format to use to validate phone numbers. If users enter phone numbers from a different country, they must also select that country to validate phone numbers based on the correct format.

### Phone format validation

The phone field input directive validates phone numbers based on the format for the selected country. You must specify an error message. In most cases, the error message should be "Enter a phone number matching the format for the selected country."

## Related content

### Components

- Field group
- Help inpline button
- Input box

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### PhoneFieldBasicExampleComponent

**Selector:** `app-phone-field-basic-example`

**Package:** `@skyux/code-examples`

#### SkyPhoneFieldInputDirective

Creates a button, search input, and text input for entering and validating
international phone numbers. Place this attribute on an `input` element, and wrap
that element in a `sky-phone-field` component. By default, the country selector
button displays a flag icon for the default country, and the phone number input
displays a sample of the correct phone number format. When users select the country
selector button, they expose the country search input, which is
[an autocomplete input](https://developer.blackbaud.com/skyux/components/autocomplete)
that allows them to select different countries. When users enter `+` followed by an
international dial code in the phone number input, the country automatically switches
to the country associated with the dial code.

**Selector:** `[skyPhoneFieldInput]`

**Package:** `@skyux/phone-field`

**Inputs:**

- `skyPhoneFieldNoValidate`: `boolean` - Whether to prevent validation on the phone number input. For validation,
phone numbers are driven through the `ngModel` attribute that you specify on an
`input` element or on a `FormControl` in a reactive form. To prevent validation,
set this property to `true`. (default: false)
- `disabled`: `boolean` - Whether to disable the phone field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)

#### SkyPhoneFieldComponent

**Selector:** `sky-phone-field`

**Package:** `@skyux/phone-field`

**Inputs:**

- `supportedCountryISOs`: `string[] | undefined` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country codes for the countries that users can select. By default, all countries are available.
- `allowExtensions`: `boolean` - Whether phone number extensions are allowed. (default: true)
- `defaultCountry`: `string` - The
[International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country code for the default country. The country selector button displays a flag
icon for this default country until users select a different country. (default: "us")
- `returnFormat`: `SkyPhoneFieldNumberReturnFormat` - The format for validated phone numbers.
Options include: `"default"`, `"international"`, and `"national"`. (default: "default")
- `selectedCountry`: `SkyPhoneFieldCountry | undefined` - The currently selected country to validate against.

**Outputs:**

- `selectedCountryChange`: `EventEmitter<SkyPhoneFieldCountry>` - Emits a `SkyPhoneFieldCountry` object when the selected country in the country search
input changes.

#### SkyPhoneFieldModule

**Package:** `@skyux/phone-field`

#### SkyPhoneFieldCountry

**Package:** `@skyux/phone-field`

#### SkyPhoneFieldNumberReturnFormat

Represents the format for validated phone numbers. `default` returns the national format for the
default country, `national` returns the national format for all countries, and `international`
returns the international format for all countries.

**Package:** `@skyux/phone-field`

#### SkyPhoneFieldTestingModule

**Package:** `@skyux/phone-field/testing`

#### SkyPhoneFieldHarnessFilters

A set of criteria that can be used to filter a list of SkyPhoneFieldHarness instances.

**Package:** `@skyux/phone-field/testing`

#### SkyPhoneFieldHarness

Harness for interacting with a phone field component in tests.

**Package:** `@skyux/phone-field/testing`

#### SkyPhoneFieldInputHarness

Harness to interact with the phone field input harness.

**Package:** `@skyux/phone-field/testing`

### Code Examples

#### Phone field with basic setup

**Selector:** `app-phone-field-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyPhoneFieldModule } from '@skyux/phone-field';

/**
 * @title Phone field with basic setup
 */
@Component({
  selector: 'app-phone-field-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyPhoneFieldModule,
  ],
})
export class PhoneFieldBasicExampleComponent {
  public phoneForm: FormGroup;
  public phoneControl: FormControl;

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.phoneControl = this.#formBuilder.control(undefined, {
      validators: Validators.required,
    });
    this.phoneForm = this.#formBuilder.group({
      phoneControl: this.phoneControl,
    });
  }
}

```

**Template:**

```html
<div class="sky-padding-even-lg">
  <form class="phone-field-example" [formGroup]="phoneForm">
    <sky-input-box
      data-sky-id="my-phone-field"
      helpPopoverTitle="How we use your phone number"
      hintText="Enter the phone number where you can be reached before 5 p.m., Monday through Friday."
      labelText="Phone number"
      [helpPopoverContent]="inlineHelpPopover"
    >
      <sky-phone-field [defaultCountry]="'us'">
        <input formControlName="phoneControl" skyPhoneFieldInput />
      </sky-phone-field>
    </sky-input-box>
  </form>
</div>

<ng-template #inlineHelpPopover>
  We use this number for calls and text about your student. We won't use it for
  other purposes.
  <br />
  <br />
  For more information, see our <a>privacy policy</a>.
</ng-template>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
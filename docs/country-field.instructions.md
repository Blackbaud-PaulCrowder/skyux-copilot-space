---
component: 'country-field'
description: 'Design guidelines, API documentation, and usage instructions for the country-field component extracted from SKY UX documentation.'
---

# Country Field Component Guidelines

## Component Overview
The country field lets users enter search criteria and then select a country from search results. Country fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use country fields when users need to select countries.

## Anatomy

### Search results

- Label
- Input field
- Required field marker
- Help inline button
- Selected country flag
- Hint text

## Options

### Required field marker

When a country field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a country field with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a country field, use hint text. This persistent inline help can explain details such as:

- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a country field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the country field from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the country field:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Related information

### Components

- Autocomplete
- Field group
- Help inline button
- Input box
- Phone field

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Package:** `@skyux/code-examples`

#### SkyCountryFieldComponent

**Selector:** `sky-country-field`

**Package:** `@skyux/lookup`

**Inputs:**

- `autocompleteAttribute`: `string | undefined` - The value for the HTML `autocomplete` attribute on the form input. (default: 'off')
- `defaultCountry`: `string | undefined` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country code for the default country.
When search results include the default country, it appears at the top of the list. (default: "us")
- `disabled`: `boolean` - Whether to disable the country field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `supportedCountryISOs`: `string[]` - The [International Organization for Standardization Alpha 2](https://www.nationsonline.org/oneworld/country_code_list.htm)
country codes for the countries that users can select. By default, all countries are available.

**Outputs:**

- `countryFieldFocusout`: `EventEmitter<FocusEvent>` - Fires when the country field is focused out.
- `selectedCountryChange`: `EventEmitter<SkyCountryFieldCountry>` - Fires when the selected country changes.

#### SkyCountryFieldModule

**Package:** `@skyux/lookup`

#### SkyCountryFieldContext

**Package:** `@skyux/lookup`

#### SkyCountryFieldCountry

Represents the data for a given country.

**Package:** `@skyux/lookup`

#### SkyCountryFieldHarnessFilters

A set of criteria that can be used to filter a list of `SkyCountryFieldHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyCountryFieldHarness

Harness for interacting with a country field component in tests.

**Package:** `@skyux/lookup/testing`

#### SkyCountryFieldSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyCountryFieldSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyCountryFieldSearchResultHarness

Harness for interacting with an autocomplete search result in tests.

**Package:** `@skyux/lookup/testing`

### Code Examples

#### Country field with basic setup

**Selector:** `app-lookup-country-field-basic-example`

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
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyCountryFieldCountry, SkyCountryFieldModule } from '@skyux/lookup';

interface DemoForm {
  country: FormControl<SkyCountryFieldCountry | undefined>;
}

function validateCountry(
  control: AbstractControl<SkyCountryFieldCountry | undefined>,
): ValidationErrors | null {
  return control.value?.name === 'Mexico' ? { invalidCountry: true } : null;
}

/**
 * @title Country field with basic setup
 */
@Component({
  selector: 'app-lookup-country-field-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCountryFieldModule,
    SkyInputBoxModule,
  ],
})
export class LookupCountryFieldBasicExampleComponent {
  protected countryControl: FormControl<SkyCountryFieldCountry | undefined>;
  public countryForm: FormGroup<DemoForm>;

  protected helpPopoverContent =
    'We use the country to validate your passport within 10 business days. You can update it at any time.';

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.countryControl = new FormControl(
      {
        name: 'Australia',
        iso2: 'au',
      },
      {
        nonNullable: true,
        validators: [validateCountry, Validators.required],
      },
    );

    this.countryForm = this.#formBuilder.group({
      country: this.countryControl,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="countryForm">
  <sky-input-box
    data-sky-id="country-field"
    hintText="If you have multiple countries, choose your primary country."
    labelText="Country"
    [helpPopoverContent]="helpPopoverContent"
  >
    <sky-country-field formControlName="country" />
    @if (countryControl.errors?.['invalidCountry']) {
      <sky-form-error
        errorName="invalidCountry"
        errorText="This country is no longer available for the date you selected."
      />
    }
  </sky-input-box>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
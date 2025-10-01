---
component: 'field-group'
description: 'Design guidelines, API documentation, and usage instructions for the field-group component extracted from SKY UX documentation.'
---

# Field Group Component Guidelines

## Component Overview
Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.

## Usage

### ✅ Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML fieldset element for its contents. It also creates a legend element and an h3 or h4 heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

**✅ Do use field groups to divide long forms into groups of related elements.**

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with h4 headings in a form section with an h3 heading. For more details, see the form design guidelines.

**✅ Do use nested field groups to create subgroups in form sections.**

### ❌ Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

**❌ Don't use field groups on short or simple forms that don't require groups.**

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a wizard instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a sectioned form instead.

## Anatomy

- Heading
- Help inline button
- Hint text

## Options

### Heading level and style

By default, field group headings create h3 headings with a sky-font-heading-3 visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the form design guidelines.

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the inputs
- Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use stacked. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the form layout guidelines.

## Content

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

**❌ Don't use full sentences or questions for field group headings.**

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see checkboxes and radio buttons.

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an h3 heading with a sky-font-heading-3 visual style. An additional heading from a field group would be unnecessary and confusing.

**❌ Don't use a field group with a lone checkbox group or radio button group.**

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

**✅ Do use a field group with multiple checkbox groups or radio button groups.**

## Related information

### Components

- Checkbox
- Help inline button
- Input box
- Radio button
- Sectioned form
- Wizard

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsFieldGroupBasicExampleComponent

**Selector:** `app-forms-field-group-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFieldGroupHelpKeyExampleComponent

**Selector:** `app-forms-field-group-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyFieldGroupHeadingLevel

**Package:** `@skyux/forms`

#### SkyFieldGroupHeadingStyle

**Package:** `@skyux/forms`

#### SkyFieldGroupComponent

Organizes form fields into a group.

**Selector:** `sky-field-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingLevel`: `SkyFieldGroupHeadingLevel` - The semantic heading level in the document structure. (default: 3)
- `headingText`: `string` - The text to display as the field group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the field group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the field group heading. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `boolean` - Whether the field group is stacked on another field group. When specified, the appropriate
vertical spacing is automatically added to the field group. (default: false)
- `headingStyle`: `SkyFieldGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 3)

#### SkyFieldGroupModule

**Package:** `@skyux/forms`

#### SkyFieldGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFieldGroupHarness

Harness for interacting with a field group component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Field group with basic setup

**Selector:** `app-forms-field-group-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Field group with basic setup
 */
@Component({
  selector: 'app-forms-field-group-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyFieldGroupModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
  ],
})
export class FormsFieldGroupBasicExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected helpPopoverContent =
    'We use your address to validate your application with regulatory agencies and to send correspondence related to your application.';

  protected states = [
    'AK',
    'AZ',
    'AL',
    'AR',
    'CA',
    'CO',
    'CT',
    'DE',
    'DC',
    'FL',
    'GA',
    'HI',
    'ID',
    'IL',
    'IN',
    'IA',
    'KS',
    'KY',
    'LA',
    'ME',
    'MD',
    'MA',
    'MI',
    'MN',
    'MS',
    'MO',
    'MT',
    'NE',
    'NV',
    'NH',
    'NJ',
    'NM',
    'NY',
    'NC',
    'ND',
    'OH',
    'OK',
    'OR',
    'PA',
    'RI',
    'SC',
    'SD',
    'TN',
    'TX',
    'UT',
    'VT',
    'VA',
    'WA',
    'WV',
    'WI',
    'WY',
  ];

  constructor() {
    this.formGroup = this.#formBuilder.group({
      streetAddress: this.#formBuilder.control(undefined),
      city: this.#formBuilder.control(undefined),
      state: this.#formBuilder.control(undefined),
      zipCode: this.#formBuilder.control(undefined),
    });
  }
}

```

**Template:**

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-field-group
      headingText="Address"
      hintText="We use this address for your end-of-year statement."
      [headingStyle]="4"
      [helpPopoverContent]="helpPopoverContent"
    >
      <sky-fluid-grid gutterSize="small" [disableMargin]="true">
        <sky-row>
          <sky-column [screenXSmall]="12">
            <sky-input-box labelText="Street address" stacked="true">
              <input
                formControlName="streetAddress"
                spellcheck="false"
                type="text"
              />
            </sky-input-box>
          </sky-column>
        </sky-row>
        <sky-row>
          <sky-column [screenSmall]="5">
            <sky-input-box labelText="City" stacked="true">
              <input formControlName="city" spellcheck="false" type="text" />
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="5" [screenXSmall]="8">
            <sky-input-box labelText="State" stacked="true">
              <select formControlName="state">
                <option [attr.value]="undefined"></option>
                @for (state of states; track state) {
                  <option value="state">
                    {{ state }}
                  </option>
                }
              </select>
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="2" [screenXSmall]="4">
            <sky-input-box labelText="Zip code">
              <input formControlName="zipCode" maxlength="5" type="text" />
            </sky-input-box>
          </sky-column>
        </sky-row>
      </sky-fluid-grid>
    </sky-field-group>
  </form>
</div>

```

#### Field group with help key

**Selector:** `app-forms-field-group-help-key-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Field group with help key
 */
@Component({
  selector: 'app-forms-field-group-help-key-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyFieldGroupModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
  ],
})
export class FormsFieldGroupHelpKeyExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected states = [
    'AK',
    'AZ',
    'AL',
    'AR',
    'CA',
    'CO',
    'CT',
    'DE',
    'DC',
    'FL',
    'GA',
    'HI',
    'ID',
    'IL',
    'IN',
    'IA',
    'KS',
    'KY',
    'LA',
    'ME',
    'MD',
    'MA',
    'MI',
    'MN',
    'MS',
    'MO',
    'MT',
    'NE',
    'NV',
    'NH',
    'NJ',
    'NM',
    'NY',
    'NC',
    'ND',
    'OH',
    'OK',
    'OR',
    'PA',
    'RI',
    'SC',
    'SD',
    'TN',
    'TX',
    'UT',
    'VT',
    'VA',
    'WA',
    'WV',
    'WI',
    'WY',
  ];

  constructor() {
    this.formGroup = this.#formBuilder.group({
      streetAddress: this.#formBuilder.control(undefined),
      city: this.#formBuilder.control(undefined),
      state: this.#formBuilder.control(undefined),
      zipCode: this.#formBuilder.control(undefined),
    });
  }
}

```

**Template:**

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-field-group
      headingText="Address"
      helpKey="address-help"
      hintText="We use this address for your end-of-year statement."
      [headingStyle]="4"
    >
      <sky-fluid-grid gutterSize="small" [disableMargin]="true">
        <sky-row>
          <sky-column [screenXSmall]="12">
            <sky-input-box labelText="Street address" stacked="true">
              <input
                formControlName="streetAddress"
                spellcheck="false"
                type="text"
              />
            </sky-input-box>
          </sky-column>
        </sky-row>
        <sky-row>
          <sky-column [screenSmall]="5">
            <sky-input-box labelText="City" stacked="true">
              <input formControlName="city" spellcheck="false" type="text" />
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="5" [screenXSmall]="8">
            <sky-input-box labelText="State" stacked="true">
              <select formControlName="state">
                <option [attr.value]="undefined"></option>
                @for (state of states; track state) {
                  <option value="state">
                    {{ state }}
                  </option>
                }
              </select>
            </sky-input-box>
          </sky-column>
          <sky-column [screenSmall]="2" [screenXSmall]="4">
            <sky-input-box labelText="Zip code">
              <input formControlName="zipCode" maxlength="5" type="text" />
            </sky-input-box>
          </sky-column>
        </sky-row>
      </sky-fluid-grid>
    </sky-field-group>
  </form>
</div>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
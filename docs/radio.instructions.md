---
component: 'radio'
description: 'Design guidelines, API documentation, and usage instructions for the radio component extracted from SKY UX documentation.'
---

# Radio Component Guidelines

## Component Overview
Radio buttons let users select one item from a short list of items.

## Usage

### ✅ Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

**✅ Do use radio button groups when users select a single item from a short list of options in a modal.**

Use icon radio button groups when icons clearly communicate the options.

**✅ Do use icon radio button groups when icons clearly illustrate the options.**

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using action buttons instead. See the form layout guidelines for more information.

**✅ Do use radio buttons to enable conditional inputs as part of a task.**

### ❌ Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different selection input instead.

**❌ Don't use radio buttons for a long list of options.**

Don't use radio buttons for two options that are exact opposites. Use a checkbox instead.

**❌ Don't use radio buttons to represent exact opposites.**

Don't use radio buttons when user selections significantly alter the workflow. Use action buttons instead, and place them at the beginning of the task.

**❌ Don't use radio buttons for options that significantly alter the workflow.**

## Anatomy

### Individual radio button

### Radio button group

### Icon radio button group

- Radio button
- Label
- Help inline button
- Hint text

## Options

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use headingLevel to specify a semantic heading level in the document structure and headingStyle to set the heading font style. For example, use a label as a heading to indicate that a radio button group is a form section just like other field groups. Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

**Radio button group labels can be turned into HTML headings.**

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use stacked to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the radio button group:

- Is the last input inside a field group
- Is the last input on a form

If a radio button group uses headingLevel, use stacked when the radio button group is followed by a field group or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

## Content

## Layout

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with headingLevel and headingStyle set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

**❌ Don't use a field group with a lone radio button group.**

## Accessibility

## Related information

### Components

- Action buttons
- Checkbox
- Field group
- Help inline button
- Modal

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsRadioHelpKeyExampleComponent

**Selector:** `app-forms-radio-help-key-example`

**Package:** `@skyux/code-examples`

#### FormsRadioIconExampleComponent

**Selector:** `app-forms-radio-icon-example`

**Package:** `@skyux/code-examples`

#### FormsRadioStandardExampleComponent

**Selector:** `app-forms-radio-standard-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Package:** `@skyux/code-examples`

#### SkyRadioGroupComponent

Organizes radio buttons into a group. It is required for radio
buttons on Angular reactive forms, and we recommend using it with all radio buttons.
On Angular forms, the component manages the selected values and keeps the forms up-to-date.
When users select a radio button, its value is driven through an `ngModel` attribute that you specify on the `sky-radio-group` element.

**Selector:** `sky-radio-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingText`: `string | undefined` - The text to display as the radio group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the radio group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to radio group. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete.
For more information about the `aria-required` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-required). (default: false)
- `ariaLabel`: `string | undefined` - The ARIA label for the radio button group. This sets the
radio button group's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button group includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the radio button group. This sets the radio button group's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button group does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `disabled`: `boolean` - Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `headingLevel`: `SkyRadioGroupHeadingLevel | undefined` - The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.
- `headingStyle`: `SkyRadioGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 4)
- `name`: `string` - The name for the collection of radio buttons that the component groups together.
This property overwrites the deprecated `name` property on individual `sky-radio` elements,
and it is required unless the `name` property is set on individual `sky-radio` elements. **[Required]**
- `stacked`: `boolean` - Whether the radio button group is stacked on another form component. When specified,
the appropriate vertical spacing is automatically added to the radio button group.
- `tabIndex`: `number | undefined` - The index for all the radio buttons in the group. If the index is not defined,
the indices for individual radio buttons are set to their positions on load.
This property supports accessibility by placing focus on the currently selected radio
button. If no radio button is selected, it places focus on the first or last button
depending on how users navigate to the radio button group.
- `value`: `any` - The value of the radio button to select by default when the group loads.
The value corresponds to the `value` property of an individual `sky-radio` element within the
group.

#### SkyRadioLabelComponent

Specifies a label for the radio button. To display a help button beside the label, include a help button element,
such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-radio-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyRadioComponent

Renders a SKY UX-themed replacement for an HTML `input` element
with `type="radio"`. When users select a radio button, its value is driven through an
`ngModel` attribute that you specify on the `sky-radio` element or the parent `sky-radio-group` element.

**Selector:** `sky-radio`

**Package:** `@skyux/forms`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the radio button label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to radio button. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `iconName`: `string | undefined` - The SVG icon to display in place of the radio button. To group radio buttons like in
the demo above, place the `sky-switch-icon-group` class on the direct parent element of the
radio buttons.
- `labelHidden`: `boolean` - Indicates whether to hide the `labelText`. (default: false)
- `labelText`: `string | undefined` - The text to display as the radio button's label. Use this instead of the `sky-radio-label` when the label is text-only.
- `checked`: `boolean` - Whether the radio button is selected. (default: false)
- `disabled`: `boolean` - Whether to disable the input on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `id`: `string | undefined` - The ID for the radio button.
If a value is not provided, an autogenerated ID is used.
- `label`: `string | undefined` - The ARIA label for the radio button. This sets the radio button's `aria-label`
attribute to provide a text equivalent for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
when the radio button does not include a visible label. You must set this property for icon
radio buttons. If the radio button includes a visible label, use `labelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels
the radio button. This sets the radio button's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the radio button does not include a visible label, use `label` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `name`: `string | undefined` - This property is deprecated in favor of the `name` property on the `sky-radio-group element`.
We recommend using the `sky-radio-group` element with all radio buttons, but if you opt not to,
then this property specifies a name for a group of radio buttons.
- `radioType`: `SkyRadioType` - The background color type after users select an icon radio button.
The valid options correspond
[the label component's](https://developer.blackbaud.com/skyux/components/label)
label types. `danger` creates a red background, `info` creates a blue background,
`success` creates a green background, and `warning` creates an orange background. (default: "info")
- `tabindex`: `number` - This property is deprecated in favor of
the `tabIndex` property on the `sky-radio-group` element. It specifies an index for the radio
button. If the index is not defined, it is set to the position of the radio button on load.
- `value`: `any` - The value bound to the radio button's `value` property. The value usually
corresponds to the radio button's label, which you specify with the `sky-radio-label`
component. **[Required]**

**Outputs:**

- `change`: `EventEmitter<SkyRadioChange>` - Fires when users select a radio button.
- `checkedChange`: `EventEmitter<boolean>` - Fires when the selected value changes.
- `disabledChange`: `EventEmitter<boolean>` - Fires when the selected value changes.

#### SkyRadioModule

**Package:** `@skyux/forms`

#### SkyRadioChange

Fires when users select a radio button.

**Package:** `@skyux/forms`

#### SkyRadioGroupHeadingLevel

**Package:** `@skyux/forms`

#### SkyRadioGroupHeadingStyle

**Package:** `@skyux/forms`

#### SkyRadioType

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyRadioFixture

Allows interaction with a SKY UX radio buttons within a radio group.

**Package:** `@skyux/forms/testing`

⚠️ **This component is deprecated.**

#### SkyRadioGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyRadioGroupHarness

Harness for interacting with a radio group component in tests.

**Package:** `@skyux/forms/testing`

#### SkyRadioHarnessFilters

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyRadioHarness

Harness for interacting with a radio button component in tests.

**Package:** `@skyux/forms/testing`

#### SkyRadioLabelHarness

Harness for interacting with a radio label component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Radio group with help key

**Selector:** `app-forms-radio-help-key-example`

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
} from '@angular/forms';
import { SkyRadioModule } from '@skyux/forms';

interface DemoForm {
  paymentMethod: FormControl<string | null>;
}

interface Item {
  name: string;
  value: string;
  disabled?: boolean;
  hintText?: string;
  helpKey?: string;
}

function validatePaymentMethod(
  control: AbstractControl,
): ValidationErrors | null {
  return control.value === 'check' ? { processingIssue: true } : null;
}

/**
 * @title Radio group with help key
 */
@Component({
  selector: 'app-forms-radio-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioHelpKeyExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected hintText = 'Card methods require proof of identification.';
  protected paymentMethod: FormControl<string | null>;

  protected paymentOptions: Item[] = [
    {
      name: 'Cash',
      value: 'cash',
      helpKey: 'cash-help',
    },
    { name: 'Check', value: 'check' },
    { name: 'Apple pay', value: 'apple', disabled: true },
    {
      name: 'Credit',
      value: 'credit',
      hintText: 'A 2% late fee is applied to payments made after the due date.',
    },
    { name: 'Debit', value: 'debit' },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.paymentMethod = this.#formBuilder.control(
      this.paymentOptions[0].name,
      {
        validators: [validatePaymentMethod],
      },
    );

    this.formGroup = this.#formBuilder.group({
      paymentMethod: this.paymentMethod,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    data-sky-id="radio-group"
    formControlName="paymentMethod"
    headingLevel="4"
    headingText="Payment method"
    helpKey="payment-help"
    [hintText]="hintText"
  >
    @for (option of paymentOptions; track option) {
      <sky-radio
        [disabled]="option.disabled"
        [value]="option.value"
        [labelText]="option.name"
        [helpKey]="option.helpKey"
        [hintText]="option.hintText"
      />
    }
    @if (paymentMethod.errors?.['processingIssue']) {
      <sky-form-error
        errorName="processingIssue"
        errorText="An error occurred with this payment method. Please contact us to resolve."
      />
    }
  </sky-radio-group>
</form>

```

#### Radio group with icons

**Selector:** `app-forms-radio-icon-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyRadioModule } from '@skyux/forms';

interface Item {
  iconName: string;
  label: string;
  name: string;
}

/**
 * @title Radio group with icons
 */
@Component({
  selector: 'app-forms-radio-icon-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioIconExampleComponent {
  protected formGroup: FormGroup;

  protected views: Item[] = [
    { iconName: 'table', label: 'Table', name: 'table' },
    { iconName: 'text-number-list-ltr', label: 'List', name: 'list' },
    { iconName: 'location', label: 'Map', name: 'map' },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      myView: this.views[0].name,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    class="sky-switch-icon-group"
    formControlName="myView"
    headingHidden="true"
    headingText="View"
  >
    @for (view of views; track view) {
      <sky-radio
        [labelHidden]="true"
        [iconName]="view.iconName"
        [labelText]="view.label"
        [value]="view.name"
      />
    }
  </sky-radio-group>
</form>

```

#### Radio group with standard setup

**Selector:** `app-forms-radio-standard-example`

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
} from '@angular/forms';
import { SkyRadioModule } from '@skyux/forms';

interface DemoForm {
  paymentMethod: FormControl<string | null>;
}

interface Item {
  name: string;
  value: string;
  disabled?: boolean;
  hintText?: string;
  helpContent?: string;
}

function validatePaymentMethod(
  control: AbstractControl,
): ValidationErrors | null {
  return control.value === 'check' ? { processingIssue: true } : null;
}

/**
 * @title Radio group with standard setup
 */
@Component({
  selector: 'app-forms-radio-standard-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioStandardExampleComponent {
  protected formGroup: FormGroup<DemoForm>;
  protected helpPopoverContent =
    "We don't charge fees for any payment method. The only exception is when credit card payments are late, which incurs a 2% fee.";
  protected helpPopoverTitle = 'Are there fees?';
  protected hintText = 'Card methods require proof of identification.';
  protected paymentMethod: FormControl<string | null>;

  protected paymentOptions: Item[] = [
    {
      name: 'Cash',
      value: 'cash',
      helpContent:
        'We accept cash at any of our locations and affiliated partners.',
    },
    { name: 'Check', value: 'check' },
    { name: 'Apple pay', value: 'apple', disabled: true },
    {
      name: 'Credit',
      value: 'credit',
      hintText: 'A 2% late fee is applied to payments made after the due date.',
    },
    { name: 'Debit', value: 'debit' },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.paymentMethod = this.#formBuilder.control(
      this.paymentOptions[0].name,
      {
        validators: [validatePaymentMethod],
      },
    );

    this.formGroup = this.#formBuilder.group({
      paymentMethod: this.paymentMethod,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    data-sky-id="radio-group"
    formControlName="paymentMethod"
    headingLevel="4"
    headingText="Payment method"
    [helpPopoverContent]="helpPopoverContent"
    [helpPopoverTitle]="helpPopoverTitle"
    [hintText]="hintText"
  >
    @for (option of paymentOptions; track option) {
      <sky-radio
        [disabled]="option.disabled"
        [value]="option.value"
        [labelText]="option.name"
        [helpPopoverContent]="option.helpContent"
        [hintText]="option.hintText"
      />
    }
    @if (paymentMethod.errors?.['processingIssue']) {
      <sky-form-error
        errorName="processingIssue"
        errorText="An error occurred with this payment method. Please contact us to resolve."
      />
    }
  </sky-radio-group>
</form>

```

#### Selection boxes with radio buttons

**Selector:** `app-forms-selection-box-radio-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyRadioModule, SkySelectionBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Selection boxes with radio buttons
 */
@Component({
  selector: 'app-forms-selection-box-radio-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyIdModule,
    SkyRadioModule,
    SkySelectionBoxModule,
  ],
})
export class FormsSelectionBoxRadioExampleComponent {
  protected items: Record<string, string>[] = [
    {
      name: 'Save time and effort',
      iconName: 'clock',
      description:
        'Automate mundane tasks and spend more time on the things that matter.',
      value: 'clock',
    },
    {
      name: 'Boost engagement',
      iconName: 'person',
      description: 'Encourage supporters to interact with your organization.',
      value: 'engagement',
    },
    {
      name: 'Build relationships',
      iconName: 'people-team',
      description:
        'Connect to supporters on a personal level and maintain accurate data.',
      value: 'relationships',
    },
  ];

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      myOption: this.items[2]['value'],
    });
  }
}

```

**Template:**

```html
<form novalidate [formGroup]="formGroup">
  <sky-radio-group ariaLabel="Demo options" formControlName="myOption">
    <sky-selection-box-grid>
      @for (item of items; track item) {
        <sky-selection-box [control]="radio">
          <sky-icon [iconName]="item['iconName']" />
          <sky-selection-box-header #radioHeaderId="skyId" skyId>
            {{ item['name'] }}
          </sky-selection-box-header>
          <sky-selection-box-description>
            {{ item['description'] }}
          </sky-selection-box-description>
          <sky-radio
            #radio
            [labelledBy]="radioHeaderId.id"
            [value]="item['value']"
          />
        </sky-selection-box>
      }
    </sky-selection-box-grid>
  </sky-radio-group>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
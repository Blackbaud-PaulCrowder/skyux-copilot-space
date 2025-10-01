---
component: 'box'
description: 'Design guidelines, API documentation, and usage instructions for the box component extracted from SKY UX documentation.'
---

# Box Component Guidelines

## Component Overview
Boxes provide containers to group related content and actions.

## Usage

### ✅ Use when

Use boxes as containers for related content and actions on pages such action hubs and record pages.

**✅ Do use boxes to organize content on action hubs.**

### ❌ Don't use when

Don't use boxes to separate individual items in a list. Use repeaters or other layout approaches instead.

**❌ Don't use boxes to separate individual items in a list.**

Don't use boxes to organize content in modal forms or split view workspaces. Use headers and spacing instead.

**❌ Don't use boxes to organize content in forms.**

Don't add boxes to pre-defined sections of page layouts. For example, don't add boxes around lists on list pages or around related links on action hubs.

**❌ Don't add boxes to the sections in the top right of action hubs.**

## Anatomy

- Container
- Content
- Heading
- Help inline button
- Control button

## Options

### Heading

In general, boxes should include short headings to describe their contents. However, headings are optional so that consumers can exclude them when boxes contain content that doesn't require headings, such as visualizations or multimedia content.

To match to a page's semantic and visual hierarchy, adjust the box heading's headingLevel and headingStyle properties. In most cases, box headings follow the page heading in the page hierarchy, and these properties should be set to 2.

### Help inline button

When you need to supplement a box with additional information but don't require persistent inline help, you can place a help inline button beside the heading to invoke contextual user assistance.

### Control button

You can include a button in the top right to provide an edit action or a context menu with multiple actions.

**✅ Do include an edit button for editable content.**

Don't include multiple buttons in boxes. Instead, break up content so that boxes only contain related content that users can manage together.

**❌ Don't include multiple buttons.**

## Layout

Use proper spacing between boxes. Depending on your scenario, you can use fluid grid, CSS flexbox, CSS Grid or spacing classes.

**✅ Use proper spacing between boxes.**

## Related information

### Components

- Action hub
- Fluid grid
- Help inline button

### Guidelines

- Action hub page
- Record page
- Spacing

## API Documentation

### Components and Directives

#### FormsCheckboxBasicExampleComponent

**Selector:** `app-forms-checkbox-basic-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxHelpKeyExampleComponent

**Selector:** `app-forms-checkbox-help-key-example`

**Package:** `@skyux/code-examples`

#### FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxBasicExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxCheckboxExampleComponent

**Selector:** `app-forms-selection-box-checkbox-example`

**Package:** `@skyux/code-examples`

#### FormsSelectionBoxRadioExampleComponent

**Selector:** `app-forms-selection-box-radio-example`

**Package:** `@skyux/code-examples`

#### LayoutBoxBasicExampleComponent

**Selector:** `app-layout-box-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutBoxHelpKeyExampleComponent

**Selector:** `app-layout-box-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyBoxContentComponent

Specifies the body content to display inside the box and provides padding around that content.

**Selector:** `sky-box-content`

**Package:** `@skyux/layout`

#### SkyBoxControlsComponent

Specifies the controls to display in upper right corner of the box. These buttons typically let users edit the box content.

**Selector:** `sky-box-controls`

**Package:** `@skyux/layout`

#### SkyBoxHeaderComponent

Specifies a header for the box.

**Selector:** `sky-box-header`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyBoxHeadingLevel

**Package:** `@skyux/layout`

#### SkyBoxHeadingStyle

**Package:** `@skyux/layout`

#### SkyBoxComponent

Provides a common look-and-feel for box content with options to display a common box header, specify body content, and display common box controls.

**Selector:** `sky-box`

**Package:** `@skyux/layout`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the box. This sets the box's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the box includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the box. This sets the box's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the box does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `ariaRole`: `string | undefined` - The ARIA role for the box
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating what the box contains. For information about
how an ARIA role indicates what an item represents on a web page,
see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).
- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingLevel`: `SkyBoxHeadingLevel` - The semantic heading level in the document structure. The default is 2. (default: 2)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the box heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the box heading. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `headingStyle`: `SkyBoxHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 2)
- `headingText`: `string | undefined` - The text to display as the box's heading.

#### SkyBoxModule

**Package:** `@skyux/layout`

#### SkyBoxHarnessFilters

A set of criteria that can be used to filter a list of `SkyBoxHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyBoxHarness

Harness for interacting with a box component in tests.

**Package:** `@skyux/layout/testing`

#### SkyCheckboxChange

Fires when users select or deselect the checkbox.

**Package:** `@skyux/forms`

#### SkyCheckboxGroupHeadingLevel

**Package:** `@skyux/forms`

#### SkyCheckboxGroupHeadingStyle

**Package:** `@skyux/forms`

#### SkyCheckboxGroupComponent

Organizes checkboxes into a group.

**Selector:** `sky-checkbox-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingText`: `string` - The text to display as the checkbox group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox group fieldset legend. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `required`: `boolean` - Whether the checkbox group is required. (default: false)
- `headingLevel`: `SkyCheckboxGroupHeadingLevel | undefined` - The semantic heading level in the document structure. By default, the heading text is not wrapped in a heading element.
- `headingStyle`: `SkyCheckboxGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 4)
- `stacked`: `boolean` - Whether the checkbox group is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox group.

#### SkyCheckboxLabelComponent

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-checkbox-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyCheckboxComponent

Replaces the HTML input element with `type="checkbox"`. When users select a checkbox, its value
is driven through an `ngModel` attribute that you specify on the `sky-checkbox` element.

**Selector:** `sky-checkbox`

**Package:** `@skyux/forms`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the checkbox label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the checkbox label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `iconName`: `string | undefined` - The SVG icon to display in place of the checkbox. To group icon checkboxes
like in the demo, place the checkboxes within a `sky-checkbox-group`.
- `labelHidden`: `boolean` - Indicates whether to hide the `labelText`. (default: false)
- `labelText`: `string | undefined` - The text to display as the checkbox's label. Use this instead of the `sky-checkbox-label` when the label is text-only.
Specifying `labelText` also enables automatic error message handling for checkbox.
- `required`: `boolean` - Whether the input is required for form validation.
When you set this property to `true`, the component adds `aria-required` and `required`
attributes to the input element so that forms display an invalid state until the input element
is complete. (default: false)
- `stacked`: `boolean` - Whether the checkbox is stacked on another form component. When specified, the appropriate
vertical spacing is automatically added to the checkbox. If the checkbox is within a checkbox group,
set `stacked` on the checkbox group component instead. (default: false)
- `tabindex`: `number | undefined` - The index for the checkbox. If not defined, the index is set to the position of the
checkbox on load. (default: 0)
- `checkboxType`: `string` - The background color type after users select a checkbox where the
`icon` property displays an icon in place of the checkbox. The valid options correspond to
[the label component's](https://developer.blackbaud.com/skyux/components/label)
label types. `"info"` creates a blue background, `"success"` creates a green
background, `"warning"` creates an orange background, and `"danger"` creates a red background. (default: "info")
- `checked`: `boolean` - Whether the checkbox is selected.
- `disabled`: `boolean` - Whether the checkbox is disabled.
- `id`: `string | undefined` - The ID for the checkbox.
If a value is not provided, an autogenerated ID is used.
- `indeterminate`: `boolean` - Whether the checkbox is in the indeterminate state. This has no visual effect for icon checkboxes.
- `label`: `string | undefined` - The ARIA label for the checkbox. This sets the checkbox's `aria-label` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility)
when the checkbox does not include a visible label. You must set this property for icon
checkboxes. If the checkbox includes a visible label, use `labelledBy` instead.
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels the
checkbox. This sets the checkbox's `aria-labelledby` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
If the checkbox does not include a visible label, use `label` instead.
- `name`: `string` - The name for the checkbox.
If a value is not provided, an autogenerated ID is used.

**Outputs:**

- `change`: `EventEmitter<SkyCheckboxChange>` - Fires when the selected value changes.
- `checkedChange`: `Observable<boolean>` - Fires when users select or deselect the checkbox.
- `disabledChange`: `Observable<boolean>` - Fires when the selected value changes.
- `indeterminateChange`: `Observable<boolean>` - Fires when the indeterminate state changes.

#### SkyCheckboxModule

**Package:** `@skyux/forms`

#### SkyInputBoxControlDirective

**Selector:** `input:not([skyId]):not(.sky-form-control),select:not([skyId]):not(.sky-form-control),textarea:not([skyId]):not(.sky-form-control)`

**Package:** `@skyux/forms`

**Inputs:**

- `autocomplete`: `string | undefined`

#### SkyInputBoxHintTextPipe

**Package:** `@skyux/forms`

#### SkyInputBoxHostService

**Package:** `@skyux/forms`

#### SkyInputBoxPopulateArgs

**Package:** `@skyux/forms`

#### SkyInputBoxComponent

A wrapper component that provides styling and accessibility to form elements.

**Selector:** `sky-input-box`

**Package:** `@skyux/forms`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to visually highlight the input box as disabled. To disable the input box's
input element, use the HTML `disabled` attribute or the Angular `FormControl.disabled`
property. If the input element is mapped to an Angular form control
(e.g. `formControlName`, `ngModel`, etc.), "disabled" styles are applied automatically;
if the input element is not associated with an Angular form control, the `disabled`
property on the input box must be set to `true` to visually indicate
the disabled state on the input box. (default: false)
- `hasErrors`: `boolean | undefined` - Whether to visually highlight the input box in an error state. If not specified, the input box
displays in an error state when either the `ngModel` or the Angular `FormControl` contains an error. (default: undefined)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the input box label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the input box label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `labelText`: `string | undefined` - The text to display as the input's label and in known validation error messages. The label
will automatically be associated with the `input`, `select`, `textarea`, or compatible SKY UX
component included in the input box.
- `characterLimit`: `number | undefined` - The maximum number of characters allowed in the input. A [SKY UX character count](https://developer.blackbaud.com/skyux/components/character-count)
will be placed on the input element with the appropriate validator.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `BooleanInput` - Whether the input box is stacked on another input box. When specified, the appropriate
vertical spacing is automatically added to the input box.

#### SkyInputBoxModule

**Package:** `@skyux/forms`

#### SkySelectionBoxDescriptionComponent

Specifies the description to display in a selection box.

**Selector:** `sky-selection-box-description`

**Package:** `@skyux/forms`

#### SkySelectionBoxGridComponent

Creates a grid layout for an array of selection boxes.

**Selector:** `sky-selection-box-grid`

**Package:** `@skyux/forms`

**Inputs:**

- `alignItems`: `SkySelectionBoxGridAlignItemsType` - How to display the selection boxes in the grid. (default: 'center')

#### SkySelectionBoxHeaderComponent

Specifies the header to display in a selection box.

**Selector:** `sky-selection-box-header`

**Package:** `@skyux/forms`

#### SkySelectionBoxComponent

Creates a button to present users with a choice or question before proceeding with a one-time process.

**Selector:** `sky-selection-box`

**Package:** `@skyux/forms`

**Inputs:**

- `control`: `SkyCheckboxComponent | SkyRadioComponent | undefined` - The radio button or checkbox to display in the selection box. **[Required]**

#### SkySelectionBoxModule

**Package:** `@skyux/forms`

#### SkySelectionBoxGridAlignItemsType

**Package:** `@skyux/forms`

#### SkySelectionBoxGridAlignItems

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyCheckboxFixture

Allows interaction with a SKY UX checkbox component.

**Package:** `@skyux/forms/testing`

⚠️ **This component is deprecated.**

#### SkyCheckboxGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxGroupHarness

Harness for interacting with a checkbox group component in tests.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxHarness

Harness for interacting with a checkbox component in tests.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxLabelHarness

Harness for interacting with a checkbox label component in tests.

**Package:** `@skyux/forms/testing`

#### SkyInputBoxHarnessFilters

A set of criteria that can be used to filter a list of SkyInputBoxHarness instances.

**Package:** `@skyux/forms/testing`

#### SkyInputBoxHarness

Harness for interacting with an input box component in tests.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxGridHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxGridHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxGridHarness

Harness for interacting with a selection box grid component in tests.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxHarness

Harness to interact with a selection box component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Standard checkboxes

**Selector:** `app-forms-checkbox-basic-example`

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
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Standard checkboxes
 */
@Component({
  selector: 'app-forms-checkbox-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxBasicExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected contactMethod: FormGroup;

  constructor() {
    this.contactMethod = this.#formBuilder.group({
      email: new FormControl(false),
      phone: new FormControl(false),
      text: new FormControl(false),
    });

    this.formGroup = this.#formBuilder.group({
      contactMethod: this.contactMethod,
      terms: new FormControl(false),
    });

    this.contactMethod.setValidators(
      (control: AbstractControl): ValidationErrors | null => {
        const group = control as FormGroup;
        const email = group.controls['email'];
        const phone = group.controls['phone'];
        const text = group.controls['text'];

        if (email.value && !phone.value && !text.value) {
          return { emailOnly: true };
        } else {
          return null;
        }
      },
    );
  }

  protected onSubmit(): void {
    this.formGroup.markAllAsTouched();

    console.log(this.formGroup.value);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    data-sky-id="checkbox-group"
    headingText="Contact method"
    headingStyle="5"
    helpPopoverContent="We use your contact info to keep you informed on current events. We will not sell your information."
    hintText="Please select at least one phone-based method."
    [formGroup]="contactMethod"
    [required]="true"
    [stacked]="true"
  >
    <sky-checkbox formControlName="email" labelText="Email" />
    <sky-checkbox formControlName="phone" labelText="Phone" />
    <sky-checkbox formControlName="text" labelText="Text" />
    @if (contactMethod.errors?.['emailOnly']) {
      <sky-form-error
        errorName="emailOnly"
        errorText="Email cannot be the only contact method."
      />
    }
  </sky-checkbox-group>
  <sky-checkbox
    data-sky-id="single-checkbox"
    formControlName="terms"
    labelText="I agree to the terms and conditions"
    [required]="true"
    [stacked]="true"
  />
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Checkboxes with help key

**Selector:** `app-forms-checkbox-help-key-example`

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
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Checkboxes with help key
 */
@Component({
  selector: 'app-forms-checkbox-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxHelpKeyExampleComponent {
  #formBuilder: FormBuilder = inject(FormBuilder);

  protected formGroup: FormGroup;
  protected contactMethod: FormGroup;

  constructor() {
    this.contactMethod = this.#formBuilder.group({
      email: new FormControl(false),
      phone: new FormControl(false),
      text: new FormControl(false),
    });

    this.formGroup = this.#formBuilder.group({
      contactMethod: this.contactMethod,
      terms: new FormControl(false),
    });

    this.contactMethod.setValidators(
      (control: AbstractControl): ValidationErrors | null => {
        const group = control as FormGroup;
        const email = group.controls['email'];
        const phone = group.controls['phone'];
        const text = group.controls['text'];

        if (email.value && !phone.value && !text.value) {
          return { emailOnly: true };
        } else {
          return null;
        }
      },
    );
  }

  protected onSubmit(): void {
    this.formGroup.markAllAsTouched();

    console.log(this.formGroup.value);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    data-sky-id="checkbox-group"
    headingText="Contact method"
    headingStyle="5"
    helpKey="contact-help"
    hintText="Please select at least one phone-based method."
    [formGroup]="contactMethod"
    [required]="true"
    [stacked]="true"
  >
    <sky-checkbox formControlName="email" labelText="Email" />
    <sky-checkbox formControlName="phone" labelText="Phone" />
    <sky-checkbox formControlName="text" labelText="Text" />
    @if (contactMethod.errors?.['emailOnly']) {
      <sky-form-error
        errorName="emailOnly"
        errorText="Email cannot be the only contact method."
      />
    }
  </sky-checkbox-group>
  <sky-checkbox
    data-sky-id="single-checkbox"
    formControlName="terms"
    helpKey="terms-help"
    labelText="I agree to the terms and conditions"
    [required]="true"
    [stacked]="true"
  />
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Icon checkbox group

**Selector:** `app-forms-checkbox-icon-group-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Icon checkbox group
 */
@Component({
  selector: 'app-forms-checkbox-icon-group-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxIconGroupExampleComponent {
  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      bold: new FormControl(false),
      italic: new FormControl(false),
      underline: new FormControl(false),
    });
  }

  public onSubmit(): void {
    console.log(this.formGroup.value);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    headingText="Text formatting"
    [formGroup]="formGroup"
    [headingHidden]="true"
    [stacked]="true"
  >
    <sky-checkbox
      formControlName="bold"
      iconName="text-bold"
      labelHidden="true"
      labelText="Bold"
    />
    <sky-checkbox
      formControlName="italic"
      iconName="text-italic"
      labelHidden="true"
      labelText="Italic"
    />
    <sky-checkbox
      formControlName="underline"
      iconName="text-underline"
      labelHidden="true"
      labelText="Underline"
    />
  </sky-checkbox-group>
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Input box

**Selector:** `app-forms-input-box-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyDatepickerModule } from '@skyux/datetime';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkyValidators } from '@skyux/validation';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDatepickerModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
    SkyStatusIndicatorModule,
  ],
})
export class FormsInputBoxBasicExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    firstName: new FormControl(''),
    lastName: new FormControl('', Validators.required),
    bio: new FormControl(''),
    email: new FormControl('', [Validators.required, SkyValidators.email]),
    dob: new FormControl('', Validators.required),
    favoriteColor: this.favoriteColor,
  });
}

```

**Template:**

```html
<div class="sky-padding-even-lg">
  <form [formGroup]="formGroup">
    <sky-fluid-grid gutterSize="small" [disableMargin]="false">
      <sky-row>
        <sky-column [screenSmall]="12">
          <h2>New member form</h2>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-first-name"
            helpKey="first-name-help"
            labelText="First name"
            stacked="true"
          >
            <input formControlName="firstName" spellcheck="false" type="text" />
          </sky-input-box>
        </sky-column>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-last-name"
            labelText="Last name"
            stacked="true"
          >
            <input
              class="last-name-input-box"
              formControlName="lastName"
              spellcheck="false"
              type="text"
            />
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12">
          <sky-input-box
            characterLimit="250"
            data-sky-id="input-box-bio"
            hintText="A brief description of the member's background, such as hometown, school, hobbies, etc."
            labelText="Bio"
            stacked="true"
          >
            <textarea formControlName="bio"></textarea>
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box
            data-sky-id="input-box-email"
            labelText="Email address"
            stacked="true"
            helpPopoverContent="We do not share this information with any third parties."
            helpPopoverTitle="Privacy notice"
          >
            <input formControlName="email" type="text" />
          </sky-input-box>
        </sky-column>
        <sky-column [screenSmall]="12" [screenMedium]="6">
          <sky-input-box labelText="Date of birth" stacked="true">
            <sky-datepicker>
              <input formControlName="dob" skyDatepickerInput />
            </sky-datepicker>
          </sky-input-box>
        </sky-column>
      </sky-row>
      <sky-row>
        <sky-column [screenSmall]="12">
          <sky-input-box
            data-sky-id="input-box-favorite-color"
            labelText="Favorite color"
          >
            <select
              class="input-box-favorite-color-select"
              formControlName="favoriteColor"
            >
              <option value="none">None</option>
              <option value="red">Red</option>
              <option value="orange">Orange</option>
              <option value="yellow">Yellow</option>
              <option value="green">Green</option>
              <option value="blue">Blue</option>
              <option value="purple">Purple</option>
              <option value="invalid">Invalid Color</option>
            </select>
            <!-- Custom form error not handled by input box. -->
            @if (favoriteColor.errors?.['invalid']) {
              <sky-form-error
                errorName="invalid"
                errorText="Invalid Color is not a color"
              />
            }
          </sky-input-box>
        </sky-column>
      </sky-row>
    </sky-fluid-grid>
  </form>
</div>

```

#### Input box with custom errors

**Selector:** `app-forms-input-box-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';

function validateColor(control: AbstractControl): ValidationErrors | null {
  if (control.value === 'invalid') {
    return { invalid: true };
  }

  return null;
}

/**
 * @title Input box with custom errors
 */
@Component({
  selector: 'app-forms-input-box-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyInputBoxModule],
})
export class FormsInputBoxWithCustomFormErrorsExampleComponent {
  protected favoriteColor = new FormControl('none', {
    validators: [validateColor],
  });

  protected formGroup = inject(FormBuilder).group({
    favoriteColor: this.favoriteColor,
  });
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-input-box
    data-sky-id="input-box-favorite-color"
    labelText="Favorite color"
  >
    <select formControlName="favoriteColor">
      <option value="none">None</option>
      <option value="red">Red</option>
      <option value="orange">Orange</option>
      <option value="yellow">Yellow</option>
      <option value="green">Green</option>
      <option value="blue">Blue</option>
      <option value="purple">Purple</option>
      <option value="invalid">Invalid Color</option>
    </select>
    @if (favoriteColor.errors?.['invalid']) {
      <sky-form-error
        errorName="invalid"
        errorText="The color Invalid Color is not a color"
      />
    }
  </sky-input-box>
</form>

```

#### Selection boxes with checkboxes

**Selector:** `app-forms-selection-box-checkbox-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormArray,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCheckboxModule, SkySelectionBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Selection boxes with checkboxes
 */
@Component({
  selector: 'app-forms-selection-box-checkbox-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyIconModule,
    SkyIdModule,
    SkySelectionBoxModule,
  ],
})
export class FormsSelectionBoxCheckboxExampleComponent {
  protected checkboxControls: FormControl[] | undefined;

  protected selectionBoxes: {
    description: string;
    iconName: string;
    name: string;
    selected?: boolean;
  }[] = [
    {
      name: 'Save time and effort',
      iconName: 'clock',
      description:
        'Automate mundane tasks and spend more time on the things that matter.',
    },
    {
      name: 'Boost engagement',
      iconName: 'person',
      description: 'Encourage supporters to interact with your organization.',
    },
    {
      name: 'Build relationships',
      iconName: 'people-team',
      description:
        'Connect to supporters on a personal level and maintain accurate data.',
    },
  ];

  protected formGroup: FormGroup;

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    const checkboxArray = this.#buildCheckboxes();
    this.checkboxControls = checkboxArray.controls as FormControl[];

    this.formGroup = this.#formBuilder.group({
      checkboxes: checkboxArray,
    });
  }

  #buildCheckboxes(): FormArray {
    const checkboxArray = this.selectionBoxes.map((checkbox) =>
      this.#formBuilder.control(checkbox.selected),
    );

    return this.#formBuilder.array(checkboxArray);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-selection-box-grid>
    @for (control of checkboxControls; track control; let i = $index) {
      <sky-selection-box [control]="checkbox">
        <sky-icon [iconName]="selectionBoxes[i].iconName" />
        <sky-selection-box-header #checkboxHeaderId="skyId" skyId>
          {{ selectionBoxes[i].name }}
        </sky-selection-box-header>
        <sky-selection-box-description>
          {{ selectionBoxes[i].description }}
        </sky-selection-box-description>
        <sky-checkbox
          #checkbox
          [formControl]="control"
          [labelledBy]="checkboxHeaderId.id"
        />
      </sky-selection-box>
    }
  </sky-selection-box-grid>
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

#### Box with header, content, and controls

**Selector:** `app-layout-box-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyBoxModule } from '@skyux/layout';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Box with header, content, and controls
 */
@Component({
  selector: 'app-layout-box-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyBoxModule, SkyDropdownModule],
})
export class LayoutBoxBasicExampleComponent {}

```

**Template:**

```html
<sky-box
  data-sky-id="box-example"
  headingText="Box header"
  helpPopoverContent="Example help content for box"
>
  <sky-box-controls>
    <sky-dropdown buttonType="context-menu" label="Box example context menu">
      <sky-dropdown-menu>
        <sky-dropdown-item>
          <button type="button">Action 1</button>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <button type="button">Action 2</button>
        </sky-dropdown-item>
      </sky-dropdown-menu>
    </sky-dropdown>
  </sky-box-controls>
  <sky-box-content>
    <p>Box content</p>
  </sky-box-content>
</sky-box>

```

#### Box with help key

**Selector:** `app-layout-box-help-key-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyBoxModule } from '@skyux/layout';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Box with help key
 */
@Component({
  selector: 'app-layout-box-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyBoxModule, SkyDropdownModule],
})
export class LayoutBoxHelpKeyExampleComponent {}

```

**Template:**

```html
<sky-box data-sky-id="box-example" headingText="Box header" helpKey="box-help">
  <sky-box-controls>
    <sky-dropdown buttonType="context-menu" label="Box example context menu">
      <sky-dropdown-menu>
        <sky-dropdown-item>
          <button type="button">Action 1</button>
        </sky-dropdown-item>
        <sky-dropdown-item>
          <button type="button">Action 2</button>
        </sky-dropdown-item>
      </sky-dropdown-menu>
    </sky-dropdown>
  </sky-box-controls>
  <sky-box-content>
    <p>Box content</p>
  </sky-box-content>
</sky-box>

```

#### Record page with blocks layout using box components

**Selector:** `app-pages-page-record-page-blocks-layout-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with blocks layout using box components
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [RecordPageContentComponent, SkyPageModule],
})
export class PagesPageRecordPageBlocksLayoutExampleComponent {
  protected readonly recentLinks = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

**Template:**

```html
<sky-page layout="blocks" helpKey="example-help">
  <sky-page-header
    pageTitle="$500 pledge"
    [parentLink]="{
      label: 'Pledges',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  />
  <sky-page-content>
    <app-record-page-content />
  </sky-page-content>
  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Related links">
      <sky-link-list-item>
        <a href="#">Analysis</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Tools</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <button type="button" class="sky-btn-link-inline">Settings</button>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
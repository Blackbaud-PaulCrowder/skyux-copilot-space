---
component: 'colorpicker'
description: 'Design guidelines, API documentation, and usage instructions for the colorpicker component extracted from SKY UX documentation.'
---

# Colorpicker Component Guidelines

## Component Overview
Colorpickers let users select a color using a variety of input methods.

## Usage

### ✅ Use when

Use colorpickers when users needs to visually select color values or specify specific hexadecimal or RGBa color values.

## Anatomy

### Colorpicker button

### Colorpicker dropdown

- Label
- Colorpicker button
- Required field marker
- Help inline button
- Reset button
- Hint text

## Options

### Required field marker

When a colorpicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a colorpicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Reset button

To allow users to clear their color selection and revert to the default value, include the reset button.

### Hint text

To highlight important considerations about a colorpicker, use hint text. This persistent inline help can explain details such as:

- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Transparency slider

To allow users to set a transparency level or alpha channel level, include the transparency slider.

### Preset color swatches

To present users with up to 12 colors to select directly, use preset color swatches.

### Stacked margin

For consistent vertical spacing when a colorpicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file attachment from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the colorpicker:

- Is the last input before a field group
- Is the last input on a form

## Related information

### Components

- Field group
- Help inline button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ColorpickerBasicExampleComponent

**Selector:** `app-colorpicker-basic-example`

**Package:** `@skyux/code-examples`

#### ColorpickerHelpKeyExampleComponent

**Selector:** `app-colorpicker-help-key-example`

**Package:** `@skyux/code-examples`

#### ColorpickerProgrammaticExampleComponent

**Selector:** `app-colorpicker-programmatic-example`

**Package:** `@skyux/code-examples`

#### SkyColorpickerInputDirective

Creates the colorpicker element and dropdown.

**Selector:** `[skyColorpickerInput]`

**Package:** `@skyux/colorpicker`

**Inputs:**

- `allowTransparency`: `boolean` - Whether to display a transparency slider for users to select transparency
levels. (default: true)
- `alphaChannel`: `string` - The type of transparency in the transparency slider. (default: "hex6")
- `outputFormat`: `string` - The format for the color when the colorpicker uses a native input
element such as a standard text input or a button. This property accepts `rgba`, `hex`,
or `hsla`, but we do not recommend using it because users never see or use its value.
Instead, if you need to access this format value, see the demo for an example. (default: "rgba")
- `presetColors`: `string[]` - The array of colors to load as preset choices. The colorpicker displays the
colors in a series of 12 boxes for users to select.
- `returnFormat`: `string` - This property is deprecated and does not affect the colorpicker.
We recommend against using it. (default: "rgba")
- `skyColorpickerInput`: `SkyColorpickerComponent` - Creates the colorpicker element and dropdown. Place this attribute on an `input` element
or `button` element, wrap the element in a `sky-colorpicker` component, and set the attribute
to the instance of the `sky-colorpicker` component. **[Required]**
- `id`: `string | undefined` - The ID should only be settable when `labelText` is undefined.
When `labelText` is set, the ID is defined by `SkyColorpickerComponent`.
- `initialColor`: `string` - The initial color to load in the colorpicker. Use a reactive or
template-driven form to set this value. This property is deprecated. As an alternative,
we recommend the `formControlName` property on reactive forms or `ngModel` on
template-driven forms. See the demo for examples.

#### SkyColorpickerComponent

The SKY UX-themed replacement for the HTML `input` element with `type="color"`.
The value that users select is driven through the `ngModel` attribute specified on
the `input` element.

**Selector:** `sky-colorpicker`

**Package:** `@skyux/colorpicker`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the colorpicker label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the colorpicker label. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `label`: `string | undefined` - The ARIA label for the colorpicker. This sets the colorpicker's `aria-label` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility)
when the colorpicker does not include a visible label. If the colorpicker includes a visible label, use `labelledBy` instead. (default: "Select color value")
- `labelHidden`: `boolean` - Whether to hide `labelText` from view. (default: false)
- `labelledBy`: `string | undefined` - The HTML element ID of the element that labels the
colorpicker. This sets the colorpicker's `aria-labelledby` attribute
[to support accessibility](https://developer.blackbaud.com/skyux/components/checkbox#accessibility).
If the colorpicker does not include a visible label, use `label` instead.
- `messageStream`: `Subject<SkyColorpickerMessage>` - The observable to send commands to the colorpicker. The commands should
respect the `SkyColorpickerMessage` type.
- `pickerButtonIcon`: `string | undefined` - The name of the icon to overlay on top of the picker.
- `showResetButton`: `boolean` - Whether to display a reset button to let users return to the default color. (default: true)
- `stacked`: `boolean` - Whether the colorpicker is stacked on another form component. When specified,
the appropriate vertical spacing is automatically added to the text editor. (default: false)
- `labelText`: `string | undefined` - The text to display as the colorpicker's label. Use this instead of a `label` element when the label is text-only.
Specifying `labelText` also enables automatic error message handling for standard colorpicker errors.

**Outputs:**

- `selectedColorApplied`: `EventEmitter<SkyColorpickerResult>` - Fires when users select **Apply** in the colorpicker to apply a color.
- `selectedColorChanged`: `EventEmitter<SkyColorpickerOutput>` - Fires when users select a color in the colorpicker.

#### SkyColorpickerModule

**Package:** `@skyux/colorpicker`

#### SkyColorpickerChangeAxis

**Package:** `@skyux/colorpicker`

#### SkyColorpickerCmyk

Colors specified as a combination of cyan, magenta, yellow, and black.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerChangeColor

**Package:** `@skyux/colorpicker`

#### SkyColorpickerHsla

Colors specified as a combination of hue, saturation, and lightness with an alpha
channel to set the opacity.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerHsva

Colors specified as a combination of hue, saturation, and value with an alpha
channel to set the opacity.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerMessageType

The commands to provide the colorpicker.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerMessage

Provides commands for the colorpicker through a message stream.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerOutput

Describes the color that users select in the colorpicker.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerResult

Indicates the color that users apply when they select Apply in the colorpicker.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerRgba

Colors specified as a combination of red, green, and blue with an alpha
channel to set the opacity.

**Package:** `@skyux/colorpicker`

#### SkyColorpickerFixture

Allows interaction with a SKY UX colorpicker component.

**Package:** `@skyux/colorpicker/testing`

⚠️ **This component is deprecated.**

#### SkyColorpickerDropdownHarnessFilters

A set of criteria that can be used to filter a list of `SkyColorpickerDropdownHarness` instances.

**Package:** `@skyux/colorpicker/testing`

#### SkyColorpickerDropdownHarness

Harness for interacting with colorpicker dropdown in tests.

**Package:** `@skyux/colorpicker/testing`

#### SkyColorpickerHarnessFilters

A set of criteria that can be used to filter a list of `SkyColorpickerHarness` instances.

**Package:** `@skyux/colorpicker/testing`

#### SkyColorpickerHarness

Harness for interacting with colorpicker components in tests.

**Package:** `@skyux/colorpicker/testing`

### Code Examples

#### Basic example

**Selector:** `app-colorpicker-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyColorpickerModule, SkyColorpickerOutput } from '@skyux/colorpicker';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Basic example
 */
@Component({
  selector: 'app-colorpicker-basic-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerBasicExampleComponent {
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;

  protected swatches: string[] = [
    '#BD4040',
    '#617FC2',
    '#60AC68',
    '#3486BA',
    '#E87134',
    '#DA9C9C',
  ];

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected onSelectedColorChanged(args: SkyColorpickerOutput): void {
    console.log('Reactive form color changed:', args);
  }

  protected submit(): void {
    const controlValue = this.favoriteColor.value;
    const favoriteColor = isColorpickerOutput(controlValue)
      ? controlValue.hex
      : controlValue;

    alert('Your favorite color is: \n' + favoriteColor);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="submit()">
  <sky-colorpicker
    #colorPicker
    data-sky-id="favorite-color"
    labelText="What is your favorite color?"
    hintText="Pick a color with at least 80% opacity."
    [stacked]="true"
    (selectedColorChanged)="onSelectedColorChanged($event)"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [presetColors]="swatches"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>

  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Colorpicker with help key

**Selector:** `app-colorpicker-help-key-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyColorpickerModule, SkyColorpickerOutput } from '@skyux/colorpicker';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Colorpicker with help key
 */
@Component({
  selector: 'app-colorpicker-help-key-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerHelpKeyExampleComponent {
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;

  protected swatches: string[] = [
    '#BD4040',
    '#617FC2',
    '#60AC68',
    '#3486BA',
    '#E87134',
    '#DA9C9C',
  ];

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected onSelectedColorChanged(args: SkyColorpickerOutput): void {
    console.log('Reactive form color changed:', args);
  }

  protected submit(): void {
    const controlValue = this.favoriteColor.value;
    const favoriteColor = isColorpickerOutput(controlValue)
      ? controlValue.hex
      : controlValue;

    alert('Your favorite color is: \n' + favoriteColor);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="submit()">
  <sky-colorpicker
    #colorPicker
    data-sky-id="favorite-color"
    labelText="What is your favorite color?"
    helpKey="color-help"
    hintText="Pick a color with at least 80% opacity."
    [stacked]="true"
    (selectedColorChanged)="onSelectedColorChanged($event)"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [presetColors]="swatches"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>

  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Interact with a colorpicker programmatically

**Selector:** `app-colorpicker-programmatic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import {
  SkyColorpickerMessage,
  SkyColorpickerMessageType,
  SkyColorpickerModule,
  SkyColorpickerOutput,
} from '@skyux/colorpicker';

import { Subject } from 'rxjs';

interface DemoForm {
  favoriteColor: FormControl<SkyColorpickerOutput | string>;
}

function isColorpickerOutput(value: unknown): value is SkyColorpickerOutput {
  return !!(value && typeof value === 'object' && 'rgba' in value);
}

/**
 * @title Interact with a colorpicker programmatically
 */
@Component({
  selector: 'app-colorpicker-programmatic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyColorpickerModule],
})
export class ColorpickerProgrammaticExampleComponent {
  protected colorpickerController = new Subject<SkyColorpickerMessage>();
  protected favoriteColor: FormControl<SkyColorpickerOutput | string>;
  protected formGroup: FormGroup<DemoForm>;
  protected showResetButton = false;

  constructor() {
    this.favoriteColor = new FormControl('#f00', {
      nonNullable: true,
      validators: [
        (control): ValidationErrors | null => {
          return isColorpickerOutput(control.value) &&
            control.value.rgba.alpha < 0.8
            ? { opaque: true }
            : null;
        },
      ],
    });

    this.formGroup = inject(FormBuilder).group<DemoForm>({
      favoriteColor: this.favoriteColor,
    });
  }

  protected openColorpicker(): void {
    this.#sendMessage(SkyColorpickerMessageType.Open);
  }

  protected resetColorpicker(): void {
    this.#sendMessage(SkyColorpickerMessageType.Reset);
  }

  protected toggleResetButton(): void {
    this.#sendMessage(SkyColorpickerMessageType.ToggleResetButton);
  }

  #sendMessage(type: SkyColorpickerMessageType): void {
    this.colorpickerController.next({ type });
  }
}

```

**Template:**

```html
<form class="sky-margin-stacked-xxl" [formGroup]="formGroup">
  <sky-colorpicker
    #colorPicker
    labelText="What is your favorite color?"
    hintText="Pick a color with at least 80% opacity."
    [messageStream]="colorpickerController"
    [showResetButton]="showResetButton"
    [stacked]="true"
  >
    <input
      formControlName="favoriteColor"
      type="text"
      [skyColorpickerInput]="colorPicker"
    />
    @if (favoriteColor.errors?.['opaque']) {
      <sky-form-error
        errorName="opaque"
        errorText="Color must have at least 80% opacity."
      />
    }
  </sky-colorpicker>
</form>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openColorpicker()"
>
  Open colorpicker
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="resetColorpicker()"
>
  Reset colorpicker
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="toggleResetButton()"
>
  Toggle reset button
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
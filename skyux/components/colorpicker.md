                   

 Colorpicker
===========

Colorpickers let users select a color using a variety of input methods.

 Usage
------

### Use when

Use colorpickers when users needs to visually select color values or specify specific hexadecimal or RGBa color values.

 Anatomy
--------

### Colorpicker button

1

Label

2

Colorpicker button

3

Required field marker (optional)

4

Help inline button (optional)

5

Reset button  (optional)

6

Hint text  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/colorpicker/color-input-anatomy.b51be343614fc86c32f0700f13e4d3b5.png)

### Colorpicker dropdown

1

Colorpicker canvas

2

Selected color swatch

3

Color slider

4

Hexadecimal input

5

RGBa inputs

6

Action buttons

7

Transparency slider (optional)

8

Preset color swatches (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/colorpicker/colorpicker-anatomy.ff9efcfe8608368b870cabbd21e66ac8.png)

 Options
--------

### Required field marker

When a colorpicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a colorpicker label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Reset button

To allow users to clear their color selection and revert to the default value, include the reset button.

### Hint text

To highlight important considerations about a colorpicker, use hint text. This persistent inline help can explain details such as:

*   Consequences of a choice that may not be apparent
*   Additional instructions or context, such as how data is used

### Transparency slider

To allow users to set a transparency level or alpha channel level, include the transparency slider.

### Preset color swatches

To present users with up to 12 colors to select directly, use preset color swatches.

### Stacked margin

For consistent vertical spacing when a colorpicker is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the file attachment from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the colorpicker:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/colorpicker/options-stacked.4dd5a37ce8069a633f188c959462ef07.png)

 Related information
--------------------

### Components

*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help-inline.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/colorpicker`[View in NPM](https://www.npmjs.com/package/@skyux/colorpicker) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/colorpicker/src/lib/modules/colorpicker/colorpicker.module.ts#L47) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/colorpicker`Copy None found.

 SkyColorpickerModule
---------------------

Type: Module

`import { SkyColorpickerModule } from '@skyux/colorpicker';`

 SkyColorpickerComponent
------------------------

Type: Component

Selector: `sky-colorpicker`

The SKY UX-themed replacement for the HTML `input` element with `type="color"`. The value that users select is driven through the `ngModel` attribute specified on the `input` element.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the colorpicker label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the colorpicker label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `label: string | undefined`

The ARIA label for the colorpicker. This sets the colorpicker's `aria-label` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md) when the colorpicker does not include a visible label. If the colorpicker includes a visible label, use `labelledBy` instead.

Default: `"Select color value"`

#### `labelHidden: boolean`

Whether to hide `labelText` from view.

Default: `false`

#### `labelText: string | undefined`

The text to display as the colorpicker's label. Use this instead of a `label` element when the label is text-only. Specifying `labelText` also enables automatic error message handling for standard colorpicker errors.

#### `labelledBy: string | undefined`

The HTML element ID of the element that labels the colorpicker. This sets the colorpicker's `aria-labelledby` attribute [to support accessibility](/skyux/components/checkbox#accessibility.md). If the colorpicker does not include a visible label, use `label` instead.

#### `messageStream: Subject<SkyColorpickerMessage>`

The observable to send commands to the colorpicker. The commands should respect the `SkyColorpickerMessage` type.

#### `showResetButton: boolean`

Whether to display a reset button to let users return to the default color.

Default: `true`

#### `stacked: boolean`

Whether the colorpicker is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the text editor.

Default: `false`

### Outputs

#### `selectedColorApplied: EventEmitter<SkyColorpickerResult>`

Fires when users select **Apply** in the colorpicker to apply a color.

#### `selectedColorChanged: EventEmitter<SkyColorpickerOutput>`

Fires when users select a color in the colorpicker.

 SkyFormErrorComponent
----------------------

Type: Component

Selector: `sky-form-error`

Displays default and custom form field error messages for form field components. Set `labelText` on the form field component to automatically display required, maximum length, minimum length, date, email, phone number, time, and URL errors. To display custom errors, include sky-form-error elements in the form field component.

### Inputs

#### `errorName: string`

Required

The name of the error.

#### `errorText: string`

Required

The error message to display.

 SkyColorpickerInputDirective
-----------------------------

Type: Directive

Selector: `[skyColorpickerInput]`

Creates the colorpicker element and dropdown.

### Inputs

#### `skyColorpickerInput: SkyColorpickerComponent`

Required

Creates the colorpicker element and dropdown. Place this attribute on an `input` element or `button` element, wrap the element in a `sky-colorpicker` component, and set the attribute to the instance of the `sky-colorpicker` component.

#### `allowTransparency: boolean`

Whether to display a transparency slider for users to select transparency levels.

Default: `true`

#### `alphaChannel: string`

The type of transparency in the transparency slider.

Default: `"hex6"`

#### `initialColor: string`

The initial color to load in the colorpicker. Use a reactive or template-driven form to set this value. This property is deprecated. As an alternative, we recommend the `formControlName` property on reactive forms or `ngModel` on template-driven forms. See the demo for examples.

#### `outputFormat: string`

The format for the color when the colorpicker uses a native input element such as a standard text input or a button. This property accepts `rgba`, `hex`, or `hsla`, but we do not recommend using it because users never see or use its value. Instead, if you need to access this format value, see the demo for an example.

Default: `"rgba"`

#### `presetColors: string[]`

The array of colors to load as preset choices. The colorpicker displays the colors in a series of 12 boxes for users to select.

#### `returnFormat: string`

This property is deprecated and does not affect the colorpicker. We recommend against using it.

Default: `"rgba"`

 SkyColorpickerCmyk
-------------------

Type: Interface

Colors specified as a combination of cyan, magenta, yellow, and black.

    interface SkyColorpickerCmyk {
      cyan: number;
      key: number;
      magenta: number;
      yellow: number;
    }

### Properties

#### `cyan: number`

The percentage of cyan.

#### `key: number`

The percentage of black.

#### `magenta: number`

The percentage of magenta.

#### `yellow: number`

The percentage of yellow.

 SkyColorpickerHsla
-------------------

Type: Interface

Colors specified as a combination of hue, saturation, and lightness with an alpha channel to set the opacity.

    interface SkyColorpickerHsla {
      alpha: number;
      hue: number;
      lightness: number;
      saturation: number;
    }

### Properties

#### `alpha: number`

The alpha channel to set the opacity.

#### `hue: number`

The hue, which is a degree on the color wheel from 0 to 360. 0 is red, 120 is green, and 240 is blue.

#### `lightness: number`

The lightness, which is a percentage value where 0 percent is black and 100 percent is white.

#### `saturation: number`

The saturation, which is a percentage value where 0 percent is a shade of gray and 100 percent is the full color.

 SkyColorpickerHsva
-------------------

Type: Interface

Colors specified as a combination of hue, saturation, and value with an alpha channel to set the opacity.

    interface SkyColorpickerHsva {
      alpha: number;
      hue: number;
      saturation: number;
      value: number;
    }

### Properties

#### `alpha: number`

The alpha channel to set the opacity.

#### `hue: number`

The hue, which is a degree on the color wheel from 0 to 360. 0 is red, 120 is green, and 240 is blue.

#### `saturation: number`

The saturation, which is a percentage value where 0 percent is a shade of gray and 100 percent is the full color.

#### `value: number`

The brightness or intensity, which is a percentage value of the color where 0 is completely black and 100 is the brightest and reveals the most color.

 SkyColorpickerRgba
-------------------

Type: Interface

Colors specified as a combination of red, green, and blue with an alpha channel to set the opacity.

    interface SkyColorpickerRgba {
      alpha: number;
      blue: number;
      green: number;
      red: number;
    }

### Properties

#### `alpha: number`

The alpha channel to set the opacity.

#### `blue: number`

The percentage of blue.

#### `green: number`

The percentage of green.

#### `red: number`

The percentage of red.

 SkyColorpickerOutput
---------------------

Type: Interface

Describes the color that users select in the colorpicker.

    interface SkyColorpickerOutput {
      cmyk: SkyColorpickerCmyk;
      cmykText: string;
      hex: string;
      hsla: SkyColorpickerHsla;
      hslaText: string;
      hsva: SkyColorpickerHsva;
      rgba: SkyColorpickerRgba;
      rgbaText: string;
    }

### Properties

#### `cmyk: SkyColorpickerCmyk`

The CMYK values for the selected color.

#### `cmykText: string`

The CMYK text value for the selected color.

#### `hex: string`

The hex value for the selected color.

#### `hsla: SkyColorpickerHsla`

The HSLA values for the selected color.

#### `hslaText: string`

The HSLA text value for the selected color.

#### `hsva: SkyColorpickerHsva`

The HSVA values for the selected color.

#### `rgba: SkyColorpickerRgba`

The RGBA values for the selected color.

#### `rgbaText: string`

The RGBA text value for the selected color.

 SkyColorpickerResult
---------------------

Type: Interface

Indicates the color that users apply when they select Apply in the colorpicker.

    interface SkyColorpickerResult {
      color: SkyColorpickerOutput;
    }

### Properties

#### `color: SkyColorpickerOutput`

Describes the color that users select in the colorpicker.

 SkyColorpickerMessage
----------------------

Type: Interface

Provides commands for the colorpicker through a message stream.

    interface SkyColorpickerMessage {
      type?: SkyColorpickerMessageType;
    }

### Properties

#### `type?: SkyColorpickerMessageType`

The message type.

 SkyColorpickerMessageType
--------------------------

Type: Enumeration

The commands to provide the colorpicker.

    enum SkyColorpickerMessageType {
      Close = 3,
      Open = 0,
      Reset = 1,
      ToggleResetButton = 2,
    }

### Properties

#### `SkyColorpickerMessageType.Close`

Closes the colorpicker.

#### `SkyColorpickerMessageType.Open`

Opens the colorpicker.

#### `SkyColorpickerMessageType.Reset`

Resets the selection in the colorpicker.

#### `SkyColorpickerMessageType.ToggleResetButton`

Toggles whether to display a reset button beside the colorpicker.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyColorpickerHarness
----------------------

Type: Class

`import { SkyColorpickerHarness } from '@skyux/colorpicker/testing';`

Harness for interacting with colorpicker components in tests.

### Methods

#### `clickColorpickerButton(): Promise<void>`

Clicks the colorpicker button.

#### Returns

`Promise<void>`

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `clickResetButton(): Promise<void>`

Clicks the reset button. Throws an error if the reset button is hidden.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the colorpicker button's `aria-label`.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the colorpicker button's `aria-labelledby`

#### Returns

`Promise<null | string>`

#### `getColorpickerDropdown(): Promise<SkyColorpickerDropdownHarness>`

Gets the `SkyColorpickerDropdownHarness` for the colorpicker dropdown controlled by the colorpicker button. Throws an error if the dropdown is not open.

#### Returns

`Promise<SkyColorpickerDropdownHarness>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help inline popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help inline popover title.

#### Returns

`Promise<undefined | string>`

#### `getHintText(): Promise<string>`

Gets the colorpicker component's hint text.

#### Returns

`Promise<string>`

#### `getLabelHidden(): Promise<boolean>`

Whether the colorpicker component's label is hidden.

#### Returns

`Promise<boolean>`

#### `getLabelText(): Promise<string>`

Gets the colorpicker component's label text.

#### Returns

`Promise<string>`

#### `hasError(errorName: string): Promise<boolean>`

Whether the custom error has fired.

#### Parameters

##### `errorName: string`

`errorName` of the custom error.

#### Returns

`Promise<boolean>`

#### `hasRequiredError(): Promise<boolean>`

Whether the required error has fired.

#### Returns

`Promise<boolean>`

#### `hasResetButton(): Promise<boolean>`

Whether the reset button is shown.

#### Returns

`Promise<boolean>`

#### `isColorpickerOpen(): Promise<boolean>`

Whether the colorpicker component is open.

#### Returns

`Promise<boolean>`

#### `isStacked(): Promise<boolean>`

Whether the colorpicker component is stacked.

#### Returns

`Promise<boolean>`

#### `SkyColorpickerHarness.with(filters: SkyColorpickerHarnessFilters): HarnessPredicate<SkyColorpickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyColorpickerHarness` that meets certain criteria

#### Parameters

##### `filters: SkyColorpickerHarnessFilters`

#### Returns

`HarnessPredicate<SkyColorpickerHarness>`

 SkyColorpickerHarnessFilters
-----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColorpickerHarness` instances.

    interface SkyColorpickerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyColorpickerDropdownHarness
------------------------------

Type: Class

`import { SkyColorpickerDropdownHarness } from '@skyux/colorpicker/testing';`

Harness for interacting with colorpicker dropdown in tests.

### Methods

#### `allowsTransparency(): Promise<boolean>`

Whether transparency is allowed.

#### Returns

`Promise<boolean>`

#### `clickApplyButton(): Promise<void>`

Clicks the colorpicker dropdown apply button.

#### Returns

`Promise<void>`

#### `clickCancelButton(): Promise<void>`

Clicks the colorpicker dropdown cancel button.

#### Returns

`Promise<void>`

#### `clickPresetColorSwatch(swatchHex: string): Promise<void>`

Clicks a specified swatch in the color preset section.

#### Parameters

##### `swatchHex: string`

Hex code of the swatch to click.

#### Returns

`Promise<void>`

#### `getPresetColorSwatches(): Promise<string[]>`

Gets an array of the hex codes of the preset color swatches.

#### Returns

`Promise<string[]>`

#### `setAlphaValue(value: string): Promise<void>`

Enters a value into the alpha input box.

#### Parameters

##### `value: string`

A decimal value from 0-1.

#### Returns

`Promise<void>`

#### `setBlueValue(value: string): Promise<void>`

Enters a value into the blue input box.

#### Parameters

##### `value: string`

A value from 0-255

#### Returns

`Promise<void>`

#### `setGreenValue(value: string): Promise<void>`

Enters a value into the green input box.

#### Parameters

##### `value: string`

A value from 0-255

#### Returns

`Promise<void>`

#### `setHexValue(value: string): Promise<void>`

Enters a value into the hex input box.

#### Parameters

##### `value: string`

A hex value

#### Returns

`Promise<void>`

#### `setRedValue(value: string): Promise<void>`

Enters a value into the red input box.

#### Parameters

##### `value: string`

A value from 0-255

#### Returns

`Promise<void>`

#### `SkyColorpickerDropdownHarness.with(filters: SkyColorpickerDropdownHarnessFilters): HarnessPredicate<SkyColorpickerDropdownHarness>`

#### Parameters

##### `filters: SkyColorpickerDropdownHarnessFilters`

#### Returns

`HarnessPredicate<SkyColorpickerDropdownHarness>`

 SkyColorpickerDropdownHarnessFilters
-------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColorpickerDropdownHarness` instances.

    interface SkyColorpickerDropdownHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyIconHarness
---------------

Type: Class

`import { SkyIconHarness } from '@skyux/icon/testing';`

Harness for interacting with an icon component in tests.

### Methods

#### `getIconName(): Promise<undefined | string>`

Gets the icon name.

#### Returns

`Promise<undefined | string>`

#### `getIconSize(): Promise<string>`

Gets the icon size.

#### Returns

`Promise<string>`

#### `getVariant(): Promise<string>`

Gets if the icon is a variant.

#### Returns

`Promise<string>`

#### `SkyIconHarness.with(filters: SkyIconHarnessFilters): HarnessPredicate<SkyIconHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyIconHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyIconHarnessFilters`

#### Returns

`HarnessPredicate<SkyIconHarness>`

 SkyIconHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyIconHarness](/skyux/components/colorpicker?docs-active-tab=design#class_sky-icon-harness.md) instances.

    interface SkyIconHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
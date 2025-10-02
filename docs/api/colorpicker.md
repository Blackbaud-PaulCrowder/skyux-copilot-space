---
component: 'colorpicker'
type: 'api-documentation'
description: 'API documentation for the colorpicker component including components, interfaces, and types.'
---

# Colorpicker API Documentation

## Components and Directives

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
to the instance of the `sky-colorpicker` component.
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
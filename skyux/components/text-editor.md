                      

 Text editor
===========

Text editors let users format and manipulate text.

 Usage
------

### Use when

Use text editors when users need to create blocks of text that include formatted text, hyperlinks, or merge fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/text-editor/use-when.abd5ded03fcf063013f812b5658f8c69.png)

Use text editors when users need to manipulate blocks of text.

### Don't use when

Don't use the text editor when users only need to enter unformatted plain text. Use a text `input` or `textarea` instead.

 Anatomy
--------

1

Label

2

Text entry area

3

Required field marker (optional)

4

Help inline button (optional)

5

Menus (optional)

6

Toolbar actions (optional)

7

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/text-editor/anatomy.74b3567cf032b00850ad0b8403a71f09.png)

 Options
--------

### Required field marker

When a text editor is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

### Help inline button

When you need to supplement the text editor label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Menus and toolbar

Default menus:

*   Edit
*   Format

Optional menu:

*   Merge

Default toolbar actions:

*   Font
*   Text size
*   Text style (bold/italic/underline)
*   Text color
*   Highlight color
*   List format (numbered/bulleted)
*   Hyperlink

Optional toolbar actions:

*   Alignment (left/center/right)
*   Undo/redo
*   Indentation

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/text-editor/option-menu-toolbar-items.44063b8d6a59b397e989c04692627b58.png)

Text editor with default options.

### Hint text

To highlight important considerations about a text editor, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on text editor content
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a text editor is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the text editor from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the text editor:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/text-editor/options-stacked.3ea164ae2bd01b71f75966ddf6e11a91.png)

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

`@skyux/text-editor`[View in NPM](https://www.npmjs.com/package/@skyux/text-editor) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/text-editor/src/lib/modules/text-editor/text-editor.module.ts#L10) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/text-editor`Copy None found.

 HTML sanitization
------------------

Don't blindly trust the HTML that users provide in the text editor. They can insert malicious content into HTML strings before you save it to your service, so we recommend using an HTML sanitizer to clean up the HTML and protect against XSS attacks.

*   We recommend the [HtmlSanitizer package](https://github.com/mganss/HtmlSanitizer) for C# projects.
*   We recommend the [Owasp HTML Sanitizer package](https://owasp.org/www-project-java-html-sanitizer/) for Java projects.

Make sure that you allow the attributes and schemes that you need. For example, email links often violate the default rules of HTML sanitizers.

 SkyTextEditorModule
--------------------

Type: Module

`import { SkyTextEditorModule } from '@skyux/text-editor';`

 SkyTextEditorComponent
-----------------------

Type: Component

Selector: `sky-text-editor`

The text editor component lets users format and manipulate text.

### Inputs

#### `autofocus: boolean | undefined`

Whether to put focus on the editor after it renders.

Default: `false`

#### `disabled: boolean`

Whether to disable the text editor on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `fontList: SkyTextEditorFont[]`

The fonts to include in the font picker.

Default: `[{name: 'Blackbaud Sans', value: '"Blackbaud Sans", Arial, sans-serif'}, {name: 'Arial', value: 'Arial'}, {name: 'Arial Black', value: '"Arial Black"'}, {name: 'Courier New', value: '"Courier New"'}, {name: 'Georgia', value: 'Georgia, serif'}, {name: 'Tahoma', value: 'Tahoma, Geneva, sans-serif'}, {name: 'Times New Roman', value: '"Times New Roman"'}, {name: 'Trebuchet MS', value: '"Trebuchet MS", sans-serif'}, {name: 'Verdana', value: 'Verdana, Geneva, sans-serif'}]`

#### `fontSizeList: number[]`

The font sizes to include in the font size picker.

Default: `[6, 8, 9, 10, 11, 12, 13, 14, 15, 16, 18, 20, 22, 24, 26, 28, 36, 48]`

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the text editor label. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `labelText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `labelText`, a [help inline](/skyux/components/help-inline.md) button is added to the text editor. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `id: string`

The unique ID attribute for the text editor. By default, the component generates a random ID.

#### `initialStyleState: SkyTextEditorStyleState`

The initial styles for all content, including background color, font size, and link state.

#### `labelText: string | undefined`

The text to display as the text editor's label.

#### `linkWindowOptions: SkyTextEditorLinkWindowOptionsType[]`

The target window options for adding a hyperlink.

Default: `[ 'new', 'existing' ]`

#### `menus: SkyTextEditorMenuType[]`

The menus to include in the menu bar.

Default: `[ 'edit', 'format' ]`

#### `mergeFields: SkyTextEditorMergeField[]`

The merge fields to include in the merge field menu.

#### `placeholder: string`

Placeholder text to display when the text entry area is empty.

#### `stacked: boolean`

Whether the text editor is stacked on another form component. When specified, the appropriate vertical spacing is automatically added to the text editor.

Default: `false`

#### `toolbarActions: SkyTextEditorToolbarActionType[]`

The actions to include in the toolbar in the specified order.

Default: `[ 'font-family', 'font-size', 'font-style', 'color', 'list', 'link ]`

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

 SkyTextEditorFont
------------------

Type: Interface

    interface SkyTextEditorFont {
      name: string;
      value: string;
    }

### Properties

#### `name: string`

The display name of the font.

#### `value: string`

The CSS `font-family` value for the font.

 SkyTextEditorLinkWindowOptionsType
-----------------------------------

Type: Type alias

    type SkyTextEditorLinkWindowOptionsType = "new" | "existing"

 SkyTextEditorMenuType
----------------------

Type: Type alias

    type SkyTextEditorMenuType = "edit" | "format" | "merge-field"

 SkyTextEditorStyleState
------------------------

Type: Interface

    interface SkyTextEditorStyleState {
      backColor: string;
      boldState: boolean;
      font: string;
      fontColor: string;
      fontSize: number;
      italicState: boolean;
      linkState: boolean;
      underlineState: boolean;
    }

### Properties

#### `backColor: string`

The background color. Accepts any CSS color value.

#### `boldState: boolean`

Whether to make text bold.

#### `font: string`

The font family. Available values: `"Blackbaud Sans"`, `"Arial"`, `"sans-serif"`, `"Arial Black"`, `"Courier New"`, and `"Times New Roman"`.

#### `fontColor: string`

The font color. Accepts any CSS color value.

#### `fontSize: number`

The font size in pixels.

#### `italicState: boolean`

Whether to italicize text.

#### `linkState: boolean`

Whether to format text as a link.

#### `underlineState: boolean`

Whether to underline text.

 SkyTextEditorMergeField
------------------------

Type: Interface

    interface SkyTextEditorMergeField {
      id: string;
      name: string;
      previewImageUrl?: string;
    }

### Properties

#### `id: string`

The identifier for the merge field.

#### `name: string`

Display text for the merge field. If it is more than 18 characters, the component truncates to 15 characters.

#### `previewImageUrl?: string`

The `src` attribute for a preview image to represent the merge field in the text editor. By default, the `name` value appears in a blue rectangle.

 SkyTextEditorToolbarActionType
-------------------------------

Type: Type alias

    type SkyTextEditorToolbarActionType = "font-family" | "font-size" | "font-style" | "color" | "list" | "alignment" | "indentation" | "undo-redo" | "link"
---
component: 'text-editor'
type: 'api-documentation'
description: 'API documentation for the text-editor component including components, interfaces, and types.'
---

# Text Editor API Documentation

## Components and Directives

#### TextEditorHelpKeyExampleComponent

**Selector:** `app-text-editor-help-key-example`

**Package:** `@skyux/code-examples`

#### TextEditorRichTextDisplayExampleComponent

**Selector:** `app-text-editor-rich-text-display-example`

**Package:** `@skyux/code-examples`

#### TextEditorExampleComponent

**Selector:** `app-text-editor-example`

**Package:** `@skyux/code-examples`

#### SkyTextEditorMenubarComponent

**Selector:** `sky-text-editor-menubar`

**Package:** `@skyux/text-editor`

**Inputs:**

- `disabled`: `boolean` (default: false)
- `editorFocusStream`: `Subject<void>`
- `menus`: `SkyTextEditorMenuType[]` (default: [])
- `mergeFields`: `SkyTextEditorMergeField[]` (default: [])

#### SkyTextEditorComponent

The text editor component lets users format and manipulate text.

**Selector:** `sky-text-editor`

**Package:** `@skyux/text-editor`

**Inputs:**

- `autofocus`: `boolean | undefined` - Whether to put focus on the editor after it renders. (default: false)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the text editor label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the text editor. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `boolean` - Whether the text editor is stacked on another form component. When specified,
the appropriate vertical spacing is automatically added to the text editor. (default: false)
- `disabled`: `boolean` - Whether to disable the text editor on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `fontList`: `SkyTextEditorFont[]` - The fonts to include in the font picker. (default: [{name: 'Blackbaud Sans', value: '"Blackbaud Sans", Arial, sans-serif'}, {name: 'Arial', value: 'Arial'}, {name: 'Arial Black', value: '"Arial Black"'}, {name: 'Courier New', value: '"Courier New"'}, {name: 'Georgia', value: 'Georgia, serif'}, {name: 'Tahoma', value: 'Tahoma, Geneva, sans-serif'}, {name: 'Times New Roman', value: '"Times New Roman"'}, {name: 'Trebuchet MS', value: '"Trebuchet MS", sans-serif'}, {name: 'Verdana', value: 'Verdana, Geneva, sans-serif'}])
- `fontSizeList`: `number[]` - The font sizes to include in the font size picker. (default: [6, 8, 9, 10, 11, 12, 13, 14, 15, 16, 18, 20, 22, 24, 26, 28, 36, 48])
- `id`: `string` - The unique ID attribute for the text editor.
By default, the component generates a random ID.
- `initialStyleState`: `SkyTextEditorStyleState` - The initial styles for all content, including background color, font size, and link state.
- `labelText`: `string | undefined` - The text to display as the text editor's label.
- `linkWindowOptions`: `SkyTextEditorLinkWindowOptionsType[]` - The target window options for adding a hyperlink. (default: [ 'new', 'existing' ])
- `menus`: `SkyTextEditorMenuType[]` - The menus to include in the menu bar. (default: [ 'edit', 'format' ])
- `mergeFields`: `SkyTextEditorMergeField[]` - The merge fields to include in the merge field menu.
- `placeholder`: `string` - Placeholder text to display when the text entry area is empty.
- `toolbarActions`: `SkyTextEditorToolbarActionType[]` - The actions to include in the toolbar in the specified order. (default: [ 'font-family', 'font-size', 'font-style', 'color', 'list', 'link ])

#### SkyTextEditorToolbarComponent

**Selector:** `sky-text-editor-toolbar`

**Package:** `@skyux/text-editor`

**Inputs:**

- `disabled`: `boolean` (default: false)
- `fontList`: `SkyTextEditorFont[]` (default: [])
- `fontSizeList`: `number[]` (default: [])
- `linkWindowOptions`: `SkyTextEditorLinkWindowOptionsType[]` (default: [])
- `toolbarActions`: `SkyTextEditorToolbarActionType[]` (default: [])
- `editorFocusStream`: `Subject<void>`
- `styleState`: `SkyTextEditorStyleState`

#### SkyTextEditorUrlModalComponent

**Selector:** `sky-text-editor-url-modal`

**Package:** `@skyux/text-editor`
---
component: 'text-editor'
description: 'Design guidelines, API documentation, and usage instructions for the text-editor component extracted from SKY UX documentation.'
---

# Text Editor Component Guidelines

## Component Overview
Text editors let users format and manipulate text.

## Usage

### ✅ Use when

Use text editors when users need to create blocks of text that include formatted text, hyperlinks, or merge fields.

### ❌ Don't use when

Don't use the text editor when users only need to enter unformatted plain text. Use a text input or textarea instead.

## Anatomy

- Label
- Text entry area
- Required field marker
- Help inline button
- Menus
- Toolbar actions
- Hint text

## Options

### Required field marker

When a text editor is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement the text editor label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Menus and toolbar

Default menus:

- Edit
- Format

Optional menu:

- Merge

Default toolbar actions:

- Font
- Text size
- Text style (bold/italic/underline)
- Text color
- Highlight color
- List format (numbered/bulleted)
- Hyperlink

Optional toolbar actions:

- Alignment (left/center/right)
- Undo/redo
- Indentation

### Hint text

To highlight important considerations about a text editor, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on text editor content
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a text editor is immediately followed by another form input, use stacked to add a bottom margin that visually separates the text editor from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the text editor:

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

#### SkyTextEditorModule

**Package:** `@skyux/text-editor`

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

#### SkyTextEditorFont

**Package:** `@skyux/text-editor`

#### SkyTextEditorLinkWindowOptionsType

**Package:** `@skyux/text-editor`

#### SkyTextEditorMenuType

**Package:** `@skyux/text-editor`

#### SkyTextEditorStyleState

**Package:** `@skyux/text-editor`

#### SkyTextEditorMergeField

**Package:** `@skyux/text-editor`

#### SkyTextEditorToolbarActionType

**Package:** `@skyux/text-editor`

#### SkyTextEditorUrlModalComponent

**Selector:** `sky-text-editor-url-modal`

**Package:** `@skyux/text-editor`

### Code Examples

#### Text editor with help key

**Selector:** `app-text-editor-help-key-example`

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
import { SkyTextEditorModule } from '@skyux/text-editor';

function validateText(
  control: AbstractControl<string>,
): ValidationErrors | null {
  return !control.value?.includes('Blackbaud') ? { companyName: true } : null;
}

/**
 * @title Text editor with help key
 */
@Component({
  selector: 'app-text-editor-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyTextEditorModule],
})
export class TextEditorHelpKeyExampleComponent {
  protected formGroup: FormGroup;
  public myText: FormControl;

  #richText = `<font style="font-size: 18px" face="Arial" color="#a25353"><b>Exclusively committed to your impact</b></font><p>Since day one, Blackbaud has been 100% focused on driving impact for social good organizations.</p><p>We equip change agents with <b>cloud software</b>, <i>services</i>, <u>expertise</u>, and <font color="#a25353">data intelligence</font> designed with unmatched insight and supported with unparalleled commitment. Every day, our <b>customers</b> achieve unmatched impact as they advance their missions.</p>`;

  constructor() {
    this.myText = new FormControl(this.#richText, {
      nonNullable: true,
      validators: [Validators.required, validateText],
    });

    this.formGroup = inject(FormBuilder).group({
      myText: this.myText,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-text-editor
    formControlName="myText"
    helpKey="email-help"
    hintText="Include details about how to opt out of future email."
    labelText="Message"
  >
    @if (myText.errors?.['companyName']) {
      <sky-form-error
        errorName="companyName"
        errorText="Message must include company name."
      />
    }
  </sky-text-editor>
</form>

```

#### Rich text display with basic setup

**Selector:** `app-text-editor-rich-text-display-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyRichTextDisplayModule } from '@skyux/text-editor';

/**
 * @title Rich text display with basic setup
 */
@Component({
  selector: 'app-text-editor-rich-text-display-example',
  templateUrl: './example.component.html',
  imports: [SkyRichTextDisplayModule],
})
export class TextEditorRichTextDisplayExampleComponent {
  protected richText = `<font style="font-size: 18px" face="Arial" color="#a25353"><b>Exclusively committed to your impact</b></font><p>Since day one, Blackbaud has been 100% focused on driving impact for social good organizations.</p><p>We equip change agents with <b>cloud software</b>, <i>services</i>, <u>expertise</u>, and <font color="#a25353">data intelligence</font> designed with unmatched insight and supported with unparalleled commitment. Every day, our <b>customers</b> achieve unmatched impact as they advance their missions.</p><ul><li><a href="#">Build a better world</a></li><li><a href="#">Explore our solutions</a></li></ul>`;
}

```

**Template:**

```html
<sky-rich-text-display [richText]="richText" />

```

#### Text editor with basic setup

**Selector:** `app-text-editor-example`

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
import { SkyTextEditorModule } from '@skyux/text-editor';

function validateText(
  control: AbstractControl<string>,
): ValidationErrors | null {
  return !control.value?.includes('Blackbaud') ? { companyName: true } : null;
}

/**
 * @title Text editor with basic setup
 */
@Component({
  selector: 'app-text-editor-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyTextEditorModule],
})
export class TextEditorExampleComponent {
  protected formGroup: FormGroup;
  public myText: FormControl;

  #richText = `<font style="font-size: 18px" face="Arial" color="#a25353"><b>Exclusively committed to your impact</b></font><p>Since day one, Blackbaud has been 100% focused on driving impact for social good organizations.</p><p>We equip change agents with <b>cloud software</b>, <i>services</i>, <u>expertise</u>, and <font color="#a25353">data intelligence</font> designed with unmatched insight and supported with unparalleled commitment. Every day, our <b>customers</b> achieve unmatched impact as they advance their missions.</p>`;

  constructor() {
    this.myText = new FormControl(this.#richText, {
      nonNullable: true,
      validators: [Validators.required, validateText],
    });

    this.formGroup = inject(FormBuilder).group({
      myText: this.myText,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-text-editor
    formControlName="myText"
    helpPopoverTitle="Ensure deliverability"
    helpPopoverContent="High quality, relevant email content and calls to action drive
      engagement and avoid being marked as junk mail. For details, see writing
      for engagement and deliverability."
    hintText="Include details about how to opt out of future email."
    labelText="Message"
  >
    @if (myText.errors?.['companyName']) {
      <sky-form-error
        errorName="companyName"
        errorText="Message must include company name."
      />
    }
  </sky-text-editor>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
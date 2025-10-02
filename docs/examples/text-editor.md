---
component: 'text-editor'
type: 'code-examples'
description: 'Code examples for the text-editor component.'
---

# Text Editor Code Examples

## Text editor with help key

**Component:** TextEditorHelpKeyExampleComponent

**Selector:** `app-text-editor-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---

## Rich text display with basic setup

**Component:** TextEditorRichTextDisplayExampleComponent

**Selector:** `app-text-editor-rich-text-display-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

```html
<sky-rich-text-display [richText]="richText" />

```

---

## Text editor with basic setup

**Component:** TextEditorExampleComponent

**Selector:** `app-text-editor-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---
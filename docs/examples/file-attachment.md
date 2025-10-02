---
component: 'file-attachment'
type: 'code-examples'
description: 'Code examples for the file-attachment component.'
---

# File Attachment Code Examples

## File attachment with basic setup

**Component:** FormsFileAttachmentBasicExampleComponent

**Selector:** `app-forms-file-attachment-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyFileAttachmentHarness,
  provideSkyFileAttachmentTesting,
} from '@skyux/forms/testing';

import { FormsFileAttachmentBasicExampleComponent } from './example.component';

describe('Basic file attachment example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyFileAttachmentHarness;
    fixture: ComponentFixture<FormsFileAttachmentBasicExampleComponent>;
  }> {
    TestBed.configureTestingModule({
      providers: [provideSkyFileAttachmentTesting()],
    });
    const fixture = TestBed.createComponent(
      FormsFileAttachmentBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyFileAttachmentHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsFileAttachmentBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set initial values', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'birth-certificate',
    });

    await expectAsync(harness.getLabelText()).toBeResolvedTo(
      'Birth certificate',
    );
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Attach a .pdf, .gif, .png, or .jpeg file.',
    );
    await expectAsync(harness.getAcceptedTypes()).toBeResolvedTo(
      'application/pdf,image/jpeg,image/png,image/gif',
    );
    await expectAsync(harness.isRequired()).toBeResolvedTo(true);

    await harness.clickHelpInline();

    await expectAsync(harness.getHelpPopoverTitle()).toBeResolvedTo(
      'Requirements',
    );
  });

  it('should throw an error if file begins with the letter a', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'birth-certificate',
    });

    const file = new File([], 'art.png', { type: 'image/png' });
    await harness.attachFile(file);

    await expectAsync(
      harness.hasCustomError('invalidStartingLetter'),
    ).toBeResolvedTo(true);
  });
});

```

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
import {
  SkyFileAttachmentClick,
  SkyFileAttachmentModule,
  SkyFileItem,
} from '@skyux/forms';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<SkyFileItem | null | undefined>,
): ValidationErrors | null {
  const fileItem = control.value;

  return fileItem?.file?.name.startsWith('a')
    ? { invalidStartingLetter: true }
    : null;
}

/**
 * @title File attachment with basic setup
 */
@Component({
  selector: 'app-forms-file-attachment-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyFileAttachmentModule],
})
export class FormsFileAttachmentBasicExampleComponent {
  protected attachment: FormControl<SkyFileItem | null | undefined>;

  protected formGroup: FormGroup<{
    attachment: FormControl<SkyFileItem | null | undefined>;
  }>;

  protected maxFileSize = 4000000;

  constructor() {
    this.attachment = new FormControl(undefined, {
      validators: [Validators.required, customValidator],
    });

    this.formGroup = inject(FormBuilder).group({
      attachment: this.attachment,
    });
  }

  protected onFileClick($event: SkyFileAttachmentClick): void {
    // Ensure we are only attempting to navigate to locally updated data for download.
    if ($event.file.url.startsWith('data:')) {
      const link = document.createElement('a');
      link.download = $event.file.file.name;
      link.href = $event.file.url;
      link.click();
    }
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-file-attachment
    acceptedTypes="application/pdf,image/jpeg,image/png,image/gif"
    data-sky-id="birth-certificate"
    formControlName="attachment"
    helpPopoverTitle="Requirements"
    hintText="Attach a .pdf, .gif, .png, or .jpeg file."
    labelText="Birth certificate"
    [helpPopoverContent]="helpInlinePopoverRef"
    [maxFileSize]="maxFileSize"
    (fileClick)="onFileClick($event)"
  >
    @if (attachment.errors?.['invalidStartingLetter']) {
      <sky-form-error
        errorName="invalidStartingLetter"
        errorText="You may not upload a file that begins with the letter 'a'."
      />
    }
  </sky-file-attachment>
</form>

<ng-template #helpInlinePopoverRef>
  Make sure the birth certificate includes:
  <ul>
    <li>Full name of child</li>
    <li>Birth date</li>
    <li>Place of birth</li>
    <li>Name and signature of the physician or midwife</li>
    <li>Registration or certificate number</li>
  </ul>
</ng-template>

```

---

## File attachment with help key

**Component:** FormsFileAttachmentHelpKeyExampleComponent

**Selector:** `app-forms-file-attachment-help-key-example`

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
import {
  SkyFileAttachmentClick,
  SkyFileAttachmentModule,
  SkyFileItem,
} from '@skyux/forms';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<SkyFileItem | null | undefined>,
): ValidationErrors | null {
  const fileItem = control.value;

  return fileItem?.file?.name.startsWith('a')
    ? { invalidStartingLetter: true }
    : null;
}

/**
 * @title File attachment with help key
 */
@Component({
  selector: 'app-forms-file-attachment-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyFileAttachmentModule],
})
export class FormsFileAttachmentHelpKeyExampleComponent {
  protected attachment: FormControl<SkyFileItem | null | undefined>;

  protected formGroup: FormGroup<{
    attachment: FormControl<SkyFileItem | null | undefined>;
  }>;

  protected maxFileSize = 4000000;

  constructor() {
    this.attachment = new FormControl(undefined, {
      validators: [Validators.required, customValidator],
    });

    this.formGroup = inject(FormBuilder).group({
      attachment: this.attachment,
    });
  }

  protected onFileClick($event: SkyFileAttachmentClick): void {
    // Ensure we are only attempting to navigate to locally updated data for download.
    if ($event.file.url.startsWith('data:')) {
      const link = document.createElement('a');
      link.download = $event.file.file.name;
      link.href = $event.file.url;
      link.click();
    }
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-file-attachment
    acceptedTypes="application/pdf,image/jpeg,image/png,image/gif"
    formControlName="attachment"
    helpKey="file-help"
    hintText="Attach a .pdf, .gif, .png, or .jpeg file."
    labelText="Birth certificate"
    [maxFileSize]="maxFileSize"
    (fileClick)="onFileClick($event)"
  >
    @if (attachment.errors?.['invalidStartingLetter']) {
      <sky-form-error
        errorName="invalidStartingLetter"
        errorText="You may not upload a file that begins with the letter 'a'."
      />
    }
  </sky-file-attachment>
</form>

```

---
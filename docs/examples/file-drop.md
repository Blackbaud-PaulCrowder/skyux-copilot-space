---
component: 'file-drop'
type: 'code-examples'
description: 'Code examples for the file-drop component.'
---

# File Drop Code Examples

## File drop with basic setup

**Component:** FormsFileDropBasicExampleComponent

**Selector:** `app-forms-file-drop-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { FormControl } from '@angular/forms';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyFileItem, SkyFileLink } from '@skyux/forms';
import {
  SkyFileDropHarness,
  SkyFileItemHarness,
  provideSkyFileAttachmentTesting,
} from '@skyux/forms/testing';

import { FormsFileDropBasicExampleComponent } from './example.component';

describe('Basic file drop example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyFileDropHarness;
    formControl: FormControl<(SkyFileItem | SkyFileLink)[] | null | undefined>;
    loader: HarnessLoader;
  }> {
    TestBed.configureTestingModule({
      providers: [provideSkyFileAttachmentTesting()],
    });
    const fixture = TestBed.createComponent(FormsFileDropBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyFileDropHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    const formControl = fixture.componentInstance.fileDrop;

    return { harness, formControl, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FormsFileDropBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set initial values', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'logo-upload',
    });

    await expectAsync(harness.getLabelText()).toBeResolvedTo('Logo image');
    await expectAsync(harness.getAcceptedTypes()).toBeResolvedTo(
      'image/png,image/jpeg',
    );
    await expectAsync(harness.getHintText()).toBeResolvedTo(
      'Upload up to 3 files under 50MB.',
    );
    await expectAsync(harness.isStacked()).toBeResolvedTo(true);

    await expectAsync(harness.getLinkUploadHintText()).toBeResolvedTo(
      'Start with http:// or https://',
    );
  });

  it('should not upload invalid files starting with `a`', async () => {
    const { harness, formControl } = await setupTest({
      dataSkyId: 'logo-upload',
    });

    const filesToUpload: File[] = [
      new File([], 'aWrongFile', { type: 'image/png' }),
      new File([], 'validFile', { type: 'image/png' }),
    ];

    await harness.loadFiles(filesToUpload);

    expect(formControl.value?.length).toBe(1);
    await expectAsync(harness.hasValidateFnError()).toBeResolvedTo(true);
  });

  it('should not allow more than 3 files to be uploaded', async () => {
    const { harness, formControl, loader } = await setupTest({
      dataSkyId: 'logo-upload',
    });

    await harness.loadFiles([
      new File([], 'validFile1', { type: 'image/png' }),
      new File([], 'validFile2', { type: 'image/png' }),
      new File([], 'validFile3', { type: 'image/png' }),
    ]);

    expect(formControl.value?.length).toBe(3);
    await expectAsync(
      harness.hasCustomError('maxNumberOfFilesReached'),
    ).toBeResolvedTo(false);
    expect(formControl.valid).toBe(true);

    await harness.enterLinkUploadText('foo.bar');
    await harness.clickLinkUploadDoneButton();

    expect(formControl.value?.length).toBe(4);
    await expectAsync(
      harness.hasCustomError('maxNumberOfFilesReached'),
    ).toBeResolvedTo(true);
    expect(formControl.valid).toBe(false);

    const validFileItemHarness = await loader.getHarness(
      SkyFileItemHarness.with({ fileName: 'validFile2' }),
    );
    await validFileItemHarness.clickDeleteButton();

    expect(formControl.value?.length).toBe(3);
    expect(formControl.valid).toBe(true);
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
import { SkyFileDropModule, SkyFileItem, SkyFileLink } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * Demonstrates how to create a custom validator function for your form control.
 */
function customValidator(
  control: AbstractControl<(SkyFileItem | SkyFileLink)[] | null | undefined>,
): ValidationErrors | null {
  if (control.value !== undefined && control.value !== null) {
    if (control.value.length > 3) {
      return { maxNumberOfFilesReached: true };
    }
  }
  return null;
}

/**
 * @title File drop with basic setup
 */
@Component({
  selector: 'app-forms-file-drop-basic-example',
  templateUrl: './example.component.html',
  imports: [
    SkyFileDropModule,
    SkyStatusIndicatorModule,
    FormsModule,
    ReactiveFormsModule,
  ],
})
export class FormsFileDropBasicExampleComponent {
  protected acceptedTypes = 'image/png,image/jpeg';
  protected hintText = 'Upload up to 3 files under 50MB.';
  protected inlineHelpContent =
    'Your logo appears in places such as authentication pages, student and parent portals, and extracurricular home pages.';
  protected labelText = 'Logo image';
  protected maxFileSize = 5242880;
  protected stacked = 'true';

  public fileDrop = new FormControl<
    (SkyFileItem | SkyFileLink)[] | null | undefined
  >(undefined, [Validators.required, customValidator]);
  public formGroup: FormGroup = inject(FormBuilder).group({
    fileDrop: this.fileDrop,
  });

  protected deleteFile(file: SkyFileItem | SkyFileLink): void {
    const index = this.fileDrop.value?.indexOf(file);

    if (index !== undefined && index !== -1) {
      this.fileDrop.value?.splice(index, 1);
      /*
        If you are adding custom validation through the form control,
        be sure to include this line after deleting a file from the form.
      */
      this.fileDrop.updateValueAndValidity();
    }
    // To ensure that empty arrays throw required errors, include this check.
    if (this.fileDrop.value?.length === 0) {
      this.fileDrop.setValue(null);
    }
  }

  protected validateFile(file: SkyFileItem): string | undefined {
    return file.file.name.startsWith('a')
      ? 'Upload a file that does not begin with the letter "a"'
      : undefined;
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-file-drop
    data-sky-id="logo-upload"
    linkUploadHintText="Start with http:// or https://"
    formControlName="fileDrop"
    [acceptedTypes]="acceptedTypes"
    [allowLinks]="true"
    [helpPopoverContent]="inlineHelpContent"
    [hintText]="hintText"
    [labelText]="labelText"
    [maxFileSize]="maxFileSize"
    [stacked]="stacked"
    [validateFn]="validateFile"
  >
    @if (fileDrop.errors?.['maxNumberOfFilesReached']) {
      <sky-form-error
        errorName="maxNumberOfFilesReached"
        errorText="Do not upload more than 3 files."
      />
    }
  </sky-file-drop>
</form>

@for (file of fileDrop.value; track file) {
  <sky-file-item [fileItem]="file" (deleteFile)="deleteFile($event)" />
}

```

---

## File drop with help key

**Component:** FormsFileDropHelpKeyExampleComponent

**Selector:** `app-forms-file-drop-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import {
  SkyFileDropChange,
  SkyFileDropModule,
  SkyFileItem,
  SkyFileLink,
} from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title File drop with help key
 */
@Component({
  selector: 'app-forms-file-drop-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyFileDropModule, SkyStatusIndicatorModule],
})
export class FormsFileDropHelpKeyExampleComponent {
  protected acceptedTypes = 'image/png,image/jpeg';
  protected allItems: (SkyFileItem | SkyFileLink)[] = [];
  protected hintText = '5 MB maximum';
  protected labelText = 'Logo image';
  protected maxFileSize = 5242880;
  protected rejectedFiles: SkyFileItem[] = [];
  protected required = true;
  protected stacked = 'true';

  #filesToUpload: SkyFileItem[] = [];
  #linksToUpload: SkyFileLink[] = [];

  protected deleteFile(file: SkyFileItem | SkyFileLink): void {
    this.#removeFromArray(this.allItems, file);
    this.#removeFromArray(this.#filesToUpload, file);
    this.#removeFromArray(this.#linksToUpload, file);
  }

  protected onFilesChanged(change: SkyFileDropChange): void {
    this.#filesToUpload = this.#filesToUpload.concat(change.files);
    this.rejectedFiles = change.rejectedFiles;
    this.allItems = this.allItems.concat(change.files);
  }

  protected onLinkChanged(change: SkyFileLink): void {
    this.#linksToUpload = this.#linksToUpload.concat(change);
    this.allItems = this.allItems.concat(change);
  }

  protected validateFile(file: SkyFileItem): string | undefined {
    return file.file.name.startsWith('a')
      ? 'Upload a file that does not begin with the letter "a"'
      : undefined;
  }

  #removeFromArray(
    items: (SkyFileItem | SkyFileLink)[],
    obj: SkyFileItem | SkyFileLink,
  ): void {
    if (items) {
      const index = items.indexOf(obj);

      if (index !== -1) {
        items.splice(index, 1);
      }
    }
  }
}

```

#### example.component.html

```html
<sky-file-drop
  helpKey="file-help"
  linkUploadHintText="Start with http:// or https://"
  [acceptedTypes]="acceptedTypes"
  [allowLinks]="true"
  [hintText]="hintText"
  [labelText]="labelText"
  [maxFileSize]="maxFileSize"
  [required]="required"
  [stacked]="stacked"
  [validateFn]="validateFile"
  (filesChanged)="onFilesChanged($event)"
  (linkChanged)="onLinkChanged($event)"
/>
@for (file of allItems; track file) {
  <div>
    <sky-file-item [fileItem]="file" (deleteFile)="deleteFile($event)" />
  </div>
}

```

---
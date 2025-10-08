# Development

                   Skip to Main Content

 Avatar
======

The avatar component displays an image to identify a record.

 Installation
-------------

NPM package

`@skyux/avatar`[View in NPM](https://www.npmjs.com/package/@skyux/avatar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/avatar/src/lib/modules/avatar/avatar.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/avatar`Copy None found.

 SkyAvatarModule
----------------

Type: Module

`import { SkyAvatarModule } from '@skyux/avatar';`

 SkyAvatarComponent
-------------------

Type: Component

Selector: `sky-avatar`

### Inputs

#### `canChange: boolean`

Whether users can change the image. To select a different image, users click the image or drag another image on top of it, much like the `sky-file-drop` component in the [file attachment module](/skyux/components/file-attachments/file-attachment.md).

Default: `false`

#### `maxFileSize: number | undefined`

The maximum file size for the image in bytes.

Default: `512000 bytes`

#### `name: string | undefined`

The name of the record that the avatar represents. If the `src` property does not specify an image, the component displays initials from the first and last words in the name. To ensure that the component extracts the correct initials, specify a name with no prefix or suffix, or just specify initials with a space between them. This property is not required, but the component requires either the `name` or `src` property.

#### `size: SkyAvatarSize | undefined`

The size of the avatar. Acceptable values are: `"small"`, `"medium"`, and `"large"`.

Default: `"large"`

#### `src: SkyAvatarSrc | undefined`

The image to identify a record. This property is not required, but the component requires either the `name` or `src` property.

### Outputs

#### `avatarChanged: EventEmitter<SkyFileItem>`

Emits a `SkyFileItem` object when the image is updated.

 SkyAvatarSize
--------------

Type: Type alias

    type SkyAvatarSize = "large" | "medium" | "small"

 SkyAvatarSrc
-------------

Type: Type alias

    type SkyAvatarSrc = string | Blob | File

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAvatarHarness
-----------------

Type: Class

`import { SkyAvatarHarness } from '@skyux/avatar/testing';`

Harness for interacting with an avatar component in tests.

### Methods

#### `closeError(): Promise<void>`

Closes the currently displayed error.

#### Returns

`Promise<void>`

#### `dropAvatarFile(file: File, waitForChange?: boolean): Promise<void>`

Simulates the user selecting or dropping an image onto the component.

#### Parameters

##### `file: File`

##### `waitForChange?: boolean`

#### Returns

`Promise<void>`

#### `getCanChange(): Promise<boolean>`

Gets whether users can change the image.

#### Returns

`Promise<boolean>`

#### `getInitials(): Promise<undefined | string>`

Gets the initials displayed when no image URL is specified.

#### Returns

`Promise<undefined | string>`

#### `getSrc(): Promise<undefined | string | Blob>`

Gets the avatar's current image URL or Blob.

#### Returns

`Promise<undefined | string | Blob>`

#### `hasFileTypeError(): Promise<boolean>`

Gets whether an error indicating an invalid file type is displayed.

#### Returns

`Promise<boolean>`

#### `hasMaxSizeError(): Promise<boolean>`

Gets whether an error indicating an invalid file size is displayed.

#### Returns

`Promise<boolean>`

#### `SkyAvatarHarness.with(filters: SkyAvatarHarnessFilters): HarnessPredicate<SkyAvatarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAvatarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAvatarHarnessFilters`

#### Returns

`HarnessPredicate<SkyAvatarHarness>`

 SkyAvatarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAvatarHarness](/skyux/components/avatar?docs-active-tab=development#class_sky-avatar-harness.md) instances.

    interface SkyAvatarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                     Skip to Main Content

 Avatar
======

The avatar component displays an image to identify a record.Installation
-------------

NPM package

`@skyux/avatar`[View in NPM](https://www.npmjs.com/package/@skyux/avatar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/avatar/src/lib/modules/avatar/avatar.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/avatar`Copy None found.

 SkyAvatarModule
----------------

Type: Module

`import { SkyAvatarModule } from '@skyux/avatar';`

 SkyAvatarComponent
-------------------

Type: Component

Selector: `sky-avatar`

### Inputs

#### `canChange: boolean`

Whether users can change the image. To select a different image, users click the image or drag another image on top of it, much like the `sky-file-drop` component in the [file attachment module](/skyux/components/file-attachments/file-attachment.md).

Default: `false`

#### `maxFileSize: number | undefined`

The maximum file size for the image in bytes.

Default: `512000 bytes`

#### `name: string | undefined`

The name of the record that the avatar represents. If the `src` property does not specify an image, the component displays initials from the first and last words in the name. To ensure that the component extracts the correct initials, specify a name with no prefix or suffix, or just specify initials with a space between them. This property is not required, but the component requires either the `name` or `src` property.

#### `size: SkyAvatarSize | undefined`

The size of the avatar. Acceptable values are: `"small"`, `"medium"`, and `"large"`.

Default: `"large"`

#### `src: SkyAvatarSrc | undefined`

The image to identify a record. This property is not required, but the component requires either the `name` or `src` property.

### Outputs

#### `avatarChanged: EventEmitter<SkyFileItem>`

Emits a `SkyFileItem` object when the image is updated.

 SkyAvatarSize
--------------

Type: Type alias

    type SkyAvatarSize = "large" | "medium" | "small"

 SkyAvatarSrc
-------------

Type: Type alias

    type SkyAvatarSrc = string | Blob | File

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAvatarHarness
-----------------

Type: Class

`import { SkyAvatarHarness } from '@skyux/avatar/testing';`

Harness for interacting with an avatar component in tests.

### Methods

#### `closeError(): Promise<void>`

Closes the currently displayed error.

#### Returns

`Promise<void>`

#### `dropAvatarFile(file: File, waitForChange?: boolean): Promise<void>`

Simulates the user selecting or dropping an image onto the component.

#### Parameters

##### `file: File`

##### `waitForChange?: boolean`

#### Returns

`Promise<void>`

#### `getCanChange(): Promise<boolean>`

Gets whether users can change the image.

#### Returns

`Promise<boolean>`

#### `getInitials(): Promise<undefined | string>`

Gets the initials displayed when no image URL is specified.

#### Returns

`Promise<undefined | string>`

#### `getSrc(): Promise<undefined | string | Blob>`

Gets the avatar's current image URL or Blob.

#### Returns

`Promise<undefined | string | Blob>`

#### `hasFileTypeError(): Promise<boolean>`

Gets whether an error indicating an invalid file type is displayed.

#### Returns

`Promise<boolean>`

#### `hasMaxSizeError(): Promise<boolean>`

Gets whether an error indicating an invalid file size is displayed.

#### Returns

`Promise<boolean>`

#### `SkyAvatarHarness.with(filters: SkyAvatarHarnessFilters): HarnessPredicate<SkyAvatarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAvatarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAvatarHarnessFilters`

#### Returns

`HarnessPredicate<SkyAvatarHarness>`

 SkyAvatarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAvatarHarness](/skyux/components/avatar?docs-active-tab=examples#class_sky-avatar-harness.md) instances.

    interface SkyAvatarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Basic example

Edit in StackBlitz

Profile picture of Robert C. Hernandez

RH

Show code

Copy

    <sky-avatar
      data-sky-id="user-profile-avatar"
      [canChange]="true"
      [maxFileSize]="1000"
      [name]="name()"
      [src]="avatar()"
      (avatarChanged)="onAvatarChanged($event)"
    />
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyAvatarHarness } from '@skyux/avatar/testing';
    
    import { of } from 'rxjs';
    
    import { AvatarExampleComponent } from './example.component';
    import { DemoService } from './example.service';
    
    describe('Basic avatar harness', () => {
      let uploadAvatarSpy: jasmine.Spy;
    
      beforeEach(() => {
        uploadAvatarSpy = jasmine
          .createSpy('uploadAvatarSpy')
          .and.returnValue(of(undefined));
    
        TestBed.configureTestingModule({
          providers: [
            {
              provide: DemoService,
              useValue: {
                uploadAvatar: uploadAvatarSpy,
              },
            },
          ],
        });
      });
    
      async function setupTest(): Promise<{
        fixture: ComponentFixture<AvatarExampleComponent>;
        harness: SkyAvatarHarness;
      }> {
        const fixture = TestBed.createComponent(AvatarExampleComponent);
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const harness: SkyAvatarHarness = await loader.getHarness(
          SkyAvatarHarness.with({ dataSkyId: 'user-profile-avatar' }),
        );
    
        return { fixture, harness };
      }
    
      function createTestFile(fileSize: number): File {
        return new File(['a'.repeat(fileSize)], 'test.png', {
          type: 'image/png',
        });
      }
    
      it('should display the expected avatar image', async () => {
        const { harness } = await setupTest();
    
        await expectAsync(harness.getInitials()).toBeResolvedTo(undefined);
        await expectAsync(harness.getSrc()).toBeResolvedTo(
          'https://imgur.com/tBiGElW.png',
        );
      });
    
      it('should allow the user to change the avatar', async () => {
        const { harness } = await setupTest();
    
        await expectAsync(harness.getCanChange()).toBeResolvedTo(true);
      });
    
      it('should upload a new avatar and set the avatar src', async () => {
        const { harness } = await setupTest();
    
        const testFile = createTestFile(100);
    
        await harness.dropAvatarFile(testFile, true);
    
        expect(uploadAvatarSpy).toHaveBeenCalledOnceWith(testFile);
    
        await expectAsync(harness.getSrc()).toBeResolvedTo(jasmine.any(Blob));
      });
    
      it('should now allow files larger than 1,000 bytes', async () => {
        const { harness } = await setupTest();
    
        const maxFileSize = 1000;
    
        await harness.dropAvatarFile(createTestFile(maxFileSize));
        await expectAsync(harness.hasMaxSizeError()).toBeResolvedTo(false);
    
        await harness.dropAvatarFile(createTestFile(maxFileSize + 1));
        await expectAsync(harness.hasMaxSizeError()).toBeResolvedTo(true);
    
        await harness.closeError();
      });
    });
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, delay, of } from 'rxjs';
    
    @Injectable({
      providedIn: 'root',
    })
    export class DemoService {
      // eslint-disable-next-line @typescript-eslint/no-unused-vars
      public uploadAvatar(_file: File): Observable<void> {
        // Simulate uploading the file to a web service.
        return of(undefined).pipe(delay(500));
      }
    }

Copy

    import { Component, inject, signal } from '@angular/core';
    import { SkyAvatarModule } from '@skyux/avatar';
    import { SkyFileItem } from '@skyux/forms';
    
    import { DemoService } from './example.service';
    
    /**
     * @title Basic example
     */
    @Component({
      selector: 'app-avatar-example',
      templateUrl: './example.component.html',
      imports: [SkyAvatarModule],
    })
    export class AvatarExampleComponent {
      #exampleSvc = inject(DemoService);
    
      protected readonly avatar = signal<string | File>(
        'https://imgur.com/tBiGElW.png',
      );
      protected readonly name = signal('Robert C. Hernandez');
    
      protected onAvatarChanged(fileItem: SkyFileItem): void {
        /**
         * This is where you might upload the new avatar,
         * but for this example we'll just update it locally.
         */
        if (fileItem) {
          this.#exampleSvc.uploadAvatar(fileItem.file).subscribe(() => {
            this.avatar.set(fileItem.file);
          });
        }
      }
    }

# Testing

                   Skip to Main Content

 Avatar
======

The avatar component displays an image to identify a record.

 Installation
-------------

NPM package

`@skyux/avatar`[View in NPM](https://www.npmjs.com/package/@skyux/avatar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/avatar/src/lib/modules/avatar/avatar.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/avatar`Copy None found.

 SkyAvatarModule
----------------

Type: Module

`import { SkyAvatarModule } from '@skyux/avatar';`

 SkyAvatarComponent
-------------------

Type: Component

Selector: `sky-avatar`

### Inputs

#### `canChange: boolean`

Whether users can change the image. To select a different image, users click the image or drag another image on top of it, much like the `sky-file-drop` component in the [file attachment module](/skyux/components/file-attachments/file-attachment.md).

Default: `false`

#### `maxFileSize: number | undefined`

The maximum file size for the image in bytes.

Default: `512000 bytes`

#### `name: string | undefined`

The name of the record that the avatar represents. If the `src` property does not specify an image, the component displays initials from the first and last words in the name. To ensure that the component extracts the correct initials, specify a name with no prefix or suffix, or just specify initials with a space between them. This property is not required, but the component requires either the `name` or `src` property.

#### `size: SkyAvatarSize | undefined`

The size of the avatar. Acceptable values are: `"small"`, `"medium"`, and `"large"`.

Default: `"large"`

#### `src: SkyAvatarSrc | undefined`

The image to identify a record. This property is not required, but the component requires either the `name` or `src` property.

### Outputs

#### `avatarChanged: EventEmitter<SkyFileItem>`

Emits a `SkyFileItem` object when the image is updated.

 SkyAvatarSize
--------------

Type: Type alias

    type SkyAvatarSize = "large" | "medium" | "small"

 SkyAvatarSrc
-------------

Type: Type alias

    type SkyAvatarSrc = string | Blob | File

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAvatarHarness
-----------------

Type: Class

`import { SkyAvatarHarness } from '@skyux/avatar/testing';`

Harness for interacting with an avatar component in tests.

### Methods

#### `closeError(): Promise<void>`

Closes the currently displayed error.

#### Returns

`Promise<void>`

#### `dropAvatarFile(file: File, waitForChange?: boolean): Promise<void>`

Simulates the user selecting or dropping an image onto the component.

#### Parameters

##### `file: File`

##### `waitForChange?: boolean`

#### Returns

`Promise<void>`

#### `getCanChange(): Promise<boolean>`

Gets whether users can change the image.

#### Returns

`Promise<boolean>`

#### `getInitials(): Promise<undefined | string>`

Gets the initials displayed when no image URL is specified.

#### Returns

`Promise<undefined | string>`

#### `getSrc(): Promise<undefined | string | Blob>`

Gets the avatar's current image URL or Blob.

#### Returns

`Promise<undefined | string | Blob>`

#### `hasFileTypeError(): Promise<boolean>`

Gets whether an error indicating an invalid file type is displayed.

#### Returns

`Promise<boolean>`

#### `hasMaxSizeError(): Promise<boolean>`

Gets whether an error indicating an invalid file size is displayed.

#### Returns

`Promise<boolean>`

#### `SkyAvatarHarness.with(filters: SkyAvatarHarnessFilters): HarnessPredicate<SkyAvatarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAvatarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAvatarHarnessFilters`

#### Returns

`HarnessPredicate<SkyAvatarHarness>`

 SkyAvatarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAvatarHarness](/skyux/components/avatar?docs-active-tab=testing#class_sky-avatar-harness.md) instances.

    interface SkyAvatarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
                   

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
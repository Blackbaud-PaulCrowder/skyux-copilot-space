---
component: 'avatar'
type: 'api-documentation'
description: 'API documentation for the avatar component including components, interfaces, and types.'
---

# Avatar API Documentation

## Components and Directives

#### AvatarExampleComponent

**Selector:** `app-avatar-example`

**Package:** `@skyux/code-examples`

#### SkyAvatarComponent

**Selector:** `sky-avatar`

**Package:** `@skyux/avatar`

**Inputs:**

- `maxFileSize`: `number | undefined` - The maximum file size for the image in bytes. (default: 512000 bytes)
- `size`: `SkyAvatarSize | undefined` - The size of the avatar.
Acceptable values are: `"small"`, `"medium"`, and `"large"`. (default: "large")
- `canChange`: `boolean` - Whether users can change the image. To select a different image,
users click the image or drag another image on top of it,
much like the `sky-file-drop` component in the
[file attachment module](https://developer.blackbaud.com/skyux/components/file-attachments/file-attachment). (default: false)
- `name`: `string | undefined` - The name of the record that the avatar represents.
If the `src` property does not specify an image, the component displays
initials from the first and last words in the name. To ensure
that the component extracts the correct initials, specify a name with no prefix
or suffix, or just specify initials with a space between them. This property is
not required, but the component requires either the `name` or `src` property.
- `src`: `SkyAvatarSrc | undefined` - The image to identify a record. This property is
not required, but the component requires either the `name` or `src` property.

**Outputs:**

- `avatarChanged`: `EventEmitter<SkyFileItem>` - Emits a `SkyFileItem` object when the image is updated.

#### SkyPageHeaderAvatarComponent

Displays an avatar within the page header to the left of the page title.
If no size is specified for the avatar component it will display at size
small on xs breakpoints and size large on small and above breakpoints.

**Selector:** `sky-page-header-avatar`

**Package:** `@skyux/pages`
---
component: 'field-group'
type: 'api-documentation'
description: 'API documentation for the field-group component including components, interfaces, and types.'
---

# Field Group API Documentation

## Components and Directives

#### FormsFieldGroupBasicExampleComponent

**Selector:** `app-forms-field-group-basic-example`

**Package:** `@skyux/code-examples`

#### FormsFieldGroupHelpKeyExampleComponent

**Selector:** `app-forms-field-group-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyFieldGroupComponent

Organizes form fields into a group.

**Selector:** `sky-field-group`

**Package:** `@skyux/forms`

**Inputs:**

- `headingHidden`: `boolean` - Indicates whether to hide the `headingText`. (default: false)
- `headingLevel`: `SkyFieldGroupHeadingLevel` - The semantic heading level in the document structure. (default: 3)
- `headingText`: `string` - The text to display as the field group's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the field group heading. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the field group heading. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `hintText`: `string | undefined` - [Persistent inline help text](https://developer.blackbaud.com/skyux/design/guidelines/user-assistance#inline-help) that provides
additional context to the user.
- `stacked`: `boolean` - Whether the field group is stacked on another field group. When specified, the appropriate
vertical spacing is automatically added to the field group. (default: false)
- `headingStyle`: `SkyFieldGroupHeadingStyle` - The heading [font style](https://developer.blackbaud.com/skyux/design/styles/typography#headings). (default: 3)
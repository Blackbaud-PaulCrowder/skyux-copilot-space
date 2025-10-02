---
component: 'error'
type: 'api-documentation'
description: 'API documentation for the error component including components, interfaces, and types.'
---

# Error API Documentation

## Components and Directives

#### ActionBarsSummaryActionBarErrorExampleComponent

**Selector:** `app-action-bars-summary-action-bar-error-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorEmbeddedExampleComponent

**Selector:** `app-errors-error-embedded-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Package:** `@skyux/code-examples`

#### FormsInputBoxWithCustomFormErrorsExampleComponent

**Selector:** `app-forms-input-box-basic-example`

**Package:** `@skyux/code-examples`

#### ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Package:** `@skyux/code-examples`

#### SkyErrorActionComponent

Specifies an interactive element to include with the error message.
For example, you can include a button to reload the page or to refresh data.

**Selector:** `sky-error-action`

**Package:** `@skyux/errors`

#### SkyErrorDescriptionComponent

Specifies a description to provide additional details about the error.

**Selector:** `sky-error-description`

**Package:** `@skyux/errors`

**Inputs:**

- `replaceDefaultDescription`: `boolean | undefined` - Whether to replace the default description. If `false`, the content
from this component is added after the default description. (default: false)

#### SkyErrorImageComponent

Specifies an image to display with the error message.

**Selector:** `sky-error-image`

**Package:** `@skyux/errors`

#### SkyErrorTitleComponent

Specifies a title to display with the error message.

**Selector:** `sky-error-title`

**Package:** `@skyux/errors`

**Inputs:**

- `replaceDefaultTitle`: `boolean | undefined` - Whether to replace the default title. If `false`, the content
from this component is added after the default title. (default: false)

#### SkyErrorComponent

Displays a SKY UX-themed error message.

**Selector:** `sky-error`

**Package:** `@skyux/errors`

**Inputs:**

- `showImage`: `boolean | undefined` - Whether to display the error image. (default: true)
- `errorType`: `SkyErrorType | undefined` - The set of pre-defined values for the image,
title, and description.

#### SkyFormErrorComponent

Displays default and custom form field error messages for form field components.
Set `labelText` on the form field component to automatically display required,
maximum length, minimum length, date, email, phone number, time, and URL errors.
To display custom errors, include sky-form-error elements in the form field component.

**Selector:** `sky-form-error`

**Package:** `@skyux/forms`

**Inputs:**

- `errorName`: `string` - The name of the error.
- `errorText`: `string` - The error message to display.

#### SkyFormErrorsComponent

**Selector:** `sky-form-errors`

**Package:** `@skyux/forms`

**Inputs:**

- `dirty`: `boolean` - Indicates whether the parent component's control is dirty (default: false)
- `errors`: `null | ValidationErrors | undefined` - The validation errors from the form control.
- `labelText`: `string | undefined` - Input label text to display in the error messages.
- `touched`: `boolean` - Indicates whether the parent component's control is touched (default: false)
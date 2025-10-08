            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Form design](/skyux/design/guidelines/form-design.md)

Form design
===========

Form design patterns provide guidance to accommodate a wide variety scenarios and workflow requirements.

On this page
============

1.  [Form containers](/skyux/design/guidelines/form-design#form-containers.md)
2.  [Form layout](/skyux/design/guidelines/form-design#form-layout.md)
3.  [Field usability](/skyux/design/guidelines/form-design#field-usability.md)
4.  [Selection inputs](/skyux/design/guidelines/form-design#selection-inputs.md)
5.  [Validation and error handling](/skyux/design/guidelines/form-design#validation-and-error-handling.md)
6.  [Unsaved data](/skyux/design/guidelines/form-design#unsaved-data.md)
7.  [Related information](/skyux/design/guidelines/form-design#related-information.md)

[

Form containers
---------------

](/skyux/design/guidelines/form-design#form-containers.md)

### Inline form

An [inline form](/skyux/components/inline-form.md) is appropriate for simple forms that meet the following criteria:

*   The form has few fields, its input controls are not complex, and it does not cause significant page morphing.
*   The content that surrounds the form will not distract users.
*   The task is functionally non-modal.

### Modal dialog

A [modal dialog](/skyux/components/modal.md) is appropriate for forms that meet any of the following criteria:

*   The task is functionally modal, and users must finish it before doing anything else.
*   Displaying the form inline would lead to substantial content shifting or require users to scroll to complete the form.
*   The form adds records from a paginated list or an infinite scroll list.

### Full-screen modal

A [full-screen modal](/skyux/components/modal.md) is appropriate for forms that meet the following criteria:

*   The task is functionally modal, and users must finish it before doing anything else.
*   Users usually perform the task in a large viewport, and a full-page modal can optimize the use of space.
*   The context of the task is self-contained.
*   The form displays feedback based on users entering data or making choices. For example, the form may display running totals or preview emails as they are constructed.
*   The form supports a complex task for a list of objects such as filling out report cards for a class.
*   The task includes subtasks that need to be completed in context.

### Sectioned form

A [sectioned form](/skyux/components/sectioned-form.md) is appropriate for forms that meet the following criteria:

*   Users add or edit complex objects and can be expected to know what they are looking for. This is common for editing pieces of larger records and for tasks such as applying filters.
*   It's beneficial to group related but independent forms to minimize the number of form-launching buttons on a page.

Sectioned forms are not appropriate when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

### Wizard

A [wizard](/skyux/components/tabs-wizard.md) is appropriate for forms that meet the following criteria:

*   The task can be divided into discrete steps that are completed in a single sitting. If a task is more than six steps, try to refactor the task into fewer steps or split it into multiple tasks.
*   The order of the steps is important.
*   The interaction complexity of each step is low.
*   User actions in earlier steps affect later steps.
*   Users must complete or review the fields in every step.

[

Form layout
-----------

](/skyux/design/guidelines/form-design#form-layout.md)

Form fields generally flow vertically, and [input boxes](/skyux/components/input-box.md) and other SKY UX form field components provide styling, ordering, and positioning within forms. To add bottom margins that ensure consistent vertical spacing between form fields, use `stacked` in most cases.

Don't use `stacked` when a form field:

*   Is the last field before a [field group](/skyux/components/field-group.md)
*   Is the last field on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

On small, medium, and large [modals](/skyux/components/modal.md), form fields should generally extend the full width of the modal. The most common exception is closely related fields, such as first and last name fields, that can flow horizontally. For a horizontal flow, use a [fluid grid](/skyux/components/fluid-grid.md) layout with `gutterSize=”small”` to provide horizontal margins and ensure that the form scales properly to smaller viewports.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-1.9c5fb738cc3acb80690aede56c460330.png)

The most common multi-column layouts are 1/2 width (6 [fluid grid](/skyux/components/fluid-grid.md) columns) and 1/3 width (4 fluid grid columns). However, single-line inputs can use different column widths when the form fields are related and the expected length of user input is predictable.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-2.5.b204424deec6825c7dc012679d3432b2.png)

Inputs can use unbalanced column widths to match highly predictable lengths of user input.

Checkboxes and radio buttons should generally be full width. However, when the labels are short and predictable, groups of checkboxes or radio buttons can be used in 1/2 or 1/3 width [fluid grids](/skyux/components/fluid-grid.md) next to similar groups. Don't use this layout to display checkbox or radio button groups beside other types of form fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-2.75.e7972f2eae2fbe93610f354f98f01698.png)

Checkbox and radio button groups with short labels can be displayed horizontally.

### Field groups

To separate forms into groups or sections, use [field groups](/skyux/components/field-group.md). This component wraps form fields in semantic and visual groups with headings. To provide consistent vertical spacing between field groups, use `stacked`. This adds a bottom margin to visually separate a field group from another field group or other form content below it.

Don't use `stacked` when a field group is the last content on a form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-2.db5179b8d1d56bae1058dea10359954a.png)

When forms require subsections, you can nest field groups inside other field groups. Adjust the field group's `headingLevel` and `headingStyle` to make the heading maintain the semantic and visual hierarchy of the form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-3.e88550cd29eb119a6e9c5cfbf1ca9050.png)

Use heading level and heading style to maintain the form hierarchy when creating subsections with nested field groups.

Don't use a field group when the only content is a lone [checkbox group](/skyux/components/checkbox.md) or [radio button group](/skyux/components/radio.md). For more details, see the layout guidelines for those components.

### Sub-forms

If alternate workflows are not feasible, it's acceptable to launch modal forms from within modal forms. For scenarios that require sub-forms, such as when users need to add multiple instances of a child record, follow the form container guidelines above.

If you do not save sub-form data until users save the underlying form, then change the submit button's label from Save to Done to indicate that the data is not saved.

### Conditional fields

Sometimes, forms include conditional fields that are only applicable when certain conditions are met. For example, conditional fields may only be applicable when users select a specific checkbox or select a particular value in a lookup field.

*   For three or fewer conditional fields, display but disable the fields when conditions are not met.
*   For more than three conditional fields, hide the fields until conditions are met.
*   If the majority of form content is conditional, use a different workflow. For example, you can start a workflow with [action buttons](/skyux/components/action-button.md) and then present relevant content based on user selections.
*   Don't use `stacked` when a form field is followed by one or more conditional fields. Instead, add the `sky-margin-stacked-sm` class to follow spacing guidelines for closely related fields. To determine whether to use `stacked` on the conditional fields themselves, follow the component guidelines.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-form-layout-4.a3540b808ac8ce2b4653f8b53d406f44.png)

[

Field usability
---------------

](/skyux/design/guidelines/form-design#field-usability.md)

### Labels

All fields require labels to tell users what information to provide..

*   Be concise. Limit labels to a few words
*   Use nouns or noun phrases. Don't use questions, commands, or other complete sentences.
*   Use sentence-style capitalization.
*   Don't use colons or other punctuation at the end of labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/usability-labels-do.8ff830479a6b92f29448ff413a49a723.png)

Do use labels to succinctly indicate the purpose of fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/usability-labels-dont.dd122d91223981d3f55daa129ce11353.png)

Don't use questions, commands, or other complete sentences as labels.

### Hint text

To highlight essential considerations about fields, use hint text. [Input box](/skyux/components/input-box.md) and other SYK UX form field components automatically handle the placement of hint text. Use hint text sparingly to emphasize details that help users complete fields and avoid errors, such as:

*   Required formats
*   Field constraints
*   Vital instructions or context

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-field-usability-3.612ce9c0cf8721d262c169209cbe2798.png)

Do use hint text to highlight key details, such as required formats.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-field-usability-4.36c6fadd9fcf5b4da1b6c85c7897ec57.png)

Do use hint text to inform users about field constraints.

Avoid overuse to ensure that hint text retains its impact and doesn't clutter forms. For longer help text or supplementary information that isn't essential, use [help buttons](/skyux/components/help-inline.md) instead to invoke user assistance.

*   Be concise. Limit hint text to 1 or 2 short sentences.
*   In general, use complete sentences, but you can use sentence fragments for brevity when the meaning is clear.

### Help inline button

To invoke inline help for form fields, use `helpKey` on [input box](/skyux/components/input-box.md) and other SKY UX form field components. The components automatically handle the placement of a [help inline button](/skyux/components/help-inline.md) next to the field label. Use help inline buttons when contextual user assistance is too long for hint text or provides supplementary information that doesn't require persistent inline help.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-design-hint-text.a6138d8590dcdc6f180d720e2613035d.png)

Don't use hint text for lengthy or supplementary user assistance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/usability-help-button-do.5ec20c098ac8d73c583b1574d6864393.png)

Do use a help inline button for lengthy or supplementary user assistance.

### Placeholder text

Don't use placeholder text within fields because it causes usability and accessibility issues. To highlight important considerations about fields, use hint text instead.

### Suggested text

To provide suggested text that helps users with data entry on common fields, you can use the HTML `autocomplete` attribute. Place this attribute on `input`, `textarea`, and `select` elements instead of using the [SKY UX autocomplete component](/skyux/components/autocomplete.md).

Browsers provide suggested text based on previous entries, so `autocomplete` is most helpful for personal information, such as names and addresses, that users enter in multiple places. Don't use `autocomplete` when browsers are unlikely to provide useful suggested text, such as for fields that request information about other users.

### Inline help

For information about whether to use persistent inline help or invoked inline help content, see the [user assistance guidelines](/skyux/design/guidelines/user-assistance.md).

[

Selection inputs
----------------

](/skyux/design/guidelines/form-design#selection-inputs.md)

You can take several different approaches to allow users to select items from lists.

*   [Checkboxes](/skyux/components/checkbox.md) are effective when users can select multiple items from a short list. Use checkboxes to present one to five items.
*   [Radio buttons](/skyux/components/radio.md) are effective when users can select a single item from a short list. Use radio buttons to present two to five items.
*   The HTML `<select>` field is effective when users are not sure of the exact value they are looking for and can select a single item from a moderately sized list. Use HTML `<select>` fields to present six to 20 items.
*   The [lookup field](/skyux/components/lookup.md) provides a typeahead search input that is effective when users know what they are looking for and can select multiple items. Use lookup fields to present very large lists.

[

Validation and error handling
-----------------------------

](/skyux/design/guidelines/form-design#validation-and-error-handling.md)

### Validation timing

Notify users about errors in forms as soon as you are certain that errors occurred. This lets users correct errors within the flow of their tasks rather than at the end when they think they are done, and it avoids interruptions that can distract users and cause errors.

Follow these guidelines on validation timing for different situations to help users complete forms successfully while also avoiding interruptions.

#### Validation when focus leaves

For most form fields, use validation when focus leaves the fields (i.e., `onblur`). This increases the probability that users completed the fields and avoids interrupting user input.

#### Live validation when typing

In rare cases, use live validation to provide immediate feedback that interrupts users while typing. Use this validation sparingly in the following cases:

1.  When real-time feedback helps users meet field constraints such as password strength, availability, and character count.
2.  When live validation can avoid unnecessary typing because user inputs definitely won't meet the required formats. You must determine the points after which to validate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/validation-do.f326599fd513672c300bf429e2e2c5da.png)

Do validate fields during typing when you can be certain that input is incorrect.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/validation-dont.dd6f4d552b513b2d7365682c36e34b06.png)

Don't validate fields when users are typing if you can't be certain that input is incorrect.

#### Re-validation and removing errors

After an error message is displayed for an input, use live validation to give users real-time feedback while they fix the issue. This saves time and effort because users don't need to exit the field to check if they fixed the error.

#### Validation on submit

Ideally, errors are caught before users submit forms, but you can validate on submit as a final check and to handle validation that can only happen on the server.

### Required field marker

When a SKY UX form field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. SKY UX form fields automatically display as required when the component is bound to a form control that is required, either via `ngModel` and the `required` HTML attribute, or via an Angular `FormControl` with the built-in `Validators.required` validator.

The [sectioned form](/skyux/components/sectioned-form.md) component includes a property to display the red asterisk in the tab panel of tabs that contain required fields.

### Other validation

Use the validation that is available in the [date range picker](/skyux/components/date-range-picker.md), [datepicker](/skyux/components/datepicker.md), [email validation](/skyux/components/email-validation.md), [file attachment](/skyux/components/file-attachments.md), [phone field](/skyux/components/phone-field.md), [timepicker](/skyux/components/timepicker.md), and [URL validation](/skyux/components/url-validation.md) components when you collect those types of data. You can also create custom validation as necessary.

### Error states and messages

SKY UX form field components automatically update their style and display an error message when they are in an error state.

Error messages are necessary to explain how to correct errors. Avoid generic messages, such as "This field is required." Instead, use more specific messages that explain how to resolve the errors, such as "Enter a first name." or "Enter a valid email address."

Focus error messages on what users need to do instead of what they did wrong. For example, use "Limit \[item\] to 50 characters." instead of "\[Item\] text cannot exceed 50 characters." Avoid humor in error messages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/field-level-error.00f877631ebb43390c371a055ec10a21.png)

The [sectioned form](/skyux/components/sectioned-form.md) component includes a property to display a danger icon in the tab panel of tabs that contain fields with validation errors.

### Form-level errors

If form content fails to load, follow the [error handling guidelines](/skyux/design/guidelines/error-handling.md) for the relevant page-level element.

If form-level actions such as Save break, display an error message using `SkyModalError`. For details, see the Development tab of the [modal](/skyux/components/modal.md) component.

If form-level actions make form fields invalid, place focus on the first invalid field. When the error isn't visible, this scrolls to ensure that users can see where to address the error.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/form-errors.ccfc9d691197807c70967bc685974c14.png)

[

Unsaved data
------------

](/skyux/design/guidelines/form-design#unsaved-data.md)

If users close a form before saving their changes, warn them about the unsaved data with a [confirmation dialog](/skyux/components/confirm.md). For modals, see the Development tab of the [component docs](/skyux/components/modal.md) for details on how to use `SkyModalIsDirtyDirective`.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/modal-close-confirm.f756192fa9878ff34249421a094c4aa3.png)

[

Related information
-------------------

](/skyux/design/guidelines/form-design#related-information.md)

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Confirmation dialog](/skyux/components/confirm.md)
*   [Date range picker](/skyux/components/date-range-picker.md)
*   [Datepicker](/skyux/components/datepicker.md)
*   [Email validation](/skyux/components/email-validation.md)
*   [Error](/skyux/components/error.md)
*   [File attachment](/skyux/components/file-attachment.md)
*   [File drop](/skyux/components/file-drop.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Inline form](/skyux/components/inline-form.md)
*   [Input box](/skyux/components/input-box.md)
*   [Modal](/skyux/components/modal.md)
*   [Phone field](/skyux/components/phone-field.md)
*   [Radio button](/skyux/components/radio.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Text editor](/skyux/components/text-editor.md)
*   [Timepicker](/skyux/components/timepicker.md)
*   [URL validation](/skyux/components/url-validation.md)
*   [Wizard](/skyux/components/tabs-wizard.md)
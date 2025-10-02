---
component: 'modal'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the modal component extracted from SKY UX documentation.'
---

# Modal Design Guidelines

## Component Overview
The modal component and service launch modals in a consistent way in SKY UX applications.

## Usage

### ✅ Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

Use modals when users need to add records from paginated lists or infinite scroll lists.

Use large modals when housing a large component that best utilizes the horizontal space, such as sectioned forms or wizards.

### ✅ Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

## Anatomy

- Heading
- Content
- Footer
- Buttons
- Help inline button

## Options

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a help inline button beside the header to invoke contextual user assistance.

## Behavior and states

### Unsaved data

If users close a modal before saving their changes, use SkyModalIsDirtyDirective to warn them about losing the unsaved data with a confirmation dialog.

## Content

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

### Buttons in the modal action bar

## Related information

### Components

- Buttons
- Confirmation dialog
- Input box

### Guidelines

- Form design
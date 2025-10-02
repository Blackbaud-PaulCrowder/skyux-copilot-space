---
component: 'sectioned-form'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the sectioned-form component extracted from SKY UX documentation.'
---

# Sectioned Form Design Guidelines

## Component Overview
Sectioned forms combine multiple forms and display large amounts of related information inside large modals.

## Usage

### ✅ Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen modals to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### ❌ Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized modals because the component requires the horizontal space that large-sized and full-screen modals provide.

## Behavior

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

## Related information

### Guidelines

- Form design
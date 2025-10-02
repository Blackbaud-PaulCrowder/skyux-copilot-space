---
component: 'confirm'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the confirm component extracted from SKY UX documentation.'
---

# Confirm Design Guidelines

## Component Overview
The confirm service launches simple confirmation dialogs that prompt users to confirm actions.

## Usage

### ✅ Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

### ❌ Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

## Anatomy

- Modal
- Heading
- Actions
- Body text

## Options

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

- A primary button triggers the recommended or most-common action.
- A secondary button triggers a less-common action.
- A link button cancels the action.
- Each button closes the dialog.

###### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the sky-btn-danger style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

## Content

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

- Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
- Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

## Related information

### Guidelines

- Form design
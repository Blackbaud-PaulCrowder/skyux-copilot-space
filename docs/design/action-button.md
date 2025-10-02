---
component: 'action-button'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the action-button component extracted from SKY UX documentation.'
---

# Action Button Design Guidelines

## Component Overview
Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

## Usage

### ✅ Use when

Use actions buttons when:

- Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different selection input and interaction.
- Methods of completion are system-defined, not user-defined.
- Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
- The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

### ❌ Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

## Behavior and states

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

- Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.
- Center the action buttons inside the modal and wrap to another row if needed.
- When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.
- If users cancel or abandon the task, do not return to the modal.
- Always provide a "Cancel" action inside a modal with action buttons.

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

- If necessary, include a question above the action buttons to explain the decision being made.
- Center the question and action buttons inside the page.
- When users select one of the action buttons, replace them with the next step of the task.
- If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.
- If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

- A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.
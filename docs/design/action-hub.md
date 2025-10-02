---
component: 'action-hub'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the action-hub component extracted from SKY UX documentation.'
---

# Action Hub Design Guidelines

## Component Overview
Action hubs direct user attention to important actions and provide quick access to common tasks. They aggregate entry points into tasks that might otherwise be spread across multiple pages.

## Usage

### ✅ Use when

Use action hubs to present prescriptive calls to action for things users must, should, or could do within an area of the system. They are often appropriate as landing pages for main navigation items but can also be descendant pages.

### ❌ Don't use when

Don't use action hubs to present information that is not actionable. Analyze information for users to provide context and make it actionable.

## Anatomy

- Page heading
- Related links
- Needs attention
- Recently accessed
- Content area
- Common actions
- Settings

## Options

### Common actions

You can include up to three secondary buttons to provide quick access to common tasks, such as adding a record. If you need to group multiple related actions, use a menu button.

## Content

### Needs attention

Display actions that users must perform based on business requirements or best practices, and link users to the place where they can complete the action, such as a modal, split view page, or record page.

Start each item in the list with a verb that communicates the action to perform. After the verb, include the number of items that require attention and a succinct description.

Order the items by workflow order, or by importance if they are not part of the same workflow.

### Content area

Additional content should reflect one of the following sets of principles.

###### Operational but optional

Content that is operational but optional should:

- be operational in nature, reflecting work that the user does on a regular basis to run the business
- provide contextual information to help the user decide whether to act
- be elevated to a needs attention item after a specific threshold is met

###### Strategic and prescriptive

Content that is strategic and prescriptive should:

- be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
- prescribe one or more actions which may take place inside or outside the system
- be synthesized and provide a context for comparison — don't require the user to figure out what the information means

###### Strategic and tied to a needs attention item

Content that is strategic and tied to a needs attention item should:

- be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
- represent progress towards an outcome that is impacted by a least one existing needs attention item
- be synthesized and provide a context for comparison — don't require the user to figure out what the information means

###### Key information call to action

Use key information calls to action when the condition for prescribing an action can be distilled to a single piece of information.

###### Charts

Action hubs are not intended for analytical tasks. If you include charts, scope the data set to the appropriate strategic or operational view for the user. You can use one filter if necessary to swap between relevant contexts.

### Page links

Groups of links to include and display in the following order.

###### Related links

Display up to 10 links to related pages in alphabetical order.

###### Recently accessed

Display up to five items in reverse chronological order to indicate what users accessed most recently.

###### Settings

Optionally include links to the settings applicable to functionality within the action hub and its descendant pages.

## Behavior and states

### Needs attention

###### Navigation

Link needs attention items to the place where users can complete the action, such as a modal, split view page, or record page.

###### Empty state

When no needs attention items are available, an empty state message indicates that users are caught up.

###### Columns

When more than six needs attention items are available in a viewpoint that is 768 pixels or larger, the content splits into two columns.

### Settings

Open settings forms in modals.

### Responsiveness

Action hubs reflow content in small viewports.

## Related information

### Guidelines

- Record page
- Split view page

### Components

- Modal
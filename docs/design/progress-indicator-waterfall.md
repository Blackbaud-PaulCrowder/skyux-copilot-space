---
component: 'progress-indicator-waterfall'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the progress-indicator-waterfall component extracted from SKY UX documentation.'
---

# Progress Indicator Waterfall Design Guidelines

## Component Overview
Waterfall progress indicators walk users through sequential steps in lengthy or complex tasks.

## Usage

### ✅ Use when

Use waterfall progress indicators for long or complex setup processes with at least three steps that users typically complete only once. Waterfall indicators are ideal when events outside of the system force users to complete tasks in multiple sittings or when users must enter large amounts of data.

Use waterfall progress indicators when the complexity of steps varies drastically. For example, one step may require a full-screen modal for complex interactions, while another step requires a small modal for a few simple inputs. Waterfall steps can open wizards if necessary.

### ❌ Don't use when

Don't use waterfall progress indicators when users monitor a sequence of events but are not responsible for completing the steps. Use passive progress indicators instead.

Don't use waterfall progress indicators when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting. Use wizards instead.

Don't use waterfall progress indicators when processes include fewer than three steps or when the number or order of steps may change. If early decisions branch in different directions, arrange the workflow so that users make those decisions before the progress indicator.

Don't use waterfall progress indicators to edit properties after completing configuration processes. Use modals instead.

If configuration properties are interrelated and require users to reexamine all or most properties, then reframe the editing task as “starting over” and restart the waterfall process.

## Anatomy

- Waterfall title
- Step indicator
- Step label
- Completed step action
- Active step action
- Step details
- Help inline button
- Start-over action

## Options

### Waterfall title

We strongly recommend including a waterfall title to reflect the context of the overall task. Do not use a left-aligned page title when you include a waterfall title. The waterfall title does not change when users progress through the waterfall steps.

### Help inline button

When you need to supplement a waterfall title with additional information but don't require persistent inline help, you can place a help inline button beside the title to invoke contextual user assistance.

### Step details

You can provide additional details about completed steps, but limit details to single pieces of information. Don't go overboard because users can reopen modals to review choices as necessary.

### Start-over action

You can include a start-over action to let users erase all saved data from the waterfall process. This returns users to the first step or to an earlier point in the workflow if decisions occurred before the waterfall progress indicator.

## Behavior & states

Waterfall progress indicators guide users through one active step at a time. When users complete a step, the progress indicator updates its step indicator and step action to the completed state and updates the next step indicator and step action to the active state. Users can review and edit completed steps, but this does not undo the completed state.

The final step summarizes the changes and requests user confirmation. You do not need to include all data that users enter in the summary, but confirmation is required. After users complete the final step, replace the waterfall progress indicator with a page that displays the finished or active state of the system.

## Content

Use a waterfall title in place of an ordinary page title to provide context for the overall task. Follow the same pattern as modal titles and start the waterfall title with a verb that indicates the action that occurs when users complete the waterfall steps.

For step labels, start with a number and concisely describe the objective using the <verb> <direct object> format. In the label for the last step, describe the cumulative change that occurs at the end of the process.

Step action (button) labels closely follow step labels and use the same <verb> <direct object> format, but they do not need to be identical. For the first step action label, be generic and conversational (“Get started”), and for completed step actions, use verbs appropriate to post hoc actions (“Change”, “Edit”).

### Layout

Waterfall progress indicators are 400 pixels wide and centered inside the page. The waterfall title is the page title. Do not combine waterfall indicators with other content or actions. If waterfall indicators require extra context such as descriptions, links, or instructions, include it after the waterfall title and before the first step.

## Related information

### Components

- Help inline button
- Modal
- Passive progress indicator
- Wizard (Tabs)

### Guidelines

- Form design
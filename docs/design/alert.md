---
component: 'alert'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the alert component extracted from SKY UX documentation.'
---

# Alert Design Guidelines

## Component Overview
Alerts highlight critical information that users absolutely must see when they visit a page.

## Usage

### ✅ Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

### ❌ Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use labels or status indicators instead.

Don't use alerts to display messages about the success or failure of user actions. Use toasts instead.

## Anatomy

- Alert icon
- Text
- Close button

## Options

### Alert type

Use the danger alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

Use the warning alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

Use the success alert for messages that convey a positive or successful state.

Use the info alert for messages that provide helpful information or context but do not require user action.

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

## Content

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

## Layout

Always place alerts at the top of the page above the page header.

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

## Related information

### Components

- Label
- Status indicator
- Toast

### Guidelines

- Call out information
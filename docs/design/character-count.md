---
component: 'character-count'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the character-count component extracted from SKY UX documentation.'
---

# Character Count Design Guidelines

## Component Overview
The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.

## Usage

### ✅ Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

### ❌ Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use normal form validation instead.

## Anatomy

- Input field
- Status indicator (danger)
- Character count indicator

## Options

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

## Behavior and states

The character count indicator component extends the form classes that define styles and the appearance of input field states.

## Content

## Layout

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

## Related information

### Components

- Input box

### Guidelines

- Form design
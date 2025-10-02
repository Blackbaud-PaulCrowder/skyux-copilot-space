---
component: 'inline-delete'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the inline-delete component extracted from SKY UX documentation.'
---

# Inline Delete Design Guidelines

## Component Overview
The inline delete confirmation appears when users delete an item in a list and requires them to confirm that they want to delete the item.

## Usage

### ✅ Use when

Use the inline delete confirmation when users need to confirm that they want to delete an item from a list.

Keep in mind that you should not delete items from lists when they are complex enough to have their own record pages. For lists with such items, do not include delete actions in the context-menu dropdowns.

### ❌ Don't use when

Don't use inline delete confirmation when users need to confirm that they want to delete an item outside of a list. Use a confirm dialog instead.

## Anatomy

- Delete button
- Cancel button
- Overlay

## Behavior and states

### Delete button

The inline delete confirmation uses the sky-btn-danger (red) style for the Delete button to visually indicate that the action deletes existing data.

## Related information

### Components

- Confirm
- Dropdown

### Guidelines

- Manage records
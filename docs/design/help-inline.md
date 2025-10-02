---
component: 'help-inline'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the help-inline component extracted from SKY UX documentation.'
---

# Help Inline Design Guidelines

## Component Overview
The help inline button beside a field or other item lets users display more information about that item.

## Usage

### ✅ Use when

Use help inline buttons to invoke help content that users don't need to see every time or that is too long for persistent inline help. This provides access to supplementary information while avoiding most of the visual noise that comes with persistent inline help.

Use help inline buttons when users may need initial assistance but:

- The tasks are performed frequently.
- Ramifications of mistakes are small.

### ❌ Don't use when

Don't use help inline buttons when a small amount of persistent inline text can help users understand tasks. Use persistent inline help instead when:

- Tasks are complex and performed infrequently.
- User actions have far-reaching consequences that are not obvious.

## Options

### Popover

Display help content in popovers when a small amount of user assistance content is valuable some of the time. For larger amounts of user assistance, use the helpKey option instead to display content in a flyout or in the help widget, which is for internal Blackbaud use only.

### Help widget or other container

For longer help content that doesn't fit in popovers, use the helpKey option. Blackbaud developers use helpKey to open content in the help widget, which is for internal Blackbaud use only, and it can be also launch content in other containers, such as flyouts or new windows. To launch content from help inline buttons, see global help.

## Layout

### Page-level and modal-level help

For complex tasks where users need comprehensive documentation, they invoke help at the page or modal level.

In Blackbaud solutions, users invoke help from the omnibar or a modal heading. To display context-sensitive help content, Blackbaud developers use the help widget, which is for internal Blackbaud use only.

### Element-level help

Place the help inline button to the right of the label for the element that the help content supports.

## Related information

### Guidelines

- Form design

### Components

- Box
- Data entry grid
- Data grid
- Description list
- File attachment
- File drop
- Flyout
- Input box
- Key info
- Modal
- Passive progress indicator
- Popover
- Single file attachment
- Status indicator
- Text editor
- Tile
- Toggle switch
- Waterfall progress indicator
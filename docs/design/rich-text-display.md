---
component: 'rich-text-display'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the rich-text-display component extracted from SKY UX documentation.'
---

# Rich Text Display Design Guidelines

## Component Overview
The rich text display sanitizes HTML strings before displaying them. It searches HTML for any malicious code, such as script tags, and removes it as necessary. This allows you to safely display HTML strings from various sources.

## Usage

### ✅ Use when

Use rich text display to safely display read-only rich text.

### ❌ Don't use

Don't use rich text display anywhere users enter or edit rich text. Use the text editor component instead.

## Related information

### Components

- Text editor
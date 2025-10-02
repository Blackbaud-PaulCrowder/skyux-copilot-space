---
component: 'tile'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the tile component extracted from SKY UX documentation.'
---

# Tile Design Guidelines

## Component Overview
Tiles create flexible containers to display content or features from external sources inside SKY UX applications.

## Usage

### ✅ Use when

Use tiles to display content or features from external sources on the Add-ins tab of record pages . As extension points in the SKY Add-ins framework, tiles are the primary container for external content in SKY UX applications. You can use a tile dashboard to automatically size and arrange tiles and to let users reorder or collapse/expand tiles to meet their specific needs.

For more information, see the SKY Add-ins documentation for tiles .

### ❌ Don't use when

Don't use tiles to organize native Blackbaud content and features or to define content categories within SKY UX applications. On record pages use boxes within fluid grids instead.

Don't use tiles to organize content within modals. For complex forms, use sectioned forms or other form containers instead.

## Anatomy

- Header
- Title
- Expand/collapse button
- Drag handle
- Content area
- Help inline button
- Settings button

## Options

### Help inline button

When you need to supplement a tile with additional information but don't require persistent inline help, you can place a help inline button beside the title to invoke contextual user assistance.

### Settings button

Show the settings button on a tile when users need to access add-in settings, authentication for connected services, or other configuration options. This button can launch whatever pattern is appropriate, such as opening a modal or a separate browser tab.

## Content

### Empty state

For tiles that are not populated, use empty-state help to explain how to use the tile.

## Related information

### Components

- Box
- Help inline button

### Guidelines

- Content containers
- Page design
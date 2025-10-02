---
component: 'error'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the error component extracted from SKY UX documentation.'
---

# Error Design Guidelines

## Component Overview
The error component displays a SKY UX-themed error message.

## Usage

### ✅ Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

Use error messages when the content inside modals fails to load.

### ❌ Don't use when

Don't use error messages to display information about background processes. Use toasts instead.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use alerts instead.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

## Anatomy

- Title
- Image
- Description
- Action

## Options

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

Use the under construction error type when pages are under maintenance or experience known outages.

Use the not found error type when pages fail to load because of 404 errors.

Use the security error type when users don't have access to view content.

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

## Content

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

## Layout

## Related Information

### Components

- Alert
- Toast

### Guidelines

- Error handling
- Form design
- User assistance
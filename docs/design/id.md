---
component: 'id'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the id component extracted from SKY UX documentation.'
---

# Id Design Guidelines

## Component Overview
The ID directive assigns a unique ID to an element and provides that ID to other elements.

## Usage

### ✅ Use when

Use the ID directive when one HTML element must be associated with another HTML element by its id attribute. For example, input and label elements must be associated by a unique ID so that clicking on the label sets focus to the input. Associating a label to its input also enables assistive technologies to describe the input to the user using the label text.

### ❌ Don't use when

Don't use the ID directive when an element does not need to be referenced by its ID attribute because doing so adds unnecessary overhead to an application.

Don't assign hard-coded IDs to elements because this causes collisions if IDs are not unique. Always use the ID directive to assign IDs because it guarantees that IDs are unique.
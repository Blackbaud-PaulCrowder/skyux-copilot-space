---
component: 'progress-indicator-passive'
description: 'Design guidelines, API documentation, and usage instructions for the progress-indicator-passive component extracted from SKY UX documentation.'
---

# Progress Indicator Passive Component Guidelines

## Component Overview
Passive progress indicators represent sequential steps in processes outside of user control.

## Usage

### ✅ Use when

Use passive progress indicators when users must be aware of sequential progress that they are not responsible for.

**✅ Do use passive progress indicators to track sequential steps that other users take.**

### ❌ Don't use when

Don't use passive progress indicators for tasks that require user interaction. Use waterfall progress indicators or wizards instead.

**❌ Don't use passive progress indicators when users must take action on any of the steps.**

Don't use passive progress indicators to represent independent steps or statuses that are not sequential.

**❌ Don't use passive progress to track steps that are not sequential.**

Don't use passive progress indicators simultaneously for multiple items in lists.

**❌ Don't display multiple passive progress indicators in lists.**

## Anatomy

- Completed step indicator
- Pending step indicator
- Step label
- Help inline button
- Step details

## Options

### Step details

You can provide additional details about completed or current steps. Use step details to provide extra context to users, but avoid too many details or the implication that users should take action.

## Content

## Layout

## Related information

### Components

- Flyout
- Help inline button
- Popover
- Waterfall progress indicator
- Wizard (Tabs)

### Guidelines

- Calling out information

## API Documentation

### Components and Directives

#### ProgressIndicatorPassiveIndicatorBasicExampleComponent

**Selector:** `app-progress-indicator-passive-indicator-basic-example`

**Package:** `@skyux/code-examples`

### Code Examples

#### Passive progress indicator

**Selector:** `app-progress-indicator-passive-indicator-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyProgressIndicatorModule } from '@skyux/progress-indicator';

/**
 * @title Passive progress indicator
 */
@Component({
  selector: 'app-progress-indicator-passive-indicator-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyProgressIndicatorModule],
})
export class ProgressIndicatorPassiveIndicatorBasicExampleComponent {}

```

**Template:**

```html
<sky-progress-indicator
  data-sky-id="example-progress-indicator"
  [isPassive]="true"
  [startingIndex]="1"
>
  <sky-progress-indicator-item
    data-sky-id="finished-step"
    helpPopoverContent="Example help content for finished step"
    helpPopoverTitle="Start here"
    title="Finished step"
    >Optional details about this step
  </sky-progress-indicator-item>
  <sky-progress-indicator-item
    helpPopoverContent="Example help content for current step"
    title="Current step"
  />
  <sky-progress-indicator-item title="HIDDEN TITLE" />
</sky-progress-indicator>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
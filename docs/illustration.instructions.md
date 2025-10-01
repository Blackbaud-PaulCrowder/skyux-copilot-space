---
component: 'illustration'
description: 'Design guidelines, API documentation, and usage instructions for the illustration component extracted from SKY UX documentation.'
---

# Illustration Component Guidelines

## Component Overview
Spot illustrations orient users and focus their attention across various experiences.

## Usage

### ✅ Use when

Use spot illustrations to focus user attention and shape visual hierarchy. Refer to the spot illustration design guidelines page to learn about their principles and role.

**✅ Do use spot illustrations for illustrative purposes.**

### ❌ Don't use when

Don't use spot illustrations as a visual shorthand to supplement action labels. Use icons instead.

**❌ Don't use spot illustrations in place of icons.**

## Options

### Size

Spot illustrations have four sizes: small, medium, large, and extra large.

**Spot illustrations have four size variations.**

## Layout

### Background color

Spot illustrations are duotone and use Blackbaud's color palette. To ensure clarity, only use them on light backgrounds.

### Alignment

To maintain visual balance, align spot illustrations vertically or horizontally with other elements, such as text, in the components and patterns where they appear.

**You can align spot illustrations horizontally to the left of other elements.**

### Standard layouts

To maintain visual balance, use SKY UX spacing values to separate elements.

#### Box call-to-action

Use small spot illustrations in this horizontal layout to draw user attention to important actions.

**Spacing for left-aligned illustrations and text.**

#### Welcome page

Use large spot illustrations within boxes to anchor content on welcome pages.

**Spacing values should scale with illustration size.**

#### Split view empty state

Use medium spot illustrations in this vertical layout when split view lists include no remaining items.

**Spacing for center-aligned illustrations and text.**

## Spot illustration library

## Requesting a spot illustration

### 1. Determine what to communicate

Some user experiences require spot illustrations to communicate literal ideas, while others use them to tell stories or elicit emotion. The context and intent help determine the appropriate spot illustration for a user experience.

### 2. Select an illustration

Select the appropriate spot illustration from the Streamline Duotone library. Illustrations in the library are in spec mode and may not reflect final colors.

### 3. File a request form

Submit an illustration request in ADO.

## Related information

### Components

- Box
- Icon

### Guidelines

- Page design

## API Documentation

### Components and Directives

#### IndicatorsIllustrationBasicExampleComponent

**Selector:** `app-indicators-illustration-basic-example`

**Package:** `@skyux/code-examples`

#### SkyIllustrationResolverService

Resolves information about spot illustrations.

**Package:** `@skyux/indicators`

#### SkyIllustrationSize

**Package:** `@skyux/indicators`

#### SkyIllustrationComponent

Displays a spot illustration at the specified size.

**Selector:** `sky-illustration`

**Package:** `@skyux/indicators`

**Inputs:**

- `name`: `InputSignal<string>` - The name of the illustration to display. **[Required]**
- `size`: `InputSignal<SkyIllustrationSize>` - The size of the illustration. **[Required]**

#### SkyIllustrationModule

**Package:** `@skyux/indicators`

#### SkyIllustrationHarnessFilters

A set of criteria that can be used to filter a list of `SkyIllustrationHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyIllustrationHarness

Harness for interacting with an illustration component in tests.

**Package:** `@skyux/indicators/testing`

### Code Examples

#### Spot illustration with basic setup

**Selector:** `app-indicators-illustration-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import {
  SkyIllustrationModule,
  SkyIllustrationResolverService,
} from '@skyux/indicators';

import { IllustrationDemoResolverService } from './illustration-demo-resolver.service';

/**
 * @title Spot illustration with basic setup
 */
@Component({
  selector: 'app-indicators-illustration-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyIllustrationModule],
  // This service is provided here as an example; your implementation of `SkyIllustrationResolverService`
  // should be provided at the application level.
  providers: [
    {
      provide: SkyIllustrationResolverService,
      useClass: IllustrationDemoResolverService,
    },
  ],
})
export class IndicatorsIllustrationBasicExampleComponent {}

```

**Template:**

```html
<sky-illustration
  data-sky-id="illustration-example"
  name="analytics-graph"
  size="md"
/>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
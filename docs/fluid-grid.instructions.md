---
component: 'fluid-grid'
description: 'Design guidelines, API documentation, and usage instructions for the fluid-grid component extracted from SKY UX documentation.'
---

# Fluid Grid Component Guidelines

## Component Overview
The fluid grid component provides a responsive 12-column layout to organize content for all device sizes.

## Related information

### Guidelines

- Form design
- Page design
- Spacing

## API Documentation

### Components and Directives

#### LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Package:** `@skyux/code-examples`

#### SkyFluidGridComponent

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the
alignment, padding, and margins do not behave as expected.

**Selector:** `sky-fluid-grid`

**Package:** `@skyux/layout`

**Inputs:**

- `disableMargin`: `boolean | undefined` - Disables the outer left and right margin of the fluid grid container. (default: false)
- `gutterSize`: `SkyFluidGridGutterSizeType` - The type that defines the size of the padding
between columns. (default: "large")

#### SkyFluidGridModule

**Package:** `@skyux/layout`

#### SkyFluidGridGutterSizeType

**Package:** `@skyux/layout`

#### SkyFluidGridHarnessFilters

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyFluidGridHarness

Harness for interacting with a fluid grid component in tests.

**Package:** `@skyux/layout/testing`

### Code Examples

#### Fluid grid with basic setup

**Selector:** `app-layout-fluid-grid-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyFluidGridGutterSizeType, SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Fluid grid with basic setup
 */
@Component({
  selector: 'app-layout-fluid-grid-example',
  templateUrl: './example.component.html',
  styles: [
    `
      .highlight-columns .sky-column {
        background-color: #97eced;
        border: 1px solid #56e0e1;
        overflow-wrap: break-word;
      }
    `,
  ],
  imports: [SkyFluidGridModule],
})
export class LayoutFluidGridExampleComponent {
  public gutterSize: SkyFluidGridGutterSizeType | undefined;
  public disableMargin = false;
}

```

**Template:**

```html
<div class="highlight-columns">
  <sky-fluid-grid
    data-sky-id="fluid-grid"
    [disableMargin]="disableMargin"
    [gutterSize]="gutterSize"
  >
    <sky-row data-sky-id="test-row">
      <sky-column data-sky-id="test-column" [screenSmall]="1">
        [screenSmall]="1"
      </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="5"> [screenSmall]="5" </sky-column>
      <sky-column [screenSmall]="7"> [screenSmall]="7" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="8"> [screenSmall]="8" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="9"> [screenSmall]="9" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="10"> [screenSmall]="10" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="11"> [screenSmall]="11" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column
        data-sky-id="dynamic-column"
        [screenXSmall]="6"
        [screenSmall]="8"
        [screenMedium]="9"
        [screenLarge]="10"
      >
        [screenXSmall]="6" [screenSmall]="8" [screenMedium]="9"
        [screenLarge]="10"
      </sky-column>
      <sky-column
        [screenXSmall]="6"
        [screenSmall]="4"
        [screenMedium]="3"
        [screenLarge]="2"
      >
        [screenXSmall]="6" [screenSmall]="4" [screenMedium]="3"
        [screenLarge]="2"
      </sky-column>
    </sky-row>

    <sky-row data-sky-id="reverse-row" [reverseColumnOrder]="true">
      <sky-column [screenSmall]="4"> First column </sky-column>
      <sky-column [screenSmall]="4"> Second column </sky-column>
      <sky-column [screenSmall]="4"> Third column </sky-column>
    </sky-row>
  </sky-fluid-grid>
</div>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
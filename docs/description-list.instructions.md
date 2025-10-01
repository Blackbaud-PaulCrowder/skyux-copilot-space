---
component: 'description-list'
description: 'Design guidelines, API documentation, and usage instructions for the description-list component extracted from SKY UX documentation.'
---

# Description List Component Guidelines

## Component Overview
Description lists display scannable data that pair terms with descriptions.

## Usage

### ✅ Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

Use description lists in longDescription mode to display glossaries or other data where the descriptions are complete sentences or longer.

### ❌ Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use key info or other methods to call out information instead.

Don't use description lists when users can understand data based on its context and don't need a label.

## Anatomy

- Term
- Description
- Help inline button

## Options

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a help inline button beside the term to invoke contextual user assistance.

## Behavior and states

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

## Content

Don't use colons or other punctuation after description list terms.

## Layout

### Horizontal lists

Use horizontal mode to display up to 6 term-description pairs in description lists that stand alone.

### Vertical lists

Use vertical mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a fluid grid to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

## Related information

### Components

- Fluid grid
- Help inline button
- Key info

### Guidelines

- Call out information

## API Documentation

### Components and Directives

#### LayoutDescriptionListHelpKeyExampleComponent

**Selector:** `app-layout-description-list-help-key-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListHorizontalExampleComponent

**Selector:** `app-layout-description-list-horizontal-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListInlineHelpExampleComponent

**Selector:** `app-layout-description-list-inline-help-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListLongDescriptionExampleComponent

**Selector:** `app-layout-description-list-long-description-example`

**Package:** `@skyux/code-examples`

#### LayoutDescriptionListVerticalExampleComponent

**Selector:** `app-layout-description-list-vertical-example`

**Package:** `@skyux/code-examples`

#### SkyDescriptionListContentComponent

Wraps the term-description pairs in the description list.

**Selector:** `sky-description-list-content`

**Package:** `@skyux/layout`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
placed beside the description list content label. Clicking the button invokes global help as configured by the application.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the description list content. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.

#### SkyDescriptionListDescriptionComponent

Specifies the description in a term-description pair.

**Selector:** `sky-description-list-description`

**Package:** `@skyux/layout`

#### SkyDescriptionListTermComponent

Specifies the term in a term-description pair. To display a help button beside
the term, include a help button element in the sky-description-list-term element
and a sky-control-help CSS class on that element.

**Selector:** `sky-description-list-term`

**Package:** `@skyux/layout`

#### SkyDescriptionListComponent

Creates a description list to display term-description pairs.

**Selector:** `sky-description-list`

**Package:** `@skyux/layout`

**Inputs:**

- `listItemWidth`: `string | undefined` - The width of term-description pairs when `mode` is set to `"horizontal"`. By default,
the width is responsive based on the width of the container element.
- `defaultDescription`: `string` - The default description to display when no description is provided
for a term-description pair. (default: "None found")
- `mode`: `SkyDescriptionListModeType` - How to display term-description pairs within the description list. (default: "vertical")

#### SkyDescriptionListModule

**Package:** `@skyux/layout`

#### SkyDescriptionListModeType

How to display the term-description pairs within a description list.

**Package:** `@skyux/layout`

#### SkyDescriptionListMode

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyDescriptionListContentHarness

Harness for interacting with a description list content component in tests.

**Package:** `@skyux/layout/testing`

#### SkyDescriptionListHarnessFilters

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyDescriptionListHarness

Harness for interacting with a description list component in tests.

**Package:** `@skyux/layout/testing`

### Code Examples

#### Description list with help key

**Selector:** `app-layout-description-list-help-key-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Description list with help key
 */
@Component({
  selector: 'app-layout-description-list-help-key-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListHelpKeyExampleComponent {
  protected items: { term: string; description: string; helpKey?: string }[] = [
    {
      term: 'College',
      description: 'Humanities and Social Sciences',
      helpKey: 'college-help',
    },
    {
      term: 'Department',
      description: 'Anthropology',
    },
    {
      term: 'Advisor',
      description: 'Cathy Green',
    },
    {
      term: 'Class year',
      description: '2024',
    },
  ];
}

```

**Template:**

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpKey]="item.helpKey">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

#### Horizontal mode

**Selector:** `app-layout-description-list-horizontal-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Horizontal mode
 */
@Component({
  selector: 'app-layout-description-list-horizontal-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListHorizontalExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];
}

```

**Template:**

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

#### Description list with inline help

**Selector:** `app-layout-description-list-inline-help-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Description list with inline help
 */
@Component({
  selector: 'app-layout-description-list-inline-help-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule, SkyHelpInlineModule],
})
export class LayoutDescriptionListInlineHelpExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];

  protected onActionClick(): void {
    alert('Help inline button clicked!');
  }
}

```

**Template:**

```html
<sky-description-list mode="horizontal">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
        <sky-help-inline
          ariaLabel="Information about {{ item.term }}"
          class="sky-control-help"
          (actionClick)="onActionClick()"
        />
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

#### Long-description mode

**Selector:** `app-layout-description-list-long-description-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Long-description mode
 */
@Component({
  selector: 'app-layout-description-list-long-description-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListLongDescriptionExampleComponent {
  protected items: { term: string; description: string }[] = [
    {
      term: 'Good Health and Well-being',
      description:
        'Ensure healthy lives and promote well-being for all at all ages.',
    },
    {
      term: 'Quality Education',
      description:
        'Ensure inclusive and equitable quality education and promote lifelong learning opportunities for all.',
    },
    {
      term: 'Gender Equity',
      description: 'Achieve gender equality and empower all women and girls.',
    },
  ];
}

```

**Template:**

```html
<sky-description-list mode="longDescription">
  @for (item of items; track item) {
    <sky-description-list-content>
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

#### Vertical mode

**Selector:** `app-layout-description-list-vertical-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Vertical mode
 */
@Component({
  selector: 'app-layout-description-list-vertical-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule],
})
export class LayoutDescriptionListVerticalExampleComponent {
  protected items: { term: string; description: string; helpText?: string }[] =
    [
      {
        term: 'College',
        description: 'Humanities and Social Sciences',
      },
      {
        term: 'Department',
        description: 'Anthropology',
      },
      {
        term: 'Advisor',
        description: 'Cathy Green',
        helpText: 'The faculty member who advises the student.',
      },
      {
        term: 'Class year',
        description: '2024',
      },
    ];
}

```

**Template:**

```html
<sky-description-list mode="vertical">
  @for (item of items; track item) {
    <sky-description-list-content [helpPopoverContent]="item.helpText">
      <sky-description-list-term>
        {{ item.term }}
      </sky-description-list-term>
      <sky-description-list-description>
        {{ item.description }}
      </sky-description-list-description>
    </sky-description-list-content>
  }
</sky-description-list>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
---
component: 'definition-list'
description: 'Design guidelines, API documentation, and usage instructions for the definition-list component extracted from SKY UX documentation.'
---

# Definition List Component Guidelines

## Component Overview
Definition lists display label-value pairs. Definition list is deprecated in favor of description list. For more information, see the definition list deprecation instructions.

## Content

## Related information

### Components

- Alert
- Toolbar

## API Documentation

### Components and Directives

#### LayoutDefinitionListBasicExampleComponent

**Selector:** `app-layout-definition-list-basic-example`

**Package:** `@skyux/code-examples`

#### SkyDefinitionListContentComponent

Wraps the label-value pairs in the definition list.

**Selector:** `sky-definition-list-content`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyDefinitionListHeadingComponent

Specifies a title for the definition list.

**Selector:** `sky-definition-list-heading`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyDefinitionListLabelComponent

Specifies the label in a label-value pair.

**Selector:** `sky-definition-list-label`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyDefinitionListValueComponent

Specifies the value in a label-value pair.

**Selector:** `sky-definition-list-value`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyDefinitionListComponent

Creates a definition list to display label-value pairs.

**Selector:** `sky-definition-list`

**Package:** `@skyux/layout`

**Inputs:**

- `defaultValue`: `string | undefined` - The default value to display when no value is provided
for a label-value pair. (default: "None found")
- `labelWidth`: `string | undefined` - The width of the label portion of the definition list. (default: "90px")

⚠️ **This component is deprecated.**

#### SkyDefinitionListModule

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

### Code Examples

#### Definition list with basic setup

**Selector:** `app-layout-definition-list-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyDefinitionListModule } from '@skyux/layout';

/**
 * @title Definition list with basic setup
 */
@Component({
  selector: 'app-layout-definition-list-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDefinitionListModule],
})
export class LayoutDefinitionListBasicExampleComponent {
  protected items: { label: string; value?: string }[] = [
    {
      label: 'Field 1',
      value: 'Field 1 value',
    },
    {
      label: 'Field 2',
      value: 'Field 2 value',
    },
    {
      label: 'Field 3',
      value: undefined,
    },
    {
      label: 'Field 4',
      value: 'Field 4 value',
    },
  ];
}

```

**Template:**

```html
<sky-definition-list>
  <sky-definition-list-heading>
    Definition list heading
  </sky-definition-list-heading>
  @for (item of items; track item) {
    <sky-definition-list-content>
      <sky-definition-list-label>
        {{ item.label }}
      </sky-definition-list-label>
      <sky-definition-list-value>
        {{ item.value }}
      </sky-definition-list-value>
    </sky-definition-list-content>
  }
</sky-definition-list>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
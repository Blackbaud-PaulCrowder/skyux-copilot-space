---
component: 'rich-text-display'
description: 'Design guidelines, API documentation, and usage instructions for the rich-text-display component extracted from SKY UX documentation.'
---

# Rich Text Display Component Guidelines

## Component Overview
The rich text display sanitizes HTML strings before displaying them. It searches HTML for any malicious code, such as script tags, and removes it as necessary. This allows you to safely display HTML strings from various sources.

## Usage

### ✅ Use when

Use rich text display to safely display read-only rich text.

**✅ Do use rich text display to show rich text content in read-only contexts.**

### ❌ Don't use

Don't use rich text display anywhere users enter or edit rich text. Use the text editor component instead.

## Related information

### Components

- Text editor

## API Documentation

### Components and Directives

#### TextEditorRichTextDisplayExampleComponent

**Selector:** `app-text-editor-rich-text-display-example`

**Package:** `@skyux/code-examples`

#### SkyRichTextDisplayComponent

**Selector:** `sky-rich-text-display`

**Package:** `@skyux/text-editor`

**Inputs:**

- `richText`: `string | undefined` - The rich text to display.

#### SkyRichTextDisplayModule

**Package:** `@skyux/text-editor`

### Code Examples

#### Rich text display with basic setup

**Selector:** `app-text-editor-rich-text-display-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyRichTextDisplayModule } from '@skyux/text-editor';

/**
 * @title Rich text display with basic setup
 */
@Component({
  selector: 'app-text-editor-rich-text-display-example',
  templateUrl: './example.component.html',
  imports: [SkyRichTextDisplayModule],
})
export class TextEditorRichTextDisplayExampleComponent {
  protected richText = `<font style="font-size: 18px" face="Arial" color="#a25353"><b>Exclusively committed to your impact</b></font><p>Since day one, Blackbaud has been 100% focused on driving impact for social good organizations.</p><p>We equip change agents with <b>cloud software</b>, <i>services</i>, <u>expertise</u>, and <font color="#a25353">data intelligence</font> designed with unmatched insight and supported with unparalleled commitment. Every day, our <b>customers</b> achieve unmatched impact as they advance their missions.</p><ul><li><a href="#">Build a better world</a></li><li><a href="#">Explore our solutions</a></li></ul>`;
}

```

**Template:**

```html
<sky-rich-text-display [richText]="richText" />

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.
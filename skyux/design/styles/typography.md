             Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Typography](/skyux/design/styles/typography.md)

Typography
==========

SKY UX supports a set of semantically defined classes for text to ensure consistent usage and to maintain visual hierarchy of type. Components generally incorporate text classes as necessary, but you may find cases where you need to apply classes directly. Styling values in the table below are for reference only; you should apply styling through the use of the classes.

[

Headings
--------

](/skyux/design/styles/typography#headings.md)

Use headings to describe sections of content or as titles of containers. In most cases, use `<h1>` - `<h5>` elements for their corresponding heading styles. In rare cases, you may also use the classes listed below to apply heading styles. For example, you can use `<h2>` for semantic reasons, but change its style to `class="sky-font-heading-3"` to fit the visual hierarchy of a page.

For accessibility reasons, do not skip over heading levels. For example, do not use `<h1>` and `<h3>` on a page without `<h2>` between them.

### Heading 1

BLKB Sans  
1.6875rem #112b55

Use this class for page titles and record names. Use this class on only one element per page.

*   `<h1>`
*   `class="sky-font-heading-1"`

Warning: Deprecated class

`class="sky-page-heading"`

### Heading 2

BLKB Sans Semibold  
1.1875rem #112b55

Use this class for headings of sections or subdivisions on a page, such as box titles.

*   `<h2>`
*   `class="sky-font-heading-2"`

Warning: Deprecated class

`class="sky-section-heading"`

### Heading 3

BLKB Sans Semibold  
1.0625rem #112b55

Use this class for headings of subsections within containers.

*   `<h3>`
*   `class="sky-font-heading-3"`

Warning: Deprecated class

`class="sky-subsection-heading"`

### Heading 4

BLKB Sans Semibold  
0.9375rem #112b55

Use this class for smaller headings on a page.

*   `<h4>`
*   `class="sky-font-heading-4"`

### Heading 5

BLKB Sans Semibold  
0.9375rem #112b55

Use this class for the smallest headings on a page.

*   `<h5>`
*   `class="sky-font-heading-5"`

[

Body copy
---------

](/skyux/design/styles/typography#body-copy.md)

Use body copy for the majority of text on a page.

### Default body copy

BLKB Sans  
0.9375rem #252b33

`class="sky-font-body-default"`

### Large body copy

BLKB Sans  
1.0625rem #252b33

`class="sky-font-body-lg"`

### Small body copy

BLKB Sans  
0.8125 #252b33

`class="sky-font-body-sm"`

[

Display fonts
-------------

](/skyux/design/styles/typography#display-fonts.md)

Use display fonts to call attention to particularly important information.

### Display 1

BLKB Sans Semibold  
48px #252b33

`class="sky-font-display-1"`

### Display 2

BLKB Sans Semibold  
28px #252b33

`class="sky-font-display-2"`

### Display 3

BLKB Sans Semibold  
20px #252b33

`class="sky-font-display-3"`

Warning: Deprecated class

`class="sky-headline"`

### Display 4

BLKB Sans Semibold  
16px #252b33

`class="sky-font-display-4"`

[

Miscellaneous
-------------

](/skyux/design/styles/typography#miscellaneous.md)

### Emphasized

BLKB Sans Semibold  
0.9375rem #252b33

This class adds extra emphasis to body copy text. Use it in a `<strong>` element to semantically communicate importance or urgency.

`class="sky-font-emphasized"`

Warning: Deprecated class

`class="sky-emphasized"`

### Deemphasized

BLKB Sans Italic  
0.9375rem #666b70

This class formats text to de-emphasize ancillary information, such as persistent inline help text.

`class="sky-font-deemphasized"`

Warning: Deprecated class

`class="sky-deemphasized"`

Data label

BLKB Sans  
0.9375rem #666b70

This class formats labels for read-only data. It uses a muted color because the label that identifies the data is less important than the content.

`class="sky-font-data-label"`

Warning: Deprecated class

`class="sky-field-label"`
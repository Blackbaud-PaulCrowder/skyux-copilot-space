             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Spacing](/skyux/design/styles/spacing.md)

Spacing
=======

SKY UX provides two spacing approaches that can be used together when laying out content: [fluid grid](/skyux/components/fluid-grid.md) and spacing classes. Fluid grid works well when laying out containers and sections within containers, and the spacing classes work well when laying out content within sections.

Horizontal spacing with fluid grid
----------------------------------

The [fluid grid](/skyux/components/fluid-grid.md) component provides a responsive 12-column layout to organize content for all device sizes. You can apply different gutters between columns to use space efficiently and prevent elements from running together visually.

### Small gutters

2x0.5 = 1rem

Use small gutters to separate content in containers when that content has visible borders. For example:

*   Side-by-side input boxes in modals

`gutterSize="small"`

### Medium gutters

2x0.75 = 1.5rem

Use medium gutters containers with visible borders in large areas, such as pages. For example:

*   Boxes on pages

`gutterSize="medium"`

### Large gutters

2x1.5 = 3rem

Use large gutters to separate content or containers in large areas, such as pages, when the content or containers do not have visible borders.

`gutterSize="large"`

Horizontal spacing with classes
-------------------------------

When content or container widths are not dynamic, use spacing classes instead of [fluid grid](/skyux/components/fluid-grid.md). The amount of vertical spacing depends on the relationship between elements.

### Inline-xs

margin-right: 0.25rem

Closely related elements have a small margin to stay visually linked. For example:

*   Status indicator icons and labels
*   Button icons and labels

`class="sky-margin-inline-xs"`

Warning: Deprecated class

`class="sky-margin-inline-compact"`

### Inline-sm

margin-right: 0.5rem

Multiple related elements need enough horizontal spacing to be distinguished from each other but still visually linked. For example:

*   Toolbar buttons
*   Help inline buttons

`class="sky-margin-inline-sm"`

Warning: Deprecated class

`class="sky-margin-inline-default"`

### Inline-lg

margin-right: 1rem

Related form inputs require limited horizontal margins to distinguish elements from each other while remaining visually linked. For example:

*   Related form inputs

`class="sky-margin-inline-lg"`

### Inline-xl

margin-right: 1.5rem

Sections of loosely related content require additional horizontal spacing to prevent elements from running together visually. For example:

*   Subsections of content within a container
*   Bordered containers of content

`class="sky-margin-inline-xl"`

### Inline-xxl

margin-right: 3rem

Borderless sections of loosely related content and sections of unrelated content require significant horizontal spacing to prevent elements from running together visually. For example:

*   Sections of page content with no borders

`class="sky-margin-inline-xxl"`

Vertical spacing
----------------

### Stacked-xs

margin-bottom: 0.25rem

Closely related elements require tight vertical margins to visually link the elements. For example:

*   Data labels and their related values

`class="sky-margin-stacked-xs"`

Warning: Deprecated class

`class="sky-margin-stacked-compact"`

### Stacked-sm

margin-bottom: 0.5rem

Related elements require small vertical margins to visually link the elements. For example:

*   Small headers and text content underneath
*   Stacked block buttons

`class="sky-margin-stacked-sm"`

### Stacked-lg

margin-bottom: 1rem

Multiple related elements require limited vertical margins to distinguish elements from each other while remaining visually linked. For example:

*   Input boxes
*   Description list

`class="sky-margin-stacked-lg"`

Warning: Deprecated class

`class="sky-margin-stacked-default"`

### Stacked-xl

margin-bottom: 1.5rem

Sections of loosely related content require extra vertical spacing to prevent them from running together visually. For example:

*   Subsections of content within a container
*   Bordered containers

`class="sky-margin-stacked-xl"`

Warning: Deprecated class

`class="sky-margin-stacked-separate"`

### Stacked-xxl

margin-bottom: 3rem

Borderless sections of loosely related content and sections of unrelated content require significant vertical spacing to prevent elements from running together visually. For example:

*   Sections of page content with no borders

`class="sky-margin-stacked-xxl"`

Container padding
-----------------

Containers require padding to set their content away from the container edge. The amount of padding differs based on the size of the container. In general, SKY UX components handle padding for you.

### Padding-md

padding: 0.75rem

Small containers within larger containers require less padding to set the content apart from its surroundings because the larger containers already have padding. For example:

*   Alert
*   Popover

`class="sky-padding-even-md"`

Warning: Deprecated class

`class="sky-padding-even-default"`

### Padding-xl

padding: 1.5rem

Large containers often run near the edge of the viewport, so significant padding is necessary to prevent the content from feeling crunched. For example:

*   Box
*   Modal
*   Page

`class="sky-padding-even-xl"`

Warning: Deprecated class

`class="sky-padding-even-large"`
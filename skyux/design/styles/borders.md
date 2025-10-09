             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Borders and shadows](/skyux/design/styles/borders.md)

Borders and shadows
===================

SKY UX uses various border and shadow styles to bound, divide, and highlight content. The styles are designed to maintain visual hierarchy regardless of how complex pages become or how many nested containers they include.

As with other types of formatting or decoration in SKY UX, use lines minimally. Remember that white space and positioning can group or highlight content without extra subdivisions or boundaries.

Borders and lines
-----------------

In general, components handle borders and line styles.

### Border separator

1px solid #bac5d8

The border separator is a single-pixel line for borders between major page elements.

*   `class="sky-border-bottom-dark"`
*   `class="sky-border-dark"`

### Row separator

1px solid #cad2e1

The row separator is a line with slightly reduced visual weight. It separates items in lists, such as rows in grids or repeaters.

`class="sky-border-bottom-row"`

### Rounded corners

border-radius: 0.25rem

Rounded corners are used on containers and interactive elements.

`class="sky-rounded-corners"`

Elevation
---------

In general, components handle the use of elevation. The elevation level determines the appearance of its shadow.

### Elevation 0

border: 1px solid #cad2e1

For no elevation and a border on containers placed within other containers, such as containers nested in [boxes](/skyux/components/box.md).

`class="sky-elevation-0-bordered"`

### Elevation 1

box-shadow:  
0 1px 3px 0 rgba(33, 44, 63, 0.2),  
0 2px 1px -1px rgba(33, 44, 63, 0.12),  
0 1px 1px 0 rgba(33, 44, 63, 0.14);

For slightly raised elevation to give a subtle emphasis to elements that don't use the container background color.  
  
Examples: [alerts](/skyux/components/alert.md) and [avatars](/skyux/components/avatar.md)

`class="sky-elevation-1"`

### Elevation 1 bordered

border: 1px solid #cad2e1  
box-shadow:  
0 1px 3px 0 rgba(33, 44, 63, 0.2),  
0 2px 1px -1px rgba(33, 44, 63, 0.12),  
0 1px 1px 0 rgba(33, 44, 63, 0.14);

For slightly raised elevation and a border to give a subtle emphasis to elements that use the container background color.  
  
Examples: [boxes](/skyux/components/box.md) and [tiles](/skyux/components/tile.md)

`class="sky-elevation-1-bordered"`

### Elevation 3

box-shadow:  
0 1px 8px 0 rgba(33, 44, 63, 0.2),  
0 3px 3px -2px rgba(33, 44, 63, 0.12),  
0 3px 4px 0 rgba(33, 44, 63, 0.14)

For elements that stay in view on scroll to appear above scrolling content.  
  
Examples: [back to top](/skyux/components/back-to-top.md) and [summary action bar](/skyux/components/summary-action-bar.md)

`class="sky-elevation-3"`

### Elevation 4

box-shadow:  
0 2px 4px -1px rgba(33, 44, 63, 0.2),  
0 1px 10px 0 rgba(33, 44, 63, 0.12),  
0 4px 5px 0 rgba(33, 44, 63, 0.14);

For a small overlay elevation on temporal elements that are easily dismissed.  
  
Examples: [popovers](/skyux/components/popover.md), [dropdown](/skyux/components/dropdown.md) menus, and picker inputs

`class="sky-elevation-4"`

### Elevation 8

box-shadow:  
0 5px 5px -3px rgba(33, 44, 63, 0.2),  
0 3px 14px 2px rgba(33, 44, 63, 0.12),  
0 8px 10px 1px rgba(33, 44, 63, 0.14);

For an overlay elevation that gives more emphasis to larger elements that are used in conjunction with the main page.  
  
Example: [flyouts](/skyux/components/flyout.md)

`class="sky-elevation-8"`

### Elevation 16

box-shadow:  
0 8px 10px -5px rgba(33, 44, 63, 0.2),  
0 6px 30px 5px rgba(33, 44, 63, 0.12),  
0 16px 24px 2px rgba(33, 44, 63, 0.14);

For floating overlays that require clear visual separation. Use for interruptive elements.  
  
Examples: [modals](/skyux/components/modal.md) and [toasts](/skyux/components/toast.md)

`class="sky-elevation-16"`
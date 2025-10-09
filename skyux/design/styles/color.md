             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Colors](/skyux/design/styles/color.md)

Colors
======

As a general rule, SKY UX uses color to convey meaning and not as pure decoration. You should rarely apply colors directly to elements because components incorporate colors as necessary. If a need for color arises outside of a component, you likely need to create a component for that scenario.

Each color has a corresponding [CSS custom property](https://developer.mozilla.org/en-US/docs/Web/CSS/--*) declared at the document's [root](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) element. You can use these custom properties with the [CSS `var()` function](https://developer.mozilla.org/en-US/docs/Web/CSS/var) as values in your own CSS classes.

Text
----

Ensure that the contrast between the text color and the background color is at least 4.5:1 to meet Web Content Accessibility Guidelines 2.1 level AA.

### Default text color

#252b33

The default color for text. `--sky-text-color-default`

### Deemphasized text color

#666b70

The color for deemphasized text, such as content labels and help text. `--sky-text-color-deemphasized`

### Text on dark background

#ffffff

The color for text on dark backgrounds, such as primary and danger button labels. `--sky-text-color-on-dark`

### Action text

#2b6bd5

Text color for links and link buttons. `--sky-text-color-action-primary`

Backgrounds
-----------

### Page background

#f1f3f7

The background color for pages. `--sky-background-color-page-default`

### Light background

#f1f3f7

The background color for elements that need to contrast with the containers they hold, such as a tile dashboard. `--sky-background-color-neutral-light`

### Container background

#ffffff

The background color for container elements, such as tile or box. `--sky-background-color-container-default`

### Primary action background

#2b6bd5

The background color for elements that invoke primary actions, such as primary buttons. `--sky-background-color-primary-dark`

### Disabled action background

#eeeeef

The background color for disabled interactive elements. `--sky-background-color-disabled`

### Selected element background

#eef3fc

The background color for selected elements. `--sky-background-color-input-selected`

### Info background light

#eef3fc

The background color for selected filters. `--sky-background-color-info-light`

### Info background

#d5e1f7

The background color for elements that convey an "info" status, such as alerts or labels. `--sky-background-color-info`

### Success background

#9ef0c7

The background color for elements that convey a "success" status, such alerts or labels. `--sky-background-color-success`

### Warning background

#fddfae

The background color for elements that convey a "warning" status, such as alerts or labels. `--sky-background-color-warning`

### Danger background

#f0b0b1

The background color for elements that convey a "danger" status, such as alerts or labels. `--sky-background-color-danger`

### Danger background dark

#d93a3d

The background color for buttons that invoke primary actions that are destructive, such as deleting an item. `--sky-background-color-danger-dark`

Highlights
----------

### Info highlight

#2b6bd5

The highlight color for elements that convey an "information" status, such as alerts or labels. `--sky-highlight-color-info`

### Success highlight

#0aa959

The highlight color for elements that convey a "success" status, such as alerts or labels. `--sky-highlight-color-success`

### Warning highlight

#fbb034

The highlight color for elements that convey a "warning" status, such as alerts or labels. `--sky-highlight-color-warning`

### Danger highlight

#d93a3d

The highlight color for elements that convey a "danger" status, such as alerts or labels. `--sky-highlight-color-danger`

Borders
-------

### Medium border

#cad2e1

The color for borders that separate containers from their surroundings. `--sky-border-color-neutral-medium`

### Medium dark border

#7289af

The color for borders of inputs or controls with no internal text, such as checkboxes or radio buttons. `--sky-border-color-neutral-medium-dark`

Categorization
--------------

Use categorization colors to categorize blocks of content when the distinction between types of content is significant to users. For example, use categorization colors for different types of events in calendars.

### Category green

#9ef0c7

The background color for categorized content. `--sky-category-color-green`

### Category teal

#6ad8d4

The background color for categorized content. `--sky-category-color-teal`

### Category purple

#dfc0fa

The background color for categorized content. `--sky-category-color-purple`

### Category orange

#f9a366

The background color for categorized content. `--sky-category-color-orange`

### Category blue

#99ecff

The background color for categorized content. `--sky-category-color-blue`

### Category yellow

#fddfae

The background color for categorized content. `--sky-category-color-yellow`

### Category red

#f0b0b1

The background color for categorized content. `--sky-category-color-red`

Data visualization
------------------

### Categorical palette

Use the categorical palette in charts and other data visualizations to differentiate categories and other data. For example, use categorical colors to distinguish the slices in a pie chart or the bars in a bar chart. Use categorical colors in their intended order, with light purple as the color of the first category in a visualization, dark purple as the next color, and so on.

Categorical colors are visually distinct, and all 12 meet 3:1 contrast on white backgrounds. The light purple, dark purple, orange, dark green, and green colors also meet 3:1 contrast with one another.

### Light purple

#B061F2

The color for the first category in a visualization.

### Dark purple

#490285

The color for the second category in a visualization.

### Orange

#DC7821

The color for the third category in a visualization.

### Dark green

#004F35

The color for the fourth category in a visualization.

### Green

#04A87D

The color for the fifth category in a visualization.

### Darker blue

#006EA8

The color for the sixth category in a visualization.

### Pink

#EB689A

The color for the seventh category in a visualization.

### Burgundy

#8F0043

The color for the eighth category in a visualization.

### Purple

#7A04DD

The color for the ninth category in a visualization.

### Blue

#079CDA

The color for the tenth category in a visualization.

### Navy

#004054

The color for the eleventh category in a visualization.

### Gold

#BA8D02

The color for the twelth category in a visualization.

### Sequential palette

Use the sequential palette to indicate the magnitude of a value within a possible range using a gradation of colors that goes from light blue to dark blue.

### Blue 10

#D6EEF9

### Blue 20

#ACDEF3

### Blue 30

#83CEED

### Blue 40

#5ABDE6

### Blue 50

#30ADE0

### Blue 60

#079CDA

### Blue 70

#067DAE

### Blue 80

#045E83

### Blue 90

#004054
             Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Responsiveness](/skyux/design/styles/responsiveness.md)

Responsiveness
==============

SKY UX supports responsive user experiences that adapt to different screen sizes. Developers generally don't need to worry about managing responsive behaviors because SKY UX incorporates responsiveness directly into its patterns and components. However, in rare cases when additional options are necessary, SKY UX supports options such as container mixins.

In general, we recommend using [fluid grid]() to achieve responsive behavior, but in rare cases where a fluid grid isn't feasible, container mixins can provide an alternative method.

[

Container mixins
----------------

](/skyux/design/styles/responsiveness#container-mixins.md)

Responsive container mixins generate CSS for a specified breakpoint and all larger breakpoints. For example, `sky-host-responsive-container-md-min` applies to the `md` and `lg` breakpoints, while `sky-host-responsive-container-xs-min` applies to the `xs`, `sm`, `md`, and `lg` breakpoints.

Unlike media queries, container mixins respond to both screen width and container width. For example, content in a medium modal on a large desktop uses the `xs` breakpoint because the modal's content area is small even though the overall screen size is large.

Containers that support mixins include [modals](), [flyouts](), [tabs](), [vertical tabs](), [data manager views](), [split views](), and [pages]().

By default, container mixins respect view encapsulation. To apply styles globally or to apply them when view encapsulation is disabled, set the optional `$encapsulate` argument to `false`. For example, use `@include mixins.sky-host-responsive-container-sm-min(false)`.

`sky-host-responsive-container-xs-min($encapsulate: true)`

Applies to the `xs`, `sm`, `md`, and `lg` screen and container sizes. `$encapsulate` defaults to `true`. None found.

`sky-host-responsive-container-sm-min($encapsulate: true)`

Applies to the `sm`, `md`, and `lg` screen and container sizes. `$encapsulate` defaults to `true`. None found.

`sky-host-responsive-container-md-min($encapsulate: true)`

Applies to the `md` and `lg` screen and container sizes. `$encapsulate` defaults to `true`. None found.

`sky-host-responsive-container-xs-min($encapsulate: true)`

Applies to the `lg` screen and container sizes. `$encapsulate` defaults to `true`. None found.

[

Demo
----

](/skyux/design/styles/responsiveness#demo.md)

This content is optimized for SMALL screens or content areas.

This content is optimized for LARGE screens or content areas.

Content for Tab 2

  
Open modal with responsive content

[

Code
----

](/skyux/design/styles/responsiveness#code.md)

TypeScript

Copy

    import { Component } from '@angular/core';
    
    @Component({
      selector: 'app-responsive-content',
      template: `
        <div class="small-container-content">
          This content is optimized for SMALL screens or content areas.
        </div>
        <div class="large-container-content">
          This content is optimized for LARGE screens or content areas.
        </div>
      `,
      styleUrl: './responsive-content.component.scss',
    })
    export class ResponsiveContentComponent {}

Sass (Scss)

Copy

    @use 'node_modules/@skyux/theme/scss/mixins' as mixins;
    
    @include mixins.sky-host-responsive-container-xs-min() {
      .small-container-content {
        display: block;
      }
    
      .large-container-content {
        display: none;
      }
    }
    
    @include mixins.sky-host-responsive-container-sm-min() {
      .small-container-content {
        display: none;
      }
    
      .large-container-content {
        display: block;
      }
    }
            

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Styles](/skyux/design/styles.md)
4.  [Motion](/skyux/design/styles/motion.md)

Motion
======

Principles
----------

Motion, by its nature, catches the eye. Our brains are well-practiced at interpreting motion, and we can use the smallest details to learn about objects, the relationships between them, and the forces at work when things change.

SKY UX uses motion to shed light on the nature of changes in the system. It uses subtle animation cues to illustrate:

*   Changes in context, such as entering or exiting a [modal dialog](/skyux/components/modal.md)
*   The results of user actions
*   Connections between different pieces of content
*   Changes in the state of the system or content

SKY UX does NOT use animations to:

*   Emphasize some content over other content
*   Draw attention to primary actions
*   Distract or divert users

Physics
-------

Like other properties of visual design, motion takes advantage of the observer's expectations to simulate physical space in a digital picture. Just as shadows suggest depth and perspective, the details of motion imply properties about objects and the forces between them. SKY UX follows some basic rules to ensure that motion looks natural and realistic and that it demonstrates context to users.

*   Use natural acceleration curves in animations.
    *   Avoid linear animations, especially for any position translations.
    *   Ease-in when an object is visible at the beginning of its motion.
    *   Ease-out when an object is visible at the end of its motion.
    *   Ease-in-out when an object is visible throughout its motion.
*   To reduce distractions, limit the number of animations that occur simultaneously.
*   When simultaneous animations for multiple objects are necessary, ensure that the following animation properties are as similar as possible:
    *   Timing
    *   Duration
    *   Transition effect
    *   Acceleration curve
    *   Trajectory

Examples
--------

SKY UX uses a set of metaphor-based motion effects. These patterns should be included in the definitions of SKY UX components and should not be invoked directly.

Slide

This behavior moves content horizontally or vertically without altering other visual properties such as scale and transparency.

SKY UX primarily employs _slide_ to **show/hide content for sidebars and other patterns that use "off-stage" content with an affordance for calling it into view**.

*   Show/hide filters (sidebar)
*   Show/hide held panel
*   Move between adjacent steps in a [wizard](/skyux/components/tabs-wizard.md)
*   Move between [tabs](/skyux/components/tabs.md) **(native mobile only)**
*   Moving surrounding content during an _expand/collapse_ effect (see below)

_Slide_ should follow these guidelines:

*   Translate only in one dimension (X or Y), not both.
*   Use an **ease-in-out** acceleration curve for the translation.
*   Use a duration of 200 or 300 milliseconds.
    *   **200 ms** for sidebars and other patterns where one set of content partially covers another
    *   **300 ms** for wizard steps, tabs, and other effects where one set of content completely replaces another

Expand/collapse

A close relative of _slide_, this behavior changes the dimensions of containers that toggle between expanded and collapsed views of content. _Expand/collapse_ does not affect the z-order of the container, which means that the surrounding content needs to be moved (using _slide_) at the same time to make room (or reclaim vacated space).

SKY UX primarily employs _expand/collapse_ to **show/hide content that is hidden "on-stage" as part of a progressive disclosure pattern**.

*   [Tiles](/skyux/components/tile.md)
*   Accordion repeaters
*   Search fields that collapse to icons

_Expand/collapse_ should follow these guidelines:

*   Increase and decrease the size of the container, but do not apply transition effects to the content.
    *   Reveal and hide the content as the container size changes.
*   Use an **ease-in-out** acceleration curve for the scale change.
*   Use a duration of **300** milliseconds.
    *   If it necessary to _slide_ other content, use a 300 ms duration for that movement as well (with the same acceleration curve).

Emerge/recede

This behavior shows content that is called or dismissed as a direct consequence of user actions. It uses an eye-catching combination of scale, translation, and transparency transformations. This gives the affected content immediate prominence and also draws a clear relationship between the content and the initiating action that a user performs. Content that _emerges_ is elevated above its surroundings (and calling affordance) in the z-order with a shadow or even a mask over the rest of the page. When the interaction that began with the _emerge_ effect is completed (or abandoned), the content _recedes_ back into its related affordance with a reverse animation.

SKY UX primarily employs _emerge/recede_ to **initiate modal dialogs or other interactions that require users to complete tasks before moving on**.

*   [Modal dialogs](/skyux/components/modal.md)
*   [Dropdowns](/skyux/components/dropdown.md)
*   [Toasts](/skyux/components/toast.md)

_Emerge/recede_ should follow these guidelines:

*   Translate the center of the _emerging_ content from the center of the affordance that calls it to the center of its desired location when visible.
    *   Toasts are an exception and always _emerge_ in their designated place. No translation is necessary.
*   Scale the _emerging_ content from 0 to its full size.
*   Increase the alpha of the _emerging_ content from 0 to 100.
*   Use an **ease-in-out** acceleration curve for all 3 transitions.
*   Use a duration of 200 or 300 milliseconds, synced for all 3 transitions.
    *   **200 ms** for menus, pickers, and dropdown/select controls
    *   **300 ms** for toasts and modal dialogs
*   If a modal dialog also uses a translucent mask behind it, the mask does not need the full _emerge_ effect. Simply increase the mask's alpha from 0 to its final value with the same acceleration and duration as the other transitions.
            

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Buttons and links](/skyux/design/guidelines/buttons-links.md)

Buttons and links
=================

Two interacting principles guide SKY UX hyperlinks and [buttons](/skyux/components/button.md): style and implementation. Style determines the appropriate appearance of an affordance to the user, while implementation involves the core HTML decision to use the `<a>` element or the `<button>` element. In SKY UX, these guidelines overlap and interact: Differences in styling do not need to correspond to the use of different tags.

Style
-----

SKY UX uses several [styles for buttons and hyperlinks](/skyux/components/button.md). The differences in appearance carry meaning about roles in the system, distinguish between navigation and action, or convey different levels of emphasis or priority.

### Primary actions

The style for a primary action is a bold, saturated color that conveys importance and drives user workflows. Only use one primary action in any given system state. Primary actions use [primary buttons](/skyux/components/button.md) for:

*   The most important action on a page.
*   The most frequently used action on a page.
*   The progressive terminal action on a dialog (such as 'Save' or 'Done').

For information about how to use primary actions, see the [primary action guidelines](/skyux/design/guidelines/page-layouts#primary-action-guidelines.md).

### Secondary actions

Secondary actions are less important or less frequently used than primary actions, so SKY UX reduces the visual weight to make them noticeable but not attention-drawing. Secondary actions use [secondary buttons](/skyux/components/button.md) for:

*   Page actions on [record pages](/skyux/design/guidelines/page-layouts/record-page.md) and [action hub pages](/skyux/design/guidelines/page-layouts/action-hub.md).
    
*   Actions in [toolbars](/skyux/components/toolbar.md) at the top of lists.
    
*   Actions that are relevant to only part of a page's content, such as actions in [boxes](/skyux/components/box.md).
    
*   Secondary tasks or actions in [modals](/skyux/components/toolbar.md).
    

### Tertiary actions

Tertiary actions receive a lighter visual weight but invisibly occupy the same amount of space as primary and secondary actions. Tertiary actions use [link buttons](/skyux/components/button.md) for:

*   Infrequently used actions or options on a page
    
*   The “regressive” action on a dialog, such as a cancel action
    

### Inline links

Inline links receive the least visual weight and appear inline with text instead of in their own rectangular space. They have no button padding or spacing and should not be used in groups with other buttons. Do not “stack” multiple inline links too close together because this creates a usability risk of mis-clicks or mis-touches. Use [inline links](/skyux/components/button.md) for pure navigation:

*   Parent-to-parent
    
*   Parent-to-child
    
*   Links to external applications or services, such as a street address that links to a map application
    

Implementation
--------------

SKY UX styles allow `<a>` and `<button>` elements to appear interchangeable, but subtle differences in behavior make it important to select the correct implementation. Most notably, the elements differ in right-click options, long-touch and force-touch behaviors for mobile browsers, keyboard shortcuts, and their behavior with screen readers and other assistive technology.

Follow this guidance on which HTML tag to use in SKY UX:

*   For actions that only load new URLs in the browser, use the `<a>` element.
    
*   For all other actions, use the `<button>` element.
    

Only use `<a>` elements when nothing changes about the state of the system and users just navigate from one view to another. If affordances load new URLs but also perform other actions, use `<button>` elements. For example, while an affordance to delete a record page redirects users to a new view, it also changes the state of the system by deleting data, so it requires a `<button>` element.

Tooltips
--------

For buttons that use [icons](/skyux/components/icon.md) without labels and buttons that are not intuitive, you can provide tooltips as necessary to define the button actions. However, we recommend that you rely on button labels whenever possible while also taking design patterns into account. Do not arbitrarily replace button labels with tooltips.

Tooltip text needs to be clear and concise, and it doesn't need to use complete sentences. Use tooltips sparingly, and do not restate button labels or provide extraneous information. Do not use tooltips in place of [popovers](/skyux/components/popover.md).
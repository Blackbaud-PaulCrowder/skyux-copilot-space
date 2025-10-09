            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Accessibility](/skyux/learn/accessibility.md)
4.  [Code](/skyux/learn/accessibility/code.md)

Code for accessibility
======================

To build an accessible application, you must leverage the technical tools and features built into SKY UX components and also understand how to use them effectively alongside accessibility best practices.

Development best practices
--------------------------

*   Use structural semantic markup. This ensures that the role of elements and their relationships is available programmatically to user agents that help to communicate the content's meaning.
    
    *   [HTML semantics overview](https://learn.shayhowe.com/html-css/getting-to-know-html/)
        
    *   [Text-level semantics, microdata, and WAI-ARIA roles](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/)
        
*   Apply [accessible techniques to HTML](https://webaim.org/articles/) for [forms](https://webaim.org/techniques/forms/), [tables](https://webaim.org/techniques/tables/), [links](https://webaim.org/techniques/hypertext/), and [images](https://webaim.org/techniques/images/), as well as for [keyboard use](https://webaim.org/techniques/keyboard/).
    
*   If you create custom interactive components or use HTML elements differently than the default semantics:
    
    1.  Review [developer getting started documentation](https://www.w3.org/WAI/tips/developing/) from the World Wide Web Consortium (W3C).
        
    2.  Follow the [five rules of Accessible Rich Internet Applications](https://www.w3.org/TR/aria-in-html/#notes2) (ARIA) from the W3C recommendation.
        
    3.  Follow the W3C's [WAI-ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/practices/read-me-first/).
        

SKY UX component features for accessible experiences
----------------------------------------------------

*   Use the built-in features of SKY UX components, such as:
    
    *   `labelText` — Provides the visible label for an input and also the label for screen readers.
    *   `helpPopoverContent` — Adds a [help inline button](/skyux/components/help-inline.md) to the component's label or heading and supplies assistive technology support for the contents in the popover.
    *   `hintText` — Provides persistent hint text that is visibly related to the input.
*   Use the [page](/skyux/components/page.md) component to provide consistent layouts with built-in semantic markup.
*   Use the [field group](/skyux/components/field-group.md) component on forms to automatically provide HTML field sets for related inputs.
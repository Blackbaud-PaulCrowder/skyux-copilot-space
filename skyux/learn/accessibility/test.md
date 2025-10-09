            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Accessibility](/skyux/learn/accessibility.md)
4.  [Test](/skyux/learn/accessibility/test.md)

Test for accessibility
======================

SKY UX employs several methods to test components for accessibility. You can use the same practices and tools to ensure your applications are highly accessible.

Run automated accessibility tests
---------------------------------

The [`@skyux-sdk/testing` library](https://github.com/blackbaud/skyux/tree/main/libs/sdk/testing) provides methods to run [`axe-core` automated accessibility tests](https://github.com/dequelabs/axe-core) in your unit tests. `axe-core` includes rules covering a subset of the W3C's WCAG 2.2 A and AA success criteria. For guidance on how to run accessibility checks in SKY UX unit tests, see [accessibility tests](/skyux/learn/accessibility/test/accessibility-tests.md).

Incorporate accessibility checks in a code review
-------------------------------------------------

Perform a review using the following SKY UX accessibility code review checklist to identify potential accessibility problems that automated `axe-core` testing can not evaluate.

Complete the following checks when reviewing your application's markup code along with the user interface:

### Text equivalents for non-text elements

1.  Ensure that `alt` attributes on `<img>` elements accurately reflect the content and/or function of the image in the [context that the image](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content) is used.
    
2.  Ensure that button text values accurately describe the purpose of buttons.
    
3.  Ensure that any decorative images have the `role="presentation"` attribute.
    

### Page order

Ensure that the visual order of elements matches the DOM order of elements.

### Semantic markup

Ensure that you use proper semantic HTML elements to describe the content of the page or component. For example, use `<ul>` for unordered lists, use `<h1>` through `<h6>` for headings, and use `<nav>` for navigation.

For details of semantic markup, see [Getting to know HTML](https://learn.shayhowe.com/html-css/getting-to-know-html/) and [Extending Semantics and Accessibility](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/).

### Custom controls

For custom interactive controls that are used in ways that are not part of the HTML standard, ensure that the elements have the necessary ARIA roles, states, and properties. For information about how to make components and behaviors accessible with ARIA roles, states, and properties, see [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices/).

Complete manual keyboard testing
--------------------------------

Follow the procedures below to ensure that people can use your feature with a keyboard only.

### Use the Tab key to move through a page or component

Ensure that navigation with the Tab key meets the following criteria:

1.  The Tab key places focus on all focusable elements.
    
2.  The Tab key does not place focus on elements that cannot receive focus.
    
3.  A visual indication occurs when each element receives focus.
    
4.  The order of focus follows the sequence and relationships in the page or component.
    
5.  The page or component does not experience any substantial change when an element receives focus. For example, it does not experience substantial change when a modal opens or focus changes again.
    
6.  The Tab key moves focus throughout the page without becoming trapped. It moves from top to bottom or bottom to top (Shift-Tab) and starts over when it reaches the bottom or top.
    

### Use all interactive elements and controls

1.  Ensure that the keyboard can access all interactive elements and controls.
    
    *   Press Enter to activate links and buttons.
        
    *   Press arrow keys and the space bar to navigate to and select/deselect radio buttons, checkboxes, tabs, dropdown menus, navigation menus, autocomplete fields, and other elements and controls.
        
    
    For information about keyboard use for different types of controls, see [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/).
    
2.  Ensure that entering data in form inputs such as radio buttons, checkboxes, and text fields does not substantially change the page or reload it.
    
3.  Test error messages.
    
    *   Ensure that the focus is placed on the error message or that an ARIA technique is used to announce the error.
        
    *   Ensure that the message includes a suggestion for how to fix the error.
        
    *   Ensure that users can move focus directly from the error message to the error.
        

### Use all modal dialogs

Ensure that navigation with the Tab key meets the following criteria:

1.  The Tab key places focus on elements that open modal dialogs, and pressing Enter opens the dialog and places focus on the first element or the title.
    
2.  The Tab key places focus on all focusable elements.
    
3.  The Tab key does not place focus on elements that cannot receive focus.
    
4.  Focus remains in the modal and does not return to the page.
    
5.  When the Tab key places focus on an element that closes the modal, pressing Enter closes the modal.
    
6.  When the modal closes, focus returns to the element that opened the modal or goes to a logical place based on actions within the modal. Focus does not return to the top of the underlying page.
            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Preview](/skyux/learn/preview.md)

Preview features
================

Monitor this page for updates to the SKY UX API that are not yet fully documented. In the developer docs, a preview tag will highlight these updates and indicate that features aren't yet represented in the design docs, demo, and code examples. This helps facilitate far-reaching changes that span multiple iterations and affect multiple components. It can also highlight breaking changes in minor versions, but the SKY UX team strives to avoid those.

[

Now released!
-------------

](/skyux/learn/preview#now-released.md)

### Form field standardization

To simplify and improve how consumers implement accessible forms that follow design guidelines, we updated our form field input components. The updates are non-breaking to enable incremental adoption. Demos, code examples, and documentation have been updated to use the new inputs.

We updated input box to use inputs from child components when they own relevant functionality. This makes input fields faster to implement and easier to manage long-term because the SKY UX team will handle breaking changes, accessibility guideline changes, and component design changes.

New inputs for components include:

*   `labelText` — Sets the visible label and also sets `aria-label` or `aria-labelledby` in several places to automatically meet accessibility criteria.
    
*   `labelHidden` — Hides labels for components that don't always need visible labels while still meeting accessibility requirements for assistive technology.
    
*   `helpPopoverContent` — Displays the [help inline](/skyux/components/help-inline.md) button beside a label and is responsible for relating the icon and popover with the component to display the content to both visual users and assistive technology.
    
*   `helpPopoverTitle` — Works with `helpPopoverContent` to provide an optional title for the popover.
    
*   `hintText` — Styles and formats hint text that typically appears below the component.
    
*   `stacked` — Styles the vertical spacing between stacked components.
    
*   `required` — For components that don't support other form controls, relates the ARIA required attribute and the visible asterisk to the field.
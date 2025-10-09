            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Deprecation](/skyux/learn/develop/deprecation.md)
5.  [Progress indicator wizard](/skyux/learn/develop/deprecation/progress-indicator-wizard.md)

Progress indicator wizard
=========================

The [progress indicator wizard](/skyux/components/progress-indicator-wizard.md) component is deprecated in favor of the [tabs wizard](/skyux/components/tabs-wizard.md) component.

How to migrate
--------------

SKY UX created a migration script to help you migrate to the tabs wizard. From a project that uses the progress indicator wizard, run the following command:

Bash

Copy

npx ng g @skyux/packages:convert-progress-indicator-wizard-to-tab-wizard

    npx ng g @skyux/packages:convert-progress-indicator-wizard-to-tab-wizard

What to review after the script
-------------------------------

After you run the migration script, review the following items in your project:

*   If your code used the `<sky-progress-indicator-title>` component, that element was converted to an `<h3>`. Review the change and update your code as necessary.
*   If you used the `messageStream` input, the tabs wizard component doesn't support that input. Review the [`SkyTabsetComponent` documentation](/skyux/components/tabs-wizard?docs-active-tab=development#class_sky-tabset-component.md) for alternative inputs.
*   If your code used the `<sky-progress-indicator-nav-button>` component with `(actionClick)="..."` or `buttonType="reset"`, the tabs wizard component doesn't support those features. Review the [`SkyTabsetNavButtonComponent`documentation](/skyux/components/tabs-wizard?docs-active-tab=development#class_sky-tabset-nav-button-component.md) for alternatives.
             

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Deprecation](/skyux/learn/develop/deprecation.md)
5.  [Page summary](/skyux/learn/develop/deprecation/page-summary.md)

Page summary
============

The [page summary](/skyux/components/page-summary.md) component is deprecated in favor of the [page](/skyux/components/page.md) component's `sky-page-header` component. For page templates and techniques to summarize page content, see the [page design guidelines](/skyux/design/guidelines/page-layouts.md).

How to migrate
--------------

SKY UX created a migration script to help you migrate to the page header component. From a project that uses the page summary component, run the following command:

Bash

Copy

npx ng g @skyux/packages:convert-page-summary-to-page-header

    npx ng g @skyux/packages:convert-page-summary-to-page-header

What to review after the script
-------------------------------

After running the migration script, you should review the following items in your project:

*   The `<sky-page-summary-key-info>` component that places key information to the right of the page summary is no longer supported. The content has been moved to `<sky-page-header-details>`. Please review the changes and the design guidelines below to update your code accordingly.
*   The migration script uses the `<sky-page-header>` component but does not use `<sky-page>`. Review the [page component](/skyux/components/page.md) documentation and consider using the `<sky-page>` component. The page component provides additional features such as a page title and layout options.

Design guidelines
-----------------

### Page header content

In general, limit the content in the page header and remove extra labels when possible. Use the [label component](/skyux/components/label.md) to highlight important page properties, such as record status, and remove labels from value-label pairs when the context is clear without them.

For more recommendations about header content on record pages, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/algebra-1.38fe9391ac5479a478b313b20766115b.png)

Don't use value-label pairs when context is clear without labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/algebra-2.297acb823195069ae5820c2c43f67e52.png)

Do use the label component to display a page status. Remove unnecessary labels from value-label pairs when the context is clear.

If a page header includes a [description list](/skyux/components/description-list.md), use `horizontal` mode. If you need to convert a definition list to a description list, see the [definition list deprecation guide](/skyux/learn/develop/deprecation/definition-list.md).

For recommendations about moving content from record page headers to other containers, such as boxes or tiles, see the [record page guidelines](/skyux/design/guidelines/page-layouts/record-page.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/horizontal-1.708d24ddfa248afe4461256df1683946.png)

Don't use vertical layouts or multiple description lists in page headers.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/horizontal-2.0b62faa34be6f28c978e386d654badfc.png)

If a description list is necessary, use a horizontal layout. Move header content to the page content when possible.

On a [list page](/skyux/design/guidelines/page-layouts/list-page.md), display summary content about the list, such as counts or calculated totals, in the list's summary details instead of the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/list-summary-details-1.b560c346ca8042f8d8aed7774bc049a4.png)

Don't put counts or calculated totals in the page header of a list page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/list-summary-details-2.f15ca6dcc646de9357e3ebe687d2e5bb.png)

Do use list summary details to display counts or totals on a list page.

### Page actions

The [page header](/skyux/components/page.md) component includes dedicated space for page-level actions. For a record page, put page actions in the `<sky-page-header-actions>` component instead of a [toolbar](/skyux/components/toolbar.md) component unless you need the toolbar's `<sky-toolbar-view-actions>` component for view controls such as "Expand all/Collapse all" for tile dashboards. If a toolbar is necessary, put it underneath the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/toolbar-1.b0e4e92d15ce428ba25ea4894378a527.png)

Don't use a toolbar for actions related to an entire record page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/toolbar-2.7458a6a7cc06cb8e9d2e48a46e5fd5d0.png)

Do use page actions for actions related to an entire record page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/toolbar-3.b58c1ab0af375ce5fb18a0cdd0f97552.png)

Do use a toolbar for page actions that include view controls on the right side.

On a list page, use a toolbar component for actions related to the list content. Don't put list actions in the `<sky-page-header-actions>` component.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/list-summary-details-2.f15ca6dcc646de9357e3ebe687d2e5bb.png)

Do use a toolbar for list actions on a list page.

In the rare case of a list page that requires both list actions and actions in the page header, use both a toolbar and a `<sky-page-header-actions>` component.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/page-summary/actions-and-toolbar-1.2fbcb921e3d68172a4a9a0bf1130211b.png)

List pages can include actions in both the page header and a toolbar when necessary.
             

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Deprecation](/skyux/learn/develop/deprecation.md)
5.  [Definition list](/skyux/learn/develop/deprecation/definition-list.md)

Definition list
===============

The [definition list](/skyux/components/definition-list.md) component is deprecated in favor of the [description list](/skyux/components/description-list.md) component.

How to migrate
--------------

SKY UX created a migration script to help you migrate to the description list component. From a project that uses the definition list component, run the following command:

Bash

Copy

npx ng g @skyux/packages:convert-definition-list-to-description-list

    npx ng g @skyux/packages:convert-definition-list-to-description-list

What to review after the script
-------------------------------

After you run the migration script, review the following items in your project:

*   If your code used the `labelWidth` input, the description list component doesn't support that input and instead resizes label widths based on the content and the responsive container. Review the change and update your code as necessary.
*   If your code used the `<sky-definition-list-heading>` component, that element was converted to an `<h3>` with the `sky-font-heading-3` class. Evaluate the change within the context of the page, and adjust the heading level and style as necessary to fit the page's heading hierarchy.
*   By default, converted description lists use `horizontal` mode. To adjust the mode of term-description pairs to fit your needs, see the guidance below and refer to the [description list](/skyux/components/description-list?docs-active-tab=development.md) documentation.

### Vertical vs. horizontal lists

Converted description lists use `horizontal` mode by default, and they most likely display well. However, in some cases, you need to adjust the display mode or use a different component.

#### `Horizontal` mode

Use `horizontal` mode when lists include up to 6 items and stand alone.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/horizontal-def-list.88a80f8f471c0d09ac17788e8465e9cd.png)

Definition list with 4 items

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/horizontal-desc-list-even-spaced.42b6f962aa6f788d29505a032df9bf19.png)

The converted description list displays items horizontally with even spacing in between.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/horizontal-def-list-xs.5f0182e66e1f81ca9bd3a5d14fdd5ede.png)

Definition list with 3 items

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/horizontal-desc-list-xs.5d2502f629d9de5a4c52fd834fdf117e.png)

The converted description list collapses to 2 columns when its container hits the xs breakpoint.

#### `Vertical` mode

Use `vertical` mode when lists in containers are placed alongside other lists or additional content. To organize lists into equal columns, use a [fluid grid](/skyux/components/fluid-grid.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/vertical-def-list.0df017fabad29d992628fcc18fb7ed8a.png)

Multiple definition lists stacked together

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/vertical-desc-list.e0e930e2d906115a429176436ddfedeb.png)

Vertical description lists use separate headings in a 2-column fluid grid.

#### `Vertical` mode for multiple lists in columns

Use `vertical` mode when you need to display multiple description lists in multiple columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/2-columns-def-list.87559ab86eda64c49334fa46ac662b54.png)

Multiple definition lists in a 2-column fluid grid

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/2-columns-desc-list.e9cd813a326724a4bbf8f4939494f050.png)

Use vertical lists for multiple description lists in a 2-column fluid grid.

### Numeric or tabular data

If the list displays numeric or tabular data, use the following option that best fits the layout and information hierarchy of your page:

*   To maintain a similar information hierarchy, use a description list component in `horizontal` mode.
*   To call out important metrics, use a [key info](/skyux/components/key-info.md) component.
*   To display information in a tabular format, use a simple HTML table with compact spacing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/numeric-def-list-1.8753b9f05851d5ba5e8844c5d07bb254.png)

Definition list with numeric data

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/numeric-desc-list-1.320caf69aca4c0ed714ab51bda1e48ff.png)

A horizontal description list displays numeric data in a grid at the xs breakpoint.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/numeric-def-list-2.1da98f0f8ee92a5f71db6679dc1ed69e.png)

Definition list with numeric data

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/numeric-desc-list-2.dced1a53bd2955e4c36d8dfe29b28ac5.png)

The key info component presents numeric data as important metrics.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/tabular-def-list.7da6e333a0003e4c3d5a7183dd86ef3c.png)

Definition list with tabular data

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/tabular-desc-list.d1478b3a1f9125be99d5bfdbe52882ff.png)

A simple HTML table with styling classes displays numeric data in a tabular format.

### Long description lists

Use `longDescription` mode when descriptions are complete sentences or longer, such as glossaries.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/long-desc-def-list.b9225798747ae9297c5a75246f2d856d.png)

Definition list with complete sentences

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/deprecation/definition-list/long-desc-desc-list.ee6767f66f5c26719ed173ef6c24dc30.png)

Use long-description lists for glossaries and other verbose content.
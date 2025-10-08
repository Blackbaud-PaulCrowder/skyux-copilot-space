            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Deprecation](/skyux/learn/develop/deprecation.md)
5.  [Select field](/skyux/learn/develop/deprecation/select-field.md)

Select field
============

The [select field](/skyux/components/select-field.md) component is deprecated. In most cases, we recommend using the [lookup](/skyux/components/lookup.md) component instead, but some scenarios require a different option, such as a [selection box](/skyux/components/selection-box.md) component or an HTML `<select>` element in an [input box](/skyux/components/input-box.md).

[

How to migrate
--------------

](/skyux/learn/develop/deprecation/select-field#how-to-migrate.md)

SKY UX didn't create a migration script because of differences between the select field and lookup components, particularly in single-select mode, and because lookup isn't always the right choice for migration. Instead, SKY UX created the following AI prompt to manually migrate your code. An AI tool will speed up the migration, but be sure to review the output carefully because AI responses may not be 100 percent complete and accurate.

Markdown

Copy

Scan the .html files in this repository, find the files that use the \`sky-select-field\` element, and use the instructions at https://github.com/blackbaud/skyux/blob/12.x.x/docs/migrating-deprecated-components/select-field/README.md to convert the \`sky-select-field\` elements to \`sky-lookup\` elements. If you find any cases where the conversion is not clear, please ask questions.

    Scan the .html files in this repository, find the files that use the
    `sky-select-field` element, and use the instructions at
    https://github.com/blackbaud/skyux/blob/12.x.x/docs/migrating-deprecated-components/select-field/README.md
    to convert the `sky-select-field` elements to `sky-lookup` elements. If you
    find any cases where the conversion is not clear, please ask questions.
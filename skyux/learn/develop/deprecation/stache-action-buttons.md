            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Deprecation](/skyux/learn/develop/deprecation.md)
5.  [Stache action buttons](/skyux/learn/develop/deprecation/stache-action-buttons.md)

Stache action buttons
=====================

The [Stache action buttons]() component is deprecated and can be replaced with the [action button](/skyux/components/action-button.md) component.

How to migrate
--------------

SKY UX didn't create a migration script because of differences between the Stache and SKY UX action buttons. Instead, SKY UX created the following AI prompt to manually migrate your code. An AI tool will speed up the migration, but be sure to review the output carefully because AI responses may not be 100 percent complete and accurate.

Markdown

Copy

Scan the .html files in this repository, find the files that use the \`stache-action-buttons\` element, and use the instructions at https://github.com/blackbaud/skyux/blob/main/docs/migrating-deprecated-components/stache-action-buttons/README.md to convert the \`stache-action-buttons\` elements to \`sky-action-button-container\` elements. If you find any cases where the conversion is not clear, please ask questions.

    Scan the .html files in this repository, find the files that use the
    `stache-action-buttons` element, and use the instructions at
    https://github.com/blackbaud/skyux/blob/main/docs/migrating-deprecated-components/stache-action-buttons/README.md
    to convert the `stache-action-buttons` elements to
    `sky-action-button-container` elements. If you find any cases where the
    conversion is not clear, please ask questions.
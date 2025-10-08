            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Linting](/skyux/learn/develop/linting.md)

Linting
=======

SKY UX provides a set of recommended [ESLint](https://eslint.org/) rules for Angular CLI projects.

[

Prerequisites
-------------

](/skyux/learn/develop/linting#prerequisites.md)

The `eslint-config-skyux` package requires `angular-eslint`. Follow the [`angular-eslint` installation instructions](https://github.com/angular-eslint/angular-eslint?tab=readme-ov-file#quick-start) before continuing.

[

Installation
------------

](/skyux/learn/develop/linting#installation.md)

To install the `eslint-config-skyux` package, run the following command in the context of your Angular CLI project.

Copy

ng add eslint-config-skyux

    ng add eslint-config-skyux

Then open your root ESLint config file and replace its contents with the following code.

eslint.config.js JavaScript

Copy

    // @ts-check
    const skyux = require('eslint-config-skyux');
    const tseslint = require('typescript-eslint');
    
    module.exports = tseslint.config(
      ...skyux,
      {
        languageOptions: {
          parserOptions: {
            projectService: true,
            tsconfigRootDir: '.',
          },
        },
      },
      {
        files: ['**/*.ts'],
        rules: {
          '@angular-eslint/directive-selector': [
            'error',
            {
              type: 'attribute',
              prefix: 'app',
              style: 'camelCase',
            },
          ],
          '@angular-eslint/component-selector': [
            'error',
            {
              type: 'element',
              prefix: 'app',
              style: 'kebab-case',
            },
          ],
        }
      }
    );

[

Usage
-----

](/skyux/learn/develop/linting#usage.md)

To lint your project, run the following command. The `--fix` option automatically fixes some errors in your code, but this option can't fix all errors.

Copy

ng lint --fix

    ng lint --fix

[

ESLint rules
------------

](/skyux/learn/develop/linting#eslint-rules.md)

The `eslint-config-skyux` recommended config includes:

*   the [recommended type-checked rules from `typescript-eslint`](https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/src/configs/flat/recommended-type-checked.ts)
*   the [recommended rules from `angular-eslint`](https://github.com/angular-eslint/angular-eslint/blob/main/packages/angular-eslint/src/configs/ts-recommended.ts)
*   the [recommended rules from `skyux-eslint`](https://github.com/blackbaud/skyux/blob/main/libs/sdk/skyux-eslint/src/configs/ts-recommended.ts)
*   [additional best-practice rules](https://github.com/blackbaud/skyux/blob/main/libs/sdk/eslint-config-skyux/src/index.ts)

[

@skyux-sdk/eslint-config is deprecated
--------------------------------------

](/skyux/learn/develop/linting#skyux-sdkeslint-config-is-deprecated.md)

We deprecated the `@skyux-sdk/eslint-config/recommended` config in favor of `eslint-config-skyux` to align with ESLint naming conventions. Both packages provide the same rules.

[

Contribution
------------

](/skyux/learn/develop/linting#contribution.md)

The source code for `eslint-config-skyux` is available on [GitHub](https://github.com/blackbaud/skyux/tree/main/libs/sdk/skyux-eslint). You can [file an issue](https://github.com/blackbaud/skyux/issues) or [review our contribution process](https://github.com/blackbaud/skyux/blob/main/CONTRIBUTING.md).
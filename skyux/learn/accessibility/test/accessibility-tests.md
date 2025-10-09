            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Accessibility](/skyux/learn/accessibility.md)
4.  [Test](/skyux/learn/accessibility/test.md)
5.  [Accessibility tests](/skyux/learn/accessibility/test/accessibility-tests.md)

Accessibility tests
===================

The [`@skyux-sdk/testing` library](https://github.com/blackbaud/skyux/tree/main/libs/sdk/testing) provides methods to run [`axe-core` automated accessibility tests](https://github.com/dequelabs/axe-core) in your unit tests. `axe-core` is an open source library of automated accessibility rules that is integrated into SKY UX to identify potential issues for a subset of the [Web Content Accessibility Guidelines 2.2 Level A and AA success criteria](https://www.w3.org/TR/WCAG22/).

We strongly recommend that you use unit tests instead of end-to-end tests based on [Angular's guidance on testing](https://v9.angular.io/guide/testing#use-e2e-end-to-end-to-test-more-than-a-single-unit), which describes many advantages of unit tests over e2e tests. SKY UX guidance is to only use e2e tests as a last resort when you can't use Angular's testing framework to examine or interact with the DOM.

Import SKY UX SDK testing library
---------------------------------

The first step to run accessibility checks in SKY UX unit tests is to import the [`@skyux-sdk/testing` library](https://github.com/blackbaud/skyux/tree/main/libs/sdk/testing) into your SPA. This library provides methods to interact with SKY UX during Karma unit tests. For accessibility testing, it extends the Jasmine `expectAsync` function to add the `toBeAccessible` matcher.

To install the testing library, open the command prompt, `cd` into your SPA's directory, and run:

Copy

npm install @skyux-sdk/testing --save-dev --save-exact

    npm install @skyux-sdk/testing --save-dev --save-exact

By default, the `SkyA11yAnalyzerConfig` interface specifies [configuration settings for `toBeAccessible` to indicate which accessibility checks to run](https://github.com/blackbaud/skyux/blob/main/libs/sdk/testing/src/lib/a11y/a11y-analyzer.ts). To overwrite the default accessibility checks, you can modify [a parameter for the `toBeAccessible` matcher](/skyux/learn/accessibility/test/accessibility-tests#overwrite-accessibility-checks.md).

Import the `expectAsync` function
---------------------------------

After you import the testing library, the next step to run accessibility checks in unit tests is to import the extended Jasmine `expectAsync` function into `.spec.ts` files. At the top of the spec files for the components to test, import the function from the testing library:

Copy

    import {
      expectAsync
    } from '@skyux-sdk/testing';
  

    import {
      expectAsync
    } from '@skyux-sdk/testing';

After you import the `expectAsync` function, you can use it to run accessibility tests for components. For components that change state, you can insert the function into existing `it` blocks. And, for components that don't change state, the function can stand alone to run accessibility checks from its own `it` block.

Insert the `expectAsync` function and `toBeAccessible` matcher
--------------------------------------------------------------

After you import the `expectAsync` function into spec files, the next step is to wrap the `expectAsync` function around the elements to test for accessibility.

Copy

    it('should pass accessibility', async () => {
      await expectAsync(element).toBeAccessible();
    }));
  

    it('should pass accessibility', async () => {
      await expectAsync(element).toBeAccessible();
    }));

Overwrite accessibility checks
------------------------------

You can specify an optional parameter within the `toBeAccessible` matcher to overwrite [the default accessibility checks that `SkyA11yAnalyzerConfig` specifies](https://github.com/blackbaud/skyux/blob/main/libs/sdk/testing/src/lib/a11y/a11y-analyzer.ts).

You adjust configuration settings to turn off accessibility checks. [The `SkyA11yAnalyzerConfig` interface](https://github.com/blackbaud/skyux/blob/main/libs/sdk/testing/src/lib/a11y/a11y-analyzer-config.ts) specifies configuration settings, and it turns all checks on by default. To turn off accessibility checks, them to `false`:

Copy

    it('should pass accessibility', async () => {
      await expectAsync(element).toBeAccessible({
        rules: {
          'color-contrast': {enabled: false }
        }
      });
    }));
  

    it('should pass accessibility', async () => {
      await expectAsync(element).toBeAccessible({
        rules: {
          'color-contrast': {enabled: false }
        }
      });
    }));

Review accessibility failures
-----------------------------

When you include accessibility rules in your unit tests, you may run into errors that uncover accessibility issues. Here is an example of an error message that appears in the command log when you run `ng test`:

Copy

    info: Starting accessibility checks for https://host.nxt.blackbaud.com/builder-allytest/...
    info: Accessibility checks finished with 1 violation.
    error: axe - \[Rule: 'label'\] Form elements must have labels - WCAG: wcag332, wcag131
    Get help at: https://dequeuniversity.com/rules/axe/2.3/label?application=webdriverjs
    Elements:
    
  

    info: Starting accessibility checks for https://host.nxt.blackbaud.com/builder-allytest/...
    info: Accessibility checks finished with 1 violation.
    error: axe - [Rule: 'label'] Form elements must have labels - WCAG: wcag332, wcag131
    Get help at: https://dequeuniversity.com/rules/axe/2.3/label?application=webdriverjs
    Elements:

The first line of the error message indicates what failed. It lists the name of the rule that failed and a detailed description that includes the WCAG 2.2 success criteria numbers. On the next line, the error message provides the URL for the rule definition to help address the failure. And finally, the error message lists the DOM elements where the failure was identified.
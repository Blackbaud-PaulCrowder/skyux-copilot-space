            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Visual theme](/skyux/learn/visual-theme.md)
4.  [Enable modern theme](/skyux/learn/visual-theme/enable-modern.md)

Enable modern theme
===================

On this page
============

1.  [Standalone SKY UX SPAs](/skyux/learn/visual-theme/enable-modern#theming-for-standalone-SPAs.md)
2.  [SKY Add-ins](/skyux/learn/visual-theme/enable-modern#theming-for-SKY-Add-ins.md)

[

Standalone SKY UX SPAs
----------------------

](/skyux/learn/visual-theme/enable-modern#theming-for-standalone-SPAs.md)

Standalone SKY UX SPAs define their visual themes. In general, standalone SPA authors should try to match the theme that users encounter on other related SPAs. It is important to maintain a consistent visual experience across workflows that connect multiple SPAs together. To set the theme in a standalone SPA:

Add `provideInitialTheme('modern')` to `providers` in the `ApplicationConfig`:

main.ts TypeScript

Copy

        import { bootstrapApplication } from '@angular/platform-browser';
        import { provideInitialTheme } from '@skyux/theme';
        import { AppComponent } from './app/app.component';
        bootstrapApplication(AppComponent, { providers: \[provideInitialTheme('modern')\] });
      

    import { bootstrapApplication } from '@angular/platform-browser';
    import { provideInitialTheme } from '@skyux/theme';
    import { AppComponent } from './app/app.component';
    bootstrapApplication(AppComponent, { providers: [provideInitialTheme('modern')] });

You can change the theme at any point in the application's lifecycle by calling `setTheme()` on `SkyThemeService`.

[

SKY Add-ins
-----------

](/skyux/learn/visual-theme/enable-modern#theming-for-SKY-Add-ins.md)

*   Add-ins that use Angular and SKY UX automatically support theme switching to match the visual theme of the host service. This means that add-ins automatically display the same visual theme as solution where they appear. A single add-in can display in both themes if viewed in two contexts that use different themes. To use SKY UX with SKY Add-ins, follow the guidance in the [SKY API documentation](https://developer.blackbaud.com/skyapi/docs/addins).
*   SKY Add-ins that don't use SKY UX can still follow the visual theme of their host service. The [styles](/skyux/design/styles.md) documentation defines the exact values of the styles for both visual themes. The SKY Add-in client supports a callback function to identify the displayed theme of a host service, so add-ins can switch styles to match.
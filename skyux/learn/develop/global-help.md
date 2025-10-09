            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Global help](/skyux/learn/develop/global-help.md)

Global help
===========

SKY UX components support displaying help content in a [popover](/skyux/components/popover.md) or a larger container, such as the the help widget (internal Blackbaud use only), a [flyout](/skyux/components/flyout.md), or a new window. This section describes how to integrate the latter into SKY UX components used by your application.

Overview
--------

Many applications provide a set of help topics that open in a common window or component that can be summoned from multiple places within the application, such as a global help button or individual UI components. Using the techniques in this section, you can use the embedded help button in many SKY UX components to display help topics using your own custom implementation.

Configuration
-------------

To implement global help, you must provide an implementation of `SkyHelpService` in your SPA's root module.

TypeScript

Copy

    import {
      SkyHelpService
    } from '@skyux/core';
    
    import {
      AppHelpService
    } from './shared/services/app-help.service';
    
    @NgModule({
      providers: [
        {
          provide: SkyHelpService,
          useClass: AppHelpService
        }
      ]
    })
    export class AppModule { }

Next, you implement a service to display global help for a given help key. The help key is a string that uniquely identifies the help topic to open.

The following example builds a URL with the help key as the path and opens that URL in a new browser window.

TypeScript

Copy

    import {
      Injectable
    } from '@angular/core';
    
    import {
      SkyHelpService
    } from '@skyux/core';
    
    @Injectable()
    export class AppHelpService extends SkyHelpService {
      public openHelp(helpKey: string): void {
        window.open(`https://example.com/help/${helpKey}`, '_blank');
      }
    }

Implementation
--------------

With the above configuration, SKY UX components in your application that have the `helpKey` input will open the help topic you specify using your help service.

The following example specifies the help key `my-help-topic.html` on a [SKY UX input box.](/skyux/components/input-box.md) A help button displays next to the input box's label and opens `https://example.com/help/my-help-topic.html` in a new window when clicked.

Copy

    <sky-input-box
      helpKey="my-help-topic.html"
      labelText="My input"
    >
      <input type="text" />
    </sky-input-box>

Testing
-------

SKY UX provides a testing controller to assist with unit tests for global help. For examples of this controller in unit tests, see the code examples for the [page component](/skyux/components/page?docs-active-tab=code-examples.md).
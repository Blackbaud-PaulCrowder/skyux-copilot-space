                  

 Back to top
===========

The back to top button in the bottom left of the page returns users to an element after they scroll away from it.

 Usage
------

### Use when

Use the back to top button when users need a quick way to access the top of [infinite scroll lists](/skyux/components/infinite-scroll.md) or other long lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-usage.1fac8fef1a83c38d1299788de071cc5d.png)

Use the the back to top bar with infinite scroll lists.

 Anatomy
--------

1

Back to top button

2

Button bar

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-anatomy.24bd9005bf359b41c87d26c4f8eb449f.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Repeater](/skyux/components/repeater.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/back-to-top/back-to-top.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBackToTopModule
-------------------

Type: Module

`import { SkyBackToTopModule } from '@skyux/layout';`

 SkyBackToTopDirective
----------------------

Type: Directive

Selector: `[skyBackToTop]`

Associates a button with an element on the page and displays that button to return to the element after users scroll away.

### Inputs

#### `skyBackToTop: "" | SkyBackToTopOptions | undefined`

Configuration options for the back to top component.

#### `skyBackToTopMessageStream: Subject<SkyBackToTopMessage> | undefined`

The observable to send commands to the back to top component. The commands respect the `SkyBackToTopMessage` type.

 SkyBackToTopOptions
--------------------

Type: Interface

Specifies options for the back to top component.

    interface SkyBackToTopOptions {
      buttonHidden?: boolean;
    }

### Properties

#### `buttonHidden?: boolean`

Whether to hide the back to top button.

 SkyBackToTopMessage
--------------------

Type: Interface

Specifies messages to send to the back to top component.

    interface SkyBackToTopMessage {
      type?: BackToTop;
    }

### Properties

#### `type?: BackToTop`

The type of message to send.

 SkyBackToTopMessageType
------------------------

Type: Enumeration

The type of message to send to the back to top component.

    enum SkyBackToTopMessageType {
      BackToTop = 0,
    }

### Properties

#### `SkyBackToTopMessageType.BackToTop`

Scrolls the element back to the top.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBackToTopHarness
--------------------

Type: Class

`import { SkyBackToTopHarness } from '@skyux/layout/testing';`

Harness for interacting with a back to top component in tests.

### Methods

#### `clickBackToTop(): Promise<void>`

Clicks the back to top button.

#### Returns

`Promise<void>`
                 

 Wait
====

The wait component and service create waits on individual elements and on pages.

 Accessibility
--------------

### Text equivalents

The wait component provides default text equivalents for screen readers to [support accessibility](/skyux/learn/accessibility.md). These ARIA values are available when users tab to a wait icon, when a wait loads, and when a wait closes. For page-level waits, the default values are sufficient for most scenarios, but for element-level waits, we recommend more specific text equivalents to describe the elements.

For example, element-level nonblocking waits default to "Loading." when they initially load and to "Loading complete." when loading finishes. If multiple elements on a page require waits, then screen readers repeat these generic messages. To support users of assistive technologies, we recommend more descriptive values, such as "Gift details loading." and "Loading complete for gift details."

### Focus

When a focused element on a page is placed in a waiting state, focus automatically shifts to the page's `body` element. If the waiting state for that element finishes before any additional change in focus, then the focus automatically reverts to the previously focused element.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/wait/wait.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyWaitModule
--------------

Type: Module

`import { SkyWaitModule } from '@skyux/indicators';`

 SkyWaitComponent
-----------------

Type: Component

Selector: `sky-wait`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the wait icon. This sets the icon's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md) when an element or page loads and when users tab to a wait icon. The default value varies based on whether the wait is for an element or a page and whether it is a blocking wait. For example, the default for a page-level blocking wait is "Page loading. Please wait." For element-level waits, we recommend that consumers overwrite the default to describe the specific element. "For more information, see the Design tab and the [WAI-ARIA `aria-label` definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `isFullPage: boolean | undefined`

When set to `true`, wait indication appears on the page level instead of the parent element level. We recommend that you use the `beginBlockingPageWait` or `beginNonBlockingPageWait` functions of the `SkyWaitService` instead of setting this on the component level.

Default: `false`

#### `isNonBlocking: boolean | undefined`

When set to `true`, wait indication appears in the bottom left corner of the element instead of hiding the entire parent element.

Default: `false`

#### `isWaiting: boolean | undefined`

When set to `true`, wait indication appears on the parent element of the `sky-wait` component.

#### `screenReaderCompletedText: string | undefined`

Screen reader text [to support accessibility](/skyux/learn/accessibility.md) when the wait toggles off. The default varies based on whether the wait is for an element or a page. For example, the default for a page-level wait is "Page loading complete." For element-level waits, we recommend that consumers overwrite the default to describe the specific element. For more information, see the Design tab and the [WCAG documentation on status messages](https://www.w3.org/WAI/WCAG21/Understanding/status-messages.html).

 SkyWaitService
---------------

Type: Service

### Methods

#### `beginBlockingPageWait(): void`

Starts a blocking page wait on the page.

#### Returns

`void`

#### `beginNonBlockingPageWait(): void`

Starts a non-blocking page wait on the page.

#### Returns

`void`

#### `blockingWrap(observable: Observable<T>): Observable<T>`

Launches a page wait and automatically stops when the specific asynchronous event completes.

#### Parameters

##### `observable: Observable<T>`

#### Returns

`Observable<T>`

#### `clearAllPageWaits(): void`

Clears all blocking and non-blocking page waits on the page.

#### Returns

`void`

#### `endBlockingPageWait(): void`

Ends a blocking page wait on the page. Blocking page wait indication is removed when all running blocking page waits are ended.

#### Returns

`void`

#### `endNonBlockingPageWait(): void`

Ends a non-blocking page wait on the page. Non-blocking page wait indication is removed when all running non-blocking page waits are ended.

#### Returns

`void`

#### `nonBlockingWrap(observable: Observable<T>): Observable<T>`

Launches a non-blocking page wait and automatically stops when the specific asynchronous event completes.

#### Parameters

##### `observable: Observable<T>`

#### Returns

`Observable<T>`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyWaitHarness
---------------

Type: Class

`import { SkyWaitHarness } from '@skyux/indicators/testing';`

Harness for interacting with a wait component in tests.

### Methods

#### `getAriaLabel(): Promise<string>`

Gets the ARIA label for the wait component or throws an error if not waiting.

#### Returns

`Promise<string>`

#### `isFullPage(): Promise<boolean>`

Gets the full page state of the wait component.

#### Returns

`Promise<boolean>`

#### `isNonBlocking(): Promise<boolean>`

Gets the blocking state of the wait component.

#### Returns

`Promise<boolean>`

#### `isWaiting(): Promise<boolean>`

Gets the waiting state of the wait component.

#### Returns

`Promise<boolean>`

#### `SkyWaitHarness.with(filters: SkyWaitHarnessFilters): HarnessPredicate<SkyWaitHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyWaitHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyWaitHarnessFilters`

#### Returns

`HarnessPredicate<SkyWaitHarness>`

 SkyWaitHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyWaitHarness](/skyux/components/wait?docs-active-tab=design#class_sky-wait-harness.md) instances.

    interface SkyWaitHarnessFilters {
      dataSkyId?: string | RegExp;
      servicePageWaitType?: "blocking" | "non-blocking";
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `servicePageWaitType?: "blocking" | "non-blocking"`

Only find blocking or non-blocking instances created by the `SkyWaitService`.
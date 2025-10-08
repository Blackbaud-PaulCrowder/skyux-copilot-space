# Design

                 Skip to Main Content

 Sectioned form
==============

Sectioned forms combine multiple forms and display large amounts of related information inside large modals.

 Usage
------

### Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen [modals](/skyux/components/modal.md) to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized [modals](/skyux/components/modal.md) because the component requires the horizontal space that large-sized and full-screen modals provide.

 Behavior
---------

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

The button in the footer of the modal only appears when the modal reaches a small enough breakpoint.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/sectioned-form/sectioned-form.module.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkySectionedFormModule
-----------------------

Type: Module

`import { SkySectionedFormModule } from '@skyux/tabs';`

 SkySectionedFormComponent
--------------------------

Type: Component

Selector: `sky-sectioned-form`

Creates a container for the sectioned forms.

### Inputs

#### `maintainSectionContent: boolean | undefined`

Whether the sectioned form loads section content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `messageStream: Subject<SkySectionedFormMessage>`

### Outputs

#### `indexChanged: EventEmitter<number>`

Fires when the active tab changes and emits the index of the active section. The index is based on the section's position when the form loads.

#### `tabsVisibleChanged: EventEmitter<boolean>`

Fires when the sectioned form tabs are shown or hidden.

 SkySectionedFormSectionComponent
---------------------------------

Type: Component

Selector: `sky-sectioned-form-section`

Creates an individual form to display as a section within the sectioned form.

### Inputs

#### `heading: string | undefined`

Required

The section header.

#### `active: boolean | undefined`

Whether the section is active when the form loads.

Default: `false`

#### `itemCount: number | undefined`

The number of items within the section. A counter appears beside the section header.

 SkySectionedFormService
------------------------

Type: Service

### Methods

#### `invalidFieldChanged(isInvalid: boolean | undefined): void`

Sets the current section's invalid state based on the `isInvalid` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isInvalid: boolean | undefined`

#### Returns

`void`

#### `requiredFieldChanged(isRequired: boolean | undefined): void`

Sets the current section's required state based on the `isRequired` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isRequired: boolean | undefined`

#### Returns

`void`

 SkySectionedFormMessage
------------------------

Type: Interface

    interface SkySectionedFormMessage {
      type: ShowTabs;
    }

### Properties

#### `type: ShowTabs`

 SkySectionedFormMessageType
----------------------------

Type: Enumeration

    enum SkySectionedFormMessageType {
      ShowTabs = 1,
    }

### Properties

#### `SkySectionedFormMessageType.ShowTabs`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySectionedFormHarness
------------------------

Type: Class

`import { SkySectionedFormHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form component in tests.

### Methods

#### `getActiveSection(): Promise<undefined | SkySectionedFormSectionHarness>`

Gets the `SkySectionedFormSectionHarness` for the currently active section.

#### Returns

`Promise<undefined | SkySectionedFormSectionHarness>`

#### `getActiveSectionContent(): Promise<undefined | SkySectionedFormSectionContentHarness>`

#### Returns

`Promise<undefined | SkySectionedFormSectionContentHarness>`

#### `getSection(filters: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness>`

Gets a specific section based on the filter criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness>`

#### `getSections(filters?: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness[]>`

Gets an array of sections based on the filter criteria. If no filter is provided, returns all sections.

#### Parameters

##### `filters?: SkySectionedFormSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness[]>`

#### `isSectionsVisible(): Promise<boolean>`

Whether the section tabs are visible. In mobile view, sectioned forms collapse to just content pane.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormHarness.with(filters: SkySectionedFormHarnessFilters): HarnessPredicate<SkySectionedFormHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormHarness>`

 SkySectionedFormHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

    interface SkySectionedFormHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySectionedFormSectionHarness
-------------------------------

Type: Class

`import { SkySectionedFormSectionHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form section component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the section to activate.

#### Returns

`Promise<void>`

#### `getSectionContent(): Promise<SkySectionedFormSectionContentHarness>`

Gets the `SkySectionedFormSectionContentHarness` for this section.

#### Returns

`Promise<SkySectionedFormSectionContentHarness>`

#### `getSectionHeading(): Promise<string>`

Gets the section heading.

#### Returns

`Promise<string>`

#### `getSectionItemCount(): Promise<number>`

Gets the section item count.

#### Returns

`Promise<number>`

#### `isActive(): Promise<boolean>`

Whether the section is active.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormSectionHarness.with(filters: SkySectionedFormSectionHarnessFilters): HarnessPredicate<SkySectionedFormSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionHarness>`

 SkySectionedFormSectionHarnessFilters
--------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

    interface SkySectionedFormSectionHarnessFilters {
      dataSkyId?: string | RegExp;
      sectionHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `sectionHeading?: string`

Finds a section whose heading matches the given value.

 SkySectionedFormSectionContentHarness
--------------------------------------

Type: Class

`import { SkySectionedFormSectionContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form content in tests.

### Methods

#### `isVisible(): Promise<boolean>`

Whether the section content is visible.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkySectionedFormSectionContentHarness.with(filters: SkySectionedFormSectionContentHarnessFilters): HarnessPredicate<SkySectionedFormSectionContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionContentHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionContentHarness>`

 SkySectionedFormSectionContentHarnessFilters
---------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

    interface SkySectionedFormSectionContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                 Skip to Main Content

 Sectioned form
==============

Sectioned forms combine multiple forms and display large amounts of related information inside large modals.

 Usage
------

### Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen [modals](/skyux/components/modal.md) to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized [modals](/skyux/components/modal.md) because the component requires the horizontal space that large-sized and full-screen modals provide.

 Behavior
---------

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

The button in the footer of the modal only appears when the modal reaches a small enough breakpoint.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/sectioned-form/sectioned-form.module.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkySectionedFormModule
-----------------------

Type: Module

`import { SkySectionedFormModule } from '@skyux/tabs';`

 SkySectionedFormComponent
--------------------------

Type: Component

Selector: `sky-sectioned-form`

Creates a container for the sectioned forms.

### Inputs

#### `maintainSectionContent: boolean | undefined`

Whether the sectioned form loads section content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `messageStream: Subject<SkySectionedFormMessage>`

### Outputs

#### `indexChanged: EventEmitter<number>`

Fires when the active tab changes and emits the index of the active section. The index is based on the section's position when the form loads.

#### `tabsVisibleChanged: EventEmitter<boolean>`

Fires when the sectioned form tabs are shown or hidden.

 SkySectionedFormSectionComponent
---------------------------------

Type: Component

Selector: `sky-sectioned-form-section`

Creates an individual form to display as a section within the sectioned form.

### Inputs

#### `heading: string | undefined`

Required

The section header.

#### `active: boolean | undefined`

Whether the section is active when the form loads.

Default: `false`

#### `itemCount: number | undefined`

The number of items within the section. A counter appears beside the section header.

 SkySectionedFormService
------------------------

Type: Service

### Methods

#### `invalidFieldChanged(isInvalid: boolean | undefined): void`

Sets the current section's invalid state based on the `isInvalid` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isInvalid: boolean | undefined`

#### Returns

`void`

#### `requiredFieldChanged(isRequired: boolean | undefined): void`

Sets the current section's required state based on the `isRequired` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isRequired: boolean | undefined`

#### Returns

`void`

 SkySectionedFormMessage
------------------------

Type: Interface

    interface SkySectionedFormMessage {
      type: ShowTabs;
    }

### Properties

#### `type: ShowTabs`

 SkySectionedFormMessageType
----------------------------

Type: Enumeration

    enum SkySectionedFormMessageType {
      ShowTabs = 1,
    }

### Properties

#### `SkySectionedFormMessageType.ShowTabs`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySectionedFormHarness
------------------------

Type: Class

`import { SkySectionedFormHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form component in tests.

### Methods

#### `getActiveSection(): Promise<undefined | SkySectionedFormSectionHarness>`

Gets the `SkySectionedFormSectionHarness` for the currently active section.

#### Returns

`Promise<undefined | SkySectionedFormSectionHarness>`

#### `getActiveSectionContent(): Promise<undefined | SkySectionedFormSectionContentHarness>`

#### Returns

`Promise<undefined | SkySectionedFormSectionContentHarness>`

#### `getSection(filters: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness>`

Gets a specific section based on the filter criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness>`

#### `getSections(filters?: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness[]>`

Gets an array of sections based on the filter criteria. If no filter is provided, returns all sections.

#### Parameters

##### `filters?: SkySectionedFormSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness[]>`

#### `isSectionsVisible(): Promise<boolean>`

Whether the section tabs are visible. In mobile view, sectioned forms collapse to just content pane.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormHarness.with(filters: SkySectionedFormHarnessFilters): HarnessPredicate<SkySectionedFormHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormHarness>`

 SkySectionedFormHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

    interface SkySectionedFormHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySectionedFormSectionHarness
-------------------------------

Type: Class

`import { SkySectionedFormSectionHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form section component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the section to activate.

#### Returns

`Promise<void>`

#### `getSectionContent(): Promise<SkySectionedFormSectionContentHarness>`

Gets the `SkySectionedFormSectionContentHarness` for this section.

#### Returns

`Promise<SkySectionedFormSectionContentHarness>`

#### `getSectionHeading(): Promise<string>`

Gets the section heading.

#### Returns

`Promise<string>`

#### `getSectionItemCount(): Promise<number>`

Gets the section item count.

#### Returns

`Promise<number>`

#### `isActive(): Promise<boolean>`

Whether the section is active.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormSectionHarness.with(filters: SkySectionedFormSectionHarnessFilters): HarnessPredicate<SkySectionedFormSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionHarness>`

 SkySectionedFormSectionHarnessFilters
--------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

    interface SkySectionedFormSectionHarnessFilters {
      dataSkyId?: string | RegExp;
      sectionHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `sectionHeading?: string`

Finds a section whose heading matches the given value.

 SkySectionedFormSectionContentHarness
--------------------------------------

Type: Class

`import { SkySectionedFormSectionContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form content in tests.

### Methods

#### `isVisible(): Promise<boolean>`

Whether the section content is visible.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkySectionedFormSectionContentHarness.with(filters: SkySectionedFormSectionContentHarnessFilters): HarnessPredicate<SkySectionedFormSectionContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionContentHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionContentHarness>`

 SkySectionedFormSectionContentHarnessFilters
---------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

    interface SkySectionedFormSectionContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                   Skip to Main Content

 Sectioned form
==============

Sectioned forms combine multiple forms and display large amounts of related information inside large modals.Usage
------

### Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen [modals](/skyux/components/modal.md) to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized [modals](/skyux/components/modal.md) because the component requires the horizontal space that large-sized and full-screen modals provide.

 Behavior
---------

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

The button in the footer of the modal only appears when the modal reaches a small enough breakpoint.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/sectioned-form/sectioned-form.module.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkySectionedFormModule
-----------------------

Type: Module

`import { SkySectionedFormModule } from '@skyux/tabs';`

 SkySectionedFormComponent
--------------------------

Type: Component

Selector: `sky-sectioned-form`

Creates a container for the sectioned forms.

### Inputs

#### `maintainSectionContent: boolean | undefined`

Whether the sectioned form loads section content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `messageStream: Subject<SkySectionedFormMessage>`

### Outputs

#### `indexChanged: EventEmitter<number>`

Fires when the active tab changes and emits the index of the active section. The index is based on the section's position when the form loads.

#### `tabsVisibleChanged: EventEmitter<boolean>`

Fires when the sectioned form tabs are shown or hidden.

 SkySectionedFormSectionComponent
---------------------------------

Type: Component

Selector: `sky-sectioned-form-section`

Creates an individual form to display as a section within the sectioned form.

### Inputs

#### `heading: string | undefined`

Required

The section header.

#### `active: boolean | undefined`

Whether the section is active when the form loads.

Default: `false`

#### `itemCount: number | undefined`

The number of items within the section. A counter appears beside the section header.

 SkySectionedFormService
------------------------

Type: Service

### Methods

#### `invalidFieldChanged(isInvalid: boolean | undefined): void`

Sets the current section's invalid state based on the `isInvalid` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isInvalid: boolean | undefined`

#### Returns

`void`

#### `requiredFieldChanged(isRequired: boolean | undefined): void`

Sets the current section's required state based on the `isRequired` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isRequired: boolean | undefined`

#### Returns

`void`

 SkySectionedFormMessage
------------------------

Type: Interface

    interface SkySectionedFormMessage {
      type: ShowTabs;
    }

### Properties

#### `type: ShowTabs`

 SkySectionedFormMessageType
----------------------------

Type: Enumeration

    enum SkySectionedFormMessageType {
      ShowTabs = 1,
    }

### Properties

#### `SkySectionedFormMessageType.ShowTabs`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySectionedFormHarness
------------------------

Type: Class

`import { SkySectionedFormHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form component in tests.

### Methods

#### `getActiveSection(): Promise<undefined | SkySectionedFormSectionHarness>`

Gets the `SkySectionedFormSectionHarness` for the currently active section.

#### Returns

`Promise<undefined | SkySectionedFormSectionHarness>`

#### `getActiveSectionContent(): Promise<undefined | SkySectionedFormSectionContentHarness>`

#### Returns

`Promise<undefined | SkySectionedFormSectionContentHarness>`

#### `getSection(filters: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness>`

Gets a specific section based on the filter criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness>`

#### `getSections(filters?: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness[]>`

Gets an array of sections based on the filter criteria. If no filter is provided, returns all sections.

#### Parameters

##### `filters?: SkySectionedFormSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness[]>`

#### `isSectionsVisible(): Promise<boolean>`

Whether the section tabs are visible. In mobile view, sectioned forms collapse to just content pane.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormHarness.with(filters: SkySectionedFormHarnessFilters): HarnessPredicate<SkySectionedFormHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormHarness>`

 SkySectionedFormHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

    interface SkySectionedFormHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySectionedFormSectionHarness
-------------------------------

Type: Class

`import { SkySectionedFormSectionHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form section component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the section to activate.

#### Returns

`Promise<void>`

#### `getSectionContent(): Promise<SkySectionedFormSectionContentHarness>`

Gets the `SkySectionedFormSectionContentHarness` for this section.

#### Returns

`Promise<SkySectionedFormSectionContentHarness>`

#### `getSectionHeading(): Promise<string>`

Gets the section heading.

#### Returns

`Promise<string>`

#### `getSectionItemCount(): Promise<number>`

Gets the section item count.

#### Returns

`Promise<number>`

#### `isActive(): Promise<boolean>`

Whether the section is active.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormSectionHarness.with(filters: SkySectionedFormSectionHarnessFilters): HarnessPredicate<SkySectionedFormSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionHarness>`

 SkySectionedFormSectionHarnessFilters
--------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

    interface SkySectionedFormSectionHarnessFilters {
      dataSkyId?: string | RegExp;
      sectionHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `sectionHeading?: string`

Finds a section whose heading matches the given value.

 SkySectionedFormSectionContentHarness
--------------------------------------

Type: Class

`import { SkySectionedFormSectionContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form content in tests.

### Methods

#### `isVisible(): Promise<boolean>`

Whether the section content is visible.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkySectionedFormSectionContentHarness.with(filters: SkySectionedFormSectionContentHarnessFilters): HarnessPredicate<SkySectionedFormSectionContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionContentHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionContentHarness>`

 SkySectionedFormSectionContentHarnessFilters
---------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

    interface SkySectionedFormSectionContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Sectioned form inside modal

Edit in StackBlitz

Open sectioned form

Show code

Copy

    import { ChangeDetectionStrategy, Component } from '@angular/core';
    
    @Component({
      standalone: true,
      selector: 'app-address-form',
      template: `<div>Address form</div>`,
      changeDetection: ChangeDetectionStrategy.OnPush,
    })
    export class AddressFormComponent {}
Copy

    <button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
      Open sectioned form
    </button>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyInputBoxHarness } from '@skyux/forms/testing';
    import { SkySectionedFormHarness } from '@skyux/tabs/testing';
    
    import { TabsSectionedFormModalExampleComponent } from './example.component';
    
    describe('Sectioned form in a modal example', () => {
      async function setupTest(): Promise<{
        sectionedFormHarness: SkySectionedFormHarness;
        fixture: ComponentFixture<TabsSectionedFormModalExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [TabsSectionedFormModalExampleComponent, NoopAnimationsModule],
        }).compileComponents();
        const fixture = TestBed.createComponent(
          TabsSectionedFormModalExampleComponent,
        );
        fixture.componentInstance.openModal();
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const sectionedFormHarness: SkySectionedFormHarness =
          await loader.getHarness(
            SkySectionedFormHarness.with({ dataSkyId: 'modal-sectioned-form' }),
          );
    
        return { sectionedFormHarness, fixture };
      }
    
      it('should set up the sectioned form', async () => {
        const { sectionedFormHarness } = await setupTest();
        let activeSection = await sectionedFormHarness.getActiveSection();
        await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
          'Addresses',
        );
        await expectAsync(activeSection?.getSectionItemCount()).toBeResolvedTo(2);
    
        await (
          await sectionedFormHarness.getSection({
            sectionHeading: 'Basic information',
          })
        ).click();
    
        await expectAsync(activeSection?.isActive()).toBeResolvedTo(false);
    
        activeSection = await sectionedFormHarness.getActiveSection();
        await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
          'Basic information',
        );
    
        const activeContent = await sectionedFormHarness.getActiveSectionContent();
    
        const idField = await (
          await activeContent?.queryHarness(
            SkyInputBoxHarness.with({ dataSkyId: 'id-field' }),
          )
        )?.querySelector('input');
    
        await expectAsync(idField?.getProperty('value')).toBeResolvedTo('5324901');
      });
    });
Copy

    <form novalidate [formGroup]="formGroup">
      <sky-fluid-grid gutterSize="small" [disableMargin]="true">
        <sky-row>
          <sky-column [screenXSmall]="6">
            <sky-input-box data-sky-id="name-field" labelText="Name" stacked="true">
              <input formControlName="name" type="text" />
            </sky-input-box>
          </sky-column>
          <sky-column [screenXSmall]="6">
            <sky-input-box data-sky-id="id-field" labelText="ID" stacked="true">
              <input formControlName="id" type="text" />
              <span class="sky-error-indicator">
                @if (formGroup.get('id')?.invalid) {
                  <sky-status-indicator
                    indicatorType="danger"
                    descriptionType="error"
                  >
                    Enter a valid value.
                  </sky-status-indicator>
                }
              </span>
            </sky-input-box>
          </sky-column>
        </sky-row>
      </sky-fluid-grid>
    </form>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      OnInit,
      inject,
    } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      ReactiveFormsModule,
      Validators,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyStatusIndicatorModule } from '@skyux/indicators';
    import { SkyFluidGridModule } from '@skyux/layout';
    import { SkySectionedFormService } from '@skyux/tabs';
    
    @Component({
      selector: 'app-information-form',
      templateUrl: './information-form.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [
        ReactiveFormsModule,
        SkyInputBoxModule,
        SkyFluidGridModule,
        SkyStatusIndicatorModule,
      ],
    })
    export class InformationFormComponent implements OnInit {
      protected id = '5324901';
      protected formGroup: FormGroup<{
        name: FormControl<string>;
        nameRequired: FormControl<boolean>;
        id: FormControl<string>;
      }>;
      protected name = '';
      protected nameRequired = false;
    
      readonly #sectionedFormSvc = inject(SkySectionedFormService);
      readonly #changeDetector = inject(ChangeDetectorRef);
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          name: new FormControl(this.name, { nonNullable: true }),
          nameRequired: new FormControl(this.nameRequired, { nonNullable: true }),
          id: new FormControl(this.id, {
            nonNullable: true,
            validators: [Validators.pattern('^[0-9]+$')],
          }),
        });
      }
    
      public ngOnInit(): void {
        this.formGroup.valueChanges.subscribe((changes) => {
          this.id = changes.id ?? '';
          this.name = changes.name ?? '';
          this.nameRequired = !!changes.nameRequired;
          this.#checkValidity();
        });
    
        this.#changeDetector.markForCheck();
      }
    
      #checkValidity(): void {
        if (this.nameRequired) {
          this.formGroup.get('name')?.setValidators([Validators.required]);
          this.#sectionedFormSvc.requiredFieldChanged(true);
        } else {
          this.formGroup.get('name')?.setValidators([]);
          this.#sectionedFormSvc.requiredFieldChanged(false);
        }
    
        if (!this.formGroup.get('name')?.value && this.nameRequired) {
          this.#sectionedFormSvc.invalidFieldChanged(true);
        } else {
          this.#sectionedFormSvc.invalidFieldChanged(false);
        }
      }
    }
Copy

    <sky-modal [headingText]="'Sectioned form — Index: ' + activeIndexDisplay">
      <sky-modal-content>
        <sky-sectioned-form
          data-sky-id="modal-sectioned-form"
          [messageStream]="sectionedFormController"
          (indexChanged)="onIndexChanged($event)"
          (tabsVisibleChanged)="onTabsVisibleChanged($event)"
        >
          <sky-sectioned-form-section heading="Basic information">
            <app-information-form />
          </sky-sectioned-form-section>
          <sky-sectioned-form-section
            heading="Addresses"
            [itemCount]="2"
            [active]="activeTab"
          >
            <app-address-form />
          </sky-sectioned-form-section>
          <sky-sectioned-form-section heading="Phone numbers" [itemCount]="3">
            <app-phone-form />
          </sky-sectioned-form-section>
        </sky-sectioned-form>
      </sky-modal-content>
      <sky-modal-footer>
        @if (tabsHidden) {
          <button
            class="sky-btn sky-btn-default"
            type="button"
            (click)="showTabs()"
          >
            <sky-icon iconName="chevron-left" />
            Show sections
          </button>
        }
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="modalInstance.save()"
        >
          Save
        </button>
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="modalInstance.cancel()"
        >
          Cancel
        </button>
      </sky-modal-footer>
    </sky-modal>
Copy

    import {
      ChangeDetectionStrategy,
      ChangeDetectorRef,
      Component,
      inject,
    } from '@angular/core';
    import { SkyIconModule } from '@skyux/icon';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    import {
      SkySectionedFormMessage,
      SkySectionedFormMessageType,
      SkySectionedFormModule,
    } from '@skyux/tabs';
    
    import { Subject } from 'rxjs';
    
    import { AddressFormComponent } from './address-form.component';
    import { InformationFormComponent } from './information-form.component';
    import { PhoneFormComponent } from './phone-form.component';
    
    @Component({
      selector: 'app-modal',
      templateUrl: './modal.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [
        AddressFormComponent,
        InformationFormComponent,
        PhoneFormComponent,
        SkyIconModule,
        SkyModalModule,
        SkySectionedFormModule,
      ],
    })
    export class ModalComponent {
      protected activeIndexDisplay: number | undefined;
      protected activeTab = true;
      protected sectionedFormController = new Subject<SkySectionedFormMessage>();
      protected tabsHidden = false;
    
      protected readonly modalInstance = inject(SkyModalInstance);
      readonly #changeDetector = inject(ChangeDetectorRef);
    
      protected onIndexChanged(newIndex: number): void {
        this.activeIndexDisplay = newIndex;
        this.#changeDetector.markForCheck();
      }
    
      protected onTabsVisibleChanged(visible: boolean): void {
        this.tabsHidden = !visible;
      }
    
      protected showTabs(): void {
        this.sectionedFormController.next({
          type: SkySectionedFormMessageType.ShowTabs,
        });
      }
    }
Copy

    import { ChangeDetectionStrategy, Component } from '@angular/core';
    
    @Component({
      standalone: true,
      selector: 'app-phone-form',
      template: `<div>Phone form</div>`,
      changeDetection: ChangeDetectionStrategy.OnPush,
    })
    export class PhoneFormComponent {}

Copy

    import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
    import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';
    
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Sectioned form inside modal
     */
    @Component({
      standalone: true,
      selector: 'app-tabs-sectioned-form-modal-example',
      templateUrl: './example.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
    })
    export class TabsSectionedFormModalExampleComponent {
      readonly #modalSvc = inject(SkyModalService);
    
      public openModal(): void {
        const modalInstance = this.#modalSvc.open(ModalComponent, {
          size: 'large',
        });
    
        modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
          if (result.reason === 'cancel') {
            console.log(`Modal cancelled`);
          } else if (result.reason === 'save') {
            console.log(`Modal saved`);
          }
        });
      }
    }

# Testing

                 Skip to Main Content

 Sectioned form
==============

Sectioned forms combine multiple forms and display large amounts of related information inside large modals.

 Usage
------

### Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen [modals](/skyux/components/modal.md) to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized [modals](/skyux/components/modal.md) because the component requires the horizontal space that large-sized and full-screen modals provide.

 Behavior
---------

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

The button in the footer of the modal only appears when the modal reaches a small enough breakpoint.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/tabs`[View in NPM](https://www.npmjs.com/package/@skyux/tabs) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/tabs/src/lib/modules/sectioned-form/sectioned-form.module.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/tabs`Copy None found.

 SkySectionedFormModule
-----------------------

Type: Module

`import { SkySectionedFormModule } from '@skyux/tabs';`

 SkySectionedFormComponent
--------------------------

Type: Component

Selector: `sky-sectioned-form`

Creates a container for the sectioned forms.

### Inputs

#### `maintainSectionContent: boolean | undefined`

Whether the sectioned form loads section content during initialization so that it displays content without moving around elements in the content container.

Default: `false`

#### `messageStream: Subject<SkySectionedFormMessage>`

### Outputs

#### `indexChanged: EventEmitter<number>`

Fires when the active tab changes and emits the index of the active section. The index is based on the section's position when the form loads.

#### `tabsVisibleChanged: EventEmitter<boolean>`

Fires when the sectioned form tabs are shown or hidden.

 SkySectionedFormSectionComponent
---------------------------------

Type: Component

Selector: `sky-sectioned-form-section`

Creates an individual form to display as a section within the sectioned form.

### Inputs

#### `heading: string | undefined`

Required

The section header.

#### `active: boolean | undefined`

Whether the section is active when the form loads.

Default: `false`

#### `itemCount: number | undefined`

The number of items within the section. A counter appears beside the section header.

 SkySectionedFormService
------------------------

Type: Service

### Methods

#### `invalidFieldChanged(isInvalid: boolean | undefined): void`

Sets the current section's invalid state based on the `isInvalid` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isInvalid: boolean | undefined`

#### Returns

`void`

#### `requiredFieldChanged(isRequired: boolean | undefined): void`

Sets the current section's required state based on the `isRequired` parameter. This method is used within a `sky-sectioned-form-section` element.

#### Parameters

##### `isRequired: boolean | undefined`

#### Returns

`void`

 SkySectionedFormMessage
------------------------

Type: Interface

    interface SkySectionedFormMessage {
      type: ShowTabs;
    }

### Properties

#### `type: ShowTabs`

 SkySectionedFormMessageType
----------------------------

Type: Enumeration

    enum SkySectionedFormMessageType {
      ShowTabs = 1,
    }

### Properties

#### `SkySectionedFormMessageType.ShowTabs`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySectionedFormHarness
------------------------

Type: Class

`import { SkySectionedFormHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form component in tests.

### Methods

#### `getActiveSection(): Promise<undefined | SkySectionedFormSectionHarness>`

Gets the `SkySectionedFormSectionHarness` for the currently active section.

#### Returns

`Promise<undefined | SkySectionedFormSectionHarness>`

#### `getActiveSectionContent(): Promise<undefined | SkySectionedFormSectionContentHarness>`

#### Returns

`Promise<undefined | SkySectionedFormSectionContentHarness>`

#### `getSection(filters: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness>`

Gets a specific section based on the filter criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness>`

#### `getSections(filters?: SkySectionedFormSectionHarnessFilters): Promise<SkySectionedFormSectionHarness[]>`

Gets an array of sections based on the filter criteria. If no filter is provided, returns all sections.

#### Parameters

##### `filters?: SkySectionedFormSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySectionedFormSectionHarness[]>`

#### `isSectionsVisible(): Promise<boolean>`

Whether the section tabs are visible. In mobile view, sectioned forms collapse to just content pane.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormHarness.with(filters: SkySectionedFormHarnessFilters): HarnessPredicate<SkySectionedFormHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormHarness>`

 SkySectionedFormHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

    interface SkySectionedFormHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySectionedFormSectionHarness
-------------------------------

Type: Class

`import { SkySectionedFormSectionHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form section component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the section to activate.

#### Returns

`Promise<void>`

#### `getSectionContent(): Promise<SkySectionedFormSectionContentHarness>`

Gets the `SkySectionedFormSectionContentHarness` for this section.

#### Returns

`Promise<SkySectionedFormSectionContentHarness>`

#### `getSectionHeading(): Promise<string>`

Gets the section heading.

#### Returns

`Promise<string>`

#### `getSectionItemCount(): Promise<number>`

Gets the section item count.

#### Returns

`Promise<number>`

#### `isActive(): Promise<boolean>`

Whether the section is active.

#### Returns

`Promise<boolean>`

#### `SkySectionedFormSectionHarness.with(filters: SkySectionedFormSectionHarnessFilters): HarnessPredicate<SkySectionedFormSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionHarness>`

 SkySectionedFormSectionHarnessFilters
--------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

    interface SkySectionedFormSectionHarnessFilters {
      dataSkyId?: string | RegExp;
      sectionHeading?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `sectionHeading?: string`

Finds a section whose heading matches the given value.

 SkySectionedFormSectionContentHarness
--------------------------------------

Type: Class

`import { SkySectionedFormSectionContentHarness } from '@skyux/tabs/testing';`

Harness for interacting with a sectioned form content in tests.

### Methods

#### `isVisible(): Promise<boolean>`

Whether the section content is visible.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkySectionedFormSectionContentHarness.with(filters: SkySectionedFormSectionContentHarnessFilters): HarnessPredicate<SkySectionedFormSectionContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySectionedFormSectionContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySectionedFormSectionContentHarnessFilters`

#### Returns

`HarnessPredicate<SkySectionedFormSectionContentHarness>`

 SkySectionedFormSectionContentHarnessFilters
---------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

    interface SkySectionedFormSectionContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.
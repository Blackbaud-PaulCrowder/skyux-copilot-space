              

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [User assistance](/skyux/design/guidelines/user-assistance.md)

User assistance
===============

When users perform tasks and explore functionality, they may require guidance. To determine how much guidance to provide, you must account for the complexity of the task, the complexity of the user interface, and the expected knowledge of users. User assistance design patterns help determine when and how to present help content to users.

Usage
-----

SKY UX design patterns include four primary techniques to display help content: empty-state help, inline help, the preloaded help widget, and preloaded popovers. To determine the appropriate technique for user assistance, consider the complexity of the task and the expected knowledge of users. The chart below provides a matrix to determine the type of user assistance to provide in different scenarios. Do not overuse help content because it can overwhelm or inhibit users. For example, only preload the help widget or popovers when user research supports the need for those techniques. When in doubt, err on the side of empty-state help and inline help.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/help-chart.b6ae6ed22308f143e523604d675ac4c2.png)

Empty-state help
----------------

### Usage

Empty-state help provides user assistance when content containers are not populated. The content can include a title, body copy, and buttons to take actions or access additional resources. The help content does not appear when content containers are populated.

Empty-state help content explains how users can take advantage of the functionality in question, and it follows these guidelines:

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/empty-state-call-to-action.ac662c9a7861ae1a921aa399f988c2cf.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/empty-state-plain-1.6a95b5883df83d7eddad508b39b35101.png)

*   Make help content unique to the content container in question. Empty-state help provides information that is specific to the current scenario, and it usually includes a specific call to action. Do not use empty-state help to display boilerplate content that you can modify and reuse in multiple scenarios.
*   In the title, use a conversational tone and explicitly state any call to action. Use [the `sky-font-emphasized` class](/skyux/design/styles/typography.md).
*   In the body copy, expand on the title as necessary and provide additional details that users need to know. Use [the `sky-font-body-default` class](/skyux/design/styles/typography.md).
*   For the button, use the [secondary button class](/skyux/components/button.md) to open a modal where users can complete the experience inline. If users cannot complete the experience inline and must navigate elsewhere, use the [link button class](/skyux/components/button.md) instead. Secondary buttons indicate modals, while links indicate navigation.
*   For an empty container where a call to action does not apply, identify the container with centered text using [the `sky-font-deemphasized` class](/skyux/design/styles/typography.md). Do not include other content such as controls or actions.
*   For Blackbaud designers and developers, we also recommend that you engage a writer on the Strategic Content Development team to help write or review the help content.

### Layout

Center empty-state help in its content container.

Inline help
-----------

### Invoked inline help

#### Usage

Invoked inline help gives users access to help content when needed while avoiding most of the visual noise that comes with persistent inline help text.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/usage-help-button.decc5a3626d65ff26c000bd126e066f2.png)

Do use help buttons to invoke help content.

Use invoked inline help when users may need initial assistance but:

*   The tasks are performed frequently.
*   Ramifications of mistakes are small.

In general, use [help inline buttons](/skyux/components/help-inline.md) to invoke the help content in [popovers](/skyux/components/popover.md), [flyouts](/skyux/components/flyout.md), or the [help widget](https://docs.blackbaud.com/bb-help-docs/). Use a [flyout](/skyux/components/flyout.md) for longer content that doesn't fit in a [popover](/skyux/components/popover.md). Blackbaud developers should use the [help widget](https://docs.blackbaud.com/bb-help-docs/) for longer content, which is for internal Blackbaud use only.

#### Layout

Page-level and modal-level help

For complex tasks where users require comprehensive documentation for the entire task, they invoke help at the page or modal level.

In Blackbaud solutions, users can invoke the help service from the omnibar or a [modal](/skyux/components/modal.md) title. To display context-sensitive help content, Blackbaud developers can use [the help widget](). This feature is for internal Blackbaud use only.

Element-level help

Place the help inline button to the right of the label for the element that the help content supports.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/element-level-help.9d2940497f412d424912381d61c497b1.png)

Do use help inline buttons to invoke element-specific help content.

### Persistent inline help

#### Usage

Sometimes a small amount of persistent inline text can help users understand tasks. Use persistent inline help when:

*   Tasks are complex and performed infrequently.
*   User actions have far-reaching consequences that are not obvious.

Use the `hintText` option in form input components for persistent inline help, and limit the content to one or two sentences to minimize the visual weight of the text.

#### Layout

Place persistent inline help text alongside the top-level elment that it supports. For example, persistent inline help for an overarching task belongs at the top of the form, while field-level help needs to be inline with the field. For more information, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

#### Forms

1

Form-level help (optional)

2

Group-level help (optional)

3

Field-level text (optional)

4

Label-level help (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/persistent-inline-help-forms.74aa23e9fd0cba2e58661b976c32f9e1.png)

#### Containers

Place persistent inline help for containers, such as [tab panels](/skyux/components/tabs.md), [split view workspace panels](/skyux/components/split-view.md), and [modals](/skyux/components/modal.md), at the top of containers. For example, place help for tab panels just below the tabs and above all other tab content.

Be concise and use persistent inline help to provide context about the container's purpose.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/persistent-inline-help-containers.5bd2bf453c34111d444fc0e0c402a24a.png)

Preloaded popovers
------------------

### Usage

[Popovers](/skyux/components/popover.md) are a great way to display contextual content on pages or modals, and you can programmatically preload popovers to display user assistance when pages or modals load. This technique allows you to guide users toward subtle-but-important elements when tasks include complex or unfamiliar capabilities. It is appropriate to preload popovers with help content when:

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/popover-example.a0c6305147a350c56cc7f41ccceacbe2.png)

*   Elements are important but easily overlooked. For example, use preloaded popovers for new filter options, view switchers, or isolated context menus.
*   Elements requires special attention when they load because user research indicates problems with discoverability.

Popovers are also useful [for invoked inline help](/skyux/design/guidelines/user-assistance#inline-help.md). For tasks with familiar or basic capabilities, they allow users to display contextual content when they interact with trigger elements.

Preloaded help widget
---------------------

### Usage

To display context-sensitive help content, Blackbaud developers can use [the help widget](). This feature is for internal Blackbaud use only.

Blackbaud developers can preload the help widget to display user assistance when a page loads. This technique allows you to display help content that is tailored to the first time that users load the page. Use this technique to introduce users to new or novel functionality. Do not use it to walk users through processes.

The Help Widget is also useful [for invoked inline help](/skyux/design/guidelines/user-assistance#inline-help.md). For tasks with familiar or basic capabilities, it allows users to display context-sensitive help content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/userassistance/help-flyout.a86c9910463761eefd3a7514d6dc6fc2.png)
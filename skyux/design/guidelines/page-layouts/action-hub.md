             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Page design](/skyux/design/guidelines/page-layouts.md)
5.  [Action hub](/skyux/design/guidelines/page-layouts/action-hub.md)

Action hub
==========

Action hubs direct user attention to important actions and provide quick access to common tasks. They aggregate entry points into tasks that might otherwise be spread across multiple pages.

Usage
-----

### Use when

Use [action hubs](/skyux/components/action-hub.md) to present prescriptive calls to action for things users must, should, or could do within an area of the system. They are often appropriate as landing pages for main navigation items but can also be descendant pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/action-hub-use-when.f5702fcb50f8fd613b9c18faf8e951db.png)

Do use action hubs to present prescriptive calls to action.

### Don't use when

Don't use action hubs to present information that is not actionable. Analyze information for users to provide context and make it actionable.

Anatomy
-------

1

Page heading

2

Related links

3

Needs attention

4

Recently accessed

5

Content area

6

Common actions (optional)

7

Settings (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/action-hub-anatomy.01bf467e0d29a369fc5f6fde6c5dbb07.png)

Options
-------

### Common actions

You can include up to three secondary buttons to provide quick access to common tasks, such as adding a record. If you need to group multiple related actions, use a menu button.

Content
-------

### Needs attention

Display actions that users must perform based on business requirements or best practices, and link users to the place where they can complete the action, such as a [modal](/skyux/components/modal.md), [split view page](/skyux/design/guidelines/page-layouts/split-view-page.md), or [record page](/skyux/design/guidelines/page-layouts/record-page.md).

Start each item in the list with a verb that communicates the action to perform. After the verb, include the number of items that require attention and a succinct description.

Order the items by workflow order, or by importance if they are not part of the same workflow.

Consider ways to operationalize strategic tasks by breaking them down into smaller, achievable chunks of work.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/needs-attention-order-600.f7d13bf69af6b36c894d1486ed949008.png)

Do order items by workflow or importance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/needs-attention-achievable-600.33831790ebc533cf639cd485175b8628.png)

Do break tasks into achievable chunks.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/needs-attention-unachievable-600.538420d9933d78ba6443e7a82bbe2500.png)

Don't present unrealistic or overly ambitious tasks.

### Content area

Additional content should reflect one of the following sets of principles.

#### Operational but optional

Content that is operational but optional should:

*   be operational in nature, reflecting work that the user does on a regular basis to run the business
*   provide contextual information to help the user decide whether to act
*   be elevated to a needs attention item after a specific threshold is met

#### Strategic and prescriptive

Content that is strategic and prescriptive should:

*   be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
*   prescribe one or more actions which may take place inside or outside the system
*   be synthesized and provide a context for comparison — don't require the user to figure out what the information means

#### Strategic and tied to a needs attention item

Content that is strategic and tied to a needs attention item should:

*   be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
*   represent progress towards an outcome that is impacted by a least one existing needs attention item
*   be synthesized and provide a context for comparison — don't require the user to figure out what the information means

#### Key information call to action

Use key information calls to action when the condition for prescribing an action can be distilled to a single piece of information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/content-section-keyinfo-cta-600.c4e74adf8329b1cf57c5a9ecb4583ba1.png)

#### Charts

Action hubs are not intended for analytical tasks. If you include charts, scope the data set to the appropriate strategic or operational view for the user. You can use one filter if necessary to swap between relevant contexts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/content-section-chart-context-cta-600.81b09016cdbee106e4db7e19931c7ade.png)

Do use charts to provide decision-making context for optional operational tasks.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/content-section-chart-history-600.f07f06167f0c813d0325320dc20ff7a7.png)

Do use charts to show categorical or time-based views of strategic information.

### Page links

Groups of links to include and display in the following order.

#### Related links

Display up to 10 links to related pages in alphabetical order.

#### Recently accessed

Display up to five items in reverse chronological order to indicate what users accessed most recently.

#### Settings

Optionally include links to the settings applicable to functionality within the action hub and its descendant pages.

Behavior and states
-------------------

### Needs attention

#### Navigation

Link needs attention items to the place where users can complete the action, such as a [modal](/skyux/components/modal.md), [split view page](/skyux/design/guidelines/page-layouts/split-view-page.md), or [record page](/skyux/design/guidelines/page-layouts/record-page.md).

#### Empty state

When no needs attention items are available, an [empty state message](/skyux/design/guidelines/user-assistance#empty-state-help.md) indicates that users are caught up.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/needs-attention-empty-600.5f5e9218db5b27300f26c925381b1343.png)

#### Columns

When more than six needs attention items are available in a viewpoint that is 768 pixels or larger, the content splits into two columns.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/needs-attention-2-column.17b7274a54a89d6d2d5fb134ebe31acd.png)

### Settings

Open settings forms in modals.

### Responsiveness

Action hubs reflow content in small viewports.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/action-hub/action-hub-responsive-600.9b0cbf8ae4e49923d5d5cd9a8c68a4b8.png)

Related information
-------------------

### Components

*   [Action hub](/skyux/components/action-hub.md)
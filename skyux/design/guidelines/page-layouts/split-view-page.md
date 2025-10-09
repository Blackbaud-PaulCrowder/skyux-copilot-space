             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Page design](/skyux/design/guidelines/page-layouts.md)
5.  [Split view page](/skyux/design/guidelines/page-layouts/split-view-page.md)

Split view page
===============

Split view pages allow users to work through a list of items.

Usage
-----

### Use when

Use split view pages when users need to work through a list of items, taking action on each of the items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/split-view-page/split-view-page-use-when.f3d946fcd814077dcf706260aef169cc.png)

Do use split view pages when users need to work through a list of items.

### Don't use when

Don't use split view pages when users need to take action on only a small number of items in the list. Use [list pages](/skyux/design/guidelines/page-layouts/list-page.md) instead.

Anatomy
-------

1

[Page](/skyux/components/page.md) using fit layout

2

Page heading

3

[Split view](/skyux/components/split-view.md)

4

Bulk action  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/split-view-page/split-view-page-anatomy.7e1a834e003490658eb6a65fedfa3dcb.png)

Options
-------

### Bulk action

If users may need to take action on all items in the list at once, you can use a bulk action. Before including a bulk action, consider whether the workflow could be redesigned to focus users only on the subset of items that need individual attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/split-view-page/split-view-page-option-global.4f49f662f85f6f8d66abdefe3137e25d.png)

You can use a global action if users may need to take action on all items in the list at once.

### List type

By default, a split view list should use a repeater layout. Other views can be used (such as a tree view for grouped items), but before using a more complex view consider whether the workflow could be redesigned to allow users to make a narrower selection upstream.

Behavior and states
-------------------

### Automatically move to the next record

When users take action on an item, remove that item from the list and open the next item in the workspace.

### Presenting additional information about an item

If users need ancillary information about an item, use a hyperlink to open a [flyout](/skyux/components/flyout.md). Only display information that is specific to the task. Don't display an entire record in the flyout. For the hyperlink, use existing text in the workspace, such as a contact name, not a separate button.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/split-view-page/split-view-page-behavior-flyout.f1d453ab35a97dd55176c4314c3ed80f.png)

You can use flyouts to present ancillary information about an item.

Content
-------

### List item

Use up to three pieces of data to identify the item. If additional content is needed to uniquely identify the item, put it in the workspace view instead of overloading the list item.

### Workspace

Follow existing guidelines to lay out workspace content based on the type of content. Use the same content structure for each item in the list.

### Summary action bar

The summary action bar can contain one primary action, multiple secondary actions, and one tertiary action. Display actions as separate buttons and collapse them to a menu if they don't fit. Use the same actions for each item in the list.

Related information
-------------------

### Components

*   [Button](/skyux/components/button.md)
*   [Flyout](/skyux/components/flyout.md)
*   [Page](/skyux/components/page.md)
*   [Repeater](/skyux/components/repeater.md)
*   [Split view](/skyux/components/split-view.md)
*   [Summary action bar](/skyux/components/summary-action-bar.md)
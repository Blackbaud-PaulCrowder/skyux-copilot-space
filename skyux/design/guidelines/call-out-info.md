            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Call out information](/skyux/design/guidelines/call-out-info.md)

Call out information
====================

The optimal method to highlight information depends on the content and its context.

On this page
============

1.  [Critical messages](/skyux/design/guidelines/call-out-info#critical-messages.md)
2.  [Summary data](/skyux/design/guidelines/call-out-info#summary-data.md)
3.  [Status](/skyux/design/guidelines/call-out-info#status.md)
4.  [Process updates](/skyux/design/guidelines/call-out-info#process-updates.md)

[

Critical messages
-----------------

](/skyux/design/guidelines/call-out-info#critical-messages.md)

To highlight critical information that users absolutely must see when visiting a page, use an [alert](/skyux/components/alert.md) component. If users only need to see an alert once, you can make it dismissible, although you might want to include a way for users to reopen it. Do not make an alert dismissible if it is important for users see every time or if it is triggered by underlying data.

[

Summary data
------------

](/skyux/design/guidelines/call-out-info#summary-data.md)

For dense sets of data, you can create summaries to highlight important points. To call out these points, use a [key info](/skyux/components/key-info.md) component. They draw user attention, and then users can decide whether to dig into the underlying data or rely on the high-level understanding.

[

Status
------

](/skyux/design/guidelines/call-out-info#status.md)

Statuses indicate a state or condition at a particular time and fall into four categories: info, success, warning, and danger. For example, a status can indicate that a submission is late, submitted, or awaiting approval.

Status importance

Some statuses are crucial to user tasks, while others are no more important than other information on a page. If statuses are crucial to user tasks, use [labels](/skyux/components/label.md) or [status indicators](/skyux/components/status-indicator.md). If not, use regular text. Err on the side of too few labels and status indicators; if you use too many, they become distracting and lose their ability to grab user attention.

If one status in an area is crucial, that does not mean all statuses are. For example, in a list of invoices with a mix of paid, unpaid, and overdue invoices, it's likely that only overdue invoices require status indicators because they are the only items that require immediate attention.

Placement

Use [labels](/skyux/components/label.md) in a summary context. For example, you can place a label in a page summary.

Use [status indicators](/skyux/components/status-indicator.md) inline to indicate that they are tied to specific pieces of data. For example, you can place a status indicator in a grid cell.

Status presentation decision tree

![](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/calloutinfo/status-decision-tree.73c3e3162f5669436bb38aa0eb4f28b2.png)

[

Process updates
---------------

](/skyux/design/guidelines/call-out-info#process-updates.md)

To communicate a message that a background process triggers, use a [toast](/skyux/components/toast.md). Background processes include processes that users initiate and system processes that users need to be aware of. Since toasts contain information the user must see, the user must manually dismiss the toast - the toast will not automatically close.
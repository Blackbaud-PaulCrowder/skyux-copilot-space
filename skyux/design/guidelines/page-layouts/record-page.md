             

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Page design](/skyux/design/guidelines/page-layouts.md)
5.  [Record page](/skyux/design/guidelines/page-layouts/record-page.md)

Record page
===========

Record pages support all user tasks related to a record. They can contain different types of views depending on the tasks that users need to complete.

Usage
-----

### Use when

Use record pages when users need to see information about an object aggregated in one place.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page.4d5577259667ab35dce988ef5ac653df.png)

Do use record pages when users need information about an object in one place.

### Don't use when

Don't use record pages when you can predict the actions that users need to take and can provide first-class experiences for those tasks, such as needs attention items in action hubs.

Anatomy
-------

1

[Page](/skyux/components/page.md)

2

Page heading

3

Record content area

4

[Avatar](/skyux/components/avatar.md) (optional)

5

Record details  (optional)

6

Page actions  (optional)

7

[Tabs](/skyux/components/tabs.md) (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-anatomy.6f8d9879c7a7629deab2f7f51174ab83.png)

Options
-------

### Avatar

If images can help users recognize or identify records, you can display a large (100px) [avatar](/skyux/components/avatar.md) at the top left of the record page.

### Record details

Record details supplement the page titles with content that is relevant across all views. Use record details to uniquely identify the record, impact user behavior, or provide context to help users understand the content on the page.

Record details can include components such as a [description list](/skyux/components/description-list.md), [label](/skyux/components/label.md), or [status indicator](/skyux/components/status-indicator.md), but limit the number of elements so that they don't lose their impact or clutter the page. Don't use record details to provide a page summary because summary details about the record belong in a Summary box in the content area's Overview tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/record-details-content-modern.eaef8e6ebdbcdf907c7d080abfd25bfe.png)

Do provide content in the record details to help users understand the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/record-details-content-dont-modern.d52d8fc41dbc3551070d70ba38c624d8.png)

Don't use the record details to provide a page summary.

### Page actions

Page actions affect the parent record and follow [button guidelines](/skyux/design/guidelines/buttons-links.md) for primary and secondary buttons. If actions are specific to child content, invoke them from the relevant content section or item instead.

Place page actions below the record details at the top of the record page. Don't place page actions within a toolbar.

Limit the number of page actions because they can create visual clutter and make it harder to scan the record page.

#### Menu button

For record pages with no primary action and no important or frequently used actions, collapse all page actions in a **Menu** button to give users a place to start when they take actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-actions-menu.84ba71bb555ebe0477be3bd369ab663f.png)

#### More button

For record pages where you need to provide a mix of important or frequently used actions alongside less important or less frequently used actions, display primary and secondary actions in the page actions section and collapse less important or less frequently used actions in a **More** button.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-actions-more.2ea858b8003dc736a7923476a394f28f.png)

#### Edit or delete records

For page actions that edit and delete records, see the [SKY UX patterns for editing or deleting data](/skyux/design/guidelines/managing-records.md).

### Tabs

[Tabs](/skyux/components/tabs.md) on record pages organize content based on tasks or context. Tabs allow users to access different aspects of the record or to complete tasks that include a significant amount of data. Organize tabs according to the specific needs of the record page, with the most important or frequently used tabs on the left.

Overview tab

The first tab on record pages displays [boxes](/skyux/components/box.md) with primary or identifying data as well as summary data that helps users understand the current state of the record and its history. For consistency, use "Overview" as the label.

The box on the top left contains basic details to identify the record, such as the name. For consistency, use "Details" as the label.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-overview-tab-1.a8409033fcd4f13ada9c688c4ce64190.png)

If it helps users to see current status of the record or summary information, you can display a Summary box directly above the Details box in the first column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-overview-tab-2.b6795b33f6690bcc79c66dd36d5c1bad.png)

If a record page benefits from an Overview tab but only requires two or three boxes, display the boxes horizontally instead of stacking them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-page-overview-tab-3.8b0fa1c140701cbf1b4d31d2061f0d52.png)

Other tabs

After the Overview tab, organize and name tabs according to the specific needs of the record. Use simple labels to make sure the purpose is clear to users.

If the record page includes SKY Add-in tabs, place them after the context-specific tabs for the record.

Finally, place common platform tabs last in the following order:

*   Notes
*   Attachments

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/pagelayout/record-page/modern-record-tabs-diagram.a4b939abd390094b6cb6e83570acd83c.png)

Layout
------

### Content area layout

Use a columnar layout with 1:1:1, 1:2, 2:1, or full-width sections as appropriate based on the content.

Related information
-------------------

### Components

*   [Avatar](/skyux/components/avatar.md)
*   [Box](/skyux/components/box.md)
*   [Button](/skyux/components/button.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Page](/skyux/components/page.md)
*   [Tabs](/skyux/components/tabs.md)
              

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Error handling](/skyux/design/guidelines/error-handling.md)

Error handling
==============

Error handling patterns provide guidance on how to present error messages depending on the context.

Style and tone
--------------

Make error and warning messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring. To provide a consistent user experience, use the [error component](/skyux/components/error.md).

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

Accessibility guidelines
------------------------

Don't rely on a single sensory characteristic of components such as shape, size, visual location, orientation, or sound to describe an error or offer a solution. "Above" and "below" are fine for referencing content in the appropriate reading order for the language used as long as the reference isn't ambiguous.

Error messages should be as specific as possible to help the user determine what is wrong.

Error message images
--------------------

The error message images apply to different scenarios and should be used accordingly.

Broken

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/broken.d1414632e8353cc7a7e1c70e36939937.png)

Use this image for:

*   Errors with the modal component, such as when a modal can't launch a form or the modal service is down on save.
*   Errors loading data, such as when a page or tab content doesn't load.
*   500 errors.

Not found

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/notfound.595ddc50302050e1f8f7b21f834c1fdd.png)

Use this image for:

*   Errors loading a page.
*   400 errors.

Under construction

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/construction.af1332f70b6c0099ba72ac8b993aa883.png)

Use this image for:

*   Errors syncing data.
*   Planned downtime.

Security or access rights

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/security.a33924a40711e2d54a722d3433db10d4.png)

Use this image for:

*   Security rights such as when users don't have rights to a page.

Other errors

Do _not_ use an image for:

*   Errors when content won't load in container components, such as boxes.
*   Errors when users can't save changes, such as when actions don't complete.

Page errors
-----------

A variety of page-level errors can occur, usually due to system failures rather than user actions. [The error component](/skyux/components/error.md) includes default content that applies to most scenarios, and the content can be customized if necessary to be more precise or prescriptive.

![Full page with broken error image and message centered on page.](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/page-error.95b6c6b2bf5502566b31c316159634d4.png)

Page element errors
-------------------

Forms

For information about validation and error handling on forms, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

Modals

Modals usually have plenty of space to display error messages, so use [the error component](/skyux/components/error.md).

![Modal with broken error image and message centered in modal.](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/modal-error.46d2f5a856380a7a370c8d9e8aafc1c7.png)

Tabs

Tabs that are used as a secondary navigation usually have views with plenty of available space to display error messages, so use [the error component](/skyux/components/error.md).

![Tabs with broken error image and message centered on page under tabs.](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/tab-error.e5f8d520696b1592d2ed92fe4767d8f9.png)

Boxes

Boxes have limited space and may not be important to users' immediate tasks, so exclude the images and buttons and only display error messages in order to minimize the visual weight.

![Box with error message under the box heading.](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/box-error.d4473eb70a162188657f5c9dfc44a533.png)

Background process errors
-------------------------

Since background processes run outside the current page context, use [toasts](/skyux/components/toast.md) to notify the user of an error with a background process. Toasts appear regardless of which page users are on and persist as they navigate through the system.

![Full page with error message in toast.](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/errorhandling/background-error.c2b0ca2ea9106d39b77819089f86d532.png)

Form errors
-----------

For validation and error handling within forms, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).
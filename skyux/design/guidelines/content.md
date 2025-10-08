            Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Content](/skyux/design/guidelines/content.md)

Content
=======

Text in the user interface (UI) facilitates a conversation between the application and users. SKY UX guidance on UI text reinforces our [design principles](/skyux/design/principles.md) and helps create a consistent, recognizable user experience. The guidance on this page covers general principles and common scenarios, and SKY UX also provides guidelines for specific scenarios elsewhere in the [design guidelines](/skyux/design/guidelines.md) and the [component documentation](/skyux/components.md).

SKY UX guidance for UI text mostly focuses on recurring or exceptional scenarios, and unless otherwise noted, SKY UX follows [Chicago Manual of Style](https://www.chicagomanualofstyle.org/home.html) and [Merriam-Webster](https://www.merriam-webster.com/).

On this page
============

1.  [Voice and tone](/skyux/design/guidelines/content#voice-and-tone.md)
2.  [Grammar and word choice](/skyux/design/guidelines/content#grammar-and-word-choice.md)
3.  [Capitalization](/skyux/design/guidelines/content#capitalization.md)
4.  [Punctuation](/skyux/design/guidelines/content#punctuation.md)
5.  [Labels](/skyux/design/guidelines/content#labels.md)
6.  [Page titles](/skyux/design/guidelines/content#page-titles.md)
7.  [Dates and times](/skyux/design/guidelines/content#dates-and-times.md)
8.  [Related information](/skyux/design/guidelines/content#related-information.md)

[

Voice and tone
--------------

](/skyux/design/guidelines/content#voice-and-tone.md)

A cohesive voice in the UI text creates a recognizable, consistent feeling that is distinct from other user experiences. UI text includes labels, inline help, error messages, and all other text that appears in the user interface.

In SKY UX applications, UI text focuses on user needs and makes every word count to communicate clearly and thoroughly. Blackbaud provides a system of action, not just a system of record, so UI text focuses on workflows, keeps users in context, and structures content around tasks. UI text must be concise and direct, and it uses active voice and short, simple sentences. When writing UI text, follow these principles:

*   Make content scannable and don't draw attention to it. The limited use of attention-getting elements helps drive user behavior.
*   Use verbiage that facilitates the conversation between users and their applications.
*   Emphasize what users can achieve, provide helpful hints, and motivate users to get the most out of the system.
*   Use straightforward, consistent terminology. Avoid synonyms for key terms.
*   Be concise and direct. Limit adjectives, adverbs, and other extraneous verbiage. Keep punctuation simple.
*   Avoid long or complicated phrasing and terms. Present guidance as commands when appropriate.

[

Grammar and word choice
-----------------------

](/skyux/design/guidelines/content#grammar-and-word-choice.md)

### Active voice

Use active voice to improve clarity and to emphasize actions. SKY UX solutions are defined by actions, and active voice describes users and functions as doing things instead of having things done to them. Active voice also makes it clearer who is doing what and leads to simpler, clearer sentences that are more conversational.

**Use active voice:**

"You can't delete this \[item\]."

"Select a valid date."

**Avoid passive voice:**

"This \[item\] can't be deleted."

"The date you select must be valid."

### Contractions

In longer UI text, such as inline help, common contractions are fine and encouraged. They create an informal, conversational tone and don't raise translation or localization concerns. However, avoid uncommon or colloquial contractions, such as "would've" or "ain't."

**Use common contractions:**

"You don't have rights to..."

"This payment isn't eligible for a refund."

**Avoid longer, more formal verbiage:**

"You do not have rights to..."

"This payment is not eligible for a refund."

### Please and sorry

Limit the use of "please" and "sorry" in UI text such as error messages. Overuse can lead users to perceive the words as formulaic or insincere.

### Symbols as word replacements

To ensure consistency and minimize translation issues, don't use symbols in place of words. For example:

*   Use “and” instead of “&.”
*   Use “plus” instead of “+.”
*   Use “number” or “pound” instead of “#.”

The only time to use a symbol in place of a word is when a symbol is part of a company's name or abbreviation, such as AT&T, Gulf + Western, or Proctor & Gamble.

[

Capitalization
--------------

](/skyux/design/guidelines/content#capitalization.md)

Use sentence-style capitalization for headings, labels, and all other UI text. Capitalize the first letter of the first word plus any proper nouns and acronyms, but lowercase everything else.

[

Punctuation
-----------

](/skyux/design/guidelines/content#punctuation.md)

### Colons

Don't use colons or other punctuation at the end of the labels for fields, buttons, and other UI elements.

### Commas

Use commas before the conjunctions in lists (aka the Oxford comma).

### Headings

In general, avoid punctuation at the end of the headings, especially periods.

[

Labels
------

](/skyux/design/guidelines/content#labels.md)

### Actions to create and remove items

Button labels for actions that create or remove items require consistent terminology to send a clear message. In general, actions fall into one of two categories:

1.  Actions create new items or delete existing items. This is the most common scenario, and when in doubt, use the following terminology for button labels:
    
    *   **New**: For buttons that open a modal to create something that didn't exist before, use **New**. For example, **New contact**.
    *   **Delete**: For buttons that remove something that existed previously, use **Delete**. For example, **Delete contact**.
2.  Actions create or sever connections between items that already exist. This scenario is less common and uses the following terminology for button labels:
    
    *   **Add**: For buttons that associate an existing item with another item, use **Add**. For example, **Add student to class**.
    *   **Remove**: For buttons that remove the association between items, use **Remove**. For example, **Remove student from class**.

Don't use **Create** as an alternative to **New** or **Add** in button labels.

This guidance applies to button labels and also to the headings on the pages or modals that appear when users create and remove items. In other UI text, use the most appropriate terminology for the particular scenario. For example, the label for the primary button in a modal that appears after users select **New** or **Add** buttons should generally be **Save** and doesn't need to use the **New** or **Add** terminology.

For additional guidance on button labels, see the [button classes](/skyux/components/button.md).

[

Page titles
-----------

](/skyux/design/guidelines/content#page-titles.md)

Page titles uniquely identify the contents of pages. They are concise and direct, and they indicate the purpose of the pages to get users up to speed quickly. The data in page titles depends on the users and the context in which they visit the pages. You can combine multiple pieces of data in page titles and pull data from multiple sources.

Follow these general guidelines for page titles:

*   Be concise.
*   Make titles unique.
*   Describe the page's content or purpose. Titles must stand on their own and make sense out of context.
*   Use meaningful, differentiating terms to facilitate scanning in browser tabs, window lists, and browser bookmarks.

Use the following format to display page titles in browser tabs: <Page title> — <Company, product, or site identifier>. If pages include tabbed subnavigation, adjust the format to include tab titles: <Tab title> — <Page title> — <Company, product, or site identifier>. For example, Blackbaud solutions use the company name after tab titles and page titles: Portfolio — Work center — Blackbaud.

[

Dates and times
---------------

](/skyux/design/guidelines/content#dates-and-times.md)

For guidance on how to display dates and times in the UI for a consistent user experience, see [Dates and times](/skyux/design/guidelines/content/dates-times.md).

[

Related information
-------------------

](/skyux/design/guidelines/content#related-information.md)

### Guidelines

*   [Form design error messages](/skyux/design/guidelines/form-design#validation-and-error-handling.md)
*   [User assistance](/skyux/design/guidelines/user-assistance.md)
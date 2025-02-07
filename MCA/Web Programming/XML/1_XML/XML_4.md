
### Structuring Data

Useful techniques that you can apply to all kinds of data-heavy documents.

Once the data is in XML, it’s very easy to repurpose for a thousand different uses.

#### XMLizing the Data

XML is based on a containment model. Each XML element can contain text or other XML elements, both of which are called the element’s children. Some XML elements may contain both text and child elements. However, there’s often more than one way to organize the data, depending on your needs. One advantage of XML is that it makes it fairly straightforward to write a program that reorganizes the data in a different form.

To get started, the first question you have to address is: what contains what? Or, another way of putting it, which information is a part of which other information?

XML is very flexible. It’s easy to vary the exact information provided with any particular element. If you don’t know something, it’s easy to leave it out. If you have extra information that wasn’t planned for, you can easily add an extra element covering that content.

Every good XML document (where "good" has a very specific meaning to be discussed in Chapter 6) must have a **root element**. This is an element that completely contains all other elements of the document. The root element’s start-tag comes before all other elements’ start-tags, and the root element’s end-tag comes after all other element’s end-tags. For the root element:

The XML declaration is not an element or a tag. Therefore, it does not need to be contained inside the root element.

The next question to ask is whether there’s any information that applies to the entire table, rather than individual rows or columns. I think there’s one key piece: e.g., the date the table describes.

XML makes it very easy to include the information that applies and leave out the information that doesn’t. There aren’t any special null values or elements used just to fill an expected slot.

---

```xml
<?xml version="1.0"?>
<SCHEDULE>
  <DATE>July 3, 2003</DATE>
  <STATION>
    <NETWORK>CBS</NETWORK>
    <CALL_LETTERS>WCBS</CALL_LETTERS>
    <CHANNEL>2</CHANNEL>
  </STATION>
  <STATION>
    <CALL_LETTERS>WLNY</CALL_LETTERS>
    <CHANNEL>55</CHANNEL>
  </STATION>
  <STATION>
    <NETWORK>HBO</NETWORK>
    <CHANNEL>501</CHANNEL>
  </STATION>
</SCHEDULE>
```

---

XML is the Extensible Markup Language. When you encounter new information, you can always invent an element to fit it.

### Advantages of XML Format

There are several benefits, including the following:

- The data is self-describing.
- The data can be manipulated with standard tools.
- The data can be viewed with standard tools.
- Different views of the same data are easy to create with style sheets.

The first major benefit of the XML format is that the data is **self-describing**. The meaning of each item of information is clearly and unambiguously indicated by the markup.

The second benefit of the XML format is that data can be manipulated in a wide range of XML-enabled tools, from expensive payware such as Adobe FrameMaker to free open-source software such as Cocoon and eXist. The data may be bigger, but the extra redundancy allows more tools to process it.

---

#### Styling the Root Element

You do not have to assign a style rule to each element in the list. Many elements can rely on the styles of their parents cascading down. The most important style, therefore, is the one for the root element:

```css
SCHEDULE { font-size: 14pt; background-color: white; color: black; display: block; }
```

CSS lets you add extra content from the style sheet either before or after particular elements using the `:before` and `:after` pseudoselectors. The text that you want to add is given as a string value of the `content` property. For example, to add the phrase “TV Listings: “ to the beginning of the `DATE` element, add this rule to the style sheet:

```css
DATE:before { content: "TV Schedule: "; }
LENGTH:before { content: "Length: "; }
START_TIME:before { content: "Starts at "; }
ORIGINAL_AIR_DATE:before { content: "First aired on "; }
REPEAT:before { content: "Repeat: "; }
CLOSED_CAPTIONED:before { content: "Closed captioned: "; }
RATING:before { content: "Rating: "; }
STARS:before { content: "Stars: "; }
YEAR_MADE:before { content: "Made in "; }
```

“July 3, 2003” isn’t the ideal title for this document. “TV Schedule: July 23, 2003” would be better.

```css
STATION { display: block; }
SHOW { display: block; }
NETWORK, CHANNEL, CALL_LETTERS { font-size: 28pt; font-weight: bold; }
NAME { font-weight: bold; }
```

---

In CSS, you can set an element’s `display` property to `none` to hide it from view:

```css
CAST { display: none; }
AIR_DATE { display: none; }
DIRECTOR { display: none; }
EPISODE_NUMBER { display: none; }
PRODUCER { display: none; }
WRITER { display: none; }
```

---

If you organize the document so it’s absolutely perfect for this one use (a printed table in a newspaper or a magazine), you may have eliminated information that’s critical for other uses. What’s flawed here is not XML. XML is robust enough to handle all these needs. However, **CSS** is a limited style language. It’s intended for words in a row that already contain all the document content in the right order and nothing else. A few elements can be hidden by setting `display` to `none`, and a little text can be added using `:before`, `:after`, and the `content` property. However, at its core, CSS just isn’t designed to handle complicated document manipulations before displaying the result to the end user.

What’s really needed is a different style language that enables you to add certain boilerplate content to elements and to perform transformations on the element content that is present. Such a language exists — the **Extensible Stylesheet Language (XSL)**. CSS is simpler than XSL. CSS works well for basic web pages and reasonably straightforward documents. XSL is considerably more complex, but it is also more powerful. XSL builds on the simple CSS formatting that you learned in this chapter, but it also transforms the source document into various forms that the reader can view.

---

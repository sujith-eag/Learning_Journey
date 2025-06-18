
### Well-formedness

Well-formedness is the minimum criterion necessary for XML processors and browsers to read files. This chapter examines the rules for well-formed documents. It explores the different parts of an XML document — tags, text, attributes, elements, and so on — and discusses the primary rules each part must follow.

---

### Well-Formedness Rules

The XML specification strictly prohibits XML parsers from trying to fix and understand malformed documents. All a parser can do is signal the error. It is not allowed to fix the error.

To be well-formed, an XML document must follow more than 100 different rules. However, most of these rules simply forbid things that you’re not very likely to do anyway if you follow the examples given in this book. For example, one rule is that the name of the element must immediately follow the `<` of the element’s start-tag. For example, `<TRIANGLE>` is a legal start-tag but `< TRIANGLE>` isn’t. On the other hand, the same rule says that it is OK to have extra space before the tag’s closing angle bracket. That is, both `<TRIANGLE>` and `<TRIANGLE >` are well-formed start-tags. Another rule says that element names must have at least one character; that is, `<>` is not a legal start-tag and `</>` is not a legal end-tag. Chances are it never would have occurred to you to create an element with a zero-length name, but computers are dumber than human beings and need to have constraints like this spelled out for them. XML’s well-formedness rules are designed to be understood by software rather than human beings, so quite a few of them are a little technical and won’t present much of a problem in practice. The only source for the complete list of rules is the XML specification itself. However, if you follow the rules given here, and check your work with an XML parser before distributing them, your documents should be fine.

---

### XML Documents

An XML document is made up of text. It is a sequence of characters with a fixed length that adheres to certain constraints. XML documents are made up of storage units called entities. Each entity contains a well-formed document fragment. This is a piece of text that meets all of XML’s well-formedness rules except for the one about there being a single root element. The various entities that make up a document will be stored in different files, databases, and other locations. The parser combines them all to form the complete document.

---

### XML Declaration

Simple XML documents are made up of a single entity, the document itself. Such documents can be understood completely on their own without reading any other files. In other words, they stand alone. Such a document normally contains a standalone pseudo-attribute in its XML declaration with the value `yes`, similar to this one:

```xml
<?xml version="1.0" standalone="yes"?>
```

I call this a pseudo-attribute because technically only elements can have attributes. The XML declaration is not an element. Therefore, `standalone` is not an attribute even if it looks like one.

External entities and entity references can be used to combine multiple files and other data sources to create a single XML document. These documents cannot be parsed without reference to other files. Therefore, they normally have a standalone pseudo-attribute with the value `no`:

```xml
<?xml version="1.0" standalone="no"?>
```

If a document does not have an XML declaration, or if a document has an XML declaration but that XML declaration does not have a standalone pseudo-attribute, the value `no` is assumed. That is, the document is assumed incapable of standing on its own, and the parser will prepare itself to read external pieces as necessary. If the document can, in fact, stand on its own, nothing is lost by the parser being ready to read an extra piece.

---

### Single Root Element

An XML document has a root element that completely contains all other elements of the document. This is also sometimes called the document element, although this element does not have to have the name `document` or `root`. Just like any other element, root elements are delimited by a start-tag and an end-tag.

```xml
<?xml version="1.0"?>
<GREETING>
  Hello XML!
</GREETING>
```

In this example, the root element is `GREETING`. The XML declaration is not an element. Therefore, it does not have to be included inside the root element. Similarly, other non-element data in an XML document, such as an `xml-stylesheet` processing instruction, a DOCTYPE declaration, or comments, do not have to be inside the root element. But all other elements (other than the root itself) and all raw character data must be contained in the root element.

---

### Text in XML

A document’s text is divided into character data and markup. To a first approximation, markup describes a document’s logical structure, while character data is the basic information of the document.

Markup includes all tags, processing instructions, DTDs, entity references, character references, comments, CDATA section delimiters, and the XML declaration. Everything else is character data. However, this is tricky because when a document is processed, some of the markup turns into character data. For example, the markup `&gt;` is turned into the greater-than sign character (`>`). The character data that’s left after the document is processed, and after all markup that refers to character data has been replaced by the actual character data, is called parsed character data, or PCDATA for short.

---

## Elements and Tags

An XML document is a singly rooted hierarchical structure of elements. Each element is delimited by a start-tag and an end-tag or is represented by a single empty-element tag.

---

### Element Names

Every element has a name made up of one or more characters. This is the name included in the element’s start- and end-tags. Element names begin with a letter, such as `y` or `A`, or an underscore `_`. Subsequent characters in the name may include letters, digits, underscores, hyphens, and periods. They cannot include whitespace.

XML names are case-sensitive. This is different from HTML in which `<P>` and `<p>` are the same tag, and a `</p>` can close a `<P>` tag.

Elements may contain (and indeed often do contain) other elements. However, elements may not overlap. Practically, this means that if an element contains a start-tag for an element, it must also contain the corresponding end-tag. Empty tags may appear anywhere.

---


### Attributes, Empty Element Tags

All information was provided either by a tag name or as the text content of an element. This is a straightforward and easy-to-understand approach, but it’s not the only one. As in HTML, XML elements may have attributes. An attribute is a name-value pair associated with an element. The name and the value are each strings, and no element can contain two attributes with the same name.  
You’re already familiar with attribute syntax from HTML. For example, consider this `<IMG>` tag:

```xml
<IMG SRC=cup.gif WIDTH=89 HEIGHT=67 ALT=”Cup of coffee”>
```

It has four attributes: the `SRC` attribute whose value is `cup.gif`, the `WIDTH` attribute whose value is 89, the `HEIGHT` attribute whose value is 67, and the `ALT` attribute whose value is "Cup of coffee." However, in XML — unlike HTML — attribute values must always be quoted, and start-tags must have matching end-tags. Thus, the XML equivalent of this tag is as follows:

```xml
<IMG SRC=”cup.gif” WIDTH=”89” HEIGHT=”67” ALT=”Cup of coffee”></IMG>
```

Another difference between HTML and XML is that XML assigns no specific meaning to the `IMG` element and its attributes. In particular, there’s no guarantee that an XML browser will interpret this element as an instruction to load and display the image in the file `cup.gif`.

Attribute syntax fits the television listings example quite nicely. One advantage is that it makes the markup somewhat more concise. For example, instead of containing a `DATE` child element, the `SCHEDULE` element only needs a `DATE` attribute:

```xml
<SCHEDULE DATE=”July 3, 2003”></SCHEDULE>
```

`STATION` should be a child of the `SCHEDULE` element rather than an attribute. For one thing, there are many stations in a schedule. Anytime there’s likely to be more than one of something, child elements are called for. Attribute names must be unique within an element. You cannot, for example, write a `SCHEDULE` element like this:

```xml
<SCHEDULE DATE=”July 3, 2003” STATION=”WPIX” STATION=”WCBS”></SCHEDULE>
```

The second reason `STATION` is naturally a child element rather than an attribute is that it has substructure; that is, it is divided into `NETWORK`, `CALL_LETTERS`, `SHOW`, and `CHANNEL` elements. Attribute values are unstructured, flat text. XML elements can conveniently encode structure.

It matters which one comes first. XML parsers preserve element order. However, they do not preserve attribute order. Whenever order matters, you need elements rather than attributes.

However, the network, call letters, and channel of a station are all unstructured, flat text; there’s only one of each per station, and their order doesn’t matter. Therefore, `STATION` elements can easily have `CALL_LETTERS`, `SHOW`, and `CHANNEL` attributes instead of `CALL_LETTERS`, `SHOW`, and `CHANNEL` child elements:

```xml
<STATION NETWORK=”CBS” CALL_LETTERS=”WCBS” CHANNEL=”2”></STATION>
```

You don’t have to store this information in attributes. Child elements still work, but you can use attributes here if you want to.

### Attribute vs. Elements

The no-attribute approach was an extreme position. It’s also possible to swing to the other extreme — storing all the information in the attributes and none in the content.

One good rule of thumb is that the data itself should be stored in elements. Information about the data (metadata) should be stored in attributes. When in doubt, put the information in the elements.

To differentiate between data and metadata, ask yourself whether someone reading the document would want to see a particular piece of information. If the answer is yes, the information probably belongs in a child element. If the answer is no, the information probably belongs in an attribute. If all tags were stripped from the document along with all the attributes, the basic information should still be present. Attributes are good places to put ID numbers, URLs, references, and other information not directly or immediately relevant to the reader. However, there are many exceptions to the basic principle of storing metadata as attributes. Reasons for making an exception include the following:

- Attributes can’t hold structure well.
- Attributes are unordered. Elements are ordered.
- Elements allow you to include meta-metadata (information about the information about the information).
- Not everyone always agrees on what is and isn’t metadata.
- Elements are more extensible in the face of future changes.

Elements can have substructure; attributes can’t. This makes elements far more flexible and may convince you to encode metadata as child elements.

Using elements instead of attributes makes it straightforward to include additional information such as the authors’ e-mail addresses, a URL where an electronic copy of the document can be found, the chapter title, and anything else that seems important.

```xml
<ARTICLE DATE=”06/28/1969”>
Polymerase Reactions in Organic Compounds
</ARTICLE>
```

However, the `DATE` attribute has substructure signified by the `/`. Getting that structure out of the attribute value is much more difficult than reading child elements of a `DATE` element like this one:

```xml
<DATE>
<YEAR>1969</YEAR>
<MONTH>06</MONTH>
<DAY>28</DAY>
</DATE>
```

If the `DATE` is stored as an attribute, however, there’s no easy way to access only part of it. You must write a separate program in a programming language such as ECMAScript or Java that can parse your date format. It’s easier to use the standard XML tools and child elements.

Furthermore, the attribute syntax is ambiguous. What does the date “10/07/2004” signify? Is it October 7th or July 10th?

### Meta-metadata

Using elements for metadata also easily allows for meta-metadata, or information about the information about the information.

“Meta-ness” is in the mind of the beholder. Who’s reading your document and why they’re reading it determines what they consider to be data and what they consider to be metadata.

### Good Time to Use Attributes

Attributes are fully appropriate for very simple data without substructure that the reader is unlikely to want to see. One example is the `HEIGHT` and `WIDTH` attributes of an `IMG` element. Although the values of these attributes may change if the image changes, it’s hard to imagine how the data in the attribute could be anything more than a very short string of text. `HEIGHT` and `WIDTH` are one-dimensional quantities (in many ways), so they work well as attributes.

Attributes are appropriate for simple information about the document that has nothing to do with the content of the document.

It’s useful to assign an `ID` attribute to each element. The value of an `ID` attribute is a unique string possessed only by one element in the document.

Attributes are also useful containers for document-specific style information. For example, if `TITLE` elements are normally rendered as bold text, but you want to make just one `TITLE` element both bold and italic, you might write something similar to this:

```xml
<TITLE STYLE=”font-style: italic”>Significant Others</TITLE>
```

### Empty Element and Empty-Element Tags

An element that contains no content, not even white space, is called an empty element. For example, this is an empty `STATION` element:

```xml
<STATION NETWORK=”CBS” CALL_LETTERS=”WCBS” CHANNEL=”2”></STATION>
```

The end-tag immediately follows the start-tag. Rather than including both a start-tag and an end-tag, you can include one empty-element tag. Empty-element tags are distinguished from start-tags by a closing `/` instead of a closing `>`. For example, instead of `<STATION></STATION>`, you would write:

```xml
<STATION/>
```

Using empty-element tags where possible is a little shorter and perhaps a little clearer than the two-tag version. However, it is exactly the same document.

____


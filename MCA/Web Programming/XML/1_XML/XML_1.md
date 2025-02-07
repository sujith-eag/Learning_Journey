
### XML is a Meta-Markup Language

XML stands for Extensible Markup Language (often misspelled as eXtensible Markup Language to justify the acronym). XML is a set of rules for defining semantic tags that break a document into parts and identify the different parts of the document. It is a meta-markup language that defines a syntax in which other domain-specific markup languages can be written.

XML, however, is a meta-markup language. It’s a language that lets you make up the tags you need as you go along. These tags must be organized according to certain general principles, but they’re quite flexible in their meaning.

You can document the tags you create in a schema written in any of several languages, including document type definitions (DTDs) and the W3C XML Schema Language.

XML says that tags begin with a `<` and end with a `>`. However, XML does not tell you what names must go between the `<` and the `>`.

---

### XML Describes Structure and Semantics, Not Formatting

XML markup describes a document’s structure and meaning. It does not describe the formatting of the elements on the page. You can add formatting to a document with a style sheet. The document itself only contains tags that say what is in the document, not what the document looks like.

By contrast, HTML encompasses formatting, structural, and semantic markup. `<B>` is a formatting tag that makes its content bold. `<STRONG>` is a semantic tag that means its contents are especially important. `<TD>` is a structural tag that indicates that the contents are a cell in a table. In fact, some tags can have all three kinds of meaning. An `<H1>` tag can simultaneously mean 20-point Helvetica bold, a level 1 heading, and the title of the page.

XML offers an infinite number of tags to fill an infinite number of needs.

---

### Self-Describing Data

XML is, at a low level, an incredibly simple data format. It can be written in 100 percent pure ASCII or Unicode text, as well as in a few other well-defined formats. Text is reasonably resistant to corruption. The removal of bytes or even large sequences of bytes does not noticeably corrupt the remaining text. This starkly contrasts with many other formats, such as compressed data or serialized Java objects, in which the corruption or loss of even a single byte can render the rest of the file unreadable.

---

### Interchange of Data Among Applications

Because XML is nonproprietary and easy to read and write, it’s an excellent format for the interchange of data among different applications. XML is not encumbered by copyright, patent, trade secret, or any other sort of intellectual property restrictions. It has been designed to be extremely expressive and very well structured while at the same time being easy for both human beings and computer programs to read and write. Thus, it’s an obvious choice for exchange languages.

---

### Structured Data

XML is ideal for large and complex documents because the data is structured. You specify a vocabulary that defines the elements in the document, and you can specify the relations between elements.

XML also provides a client-side include mechanism that integrates data from multiple sources and displays it as a single document. (In fact, it provides at least three different ways of doing this, a source of some confusion.) The data can even be rearranged on the fly. Parts of it can be shown or hidden depending on user actions. You’ll find this extremely useful when you’re working with large information repositories like relational databases.

---

### Related Technologies

XML doesn’t operate in a vacuum. Using XML as more than a data format involves several related technologies and standards, including the following:

- HTML for backward compatibility with legacy browsers
- The CSS and XSL style sheet languages to define the appearance of XML documents
- URLs and URIs to specify the locations of XML documents
- XLinks to connect XML documents to each other
- The Unicode character set to encode the text of an XML document

---


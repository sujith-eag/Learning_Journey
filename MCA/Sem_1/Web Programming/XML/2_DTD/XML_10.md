

The items where the pieces of an XML document are stored, in whatever form they take, are called **entities**. Entity references load these entities into the main XML document. General entity references load data into the root element of an XML document. `&lt;`, `&gt;`, `&apos;`, `&quote;`, and `&amp;` are predefined general entity references that refer to the text entities `<`, `>`, `‘`, `“`, and `&`, respectively. Parameter entity references load data into the document’s document type definition (DTD). They begin with a `%` instead of an `&`.  
Unparsed entities point to non-XML, binary data whose type is identified with a notation and are referenced by an ENTITY type attribute. All three kinds of entities are declared in the DTD.

Logically speaking, an XML document is composed of a prolog followed by a root element that strictly contains all other elements; but physically the content of an XML document can be spread across multiple files. For example, each SHOW element might appear in a separate file even though the root element contains several thousand shows broadcast on one day. The storage units that contain particular parts of an XML document are entities. An entity can be a file, a database record, or any other item that contains data.

The storage unit that contains the XML declaration, the document type declaration, and the root element is called the **document entity**. Thus, every XML document has at least one entity. However, the root element and its descendants may also contain entity references pointing to additional data that should be inserted into the document. A validating XML processor combines all the referenced entities into a single logical document before it passes the document on to the end application or displays the file.

Entities hold content: well-formed XML, other forms of text, or binary data. The prolog and the document type declaration are part of the root entity of the document. An XSL style sheet qualifies as an entity, but only because it itself is a well-formed XML document. The entity that makes up the style sheet is not one of the entities that compose the XML document to which the style sheet applies. A CSS style sheet is not an entity at all.

Most entities have names by which you can refer to them. The only exception is the document entity — the main file containing the XML document.

Entities can be either internal or external. Internal entities are defined completely within the DTD. External entities, by contrast, draw their content from another source located via a URL. The main document only includes a reference to the URL where the actual content resides.  
Entities fall into two categories: **parsed** and **unparsed**. Parsed entities contain well-formed XML text. Unparsed entities contain either binary data or non-XML text (such as an e-mail message). Currently, unparsed entities aren’t well supported (if at all) by most browsers, editors, and other tools.

### Internal General Entities

You can think of an internal general entity reference as an abbreviation for commonly used text or text that’s hard to type. An `<!ENTITY>` declaration in the DTD defines an abbreviation and the text that the abbreviation stands for. For example, instead of typing the same footer at the bottom of every page, you can simply define that text as the `FOOTER` entity in the DTD and then type `&FOOTER;` at the bottom of each page. Furthermore, if you decide to change the footer block (perhaps because your e-mail address changes), you only need to make the change once in the DTD instead of on every page that shares the footer.

General entity references begin with an ampersand (`&`) and end with a semicolon (`;`), with the entity’s name between these two characters. For example, `&lt;` is a general entity reference for the less-than sign (`<`). The name of this entity is `lt`. The replacement text of this entity is the one-character string `<`. Entity names consist of any set of alphanumeric characters and the underscore. White space and other punctuation characters are prohibited. Like most everything else in XML, entity references are case-sensitive.

### Defining an internal general entity reference

`<!ENTITY name "replacement text">`

The name is the abbreviation for the replacement text. The replacement text must be enclosed in quotation marks because it can contain white space and XML markup. You type the name of the entity in the document, but the reader sees the replacement text.

```xml
<?xml version="1.0"?>
<!DOCTYPE DOCUMENT [
	<!ENTITY ERH "Elliotte Rusty Harold">
	<!ELEMENT DOCUMENT (TITLE, SIGNATURE)>
	<!ELEMENT TITLE (#PCDATA)>
	<!ELEMENT COPYRIGHT (#PCDATA)>
	<!ELEMENT EMAIL (#PCDATA)>
	<!ELEMENT LAST_MODIFIED (#PCDATA)>
	<!ELEMENT SIGNATURE (COPYRIGHT, EMAIL, LAST_MODIFIED)>
]>
<DOCUMENT>
	<TITLE>&ERH;</TITLE>
	<SIGNATURE>
		<COPYRIGHT>2004 &ERH;</COPYRIGHT>
		<EMAIL>elharo@metalab.unc.edu</EMAIL>
		<LAST_MODIFIED>July 30, 2004</LAST_MODIFIED>
	</SIGNATURE>
</DOCUMENT>
```

The `ERH` in title and copyright will be replaced by the name.

General entity definitions cannot contain the three characters `%`, `&`, and `"` directly, although you can include them via character references.

An entity value can contain tags and span multiple lines. For example, the following `SIGNATURE` entity is valid:

```xml
<!ENTITY SIGNATURE
"<SIGNATURE>
<COPYRIGHT>2004 Elliotte Rusty Harold</COPYRIGHT>
<EMAIL>elharo@metalab.unc.edu</EMAIL>
<LAST_MODIFIED>July 30, 2004</LAST_MODIFIED>
</SIGNATURE>"
>
```

An entity value can also contain multiple elements, as in the following example:

```xml
<!ENTITY SIGNATURE
"<HR/>
<COPYRIGHT>2004 Elliotte Rusty Harold</COPYRIGHT>
<EMAIL>elharo@metalab.unc.edu</EMAIL>
<LAST_MODIFIED>July 30, 2004</LAST_MODIFIED>"
>
```

One advantage of using entity references instead of the full text is that it’s easier to change the text. This is especially useful when a single DTD is shared between multiple documents. For example, to change the email address, rather than searching and replacing through multiple files, it can simply be changed in one line of the DTD.

### Using general entity references in the DTD

The next obvious question is whether it’s possible to parameterize entities. For example, could you use the preceding `SIGNATURE` entity but change the date in each separate `LAST_MODIFIED` element on each page? The answer is yes. Entities can contain other entities, and all of these entities can be redefined in a document’s internal DTD subset. This enables both modularization and parameterization of DTDs. You can include one general entity reference inside the definition of another, like this:

`<!ENTITY COPY2004 "Copyright 2004 &ERH;">`

There are restrictions. The first restriction is that the declaration cannot contain a circular reference. The second restriction: General entity references cannot insert text that is only part of the DTD and that will not be used as part of the document content.

### Predefined general entity references

|Entity Reference|Character|
|---|---|
|`&amp;`|`&`|
|`&lt;`|`<`|
|`&gt;`|`>`|
|`&quot;`|`“`|
|`&apos;`|`‘`|

---

### External General Entities

Documents using only internal entities closely resemble the HTML model. The complete text of the document is available in a single file. Images, applets, sounds, and other non-HTML data may be linked to the file, but at least all the text is present. Of course, the HTML model has some problems. In particular, it’s quite difficult to embed dynamic information in the file. CGI scripts, Java applets, fancy database software, server-side includes, ASP, JSP, PHP, and various other technologies can all add this capability to HTML; but HTML alone only provides a static document. You have to go outside HTML to build a document from multiple pieces.

XML allows you to embed both well-formed XML documents and document fragments inside other XML documents. Furthermore, XML defines the syntax whereby an XML parser can build a document out of multiple smaller XML documents and pieces thereof found either on local or remote systems. Documents may contain other documents, which may contain other documents. As long as there’s no recursion (an error reported by the processor), the application only sees a single, complete document. In essence, this provides client-side includes.

External entities are data outside the main file containing the root element/document entity. External entity references let you embed these external entities in the parsed character data content of your document (though not in the attribute values) and thus build a single XML document from multiple independent files.

The text of the entity comes from a document at a given Uniform Resource Identifier (URI). This URI is specified in the entity’s declaration in the DTD using this syntax:

`<!ENTITY name SYSTEM "URI">`

An XML External parsed entity, suppose this can be retrieved by a URL:

```xml
<COPYRIGHT>2004 Elliotte Rusty Harold</COPYRIGHT>
<EMAIL>elharo@metalab.unc.edu</EMAIL>
<LAST_MODIFIED>July 30, 2004</LAST_MODIFIED>
<HR/>
```

Associating this with an entity reference `&SIG;` by adding the following declaration:

```xml
<!ENTITY SIG SYSTEM "http://cafeconleche.org/boilerplate/signature.xml">
```

If the file to be included is in the same directory as the file doing the including, you only need to use the filename.

`<!ENTITY SIG SYSTEM "signature.xml">`

Contents of the signature file can be included in a document at any point merely by using `&SIG;`:

```xml
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DOCUMENT [
	<!ELEMENT DOCUMENT (TITLE, COPYRIGHT, EMAIL, LAST_MODIFIED, HR?)>
	<!ELEMENT TITLE (#PCDATA)>
	<!ELEMENT COPYRIGHT (#PCDATA)>
	<!ELEMENT EMAIL (#PCDATA)>
	<!ELEMENT HR EMPTY>
	<!ELEMENT LAST_MODIFIED (#PCDATA)>
	<!ENTITY SIG SYSTEM "signature.xml">
]>
<DOCUMENT>
	<TITLE>Entity references</TITLE>
	&SIG;
</DOCUMENT>
```

The DTD declares both the internal elements, such as TITLE, and the external elements, such as COPYRIGHT. Validating parsers are required to resolve all entity references and replace them with their values before checking the document against its DTD.  
The `standalone` attribute of the XML declaration now has the value `no` because this file is no longer complete. Parsing the file requires additional data from the external file `signature.xml`. Technically, though, the standalone declaration isn’t required because its default value is `no`.

### Text Declarations

There’s no guarantee or requirement that all the external parsed entities a document includes will use the same encoding. Each external parsed entity can have a different encoding. To account for this, each external parsed entity can have its own text declaration. Text declarations look like XML declarations except that the version pseudo-attribute is optional, the encoding pseudo-attribute is required, and there’s no standalone pseudo-attribute. These are legal text declarations:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml encoding="UTF-8"?>
```

However, this is not a legal text declaration because the encoding is omitted:

```xml
<?xml version="1.0"?>
```

This is not a legal text declaration because it includes a standalone declaration:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
```

If the external parsed entity has a root element, and if it either has a version pseudo-attribute in the text declaration or does not have a text declaration at all, then the external parsed entity may itself be a well-formed XML document.

Whether a well-formed XML document or not, an external parsed entity cannot contain a document type declaration. This means an external parsed entity cannot be valid on its own. It can only be validated when it’s inserted into a full XML document that does have a document type declaration.

A document that uses external parsed entities can be valid as long as it properly declares all the elements and attributes used in both the document entity and all the other entities.

---

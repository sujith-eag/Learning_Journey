
### Document Type Definition

A document type definition lists the elements, attributes, entities, and notations that can be used in a document, as well as their possible relationships to one another. A DTD specifies a set of rules for the structure of a document. A DTD defines exactly what is and what is not allowed to appear inside a document.

For example, a DTD may dictate that each BOOK element has exactly one ISBN child element, exactly one TITLE child element, and one or more AUTHOR children, and it may or may not contain a single SUBTITLE. Each such rule is given in a declaration.

Every valid XML document must specify the DTD it’s valid with respect to. This DTD can be included in the XML document it describes, or that document can link to it at an external URL. Such external DTDs can be shared by different documents and web sites. If the DTD is not directly included in the document but is linked in from an external source, changes made to the DTD automatically propagate to all documents using that DTD. On the other hand, backward compatibility is not guaranteed when a DTD is modified. Incompatible changes can invalidate documents.

Furthermore, a DTD shows how the different elements of a document are arranged. A DTD shows the generic structure of a document separate from the actual data in the individual document instances. This means that you can slap a lot of fancy styles and formatting onto the underlying structure without destroying it.

---

### Element Declaration

Elements are declared using element declarations. Each element declaration gives the name of the element and lists the elements and text that it can contain.

This list is called the content specification. For example, this element declaration for the GREETING element says that elements with the name GREETING must contain only parsed character data:

```xml
<!ELEMENT GREETING (#PCDATA)>
```

Every declaration begins with `<!`. Element declarations begin with `<!ELEMENT` (case-sensitive, as most things are in XML). This is followed by some white space and the name of the element being declared, GREETING in this example. Then there’s some more white space and the content specification for this element. This content spec (#PCDATA) says that the element must contain parsed character data. Parsed character data is essentially any text that’s not markup.

---

#### DTD Files

Declarations are placed in DTDs. Often a DTD is a single file, separate from the document itself (although as you’ll soon see, other storage schemes are possible). Extension `.dtd`.

---

### Document Type Declarations

A document type declaration is not the same thing as a document type definition. Only the document type definition is abbreviated DTD. A document type declaration must contain or refer to a document type definition, but a document type definition never contains a document type declaration.

A document type declaration is placed in an XML document’s prolog to say what DTD that document adheres to. It also specifies which element is the root element of the document. The document type declaration can either specify the DTD directly, by including it inside the document type declaration, or indirectly, by giving the URL where the DTD is found.

A document type declaration begins with `<!DOCTYPE` and ends with a `>`. In between is the name of the root element, followed either by a pair of square brackets containing the DTD itself or by the `SYSTEM` keyword and a URL where the DTD can be found (or, occasionally, both). A document type declaration has this basic form:

```dtd
<!DOCTYPE name_of_root_element
SYSTEM “URL of the external DTD subset” [
internal DTD subset
]>
```

Examples:

```dtd
<!DOCTYPE GREETING SYSTEM “http://example.org/greeting.dtd”>

<!DOCTYPE GREETING [
<!ELEMENT GREETING (#PCDATA)>
]>
```

```dtd
<?xml version=”1.0”?>
<!DOCTYPE GREETING SYSTEM “greeting.dtd”>
<GREETING>
Hello XML!
</GREETING>
```

A document can’t have more than one document type declaration, that is, more than one `<!DOCTYPE>`. To use elements declared in more than one external DTD, you need external parameter entity references.

---

### Internal DTDs

Putting the entire DTD inside the document type declaration isn’t as reusable or modular as locating it with a URL:

```dtd
<?xml version=”1.0”?>
<!DOCTYPE GREETING [
	<!ELEMENT GREETING (#PCDATA)>
]>
<GREETING>
Hello XML!
</GREETING>
```

---

### With Style Sheet

```dtd
<?xml version=”1.0”?>
<?xml-stylesheet type=”text/css” href=”greeting.css”?>
<!DOCTYPE GREETING [
	<!ELEMENT GREETING (#PCDATA)>
]>
<GREETING>
Hello XML!
</GREETING>
```

Notice how the three essential parts of the document can be stored in three different files. The data is in the document file, the structure applied to the data is in the DTD file, and the formatting is in the style sheet. This tripartition enables you to inspect or change any or all of these relatively independently.

---

### Validating against a DTD

To be considered valid, an XML document must satisfy four criteria:

1. It must be well-formed.
2. It must have a document type declaration.
3. Its root element must be the one specified by the document type declaration.
4. It must satisfy all the constraints of the DTD specified by the document type declaration.

**Invalid Example:**

```xml
<?xml version=”1.0”?>
<!DOCTYPE GREETING SYSTEM “greeting.dtd”>
<FOO>
Hello XML!
</FOO>
```

---
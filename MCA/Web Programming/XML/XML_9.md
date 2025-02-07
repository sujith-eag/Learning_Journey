

The Attribute Contains Information About the Content Rather Than the Content Itself

---

### Declaring Attributes

Like elements, the attributes used in a document must be declared in the DTD for the document to be valid. Attributes are declared by an attribute list in the following form:

```xml
<!ATTLIST Element_name Attribute_name Type Default_value>
```

- `<!` starts all declarations.
- `ATTLIST` is the keyword that indicates this is an attribute list.
- `Element_name` is the name of the element possessing this attribute.
- `Attribute_name` is the name of the attribute.
- `Type` is the kind of attribute — one of the 10 types.
- `Default_value` is the value the attribute takes on if no value is specified for the attribute.

---

### Example of Declaring Attributes

```xml
<GREETING LANGUAGE="French">
   Salut!
</GREETING>
```

This element might be declared as follows in the DTD:

```xml
<!ELEMENT GREETING (#PCDATA)>
<!ATTLIST GREETING LANGUAGE CDATA "English">
```

The `<!ELEMENT>` declaration simply says that a `GREETING` element contains parsed character data. The `<!ATTLIST>` declaration says that `GREETING` elements have an attribute with the name `LANGUAGE` and the type `CDATA`, essentially the same as `#PCDATA` for element content. The word "English" in quotation marks is the default value. If you encounter a `GREETING` element without a `LANGUAGE` attribute, the value "English" is used by default.

The attribute is declared separately from the element itself. The name of the element to which the attribute belongs is included in the `<!ATTLIST>` declaration. This attribute declaration applies only to that element, `GREETING` in the preceding example. If other elements also have `LANGUAGE` attributes, they require separate `<!ATTLIST>` declarations.

As with most declarations, the exact order in which attribute declarations appear is not important. They can come before or after the element declaration they’re associated with.

---

### Declaring Multiple Attributes

```xml
<RECTANGLE LENGTH="70px" WIDTH="85px"/>
```

You can declare these attributes in several attribute declarations, with one declaration for each attribute, as in the following example:

```xml
<!ELEMENT RECTANGLE EMPTY>
<!ATTLIST RECTANGLE LENGTH CDATA "0px">
<!ATTLIST RECTANGLE WIDTH CDATA "0px">
```

The preceding example says that `RECTANGLE` elements possess `LENGTH` and `WIDTH` attributes, each of which has the default value `0px`. You can combine the two `<!ATTLIST>` declarations into a single declaration like this:

```xml
<!ATTLIST RECTANGLE LENGTH CDATA "0px"
                WIDTH CDATA "0px">
```

---

### Alternatives to Default Attribute Values

Instead of specifying an explicit default attribute value such as `0px`, an attribute declaration can require the author to provide a value, allow the value to be omitted completely, or even always use the default value. These requirements are specified with the three keywords `#REQUIRED`, `#IMPLIED`, and `#FIXED`, respectively.

---

### `#REQUIRED`

You might not always have a good option for a default value. `#REQUIRED` helps you guarantee that the minimum information necessary for processing a document is present. Any attribute that must be in the document should be defaulted to `#REQUIRED`.

You might also want to use `#REQUIRED` to force authors to give their `IMG` elements `WIDTH`, `HEIGHT`, and `ALT` attributes, as in the following example:

```xml
<!ELEMENT IMG EMPTY>
<!ATTLIST IMG ALT CDATA #REQUIRED>
<!ATTLIST IMG WIDTH CDATA #REQUIRED>
<!ATTLIST IMG HEIGHT CDATA #REQUIRED>
```

---

### `#IMPLIED`

Sometimes you may not have a good option for a default value, but you do not want to require the author of the document to include the attribute either. The attribute is optional.

As with elements, attribute values are almost never set to `N/A`, `Not Available`, unknown, the empty string, or an illegal flag value such as `-1`. If the value of an attribute is not known or not available, simply omit it from the instance document, and declare it `#IMPLIED` in the DTD.

---

### `#FIXED`

Finally, you may want to provide a default value for the attribute without allowing the author to change it.

---

### Attribute Types

All preceding examples have been `CDATA` type attributes. This is the most general type, but there are nine other types permitted for attributes. Altogether, the 10 types are as follows:

- **CDATA**
- **NMTOKEN**
- **NMTOKENS**
- **Enumerated**
- **ID**
- **IDREF**
- **IDREFS**
- **ENTITY**
- **ENTITIES**
- **NOTATION**

Nine of the preceding types are constants used in the type field. The tenth, an enumerated type, lists all valid values explicitly.

---

### CDATA

The `CDATA` type is the most general attribute type. It means the attribute value may be any string of text not containing a less-than sign (`<`) or quotation marks (`"`). These characters can be inserted using the usual entity references (`&lt;`, and `&quot;`) or by character references (`&#x3C;`, and `&#x22;`).

---

### Enumerated

The enumerated type is not an XML keyword, but a list of possible values for the attribute, separated by vertical bars. Each value must be a valid XML name token. The document author can choose any member of the list as the value of the attribute.

```xml
<!ATTLIST P VISIBLE (TRUE | FALSE) "TRUE">
```

---

### Key Points on Attributes

- Attributes are declared by an `<!ATTLIST>` declaration in the DTD.
- One `<!ATTLIST>` can declare an indefinite number of attributes for a single element.
- Attributes normally have default values, but this condition can be changed by using the keywords `#REQUIRED`, `#IMPLIED`, or `#FIXED`.
- There are 10 attribute types: **CDATA**, **Enumerated**, **NMTOKEN**, **NMTOKENS**, **ID**, **IDREF**, **IDREFS**, **ENTITY**, **ENTITIES**, and **NOTATION**.
- The `CDATA` type is the most general. It means an attribute can contain character data. Any well-formed content is valid.
- The `NMTOKEN` type means a valid attribute contains an XML name token. A name token is like an XML name except that it can start with numbers or a hyphen.
- The `NMTOKENS` type means a valid attribute contains a list of XML name tokens separated by white space.
- The `ID` type means a valid attribute contains an XML name that is unique among all `ID` type attributes in the document. An element can have at most one attribute of `ID` type.
- The `IDREF` type means a valid attribute contains an XML name that is also the value of an `ID` type attribute of some element in this document.
- The `IDREFS` type means a valid attribute contains a list of `ID` values separated by white space.
- The `ENTITY` type means a valid attribute contains the name of an unparsed entity declared in the DTD.
- The `ENTITIES` type means a valid attribute contains a white-space separated list of unparsed entity names declared in the DTD.
- The `NOTATION` type means a valid attribute contains the name of a notation declared in the DTD.

---
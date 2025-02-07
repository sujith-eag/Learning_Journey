
### Internal Parameter Entities

General entities become part of the instance document, not the DTD. They can be used in the DTD, but only in places where they will become part of the document content. General entity references cannot insert text that is only part of the DTD and will not be used as part of the document content. It’s often useful, however, to have entity references in a DTD. For this purpose, XML provides the parameter entity reference.

**Key Differences between General Entities and Parameter Entities**:

1. Parameter entity references begin with a percent sign (%) instead of an ampersand (&).
2. Parameter entity references can only appear in the DTD, not the document content.

Parameter entities are declared in the DTD like general entities with the addition of a percent sign before the name. The syntax looks like this:

```xml
<!ENTITY % name "replacement text">
```

The reader sees the replacement text, which must appear in quotes, as in the following example:

```xml
<!ENTITY % ERH "Elliotte Rusty Harold">
<!ENTITY COPY2004 "Copyright 2004 %ERH;">
```

Our earlier failed attempt to abbreviate `(#PCDATA)` works when a parameter entity reference replaces the general entity reference:

```xml
<!ENTITY % PCD "(#PCDATA)">
<!ELEMENT GIVEN_NAME %PCD;>
<!ELEMENT SURNAME %PCD;>
```

The real value of parameter entity references becomes apparent when you’re sharing common lists of children and attributes between elements. The larger the block of text you’re replacing and the more times you use it, the more useful parameter entity references become.

For example, there are four person elements: ACTOR, WRITER, PRODUCER, and DIRECTOR. Each has the same content model or attribute list containing a given name, middle name, middle initial, and/or surname.

The person elements all have the same contents. If you invent a new child element, such as TITLE or HONORIFIC, this element must be declared as a possible child of all four person elements.

DTDs are much easier to maintain if you don’t give each similar element a separate content model. Instead, make the content model a parameter entity reference; then use that parameter entity reference in each of the container element declarations, as in the following example:

```xml
<!ENTITY % NAMES_CONTENT "((GIVEN_NAME, (MIDDLE_NAME | MIDDLE_INITIAL)*, SURNAME?) 
| ((MIDDLE_NAME | MIDDLE_INITIAL)+, SURNAME) | SURNAME)">
<!ELEMENT ACTOR %NAMES_CONTENT;>
<!ELEMENT DIRECTOR %NAMES_CONTENT;>
<!ELEMENT NAME %NAMES_CONTENT;>
<!ELEMENT PRODUCER %NAMES_CONTENT;>
```

Parameter entities can only be used to define content models, element names, and other parts of declarations in the external DTD subset. That is, parameter entity references can only appear inside a declaration in the external DTD subset when their replacement text is something less than a complete declaration.

You’ll mainly use parameter entity references in internal DTD subsets when they’re referring to external parameter entities; that is, when they’re pulling in declarations or parts of declarations from a different file.

---

### External Parameter Entities

External parameter entities enable you to build large DTDs from smaller ones. That is, one DTD can link to another and, in so doing, pull in the elements and entities declared in the first. Although cycles are prohibited — DTD 1 cannot refer to DTD 2 if DTD 2 refers to DTD 1 — such nested DTDs can become large and complex.

At the same time, breaking a DTD into smaller, more manageable chunks makes the DTD easier to analyze, modify, and reuse. Both the document and its DTD become much easier to understand when split into separate files. Furthermore, using smaller, modular DTDs that only describe one set of elements makes it easier to mix and match DTDs created by different people or organizations.

For example, if you’re writing a technical article about high-temperature superconductivity, you can use:

- A molecular sciences DTD to describe the molecules involved,
- A math DTD to write down your equations,
- A vector graphics DTD for the figures, and
- A basic HTML DTD to handle the explanatory text.

**Example**: A DTD about a show in `show.dtd` can be used by a valid document as follows:

```xml
<!DOCTYPE SHOW SYSTEM "show.dtd">
```

```xml
<!ELEMENT STATION (
    ( (NETWORK, CALL_LETTERS?) | CALL_LETTERS ),
    CHANNEL, SHOW+)>
<!ELEMENT NETWORK (#PCDATA)>
<!ELEMENT CALL_LETTERS (#PCDATA)>
<!ELEMENT CHANNEL  (#PCDATA)>
```

Upon closer inspection, you should notice that something is missing: the definition of the `SHOW` element. The definition is in the separate file `show.dtd` and needs to be connected to this DTD.

You connect DTDs with external parameter entity references. This connection takes the following form:

```xml
<!ENTITY % name SYSTEM "URI">
%name;
```

For example:

```xml
<!ENTITY % SHOW SYSTEM "show.dtd">
%SHOW;
```

This example uses a relative URL (`show.dtd`) and assumes that the file `show.dtd` will be found in the same place as the linking DTD. If that’s not the case, you can use an absolute URL, as follows:

```xml
<!ENTITY % SHOW SYSTEM "http://www.cafeconleche.org/dtds/show.dtd">
%SHOW;
```

```xml
<!ELEMENT STATION (
    ( (NETWORK, CALL_LETTERS?) | CALL_LETTERS ),
    CHANNEL, SHOW+)>
<!ELEMENT NETWORK (#PCDATA)>
<!ELEMENT CALL_LETTERS (#PCDATA)>
<!ELEMENT CHANNEL (#PCDATA)>
<!ENTITY % SHOW SYSTEM "http://www.cafeconleche.org/dtds/show.dtd">
%SHOW;
```

A `SCHEDULE` element also contains a `DATE` child element. Although `DATE` could have its own DTD, it doesn’t make sense to split DTDs excessively. Unless you expect there will be documents that contain `DATE` elements not part of a `SCHEDULE`, you should include it in the same DTD.

```xml
<!ELEMENT SCHEDULE (DATE, STATION+)>
<!ELEMENT DATE (#PCDATA)>
<!ENTITY % STATION SYSTEM "station.dtd">
%STATION;
```

It’s now possible to write a valid document including all the shows and stations in the schedule. This document only refers to the schedule DTD using the following document type declaration:

```xml
<!DOCTYPE SCHEDULE SYSTEM "schedule.dtd">
```

It does not need to include the station DTD specifically because the schedule DTD will pull it in, and it does not need to include the show DTD because the station DTD will pull that in. DTD inclusion can have an indefinite number of levels.

---

### Building a Document from Pieces

General entity references allow authors to split documents into many different, smaller, more manageable documents—one for each schedule, station, and show. External entity references connect the shows to form stations and the stations to form schedules.

Unfortunately, you cannot embed just any XML document as an external parsed entity. In particular, the documents you embed cannot have document type declarations. Furthermore, they cannot have standalone declarations because they use a text declaration instead of an XML declaration.

The prolog of an XML file was:

```xml
<?xml version="1.0" standalone="no"?>
<!DOCTYPE SHOW SYSTEM "show.dtd">
```

It is modified so it can be embedded into a new document using an entity reference. The prolog has a text declaration instead of an XML declaration. The document type declaration is completely omitted.

```xml
<?xml encoding="UTF-8"?>
<SHOW>
<NAME>Oprah Winfrey</NAME>
<TYPE>Series/Talk</TYPE>
<START_TIME>19:00-0500</START_TIME>
<LENGTH>60 minutes</LENGTH>
<AIR_DATE>July 3, 2003</AIR_DATE>
<ORIGINAL_AIR_DATE>February 4, 2003</ORIGINAL_AIR_DATE>
<CLOSED_CAPTIONED>Yes</CLOSED_CAPTIONED>
<REPEAT>Yes</REPEAT>
<RATING>TV-PG</RATING>
<DESCRIPTION>
Guests gabber; Oprah looks sympathetic.
</DESCRIPTION>
</SHOW>
```

`wlny.dtd` and `wlny.xml` use external parsed entities to put together a complete station.

```xml
<!-- wlny.dtd -->
<!ENTITY Oprah SYSTEM "oprah.xml">
<!ENTITY SiliconTowers SYSTEM "silicontowers.xml">
```

```xml
<!-- wlny.xml -->
<?xml version="1.0"?>
<!DOCTYPE STATION SYSTEM "wlny.dtd">
<STATION>
<CALL_LETTERS>WLNY</CALL_LETTERS>
<CHANNEL>55</CHANNEL>
&Oprah;
&SiliconTowers;
</STATION>
```

It would be nice to continue this procedure — building a cast by combining actors, a person by combining names, and so forth. Unfortunately, if you try this, you rapidly run into a limitation. The documents embedded via external entities cannot have their own document type declarations. At most, their prologs can contain text declarations. This means you can only have a single level of document embedding. This contrasts with DTD embedding. DTDs can be nested arbitrarily deeply, but instance documents cannot be.

```xml
<?xml version="1.0" standalone="no"?>
<!DOCTYPE SCHEDULE SYSTEM "schedule.dtd" [
<!ENTITY % shows SYSTEM "shows.dtd">
%shows;
<!ENTITY WLNY SYSTEM "wlny.xml">
<!ENTITY WCBS SYSTEM "wcbs.xml">
<!ENTITY HBO SYSTEM "hbo.xml">
]>
<SCHEDULE>
<DATE>July 3, 2003</DATE>
&WCBS;
&WLNY;
&HBO;
</SCHEDULE>
```

The station documents are not usable on their own because the entity references they contain are not defined until they’re aggregated into the master document.

---

### NON-XML Data

Most of the world’s accumulated data isn’t XML. A significant amount is stored in plain text, HTML, and Microsoft Word, to name just three common non-XML formats.

XML provides three constructs for working with non-XML data: **notations**, **unparsed entities**, and **processing instructions**. Notations describe the format of non-XML data. Unparsed entities provide links to the actual location of the non-XML data. Processing instructions give information about how to view the data.

---

### Summary of XML Entities

XML documents are built from both internal and external entities.

- **Entities** are the physical storage units from which an XML document is assembled.
- An entity holds content: well-formed XML, other forms of text, or binary data.
- **Internal entities** are defined completely within the DTD.
- **External entities** draw their content from another resource located via a URL.
- **General entity references** have the form `&name;` and are used in a document’s content.
- **Internal general entity references** are replaced by an entity value given in the entity declaration.
- **External general entity references** are replaced by the data at a URL specified in the entity declaration after the `SYSTEM` keyword.
- **Parameter entity references** have the form `%name;` and are used exclusively in DTDs.
- You can merge different DTDs with external parameter entity references.
- **External entity references** enable you to build large, compound documents out of small parts.
- Invalid documents can still use DTDs to define entity references.
- **Notations** define a data type for non-XML data using a `NOTATION` declaration.
- **Unparsed entities** are storage units containing non-XML text or binary data.
- **Unparsed entities** are defined in the DTD using an `ENTITY` declaration with an extra `NDATA` declaration identifying the type of data through a notation name.
- Documents include unparsed entities using `ENTITY` or `ENTITIES` attributes.
- **INCLUDE** and **IGNORE** blocks specify that the enclosed declarations of the DTD are or are not (respectively) to be considered when parsing the document.

---



### Element Declarations

Elements form the primary structure of an XML document. In valid documents, elements are constrained by element declarations. An element declaration specifies what children, in which orders and quantities, an element with a particular name can have.

Each element used in a valid XML document must be declared by an element declaration in the document’s DTD. Each element declaration gives the name of an element and lists the permissible contents of elements with that name. The list of contents is sometimes called the content specification. The content specification uses a simple grammar to precisely specify what is and isn’t allowed in a document. All it really means is that you attach punctuation marks such as `*`, `?`, `+`, `|`, `(`, and `)` to element names to indicate where and how many times an element may appear.

---

### `ANY`

```xml
<!ELEMENT SCHEDULE ANY>
```

In this declaration, the content specification is the keyword `ANY` (again case-sensitive). This says that all possible elements, as well as plain text, can be children of the `SCHEDULE` element.

---

### `#PCDATA`

```xml
<!ELEMENT YEAR (#PCDATA)>
```

This declaration says that a `DATE` can contain only parsed character data, that is, text that’s not markup. It cannot contain children of its own. Therefore, this `DATE` element is valid:

```xml
<DATE>June 20, 2004</DATE>
```

---

### Content Model

A content model is a parenthesized list of the possible child elements along with various quantifiers that identify how many of each can appear, and other punctuation that indicates whether or not order is significant.

---

### Loosening Restrictions on Children

You can loosen the restrictions on the number of child elements by using quantifiers. You can also loosen the restrictions on order by using choices.

---

### `+` One or More Children

To indicate that you want one or more of a given element, place a plus sign (`+`) after the element name in the child list:

```xml
<!ELEMENT SCHEDULE (DATE, STATION+)>
```

This says that a `SCHEDULE` element must contain a single `DATE` element followed by one or more `STATION` elements. You can also use the `+` quantifier to indicate that each `CAST` has one or more actors:

```xml
<!ELEMENT CAST (ACTOR+)>
```

---

### `?` Zero or One Child

In many cases, an element may only appear once or not at all. You can indicate that a child element is optional in a sequence — that is, that it can appear or not appear — by suffixing its name with a `?`:

```xml
<!ELEMENT ACTOR
(GIVEN_NAME?, MIDDLE_NAME?, MIDDLE_INITIAL?, SURNAME?)>
<!ELEMENT WRITER
(GIVEN_NAME?, MIDDLE_NAME?, MIDDLE_INITIAL?, SURNAME?)>
<!ELEMENT PRODUCER (GIVEN_NAME?, MIDDLE_NAME?, MIDDLE_INITIAL?, SURNAME?)>
<!ELEMENT DIRECTOR (GIVEN_NAME?, MIDDLE_NAME?, MIDDLE_INITIAL?, SURNAME?)>
```

Different elements in the same content model can have different quantifiers.

---

### `*` Zero or More Elements

This indicates a child can appear zero or more times. It can appear once, twice, a thousand times, or not at all. Several potential child elements of `SHOW` can appear once, several times, or not at all:

```xml
<!ELEMENT SHOW (NAME, TYPE?, EPISODE_NUMBER?, START_TIME+,
LENGTH, AIR_DATE, ORIGINAL_AIR_DATE? CLOSED_CAPTIONED?,
REPEAT?, RATING?, STARS?, DIRECTOR*, WRITER*, CAST?,
PRODUCER*, DESCRIPTION)>
```

---

### Choices

You can indicate that the document author needs to input either one or another element by separating child elements with a vertical bar (`|`) rather than with a comma (`,`). For example, this declaration says that the `PAYMENT` element must have a single child element of type `CASH` or `CREDIT_CARD`:

```xml
<!ELEMENT PAYMENT (CASH | CREDIT_CARD)>
```

This sort of content specification is called a choice. You can separate any number of children with vertical bars when you want exactly one of them to be used. For example, the following says that the `PAYMENT` element must have a single child of type `CASH`, `CREDIT_CARD`, or `CHECK`:

```xml
<!ELEMENT PAYMENT (CASH | CREDIT_CARD | CHECK)>
```

---

### Parentheses

Each set of parentheses combines several elements so that the combination is treated as a single unit when validating. This parenthesized unit can then be nested inside other parentheses in place of a single element. Furthermore, you can then affix a plus sign, an asterisk, or a question mark to it. You can group these parenthesized combinations into still larger parenthesized groups to produce quite complex structures. This is a very powerful technique.

```xml
<!ELEMENT DL (DT, DD)*>
```

The parentheses indicate that it’s the matched `<DT><DD>` pair being repeated, not `<DD>` alone.

---

### More Complex Parentheses Usage

This declaration says that an `ACTOR` element can have one or more of `GIVEN_NAME`, `MIDDLE_NAME`, `MIDDLE_INITIAL`, or `SURNAME` child elements:

```xml
<!ELEMENT ACTOR
(GIVEN_NAME | MIDDLE_NAME | MIDDLE_INITIAL | SURNAME)+>
```

To indicate that an `ACTOR` can have any number of middle names and middle initials in any order, but at most one `GIVEN_NAME` and one `SURNAME`, the constraint can be encoded like this. This still allows an `ACTOR` to have no names at all:

```xml
<!ELEMENT ACTOR (GIVEN_NAME?,
(MIDDLE_NAME | MIDDLE_INITIAL)*,
SURNAME?)>
```

A more complex nesting of parentheses can require that each actor have at least one name, though it doesn’t matter whether it’s a `GIVEN_NAME` (Cher), a `MIDDLE_NAME` (Kennedy), or a `SURNAME` (Teller):

```xml
<!ELEMENT ACTOR (
(GIVEN_NAME, (MIDDLE_NAME | MIDDLE_INITIAL)*, SURNAME?)
| ((MIDDLE_NAME | MIDDLE_INITIAL)+, SURNAME)
| SURNAME
)>
```

---

### Mixed Content

You can declare tags that contain both child elements and character data. This is called mixed content. You can use this to allow each `CAST` to include arbitrary text as well as `ACTOR` child elements, as in the following example:

```xml
<!ELEMENT CAST (#PCDATA | ACTOR)*>
```

Mixing child elements with parsed character data severely restricts the structure you can impose on your documents. In particular, you can specify only the names of the child elements that can appear. You cannot constrain the order in which they appear, the number of each that appears, or whether they appear at all. In terms of DTDs, think of this as meaning that the child part of the DTD must look like this:

```xml
<!ELEMENT PARENT (#PCDATA | CHILD1 | CHILD2 | CHILD3)*>
```

---

### Empty Elements

Valid documents must declare both the empty and nonempty elements they use. Because empty elements by definition don’t have children, they’re easy to declare. Use an `<!ELEMENT>` declaration containing the name of the empty element as normal, but use the keyword `EMPTY` (case-sensitive as all XML tags are) instead of a list of children. For example:

```xml
<!ELEMENT BR EMPTY>
<!ELEMENT IMG EMPTY>
<!ELEMENT HR EMPTY>
```

---


```xml
<?xml version="1.0"?>
<FOO>
  Hello XML!
</FOO>
```

The first line of the simple XML document in Listing 3-1 is the XML declaration:

`<?xml version="1.0"?>`

The XML declaration has a **version** attribute. An attribute is a name-value pair separated by an equals sign. The name is on the left side of the equals sign, and the value is on the right side between double quote marks.

---

### Meaning in Markup

Markup can indicate three kinds of meaning: **structural**, **semantic**, or **stylistic**.

- **Structure** specifies the relations between the different elements in the document.
- **Semantics** relates the individual elements to the real world outside of the document itself.
- **Style** specifies how an element is displayed.

**Semantic meaning** exists outside the document, in the mind of the author or reader, or in some computer program that generates or reads these files. For example, a web browser that understands HTML but not XML would assign the meaning "paragraph" to the tags `<P>` and `</P>`, but not to the tags `<GREETING>` and `</GREETING>`.

Naturally, it’s better to pick tags that more closely reflect the meaning of the information they contain.

---

### Style Sheet for an XML Document

A style sheet for an XML document tells browsers how to display particular tags. Like tag sets, style sheets can be shared between different documents and different people, and the style sheets you create can be integrated with style sheets others have written.

Here is an example of a simple style rule for the `GREETING` element:

```css
GREETING { display: block; font-size: 24pt; font-weight: bold }
```

The `<?xml-stylesheet?>` processing instruction has two required attributes: **type** and **href**. The **type** attribute specifies the style sheet language used, and the **href** attribute specifies a URL (possibly relative) where the style sheet can be found.

---

```xml
<?xml version="1.0"?>
<?xml-stylesheet type="text/css" href="greeting.css"?>
<GREETING>
  Hello XML!
</GREETING>
```

---


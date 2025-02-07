
**Namespaces in XML**

Namespaces are a way of attaching prefixes and Uniform Resource Identifiers (URIs) to element and attribute names. This allows applications to distinguish between elements and attributes from different XML vocabularies, even when they have the same names.

When mixing and matching elements from different XML applications, you’re likely to encounter the same name used for two different things. Namespaces help resolve this conflict by associating a URI with each XML application and attaching a unique prefix to each element to indicate which application it belongs to. For example, you can have both `BOOK:TITLE` and `HTML:TITLE` elements or `POSTAL:ADDRESS` and `HTML:ADDRESS` elements, as opposed to having just one generic `TITLE` or `ADDRESS` element.

### Defining Your Own Namespace

If you mix in elements from your own custom vocabulary, you can place them in a separate namespace, identified by a URI within a domain you own.

A **Uniform Resource Identifier (URI)** is an abstraction of a URL. Whereas a URL locates a resource, a URI simply identifies it. For instance, a URI for a person could potentially include that person’s social security number, though this doesn’t mean you can look up the person in a web browser using the URI. In theory, URIs are a superset of URLs, which also include **Uniform Resource Names (URNs)**. In practice, most URIs used today, including most namespace URIs, are actually URLs.

Importantly, the URI that defines a namespace does not necessarily point to a specific file. Its purpose is primarily to group and disambiguate element and attribute names in the XML document. There’s no guarantee that the document at the namespace URI describes the syntax used in the document, or even that the document exists at the URI. In fact, most namespace URIs return 404 errors when accessed.

That said, if there is a canonical URI for a particular XML application, it is a good choice for the namespace definition, but the key point is that the URI serves a symbolic function of identification rather than direct referencing of an actual resource.

### Impact of Namespaces on XML Syntax

Namespaces are carefully crafted to layer on top of the XML 1.0 specification. Other than reserving the colon character to separate prefixes and local names, namespaces have no direct effect on standard XML syntax.

---

### Associating a Namespace with a Prefix

To associate a namespace URI with a prefix, you add an `xmlns:prefix` attribute to the element(s) it applies to. The prefix is then used to qualify element and attribute names within that element's scope. The value of the attribute is the URI of the namespace. For example:

```xml
xmlns:P="http://ns.cafeconleche.org/people/"
```

This `xmlns:P` attribute associates the prefix `P` with the URI `http://ns.cafeconleche.org/people/`. Once this attribute is added to an element, the `P` prefix can be used to qualify both that element's name and the names of its attributes and descendants. Within that element, the `P` prefix identifies something as belonging to the `http://ns.cafeconleche.org/people/` namespace. The prefix is attached to the local name with a colon.

---

### Example of Namespaces in Use

Distinguishing different uses of the same element names:

```xml
<HTML xmlns:SCR="http://ns.cafeconleche.org/scripts/">
  <HEAD><TITLE>Screenplays for Auction</TITLE></HEAD>
  <BODY>
    <H1>January 27, 2004 Auction</H1>
    <P>Pilot scripts for the Fall season:</P>
    <SCR:SCRIPT>
      <SCR:TITLE>Chicken Feathers</SCR:TITLE>
      <SCR:AUTHOR>
        <P:PERSON xmlns:P="http://ns.cafeconleche.org/people/">
          <P:FIRST>William</P:FIRST>
          <P:LAST>Sanders</P:LAST>
          <P:TITLE>Col.</P:TITLE>
        </P:PERSON>
      </SCR:AUTHOR>
      <SCR:SYNOPSIS>
        Hijinks in a poultry factory
      </SCR:SYNOPSIS>
    </SCR:SCRIPT>
  </BODY>
</HTML>
```

- The `HTML` document uses the `SCR` prefix for elements related to a script (e.g., `<SCR:SCRIPT>`, `<SCR:TITLE>`).
- The `P` prefix is used to distinguish elements related to a person (e.g., `<P:PERSON>`, `<P:FIRST>`, `<P:LAST>`, `<P:TITLE>`).


---

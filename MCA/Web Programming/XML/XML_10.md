
The items where the
pieces of an XML document are stored, in whatever form they
take, are called entities. Entity references load these entities
into the main XML document. General entity references load
data into the root element of an XML document. &lt;, &gt;,
&apos;, &quote;, and &amp; are predefined general entity
references that refer to the text entities <, >, ‘, “, and &,
respectively. Parameter entity references load data into the
document’s document type definition (DTD). They begin with
a % instead of an &. Unparsed entities point to non-XML, binary
data whose type is identified with a notation and are referenced
by an ENTITY type attribute. All three kinds of entities are
declared in the DTD.



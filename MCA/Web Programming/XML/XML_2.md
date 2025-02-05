
### XML Application

XML is a meta-markup language for designing domain-specific markup languages. Each specific XML-based markup language is called an XML application. This is not an application that uses XML, such as the Mozilla web browser. Instead, it is an application of XML to a specific domain, such as Chemical Markup Language (CML) for chemistry or GedML for genealogy.

Each XML application has its own semantics and vocabulary, but the application still uses XML syntax.

Examples of XML applications include:

- **Chemical Markup Language (CML)**
- **Mathematical Markup Language (MathML)**
- **RSS**
- **Scalable Vector Graphics (SVG)**
- **MusicXML**
- **VoiceXML**

---

### XSL

XSL, the Extensible Stylesheet Language, is actually two XML applications.

1. **XSLT (XSL Transformations):** This is a vocabulary for transforming XML documents. XSLT defines markup that represents trees, nodes, patterns, templates, and other constructs that can be used to transform XML documents from one markup vocabulary to another (or even to the same vocabulary with different data).
    
2. **XSL-FO (XSL Formatting Objects):** This is an XML vocabulary for formatting the transformed XML document produced by the first part. XSL-FO provides elements that describe the layout of a page, including pagination, blocks, characters, lists, graphics, boxes, fonts, and more.
    

Here is an example of a simple XSLT style sheet that transforms an input document into XSL formatting objects:

```xml
<?xml version="1.0"?>
<xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns:fo="http://www.w3.org/1999/XSL/Format">
  <xsl:template match="/">
    <fo:root xmlns:fo="http://www.w3.org/1999/XSL/Format">
      <fo:layout-master-set>
        <fo:simple-page-master master-name="only">
          <fo:region-body/>
        </fo:simple-page-master>
      </fo:layout-master-set>
      <fo:page-sequence master-reference="only">
        <fo:flow flow-name="xsl-region-body">
          <xsl:apply-templates select="//ATOM"/>
        </fo:flow>
      </fo:page-sequence>
    </fo:root>
  </xsl:template>

  <xsl:template match="ATOM">
    <fo:block font-size="20pt" font-family="serif" line-height="30pt">
      <xsl:value-of select="NAME"/>
    </fo:block>
  </xsl:template>
</xsl:stylesheet>
```

---

### XLinks

XML introduces a new, more general kind of link called an **XLink**. XLinks accomplish everything possible with HTML’s URL-based hyperlinks and anchors. However, with XLinks, any element can become a link, not just `<A>` elements. For example, a footnote element can link directly to the text of the note like this:

```xml
<footnote xmlns:xlink="http://www.w3.org/1999/xlink"
          xlink:type="simple"
          xlink:href="footnote7.xml">7</footnote>
```

Furthermore, XLinks can do many things that HTML links cannot. XLinks can be bidirectional, meaning readers can return to the page they came from. XLinks can link to arbitrary positions in a document. XLinks can also embed text or graphic data inside a document, rather than requiring the user to activate the link (similar to HTML’s `<IMG>` tag but more flexible).

In short, XLinks make hypertext even more powerful.

---


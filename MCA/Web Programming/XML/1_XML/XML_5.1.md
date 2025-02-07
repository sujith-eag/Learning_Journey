
### XSL

SS styles only apply to element content, not to attributes. If you use CSS, any data that you want to display to the reader should be part of an element’s content rather than one of its attributes.

However, there is an alternative stylesheet language that does allow browsers to display attribute content. This is the **Extensible Stylesheet Language (XSL)**. XSL is divided into two parts:

- **XSL Transformations (XSLT)**: This enables you to replace one tag with another. You define rules that map your XML tags to standard HTML tags, or to HTML tags plus CSS attributes. XSLT can reorder elements in the document and even add additional content that was never present in the XML document.
- **XSL Formatting Objects (XSL-FO)**: This defines an extremely powerful view of documents as pages. XSL-FO enables you to specify the appearance and layout of a page, including:
    - Multiple columns
    - Text flow around objects
    - Line spacing
    - Widow and orphan control
    - Font faces, styles, sizes, etc.

It is designed to be powerful enough to lay out documents for both the Web and print automatically from the same source document. For example, a local newspaper could use two different XSL style sheets to generate both the printed and online editions of the television listings from the same source document automatically. However, no web browsers yet support XSL formatting objects.

#### Templates

An XSLT stylesheet contains templates into which data from the XML document is poured. For example, a template might look similar to this:

```xml
<HTML>
  <HEAD>
    <TITLE>
      XSLT Instructions to get the date
    </TITLE>
  </HEAD>
  <BODY>
    <H1>XSLT Instructions to get the date</H1>
    XSLT Instructions to get the schedule
  </BODY>
</HTML>
```

The italicized sections will be replaced by particular XSLT elements that copy data from the underlying XML document into this template. You can apply this template to many different data sets.

The actual transformation of the source XML document by the XSLT stylesheet takes place on the **client** rather than on the server. Furthermore, the output document does not have to be HTML. It can be any well-formed XML.

XSLT instructions can retrieve any data in the XML document. This includes:

- Element content
- Element names
- Attribute names and values
- Its absolute and relative position in the tree structure of the XML document, and more.

Once the data is extracted from an element, it can be moved, copied, and manipulated in a variety of ways.

---

### Example XSLT Stylesheet

```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="SCHEDULE">
    <HTML>
      <HEAD>
        <TITLE>TV Listings</TITLE>
      </HEAD>
      <BODY>
        <H1>TV Listings</H1>
        <HR></HR>
        Copyright 2003
        <A HREF="http://www.elharo.com">Elliotte Rusty Harold</A>
        <BR />
        <A HREF="mailto:elharo@metalab.unc.edu">elharo@metalab.unc.edu</A>
      </BODY>
    </HTML>
  </xsl:template>
</xsl:stylesheet>
```

This stylesheet resembles an HTML file included inside an `<xsl:template>` element. In other words, its structure looks like this:

```xml
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="SCHEDULE">
    HTML file goes here
  </xsl:template>
</xsl:stylesheet>
```

It is not just an XSLT stylesheet; it’s also an XML document. It begins with an XML declaration. The root element of this document is `<xsl:stylesheet>`. This stylesheet contains a single template for the XML data encoded as an `<xsl:template>` element. The `<xsl:template>` element has a `match` attribute with the value `SCHEDULE`, and its content is a well-formed HTML document.

**Note**: The HTML must be well-formed because XSLT style sheets are well-formed XML documents.

---

### Attaching the XSLT Stylesheet to the XML Document

Attaching the XSLT stylesheet to the XML document is straightforward. Simply add an `<?xml-stylesheet?>` processing instruction with a type attribute set to `application/xml` and an `href` attribute that points to the stylesheet:

```xml
<?xml version="1.0"?>
<?xml-stylesheet type="application/xml" href="5-2.xsl"?>
<SCHEDULE DATE="July 3, 2003">
```

This is the same way that a CSS stylesheet is attached to a document, except the type attribute uses `application/xml` instead of `text/css`.

---

### XSLT Instructions to Extract Data

After the browser loads the XML document, it compares the root to each `<xsl:template>` element until it finds one that matches.

Although the style sheet in Listing 5-3 displays something (unlike the CSS stylesheet of Figure 5-2), it doesn’t show any data from the XML document. To add this, you need to use XSLT instruction elements to copy data from the source XML document into the output document.

Here’s an example using `xsl:value-of` to insert the `DATE` attribute from the `SCHEDULE` element:

```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="SCHEDULE">
    <HTML>
      <HEAD>
        <TITLE>TV Listings <xsl:value-of select="@DATE"/></TITLE>
      </HEAD>
      <BODY>
        <H1>TV Listings <xsl:value-of select="@DATE"/></H1>
        <HR></HR>
        Copyright 2003
        <A HREF="http://www.elharo.com">Elliotte Rusty Harold</A>
        <BR />
        <A HREF="mailto:elharo@metalab.unc.edu">elharo@metalab.unc.edu</A>
      </BODY>
    </HTML>
  </xsl:template>
</xsl:stylesheet>
```

In the example above, the XSLT instruction extracts the `DATE` attribute from the `SCHEDULE` element using:

```xslt
<xsl:value-of select="@DATE"/>
```

This instruction copies the value of the `DATE` attribute into the output.

---

### Iterating Over Elements with `xsl:for-each`

If there are multiple elements to display, you can use `xsl:for-each`. This loop will go through each `STATION` element, output its attributes, and loop through each `SHOW` element inside it:

```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="SCHEDULE">
    <HTML>
      <HEAD>
        <TITLE>TV Listings <xsl:value-of select="@DATE"/></TITLE>
      </HEAD>
      <BODY>
        <H1>TV Listings <xsl:value-of select="@DATE"/></H1>
        <xsl:for-each select="STATION">
          <H2>
            <xsl:value-of select="@NETWORK"/>
            <xsl:value-of select="@CALL_LETTERS"/>
            <xsl:value-of select="@CHANNEL"/>
          </H2>
        </xsl:for-each>
        <HR></HR>
        Copyright 2003
        <A HREF="http://www.elharo.com">Elliotte Rusty Harold</A>
        <BR />
        <A HREF="mailto:elharo@metalab.unc.edu">elharo@metalab.unc.edu</A>
      </BODY>
    </HTML>
  </xsl:template>
</xsl:stylesheet>
```

---

### Conditional Logic with `xsl:if`

To conditionally display data based on certain conditions, you can use the `xsl:if` element:

```xslt
<H2>
  <xsl:if test="@NETWORK=''">
    <xsl:value-of select="@CALL_LETTERS"/>
  </xsl:if>
  <xsl:value-of select="@NETWORK"/>
  <xsl:value-of select="@CHANNEL"/>
</H2>
```

This will only display the call letters if the `NETWORK` attribute is empty.

---

### Sorting Data with `xsl:sort`

You can easily sort the data by various criteria using `xsl:sort` within `xsl:for-each`. For example, to sort by `start time` in ascending order:

```xslt
<xsl:for-each select="STATION">
  <xsl:sort select="@START_TIME" order="ascending"/>
</xsl:for-each>
```

---

### Displaying Data in a Table

You can arrange the shows in a table format, as follows:

```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="SCHEDULE">
    <HTML>
      <HEAD>
        <TITLE>TV Listings <xsl:value-of select="@DATE"/></TITLE>
      </HEAD>
      <BODY>
        <H1 STYLE="text-align: center">TV Listings <xsl:value-of select="@DATE"/></H1>
        <TABLE CELLSPACING="0" RULES="all" FRAME="box">
          <xsl:for-each select="STATION">
            <xsl:sort select="@CHANNEL" />
            <TR>
              <TD><xsl:value-of select="@NETWORK"/></TD>
              <TD><xsl:value-of select="@CHANNEL"/></TD>
              <xsl:for-each select="SHOW">
                <TD><B><xsl:value-of select="@NAME"/></B></TD>
              </xsl:for-each>
            </TR>
          </xsl:for-each>
        </TABLE>
        <HR></HR>
        Copyright 2003
        <A HREF="http://www.elharo.com">Elliotte Rusty Harold</A>
        <BR />
        <A HREF="mailto:elharo@metalab.unc.edu">elharo@metalab.unc.edu</A>
      </BODY>
    </HTML>
  </xsl:template>
</xsl:stylesheet>
```

---

### CSS vs. XSL

XSL is definitely more powerful than CSS. CSS only allows you to apply formatting to element content. It does not allow you to change or reorder that content, choose different formatting for elements based on their contents or attributes, or add boilerplate text like a signature block. XSL is far more appropriate when the XML documents contain only the minimum of data and none of the HTML frou-frou that surrounds the data.

---


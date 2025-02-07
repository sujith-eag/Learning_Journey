
### Attributes

Elements can have attributes. Each attribute of an element is encoded in the start-tag of the element as a name-value pair separated by an equals sign (`=`) and, optionally, some extra whitespace. The attribute value is enclosed in either single or double quotes. For example:

```xml
<GREETING LANGUAGE="English">
  Hello XML!
  <MOVIE SRC="WavingHand.mov"/>
</GREETING>
```

Here, the `GREETING` element has a `LANGUAGE` attribute that has the value `English`. The `MOVIE` element has an `SRC` attribute with the value `WavingHand.mov`.

- The same element cannot have two attributes with the same name.
- Attribute names are case-sensitive.
- Attribute values are strings. Even when the string shows a number, as in the `LENGTH` attribute that follows, that number is the two characters `7` and `2`, not the binary number `72`.

```xml
<RULE LENGTH="72"/>
```

If you’re writing code to process XML, you’ll need to convert the string to a number before performing arithmetic on it.

Here are a few limits on the content of an attribute value:

- Attribute values can contain whitespace, begin with a number, or contain any punctuation characters (except, sometimes, for single and double quotes).
- The only characters an attribute value cannot contain are the angle brackets `<` and `>`, though these can be included using the `&lt;` and `&gt;` entity references.

---

### Predefined Attributes

XML assigns special meaning to attributes that begin with `xml:`. Currently, three such attributes are defined: `xml:lang`, `xml:space`, and `xml:base`.

- The `xml:space` attribute describes how whitespace is treated in the element.
- The `xml:lang` attribute describes the language (and, optionally, dialect and country) in which the element is written.
- The `xml:base` attribute provides the base URL against which relative URLs in the element should be resolved.

XML, however, preserves whitespace by default. The XML processor passes all whitespace characters to the application unchanged. The application usually ignores the extra whitespace. However, the XML processor can tell the application that certain elements contain significant whitespace that should be preserved. The page author uses the `xml:space` attribute to indicate these elements to the application. The value `preserve` indicates that whitespace is significant; the value `default` indicates that it isn’t.

```xml
<?xml version="1.0"?>
<PROGRAM xml:space="preserve">
  public class AsciiTable {
    public static void main (String[] args) {
      for (int i = 0; i < 128; i++) {
        System.out.println(i + "\n" + (char) i);
      }
    }
  }
</PROGRAM>
```

Descendants (child elements and their children, and their children’s children, and so on) of an element for which `xml:space` is defined are assumed to behave similarly to their parent (either preserving or not preserving space), unless they possess an `xml:space` attribute with a conflicting value.

---

### xml:lang

The `xml:lang` attribute identifies the language in which its element’s content is written. Ideally, each of these attribute values should be one of the two-letter language codes defined by the original ISO-639 standard.

---

### Entity References

Entity references are used to represent characters that are difficult to encode directly in XML. Here are a few common predefined entity references:

|Entity Reference|Character|
|---|---|
|`&amp;`|`&`|
|`&lt;`|`<`|
|`&gt;`|`>`|
|`&quot;`|`"`|
|`&apos;`|`'`|

---

### Processing Instructions

Processing instructions are like comments that are intended for computer programs reading the document rather than people reading the document. However, XML parsers are required to pass along the contents of processing instructions to the application on whose behalf they’re parsing, unlike comments that a parser is allowed to silently discard. The application that receives the information is free to ignore any processing instruction it doesn’t understand.

Processing instructions begin with `<?` and end with `?>`. The starting `<?` is followed by an XML name called the target, which identifies the program that the instruction is intended for, followed by data for that program. For example, you saw this processing instruction in the last chapter:

```xml
<?xml-stylesheet type="text/xml" href="5-2.xsl"?>
```

The target of this processing instruction is `xml-stylesheet`. This is a standard name that means the data in this processing instruction is intended for any web browser that can apply a style sheet to the document. `type="text/xml"` and `href="5-2.xsl"` are the processing instruction data that will be passed to the application reading the document. If that application happens to be a web browser that understands XSLT, it will apply the style sheet `5-2.xsl` to the document and render the result. If that application is anything other than a web browser, it will simply ignore the processing instruction.

---

### Comments

Comments in XML are enclosed within `<!--` and `-->`. They are ignored by XML processors.

```xml
<!-- This is a comment -->
```

---

### CDATA

CDATA sections are used when you want all text to be interpreted as pure character data rather than as markup. The text within a CDATA section is not processed by the XML parser, and special characters like `<` and `&` are not treated as markup.

```xml
<![CDATA[
System.out.print("<");
if (x <= args.length && y > z) {
  System.out.println(args[x - y]);
}
System.out.println(">");
]]>
```

The only text that’s not allowed within a CDATA section is the closing CDATA delimiter `]]>`. Comments may appear in CDATA sections but do not act as comments. That is, both the comment tags and all the text they contain will be displayed.

CDATA sections are extremely useful if you’re trying to write about HTML or XML in XML. For example, this book contains many small blocks of XML code.

---



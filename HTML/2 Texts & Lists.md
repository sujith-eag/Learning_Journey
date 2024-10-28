#02sep24

### Paragraphs  `<p> </p>`    

All text can be put inside the `<body>` but the spaces will not be considered so paragraph tag can be used.


### Headings `<h1>  </h1>`

The larger and bolder texts form the headings, there are 6 versions from `<h1>` to `<h6>`


### Strong `<strong>  </strong>`

The `<strong>` tag is used when we want to indicate the importance, seriousness, or urgency of a word or section of content without changing the meaning of the content itself.


### Emphasis `<em>  </em>`

The `<em>` tag places stress emphasis on a particular piece of content in a way that changes the actual meaning of the content with verbal stress.


### Italic `<i>  </i>`

The `<i>` tag is used to convey a different mood or voice from the surrounding content. It’s often used with foreign words or idiomatic phrases, technical terms, ship names, thoughts, etc


### Bold `<b>  </b>`

The `<b>` tag draws attentions to word or section of content for utilitarian purposes without conveying extra importance, emphasis, alternate voice or mood, etc. It is the _least_ semantic of the HTML tags we’ve discussed in this post, and should only be used when no other tag is more appropriate.

______

### Small `<small>  </small>`
Defines smaller text

### Highlight / mark `<mark>  </mark>`

### Strike out / delete  `<del>  </del>`

### Insert `<ins>  </ins>`
after deletion other word can be shown as inserted, which is represented by underline.

### Subscript `<sub>  </sub>`
Used to denote the text which is half the size and at lower part of text, similar to formulas in maths chemistry.

### Superscript `<sup>  </sup>`
The text appears half a character above the normal line and in small font. Superscript text can be used to show footnotes links.


## Nesting and Indentation

Nesting is used to show the parent, child and sibling tag relation.  
Indentation is used to make this relationships easier to see.


## HTML Comments `<!-- text-->`
VScode shortcut for comment,  `Ctrl + /` to convert any line into comment or revert it.

____________

## Lists

### Unordered Lists  `<ul>  <li> </li>  </ul>`       #02sep24 
Used when the order doesn't matter. each item in the list is represented by `<li>` which will be represented by a bullet point of circle, square or dot. The styles will be defined by CSS `line-style-type`


### Ordered Lists `<Ol>  <li> </li>  </ul>`
For creating a list of items where order and numbering does matter.
By default `<ol>` will assign numbers to each of the list items added.

Both can be listed inside the other as much as needed.
if a second list has to be nested inside the second item, then it should be inside it's `<li>  </li>`

```HTML
<ul>
  <li>first item</li>
  <li>
    second item
    <!-- Look, the closing </li> tag is not placed here! -->
    <ul>
      <li>second item first subitem</li>
      <li>
        second item second subitem
        <!-- Same for the second nested unordered list! -->
        <ul>
          <li>second item second subitem first sub-subitem</li>
          <li>second item second subitem second sub-subitem</li>
          <li>second item second subitem third sub-subitem</li>
        </ul>
      </li>
      <!-- Closing </li> tag for the li that
                  contains the third unordered list -->
      <li>second item third subitem</li>
    </ul>
    <!-- Here is the closing </li> tag -->
  </li>
  <li>third item</li>
</ul>


- first item
- second item
    - second item first subitem
    - second item second subitem
        - second item second subitem first sub-subitem
        - second item second subitem second sub-subitem
        - second item second subitem third sub-subitem
    - second item third subitem
- third item
```

## Global Attributes

`reversed`  numbered from high to low.    
`start="4"` starts numbers from 4.  
`type`  `a` for lowercase `A` for uppercase.  
`i` for lower roman `I` for upper roman.  

```HTML
<ol start="4">        starts from 4
</ol>

<ol reversed>  </ol>
```

#### Value attribute

Used on individual `<li>` within an ordered list to change the value of the list.
```HTML
<ol>
  <li>Head north on N Halsted St</li>
  <li value="9">Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```


### Description Lists

Another type of list is the description list. 
Description lists are used to outline multiple terms and their descriptions, as in a glossary, for example.

Creating a description list in HTML is accomplished using the description list block-level element, `<dl>`. 
Instead of using a `<li>` element to mark up list items, the description list requires two block-level elements: 
the description term element, `<dt>`, 
and the description element, `<dd>`.

`<dd>` element includes a left `margin` by default.
The definition term and the description that directly follows it correspond to one another; thus, the order of these elements is important.

```HTML
<dl>
  <dt>study</dt>
  <dd>The devotion of time and attention to acquiring knowledge on an academic subject, especially by means of books</dd>
  <dt>design</dt>
  <dd>A plan or drawing produced to show the look and function or workings of a building, garment, or other object before it is built or made</dd>
  <dd>Purpose, planning, or intention that exists or is thought to exist behind an action, fact, or material object</dd>
  <dt>business</dt>
  <dt>work</dt>
  <dd>A person's regular occupation, profession, or trade</dd>
</dl>


study

The devotion of time and attention to acquiring knowledge on an academic subject, especially by means of books

design

A plan or drawing produced to show the look and function or workings of a building, garment, or other object before it is built or made

Purpose, planning, or intention that exists or is thought to exist behind an action, fact, or material object

business

work

A person's regular occupation, profession, or trade

```


### `list-style-type` property

List items styling done through CSS.
The style maybe placed on either the `<ul>  <ol>  or  <li>` elements within CSS.  [[List Styles]]

```CSS
/* Partial list of types */
list-style-type: disc;
list-style-type: circle;
list-style-type: square;
list-style-type: decimal;
list-style-type: georgian;
list-style-type: trad-chinese-informal;
list-style-type: kannada;

/* <string> value */
list-style-type: "-";

/* Identifier matching an @counter-style rule */
list-style-type: custom-counter-style;

/* Keyword value */
list-style-type: none;

/* Global values */
list-style-type: inherit;
list-style-type: initial;
list-style-type: revert;
list-style-type: revert-layer;
list-style-type: unset;
```


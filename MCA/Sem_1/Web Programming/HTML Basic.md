
### HTML5 Features

- New semantic elements (e.g., `<article>`, `<section>`, `<header>`, `<footer>`)
- Native support for audio and video
- Offline web apps
- Geolocation API
- Local storage (instead of cookies)
- Canvas for 2D graphics
- Form enhancements (e.g., new input types like `email`, `date`, `tel`)
- Emphasis on interactivity

---

### HTML Formatting

```html
<b> - Bold text  
<em> - Emphasized text  
<strong> - Important text  
<i> - Italic text  
<mark> - Marked text  
<small> - Smaller text  
<del> - Deleted text  
<ins> - Inserted text  
<sub> - Subscript text  
<sup> - Superscript text
```

---

### HTML Attributes

- **HTML attributes** provide additional information about an element, defining its behavior or appearance. They are specified in the opening tag and usually come in name-value pairs.
    
- The `<a>` tag defines a hyperlink. The `href` attribute specifies the URL of the page the link goes to.
    
    ```html
    <a href="www.google.com">Go to Google's website</a>
    ```
    
- The `title` attribute defines extra information about an element. The value of the `title` attribute will be displayed as a tooltip when you mouse over the element.
    
    ```html
    <h2 title="Hello There!">Heading 2</h2>
    ```
    

---

### HTML Font

- The `<font>` tag in HTML was used to define the font size, color, and face of text. It uses a scale from 1 to 7:
    - `1` is the smallest font size.
    - `7` is the largest font size.
    - `3` is the default size.

Example:

```html
<p><font size="5">Here is a size 5 font</font></p>
```

---

### HTML Links

- A hyperlink references or links to other resources, such as HTML5 documents and images. By default, web browsers underline text hyperlinks and color them blue.

Example:

```html
<a href="www.google.com">Go to Google's website</a>
```

- Link state colors:
    - An unvisited link is underlined and blue.
    - A visited link is underlined and purple.
    - An active link is underlined and red.

You can change these link state colors using CSS.

---

### HTML Links - The `target` Attribute

- By default, the linked page will be displayed in the current browser window. To change this, specify another target for the link.
- The `target` attribute can have one of the following values:
    - `_self`: Default. Opens the document in the same window/tab.
    - `_blank`: Opens the document in a new window or tab.
    - `_parent`: Opens the document in the parent frame.
    - `_top`: Opens the document in the full body of the window.

---

### HTML Images

- The `<img>` tag is used to embed an image in an HTML page. The `src` attribute specifies the path to the image.

Example:

```html
<img src="image1.jpg" width="500" height="600">
```

- The `alt` attribute specifies an alternate text for an image, in case it can't be displayed.

```html
<img src="image2.jpg" alt="New Year wishes">
```

- **Image as a Link**: To use an image as a link, place the `<img>` tag inside the `<a>` tag.
    
- **Background Image**: To add a background image on an HTML element, use the `style` attribute and the CSS `background-image` property.
    
    ```html
    <p style="background-image: url('img_girl.jpg');">
    ```
    

---

### HTML Lists

- **Unordered List**: Starts with the `<ul>` tag. Each list item starts with the `<li>` tag, and items are marked with bullets by default.

```html
<ul style="list-style-type:disc;">
  <li>Web Programming</li>
  <li>Java</li>
  <li>Python</li>
</ul>
```

- **Ordered List**: Starts with the `<ol>` tag. Each list item starts with the `<li>` tag, and items are numbered by default.

```html
<ol type="i">
  <li>Web Programming</li>
  <li>Java</li>
  <li>Python</li>
</ol>
```

- **Description List**: A list of terms with a description for each term. Use `<dl>` for the list, `<dt>` for the term, and `<dd>` for the description.

---

### HTML Tables

- A table consists of table cells inside rows and columns. Use the `<tr>` tag to define a row, and `<td>` to define a table cell.

```html
<table>
  <tr>
    <th>Company</th>
    <th>Contact</th>
  </tr>
  <tr>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td>
  </tr>
  <tr>
    <td>Centro comercial Moctezuma</td>
    <td>Francisco Chang</td>
  </tr>
</table>
```

---

### HTML Table Tags

- `<table>`: Defines the table structure.
- `<caption>`: Adds a title above the table.
- `<colgroup>`: Groups the columns for styling purposes.
- `<col>`: Allows us to apply styles to individual columns within the `<colgroup>`.
- `<thead>`: Wraps the header row, grouping all header content together.
- `<tr>`: Defines a row in the table.
- `<th>`: Specifies header cells (bold and centered by default).
- `<td>`: Specifies data cells within the rows.
- `<tbody>`: Groups the body content in the table.
- `<tfoot>`: Groups the footer content and can contain summary information like averages or totals.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>HTML Table with Colspan and Rowspan</title>
  <style>
    table {
      width: 80%;
      border-collapse:collapse;
    }
    th, td {
      border: 1px solid black;
      padding: 8px;
      text-align: center;
    }
    caption {
      font-size: 1.5em;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <table>
    <caption>Team Meeting Schedule</caption>

    <!-- Grouping columns for styling -->
    <colgroup>
      <col style="background-color: #f2f2f2;">
      <col style="background-color: #e0e0e0;">
      <col style="background-color: #f2f2f2;">
      <col style="background-color: #e0e0e0;">
    </colgroup>

    <!-- Table header -->
    <thead>
      <tr>
        <th rowspan="2">Team Member</th>
        <th colspan="2">Meeting Times</th>
        <th rowspan="2">Notes</th>
      </tr>
      <tr>
        <th>Morning</th>
        <th>Afternoon</th>
      </tr>
    </thead>

    <!-- Table body -->
    <tbody>
      <tr>
        <td>John Doe</td>
        <td>9:00 AM</td>
        <td>2:00 PM</td>
        <td>Available for both</td>
      </tr>
      <tr>
        <td>Jane Smith</td>
        <td>10:30 AM</td>
        <td>1:30 PM</td>
        <td>Prefer afternoon</td>
      </tr>
      <tr>
        <td>Sam Wilson</td>
        <td colspan="2">Unavailable</td>
        <td>Out of office</td>
      </tr>
    </tbody>

    <!-- Table footer -->
    <tfoot>
      <tr>
        <td colspan="4">End of Schedule</td>
      </tr>
    </tfoot>
  </table>
</body>
</html>

```

---

### HTML Table Borders

- To add borders to tables, use the CSS `border` property.

```css
table, th, td {
  border: 1px solid black;
}
```

- **Collapsed Table Borders**: To avoid double borders, set `border-collapse` to `collapse`.

```css
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

- **Round Table Borders**: Use `border-radius` to round the corners.

```css
table, th, td {
  border: 1px solid black;
  border-radius: 10px;
}
```

---

### HTML Table Sizes

- **Table Width**: To set the width of a table, add the `style` attribute to the `<table>` tag.

```html
<table style="width:100%">
  <tr>
    <th style="width:70%">Firstname</th>
    <th>Age</th>
  </tr>
  <tr style="height:200px">
    <td>Jill</td>
    <td>50</td>
  </tr>
</table>
```

- **Rowspan and Colspan**: Use `rowspan` and `colspan` to make a cell span over multiple rows or columns.

```html
<table border="1">
  <tr>
    <th colspan="2">Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>43</td>
  </tr>
</table>
```

---

### HTML - `bgcolor` Attribute

- The `bgcolor` attribute is used to set the background color of an element (typically a `<body>` or `<table>`).

```html
<body bgcolor="yellow">
<body style="background-color: yellow;>
  <h1>This background is yellow!</h1>
</body>
```

- The `style` attribute is used to add inline styles to an element.

```html
<p style="color:red;">This is a red paragraph.</p>
```

---


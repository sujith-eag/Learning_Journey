[[3 Declaration]]
There are three methods to do so.
## External CSS    #02sep24 
It involves creating a separate file for the CSS and linking it inside of an HTML’s opening and closing `<head>` tags with a void `<link>` element:

First, we add a void `<link>` element inside of the opening and closing `<head>` tags of the HTML file. 
The `href` attribute is the location of the CSS file.
The `rel` attribute is required, and it specifies the relationship between the HTML file and the linked file.

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="styles.css">
</head>
```
```css
/* styles.css */

div {
  color: white;
  background-color: black;
}

p {
  color: red;
}
```

A couple of the pros to this method are:
1. It keeps our HTML and CSS separated, which results in the HTML file being smaller and making things look cleaner.
2. We only need to edit the CSS in _one_ place, which is especially handy for websites with many pages that all share similar styles.

## Internal CSS

Internal CSS (or embedded CSS) involves adding the CSS within the HTML file itself instead of creating a completely separate file. 

The rules are placed inside of a pair of opening and closing `<style>` tags, which are then placed inside of the opening and closing `<head>` tags of your HTML file. 
Since the styles are being placed directly inside of the `<head>` tags, we no longer need a `<link>` element that the external method requires.

Besides these differences, the syntax is exactly the same as the external method (selector, curly braces, declarations):

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>
  ...
</body>
```

This method can be useful for adding unique styles to a _single page_ of a website, but it doesn’t keep things separate like the external method, and depending on how many rules and declarations there are it can cause the HTML file to get pretty big.

## Inline CSS

Inline CSS makes it possible to add styles directly to HTML elements, though this method isn’t as recommended:

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

No selectors are used here, since the styles are being added directly to the opening `<div>` tag itself. 
Next, we have the `style=` attribute, with its value within the pair of quotation marks being the declarations.



[[3 Declaration]]        Next

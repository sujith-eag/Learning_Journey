shortcode template
These are essentially `partial templates` but instead of being used inside of templates inside layout folder for `HTML` files, it is used inside content folder with the `markdown` files to insert some specific code. 

crating a file `shortcodes/someshortcode.html`
`{{< someshortcode >}}`  accessing it inside `md` file.

parameters inside the short code `{{< someshortcode color="blue">}}`
it can be accessed inside `html` file using `.Get`
```
`<p style= "color:{{ .Get `color` }}"`>This is the framework text</p>
```
There can be positional parameter using indexing

Doubly tagged shortcode to contain more data `{{< shortcode >}} {{< /shortcode}}`  to get all the contain in between `{{.Ineer}}`

If markdown is inside, it wont get turned to proper html, so then instead of `<>` it can use `%%` which renders the html
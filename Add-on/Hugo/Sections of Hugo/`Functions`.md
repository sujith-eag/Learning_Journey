(template functions)
Prebuilt code to be used in templates. `{{ funcName param1 param2 }} {{ end }} `
`truncate` to cut off a string to certain number.
`range` to loop through collection like page lists `.Pages`



`if statements`
`eq, lt, le, gt, ge, not` which means `=, <, <=, >, >=, !`
operator comes before the two things that has to be compared, not in between.
making a statement to highlight current page
```go
 {{ $title := .Title }}
 {{ range .Site.Pages }}
	 <li><a href="{{ .RelPermalink }}" style="{{ if eq .Title $title }} backgound-color: yellow {{ end }}" > {{}}
```

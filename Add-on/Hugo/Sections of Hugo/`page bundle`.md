`leaf bundles`  `page bundles` that contains `index.md` file with resources or none, at end of branch with no descendants. Use it to associate one or more resources with content.
It is a directory that encapsulates both content and associated resources.

a dir `about` with `index.md` and `welcome.jpg` is a `page bundle`, because it logically associates a resource with content by bundling them together. (`about` dir is basically one page with all needed resources), resources can be nested inside other dir without `index.md`.



### Example for Page resource capture and render

Methods to be used on `page object`To capture page resource
```go
Resources.ByType
Resources.Get
Resources.Match
Resources.GetMatch
```
Once resource is captured, applicable methods can be used to return a value or perform action.

Assume a dir `example` with `index.md`,  `data/books.json`, `images/a.jpg, b.jpg` and `snippets/text.md` . So this is a `page bundle` where one index files exists with no other folders having it. all dir become `page resources`

Render a single image and throw an error if file does not exist.
```go
{{ $path := "image/a.jpg" }}
{{ with .Resources.Get $path }}
	<img src="{{ .RelPermalink }}"  width="{{ .Width }}" height="{{ .Height }}"  alt="" >
{{ else }}
	{{ errorf "Unable to get page resources %q" $path }}
{{ end }}
```

Render all images, resized to 300px
```go
{{ range .Resources.ByType "image" }}
	{{ with .Resize "300x" }}
		<img src="{{ .RelPermalink }}" width="{{ .Width }}" height="{{ .Height }}"  alt="" >
	{{ end }}
{{ end }}
```

Render the markdown snippet
```go
{{with .Resource.Get "snippets/text.md"}}
	{{ .Content }}
{{ end }}
```

List the titles in the data file, and throw error if the file does not exist.
```go
{{ $path := "data/books.json"}}
{{ with .Resources.Get $path }}
	{{ with . | transform.Unmarshal }}
		<p>Books:</p>
		<ul>
			{{ range . }}
				<li> {{ .title }} </li>
			{{ end }}
		</ul>
	{{ end }}
{{ else }}
	{{ errorf "Unable to get page resources %q" $path }}
{{ end }}
```


Further on metadata in [page resources](https://gohugo.io/content-management/page-resources/)
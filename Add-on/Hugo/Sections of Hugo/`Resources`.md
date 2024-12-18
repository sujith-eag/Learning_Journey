`Resources` method on a `page` object Returns a collection of [[`page resources`]].
A page resource is a file within a page bundle.

`resources`  is for global resources

`PAGE.Resources`  is syntax
returns `resources.Resources`

## Methods 

### ByType

Returns a collection of page resources of the given [[`media type`]], or nill if none found.
Media types are `image, audio, text, video, application`

```go
{{ range .Resources.ByType "image" }}
	<img src="{{ .RelPermalink }}" width="{{ .Width }}" height="{{ .Height }}"  alt="">
{{ end }}
```
When working with global resources, instead of page resources, use the `resources.ByType` function.


### Get

Returns a page resource from the given path, or nill if none are found.
```go
{{ with .Resources.Get "images/a.jpg" }}
	<img src="{{ .RelPermalink }}" width=.......>
{{ end }}
```
`resources.Get` for global resources


### GetMatch

Returns the first page resources from the paths matching the given [`glob pattern`](https://github.com/gobwas/glob#example), or nill
```go
{{ with .Resources.GetMatch "images/*.jpg"}}
	<img src="{{ .RelPermalink }}"  width=......>
{{ end }}
```


### Match
Returns a collection of page resources from paths matching the given glob pattern or nill
```go
{{ range .Resources.Match "images/*.jpg"}}
	<img src="{{ .RelPermalink }}"  width=......>
{{ end }}
```
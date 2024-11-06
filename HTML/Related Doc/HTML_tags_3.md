## [Image and multimedia](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#image_and_multimedia)

HTML supports various multimedia resources such as images, audio, and video.

|Element|Description|
|---|---|
|[`<area>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/area)|Defines an area inside an image map that has predefined clickable areas. An _image map_ allows geometric areas on an image to be associated with [hyperlink](https://developer.mozilla.org/en-US/docs/Glossary/Hyperlink).|
|[`<audio>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)|Used to embed sound content in documents. It may contain one or more audio sources, represented using the `src` attribute or the source element: the browser will choose the most suitable one. It can also be the destination for streamed media, using a [`MediaStream`](https://developer.mozilla.org/en-US/docs/Web/API/MediaStream).|
|[`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)|Embeds an image into the document.|
|[`<map>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/map)|Used with [`<area>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/area) elements to define an image map (a clickable link area).|
|[`<track>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/track)|Used as a child of the media elements, audio and video. It lets you specify timed text tracks (or time-based data), for example to automatically handle subtitles. The tracks are formatted in [WebVTT format](https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API) (`.vtt` files)—Web Video Text Tracks.|
|[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)|Embeds a media player which supports video playback into the document. You can also use `<video>` for audio content, but the audio element may provide a more appropriate user experience.|
## [Embedded content](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#embedded_content)

In addition to regular multimedia content, HTML can include a variety of other content, even if it's not always easy to interact with.

|Element|Description|
|---|---|
|[`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)|Embeds external content at the specified point in the document. This content is provided by an external application or other source of interactive content such as a browser plug-in.|
|[`<fencedframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fencedframe)|Represents a nested browsing context, like `<iframe>` but with more native privacy features built in.|
|[`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)|Represents a nested browsing context, embedding another HTML page into the current one.|
|[`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)|Represents an external resource, which can be treated as an image, a nested browsing context, or a resource to be handled by a plugin.|
|[`<picture>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture)|Contains zero or more [`<source>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source) elements and one [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) element to offer alternative versions of an image for different display/device scenarios.|
|[`<portal>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/portal)|Enables the embedding of another HTML page into the current one to enable smoother navigation into new pages.|
|[`<source>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source)|Specifies multiple media resources for the picture, the audio element, or the video element. It is a void element, meaning that it has no content and does not have a closing tag. It is commonly used to offer the same media content in multiple file formats in order to provide compatibility with a broad range of browsers given their differing support for [image file formats](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types) and [media file formats](https://developer.mozilla.org/en-US/docs/Web/Media/Formats).|

## [SVG and MathML](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#svg_and_mathml)

You can embed [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) and [MathML](https://developer.mozilla.org/en-US/docs/Web/MathML) content directly into HTML documents, using the [`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg) and `[<math>](https://developer.mozilla.org/en-US/docs/Web/MathML/Element/math "<math>")` elements.

|Element|Description|
|---|---|
|[`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)|Container defining a new coordinate system and [viewport](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox). It is used as the outermost element of SVG documents, but it can also be used to embed an SVG fragment inside an SVG or HTML document.|
|`[<math>](https://developer.mozilla.org/en-US/docs/Web/MathML/Element/math "<math>")`|The top-level element in MathML. Every valid MathML instance must be wrapped in it. In addition, you must not nest a second `<math>` element in another, but you can have an arbitrary number of other child elements in it.|

## [Scripting](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#scripting)

To create dynamic content and Web applications, HTML supports the use of scripting languages, most prominently JavaScript. Certain elements support this capability.

|Element|Description|
|---|---|
|[`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas)|Container element to use with either the [canvas scripting API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) or the [WebGL API](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) to draw graphics and animations.|
|[`<noscript>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noscript)|Defines a section of HTML to be inserted if a script type on the page is unsupported or if scripting is currently turned off in the browser.|
|[`<script>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)|Used to embed executable code or data; this is typically used to embed or refer to JavaScript code. The `<script>` element can also be used with other languages, such as [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)'s GLSL shader programming language and [JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON).|

## [Demarcating edits](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#demarcating_edits)

These elements let you provide indications that specific parts of the text have been altered.

|Element|Description|
|---|---|
|[`<del>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/del)|Represents a range of text that has been deleted from a document. This can be used when rendering "track changes" or source code diff information, for example. The `<ins>` element can be used for the opposite purpose: to indicate text that has been added to the document.|
|[`<ins>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ins)|Represents a range of text that has been added to a document. You can use the `<del>` element to similarly represent a range of text that has been deleted from the document.|

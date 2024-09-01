## [Table content](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#table_content)

The elements here are used to create and handle tabular data.

|Element|Description|
|---|---|
|[`<caption>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/caption)|Specifies the caption (or title) of a table.|
|[`<col>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/col)|Defines one or more columns in a column group represented by its implicit or explicit parent [`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup) element. The `<col>` element is only valid as a child of a [`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup) element that has no [`span`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup#span) attribute defined.|
|[`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup)|Defines a group of columns within a table.|
|[`<table>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)|Represents tabular data—that is, information presented in a two-dimensional table comprised of rows and columns of cells containing data.|
|[`<tbody>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tbody)|Encapsulates a set of table rows ([`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) elements), indicating that they comprise the body of a table's (main) data.|
|[`<td>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td)|A child of the [`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) element, it defines a cell of a table that contains data.|
|[`<tfoot>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tfoot)|Encapsulates a set of table rows ([`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) elements), indicating that they comprise the foot of a table with information about the table's columns. This is usually a summary of the columns, e.g., a sum of the given numbers in a column.|
|[`<th>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th)|A child of the [`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) element, it defines a cell as the header of a group of table cells. The nature of this group can be explicitly defined by the [`scope`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th#scope) and [`headers`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th#headers) attributes.|
|[`<thead>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/thead)|Encapsulates a set of table rows ([`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) elements), indicating that they comprise the head of a table with information about the table's columns. This is usually in the form of column headers ([`<th>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th) elements).|
|[`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr)|Defines a row of cells in a table. The row's cells can then be established using a mix of [`<td>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td) (data cell) and [`<th>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th) (header cell) elements.|

## [Forms](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#forms)

HTML provides several elements that can be used together to create forms that the user can fill out and submit to the website or application. Further information about this available in the [HTML forms guide](https://developer.mozilla.org/en-US/docs/Learn/Forms).

|Element|Description|
|---|---|
|[`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)|An interactive element activated by a user with a mouse, keyboard, finger, voice command, or other assistive technology. Once activated, it performs an action, such as submitting a [form](https://developer.mozilla.org/en-US/docs/Learn/Forms) or opening a dialog.|
|[`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist)|Contains a set of [`<option>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option) elements that represent the permissible or recommended options available to choose from within other controls.|
|[`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset)|Used to group several controls as well as labels ([`<label>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)) within a web form.|
|[`<form>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)|Represents a document section containing interactive controls for submitting information.|
|[`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)|Used to create interactive controls for web-based forms to accept data from the user; a wide variety of types of input data and control widgets are available, depending on the device and user agent. The `<input>` element is one of the most powerful and complex in all of HTML due to the sheer number of combinations of input types and attributes.|
|[`<label>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)|Represents a caption for an item in a user interface.|
|[`<legend>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend)|Represents a caption for the content of its parent [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset).|
|[`<meter>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meter)|Represents either a scalar value within a known range or a fractional value.|
|[`<optgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/optgroup)|Creates a grouping of options within a [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element.|
|[`<option>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option)|Used to define an item contained in a select, an [`<optgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/optgroup), or a [`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist) element. As such, `<option>` can represent menu items in popups and other lists of items in an HTML document.|
|[`<output>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/output)|Container element into which a site or app can inject the results of a calculation or the outcome of a user action.|
|[`<progress>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress)|Displays an indicator showing the completion progress of a task, typically displayed as a progress bar.|
|[`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select)|Represents a control that provides a menu of options.|
|[`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea)|Represents a multi-line plain-text editing control, useful when you want to allow users to enter a sizeable amount of free-form text, for example, a comment on a review or feedback form.|


[[HTML tags 5]]
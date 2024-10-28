
The **`<input>`** HTML element is used to create interactive controls for web-based forms in order to accept data from the user;   
Wide variety of types of input data and control widgets are available, depending on the device and user agent. 

The `<input>` element is one of the most powerful and complex in all of HTML due to the sheer number of combinations of input types and attributes.
These are the interactive elements that allow users to interact with the site

#04sep24
### `<input>`           

```html
<label for="name">Name (4 to 8 characters):</label>

<input type="text" id="name" name="name" required minlength="4" maxlength="8" size="10" />
```

```html
<label for="textInput">Note the red caret:</label>
<input id="textInput" class="custom" size="32" />
```

```html
<!-- inaccessible -->
<p>Enter your name: <input id="name" type="text" size="30" /></p>

<!-- implicit label -->
<p>
  <label>Enter your name: <input id="name" type="text" size="30" /></label>
</p>

<!-- explicit label -->
<p>
  <label for="name">Enter your name: </label>
  <input id="name" type="text" size="30" />
</p>
```

The first example is inaccessible: no relationship exists between the prompt and the `<input>` element.

In addition to an accessible name, the label provides a larger 'hit' area for mouse and touch screen users to click on or touch. By pairing a `<label>` with an `<input>`, clicking on either one will focus the `<input>`. If you use plain text to "label" your input, this won't happen. Having the prompt part of the activation area for the input is helpful for people with motor control conditions.

As web developers, it's important that we never assume that people will know all the things that we know. The diversity of people using the web—and by extension your website—practically guarantees that some of your site's visitors will have some variation in thought processes and/or circumstances that leads them to interpret your forms very differently from you without clear and properly-presented labels.

### Labels

When including inputs, it is an accessibility requirement to add labels alongside. This is needed so those who use assistive technologies can tell what the input is for. Also, clicking or touching a label gives focus to the label's associated form control. This improves the accessibility and usability for sighted users, increases the area a user can click or touch to activate the form control. This is especially useful (and even needed) for radio buttons and checkboxes, which are tiny. For more information about labels in general see [Labels](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#labels).


 `<input>` needs an `id` attribute. 
 The `<label>` then needs a `for` attribute whose value is the same as the input's `id`.
```html
<label for="peas">Do you like peas?</label>
<input type="checkbox" name="peas" id="peas" />
```


# `<input> types`

How an `<input>` works varies considerably depending on the value of its `type` attribute, 
If this attribute is not specified, the default type adopted is `text`.

#### Button as `<input>`
`<input>` elements of type **`button`** are rendered as simple push buttons, which can be programmed to control custom functionality anywhere on a webpage as required when assigned an event handler function.
The newer [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) element is now the way to create buttons. You can include HTML in the label, even images also.

```html
<input type="button" value="Add to favorites">

same as 
<button>Add to favorite</button>
```

# [checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox)
A single value can be selected and deselected
```html
<fieldset>
  <legend>Choose your monster's features:</legend>

  <div>
    <input type="checkbox" id="scales" name="scales" checked />
    <label for="scales">Scales</label>
  </div>

  <div>
    <input type="checkbox" id="horns" name="horns" />
    <label for="horns">Horns</label>
  </div>
</fieldset>
```

value attribute represents the value given to the data submitted with checkbox's name.

# [radio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio)
Similar to checkbox, only one button in a given group can be selected at the same time.
Generally used in radio groups (a collection of radio buttons describing set of related options)
```html
<fieldset>
  <legend>Select a maintenance drone:</legend>

  <div>
    <input type="radio" id="huey" name="drone" value="huey" checked />
    <label for="huey">Huey</label>
  </div>

  <div>
    <input type="radio" id="dewey" name="drone" value="dewey" />
    <label for="dewey">Dewey</label>
  </div>
</fieldset>
```

The value attribute is a string containing the radio button's value.
The value is never shown to user, but used to identify which radio button in a group is selected.

A radio group is defined by giving each of radio buttons in the group the same name.


# [date](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date)
A control for entering a date (year, month, and day, with no time). Opens a date picker or numeric wheels for year, month, day when active in supporting browsers.
The value is normalized to the format `yyyy-mm-dd`.
```html
<label for="start">Start date:</label>

<input type="date" id="start" name="trip-start" value="2018-07-22" min="2018-01-01" max="2018-12-31" />
```

Value is used to set a default date.
The displayed date format will differ from the actual `value` — the displayed date is formatted _based on the locale of the user's browser_, but the parsed `value` is always formatted `yyyy-mm-dd`.

# [datetime-local](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/datetime-local)
A control for entering a date and time, with no time zone. Opens a date picker or numeric wheels for date- and time-components when active in supporting browsers.

# [email](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email)
A field for editing an email address. Looks like a `text` input, but has validation parameters and relevant keyboard in supporting browsers and devices with dynamic keyboards.

# [file](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file)
A control that lets the user select a file. Use the [`accept`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#accept) attribute to define the types of files that the control can select.

# [image](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/image)
A graphical `submit` button. Displays an image defined by the `src` attribute. The [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#alt) attribute displays if the image [`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#src) is missing.

# [number](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number)
A control for entering a number. Displays a spinner and adds default validation. Displays a numeric keypad in some devices with dynamic keypads.

# [password](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password)
A single-line text field whose value is obscured. Will alert user if site is not secure.

# [range](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/range)
A control for entering a number whose exact value is not important. Displays as a range widget defaulting to the middle value. Used in conjunction [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#min) and [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#max) to define the range of acceptable values.


# [submit](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit)
A button that submits the form.



# Attributes for the `<input>`

Each type has a different set of attributes it accepts

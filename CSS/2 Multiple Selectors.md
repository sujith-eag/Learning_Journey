Prev [[1 Selectors]]

## 1 Grouping selectors   #02sep24 

When we have two groups of elements that share some of their style declarations. Both `.read` and `.unread` selectors share declarations, but otherwise have several of their own unique declarations.

```css
.read {
		  color: white;
		  background-color: black;
		  /* several unique declarations */
		}

.unread {
		  color: white;
		  background-color: black;
		  /* several unique declarations */
		}
```

We can group two selectors together as a ***comma-separated list***:
```css
.read,
.unread {
		  color: white;
		  background-color: black;
		}

.read {
	  /* several unique declarations */
	   }

.unread {
	  /* several unique declarations */
		}
```

It makes it easier to edit either the `color` or `background-color` for both classes at once.


## 2 Chaining selectors

Selectors can be chained as a list when there is no separation between the selectors.
`.class.class`  or `.class#ID`

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

If we only want to apply a separate rule to the element that also has `header` as a second class. We could chain both the class selectors together in our CSS:
`.subsection.header` selects only the element that has both the `subsection` _and_ `header` classes. 
```css
.subsection.header {
					  color: red;
					}
```

This can also be used to chain a class and an ID:
```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">
    This is where a preview for a post might go.
  </p>
</div>
```
```css
.subsection.header {
					  color: red;
					}

.subsection#preview {
					  color: blue;
					}
```


You can’t chain more than one type selector since an element can’t be two different types at once. 
Chaining two type selectors like `div` and `p` would give us the selector `divp`, which wouldn’t work since the selector would try to find a literal `<divp>` element, which doesn’t exist.


## 3 Combinator
Combinators allow us to combine multiple selectors differently than either grouping or chaining them, as they show a relationship between the selectors. 

#### 3.1 Descendant combinator
**Descendant combinator**, is represented in CSS by a single space between selectors.

`child` class will only be selected if it is nested inside `ancestor`, regardless of how deep that nesting is. 

```html
<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"><!-- D --></div>
```
```css
.ancestor .contents {
  /* some declarations */
}
```

The first two elements with the `contents` class (B and C) would be selected, but that last element (D) wouldn’t be.

There’s really no limit to how many combinators you can add to a rule,
so `.one .two .three .four` would be totally valid. 

Element with class of `four` will be selected only if it is nested within `three two one`



Next    [[3 Declaration]]


Prev   [[1 Selectors]]                 

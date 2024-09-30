
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

#### 3.1 Descendant combinator `A  B`
Specifies that the element selected by `B` is a descendant of the element selected by `A`, but is not necessarily a direct child.

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


### Next-sibling combinator `A + B`
Specifies that the elements selected by both `A` and `B` have the same parent and that the element selected by `B` immediately follows the element selected by `A` horizontally.

### Subsequent-sibling combinator `A ~ B`
Specifies that the elements selected by both `A` and `B` share the same parent and that the element selected by `A` comes before—but not necessarily immediately before—the element selected by `B`.

### Child combinator `A > B`
Specifies that the element selected by `B` is the direct child of the element selected by `A`.


### Column combinator `A || B`
Specifies that the element selected by `B` is located within the table column specified by `A`. Elements which span multiple columns are considered to be a member of all of those columns.



# Cascade of CSS
#### Specificity
A CSS declaration that is more specific will take precedence over less specific ones. 
Inline styles, have the highest specificity compared to selectors.

1. ID selectors (most specific selector)
2. Class selectors
3. Type selectors

An ID selector will always beat any number of class selectors, 
a class selector will always beat any number of type selectors, 
and a type selector will always beat any number of less specific selectors.

```html
<!-- index.html -->
<div class="main">
  <div class="list" id="subsection">Blue text</div>
</div>
```
```css
#subsection {
  color: blue; }

.main .list {
  color: red; }
```
The color will be set as blue because the selector is an ID.



### Additional resources

- [An interactive Scrim](https://scrimba.com/scrim/co12d4cf99cf2776f19e84a9d) 
  Video covers how selectors can be chained and used along with rules to select specific items.

- [The CSS Cascade](https://2019.wattenberger.com/blog/css-cascade) 
  interactive read that in detail about other factors that affect what CSS rules actually end up being applied.
- [CSS Specificity Explained](https://www.youtube.com/watch?v=c0kfcP_nD9E) 
  video from Kevin Powell about specificity of selectors and priorities.
- [Interactive Scrim on the CSS Cascade.](https://v1.scrimba.com/scrim/c9gwmnAR)
- [CSS Specificity Calculator](https://specificity.keegan.st/) allows you to fill in your own selectors and have their specificity calculated and visualized.




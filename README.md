Ebay Listing Grid
=================

Ebay Listing Grid (ELG) is a CSS grid and a micro framework for designing responsive ebay listing templates, no javascript required. 

 * tiny (**only 8 css** `property: value;`)
 * only **two classes** (`g-row` and `g-col`)
 * fluid columns with **fixed gutters**
 * mobile first
 * allows columns ordering
 * supports all major modern browsers, serving one-column mobile layout to older browsers

**[Template example](http://tarqez.github.io/ebay-listing-grid)** &nbsp;|&nbsp; [Source](elg.css)

### Basic example
**_content with sidebar on the right_**

```html
<div class="g-row">
	<div class="g-col g-content"> ... </div>
	<div class="g-col g-sidebar"> ... </div>
</div>
```

```css
@media only screen and (min-width: 48em) {
	.g-content {width: 66.66%;}
	.g-sidebar {width: 33.33%;}
}
```

**Rows** are div elements with `g-row` class, while **cols** are div elements with `g-col` class.

In the example, we have a row with two cols that stack up in viewports up to 48em of width. Beyond 48em, cols line up with widths of 66.66% the first, 33.33% the second.

ELG is mobile first, therefore it provides 100%-width cols by default. We start with a one column layout and then with a multiple cols layout for larger viewport. We do this by setting widths in percentages for each media query breakpoint.


### Column ordering example
**_moving sidebar on the left_**

What if we want to keep the `.g-content` on top of the `.g-sidebar` for mobile layout, while having the `.g-sidebar` on the left for larger viewport? Column ordering comes in handy and we only need to add `left:` and `right:` properties to css.

```css
@media only screen and (min-width: 48em) {
	.g-content {
		width: 66.66%; 
		left: 33.33%;
	}
	.g-sidebar {
		width: 33.33%;
		right: 66.66%
	}
}
```

For viewports beyond 48em, we push `.g-content` from the left and `.g-sidebar` from the right. We need simple math to calculate the distances in percentages.

**[Ordering 3 cols example](http://tarqez.github.io/ebay-listing-grid/3cols_ordering.html)**

### Responsiveness in ebay listing

Templates are embedded in ebay pages, which don't allow full control on our layout behavior. For example on a large monitor of PCs and laptops, ebay fixes page viewport width to more than 1000px, resizing the browser window doesn't resize the viewport and a horizontal scrollbar bar appears. As a consequence, the template layout doesn't adapt responsevely to the new browser window.

But, when we use the ebay app on our phones, we will see the mobile layout. 

##### Mobile browsers and the javascript trick

Unfortunately the mobile version of the ebay website doesn't show the mobile template layout, because we don't have full control on ebay page, as said above. A trick that works in some mobile browsers is to add on top of css + HTML code the javascript

```javascript
<script>
	var vp = document.createElement("meta");
	vp.setAttribute("name", "viewport");
	vp.setAttribute("content", "width=device-width, initial-scale=1");
	document.getElementsByTagName("head")[0].appendChild(vp);
</script>
```

I have tested this on 

* Chrome mobile 49.0.x - works
* Android 4.4.4 stock browser - works
* Firefox mobile 45.0.x - doesn't works

### Cautions

1. Don't use ebay _quick listing tool_. Use the _form with more choices_ to avoid unwanted changes of template code (you don't need this caution with API and File Exchange)

2. Remove all unnecessary blanks and join all lines of template code in only one line

3. Use prefix for all your css _ID_ and _class_ names to avoid collitions with ebay names, like `.g-content` in the example above

---

### Thanks

ELG is a fork from [Dead Simple Grid](http://github.com/mourner/dead-simple-grid) an idea of Vladimir Agafonkin (creator of Leaflet)

Ebay Simple Grid
================

Ebay Simple Grid (ESG) is a CSS grid micro framework/concept for designing ebay listing responsive templates, no javascript required. 

 * tiny (just **8 css** `property: value;`), no dependencies
 * only **two classes** (`s-row` and `s-col`)
 * fluid columns with **fixed gutters**
 * mobile first, then you set column width in media queries for larger viewport
 * column ordering by `left` and `right` css properties
 * supports all major modern browsers, serving one-column mobile layout to older browsers

**[Template example](http://tarqez.github.com/ebay-simple-grid)** &nbsp;|&nbsp; [Source](css/esg.css)

### Basic example with sidebar on the right

```html
<div class="s-row">
	<div class="s-col content"> ... </div>
	<div class="s-col sidebar"> ... </div>
</div>
```

```css
@media only screen and (min-width: 48em) {
	.content {width: 66.66%;}
	.sidebar {width: 33.33%;}
}
```

**Rows** of the grid are block elements classed with `s-row`, while **cols** are block elements inside a row classed with `s-col`.

In the example, we have a row with two cols that stack up in viewports up to 48em of width. Beyond 48em, cols line up with widths of 66.66% the first, 33.33% the second.

ESG is mobile-first, therefore it provides 100%-width cols by default. We start with a one-column layout and then a multiple-cols layout for larger vieport. We do this by setting widths in simple percentages for each media query breakpoint.


### Basic example with sidebar on the left
##### (column ordering)

We want to move the sidebar on the left, swapping it with the content. We also want to keep the sidebar on the bottom of the stack in mobile layout. We only need to change the css, this way:

```css
@media only screen and (min-width: 48em) {
	.content {
		width: 66.66%; 
		left: 33.33%;
	}
	.sidebar {
		width: 33.33%;
		right: 66.66%
	}
}
```

For viewports larger or equal to 48em, we push `.content` from left by the width of the sidebar and, push `.sidebar` from right by the width of the content. We do this by css properties `left` and `right`.

### Explanation

#### Fixed Gutters and Box Sizing

Fixed gutter widths for columns are set as padding combined with `box-sizing: border-box` for `col` elements. This  means that your fluid design can finally have consistent whitespace, and you don't need to mess with weird percentages like `margin: 0 1.337%` and related column width calculations. Need a one-third column? Set its width to `33.33%` and padding to any value you like (ESG sets 1.5em by default).

#### Column Setup

All `col` elements are places inside clearfixed `row` elements and have `float: left; width: 100%` set by default. This means that you only need to change `width` to set up columns &mdash; no other properties required.

Need to turn 3 one-column elements into 3 columns? Set their width to `33.33%` and you're all set. Need to switch a 2-column block back to one-column mode? Set their width to `100%`. Forget about messing with classes or SASS/Less mixins and formulas.


#### Mobile First and Browser Support

The `box-sizing` property is widely supported, starting from IE 8. CSS3 Media queries are supported by all modern browsers, and a polyfill ([Respond.js][]) can be used to cover IE 8. Due to mobile first approach (we start from one column layout and build from there), older browsers which don't support both features (e.g. IE 6&ndash;7) receive a mobile layout which is perfectly accessible. So you have everyone covered nicely.

---

### Thanks

ESG is a fork from [Dead Simple Grid](http://github.com/mourner/dead-simple-grid) an idea of Vladimir Agafonkin (creator of Leaflet)

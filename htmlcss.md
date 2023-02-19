# HTML/CSS

## Box Model

The CSS box model refers to how HTML elements are modeled in browser engines and how the dimensions of those HTML elements are derived from CSS properties. It is a fundamental concept for the composition of HTML webpages.<sup>[[1]](#references)</sup>

![](https://www.simplilearn.com/ice9/free_resources_article_thumb/CSS-Box-Model.png)<sup>[[2]](#references)</sup>

Explanation of the different parts shown in above figure:

* Content - The content of the box, where text and images appear

* Padding - Clears an area around the content. The padding is transparent

* Border - A border that goes around the padding and content

* Margin - Clears an area outside the border. The margin is transparent

The box model allows us to add a border around elements, and to define space between elements.

Demonstration of the box model:

```css
div {
  width: 300px;
  border: 15px solid green;
  padding: 50px;
  margin: 20px;
}
```

When we set the width and height properties of an element with CSS, we just set the width and height of the content area. To calculate the full size of an element, we must also add padding, borders and margins.

The total width of an element should be calculated like this:

Total element width = width + left padding + right padding + left border + right border + left margin + right margin

The total height of an element should be calculated like this:

Total element height = height + top padding + bottom padding + top border + bottom border + top margin + bottom margin<sup>[[3]](#references)</sup>

## Inline versus Block Elements

Every HTML element has a default display value, depending on what type of element it is.

There are two display values: block and inline.

### Block-level Elements

A block-level element always starts on a new line, and the browsers automatically add some space (a margin) before and after the element.

A block-level element always takes up the full width available (stretches out to the left and right as far as it can).

Two commonly used block elements are: `<p>` and `<div>.`

The `<p>` element defines a paragraph in an HTML document.

The `<div>` element defines a division or a section in an HTML document.

 The `<p>` and `<div>` element is a block-level element.<sup>[[4]](#references)</sup>

### Inline Elements

An inline element does not start on a new line.

An inline element only takes up as much width as necessary.

An inline element cannot contain a block-level element!

#### Examples

`<a>` `<br>` `<b>` `<small>` `<span>` `<i>` etc.

## Positioning: Relative/Absolute<sup>[[5]](#references)</sup>

The position CSS property sets how an element is positioned in a document. The top, right, bottom, and left properties determine the final location of positioned elements.

### Relative

An element with position: relative; is positioned relative to its normal position.

Setting the top, right, bottom, and left properties of a relatively-positioned element will cause it to be adjusted away from its normal position. Other content will not be adjusted to fit into any gap left by the element.

```css
div {
  position: relative;
  left: 30px;
  border: 3px solid #73AD21;
}
```

### Absolute

position: absolute;

An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed).

However; if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling

```css
div {
  position: absolute;
  top: 80px;
  right: 0;
  width: 200px;
  height: 100px;
  border: 3px solid #73AD21;
}
```

### Static

position: static;

HTML elements are positioned static by default.

Static positioned elements are not affected by the top, bottom, left, and right properties.

An element with position: static; is not positioned in any special way; it is always positioned according to the normal flow of the page.

```css
div {
  position: static;
  border: 3px solid #73AD21;
}
```

## Common CSS structural classes<sup>[[6]](#references)</sup>

Structural pseudo classes allow access to the child elements present within the hierarchy of parent elements. We can select first-child element, last-child element, alternate elements present within the hierarchy of parent elements.

1. :first-child

:first-child represents the element that is prior to its siblings in a tree structure.

```css
<style>
table tr:first-child{
 background-color:gray;
}
</style>
```

2. :nth-child(n)

:nth-child(Expression) class applies CSS properties to those elements that appear at the position evaluated by the resultant of an expression. The expression evaluates to a value resulting in the position of the element in a tree structure.

For example, :nth-child(2n+1) pseudo class applies to the rows of table that appear at the position of the given expression.

tr:nth-child(2n+1) represents rows such as 1th, 3th, 5th, 7th.... for the n values of 0, 1, 2, 3.......

```css
<style>
table tr:nth-child(2n+1){
 background-color:gray;
}
</style>
```

It means the background-color of the 1th, 3th, 5th , etc, element is gray.

3. :last-child

:last-child pseudo class represents the element that is at the end of its siblings in a tree structure.

```css
<style>
ul li:last-child{
 background-color:lightblue;
}
</style>
```

It means the background-color of the last child of unordered list is lightblue.
4. :nth-last-child(n)

:nth-last-child(Expression) is the same as :nth-child(Expression) but the positioning of elements start from the end.

tr:nth-last-child(2n+1) represents last row, 3th last row, 5th last row, etc, element.

```css
<style>
table tr:nth-last-child(2n+1){
 background-color:lightblue;
}
</style>
```

:nth-last-child(1) and :nth-last-child(2) means the last, 2nd last elements in the list of siblings.

5. :only-child

:only-child represents the element that is a sole child of the parent element and there is no other sibling.

```css
<style>
div p:only-child{
 background-color:lightblue;
}
</style>
```

It means the first and last elements are same.
6. :first-of-type

There might be more than one type of siblings under a common parent. It selects the first element of the one type of sibling.

```css
<style>
dl dd:first-of-type{
 background-color:lightblue;
}
</style>
```

In the above example, there are two types of siblings i.e. dd and dt. And we choose the `<dl>` element to apply the CSS properties. It is the same as :nth-child(1).

7. :nth-of-type(n)

There may be more than one elements of the same type under a common parent. :nth-of-type(Expression) represents those elements of the same type at the position evaluated by the Expression.

```css
<style>
tr td:nth-of-type(2n+1){
 background-color:gray;
}
tr td:nth-of-type(2n){
 background-color:lightblue;
}
</style>
```

8. :last-of-type

:last-of-type represents the last element in the list of same type of siblings.

```css
<style>
dl dd:last-of-type{
 background-color:lightblue;
}
</style>
```

9. :nth-last-of-type(n)

It is the same as :nth-of-type(n) but it starts counting of position from the end instead of start.

```css
<style>
body > h2:nth-last-of-type(n+6){
 color:blue;
}
</style>
```

It means that the color of all `<h2>` elements is blue except the last five elements.

## Common CSS styling classes

Link pseudo-classes give web designers the ability to style various states of HTML links. The CSS pseudo-classes commonly used for styling hyperlinks are :link, :visited, :hover, :active, and :focus.
Here’s a description of each pseudo-class:

:link - Select unvisited links.

:visited - selects visited links

:hover – the state that happens when the user places their mouse pointer on top of a link.

:active – the state that happens when the user clicks on a link.

:focus – the state that occurs when the user focuses on the link. This state can be seen when you tab to a link, or after you click on a link.<sup>[[7]](#references)</sup>

## CSS Specificity<sup>[[8]](#references)</sup>

When more than one set of CSS rules apply to the same element, the browser will have to decide which specific set will be applied to the element. The rules the browser follows are collectively called Specificity.

Specificity Rules include:  

* CSS style applied by referencing external stylesheet has lowest precedence and is overridden by Internal and inline CSS.

* Internal CSS is overridden by inline CSS.

* Inline CSS has highest priority and overrides all other selectors.

Specificity Hierarchy :Every element selector has a position in the Hierarchy.

* Inline style: Inline style has highest priority.

* Identifiers(ID): ID have the second highest priority.

* Classes, pseudo-classes and attributes: Classes, pseudo-classes and attributes are come next.

* Elements and pseudo-elements: Elements and pseudo-elements have lowest priority.

When two or more selectors have equal specificity, the last(latest) one counts.

Universal selectors like body and inherited selectors have least specificity.

## CSS Responsive Queries

Web pages can be viewed using many different devices: desktops, tablets, and phones. Your web page should look good, and be easy to use, regardless of the device.

It is called responsive web design when you use CSS and HTML to resize, hide, shrink, enlarge, or move the content to make it look good on any screen.<sup>[[9]](#references)</sup>

### viewport

Pages optimized for a variety of devices must include a meta viewport tag in the head of the document. A meta viewport tag gives the browser instructions on how to control the page's dimensions and scaling.

To attempt to provide the best experience, mobile browsers render the page at a desktop screen width (usually about 980px, though this varies across devices), and then try to make the content look better by increasing font sizes and scaling the content to fit the screen. This means that font sizes may appear inconsistent to users, who may have to double-tap or pinch-to-zoom in order to see and interact with the content.<sup>[[10]](#references)</sup>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    …
    <meta name="viewport" content="width=device-width, initial-scale=1">
    …
  </head>
  …
```

### Media Query

Media query is a CSS technique introduced in CSS3.

It uses the @media rule to include a block of CSS properties only if a certain condition is true.

Media queries allow you to apply CSS styles depending on a device's general type (such as print vs. screen) or other characteristics such as screen resolution or browser viewport width. 

Media queries are used for the following:

* To conditionally apply styles with the CSS @media and @import at-rules.

* To target specific media for the `<style>`, `<link>`, `<source>`, and other HTML elements with the media= attribute.

* To test and monitor media states using the Window.matchMedia() and MediaQueryList.addListener() JavaScript methods.

Syntax

A media query is composed of an optional media type and any number of media feature expressions, which may optionally be combined in various ways using logical operators. Media queries are case-insensitive.

* Media types define the broad category of device for which the media query applies: all, print, screen. The type is optional (assumed to be all) except when using the not or only logical operators.

* Media features describe a specific characteristic of the user agent, output device, or environment: 

Targeting media types

Media types describe the general category of a given device. Although websites are commonly designed with screens in mind, you may want to create styles that target special devices such as printers or audio-based screen readers. For example, this CSS targets printers:

```css
@media print {
  /* … */
}
```

You can also target multiple devices. For instance, this @media rule uses two media queries to target both screen and print devices:

```css
@media screen, print {
  /* … */
}
```

See media type for a list of all media types. Because they describe devices in only very broad terms, just a few are available; to target more specific attributes, use media features instead.
Targeting media features

Media features describe the specific characteristics of a given user agent, output device, or environment. For instance, you can apply specific styles to widescreen monitors, computers that use mice, or to devices that are being used in low-light conditions. This example applies styles when the user's primary input mechanism (such as a mouse) can hover over elements:

```css
@media (hover: hover) {
  /* … */
}
```

Many media features are range features, which means they can be prefixed with "min-" or "max-" to express "minimum condition" or "maximum condition" constraints. For example, this CSS will apply styles only if your browser's viewport width is equal to or narrower than 1250px:

```css
@media (max-width: 1250px) {
  /* … */
}
```

If you create a media feature query without specifying a value, the nested styles will be used as long as the feature's value is not zero (or none, in Level 4). For example, this CSS will apply to any device with a color screen:

```css
@media (color) {
  /* … */
}
```

If a feature doesn't apply to the device on which the browser is running, expressions involving that media feature are always false.<sup>[[11]](#references)</sup>

## Flex box

CSS Flexible Box Layout, commonly known as Flexbox, is a CSS 3 web layout model. It is in the W3C's candidate recommendation stage. The flex layout allows responsive elements within a container to be automatically arranged depending on viewport size.<sup>[[12]](#references)</sup>

The main idea behind the flex layout is to give the container the ability to alter its items’ width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space or shrinks them to prevent overflow.

Most importantly, the flexbox layout is direction-agnostic as opposed to the regular layouts (block which is vertically-based and inline which is horizontally-based). While those work well for pages, they lack flexibility (no pun intended) to support large or complex applications (especially when it comes to orientation changing, resizing, stretching, shrinking, etc.).<sup>[[13]](#references)</sup>

### Flexbox properties<sup>[[14]](#references)</sup>

#### Properties for the Parent(flex container)

##### display

This defines a flex container; inline or block depending on the given value. It enables a flex context for all its direct children.display
This defines a flex container; inline or block depending on the given value. It enables a flex context for all its direct children.

#### flex-direction

This establishes the main-axis, thus defining the direction flex items are placed in the flex container. Flexbox is (aside from optional wrapping) a single-direction layout concept. Think of flex items as primarily laying out either in horizontal rows or vertical columns.

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

#### flex-wrap

By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property.

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

* nowrap (default): all flex items will be on one line
* wrap: flex items will wrap onto multiple lines, from top to bottom.
* wrap-reverse: flex items will wrap onto multiple lines from bottom to top.

#### flex-flow

This is a shorthand for the flex-direction and flex-wrap properties, which together define the flex container’s main and cross axes. The default value is row nowrap.

```css
.container {
  flex-flow: column wrap;
}
```

#### justify-content

This defines the alignment along the main axis. It helps distribute extra free space leftover when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size. It also exerts some control over the alignment of items when they overflow the line.

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```

* flex-start (default): items are packed toward the start of the flex-direction.
* flex-end: items are packed toward the end of the flex-direction.
* start: items are packed toward the start of the writing-mode direction.
* end: items are packed toward the end of the writing-mode direction.
* left: items are packed toward left edge of the container, unless that doesn’t make sense with the flex-direction, then it behaves like start.
* right: items are packed toward right edge of the container, unless that doesn’t make sense with the flex-direction, then it behaves like end.
* center: items are centered along the line
* space-between: items are evenly distributed in the line; first item is on the start line, last item on the end line
* space-around: items are evenly distributed in the line with equal space around them. Note that visually the spaces aren’t equal, since all the items have equal space on both sides. The first item will have one unit of space against the container edge, but two units of space between the next item because that next item has its own spacing that applies.
* space-evenly: items are distributed so that the spacing between any two items (and the space to the edges) is equal.

#### align-items

This defines the default behavior for how flex items are laid out along the cross axis on the current line. Think of it as the justify-content version for the cross-axis (perpendicular to the main-axis).

```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}
```

* stretch (default): stretch to fill the container (still respect min-width/max-width)
* flex-start / start / self-start: items are placed at the start of the cross axis. The difference between these is subtle, and is about respecting the flex-direction rules or the writing-mode rules.
* flex-end / end / self-end: items are placed at the end of the cross axis. The difference again is subtle and is about respecting flex-direction rules vs. writing-mode rules.
* center: items are centered in the cross-axis
* baseline: items are aligned such as their baselines align

#### align-content

This aligns a flex container’s lines within when there is extra space in the cross-axis, similar to how justify-content aligns individual items within the main-axis.

This property only takes effect on multi-line flexible containers, where flex-wrap is set to either wrap or wrap-reverse). A single-line flexible container (i.e. where flex-wrap is set to its default value, no-wrap) will not reflect align-content.

.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}

* normal (default): items are packed in their default position as if no value was set.
* flex-start / start: items packed to the start of the container. The (more supported) flex-start honors the flex-direction while start honors the writing-mode direction.
* flex-end / end: items packed to the end of the container. The (more support) flex-end honors the flex-direction while end honors the writing-mode direction.
* center: items centered in the container
* space-between: items evenly distributed; the first line is at the start of the container while the last one is at the end
* space-around: items evenly distributed with equal space around each line
* space-evenly: items are evenly distributed with equal space around them
* stretch: lines stretch to take up the remaining space

#### gap, row-gap, column-gap

The gap property explicitly controls the space between flex items. It applies that spacing only between items not on the outer edges.

```css
.container {
  display: flex;
  ...
  gap: 10px;
  gap: 10px 20px; /* row-gap column gap */
  row-gap: 10px;
  column-gap: 20px;
}
```

The behavior could be thought of as a minimum gutter, as if the gutter is bigger somehow (because of something like justify-content: space-between;) then the gap will only take effect if that space would end up smaller.

### Properties for the Children (flex items)

#### Order

By default, flex items are laid out in the source order. However, the order property controls the order in which they appear in the flex container.

```css
.item {
  order: 5; /* default is 0 */
}
```

Items with the same order revert to source order

#### flex-grow

This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

If all items have flex-grow set to 1, the remaining space in the container will be distributed equally to all children. If one of the children has a value of 2, that child would take up twice as much of the space either one of the others (or it will try, at least).

```css
.item {
  flex-grow: 4; /* default 0 */
}
```

Negative numbers are invalid.

#### flex-shrink

This defines the ability for a flex item to shrink if necessary.

```css
.item {
  flex-shrink: 3; /* default 1 */
}
```

Negative numbers are invalid.

## Grid

CSS Grid Layout (aka “Grid” or “CSS Grid”), is a two-dimensional grid-based layout system that, compared to any web layout system of the past, completely changes the way we design user interfaces.

### Important CSS Grid terminology<sup>[[15]](#references)</sup>

#### Grid Container

The element on which display: grid is applied. It’s the direct parent of all the grid items. In this example container is the grid container.

#### Grid Item

The children (i.e. direct descendants) of the grid container. Here the item elements are grid items, but sub-item isn’t.

#### Grid Line

The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.

#### Grid Cell

The space between two adjacent row and two adjacent column grid lines. It’s a single “unit” of the grid. Here’s the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.

#### Grid Track

The space between two adjacent grid lines. You can think of them as the columns or rows of the grid. Here’s the grid track between the second and third-row grid lines.

#### Grid Area

The total space surrounded by four grid lines. A grid area may be composed of any number of grid cells. Here’s the grid area between row grid lines 1 and 3, and column grid lines 1 and 3.

### Properties for the Parent (Grid Container)

#### display

Defines the element as a grid container and establishes a new grid formatting context for its contents.

Values:

* grid – generates a block-level grid
* inline-grid – generates an inline-level grid

```css
.container {
  display: grid | inline-grid;
}
```

#### grid-template-columns, grid-template-rows

Defines the columns and rows of the grid with a space-separated list of values. The values represent the track size, and the space between them represents the grid line.

Values:

* `<track-size>` – can be a length, a percentage, or a fraction of the free space in the grid using the fr unit (more on this unit over at DigitalOcean)
* `<line-name>` – an arbitrary name of your choosing

```css
.container {
  grid-template-columns: ...  ...;
  /* e.g. 
      1fr 1fr
      minmax(10px, 1fr) 3fr
      repeat(5, 1fr)
      50px auto 100px 1fr
  */
  grid-template-rows: ... ...;
  /* e.g. 
      min-content 1fr min-content
      100px 1fr max-content
  */
}
```

Grid lines are automatically assigned positive numbers from these assignments (-1 being an alternate for the very last row).

#### grid-template-areas

Defines a grid template by referencing the names of the grid areas which are specified with the grid-area property. Repeating the name of a grid area causes the content to span those cells. A period signifies an empty cell. The syntax itself provides a visualization of the structure of the grid.

Values:

* <grid-area-name> – the name of a grid area specified with grid-area
* . – a period signifies an empty grid cell
* none – no grid areas are defined

```css
.container {
  grid-template-areas: 
    "<grid-area-name> | . | none | ..."
    "...";
}
```

#### grid-template

A shorthand for setting grid-template-rows, grid-template-columns, and grid-template-areas in a single declaration.

Values:

* none – sets all three properties to their initial values
* `<grid-template-rows>` / `<grid-template-columns>` – sets grid-template-columns and grid-template-rows to the specified values, respectively, and sets grid-template-areas to none

```css
.container {
  grid-template: none | <grid-template-rows> / <grid-template-columns>;
}
```

#### column-gap, row-gap, grid-column-gap, grid-row-gap

Specifies the size of the grid lines. You can think of it like setting the width of the gutters between the columns/rows.

Values:

* `<line-size>` – a length value

```css
.container {
  /* standard */
  column-gap: `<line-size>;
  row-gap: <line-size>;

  /* old */
  grid-column-gap: <line-size>;
  grid-row-gap: <line-size>;
}
```

#### justify-items

Aligns grid items along the inline (row) axis (as opposed to align-items which aligns along the block (column) axis). This value applies to all grid items inside the container.

Values:

* start – aligns items to be flush with the start edge of their cell
* end – aligns items to be flush with the end edge of their cell
* center – aligns items in the center of their cell
* stretch – fills the whole width of the cell (this is the default)

```css
.container {
  justify-items: start | end | center | stretch;
}
```

## Common header meta tags<sup>[[16]](#references)</sup>

The `<meta>` tag defines metadata about an HTML document. Metadata is data (information) about data.

`<meta>` tags always go inside the `<head>` element, and are typically used to specify character set, page description, keywords, author of the document, and viewport settings.

Metadata will not be displayed on the page, but is machine parsable.

Metadata is used by browsers (how to display content or reload page), search engines (keywords), and other web services.

```html
Define keywords for search engines:
<meta name="keywords" content="HTML, CSS, JavaScript">

Define a description of your web page:
<meta name="description" content="Free Web tutorials for HTML and CSS">

Define the author of a page:
<meta name="author" content="John Doe">

Refresh document every 30 seconds:
<meta http-equiv="refresh" content="30">

Setting the viewport to make your website look good on all devices:
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## References

1. https://en.wikipedia.org/wiki/CSS_box_model

2. https://www.simplilearn.com/ice9/free_resources_article_thumb/CSS-Box-Model.png

3. https://www.w3schools.com/css/css_boxmodel.asp

4. https://www.w3schools.com/html/html_blocks.asp

5. https://www.w3schools.com/css/css_positioning.asp

6. https://www.web4college.com/css/web4-css-structural-classes.php

7. https://www.webfx.com/blog/web-design/link-pseudo-classes/

8. https://www.geeksforgeeks.org/css-specificity/

9. https://www.w3schools.com/css/css_rwd_intro.asp

10. https://web.dev/responsive-web-design-basics/

11. https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#syntax

12. https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiYg7mpguX7AhWd-3MBHbZJAp0QmhN6BAhiEAI&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FCSS_Flexible_Box_Layout&usg=AOvVaw0kwGrHrbEalsliElVXJcuN

13. https://css-tricks.com/snippets/css/a-guide-to-flexbox/

14. https://css-tricks.com/snippets/css/a-guide-to-flexbox/

15. https://css-tricks.com/snippets/css/complete-guide-grid/

16. https://www.w3schools.com/tags/tag_meta.asp
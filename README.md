# css_basics

There is some useful info here:
https://css-tricks.com/

### Selectors and properties

https://css-tricks.com/almanac/

### Colors

This website is very nice:
https://paletton.com/

You pick one color and it gives the complement colors to use together.

### Selectors

**Cascading and Specificity**

`Cascading` style sheets at the most basic level it indicates that order of CSS rules mater.

There is also something called `specificity`. The css takes the most specific style to render.

A list of way to apply selectors:

```
.class
#id
*
element
element1, element2  // apply to both element1 and element2
element1 element2  // apply all element2's which are inside of an element1
element1 > element2 // apply to element2 which has element1 as direct parent
element1 + element2  // apply to element2 whcih is exactly after element1 (not inside)
:hover
:last-child
:first-child
!important (not recomended, override cascading)

```

Example for `element > element`
Apply the style to only direct parent. Assuming you have the selecor like this:

```css
h2 > p {
  color: red;
}
```

This will work with

```html
<h2>
  <p>Hello</p>
</h2>
```

but won't work for

```html
<h2>
  <div>
    <p>Hello</p>
  </div>
</h2>
```

This will work for above. This means all p's inside of h2

```css
h2 p {
  color: red;
}
```

What selectors win out in the cascade depends on:

- Specificity: check something called [specificity calculator](https://specificity.keegan.st)
- Importance: the #import mark
- Source Order: apprently the order matters. The later lines win when there is conflict.

### Font

An easy way to have fonts available. Use [Google Fonts](https://fonts.google.com/)
Select the one you like and embed it in your html file like this:

```html
<link
  href="https://fonts.googleapis.com/css2?family=Noto+Sans&display=swap"
  rel="stylesheet"
/>
```

and in your css file for font family like this:

```css
font-family: 'Noto Sans', sans-serif;
```

### Image

Basic image size change in html.

```html
<img src="{your source link}" width="200px" height="200px" />
```

Float the image so the text can wrap around it

```css
img {
  float: right;
}
```

When you use the "float" property, you almost always for the next element you need to use the "clear" property to let the next element show in underneath it. For example, the footer element can be made sure to appear at the bottom.

```css
footer {
  clear: both;
  text-align: center;
}
```

### Show the items in the place we want them to be

This is a very challenging problem for css!!

Let's look at some solutions.

#### flexbox

One of the most popular ways to tackle this is. Make your contents responsive.

The best website to learn flex: [flexbox froggy](https://flexboxfroggy.com)!!

Check this website to find the layout you want!
https://css-tricks.com/snippets/css/a-guide-to-flexbox/

```scss
.things-in-flexbox {
  display: flex;  //activate flexbox
  flex-wrap: wrap // this will wrap your things in flexbox
  justify-content: center // make the contents in the center
}
```

Useful flexbox properties:

- justify-content:

  - flex-start (default)
  - center
  - flex-end
  - space-around
  - space-between

- align-items:

  - center
  - flex-end

- flex-direction:

  - row (default)
  - row-reverse
  - \*column
  - column-reverse

- order:

  Sometimes reversing the row or column order of a container is not enough. In these cases, we can apply the order property to individual items. By default, items have a value of 0, but we can use this property to also set it to a positive or negative integer value (-2, -1, 0, 1, 2).

- align-self (apply individual items in the flexbox):

  - accept the same values as align-items

- flex-wrap

  - nowrap: every item fit into a single line
  - wrap: itms wrap around to additional lines
  - wrap-reverse: wrap around to additional lines in reverse

- flex-flow (just a shorthand for flex-direction and flex-wrap)
  Here, these two are the same:

  ```css
  .container {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
  }
  ```

  ```css
  .container {
    display: flex;
    flex-flow: column wrap;
  }
  ```

- align-content (minimize the lines for items that are aligned):
  - flex-start
  - flex-end

\*Notes:

- when flex direction is column, `justify-content` changes to vertical and `align-items` changes to horizontal.

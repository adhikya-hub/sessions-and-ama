# AMA

## What is the use of the `<head>` tag?
The `<head>` tag stores metadata about the webpage like title, links to CSS files, meta tags, favicon, and scripts. It is not displayed on the webpage.

## What is the `flex` attribute in flexbox?
`flex` is a shorthand property used on flex items to control:
- `flex-grow`
- `flex-shrink`
- `flex-basis`

Example:
```css
flex: 1;
````
is shorthand for:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0;
````

## What is `transform` in CSS?

`transform` is used to change the shape, position, rotation, size, or skew of an element.

Example:

```css
transform: rotate(45deg);
transform: scale(1.2);
transform: translateX(50px);
```

## Difference between `<b>` and `<strong>`

* `<b>` → Makes text bold only.
* `<strong>` → Makes text bold and gives semantic importance.

Example:

```html
<b>Bold</b>
<strong>Important text</strong>
```

## What do `<br>` and `<hr>` tags do?

* `<br>` → Adds a line break.
* `<hr>` → Creates a horizontal line.

Example:

```html
Hello<br>World
<hr>
```

## Difference between `<em>` and `<i>`

* `<i>` → Italic text only.
* `<em>` → Italic text with semantic emphasis.

Example:

```html
<i>Hello</i>
<em>Important</em>
```

## Can we pass values in `rem` in media queries?

Yes.

Example:

```css
@media (min-width: 40rem) {
    body {
        background: red;
    }
}
```

## How can we make an image sticky?

Use `position: sticky`.

Example:

```css
img {
    position: sticky;
    top: 0;
}
```

## What is `order` in flexbox?

`order` changes the visual order of flex items.

Example:

```css
.item {
    order: 2;
}
```

Lower order values appear first.

## What are different border styles in CSS?

Common border styles:

* solid
* dashed
* dotted
* double
* groove
* ridge
* inset
* outset
* none

Example:

```css
border: 2px dashed red;
```

## What are form attributes?

Form attributes provide additional behavior to forms.

Common attributes:

* `action`
* `method`
* `target`
* `autocomplete`
* `novalidate`

Example:

```html
<form action="/submit" method="POST">
```

## How do you create 3 columns in grid?

Example:

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}
```

## What are semantic tags?

Semantic tags clearly describe the meaning of content.

Examples:

* `<header>`
* `<nav>`
* `<main>`
* `<section>`
* `<article>`
* `<footer>`

## What is the default value of `position`?

The default value is:

```css
position: static;
```

## How can we make a block element inline?

Use:

```css
display: inline;
```

Example:

```css
div {
    display: inline;
}
```

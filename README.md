# ![sass5-logo](/images/sass5-s-30.png) Sass

### Todos

- [ ] Change layout to standardize with HTML and CSS README files
- [ ] Convert all code to code blocks
- [ ] Create Toggle for all Benefits

<br>

<b>Benefits for continuing to use SASS as many preprocessor features get integrated
into the native CSS spec:</b>

<details>
<summary><b>Sass Module System</b></summary>

- Separating `.sass` files into partials `_name.sass` to keep all elements
    separated and sorted
  - Use `@use` to include partials and `_index.sass` in `main.sass`
  - Using `@forward` in `_index.sass` files to consolidate partials for `@use`.

- Functions:
  - Compute and return values
  - There are included functions with SASS, like
    `rgba(#color, transparency-level)` for calculating rgba
    transparency color values from hex values or `mix(color1, color2, n%)` for
    mixing two colors with `n%` saturation of `color2`

</details>

<br>

- Mixin:
  - none of the `@mixin` functionality is present in native CSS
  - no plans for integration

- Loops:
  - allows the ability to create custom flexbox grids and make them responsive
    with `@media` queries
  - `@for $i from 0 through 9` to iterate over `i` elements
  - no plans for integration

- `@if` `@else if` `@else` statements:
  - Example: use to set line spacing depending on font size
  - can be used for custom messaging for debugging
  - no plans for integration

- Nesting:
  - being able to use multiple selectors, `&-name`, is not supported in CSS yet.
  - planed to be integrated into native CSS spec.

- Indentations use:
  - using `.sass` file extension we can use indentation instead
    of curly brackets and semicolons!<br>
    `Pythonites and YAMLites rejoice!`

<br>
<br>

## Table of Contents

- <b>[SCSS vs SASS](#scss-vs-sass)</b>
- <b>[Generated Files using Live Sass Compiler extension](#generated-files-using-live-sass-compiler-extension)</b>
- <b>[SCSS Variables](#scss-variables)</b>
- <b>[Maps](#maps)</b>
- <b>[Nesting](#nesting)</b>
- <b>[Separating files using Sass Module System](#separating-files-using-sass-module-system)</b>
- <b>[Sass File Structure](#sass-file-structure)</b>
- <b>[Functions](#functions)</b>
- <b>[Mixin](#mixin)</b>
- <b>[Extend](#extend)</b>
- <b>[Math Operations](#math-operations)</b>
<br>
<br>
<br>

## SCSS vs SASS

- SCSS - Sassy CSS, SCSS Syntax: uses curly braces & semicolons same as CSS
- original Sass: Indented Syntax: uses indentation, .sass extension

> I will be using `*.sass` file extension as it allows use of indentation rather
> then curly braces, which is more Pythonic (and I hate curly braces)

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Generated Files using Live Sass Compiler extension

- creates the .css file and .css.map file:
  - do not edit the generated .css as it gets overwritten every time its compiled.
  - .css.map file:
    - `"sources":["main.scss","main.css"]` points to original source files that
      were used to generate the CSS. These paths are relative to the location of
      the source map file.
    - `"file":"main.css"` name of CSS file the source map corresponds to.
<br>

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## SCSS Variables

```scss
$variable-one: #000000
$variable-two: pink

body
  background: $variable-one
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Maps

Using a variable, assign key-value pairs in parentheses:

Example:

```scss
$font-weights:
  "regular": 400,
  "medium": 500,
  "bold": 700,

body
  font-weight: map-get(#font-weights, regular)
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>
<br>

## Nesting

- styling an html element that is inside a main html element, making the style
  apply only within that element, not globally.

Example:

```scss
.main
  width: 80%  
  margin: 0 auto  

  /* "&" = the parent (ie .main).
  Use interpolation with "#" to wrap "&" to get
  everything before it */
  #{&}-paragraph
    font-weight: map-get(#font-weights, bold)

    &:hover
      color: $variable-two
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Separating files using Sass Module System

Use `@use` and `@forward`

> Do NOT use `@import 'file-name';`. It is being deprecated.

- a partial SCSS file is indicated by name starting with `underscore`, so
  compilers ignore them.
- separate resets and variables into their corresponding partials files.

- use `@use 'file-name';` to include partials files.<br>
  <i>Note:</i> does NOT need file extension.
  - it prevents collisions by requiring specified namespace:<br>
  `file-name.$style-name` rather than just `$style-name`

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Sass File Structure

> This is my Sass file structure. There are many like it, but this one is mine.

📂sass<br>
 ┣ 📂components<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_cards.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_mixins.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_resets.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass-5.png)_variables.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass-5.png)_functions.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass-5.png)_index.sass<br>
 ┣ 📂theme<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_colors.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_fonts.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass-5.png)_spacing.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass-5.png)_index.sass<br>
 ┣ ![sass5-logo](/images/css3.png)main.css `-generated with` [Live Sass Compiler](https://github.com/ilya0x/My-Favorite-Visual-Studio-Code-Extensions#-live-sass-compiler)<br>
 ┣ ![sass5-logo](/images/css3.png)main.css.map `-generated with` [Live Sass Compiler](https://github.com/ilya0x/My-Favorite-Visual-Studio-Code-Extensions#-live-sass-compiler)<br>
 ┗ ![sass5-logo](/images/sass-5.png)main.sass<br>

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Functions

- Compute and return values

Example:

```scss
@function weight(&weight-name)
  @return map-get($font-weights, &weight-name)
```

- using function and passing in the `font-weight` choice (from `_variables.scss`
  partial file):

```scss
font-weight: weight(bold)
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Mixin

- Define Styles
- use `@mixin` to create snippets of css that can be "mixed into" any style

Example:

`@mixin flexCenter {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`display: flex;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`align-items: center;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`justify-content: center;`<br>
`}`<br>

`.main {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`@include flexCenter;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`//! "mixes in" flex related snippet of style`<br>

&nbsp;&nbsp;&nbsp;&nbsp;`width: 80%;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`margin: 0 auto;`<br>
`}`<br>

Example: choosing between a light and dark theme

`@mixin theme($light-theme: true) {` (assign Boolean value to variable)<br>
&nbsp;&nbsp;&nbsp;&nbsp;`@if $light-theme {` (if light-theme is true)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(light theme styles:)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`background:
lighten($variable-one, $amount: 100%);`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`color: darken($variable-two,
$amount: 100%);`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>
`}`<br>

`.light {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`@include theme($light-theme: true);`<br>
`}`<br>

Example: Media Query - change layout depending on window size

added `$mobile: 800px;` to `_variables.scss`

`@mixin mobile {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`@media (max-width: $mobile) {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`@content;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>
`}`<br>

`.main {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`...`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`@include mobile{`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`flex-direction: column;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>
`}`
<br>

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Extend

- extend a class with `@extend` to have its properties applied to the parent class

Example:

`.main {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`...`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`#{&}-paragraph1;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`font-weight: weight(bold);`<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`&:hover {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`color: pink;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>

&nbsp;&nbsp;&nbsp;&nbsp;`#{&}-paragraph2;`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`@extend .main-paragraph1;`
extends all styles from -paragraph1<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`&:hover {`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`color:
blue;` supersedes the extended style<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`<br>
&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br>

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

## Math Operations

- does NOT need `calc()` function
- has to be same type (%, px, etc.)
- SCSS passes through only the result
- if using `calc()` function, SCSS will pass through the whole thing including operation

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

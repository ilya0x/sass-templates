# ![sass5-logo](/images/sass5-s-30.png) Sass

<br>

<img src="images/oprah.jpg" height=150>
<br>

Benefits for continuing to use SASS as many preprocessor features get integrated
into the native CSS spec:

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

<details>
<summary><b>Mixin</b></summary>

- none of the `@mixin` functionality is present in native CSS
- no plans for integration

</details>

<details>
<summary><b>Loops</b></summary>

- allows the ability to create custom flexbox grids and make them responsive
  with `@media` queries
- `@for $i from 0 through 9` to iterate over `i` elements
- no plans for integration

</details>

<details>
<summary><b><code>@if</code> <code>@else if</code> <code>@else</code> statements</b></summary>

- Example: use to set line spacing depending on font size
- can be used for custom messaging for debugging
- no plans for integration

</details>

<details>
<summary><b>Nesting</b></summary>

- being able to use multiple selectors, `&-name`, is not supported in CSS yet.
- planed to be integrated into native CSS spec.

</details>

<details>
<summary><b>Indentations use</b></summary>

- using `.sass` file extension we can use indentation instead
    of curly brackets and semicolons!<br>

> Pythonites and YAMLites rejoice!

</details>

<br>

## <img src="./images/template-20.png" alt="template"> Templates

<b>[FLEXBOX Layout](/flexbox-photo-gallery-sass/)</b> - Photo Gallery using
FLEXBOX Layout

<br>

## <img src="./images/vscode-20.png" alt="Flask"> Visual Studio Code Extensions

<b>[Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass)
</b> - Compile Sass or Scss to CSS at realtime.

<b>[Sass (.sass only)](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)
</b> - Indented Sass syntax Highlighting, Autocomplete & Formatter

<b>[SCSS Formatter](https://marketplace.visualstudio.com/items?itemName=sibiraj-s.vscode-scss-formatter)
</b> - Formats .scss files

<br>

## 📝Notes

> These notes are updated on regular basis

<br>

### Table of Contents

- <b>[SCSS vs SASS](#scss-vs-sass)</b>
- <b>[Generated Files using Live Sass Compiler extension](#generated-files-using-live-sass-compiler-extension)</b>
- <b>[Sass Variables](#sass-variables)</b>
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

### .SCSS vs .SASS

- SCSS - Sassy CSS, SCSS Syntax: uses curly braces & semicolons same as CSS
- original Sass: Indented Syntax: uses indentation, .sass extension

> I will be using `*.sass` file extension as it allows use of indentation rather
> then curly braces, which is more Pythonic (and I hate curly braces)

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

### Generated Files using Live Sass Compiler extension

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

### Sass Variables

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

### Maps

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

### Nesting

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

### Separating files using Sass Module System

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

### Sass File Structure

> This is my Sass file structure. There are many like it, but this one is mine.

📂sass<br>
 ┣ 📂components<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_cards.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_mixins.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_resets.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass5-s-15.png)_variables.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass5-s-15.png)_functions.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass5-s-15.png)_index.sass<br>
 ┣ 📂theme<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_colors.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_fonts.sass<br>
 ┃ ┗ ![sass5-logo](/images/sass5-s-15.png)_spacing.sass<br>
 ┃ ┣ ![sass5-logo](/images/sass5-s-15.png)_index.sass<br>
 ┣ ![sass5-logo](/images/css3-15.png)main.css <i>(generated with [Live Sass Compiler](https://github.com/ilya0x/My-Favorite-Visual-Studio-Code-Extensions#-live-sass-compiler))</i><br>
 ┣ ![sass5-logo](/images/css3-15.png)main.css.map <i>(generated with [Live Sass Compiler](https://github.com/ilya0x/My-Favorite-Visual-Studio-Code-Extensions#-live-sass-compiler))</i><br>
 ┗ ![sass5-logo](/images/sass5-s-15.png)main.sass<br>

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

### Functions

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

### Mixin

- Define Styles
- use `@mixin` to create snippets of css that can be "mixed into" any style

Example:

``` scss
@mixin flexCenter
  display: flex
  align-items: center
  justify-content: center

.main
  @include flexCenter
  // `mixes in` flex related snippet of style

  width: 80%
  margin: 0 auto
```

<br>

Example: choosing between a light and dark theme:

```scss
@mixin theme($light-theme: true)
// assign Boolean value to variable
  @if $light-theme
  // if light-theme is true
    // light theme styles:
    background: lighten($variable-one, $amount: 100%)
    color: darken($variable-two, $amount: 100%)

.light
  @include theme($light-theme: true)
```

Example: Media Query - change layout depending on window size

added `$mobile: 800px;` to `_variables.scss`

``` scss
@mixin mobile
  @media (max-width: $mobile)
    @content

.main
  ...
  @include mobile
    flex-direction: column
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

### Extend

- extend a class with `@extend` to have its properties applied to the parent class

Example:

``` scss
.main
  ...
  #{&}-paragraph1
    font-weight: weight(bold)

    :hover
      color: pink

  #{&}-paragraph2
    @extend .main-paragraph1 
    // extends all styles from -paragraph1

    &:hover
      color: blue 
      // supersedes the extended style
```

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

### Math Operations

- does NOT need `calc()` function
- has to be same type (%, px, etc.)
- SCSS passes through only the result
- if using `calc()` function, SCSS will pass through the whole thing including operation

<br>
<br>

[Back to Table of Contents](#table-of-contents)
<br>
<br>

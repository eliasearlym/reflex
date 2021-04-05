<p><img style="" src="./img/reflex.banner.png"></p>

# Reflex<!-- omit in toc -->

Reflex is an advanced frontend framework based on the CSS flexbox layout module. Build and style complex UIs, layouts, grids and objects with ease. Apply flexbox properties to elements quickly with an intuitive shorthand command syntax.

# Features<!-- omit in toc -->

**Usage**

- Simple syntax and intuitive APIs make learning and using Reflex easy.

**Grid**

- Powerful and simple `[data-grid]` API.
- Fully responsive and customizable.
- Complete vendor prefixing.
- Grid trait system.
- Add/override default breakpoints, columns, traits and more.

**Layout**

- Control gutters with the responsive `data-gutter` API.
- Control height with the responsive `data-spacer` API.

**Shorthand**

- Apply flexbox properties with intuitive shorthand commands.
- Use shorthand commands via mixins or the `[data-flex]` and `[class]` APIs.

**CSS Resetting**

- Ships with normalize.css.
- Custom resetting available.

**Browser compatibility**

- All flexbox properties are fully vendor prefixed.

**Developers**

- Customize breakpoints, classes, values, metrics and vocabulary using the `_custom.scss` partial.

<hr>

# Table of contents

- [Table of contents](#table-of-contents)
- [1.0: The Grid](#10-the-grid)
  - [1.1: 12-columns](#11-12-columns)
  - [1.2: Breakpoints](#12-breakpoints)
  - [1.3: Grid areas](#13-grid-areas)
  - [1.4: Grid traits](#14-grid-traits)
    - [Gap](#gap)
    - [Flex-wrap](#flex-wrap)
    - [Justify-content](#justify-content)
    - [Align-items](#align-items)
- [2.0: Layout](#20-layout)
  - [2.1: Gutters](#21-gutters)
  - [2.1: Spacers](#21-spacers)
- [3.0: Shorthand](#30-shorthand)
  - [3.1: Singular](#31-singular)
  - [3.2: Grouped](#32-grouped)
- [4.0: Customizing Reflex](#40-customizing-reflex)

<hr>

# 1.0: The Grid

The `data-grid` API makes creating responsive grids and grid items simple.

## 1.1: 12-columns

Reflex uses a 12-column system to define the `width` of elements.

### Column example<!-- omit in toc -->

`data-grid="12"` makes the element 12 columns wide (100%). Writing `data-grid="6"` would make the item 6 out of 12 columns wide (50%).

```html
<div class="item" data-grid="12"></div>
```

```css
/* data-grid="12" in CSS is equivalent to... */

.item {
    width: 100%;
}
```

**TLDR:** Numbers 1-12 control element width based on a 12-column system.

## 1.2: Breakpoints

**Back to top** - [Table of Contents](#table-of-contents)

Breakpoints allow us to change the width of an element at certain screen sizes.

### Breakpoint syntax<!-- omit in toc -->

- **`blank`** = `0px`
- **`xs`** = `480px`
- **`s`** = `576px`
- **`m`** = `768px`
- **`l`** = `960px`
- **`xl`** = `1056px`

### Breakpoint example<!-- omit in toc -->

 `blank` `xs` `s` `m` `l` `xl` represent breakpoints. We can control the width of the item relative to the screensize by using these letters. This is what makes the system responsive.

```html
<div class="item" data-grid="12 s6 m4"></div>
```

```css
/* data-grid="12 s6 m4" in CSS is equivalent to... */

/* 12 */
.item {
    width: 100%;
}

/* s6 */
@media (min-width: 576px) {
    .item {
        width: 50%;
    }
}

/* m4 */
@media (min-width: 768px) {
    .item {
        width: 33.3%;
    }
}
```

**TLDR:** Letters `s` `m` `l` `xl` control element width relative to screensize.

## 1.3: Grid areas

**Back to top** - [Table of Contents](#table-of-contents)

Grid areas are used to apply traits to grid items.

### Grid area example<!-- omit in toc -->

It is common to have spacing between grid items especially boxes. By enclosing 4 grid items in a grid area, we can apply a gap trait easily. `gap-2` adds a `12px` gap between the grid items.

```html
<div class="parent area" data-grid="area gap-2">

    <div class="child item" data-grid="12 s6"></div>
    <div class="child item" data-grid="12 s6"></div>
    <div class="child item" data-grid="12 s6"></div>
    <div class="child item" data-grid="12 s6"></div>

</div>
```

**TLDR:** Grid areas apply traits to enclosed grid items.

## 1.4: Grid traits

### Gap

**Back to top** - [Table of Contents](#table-of-contents)

Gaps add spacing between grid items.

#### Default gap values<!-- omit in toc -->

- **`gap-1`** adds a **6px** gap between grid items.
- **`gap-2`** adds a **12px** gap between grid items.
- **`gap-3`** adds a **18px** gap between grid items.
- **`gap-4`** adds a **24px** gap between grid items.
- **`gap-5`** adds a **30px** gap between grid items.
- **`gap-6`** adds a **36px** gap between grid items.
- **`gap-7`** adds a **48px** gap between grid items.
- **`gap-8`** adds a **60px** gap between grid items.

#### `Gap` examples<!-- omit in toc -->

```html
<!-- Apply a 12px gap between children -->
<div data-grid="area gap-2">

    <div data-grid="12 s6"></div>
    <div data-grid="12 s6"></div>

</div>

<!-- Apply a 24px gap between children -->
<div data-grid="area gap-4">

    <div data-grid="12 s6"></div>
    <div data-grid="12 s6"></div>

</div>
```

### Flex-wrap

**Back to top** - [Table of Contents](#table-of-contents)

`flex-wrap` controls grid item wrapping

#### Values<!-- omit in toc -->

- **`reverse`** or **`fw-wr`** reverses the order of grid items.
- **`no-wrap`** or **`fw-nw`** disable wrapping of grid items.

#### Example<!-- omit in toc -->

```html
<!-- Reverses order of grid items (4,3,2,1) -->
<div data-grid="area reverse">

    <div class="item-1"></div>
    <div class="item-2"></div>
    <div class="item-3"></div>
    <div class="item-4"></div>

</div>
```

### Justify-content

**Back to top** - [Table of Contents](#table-of-contents)

By default, grid areas use `justify-content: flex-start;` to orient grid items. To adjust this orientation simple use one of the following commands when declaring a grid area.

#### Values<!-- omit in toc -->

- **`jc-sb`** Change `justify-content` value to `space-between`
- **`jc-c`** Change `justify-content` value to `center`
- **`jc-fe`** Change `justify-content` value to `flex-end`

#### Example<!-- omit in toc -->

```html
<div data-grid="area jc-sb"></div>
```

### Align-items

**Back to top** - [Table of Contents](#table-of-contents)

By default, grid areas use `align-items: stretch;` to orient grid items. To adjust this orientation simple use one of the following commands when declaring a grid area.

#### Align-items values<!-- omit in toc -->

- **`ai-fs`** Change `align-items` value to `space-between`
- **`ai-c`** Change `align-items` value to `center`
- **`ai-fe`** Change `align-items` value to `flex-end`

#### `Align-items` example<!-- omit in toc -->

```html
<div data-grid="area ai-fs"></div>
```

<hr>

# 2.0: Layout

## 2.1: Gutters

**Back to top** - [Table of Contents](#table-of-contents)

The `[data-gutter]` API helps create responsive gutters. Gutters can be used in layouts and elements to apply `padding` to an element. This API can apply padding to an element in any direction (`top` `right` `bottom` `left`) and change it responsively using breakpoints.

### Gutter syntax<!-- omit in toc -->

#### Breakpoints ([See Section](#12-breakpoints))<!-- omit in toc -->

#### Direction<!-- omit in toc -->

- **`a`** = `top` `right` `bottom` `left`
- **`v`** = `top` `bottom`
- **`h`** = `right` `left`
- **`t`** = `top`
- **`r`** = `right`
- **`b`** = `bottom`
- **`l`** = `left`

#### Padding<!-- omit in toc -->

- **`0`** = `0px`
- **`1`** = `6px`
- **`2`** = `12px`
- **`3`** = `18px`
- **`4`** = `24px`
- **`5`** = `30px`
- **`6`** = `36px`
- **`7`** = `48px`
- **`8`** = `60px`
  
#### Gutter syntax examples<!-- omit in toc -->

- `data-gutter="a4 sa5 ma6"`
- `data-gutter="v4 sv5 mv6 h6 sh7 sh8"`
- `data-gutter="t4 r5 b6 l7"`


### Gutter example 1<!-- omit in toc -->

```html
<!-- Adds padding in all ('a') directions to section element -->
<section data-gutter="a4 sa5 ma6">
    <h1>Hello world</h1>
</section>
```

```css
/* data-gutter="a4 sa5 ma6" in CSS is equivalent to... */

/* a4 */
section {
    padding-top: 24px;
    padding-right: 24px;
    padding-bottom: 24px;
    padding-left: 24px;
}

/* sa5 */
@media (min-width: 576px) {
    section {
        padding-top: 30px;
        padding-right: 30px;
        padding-bottom: 30px;
        padding-left: 30px;
    }
}

/* ma6 */
@media (min-width: 768px) {
    section {
        padding-top: 36px;
        padding-right: 36px;
        padding-bottom: 36px;
        padding-left: 36px;
    }
}
```

### Gutter example 2<!-- omit in toc -->

```html
<!-- We can also target the vertical and horizontal directions using 'v' or 'h' -->
<section data-gutter="v4 sv5 mv6">
    <h1>Hello world</h1>
</section>
```

```css
/* data-gutter="v4 sv5 mv6" in CSS is equivalent to... */

/* v4 */
section {
    padding-top: 24px;
    padding-bottom: 24px;
}

/* sv5 */
@media (min-width: 576px) {
    section {
        padding-top: 30px;
        padding-bottom: 30px;
    }
}

/* mv6 */
@media (min-width: 768px) {
    section {
        padding-top: 36px;
        padding-bottom: 36px;
    }
}
```

### Gutter example 3<!-- omit in toc -->

```html
<!-- Finally we can target specific directions using 't', 'r', 'b' and 'l' -->
<section data-gutter="t4 r5 b6 l7">
    <h1>Hello world</h1>
</section>
```

```css
/* data-gutter="v4 sv5 mv6" in CSS is equivalent to... */

section {
    /* t4 */
    padding-top: 24px;

    /* r5 */
    padding-right: 30px;

    /* b6 */
    padding-bottom: 36px;

    /* l7 */
    padding-left: 48px;
}
```

## 2.1: Spacers

**Back to top** - [Table of Contents](#table-of-contents)

The `[data-spacer]` API helps create responsively adjust height. Spacers are typically used to stylize elements.

### Spacer syntax<!-- omit in toc -->

#### Breakpoints ([See Section](#12-breakpoints))<!-- omit in toc -->

#### Height<!-- omit in toc -->

- **`0`** = `0px`
- **`1`** = `60px`
- **`2`** = `84px`
- **`3`** = `120px`
- **`4`** = `168px`
- **`5`** = `228px`
- **`6`** = `300px`
- **`7`** = `384px`
- **`8`** = `480px`
- **`9`** = `540px`
- **`10`** = `600px`
- **`11`** = `660px`
- **`12`** = `720px`

### Spacer example<!-- omit in toc -->

```html
<!-- Creates an element with responsive height -->
<div class="box" data-spacer="4 s5 m6"></div>
```

```css
/* data-spacer="4 s5 m6" in CSS is equivalent to... */

/* a4 */
.box {
    min-height: 168px;
}

/* s5 */
@media (min-width: 576px) {
    .box {
        min-height: 228px;
    }
}

/* m6 */
@media (min-width: 768px) {
    .box {
        min-height: 300px;
    }
}
```

<hr>

# 3.0: Shorthand

## 3.1: Singular

**Back to top** - [Table of Contents](#table-of-contents)

Apply singular flexbox properties to elements quickly using a shorthand syntax. This syntax can be declared using mixins ONLY.


### 3.1.1: Singular syntax<!-- omit in toc -->

<!--
##### `display`
##### `flex-direction`
##### `flex-wrap`
-->

<!---------------------------------------------------------------->
<!-- Display -->

#### `display`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`d-f`** = `display: flex;`
- **`d-if`** = `display: inline-flex;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- Flex-direction -->

#### `flex-direction`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`fd-r`** = `flex-direction: row;`
- **`fd-rr`** = `flex-direction: row-reverse;`
- **`fd-c`** = `flex-direction: column;`
- **`fd-cr`** = `flex-direction: column-reverse;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- Flex-wrap -->

#### `flex-wrap`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`fw-w`** = `flex-wrap: wrap;`
- **`fw-wr`** = `flex-wrap: wrap-reverse;`
- **`fw-nw`** = `flex-wrap: no-wrap;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- justify-content -->

#### `justify-content`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`jc-c`** = `justify-content: center;`
- **`jc-fs`** = `justify-content: flex-start;`
- **`jc-fe`** = `justify-content: flex-end;`
- **`jc-sb`** = `justify-content: space-between;`
- **`jc-sa`** = `justify-content: space-around;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- align-items -->

#### `align-items`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`ai-c`** = `align-items: center;`
- **`ai-fs`** = `align-items: flex-start;`
- **`ai-fe`** = `align-items: flex-end;`
- **`ai-s`** = `align-items: stretch;`
- **`ai-b`** = `align-items: baseline;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- align-self -->

#### `align-self`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`as-a`** = `align-self: auto;`
- **`as-c`** = `align-self: center;`
- **`as-fs`** = `align-self: flex-start;`
- **`as-fe`** = `align-self: flex-end;`
- **`as-sb`** = `align-self: space-between;`
- **`as-sa`** = `align-self: space-around;`
- **`as-s`** = `align-self: stretch;`

<hr></details>
<!---------------------------------------------------------------->

### 3.1.2: Singular examples<!-- omit in toc -->

```scss
// Mixins

// SCSS
.item-1 {
    @include d-f;
    @include fd-r;
    @include fw-w;
    @include js-c;
    @include ai-c;
}

// Compiled CSS
.item-1 {
    display: flex;
    align-items: center;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
}
```

## 3.2: Grouped

**Back to top** - [Table of Contents](#table-of-contents)

Apply multiple properties at once using command sequences. This is by far the most efficient way to use the flexbox shorthand syntax and we recommend it.

### 3.2.1: Grouped syntax<!-- omit in toc -->

Each command sequence is structured as such: `fluid (Optional)`-`flex-direction`-`justify-content`-`align-items`. Sequences can be declared as mixins or used in the inline HTML APIs.

<!---------------------------------------------------------------->
<!-- fluid -->

#### `fluid`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`f`** = `width: 100%; margin: 0 auto;`
- **`fr`** = `width: 100%; margin: 0 0 0 auto;`
- **`fl`** = `width: 100%; margin: 0 auto 0 0;`
- **`f_`** = `width: 100%;`

**Examples**
- `f-r-c-c`
- `fr-r-c-c`
- `fl-r-c-c`
- `f_r-c-c`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- flex-direction -->

#### `flex-direction`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`r`** = `flex-direction: row;`
- **`c`** = `flex-direction: column;`


<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- justify-content -->

#### `justify-content`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`c`** = `justify-content: center;`
- **`fs`** = `justify-content: flex-start;`
- **`fe`** = `justify-content: flex-end;`
- **`sb`** = `justify-content: space-between;`
- **`sa`** = `justify-content: space-around;`

<hr></details>
<!---------------------------------------------------------------->
<!---------------------------------------------------------------->
<!-- align-items -->

#### `align-items`<!-- omit in toc -->

<details><summary><b><code>Options</code></b></summary><br>

- **`c`** = `align-items: center;`
- **`fs`** = `align-items: flex-start;`
- **`fe`** = `align-items: flex-end;`
- **`s`** = `align-items: stretch;`

<hr></details>
<!---------------------------------------------------------------->

### 3.2.2: Grouped examples<!-- omit in toc -->

<!---------------------------------------------------------------->
<!-- Mixin examples -->

#### Mixin<!-- omit in toc -->

```scss
///
/// Command sequence mixins
///
/// Argument 1: fluid (Optional)
/// Argument 2: flex-direction
/// Argument 3: justify-content
/// Argument 4: align-items
///

// Example 1: row-center-center
.item-1 {
    @include r-c-c;
}

// Example 1: Compiled CSS
.item-1 {
    display: flex;
    align-items: center;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
}

// Example 2: column-center-center
.item-2 {
    @include c-c-c;
}

// Example 2: Compiled CSS
.item-2 {
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    position: relative;
}

// Example 3: fluid-row-center-center
.item-3 {
    @include f-r-c-c;
}

// Example 3: Compiled CSS
.item-3 {
    display: flex;
    align-items: center;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
    margin-right: auto;
    margin-left: auto;
    width: 100%;
}
```

#### Inline<!-- omit in toc -->

```html
<!-- [data-flex] -->
<div class="item-1" data-flex="r-c-c"></div>
<div class="item-1" data-flex="c-c-c"></div>
<div class="item-1" data-flex="f-r-c-c"></div> 

<!-- [class] -->
<div class="item-2 r-c-c"></div>
<div class="item-2 c-c-c"></div>
<div class="item-2 f-r-c-c"></div>  
```

<hr>

# 4.0: Customizing Reflex

## 4.1: Adding new values and overriding default values<!-- omit in toc -->

**Back to top** - [Table of Contents](#table-of-contents)

- **Defaults** are stored in `classes/_default.scss`
- The `classes/_custom.scss` partial can be used to add, override and remove values default values.

### Example 1: Add a new breakpoint<!-- omit in toc -->

```scss
/// File: classes/_default.scss
$default-breakpoints: (
    "0": (
        "class": "",
        "width": 0
    ),
    "1": (
        "class": "xs",
        "width": 480
    ),
    "2": (
        "class": "s",
        "width": 576
    ),
    "3": (
        "class": "m",
        "width": 768
    ),
    "4": (
        "class": "l",
        "width": 960
    ),
    "5": (
        "class": "xl",
        "width": 1056
    ),
);
```

```scss
/// File: classes/_custom.scss
// Add "xxl" breakpoint
$custom-breakpoints: (
    "6": (
        "class": "xxl",
        "width": 1152
    ),
);
```

### Example 2: Override a default breakpoint<!-- omit in toc -->

```scss
/// File: classes/_default.scss
// We are going to override "1" and make the width 500.
$default-breakpoints: (
    "0": (
        "class": "",
        "width": 0
    ),
    "1": (
        "class": "xs",
        "width": 480
    ),
    "2": (
        "class": "s",
        "width": 576
    ),
    "3": (
        "class": "m",
        "width": 768
    ),
    "4": (
        "class": "l",
        "width": 960
    ),
    "5": (
        "class": "xl",
        "width": 1056
    ),
);
```

```scss
/// File: classes/_custom.scss
$custom-breakpoints: (
    "1": (
        "class": "xs",
        "width": 500
    ),
);
```

### Example 3: Remove a breakpoint<!-- omit in toc -->

```scss
/// File: classes/_default.scss
$default-breakpoints: (
    "0": (
        "class": "",
        "width": 0
    ),
    "1": (
        "class": "xs",
        "width": 480
    ),
    "2": (
        "class": "s",
        "width": 576
    ),
    "3": (
        "class": "m",
        "width": 768
    ),
    "4": (
        "class": "l",
        "width": 960
    ),
    "5": (
        "class": "xl",
        "width": 1056
    ),
);
```

```scss
/// File: classes/_custom.scss
// Key removal
$default-breakpoints: map.remove($default-breakpoints, "1");
```

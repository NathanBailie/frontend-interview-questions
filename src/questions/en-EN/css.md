<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/css.png">
  <h2>CSS questions</h2>
</div>
<br />

<details>
<summary><span>1. What is CSS?</span></summary>
<br />

CSS (Cascading Style Sheets) is a style sheet language used to describe the presentation of HTML documents. It defines how elements should be displayed on screen, controlling layout, colors, fonts, spacing and other visual aspects of web pages.

</details>

---

<details>
<summary><span>2. What are the ways to connect a CSS file?</span></summary>
<br />

There are three ways to include CSS in an HTML document:

1. **External CSS**

   In HTML:

   ```html
   <link rel="stylesheet" href="styles.css" />
   ```

   In React:

   ```jsx
   import './styles.css';
   ```

   Key benefits:

   - Placed in the `<head>` section (HTML) or at the top of component file (React)
   - Most maintainable approach
   - Can be cached by browsers
   - One file can be used for multiple pages/components

2. **Internal CSS**

   In HTML:

   ```html
   <style>
   	body {
   		background-color: white;
   	}
   </style>
   ```

   In Vue:

   ```vue
   <style>
   .component {
   	background-color: white;
   }
   </style>
   ```

   - Placed in the `<head>` section (HTML) or within component file (Vue)
   - Styles only apply to that specific HTML page/component
   - Increases page size and loading time

3. **Inline CSS**
   ```html
   <p style="color: blue; font-size: 16px;">This is a paragraph</p>
   ```
   - Applied directly to individual HTML elements
   - Highest specificity
   - Hardest to maintain
   - Mixes content with presentation

</details>

---

<details>
<summary><span>3. What is the difference between margin and padding?</span></summary>
<br />

- **Padding** is the space inside an element between its content and border
- **Margin** is the space outside an element that creates distance from other elements

</details>

---

<details>
<summary><span>4. What are the possible values of the display property?</span></summary>
<br />

Most commonly used display values:

- block
- inline
- inline-block
- none
- flex
- grid
- table
- inherit
- initial

</details>

---

<details>
<summary><span>5. What are the characteristics of block elements?</span></summary>
<br />

- Start on a new line
- Take up full width available by default
- Can be sized using width and height properties
- Can be centered using margin: auto
- Respect margin and padding properties
- Can contain other block and inline elements

</details>

---

<details>
<summary><span>6. What are the characteristics of inline elements?</span></summary>
<br />

- Flow within text content in a single line
- Only take up as much width as their content
- Cannot have width and height set
- Can be horizontally aligned using text-align property
- Vertical margin has no effect
- Only horizontal padding and margins are respected
- Can only contain other inline elements
- Line height affects vertical spacing

</details>

---

<details>
<summary><span>7. What block elements do you know?</span></summary>
<br />

Common block elements:

- `<div>` - generic container
- `<p>` - paragraph
- `<h1>` to `<h6>` - headings
- `<section>` - section container
- `<article>` - article container
- `<header>` - header container
- `<footer>` - footer container
- `<form>` - form container
- `<ul>`, `<ol>` - lists
- `<li>` - list item
- `<main>` - main content
- `<nav>` - navigation container
- `<aside>` - sidebar content
- `<blockquote>` - quoted content

</details>

---

<details>
<summary><span>8. What inline elements do you know?</span></summary>
<br />

Common inline elements:

- `<span>` - generic inline container
- `<img>` - image
- `<a>` - hyperlink
- `<label>` - form label
- `<input>` - form input
- `<button>` - clickable button
- `<code>` - code snippet
- `<br>` - line break
- `<b>` - bold text
- `<strong>` - strong emphasis
- `<i>` - italicized text
- `<em>` - emphasized text
- `<small>` - smaller text
- `<sub>` - subscript
- `<sup>` - superscript

</details>

---

<details>
<summary><span>9. How do inline-block elements differ from block and inline elements?</span></summary>
<br />

Key characteristics of inline-block elements:

- Combine features of both block and inline elements
- Flow within text content like inline elements
- Do not force new lines like inline elements
- Can have width, height, margins and padding like block elements
- Both vertical and horizontal margins/padding are applied
- Do not take up full parent width by default
- Multiple elements can sit side by side if space allows

</details>

---

<details>
<summary><span>10. What is z-index and how does it work?</span></summary>
<br />

This property defines the stacking order of elements along the Z-axis (depth), determining which elements appear on top of others. It only works for elements with position: relative, absolute, fixed, or sticky.

- The higher the z-index value, the closer the element is to the user
- The lower the value, the further the element is
- If z-index is not set, elements are arranged in the order they appear in the code
</details>

---

<details>
<summary><span>11. What is selector specificity?</span></summary>
<br />

It is the specific weight by which the browser determines the priority of styles when multiple rules are applied to the same element. The higher the specificity, the higher the priority of the style

If two or more selectors conflict, the browser selects the one with the greater weight. If the specificity is the same, the rule written later in the code is applied

Selector specificity can be represented as a tuple of three numbers, where:

- The first value is the number of ID selectors (highest priority)
- The second value is the sum of classes, attributes, and pseudo-classes
- The third value is the number of tags and pseudo-elements

</details>

---

<details>
<summary><span>12. What is a pseudo-element? Provide examples</span></summary>
<br />

A pseudo-element in CSS allows styling a part of an element without modifying the HTML markup.

Most commonly used:

- `::before` - adds content before the element
- `::after` - adds content after the element
- `::first-letter` - letter styles the first letter of the text
- `::first-line` - line styles the first line of the text

</details>

---

<details>
<summary><span>13. What is a pseudo-classes? Provide examples</span></summary>
<br />

This is a way to apply styles to an element based on its state or position in the DOM, without adding classes or attributes in HTML

Main pseudo-classes:

- `:hover` – applied when the user hovers over an element
- `:focus` – activated when an element gains focus (e.g., when clicking inside an input field)
- `:active` – when an element is active (pressed)
- `:checked` – applied to a checked checkbox or radio button
- `:first-child` / `:last-child `– styles the first or last child element
- `:nth-child(n)` – selects a specific child element among siblings (e.g., the second item in a list)
- `:disabled` – used for disabled form elements

</details>

---

<details>
<summary><span>14. What are the types of element positioning?</span></summary>
<br />

- `static`
- `relative`
- `absolute`
- `fixed`
- `sticky`

</details>

---

<details>
<summary><span>15. What is the difference between <b>relative</b> and <b>absolute</b> positioning?</span></summary>
<br />

- `relative` — the element remains in the document flow but can be shifted relative to its original position
- `absolute` — the element is removed from the document flow and positioned relative to the nearest parent with **fixed**, **relative** or **absolute** positioning

</details>

---

<details>
<summary><span>16. What is the difference between <b>fixed</b> and <b>sticky</b> positioning?</span></summary>
<br />

- `fixed` — the element is anchored relative to the browser window and remains in place even when the entire page is scrolled.

- `sticky` — the element behaves like relative until it reaches the position specified via top, left, etc. Then, it sticks to that position within its parent and stays there until the end of the parent's area, without exceeding its boundaries.

</details>

---

<details>
<summary><span>17. How does <b>flexbox</b> work and what are its main properties?</span></summary>
<br />

It is a CSS tool for convenient element positioning on a page, used to create responsive interfaces and center elements.
<br /><br />

Flexbox uses **two axes** that help control element placement:

1. **Main Axis** — the direction along which elements are placed
   - Defined by the `flex-direction` property
   - Can be **horizontal** (`row`) or **vertical** (`column`)
2. **Cross Axis** — perpendicular to the main axis, responsible for element alignment
   - Controlled via `align-items` and `align-content`

---

### **Alignment along the main axis (`justify-content`)**

Used to control element placement **horizontally** (if `flex-direction: row`) or **vertically** (if `flex-direction: column`):

- `flex-start` — elements are aligned at the start
- `flex-end` — aligned at the end
- `center` — centered
- `space-between` — evenly distributed **without gaps at the edges**
- `space-around` — evenly distributed **with gaps on the sides**
- `space-evenly` — fully evenly distributed, including the edges

---

### **Alignment along the cross axis (`align-items`)**

Controls element placement **perpendicular to the main axis**:

- `stretch` (default) — elements stretch to fit the container height
- `flex-start` — aligned at the start of the cross axis
- `flex-end` — aligned at the end
- `center` — centered
- `baseline` — aligned along the text baseline

---

### 🔹 **Additional Flexbox commands**

- **`flex-direction`** — sets the direction of elements (`row`, `column`, `row-reverse`, `column-reverse`, `inherit`, `initial`, `unset`).
- **`flex-wrap`** — controls line wrapping (`nowrap`, `wrap`, `wrap-reverse`, `inherit`, `initial`, `unset`).
- **`flex-flow`** — combines `flex-direction` and `flex-wrap` (e.g., `row wrap`, `column nowrap`).
- **`flex-shrink`** — defines how much elements shrink (`0` — does not shrink, `1` — standard shrinking).
- **`flex-grow`** — regulates element growth (`0` — does not grow, `1+` — degree of growth).
- **`flex-basis`** — sets the initial size (`auto`, `100px`, `25%`).
- **`order`** — changes display order (`-1`, `0`, `1`, `2`, etc.).
- **`align-self`** — individual alignment (`auto`, `flex-start`, `flex-end`, `center`, `baseline`, `stretch`).
- **`align-content`** — manages row placement (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `stretch`).
- **`justify-content`** — controls element positioning along the main axis (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`).

</details>

---

<details>
<summary><span>18. How is the <b>grid</b> system structured?</span></summary>
<br />

It is a tool for creating complex layouts that allows working with row and column grids. Unlike Flexbox, which controls elements along one axis, **Grid** organizes content in a **two-dimensional** structure.

### **Main grid properties (`grid-container`)**

Used on the parent element (`display: grid;`):

- **`grid-template-columns`** — sets the number and width of columns (`100px 200px 1fr`).
- **`grid-template-rows`** — defines row heights (`50px auto 1fr`).
- **`grid-template-areas`** — sets named areas (`"header header" "sidebar main" "footer footer"`).
- **`grid-template`** — combines `grid-template-rows`, `grid-template-columns`, and `grid-template-areas` into one property.
- **`grid-gap` / `gap`** — sets spacing between elements (`10px`, `20px`).
- **`justify-items`** — controls alignment **inside cells** (`start`, `end`, `center`, `stretch`).
- **`align-items`** — sets vertical alignment inside **cells** (`start`, `end`, `center`, `stretch`).
- **`justify-content`** — distributes the entire grid along the **main axis** (`start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`).
- **`align-content`** — distributes the entire grid along the **cross axis** (similar to `justify-content`, but vertically).

---

### **Grid item properties (`grid-item`)**

Used on child elements inside `grid-container`:

- **`grid-column-start` / `grid-column-end`** — defines which column the element starts and ends in (`2 / 4`).
- **`grid-row-start` / `grid-row-end`** — sets rows (`1 / 3`).
- **`grid-area`** — combines `row` and `column` (`1 / 2 / 3 / 4`).
- **`justify-self`** — controls horizontal positioning of an element (`start`, `end`, `center`, `stretch`).
- **`align-self`** — adjusts vertical positioning of an element (`start`, `end`, `center`, `stretch`).

---

### 🔹 **Automatic placement (`auto-fill`, `auto-fit`)**

- **`grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));`**
- **`grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));`**

✔ `auto-fill` **fills the grid with the maximum number of possible columns**.  
✔ `auto-fit` **adjusts column sizes so they fill the available space**.

</details>

---

<details>
<summary><span>19. When to use flexbox and when to use grids?</span></summary>
<br />

**Flexbox** — a tool for one-axis element management, ideal for arranging components **horizontally or vertically**.  
**Grid** — a powerful system for two-dimensional layouts, where elements need to be **positioned in both rows and columns**.

The choice depends on the task: if flexibility along a single axis is needed — **Flexbox**, if a structured grid is required — **Grid**.

</details>

---

<details>
<summary><span>20. What is the difference between <b>div</b> and <b>span</b>?</span></summary>
<br />

- `div` — a block-level element used for grouping content and creating structural blocks.
- `span` — an inline element used for highlighting specific parts of text or styling within a line.

</details>

---

<details>
<summary><span>21. What is <b>box-sizing</b> and what values can it take?</span></summary>
<br />

**`box-sizing`** is a CSS property that defines how the size of an element is calculated, including its width and height.

### **Available values**

- **`content-box`** (default) — the element's size is calculated **excluding** `padding` and `border`.
- **`border-box`** — **all** inner paddings (`padding`) and borders (`border`) are included within the specified `width` and `height`.

</details>

---

<details>
<summary><span>22. What are the ways to hide an element from a page?</span></summary>
<br />

There are several ways to hide an element:

- **`display: none`** — completely removes the element from the document flow; it does not take up space.
- **`visibility: hidden`** — the element is invisible but still takes up space on the page.
- **`opacity: 0`** — makes the element fully transparent, but it remains clickable.
- **`width: 0; height: 0`** — collapses the element to zero dimensions.
- **`position: absolute; left: -9999px`** — moves the element far beyond the visible area.
- **`clip-path: polygon(0 0)`** — crops the element to an invisible point.

Each method has its own characteristics:

- `display: none` **cannot be animated**.
- `visibility` and `opacity` **can be animated**.
- `opacity` **preserves interactivity** (the element remains clickable).
- `position: absolute` **may affect performance**.

</details>

---

<details>
<summary><span>23. What is the difference between opacity and visibility?</span></summary>
<br />

- **`opacity`** controls transparency levels, **can be animated**, and keeps the element **interactive** (clickable, responsive to events).
- **`visibility`** simply hides the element, but it remains in the document flow and **does not respond to events**. `visibility` **cannot be animated** using `transition`.

</details>

---

<details>
<summary><span>24. What are the relative size units?</span></summary>
<br />

- **`em`** — depends on the font size of the parent element.
- **`rem`** — depends on the font size of the root element (`html`).
- **`%`** — percentage-based size relative to the parent element.
- **`vh`** — percentage of the viewport height.
- **`vw`** — percentage of the viewport width.
- **`vmin`** — percentage of the smaller dimension (`vh` or `vw`).
- **`vmax`** — percentage of the larger dimension (`vh` or `vw`).
- **`ex`** — depends on the height of the lowercase letter `x` in the current font.
- **`ch`** — depends on the width of the `0` character in the current font.

</details>

---

<details>
<summary><span>25. What are media queries used for?</span></summary>
<br />

Media queries allow different styles to be applied based on device characteristics (screen width, orientation, device type, etc.). They are the primary tool for creating **responsive design**.

</details>

---

<details>
<summary><span>26. How to ensure responsiveness without media queries?</span></summary>
<br />

- **Flexbox and Grid** — flexible layouts that adapt to available space.
- **Relative units (`em`, `rem`, `%`, `vh`, `vw`)** — scale based on the container or screen.
- **`max-width` and `min-width`** — prevent elements from being too large or too small.
- **`clamp()`** — sets a dynamic range (`clamp(200px, 50%, 600px)`).
- **`auto` instead of fixed sizes** — elements adjust to content.
- **`fit-content`** — used for adaptive widths (`width: fit-content;`).
- **`calc()`** — allows combining sizes (`width: calc(100% - 50px);`).
- **`aspect-ratio`** — maintains correct proportions without media queries (`aspect-ratio: 16/9;`).
- **CSS `container queries` (modern browsers)** — adapts styling based on the parent block's size.

</details>

---

<details>
<summary><span>27. What is <b>@keyframes</b>?</span></summary>
<br />

`@keyframes` is a CSS rule that allows animations to be created by defining a sequence of styles at specific points in an animation. It is used together with the `animation` property to apply animations to elements.

### **Main animation properties**

- **`animation-name`** — defines the name of the `@keyframes` animation.
- **`animation-duration`** — sets the animation duration in seconds or milliseconds.
- **`animation-timing-function`** — controls transition behavior (`linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`, `steps()`).
- **`animation-delay`** — sets the delay before the animation starts.
- **`animation-iteration-count`** — sets the number of repetitions (`1`, `infinite`, etc.).
- **`animation-direction`** — defines playback direction (`normal`, `reverse`, `alternate`, `alternate-reverse`).
- **`animation-fill-mode`** — controls the element's state before and after the animation (`none`, `forwards`, `backwards`, `both`).
- **`animation-play-state`** — defines whether the animation is **running** or **paused**.

</details>

---

<details>
<summary><span>28. How does <b>transition</b> work?</span></summary>
<br />

`transition` is a CSS property for smooth transitions between values of other properties.

### **Main parameters:**

- **`transition-property`** — defines the property to animate.
- **`transition-duration`** — sets the duration of the transition.
- **`transition-timing-function`** — controls easing behavior.
- **`transition-delay`** — defines a delay before the transition starts.

Example: `transition: all 0.3s ease;`

</details>

---

<details>
<summary><span>29. What is <b>will-change</b> and when should it be used?</span></summary>
<br />

This CSS property tells the browser which properties are likely to change, allowing it to optimize rendering in advance.

It is used to improve the performance of complex animations but should be applied **sparingly** to avoid unnecessary load on the browser.

</details>

---

<details>
<summary><span>30. What is <b>float</b>?</span></summary>
<br />

This is a CSS property that allows an element to "float" along the left or right edge of its container while text and inline elements wrap around it.  
<br /><br />

### **Main values:**

- `left` — the element floats at the left edge.
- `right` — the element floats at the right edge.
- `none` — disables floating (default value).

### **Key characteristics:**

- Floating elements **are removed from the document flow**.
- The **parent container may collapse** if it only contains floating elements.
- The `clear` property **is used to prevent unwanted wrapping**.

</details>

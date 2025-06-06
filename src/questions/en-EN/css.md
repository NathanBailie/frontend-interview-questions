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

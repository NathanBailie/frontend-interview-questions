<a href="../../README.md">← Back</a>

<div align="center">
  <h2>📝 CSS Questions</h1>
</div>

<details>
<summary><h3 style="display: inline;">What is CSS?</h3></summary>
<br />

CSS (Cascading Style Sheets) is a style sheet language used to describe the presentation of HTML documents. It defines how elements should be displayed on screen, controlling layout, colors, fonts, spacing and other visual aspects of web pages.

</details>

---

<details>
<summary><h3 style="display: inline;">What are the ways to connect a CSS file?</h3></summary>
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
<summary><h3 style="display: inline;">What is the difference between margin and padding?</h3></summary>
<br />

- **Padding** is the space inside an element between its content and border
- **Margin** is the space outside an element that creates distance from other elements

</details>

---

<details>
<summary><h3 style="display: inline;">What are the possible values of the display property?</h3></summary>
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
<summary><h3 style="display: inline;">What are the characteristics of block elements?</h3></summary>
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
<summary><h3 style="display: inline;">What are the characteristics of inline elements?</h3></summary>
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
<summary><h3 style="display: inline;">What block elements do you know?</h3></summary>
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
<summary><h3 style="display: inline;">What inline elements do you know?</h3></summary>
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
<summary><h3 style="display: inline;">How do inline-block elements differ from block and inline elements?</h3></summary>
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

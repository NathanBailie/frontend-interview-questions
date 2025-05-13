  <a href="../../README.md">← Back</a>

<div align="center">
  <h2>📝 CSS Questions</h1>
</div>

### 1. What is CSS?

<details>
<summary>🔍 <b>Answer</b></summary>
<br />

CSS (Cascading Style Sheets) is a style sheet language used to describe the presentation of HTML documents. It defines how elements should be displayed on screen, controlling layout, colors, fonts, spacing and other visual aspects of web pages.

</details>

---

### 2. What are the ways to connect a CSS file?

<details>
<summary>🔍 <b>Answer</b></summary>
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

<a href="../../README.md">← Back</a>

<div align="center">
  <h2>📝 HTML Questions</h1>
</div>

<details>
<summary><h3 style="display: inline;">What is HTML?</h3></summary>
<br />

HTML (HyperText Markup Language) is the standard markup language used to create and structure content on the web.

</details>

---

<details>
<summary><h3 style="display: inline;">What is DOCTYPE?</h3></summary>
<br />

DOCTYPE (Document Type Declaration) is an instruction at the beginning of an HTML document that tells the browser which version of HTML to use for rendering the page

</details>

---

<details>
<summary><h3 style="display: inline;">What are the ways to link a JavaScript file to an HTML document?</h3></summary>
<br />

There are two main ways to include JavaScript in an HTML document:

1. **External JavaScript**

   ```html
   <!-- Synchronous loading (at the end of body) -->
   <body>
   	<!-- content -->
   	<script src="script.js"></script>
   </body>

   <!-- Asynchronous loading (in head) -->
   <head>
   	<script src="script.js" defer></script>
   	<!-- Executes after HTML is parsed, doesn't block HTML parsing -->
   	<script src="script.js" async></script>
   	<!-- Executes immediately when downloaded, doesn't block HTML parsing, may break execution order -->
   </head>
   ```

   Key points:

   - Most maintainable approach
   - Can be cached by browsers
   - Can control loading behavior with `defer` and `async` attributes
   - One file can be reused across multiple pages

2. **Inline JavaScript**

   ```html
   <script>
   	function sayHello() {
   		alert('Hello!');
   	}
   </script>
   ```

   or directly in HTML elements:

   ```html
   <button onclick="sayHello()">Click me</button>
   ```

   - Code is embedded directly in HTML
   - Cannot be cached
   - Mixes behavior with content
   - Useful for small, page-specific scripts
   </details>

---

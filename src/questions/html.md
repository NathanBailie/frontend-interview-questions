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

<details>
<summary><h3 style="display: inline;">What is semantic markup?</h3></summary>
<br />

Semantic markup is an approach to HTML markup where tags are used to convey the meaning of content rather than just defining its appearance

</details>

---

<details>
<summary><h3 style="display: inline;">What are examples of semantic HTML tags?</h3></summary>
<br />

Here are common semantic HTML tags:

- `<header>` - Defines a header section
- `<nav>` - Contains navigation links
- `<main>` - Specifies the main content
- `<article>` - Represents a self-contained composition
- `<section>` - Defines a thematic grouping of content
- `<aside>` - Contains content tangentially related to surrounding content
- `<footer>` - Defines a footer section
</details>

---

<details>
<summary><h3 style="display: inline;">What are the benefits of semantic markup?</h3></summary>
<br />

- **Improves SEO**: Search engines better understand the page structure, which can improve site rankings in search results

- **Enhances accessibility**: Screen readers and other assistive technologies can better interpret content, making the site more usable for people with disabilities

- **Simplifies code maintenance**: Semantic tags make code more readable, reducing the complexity of editing and scaling

- **Improves user experience**: Logically structured content helps users find information more quickly

- **Increases compatibility**: Semantic HTML adapts better to different devices and future web standards

</details>

---

<details>
<summary><h3 style="display: inline;">What are examples of global HTML attributes?</h3></summary>
<br />

- `class` - Specifies one or more class names for styling and JavaScript selection
- `id` - Defines a unique identifier for an element
- `style` - Contains inline CSS styles
- `title` - Provides additional information shown on hover
- `data-*` - Custom data attributes for storing extra information
- `hidden` - Hides an element from display
- `lang` - Specifies the language of element's content
- `dir` - Sets text direction (ltr or rtl)
- `tabindex` - Controls element's tab order
- `contenteditable` - Makes element content editable

</details>

---

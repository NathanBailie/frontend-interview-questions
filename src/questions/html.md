<a href="../../README.md">← Back</a>

<div align="center">
  <h2>📝 HTML Questions</h2>
</div>

<details>
<summary><span>What is HTML?</span></summary>
<br />

HTML (HyperText Markup Language) is the standard markup language used to create and structure content on the web.

</details>

---

<details>
<summary><span>What is DOCTYPE?</span></summary>
<br />

DOCTYPE (Document Type Declaration) is an instruction at the beginning of an HTML document that tells the browser which version of HTML to use for rendering the page

</details>

---

<details>
<summary><span>What are the ways to link a JavaScript file to an HTML document?</span></summary>
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
<summary><span>What is semantic markup?</span></summary>
<br />

Semantic markup is an approach to HTML markup where tags are used to convey the meaning of content rather than just defining its appearance

</details>

---

<details>
<summary><span>What are examples of semantic HTML tags?</span></summary>
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
<summary><span>What are the benefits of semantic markup?</span></summary>
<br />

- **Improves SEO**: Search engines better understand the page structure, which can improve site rankings in search results

- **Enhances accessibility**: Screen readers and other assistive technologies can better interpret content, making the site more usable for people with disabilities

- **Simplifies code maintenance**: Semantic tags make code more readable, reducing the complexity of editing and scaling

- **Improves user experience**: Logically structured content helps users find information more quickly

- **Increases compatibility**: Semantic HTML adapts better to different devices and future web standards

</details>

---

<details>
<summary><span>What are examples of global HTML attributes?</span></summary>
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

<details>
<summary><span>What meta tags do you know?</span></summary>
<br />

- `<meta charset="UTF-8">` - Specifies document encoding. UTF-8 is the most common

- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` - Controls scaling and adaptation of the page on mobile devices

- `<meta name="description" content="Page description">` - Brief description of page content for search engines and social media

- `<meta name="keywords" content="keywords, here">` - List of keywords

- `<meta name="author" content="Author name">` - Specifies the page or website author

- `<meta name="robots" content="index, follow">` - Sets instructions for search engine robots (e.g. whether to index or not)

- `<meta property="og:title" content="Social media title">` - Page title for display on Facebook, LinkedIn etc

- `<meta property="og:description" content="Social media description">` - Brief description when sharing links

- `<meta property="og:image" content="image URL">` - Link to image displayed when sharing

</details>

---

<details>
<summary><span>What are data attributes used for?</span></summary>
<br />

They are used to store additional data directly in the markup. Nowadays, they are most commonly used to store test IDs, making it easier to locate the required element

</details>

---

<details>
<summary><span>What is the label tag used for?</span></summary>
<br />

**Binding label to form element** - this makes the interface more convenient since users can click on the text to activate the corresponding `<input>`, `<textarea>` or `<select>`

**Improving accessibility** - screen readers recognize `<label>` and help people with disabilities understand what data needs to be entered.

</details>

---

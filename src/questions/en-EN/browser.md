<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/browser.png">
  <h2>Browser questions</h2>
</div>
<br />

<details>
<summary><span>1. What happens from entering a URL in the address bar and pressing Enter to receiving and rendering HTML in the browser?</span></summary>
<br />

### **1. Entering URL and parsing**

- The user enters a URL, e.g., `https://example.com`.
- The browser analyzes the URL and determines:
  - Protocol (`https`)
  - Domain name (`example.com`)
  - Path, parameters, anchor (if present)

---

### **2. Cache check**

Before making a request, the browser checks local sources:

- **DNS cache** (if the IP address was previously requested)
- **HTTP cache** (if the page was loaded and stored)
- **Service Worker** (if configured, it can process the request)

If the IP address is found in the cache, the DNS resolution step is skipped.

---

### **3. DNS resolution and finding the IP address**

If no IP is found in the cache, the browser makes a DNS request. The request goes through several steps, moving along a chain of servers:

1. **Local DNS** (Internet provider) checks for a record.
2. If no record exists, the request is forwarded to **root DNS servers**.
3. The root server directs the request to the **domain zone server** (e.g., `.com`).
4. The domain zone server directs the request to the **authoritative DNS server of the site** (e.g., DNS for `example.com`).
5. The authoritative server returns the **IP address** corresponding to the domain.

As a result: `example.com` → `93.184.216.34`.

---

### **4. Establishing a TCP connection**

The browser establishes a connection with the obtained IP via **TCP**:

- The connection opens on port **80 (HTTP) or 443 (HTTPS)**.
- **Three-way handshake** is used. This process consists of three steps:

  - The browser (client) sends a **SYN packet** to the server, requesting a connection.
  - The server accepts the SYN request and responds with a **SYN-ACK packet**, confirming readiness.
  - The client receives SYN-ACK and sends an **ACK packet**, confirming the connection.

---

### **5. TLS handshake (for HTTPS)**

For secure communication, the browser and server:

- Exchange certificates.
- Establish a **shared encryption key** (SSL/TLS).

---

### **6. Sending an HTTP request**

The browser sends an **HTTP request**:

```
GET / HTTP/1.1
Host: example.com
User-Agent: Chrome/...
Accept: text/html
```

---

### **7. Server receives and processes the request**

- The server processes the request and generates an **HTTP response**:
  - If the site is dynamic, backend processing may occur (Node.js, PHP, Python, etc.).
  - If the page is static, it serves an HTML file.

---

### **8. Server response**

The server sends an **HTTP response**:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: ...
```

</details>

---

<details>
<summary><span>2. What is <b>CRP</b>?</span></summary>
<br />

**Critical Rendering Path (CRP)** is the sequence of steps a browser follows to process HTML, CSS, and JavaScript into a fully rendered web page displayed on screen.

</details>

---

<details>
<summary><span>3. What are the stages of <b>CRP</b>?</span></summary>
<br />

1. **Parsing HTML** – The browser loads HTML and builds the DOM tree.

2. **Processing CSS** – CSS is loaded and the CSSOM (style model) is formed.

3. **Building the Render Tree** – DOM and CSSOM are combined to create a structure of elements for rendering.

4. **Layout stage (positioning computation)** – The browser calculates element sizes and positions.

5. **Painting stage (drawing)** – Pixels are converted into a visual representation, displaying content.

6. **Compositing stage (layer assembly)** – The final step where elements are combined into a single image and displayed on the screen.

</details>

---

<details>
<summary><span>4. What actually blocks page rendering?</span></summary>
<br />

1. **CSS files** – External stylesheets block rendering until fully loaded and processed by the browser, as they affect page appearance.

2. **Synchronous JavaScript (`<script>` without `defer` or `async`)** – Halts HTML parsing, delaying DOM construction and rendering.

3. **Web Fonts** – If `font-display: auto` or `block` is used, the browser may hide text (FOIT) while waiting for the font to load.

4. **`@import` in CSS** – Especially with nested imports, slows down loading and processing of styles, blocking rendering.

</details>

---

<details>
<summary><span>5. When should a JS file be placed before the closing <b>body</b> tag?</span></summary>
<br />

1. **When the script depends on HTML elements** – If JavaScript interacts with the DOM (`document.getElementById`, `querySelector`), elements must be fully loaded.

2. **When JavaScript interacts with styles** – If the script modifies CSS or depends on `getComputedStyle()`, it’s crucial that the browser first constructs the CSSOM.

Placing scripts before `</body>` also avoids blocking rendering.

</details>

---

<details>
<summary><span>6. What can cause a <b>reflow</b>?</span></summary>
<br />

1. **Changing an element’s dimensions** – Setting or modifying `width`, `height`, `padding`, `margin`, `border`, `box-sizing`, etc.

2. **Adding or removing elements in the DOM** – Any DOM structure change (insertion, deletion, node movement) affects layout.

3. **Changing styles affecting layout** – e.g., `display`, `position`, `float`, `font-size`, `line-height`.

4. **Computing sizes via JavaScript** – Calls like `getBoundingClientRect()`, `offsetWidth`, `scrollHeight` may trigger forced reflow if the DOM has changed.

5. **Font changes** – Loading a new font (`@font-face`) or switching `font-family` can alter text sizes and cause recalculations.

6. **Layout-property changes during animation** – Properties like `top`, `left`, `width`, `height` (especially without GPU optimization) trigger reflow.

7. **Editable areas (`contenteditable`)** – Text changes or content insertion may cause reflow while interacting.

8. **Complex structures (e.g., tables)** – Tables with interdependent cell sizes often trigger reflow and require more computation.

</details>

---

<details>
<summary><span>7. How can <b>CRP</b> be optimized?</span></summary>
<br />

1. **Reduce the number of critical resources**  
   — Remove unused CSS and JS  
   — Defer loading of non-critical resources (lazy loading)

2. **Minimize rendering-blocking resources**  
   — Use `async` and `defer` for scripts  
   — Inline critical styles in `<style>`, defer the rest

3. **Minimize critical resource sizes**  
   — Minify CSS, JS, HTML  
   — Compress with Gzip or Brotli

4. **Optimize HTTP request count**  
   — Bundle files  
   — Inline critical styles and scripts

5. **Optimize resource loading order**  
   — Prioritize loading essential resources for the first screen  
   — Defer loading of non-important content (`lazy loading`)

6. **Use `<preload>`, `<prefetch>`, `<preconnect>`**  
   — `preload` — Load critical resources early  
   — `prefetch` — Load resources that will be needed later  
   — `preconnect` — Pre-connect to external domains (e.g., fonts, analytics)

7. **Use CDN (Content Delivery Network)**  
   — Accelerates loading by serving resources from the nearest servers

</details>

---

<details>
<summary><span>8. What storage options are available in the browser?</span></summary>
<br />

| Storage            | Data volume                 | Retention period                                     | Accessibility                             | Features                                                        |
| ------------------ | --------------------------- | ---------------------------------------------------- | ----------------------------------------- | --------------------------------------------------------------- |
| **Cookies**        | ~4 KB per cookie            | Set by the server or JavaScript, may be time-limited | Sent to the server with each HTTP request | Used for authentication, storing user preferences               |
| **LocalStorage**   | Up to 5–10 MB               | Until the user manually deletes it                   | Only within the current domain            | Stores data between sessions, synchronous API                   |
| **SessionStorage** | Up to 5–10 MB               | Until the browser tab is closed                      | Only within a single tab                  | Temporary data storage unique to the tab                        |
| **IndexedDB**      | Limited only by disk space  | Long-term storage                                    | Browser-only                              | Asynchronous storage for structured data, supports transactions |
| **Cache Storage**  | Depends on browser policies | Long-term storage                                    | Browser-only                              | Used in Service Worker for caching resources (e.g., in PWA)     |

</details>

<!-- <details>
<summary><span></span></summary>
<br />

</details>

--- -->

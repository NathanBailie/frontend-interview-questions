<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/nodejs.png">
  <h2>Node.js</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>Node.js</b>?</span></summary>
<br />

Node.js is a JavaScript runtime environment outside the browser, built on the V8 engine. It allows you to create server-side applications that handle many requests asynchronously.

</details>

---

<details>
<summary><span>2. What is Node.js made of?</span></summary>
<br />

- **V8** — the engine that executes JavaScript
- **libuv** — a library for **asynchronous I/O** and **thread management**
- **Built-in modules** — such as **fs**, **http**, **path**
- **npm** — a package manager for installing and managing dependencies

</details>

---

<details>
<summary><span>3. What does the <b>V8 engine</b> do?</span></summary>
<br />

**V8** is a high-performance engine from Google that **compiles JavaScript into machine code**. It handles **execution and optimization** of JS code in Node.js.

</details>

---

<details>
<summary><span>4. What does the <b>libuv</b> library do?</span></summary>
<br />

**libuv** is a library that provides **asynchronous I/O**, **event handling**, **timers**, **network sockets**, and a **thread pool**. It enables Node.js to efficiently process many operations without blocking the main thread.

</details>

---

<details>
<summary><span>5. What are the <b>advantages and disadvantages of the Event Loop</b> in Node.js?</span></summary>
<br />

**Advantages**:

- **Asynchronous** — handles many requests efficiently without blocking
- **High performance** for I/O operations
- **Easy scalability** through non-blocking architecture

**Disadvantages**:

- **Single-threaded limitation** — heavy computations can block the loop
- **Debugging complexity** in asynchronous code
- **Low performance** for CPU-intensive tasks

</details>

---

<details>
<summary><span>6. Is Node.js <b>single-threaded or multi-threaded</b>?</span></summary>
<br />

Node.js is single-threaded by design: the main thread handles JavaScript code using an event-driven model.

However, under the hood, Node.js uses the <b>libuv</b> library, which is <b>multi-threaded</b>. It handles asynchronous operations like file system access, DNS, cryptography, etc.

By default, libuv runs a <b>thread pool of 4 threads</b>. You can increase this up to <b>128</b> using the `UV_THREADPOOL_SIZE` environment variable.

Important: if more tasks are submitted than available threads (e.g., 5 tasks with 4 threads), the 5th task will <b>wait</b> until one of the threads becomes free.

</details>

---

<details>
<summary><span>7. What does the <b>event demultiplexer</b> do?</span></summary>
<br />

An event demultiplexer is a mechanism that monitors multiple sources of events (e.g., sockets, timers, file descriptors) and determines which are ready for processing.

In Node.js and libuv, it:

- **waits for events** from various asynchronous operations
- **selects ready events** (e.g., file read completion or incoming socket data)
- **passes control** to the appropriate handlers (callback functions)

This allows efficient management of many operations in a single thread without blocking execution.

</details>

---

<details>
<summary><span>8. Describe the cycle: <b>application → event demultiplexer → queue → Event Loop</b></span></summary>
<br />

The process works step by step:

1. The **application** initiates asynchronous operations (e.g., file read, DB query, timer).
2. These operations are passed to the **event demultiplexer** (e.g., `epoll`, `kqueue`, `IOCP` depending on platform), which monitors when they complete or become ready.
3. Once an operation finishes, its info is placed into the **ready event queue** (callback queue).
4. The **Event Loop** checks this queue and sequentially invokes the corresponding **callback functions**.

This enables non-blocking execution, allowing Node.js to handle many operations efficiently in a single thread.

</details>

---

<details>
<summary><span>9. How does the <b>thread scheduler</b> work?</span></summary>
<br />

The thread scheduler in libuv manages tasks that require blocking execution (e.g., `fs`, `crypto`, `dns`).

- Tasks are placed in a queue.
- Threads from the pool (default: 4) pick up tasks in order.
- If all threads are busy, new tasks wait until a thread is free.
- After execution, the result is passed back to the Event Loop.

</details>

---

<details>
<summary><span>10. What performs <b>optimization</b> inside Node.js?</span></summary>
<br />

Optimization in Node.js is achieved through:

- <b>V8</b> — the engine that compiles JavaScript into machine code and applies JIT optimizations
- <b>libuv</b> — efficiently manages asynchronous tasks and thread pooling
- <b>Event Loop</b> — minimizes blocking by distributing tasks across phases
- <b>Hidden classes and inline caching</b> — accelerate property access on objects

These components work together to improve performance and reduce latency.

</details>

---

<details>
<summary><span>11. What is <b>deoptimization</b>?</span></summary>
<br />

Deoptimization is the process where the V8 engine reverses previously applied JIT optimizations if they become invalid or inefficient.

Common triggers include:

- changes in object structure
- unpredictable data types
- execution of rarely used code paths

After deoptimization, code runs slower but remains correct. This helps V8 balance speed and stability.

</details>

---

<details>
<summary><span>12. Can you <b>measure performance</b> in libuv?</span></summary>
<br />

Yes, although libuv doesn’t expose built-in metrics directly, performance can be assessed indirectly:

- by measuring <b>execution time of async tasks</b> (e.g., `fs`, `crypto`)
- using <b>Event Loop profiling tools</b> like `perf_hooks`, `clinic.js`
- by observing <b>callback delays</b> — increased lag may indicate thread pool overload

You can also increase `UV_THREADPOOL_SIZE` and compare results.

</details>

---

<details>
<summary><span>13. How can you tell if an app is slowing down? Is there a metric to detect inefficient operations?</span></summary>
<br />

Yes — you can monitor <b>event loop lag</b>, which measures delays between Event Loop cycles.

If lag increases, it may indicate:

- blocking operations
- overloaded queues
- inefficient code

Tools for measurement include:

- <code>perf_hooks.monitorEventLoopDelay()</code>
- utilities like <code>clinic.js</code>, <code>node --trace-events</code>

</details>

---

<details>
<summary><span>14. Can Node.js run TypeScript?</span></summary>
<br />

Not directly — Node.js executes only JavaScript.

However, you can use TypeScript with Node.js via:

- <b>transpilation</b> to JavaScript (e.g., using <code>tsc</code> or <code>esbuild</code>)
- <b>runtime wrappers</b> like <code>ts-node</code>, which compile TypeScript on the fly

So Node.js can work with TypeScript, but through an intermediate layer.

</details>

---

<details>
<summary><span>15. How does Node.js <b>execute your code</b>? What happens after JavaScript is passed to Node?</span></summary>
<br />

Once launched, JavaScript code goes through several stages:

1. <b>V8</b> compiles JavaScript into machine code
2. <b>Node.js</b> wraps the code in its module system (CommonJS)
3. <b>Event Loop</b> starts and begins tracking asynchronous events
4. <b>libuv</b> handles system-level operations (I/O, timers, threads)
5. Callback functions are queued and executed when ready

This turns your JS code into an asynchronous, non-blocking application powered by V8, libuv, and the Event Loop.

</details>

---

<details>
<summary><span>16. What’s the difference between <b>CommonJS</b> and <b>ES Modules</b>?</span></summary>
<br />

<b>CommonJS</b> — the legacy module system, default in Node.js:

- Synchronous loading: `require()`
- Export via `module.exports`
- Works only in Node.js
- Executes immediately on import (cached)
- Exports value copies (not live bindings)

<b>ES Modules (ESM)</b> — the modern JavaScript standard:

- Asynchronous loading: `import` / `export`
- Supported in both browsers and Node.js (via flag or `.mjs` extension)
- Enables static analysis and tree-shaking
- Exports live bindings that update when values change

They’re not directly compatible — you can’t use `require()` inside ESM without a wrapper.

</details>

---

<details>
<summary><span>17. What <b>vulnerabilities</b> exist when working with Node.js?</span></summary>
<br />

Node.js applications may be vulnerable to:

- <b>Injection attacks</b> — SQL, NoSQL, shell commands
- <b>XSS</b> — especially in templating and frontend rendering
- <b>Prototype Pollution</b> — modifying object prototypes
- <b>DoS</b> — via blocking operations or large payloads
- <b>Data leaks</b> — due to misconfigured cookies, JWT, CORS
- <b>Dependency vulnerabilities</b> — especially from outdated npm packages

To protect your app:

- use <code>helmet</code>, <code>rate-limiter</code>, <code>validator</code>
- regularly audit dependencies (<code>npm audit</code>)
- avoid blocking code and unsanitized input

</details>

---

<details>
<summary><span>18. What is an <b>AST</b> and what does it do?</span></summary>
<br />

<b>AST</b> (Abstract Syntax Tree) is a hierarchical representation of source code structure.

Its functions include:

- enabling compilers or interpreters to <b>analyze</b> and <b>transform</b> code
- powering <b>optimization</b>, <b>transpilation</b> (e.g., TypeScript to JavaScript), <b>linting</b>, and <b>minification</b>
- helping tools (like Babel, ESLint) understand code at the construct level

AST is the intermediate form between raw source code and machine execution.

</details>

---

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->

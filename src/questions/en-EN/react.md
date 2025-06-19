<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/react.png">
  <h2>React Questions</h2>
</div>
<br />

<details>
<summary><span>1. What is React?</span></summary>
<br />

It’s a JavaScript library for building user interfaces using components and the virtual DOM.

</details>

---

<details>
<summary><span>2. What are the advantages of React?</span></summary>
<br />

- **Component-based approach** — the UI is split into reusable and isolated blocks
- **Virtual DOM** — only the changed parts of the tree are updated, speeding up rendering
- **One-way data flow** — simplifies debugging and makes the app behavior predictable
- **JSX** — a declarative syntax that combines JavaScript and HTML
- **Hooks** — a convenient way to manage state and lifecycle without classes
- **Large ecosystem** — many ready-to-use solutions and libraries (React Router, Redux, etc.)
- **Community support** — tons of learning resources and active developers
- **Great for SPA and SSR** — works on both client and server rendering (e.g. via Next.js)
- **Versatility** — applicable not only for web (React Native for mobile development)

</details>

---

<details>
<summary><span>3. Can you explain about the <b>reconciliation algorithm</b>?</span></summary>
<br />

**Reconciliation in React** is the process of comparing the new and previous Virtual DOM to determine the minimal changes needed in the real DOM.

**Key points:**

- On each re-render, React creates a new Virtual DOM tree.
- The algorithm compares it to the previous tree, computing a _diff_ — the differences between them.
- React uses heuristics:
  - components with different types are treated as different and replaced entirely;
  - list elements require unique `key`s for proper comparison;
  - if the component type is the same — only props and children are compared.

</details>

---

<details>
<summary><span>4. What is the complexity of the reconciliation algorithm?</span></summary>
<br />

_On average_, the complexity is close to **O(n)**, but due to optimizations and heuristics — **it runs faster in practice**, especially with well-structured components and correct `key`s in lists.

</details>

---

<details>
<summary><span>5. <b>Lifecycle phases</b> and methods?</span></summary>
<br />

In React, a component’s lifecycle is divided into **mounting**, **updating**, and **unmounting** — each phase includes specific methods or hooks depending on the component type.

**For class components:**

- `constructor` — initializes state.
- `componentDidMount` — called after the first render.
- `componentDidUpdate` — called after prop or state updates.
- `componentWillUnmount` — cleanup before the component is removed.

**For functional components (with hooks):**

- `useEffect(() => {...}, [])` — similar to `componentDidMount`.
- `useEffect(() => {...}, [deps])` — similar to `componentDidUpdate`.
- Returning a cleanup function `return () => {}` inside `useEffect` — similar to `componentWillUnmount`.

</details>

---

<details>
<summary><span>6. Which version of React introduced hooks?</span></summary>
<br />

Hooks were introduced in **React 16.8**, released in **February 2019**.

</details>

---

<details>
<summary><span>7. What is the <b>Virtual DOM</b>?</span></summary>
<br />

**Virtual DOM** is a lightweight abstraction of the real DOM — essentially a JavaScript-based in-memory tree that React uses to calculate UI changes before applying them to the real DOM.

Instead of changing the DOM directly, React builds a virtual tree, applies changes to it, then compares it to the previous version (**diffing**), and applies only the necessary updates to the browser DOM.

This approach minimizes costly DOM operations and makes UI updates faster and more efficient.

</details>

---

<details>
<summary><span>8. What hooks do you know?</span></summary>
<br />

Most common and widely used:

- `useState` — stores and updates local component state.
- `useEffect` — handles side effects (e.g. requests, timers).
- `useContext` — accesses context value without a Consumer.
- `useRef` — stores mutable values or references to DOM elements.
- `useMemo` — caches computed values for performance.
- `useCallback` — caches functions to avoid unnecessary re-renders.
- `useReducer` — manages complex state using a reducer function.
- `useLayoutEffect` — like `useEffect`, but runs before paint.

</details>

---

<details>
<summary><span>9. What is <b>useState</b> for?</span></summary>
<br />

**`useState`** is a hook for storing and managing local state in functional components.

It preserves a value between renders and provides a way to update it — triggering a re-render when changed.

</details>

---

<details>
<summary><span>10. What is <b>useRef</b> for?</span></summary>
<br />

**`useRef`** returns a mutable object with a `.current` property — allowing you to store values across renders **without** triggering re-renders.

Common use cases:

- accessing DOM elements directly;
- storing values not tied to rendering (timers, previous values, etc.).

Updating `.current` **does not trigger a component re-render**.

</details>

---

<details>
<summary><span>11. What’s the difference between <b>useRef</b> and <b>useState</b>?</span></summary>
<br />

**`useRef`** doesn’t cause a component to re-render when its value changes (stored in `.current`), while **`useState`** does — making `useRef` great for non-visual or transient values.

</details>

---

<details>
<summary><span>12. What is <b>useContext</b> used for?</span></summary>
<br />

**`useContext`** allows you to access shared data (context) inside any component within the matching `<Provider>`, helping to avoid prop drilling.

</details>

---

<details>
<summary><span>13. What are the downsides of <b>useContext</b>?</span></summary>
<br />

**The main downside of `useContext`** is that any change in the context value causes **all** consuming components to re-render, even if they only use part of the context — potentially hurting performance.

</details>

---

<details>
<summary><span>14. What are <b>props</b>?</span></summary>
<br />

**Props** are the mechanism for passing data from a parent component to a child in React, allowing components to be dynamic and reusable.

They are read-only — a child can use them but should not modify them.

</details>

---

<details>
<summary><span>15. What is <b>prop drilling</b>?</span></summary>
<br />

**Prop drilling** is when data is passed through a chain of intermediate components via props, even if only a deeply nested component needs it.

It becomes problematic as it **adds unnecessary complexity** — every level must forward props it doesn’t use, making the code harder to maintain and scale.

</details>

---

<details>
<summary><span>16. What is <b>useEffect</b>?</span></summary>
<br />

**`useEffect`** is a hook that replaces class component lifecycle methods in functional components.

The code inside `useEffect` runs **after the component is mounted**.  
To track changes to specific values, you can pass a dependency array as the second argument.

For cleanup tasks (e.g., unsubscribing, stopping timers), `useEffect` can return a **cleanup function**, which runs **on component unmount** or before the next effect execution.

The behavior of `useEffect` depends on the second argument:

- Without a dependency array — runs **on every render and re-render**;
- With an empty array `[]` — runs **only once** on initial render (mount);
- With specific dependencies `[dep1, dep2]` — runs on initial render and **whenever dependencies change**.

</details>

---

<details>
<summary><span>17. What's the difference between <b>useEffect</b> and <b>useLayoutEffect</b>?</span></summary>
<br />

**`useLayoutEffect`** works almost the same as `useEffect`, with one key difference:  
it runs **synchronously after all DOM mutations**, but **before** the browser paints the updated UI.

Unlike `useEffect`, which is **asynchronous and runs after paint**, `useLayoutEffect` allows effects to finish **before the user sees anything** — e.g., measuring dimensions, positioning, forcing scroll, or running sync animations.

> ⚠️ If code inside `useLayoutEffect` takes too long, it may cause a UI "freeze" as painting is delayed.

</details>

---

<details>
<summary><span>18. What is <b>JSX</b>?</span></summary>
<br />

JSX is a way to write HTML-like markup directly in JavaScript to describe what the UI should look like in React components.

</details>

---

<details>
<summary><span>19. What are <b>logical</b> and <b>presentational</b> components?</span></summary>
<br />

**Presentational components** focus on appearance — they render given data as UI.

**Logical components** handle business logic, state, and data processing, passing everything needed to child presentational components.

</details>

---

<details>
<summary><span>20. What's the difference between <b>controlled</b> and <b>uncontrolled</b> components?</span></summary>
<br />

**Controlled components** manage their state via React: the value (e.g., `input`) is stored in `useState` and updated via events.

**Uncontrolled components** store their state inside the DOM and use `ref` to access values instead of state.

</details>

---

<details>
<summary><span>21. What triggers a component re-render?</span></summary>
<br />

A React component re-renders when:

- Its **state (`state`)** changes;
- New **props (`props`)** are received from the parent;
- The **context (`context`)** it uses changes;
- The **parent component re-renders**, and this component is not optimized (e.g., not wrapped in `React.memo`);
- `forceUpdate` is called (in class components).

</details>

---

<details>
<summary><span>22. What is <b>memoization</b>?</span></summary>
<br />

**Memoization** is an optimization technique where a function’s result is **cached**, so it's not recalculated on repeated calls with the same arguments.

In React, it helps **prevent unnecessary re-renders** and redundant computations — especially with `useMemo`, `useCallback`, or `React.memo`.

</details>

---

<details>
<summary><span>23. How does <b>useMemo</b> work?</span></summary>
<br />

**`useMemo`** is a hook that caches a function’s result and reuses it, so it's not re-executed on every render.

A new computation runs only if dependencies (passed in the array) change.

</details>

---

<details>
<summary><span>24. How does <b>useCallback</b> work?</span></summary>
<br />

**`useCallback`** caches the function itself to avoid recreating it on each render.

A new function is created only if the dependencies in the second argument array change.

</details>

---

<details>
<summary><span>25. Why use <b>React.memo</b>?</span></summary>
<br />

**`React.memo`** allows React to _remember_ a component’s render result so it can **skip re-rendering** if props haven’t changed.

</details>

---

<details>
<summary><span>26. What does React.memo accept as a second argument?</span></summary>
<br />

The second argument to `React.memo` is a comparator function `areEqual(prevProps, nextProps)` that compares old and new props.

By default, it uses **shallow comparison** (`Object.is`). If props contain nested objects, arrays, or other complex structures, you can provide a **custom comparison function** to perform a deep check of necessary fields.

The function should return:

- `true` — if **props are equal** and **re-render is unnecessary**;
- `false` — if **props differ**, and the component needs to re-render.

This gives precise control over when a component updates — useful for performance optimization.

</details>

---

<details>
<summary><span>27. What is a <b>pure component</b>?</span></summary>
<br />

A **pure component** is one that always returns the same output given the same props and doesn't cause side effects.

</details>

---

<details>
<summary><span>28. What is <b>batching</b>?</span></summary>
<br />

**Batching** is a mechanism in React where **multiple state updates are grouped into a single re-render** to reduce extra repaints and boost performance.

Previously, batching only worked inside synthetic events, but since React 18, it’s **enabled by default even in async code** (e.g., `setTimeout`, `fetch`, `Promise`).

</details>

---

<details>
<summary><span>29. What is <b>React Fiber</b>?</span></summary>
<br />

**React Fiber** is the internal engine architecture introduced in React 16, allowing more flexible and efficient rendering.

Fiber splits React's work into small units and processes them step-by-step, which enables:

- prioritizing updates (e.g., based on urgency);
- interrupting long renders and resuming later (for responsive UI);
- using asynchronous rendering features (`Concurrent Mode`).

Thanks to Fiber, React can better manage performance — especially in complex UIs with large data loads.

</details>

---

<details>
<summary><span>30. What is <b>React Fragment</b>?</span></summary>
<br />

**React Fragment** is a special component that lets you group multiple elements **without adding extra nodes to the DOM**.

</details>

---

<details>
<summary><span>31. What's the difference between <b>React.Fragment</b> and <b><></></b>?</span></summary>
<br />

- **`<>...</>`** — short syntax to use when no attributes are needed
- **`<React.Fragment>...</React.Fragment>`** — full form required if `key` or other attributes are needed

</details>

---

<details>
<summary><span>32. Why are <b>keys</b> needed in lists?</span></summary>
<br />

Keys in lists help React efficiently track which elements have changed, been added, or removed — enabling precise updates without re-rendering the entire component tree.

</details>

---

<details>
<summary><span>33. What is <b>conditional rendering</b>?</span></summary>
<br />

**Conditional rendering** is a way to display different UI elements depending on conditions — like whether a user is logged in or if data has loaded.

</details>

---

<details>
<summary><span>34. How to access a DOM element in React?</span></summary>
<br />

In React, you can access a DOM element using **refs** — via `useRef` in functional components or `createRef` in class components.

</details>

---

<details>
<summary><span>35. What <b>new hooks</b> have been introduced in React?</span></summary>
<br />

1. **`useId`** — generates a unique and stable ID, useful for form elements and SSR.
2. **`useTransition`** — lets you mark some updates as "low priority" to improve UI responsiveness.
3. **`useDeferredValue`** — delays updating a value to prevent UI "freezes" during rapid input.
4. **`useSyncExternalStore`** — safe way to subscribe to external stores, works with Concurrent Mode.
5. **`useInsertionEffect`** — runs before DOM paint, intended for styling libraries that inject styles directly.

Also in React 19 experimental (canary) version:

6. **`use`** — allows using Promises and other resources inside components.
7. **`useFormStatus`** — provides real-time form submission state.
8. **`useOptimistic`** — enables optimistic UI updates before async operations complete.

</details>

---

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->

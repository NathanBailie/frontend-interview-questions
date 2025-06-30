<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/vue.png">
  <h2>Vue</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>Vue</b>?</span></summary>
<br />

Vue is a flexible JavaScript framework for building interfaces. It offers reactivity, a convenient component system, and is great for building SPAs.

</details>

---

<details>
<summary><span>2. What is the <b>Virtual DOM</b>?</span></summary>
<br />

The Virtual DOM is a "virtual" representation of the real DOM in memory. Instead of directly modifying the web page, Vue first makes changes in the virtual copy, compares it with the previous version (diffing), and then updates only the changed parts. This makes the interface faster and smoother.

</details>

---

<details>
<summary><span>3. What is the <b>component-based approach</b>?</span></summary>
<br />

The component-based approach is a way of building interfaces by dividing the application into independent and reusable parts—components. Each component is responsible for its part of the UI and logic, making the code more understandable, flexible, and maintainable.

</details>

---

<details>
<summary><span>4. Can you describe the <b>component lifecycle</b>?</span></summary>
<br />

The component lifecycle in Vue can be broken down into several phases:

**1. Initialization**

- `beforeCreate` — before data and events are initialized
- `created` — data and events are already available

**2. Mounting into the DOM**

- `beforeMount` — before the template is inserted into the DOM
- `mounted` — the component is rendered and accessible in the DOM

**3. Updating (when reactive data changes)**

- `beforeUpdate` — before the DOM is updated
- `updated` — after the DOM is updated

**4. Unmounting (component removal)**

- `beforeUnmount` — before removal from the DOM
- `unmounted` — after removal

</details>

---

<details>
<summary><span>5. What is a <b>directive</b>?</span></summary>
<br />

A directive is a special attribute in a Vue template that extends HTML and adds dynamic behavior. It starts with the prefix `v-` (e.g., `v-if`, `v-for`, `v-model`) and links the DOM with the component's logic.

Directives allow you to control rendering, event handling, and much more.

</details>

---

<details>
<summary><span>6. What directives are available?</span></summary>
<br />

There are two groups of directives in Vue:

**Standard directives:**

- `v-if`, `v-else`, `v-else-if` — conditional rendering
- `v-for` — list rendering
- `v-bind` — attribute binding
- `v-model` — two-way data binding
- `v-on` — event handling
- `v-show` — visibility control
- `v-slot` — slot passing
- `v-pre`, `v-cloak`, `v-once` — special template instructions

**Custom directives:**  
You can create your own — for example, `v-focus` to automatically focus an element on load.

</details>

---

<details>
<summary><span>7. What is <b>reactivity</b>?</span></summary>
<br />

Reactivity is Vue's ability to automatically track changes in data and update the interface without manual intervention. When you change a reactive value, Vue "understands" which parts of the DOM need to be re-rendered.

At the core of this system are special reactive wrappers (`ref`, `reactive`) that track changes and trigger component updates when needed.

</details>

---

<details>
<summary><span>8. What is the <b>Composition API</b>?</span></summary>
<br />

The Composition API is a way of organizing component logic in Vue 3. Instead of separating code into options (`data`, `methods`, `computed`), you can group related logic in functions and use reactive primitives (`ref`, `reactive`, `computed`, `watch`) directly within `setup()`.

This makes the code more readable and reusable, especially in large applications.

</details>

---

<details>
<summary><span>9. What is <b>two-way binding</b>?</span></summary>
<br />

Two-way binding means that data and the interface stay in sync in both directions: changes in the model update the DOM, and user input updates the data.

</details>

---

<details>
<summary><span>10. How is two-way binding implemented?</span></summary>
<br />

| Element                 | Event    | Attribute |
| ----------------------- | -------- | --------- |
| `<input>`, `<textarea>` | `input`  | `value`   |
| `checkbox`, `radio`     | `change` | `checked` |
| `<select>` (lists)      | `change` | `value`   |

</details>

---

<details>
<summary><span>11. What are the <b>differences in v-model</b> usage between Vue 2 and Vue 3?</span></summary>
<br />

Vue 2 supports only one `v-model` binding per component. It works with the `value` attribute and listens for the `input` event — that’s how data syncs between parent and child components.

In Vue 3, you can use multiple `v-model`s with different names:

```html
<my-form
	v-model:inputValue="inputValue"
	v-model:visible="isVisible"
	v-model:contract="contractData"
/>
```

</details>

---

<details>
<summary><span>12. How to create a <b>custom directive</b>?</span></summary>
<br />

In Vue 3, custom directives are created using the `app.directive` method. This allows you to add your own logic to interact directly with DOM elements.

**Example: autofocus directive**

1. **Registering the directive:**

```js
app.directive('focus', {
	mounted(el) {
		el.focus();
	},
});
```

2. **Usage in template:**

```html
<input v-focus />
```

</details>

---

<details>
<summary><span>13. Is a root div required in Vue?</span></summary>
<br />

**In Vue 2** — yes, a component template must have **a single root element** (usually a `div`). Returning multiple sibling elements causes an error.

**In Vue 3** — no, you can return **multiple sibling elements** without a wrapper. This feature is called fragment support and simplifies template structure:

```vue
<template>
	<h1>Hello</h1>
	<p>This is a component without a wrapper</p>
</template>
```

</details>

---

<details>
<summary><span>14. What is a <b>slot</b>?</span></summary>
<br />

A `slot` is a special placeholder in a Vue component's template where a parent can insert arbitrary content. This makes the component flexible and reusable.

**Example:**

```vue
<template>
	<div class="card">
		<slot></slot>
	</div>
</template>
```

```vue
<Card>
  <p>This content is passed through the slot</p>
</Card>
```

Here, the `<p>` from the parent appears inside `.card` — exactly where the `<slot>` is placed.

</details>

---

<details>
<summary><span>15. What types of slots are there?</span></summary>
<br />

Vue supports several types of slots for flexible content insertion into components:

**Default (unnamed) slot**  
Used when no specific name is provided:

```vue
<slot></slot>
```

**Named slots**  
Allow you to insert content into specific template regions:

```vue
<slot name="header"></slot>
```

</details>

---

<details>
<summary><span>16. How does <b>conditional rendering</b> work in Vue?</span></summary>
<br />

Conditional rendering in Vue is used to show or hide DOM elements based on specific conditions. The main directives for this are `v-if`, `v-else-if`, and `v-else`.

- `v-if`: renders the element only if the expression is true.
- `v-else-if`: provides an alternative condition if the previous `v-if` was false.
- `v-else`: renders if none of the previous conditions match.

Example:

```html
<p v-if="isLoggedIn">Welcome!</p>
<p v-else>Please log in.</p>
```

</details>

---

<details>
<summary><span>17. What is the difference between <b>v-if</b> and <b>v-show</b>?</span></summary>
<br />

`v-if` fully adds or removes the element from the DOM, while `v-show` only toggles the `display` CSS property.

</details>

---

<details>
<summary><span>18. What is <b>interpolation</b>?</span></summary>
<br />

It's a way to insert data from JavaScript into a template using double curly braces `{{ }}`.

Example:

```html
<p>Hello, {{ username }}!</p>
```

</details>

---

<details>
<summary><span>19. What are <b>modifiers</b>?</span></summary>
<br />

**Modifiers** in Vue are special suffixes added to directives using a dot (`.`) to tweak their default behavior.

They are often used with:

- **`v-on`** (event handling)
- **`v-model`** (two-way data binding)

---

### Examples with `v-on`:

- `v-on:submit.prevent` — prevents default form submission.
- `v-on:click.stop` — stops event bubbling (`stopPropagation`).
- `v-on:keydown.enter` — triggers only on Enter key press.

---

### Examples with `v-model`:

- `v-model.lazy` — updates the data **only on `change`**, not every `input`.
- `v-model.trim` — automatically **trims whitespace** at the start and end.
- `v-model.number` — **casts the input to a number** (if possible).

---

Modifiers help keep your code cleaner and reduce the need for extra event handler logic.

</details>

---

<details>
<summary><span>20. What does the <b>scoped</b> flag do?</span></summary>
<br />

The `scoped` flag is used in Vue component `<style>` tags to **limit CSS rules to only affect the current component**.

For example:

```vue
<style scoped>
h1 {
	color: red;
}
</style>
```

</details>

---

<details>
<summary><span>21. What are <b>reactive and computed properties</b>?</span></summary>
<br />

Vue provides two key types of reactive properties:

---

### Reactive properties

These are regular variables created using `ref()` or `reactive()`, which Vue tracks and updates when their values change.

Example:

```js
<script setup>
import { ref } from 'vue';

const count = ref(0);
</script>

<template>
  <button @click="count++">Clicked {{ count }} times</button>
</template>
```

When `count.value` changes, Vue automatically updates the DOM.

---

### Computed properties

These depend on other reactive values and are **automatically recalculated** when those dependencies change. They're useful for creating derived values that are **cached** until dependencies change.

Example:

```js
<script setup>
import { ref, computed } from 'vue';

const firstName = ref('John');
const lastName = ref('Doe');

const fullName = computed(() => `${firstName.value} ${lastName.value}`);
</script>

<template>
  <p>{{ fullName }}</p>
</template>
```

`fullName` will only be recalculated when `firstName` or `lastName` changes.

---

### Difference:

| Property Type      | Updates Manually | Cached | Used For         |
| ------------------ | ---------------- | ------ | ---------------- |
| `ref` / `reactive` | Yes              | No     | Storing raw data |
| `computed`         | No (automatic)   | Yes    | Derived values   |

</details>

---

<details>
<summary><span>22. <b>How to access a DOM element</b> in Vue?</span></summary>
<br />

In Vue, DOM access is done using a **template ref** via the `ref` directive in the template and `ref()` or `onMounted()` in the script.

---

### Steps:

1. Add `ref="name"` to the desired element in the template.
2. Access it in `<script setup>` or `setup()` via `ref()`.

---

### Composition API:

```vue
<template>
	<input ref="myInput" />
</template>

<script setup>
import { ref, onMounted } from 'vue';

const myInput = ref(null);

onMounted(() => {
	myInput.value.focus();
});
</script>
```

---

### Important:

- `myInput.value` will be `null` until the component is mounted, so access should happen in `onMounted()`.
- This also works for components: if a ref targets a component, `.value` will be the component instance, not the DOM element.

### Options API:

```vue
<template>
	<div ref="box"></div>
</template>

<script>
export default {
	mounted() {
		this.$refs.box.style.background = 'red';
	},
};
</script>
```

</details>

---

<details>
<summary><span>23. How to implement <b>lazy loading</b> of a component or page?</span></summary>
<br />

Lazy loading is done via `defineAsyncComponent` and dynamic imports in `vue-router` routes.

**Using `defineAsyncComponent`:**

```js
import { defineAsyncComponent } from 'vue';

const LazyPage = defineAsyncComponent(() => import('./pages/LazyPage.vue'));
```

**Dynamic import in `vue-router`:**

```js
import { createRouter, createWebHistory } from 'vue-router';

const routes = [
	{
		path: '/about',
		component: () => import('./views/About.vue'),
	},
];

const router = createRouter({
	history: createWebHistory(),
	routes,
});
```

</details>

---

<details>
<summary><span>24. What is <b>keep-alive</b>?</span></summary>
<br />

`<keep-alive>` is a special Vue component that **caches inactive components** and preserves their state when they are re-activated.

When switching between tabs, routes, or components wrapped in `<keep-alive>`, Vue doesn't destroy them but keeps them in memory, saving resources and improving performance.

### Highlights:<br />

- Only works with **dynamic components** (`<component :is="...">`) or `router-view`.
- You can use `include` / `exclude` to filter which components to cache.
- Lifecycle hooks:
  - `activated()` — triggered when the component wakes up.
  - `deactivated()` — triggered when it’s cached.

### Example:

```vue
<keep-alive>
  <component :is="currentTabComponent" />
</keep-alive>
```

### When to use:

- For tabs, modals, form steps, or anything that should retain its state.
- Especially useful in SPAs when switching between pages with form input or user data.

</details>

---

<details>
<summary><span>25. What is a <b>teleport</b>?</span></summary>
<br />

Teleport allows you to **render part of a component’s template elsewhere in the DOM tree**, without breaking component logic. It's especially useful for modals, tooltips, and overlays that need to appear outside of the main `#app` container.

---

### Example:

```vue
<teleport to="body">
  <div class="modal">
    I appear directly inside the <body>!
  </div>
</teleport>
```

Here, `to="body"` means the `<teleport>` content will be inserted inside the `<body>` tag, not within the component's usual DOM hierarchy.

</details>

---

<details>
<summary><span>26. What is the purpose of the <b>key</b> in a <b>v-for</b> loop?</span></summary>
<br />

The `key` attribute in a `v-for` loop helps Vue accurately and efficiently track list elements and maintain their state during DOM updates.

</details>

---

<details>
<summary><span>27. How to <b>force a component to re-render</b> in Vue?</span></summary>
<br />

You can force a Vue component to re-render using `this.$forceUpdate()` (Options API) or by changing the component’s `:key` (Composition API).

</details>

---

<details>
<summary><span>28. What is the purpose of the <b>Watch API</b>?</span></summary>
<br />

The Watch API is used to **react to changes in reactive data** and perform side effects.

- **Vue 2:**

```js
watch: {
  count(newVal) {
    console.log('Count changed:', newVal)
  }
}
```

- **Vue 3:**

```js
watch(count, newVal => {
	console.log('Count changed:', newVal);
});
```

</details>

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->

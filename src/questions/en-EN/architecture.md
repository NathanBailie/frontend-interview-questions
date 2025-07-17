<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/architecture.png">
  <h2>Architecture</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>architecture</b>?</span></summary>
<br />

**Architecture** is a structured approach to building an application, defining how components interact, how data is processed, and ensuring scalability and maintainability.

It can be described as a set of key design decisions made early in the process that are difficult to change later — these decisions set the direction for the entire system.

</details>

---

<details>
<summary><span>2. What are the main problems that architecture should solve?</span></summary>
<br />

Architecture should reduce coupling — minimizing dependencies between parts of the system — while managing cohesion, ensuring logical grouping of related elements. This allows the system to be flexible, scalable, and easily extendable.

Architecture also addresses separation of concerns, manageability, testability, and resilience to changes.

</details>

---

<details>
<summary><span>3. What are the <b>quality attributes of architecture</b>?</span></summary>
<br />

Key quality attributes of architecture include:

- **Readability** — facilitates understanding of code structure and logic.
- **Reusability** — allows components to be reused without duplication.
- **Loose coupling and high cohesion** — minimize dependencies and increase robustness to changes.
- **Flexibility** — simplifies adapting architecture to changing business requirements.
- **Reliability** — achieved through testing, reviews, and error handling.
- **Maintainability** — enables effective development and fixes.
- **Testability** — simplifies writing and executing tests.

</details>

---

<details>
<summary><span>4. Why is it worth thinking about architecture?</span></summary>
<br />

Good architecture helps build a system that's easier to scale, maintain, and adapt to new requirements. It ensures resilience to changes and simplifies teamwork.

Without architectural foundation, a project can quickly spiral into chaos: changes become risky, progress slows down, and maintenance requires increasing effort.

</details>

---

<details>  
<summary><span>5. What <b>principles</b> and <b>development methodologies</b> do you know?</span></summary>  
<br />

- **DRY (Don’t Repeat Yourself)** — avoid duplicating code and logic by extracting reusable units.
- **KISS (Keep It Simple, Stupid)** — simplicity is more important than cleverness; solutions should be clear and concise.
- **SOC (Separation of Concerns)** — each part of the system should handle its own task.
- **FF (Fail Fast)** — the sooner a system reports an error, the easier it is to catch and fix.
- **YAGNI (You Ain’t Gonna Need It)** — don’t implement what isn’t currently needed.
- **SOLID** — a methodology for building reliable and extendable OOP code, based on five principles (Single Responsibility, Open/Closed, etc.).
- **TDD (Test-Driven Development)** — development through testing: write tests first, then code to satisfy them.
- **TDA (Test-Driven Architecture)** — architecture is designed with testability in mind, often paired with TDD.
- **DDD (Domain-Driven Design)** — designing around the domain, where architecture reflects business logic.

These approaches help create code that is easier to scale, maintain, and adapt.

</details>

---

<details>
<summary><span>6. Explain the <b>SOLID</b> principles?</span></summary>
<br />

- **S — Single Responsibility Principle (SRP)**: each module should be responsible for only one part of functionality, within one domain.
- **O — Open/Closed Principle (OCP)**: code should be open for extension but closed for modification.
- **L — Liskov Substitution Principle (LSP)**: subclasses should fully substitute base classes without violating logic.
- **I — Interface Segregation Principle (ISP)**: avoid forcing an object to implement interfaces it doesn’t need.
- **D — Dependency Inversion Principle (DIP)**: dependencies should be based on abstractions, not concrete implementations.

</details>

---

<details>  
<summary><span>7. What is <b>clean architecture</b>?</span></summary>  
<br />

**Clean architecture** is an approach to system design where business logic is separated from infrastructure, UI, and other external layers. It is built around independent layers with dependencies directed inward — toward the application core.

**Key ideas:**

- At the center: business rules — entities and use cases.
- Outer layers (UI, databases, frameworks) are easily replaceable.
- Communication between layers is done through abstractions (interfaces), applying dependency inversion.

This approach makes the project flexible, easy to test, and resilient to external changes.

</details>

---

<details>
<summary><span>8. What makes up <b>Atomic Architecture</b>?</span></summary>
<br />

Atomic architecture is a UI component organization approach based on Atomic Design principles. It divides the interface into abstraction levels:

- **Atoms** — basic elements: buttons, inputs, icons.
- **Molecules** — simple compositions of atoms, e.g., a login form.
- **Organisms** — more complex blocks made of molecules and atoms, e.g., a header.
- **Templates** — page layouts with placed organisms.
- **Pages** — specific implementations of templates with actual data.

This approach increases component reusability and simplifies design maintenance.

</details>

---

<details>
<summary><span>9. How is <b>Feature-Sliced Design</b> architecture structured?</span></summary>
<br />

Feature-Sliced Design (FSD) is a frontend architecture approach aimed at scalability and maintainability of large projects. It is based on decomposition by business entities and abstraction levels.

**Main layers:**

- **App** — application configuration and global initialization.
- **Processes** — cross-cutting business processes (e.g., order checkout).
- **Pages** — specific pages connecting UI and business logic.
- **Widgets** — compound blocks combining multiple features and UI elements.
- **Features** — independent business functions (e.g., product filtering).
- **Entities** — models and logic of business entities (e.g., user, product).
- **Shared** — common utilities, components, types, and styles accessible to all layers.

**Key architectural principles:**

- **Separation of logic and UI** within each module: business logic and visual representation are isolated for flexibility and testability.
- **Imports through Public API** — access to external modules is only via a strictly defined public interface (`index.ts`).
- **One-way dependency flow:** imports are allowed from lower to higher layers, but not vice versa. The `shared` layer is the exception — it's accessible to all.

</details>

---

<details>
<summary><span>10. What is declarativity?</span></summary>
<br />

Declarativity is a programming style where the developer describes **what** should be done, rather than **how** it should be executed. Instead of explicit steps, control is handed over to the runtime environment or framework.

Examples:

- In HTML: `<button disabled>` — we don't describe how exactly the button becomes inactive.
- In Vue: `v-if="isVisible"` — we state that the element is displayed under a certain condition, without manually managing the DOM.

This approach simplifies code readability, increases expressiveness, and reduces errors when interacting with low-level details.

</details>

---

<details>
<summary><span>11. Describe the core <b>OOP principles</b></span></summary>
<br />

- **Encapsulation** — hiding internal implementation and exposing a public interface. Data is protected from direct external interference.
- **Inheritance** — creating new classes based on existing ones, reusing logic and extending functionality.
- **Polymorphism** — a common interface for different types of objects. Allows invoking methods without knowing the exact object type.
- **Abstraction** — focusing on the key characteristics of an object while hiding complex details. It emphasizes what’s important, not how it’s implemented.

</details>

---

<details>
<summary><span>12. When should OOP be used?</span></summary>
<br />

Object-Oriented Programming (OOP) is suitable when:

- the system contains many similar entities with shared properties and behavior (e.g., users, products, orders),
- clear modeling of structure and interactions within the application is required,
- the project is large and intended for long-term development,
- code needs to be easily extendable and reusable (through inheritance, interfaces, and abstractions),
- a typed language is used (e.g., TypeScript), where classes simplify auto-completion and enhance safety.

OOP is especially helpful in building complex architectures with rich business logic.

Note: for small utilities and simple scripts, a functional style may be more efficient — it's more concise and easier to maintain.

</details>

---

<details>
<summary><span>13. What is <b>composition</b>?</span></summary>
<br />

Composition is a design principle where object behavior is formed by combining other objects or functions rather than through inheritance. Instead of creating nested hierarchies, components are "assembled" from smaller building blocks.

Advantages of composition:

- More flexible code structure.
- Easy reusability and component swapping.
- Simplified testing and maintenance.

Example: instead of an `AuthUser` class inheriting from `User`, create a `User` object and "attach" authorization logic as a separate module.

</details>

---

<details>
<summary><span>14. When to use composition vs inheritance?</span></summary>
<br />

Choosing between composition and inheritance depends on your goals and the flexibility of the architecture:

**Composition** is preferable when:

- you need flexible and reusable logic blocks,
- behavior should be set dynamically,
- objects consist of independent parts (e.g., a user with different roles).

**Inheritance** is suitable when:

- there is a clear object hierarchy,
- base logic needs to be extended but not changed,
- behavior needs to be reused in subclasses.

💡 Composition is usually favored — it reduces coupling, promotes modular code, and pairs well with modern approaches (like hooks in Vue or React).

</details>

---

<details>
<summary><span>15. Why should inheritance be used cautiously?</span></summary>
<br />

Inheritance can lead to excessive coupling and system fragility. Changes in a base class automatically affect all subclasses, increasing the risk of unexpected bugs. It often causes deep and confusing hierarchies, making maintenance and testing harder.

Additionally:

- Encapsulation may be violated.
- Subclasses become dependent on internal parent logic.
- It's hard to reuse logic without duplication.

💡 In modern applications, **no more than one level of inheritance** is typically used, with a preference for composition — it's more flexible and easier to maintain.

</details>

---

<details>
<summary><span>16. What is the role of the <b>.editorconfig</b> file and why is it important?</span></summary>
<br />

The `.editorconfig` file sets unified code formatting rules for all team members — from indentation and encoding to line endings. It helps maintain consistent style across the project, especially when developers use different editors.

While `.editorconfig` doesn't directly affect architecture, it supports its cleanliness — a unified style improves readability, understanding, and maintainability of code, thereby reducing risks to architectural decisions.

</details>

---

<details>
<summary><span>17. What are <b>pre-commit hooks</b> for?</span></summary>
<br />

Pre-commit hooks are scripts that run automatically before a commit in Git. They help verify and prepare changes before they are stored in the repository.

Why they’re needed:

- Code quality checks (linting, formatting).
- Running tests — to avoid committing bugs.
- Removing temporary or unnecessary files.
- Enforcing team-wide standards.

Though pre-commit hooks don’t directly impact architecture, they **support project stability** and help prevent accidental or harmful code changes.

</details>

---

<details>
<summary><span>18. Should tests run on pre-push or pre-commit?</span></summary>
<br />

Tests are better run on <b>pre-push</b> rather than pre-commit.

Why:

- Pre-commit should be fast — it runs frequently, and long tests can disrupt workflow.
- Pre-push runs less often (only before sending changes to the server), so it’s appropriate to verify that everything truly works.

This approach saves time and preserves code quality.

</details>

---

<details>
<summary><span>19. What is the purpose of building a frontend application and why is a bundler used?</span></summary>
<br />

**Building** is the process of transforming source code into a final version ready to run in the browser. A bundler (such as `Vite`, `Webpack`) helps combine modules, styles, images, and other resources into an optimized package.

**Why it’s needed:**

- **Minification** — removes unnecessary code and reduces file size.
- **Module bundling** — reduces the number of network requests.
- **Syntax transformation** — supports modern technologies: `TypeScript`, `JSX`, `SCSS`.
- **Performance optimization** — compression, caching, lazy loading.
- **Removal of dev code** — excludes tests, logs, and other elements unnecessary in production.
- **Architecture support** — helps organize the project: aliases, proper imports, layer enforcement.

**Building** is more than packaging — it's a key step in delivering a **reliable**, **fast**, and **maintainable** frontend application.

</details>

---

<details>
<summary><span>20. Why is Webpack still actively used, even though faster bundlers exist?</span></summary>
<br />

- **Powerful configuration** — gives fine-grained control over the build process.
- **Deep integration** — many large-scale projects and libraries (especially in enterprise) already use Webpack.
- **Rich ecosystem** — a large number of plugins, loaders, and ready-made solutions.
- **Compatibility with various technologies** — easy to integrate with `TypeScript`, `React`, `Vue`, `SCSS`, and more.
- **Versatility** — suitable for both frontend and backend bundling.
- **Support for Webpack Module Federation** — valuable in complex micro-frontends.

Although modern bundlers are faster and easier to learn, Webpack remains a solid choice for projects with non-standard requirements or complex architectures.

</details>

---

<details>
<summary><span>21. Can a <b>.env</b> file with variables be committed to the repository?</span></summary>
<br />

In most cases, the `.env` file **should not be committed** to the repository, especially if it contains **sensitive data**: tokens, passwords, API keys, and other confidential information.

Leaking keys can lead to system compromise or resource loss.

That’s why the `.env` file should be added to `.gitignore` to prevent it from being included in the repo.

Exceptions are possible if the `.env` file doesn’t contain sensitive data and is used for testing, but even then, it’s best to be cautious.

</details>

---

<details>
<summary><span>22. When is it okay to use a secret key in a .env file?</span></summary>
<br />

A secret key can be used in a `.env` file **if it doesn’t end up in the final application build** and is processed only on the server side. Such variables must not be accessible in the browser or client-side JavaScript.

If the key is used in client code (e.g., in `.env.public`), it should either be encrypted or replaced with intermediary proxy solutions.

</details>

---

<details>
<summary><span>23. What are the <b>programming paradigms</b>?</span></summary>
<br />

Programming paradigms are approaches to organizing code and building application logic. Each paradigm defines its own style of thinking and design.

**Main paradigms:**

- **Imperative** — describes _how_ to achieve a goal using step-by-step instructions. Examples: `JavaScript`, `C`.
- **Procedural** — a subtype of imperative; emphasizes functions and procedures. Examples: `Pascal`, `C`.
- **Declarative** — describes _what_ should be done, not _how_. Examples: `HTML`, `SQL`, templates in `Vue`.
- **Object-Oriented (OOP)** — built around objects with state and behavior. Uses classes, inheritance, and polymorphism.
- **Functional** — emphasizes pure functions, immutability, and composition. Examples: `Haskell`, `Elm`, `Ramda.js`.
- **Event-driven** — behavior is structured around event handling. Often used in UI and async systems.
- **Reactive** — tracks changes in data over time and updates dependent elements automatically (e.g., UI). Examples: `RxJS`, reactivity in `Vue`.
- **Logical** — based on rules and logical inferences instead of explicit instructions. Example: `Prolog`.

Modern languages often support **multi-paradigm** approaches, allowing combinations of styles (e.g., `TypeScript` combines OOP, functional, and reactive paradigms).

</details>

---

<details>
<summary><span>24. How is a framework better than native JavaScript?</span></summary>
<br />

Frameworks simplify development through built-in architecture, reactivity, and tooling that would otherwise require manual implementation in pure JavaScript.

**Benefits of a framework:**

- **DOM optimization** — virtual DOM and reactivity reduce manual operations and improve interface performance.
- **Component extensibility** — instead of inheritance, frameworks use composition and assembly mechanisms for more flexible architecture.
- **Simplified logic** — no need to manually manage state, component connections, or update mechanisms.
- **Convenient interaction APIs** — a declarative approach enables easy lifecycle management, data flow, and UI composition.

A framework is not just about syntax — it’s an **environment with best practices**, architecture, and support, allowing developers to focus on business logic rather than boilerplate.

</details>

---

<details>
<summary><span>25. What key problems does <b>frontend</b> solve?</span></summary>
<br />

Frontend is much more than rendering buttons — it's a system that solves numerous technical challenges to create fast, responsive, and user-friendly interfaces.

**Key problems frontend solves:**

- **DOM optimization** — direct DOM manipulation is resource-intensive. Techniques like virtual DOM, reactivity, and declarative templates boost performance.
- **Routing** — handles displaying different pages and states without reloading (SPA). Modern frameworks offer efficient routing mechanisms.
- **State management** — centralized stores (`store`) allow data synchronization across components (e.g., `Pinia`, `Vuex`, `Redux`).
- **Component communication** — mechanisms like `props`, events, `provide/inject`, `composables` help decouple UI elements.
- **Architecture organization** — frontend defines how to structure projects: by layers, features, separating logic from presentation.
- **User experience (UX)** — animations, responsive feedback, adaptation to devices and user states are handled on the frontend.
- **Async operations and APIs** — frontend fetches data from servers, handles loading states, errors, and real-time updates.

Modern libraries and frameworks help tackle these challenges efficiently, making interfaces not just beautiful but also fast, scalable, and maintainable.

</details>

---

<details>
<summary><span>26. What are the conceptual <b>differences between frontend frameworks</b>?</span></summary>
<br />

Frontend frameworks (`Vue`, `React`, `Angular`, `Svelte`, `Solid`) solve similar problems: UI rendering, state management, routing, reactivity, etc.  
But they approach these differently — with distinct architectures, philosophies, and developer experiences.

**Key conceptual differences:**

- **Architectural style**

  - `Vue` — declarative templates + `Composition API`, flexible architecture. FSD fits naturally.
  - `React` — functional style via `JSX`; logic and markup are unified; architecture is flexible and handcrafted.
  - `Angular` — strict structure: MVC, DI (dependency injection), annotations and modules; enterprise-focused.
  - `Svelte` — compiler-based, no virtual DOM, minimal abstraction.
  - `Solid` — fine-grained reactivity, top-tier performance, JSX like React but without a virtual DOM.

- **Template–logic connection**

  - `Vue` — separates template and logic (`template`, `script`, `style`).
  - `React` — merges logic and markup using `JSX`.
  - `Angular` — uses separate HTML templates and `TypeScript` classes.
  - `Svelte` — resembles `Vue` structurally but is compiled.
  - `Solid` — logic written in `JSX`, React-like, but with low-level reactivity.

- **State and reactivity**

  - `Vue` — built-in reactivity via `ref`, `reactive`.
  - `React` — hook-based (`useState`, `useEffect`), full component re-renders.
  - `Angular` — imperative with optional `RxJS`.
  - `Svelte / Solid` — variable-level reactivity, no full component re-renders.

- **Component communication**

  - `Vue` — `props`, events, `provide/inject`, `composables`.
  - `React` — `props`, `context`, custom hooks.
  - `Angular` — `@Input`, `@Output`, services.
  - `Svelte / Solid` — `props`, contexts, functions, reactive variables.

- **Typing and structure**

  - `Vue` — flexible; TypeScript optional.
  - `React` — full TypeScript support.
  - `Angular` — strictly typed; TypeScript required.
  - `Svelte` — TypeScript supported, but flexible.
  - `Solid` — TypeScript-focused; strongly typed APIs.

- **Bundle size and performance**

  - `Svelte / Solid` — small bundles, high performance via compilation.
  - `Vue / React` — moderate size, good optimization.
  - `Angular` — heaviest, but highly scalable for large teams and apps.

- **Maturity and community**
  - `React / Vue / Angular` — mature with large communities and ecosystems.
  - `Svelte / Solid` — newer, rapidly evolving, performance-focused.

---

💡 **Summary**: All frameworks solve the same core problems (UI, state, interaction), but in their own way. The choice depends on:

- project requirements,
- team size,
- architecture preference (strict vs flexible),
- performance and typing needs.

</details>

---

<details>
<summary><span>27. When does it make sense to use a prebuilt template from a UI library?</span></summary>
<br />

UI templates from libraries are useful when you need to build interfaces quickly with minimal effort on design, layout, and component testing.

**It makes sense to use templates when:**

- **Speed is critical** — templates help bootstrap interfaces without custom styling.
- **Project doesn’t require unique design** — ideal for admin panels, MVPs, dashboards, or internal tools.
- **Visual consistency matters** — templates ensure a unified style and behavior across components.
- **Components are logic-heavy** — tables with pagination, forms with validation, modals, selects — these are easier to use prebuilt.
- **Small team or no designer** — the library handles the visual aspect.

**You should avoid templates when:**

- Custom UI is needed to reflect brand and design precisely.
- The library pulls in heavy dependencies or bloats the bundle.
- Customizing the template is harder and slower than building from scratch.

💡 **Compromise strategy** — use the library as a foundation, customizing only what's crucial for UX and visual identity.

</details>

---

<details>
<summary><span>28. What is a <b>pattern</b>?</span></summary>
<br />

A **pattern** is a common, well-established solution to a frequently encountered problem or architectural situation. It’s not a specific piece of code, but an **abstract model** or concept that can be adapted to various languages and projects.

</details>

---

<details>
<summary><span>29. Briefly describe popular <b>GoF</b> patterns</span></summary>
<br />

**Creational patterns:**

- **Singleton** — ensures that a class has only one instance and provides global access to it.
- **Factory Method** — creates objects via an interface, hiding the concrete classes being instantiated.
- **Builder** — step-by-step construction of complex objects with various configurations.
- **Abstract Factory** — creates families of related objects without specifying their concrete classes.

**Structural patterns:**

- **Adapter** — allows using incompatible interfaces by wrapping one in another.
- **Facade** — offers a simplified interface to a complex system, hiding its inner workings.
- **Decorator** — adds new behavior to an object without modifying its structure.
- **Proxy** — a stand-in object that controls access to another (e.g., caching, logging, protection).
- **Composite** — lets you treat tree-like object structures as a single entity.

**Behavioral patterns:**

- **Observer** — notifies subscribed objects about changes in a subject’s state.
- **Mediator** — centralizes communication between objects, reducing their interdependencies.
- **Strategy** — defines a family of algorithms and allows switching them at runtime.
- **Iterator** — provides a uniform way to traverse collections without revealing their internal structure.
- **Command** — encapsulates an action and its parameters, enabling deferred execution, logging, or undo functionality.

💡 These patterns are described in the book _Design Patterns: Elements of Reusable Object-Oriented Software_ by the "Gang of Four" (GoF) and are still widely used in architecture, API, and UI design.

</details>

---

<details>
<summary><span>30. What is <b>coverage</b> and why is it needed in a project?</span></summary>
<br />

**Coverage** is a metric that shows how much of the source code is executed during test runs. It's expressed as a percentage and helps evaluate how thoroughly an application’s logic is tested.

**Coverage indicates:**

- Coverage of functions, conditions, branches (`if/else`), loops, and specific lines.
- Which parts of the code were actually executed during testing.
- Where "gaps" remain — logic that hasn’t been tested.

**Why coverage matters:**

- Helps assess test reliability and find missing cases.
- Facilitates refactoring — shows which sections are protected by tests.
- Raises quality standards — allows setting a minimum threshold (e.g., 80%).

💡 Note: **High coverage doesn’t guarantee test quality**, but lack of coverage almost always signals risk.

</details>

---

<details>
<summary><span>31. What is <b>dependency injection</b>?</span></summary>
<br />

**Dependency Injection (DI)** is a pattern where an object receives its dependencies (other objects, services, etc.) from the outside rather than creating them itself.

**Why DI is useful:**

- **Separation of concerns** — the object doesn’t manage its dependencies, it simply uses them.
- **Testability** — dependencies can be easily replaced with mocks or stubs.
- **Flexibility and scalability** — changing dependency implementations doesn’t require modifying core code.
- **Inversion of Control (IoC)** — object creation is delegated to an external system.

**Example (pseudocode):**

```ts
// Without DI — object creates its own dependency
class UserService {
	constructor() {
		this.api = new ApiClient();
	}
}

// With DI — dependency is passed from outside
class UserService {
	constructor(apiClient) {
		this.api = apiClient;
	}
}
```

</details>

---

<details>
<summary><span>32. What are <b>dynamic imports of components</b> for?</span></summary>
<br />

**Dynamic imports** allow components to be loaded only when needed, rather than during initial application load. They are crucial for optimizing performance and managing bundle size.

**Reasons to use dynamic imports:**

- **Lazy-loading** — components load on demand (e.g., when navigating to a page), reducing the size of the initial request.
- **Code-splitting** — breaks the app into independent chunks that load separately.
- **Lower client load** — unused components don’t consume resources until necessary.
- **Faster initial render** — only critical code loads immediately; the rest loads later.

**Examples:**
**Vue 3:**

```js
const ProfilePage = defineAsyncComponent(() => import('@/pages/Profile.vue'));
```

**React:**

```js
export const SettingsPage = lazy(() => import('./SettingsPage'));
```

</details>

---

<details>
<summary><span>33. What is a <b>template method</b>?</span></summary>
<br />

A **Template Method** is a behavioral design pattern that defines the overall sequence of steps in an algorithm while leaving some details for subclasses to implement. It sets the structure, allowing specific steps to be overridden.

**Why it’s used:**

- Ensures **control over the algorithm**, while customizing only necessary parts.
- Eliminates **duplication** — shared logic lives in a base class.
- Promotes **extensibility** without breaking architecture.

**Example:**

```ts
abstract class Page {
	render() {
		this.renderHeader();
		this.renderContent();
		this.renderFooter();
	}

	protected abstract renderContent(): void;

	private renderHeader() {
		console.log('Header');
	}

	private renderFooter() {
		console.log('Footer');
	}
}

class HomePage extends Page {
	protected renderContent() {
		console.log('Home content');
	}
}
```

💡 `Page.render()` is the template method. Header and Footer are fixed; Content is customizable.

Bottom line: the template method lays out the “skeleton” of behavior, letting you vary selected steps without altering the whole algorithm.

</details>

---

<details>
<summary><span>34. What is <b>SSR</b> (Server-Side Rendering) used for?</span></summary>
<br />

**SSR (Server-Side Rendering)** is a technique where the HTML page is generated on the server rather than in the browser. Instead of sending an empty HTML shell and rendering it with JavaScript, the client receives fully formed HTML.

**Why SSR is used:**

- **Faster initial page display** — browser receives content immediately, no JS wait.
- **Better SEO** — search engines index content more effectively when it's part of the initial HTML.
- **Reduced client load** — helpful for low-powered devices or slow connections.
- **Improved accessibility and UX** — content loads faster, layout appears more stable.

**Used in:**

- Marketing websites and landing pages.
- Blogs, articles, e-commerce platforms.
- When fast delivery of content to search engines and social previews matters.

💡 SSR can be combined with SPA — this is called **hybrid rendering**, seen in `Nuxt`, `Next.js`, `SvelteKit`.

</details>

---

<details>
<summary><span>35. What are the <b>disadvantages of SSR</b>?</span></summary>
<br />

Despite SSR’s benefits (fast initial render, SEO, UX), it has **notable drawbacks** worth considering when choosing an architecture.

**Disadvantages of SSR:**

- **Server load** — every request requires HTML generation on the server, increasing pressure under heavy traffic.
- **Infrastructure complexity** — requires a server or serverless platform for rendering, complicating deployment and scaling.
- **Slower response time** — if the server is overloaded or the network is unstable, SSR may lag behind SPA.
- **Reduced interactivity** — hydration (activating JS after HTML arrives) can delay interactions.
- **Debugging and development complexity** — SSR demands environment awareness (`window`, `document` may be unavailable), adding code challenges.
- **Caching intricacies** — improper cache setup can result in frequent unnecessary re-rendering.

💡 SSR works great for public pages, blogs, e-commerce — but may be overkill for internal SPAs or admin panels.

</details>

<!-- <details>
<summary><span></span></summary>
<br />

</details>

--- -->

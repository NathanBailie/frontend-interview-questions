<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/ts.png">
  <h2>TypeScript Questions</h2>
</div>
<br />

<details>
<summary><span>1. What is TypeScript?</span></summary>
<br />

**TypeScript** is a superset of JavaScript that adds support for static typing.

</details>

---

<details>
<summary><span>2. What are the advantages of TypeScript?</span></summary>
<br />

- Static typing helps catch errors during development
- Improves code readability and maintainability
- Provides better IDE support (autocomplete, refactoring)
- Enables safer refactoring of large projects
- Simplifies code documentation through types
- Enhances team collaboration with explicit contracts
- Backward compatibility with JavaScript
- Support for modern ECMAScript features
- Allows gradual adoption in a project

</details>

---

<details>
<summary><span>3. What are the disadvantages of TypeScript?</span></summary>
<br />

- Requires compilation to JavaScript — adds a build step
- Typing takes extra time — code is written more slowly
- Higher entry threshold, especially for beginners
- Code becomes larger — due to type declarations
- Requires additional tools — compiler, configs, etc.
- Not all libraries are well typed — possible issues
- Complex types can be confusing — especially with overuse
- Types don't guarantee safety — can be bypassed via `any`

</details>

---

<details>
<summary><span>4. What data types exist in TypeScript?</span></summary>
<br />

Here's a brief structure of data types in **TypeScript**:

1. **Primitive types**  
   – string  
   – number  
   – boolean  
   – bigint  
   – symbol  
   – null  
   – undefined

2. **Special types**  
   – any  
   – unknown  
   – never  
   – void

3. **Composite types**  
   – interfaces (`interface`)  
   – type aliases (`type`)

4. **Union and Intersection types**  
   – union (`|`)  
   – intersection (`&`)

5. **Literal types**  
   – string literals  
   – number literals  
   – boolean literals  
   – template literals  
   – combined literals

6. **Generic types**

Let me know if you’d like this formatted with examples or styled as a cheatsheet.

</details>

---

<details>
<summary><span>5. What is the optional property modifier used for?</span></summary>
<br />

The optional property modifier (`?`) indicates that an object property may be omitted. It's useful when certain fields are optional.

</details>

---

<details>
<summary><span>6. What are the drawbacks of the `any` type?</span></summary>
<br />

1. Disables type checking — errors may occur at runtime
2. Reduces code safety and reliability
3. Hinders refactoring and autocomplete — IDE loses type info
4. Hurts readability — expected data becomes unclear
5. Masks actual type problems
6. Reduces long-term maintainability — code becomes harder to support

</details>

---

<details>
<summary><span>7. When is the `unknown` type used?</span></summary>
<br />

`unknown` is a safer alternative to `any`, used when the data type is not known in advance and needs to be checked before use.

</details>

---

<details>
<summary><span>8. What does the `void` type do?</span></summary>
<br />

The `void` type is used to indicate that a function does not return a value.

</details>

---

<details>
<summary><span>9. What is the `never` type used for?</span></summary>
<br />

The `never` type is used to indicate values that never occur.

For example:

1. In functions that never complete normally — e.g., they throw an error or run infinitely
2. In exhaustive checks — like in `switch-case` to ensure all types are handled
3. In conditional types with `infer` — for extracting, excluding, or validating types based on structure

</details>

---

<details>
<summary><span>10. What is type narrowing?</span></summary>
<br />

It’s the process of refining an unknown or union type to a more specific type based on conditions in the code.

</details>

---

<details>
<summary><span>11. What are the ways to narrow a type?</span></summary>
<br />

1. `typeof` — check primitive types
2. `in` — check property existence in an object
3. `instanceof` — check class instance
4. User-defined type guards — functions using `is`
5. Discriminated unions — via unique property
6. Null and undefined checks
7. Truthy/falsy checks — to exclude falsy values
8. Literal comparison

</details>

---

<details>
<summary><span>12. What is the purpose of the <b>as const</b> utility?</span></summary>
<br />

The `as const` utility is used to convert a value into an **immutable literal type**, making all its properties `readonly`.

```ts
const status = {
	success: 'SUCCESS',
	error: 'ERROR',
} as const;
```

</details>

---

<details>
<summary><span>13. What are a supertype and a subtype?</span></summary>
<br />

**Supertype** — a more general type that encompasses a set of values and may include more specific types.

**Subtype** — a more specific version of a supertype, compatible with it and usable where the supertype is expected.

Simply put:

> **A subtype can be used where a supertype is expected, but not vice versa.**

For example, `string` is a subtype of `string | number` because it fits within the broader union.

</details>

---

<details>
<summary><span>14. What is a generic?</span></summary>
<br />

**Generic** — a parameterized type that allows writing code that works with different data types while maintaining type safety.

</details>

---

<details>
<summary><span>15. How to constrain a generic?</span></summary>
<br />

Generics can be constrained using the `extends` keyword, which specifies that a type parameter must be a subtype of a given type.

</details>

---

<details>
<summary><span>16. What are conditional types?</span></summary>
<br />

These are types defined based on a condition: they take one type if true and another if false.

They follow the pattern `A extends B ? X : Y`, where the result depends on whether `A` matches `B`.

</details>

---

<details>
<summary><span>17. What is the benefit of conditional types?</span></summary>
<br />

1. **Type flexibility** — dynamically define types based on others
2. **Type safety** — improve control over types through conditions
3. **Simplifies complex logic** — express complex type structures more clearly than unions
4. **Create utility types** — many built-in utility types in TypeScript rely on conditionals
5. **Type validation** — verify and branch behavior within the type system

</details>

---

<details>
<summary><span>18. What are type guards?</span></summary>
<br />

<strong>Type guards</strong> are constructs in TypeScript that allow you to determine the exact type of a variable at runtime and narrow its type within a code block, ensuring safe interaction with data.

</details>

---

<details>
<summary><span>19. What is type conversion?</span></summary>
<br />

<strong>Type conversion</strong> is the process of converting a value from one type to another so it can be used in the appropriate context.

In TypeScript, it can be:

- <strong>Implicit</strong> — TypeScript automatically converts the type, for example:

  ```ts
  const num = '5' as any;
  const doubled = num * 2; // num became a number
  ```

- <strong>Explicit (type assertion)</strong> — you manually specify the type to convert to:
  ```ts
  const value = input as string;
  ```

</details>

---

<details>
<summary><span>20. What is type assertion?</span></summary>
<br />

<strong>Type assertion</strong> in TypeScript is a way to <em>explicitly cast a value to a desired type</em> when you’re sure you know its type better than the compiler does.

Example of type assertion using <code>as</code>:

```ts
const someValue: unknown = 'Hello, TypeScript';

const strLength = (someValue as string).length;

console.log(strLength); // 17
```

</details>

---

<details>
<summary><span>21. Why is type assertion potentially unsafe?</span></summary>
<br />

Using <code>as</code> in TypeScript can be unsafe because it forcibly assigns a type without checking whether the value actually matches it — which can lead to runtime errors. This approach disables the type safety that TypeScript is designed to provide.

</details>

---

<details>
<summary><span>22. When is it appropriate to use <b>as</b>?</span></summary>
<br />

Using <code>as</code> is acceptable when:

1. <strong>You know the value’s type for sure</strong>, and TypeScript can’t infer it:

   ```ts
   const input = document.getElementById('email') as HTMLInputElement;
   input.value = 'example@example.com';
   ```

2. <strong>You’re working with <code>unknown</code> or <code>any</code></strong>, and have manually verified the type:

   ```ts
   function handle(value: unknown) {
   	if (typeof value === 'string') {
   		const length = (value as string).length;
   	}
   }
   ```

3. <strong>After <code>JSON.parse</code> or external data</strong>, when only you know the structure:

   ```ts
   const user = JSON.parse(data) as User;
   ```

4. <strong>When coercing incompatible types via <code>unknown</code></strong>:
   ```ts
   const point = { x: 1, y: 2 } as unknown as [number, number];
   ```

</details>

---

<details>
<summary><span>23. What’s the difference between <b>as</b> and <b>satisfies</b>?</span></summary>
<br />

<strong><code>as</code> — Type assertion:</strong>

- Explicitly tells the compiler the value’s type.
- Doesn’t check actual type conformance.
- Strips excess properties and <strong>can lose precise types</strong>.
- Used when:
  - you’re hinting the type to the compiler;
  - working with <code>unknown</code> or <code>any</code>;
  - coercing incompatible types with <code>as unknown as</code>.

---

<strong><code>satisfies</code> — Type constraint checking:</strong>

- Verifies whether an object conforms to a given type.
- <strong>Preserves precise types and extra fields</strong>.
- Doesn’t cast the value — only checks it at compile time.
- Used when:
  - you need to ensure type compatibility without losing specificity;
  - you want to retain narrow types (e.g., <code>readonly</code>, <code>const</code>);
  - working with object literals or configuration values.

</details>

---

<details>
<summary><span>24. What does the <b>keyof</b> operator do?</span></summary>
<br />

The <code>keyof</code> operator in TypeScript returns the set of keys of a given object type as a union of string literals.

</details>

---

<details>
<summary><span>25. What does the <b>typeof</b> operator do?</span></summary>
<br />

The <code>typeof</code> operator in TypeScript returns a string that indicates the type of a primitive value, or is used in type contexts to obtain the type of a variable.

</details>

---

<details>
<summary><span>26. What does the <b>optional chaining operator</b> (?.) do?</span></summary>
<br />

The optional chaining operator <code>?.</code> allows safe access to properties or methods on an object that might be <code>null</code> or <code>undefined</code> without throwing an error.

</details>

---

<details>
<summary><span>27. What does the <b>non-null assertion operator (!)</b> do?</span></summary>
<br />

The <code>!</code> (non-null assertion) operator in TypeScript tells the compiler that a value is <strong>definitely not <code>null</code> or <code>undefined</code></strong> and lets you access its properties without type-checking errors.

</details>

---

<details>
<summary><span>28. What is <b>enum</b>?</span></summary>
<br />

`enum` in TypeScript is a way to define a set of named constants, which are automatically assigned numeric or string values.

</details>

---

<details>
<summary><span>29. What are the problems with <b>enum</b>?</span></summary>
<br />

- Implicit behavior during compilation — generates extra JS code.
- Doesn’t work well with `const` context — lacks strict typing like `as const`.
- Can cause issues when comparing string values (especially in serialization).
- Doesn’t always support value autocompletion.
- Integrates poorly with modern tools (`const enum` requires special settings).

💡 Alternative — use `as const` with objects or string literals.

</details>

---

<details>
<summary><span>30. What's the difference between <b>enum</b> and an <b>object</b>?</span></summary>
<br />

**`enum`** and plain objects in TypeScript differ in behavior, purpose, and compilation result:

- **`enum`**:

  - creates a special structure with named values (number or string);
  - supports **reverse mapping** (only for numeric enums);
  - generates **extra JavaScript code** (runtime object);
  - can be used as a type, but **doesn’t always protect against assigning arbitrary values**;
  - good for use cases where runtime values matter.

- **object (`as const`)**:

  - simpler and generates no extra JS code;
  - compatible with `as const` for **strict literal typing**;
  - does not support reverse mapping;
  - ideal for configs, API constants, and serialization;
  - allows **enumeration of values** via `keyof typeof`.

💡 If you need simplicity, type safety, and type-level usage — prefer `as const` objects. If runtime values are needed — `enum` is acceptable.

</details>

---

<details>
<summary><span>31. Difference between <b>type</b> and <b>interface</b>?</span></summary>
<br />

- **`interface`**:

  - primarily for describing object and class structures;
  - supports extension via `extends` and implementation via `implements`;
  - supports **declaration merging** — interfaces with the same name merge automatically;
  - preferred when modeling a public API of an object or class.

- **`type`**:

  - creates aliases for **any types**: primitives, unions (`|`), intersections (`&`), tuples, functions, etc.;
  - doesn’t support name-based merging;
  - more flexible and powerful for complex type manipulations.

💡 In modern TypeScript, they are largely interchangeable. Use `interface` for objects and classes; use `type` for more general or complex structures.

</details>

---

<details>
<summary><span>32. What is structural typing?</span></summary>
<br />

**Structural typing** is a principle where types are considered compatible if their **structure matches**, regardless of type or interface names.

In TypeScript, this means an object fits an interface if it has **all the required properties with correct types**, even without explicitly implementing it. This resembles the concept of _duck typing_:
**"If it looks like a type and acts like a type — it is that type."**

</details>

---

<details>
<summary><span>33. Why think of types as <b>sets</b>?</span></summary>
<br />

In TypeScript, it’s helpful to think of types as **sets of possible values**, making type operations easier to reason about:

- **union** (`|`) — joins sets of values;
- **intersection** (`&`) — creates a set common to both types;
- **inheritance** (`extends`) — acts like a subset relationship;
- **`never`** — represents an empty set.

This mindset helps to intuitively reason about types, compatibility, and transformations.
💡 Thinking in sets makes the type system more predictable, logical, and useful for designing complex types.

</details>

---

<details>
<summary><span>34. What are <b>mapped types</b>?</span></summary>
<br />

**Mapped types** let you create new types based on existing ones by iterating over keys using `in` and transforming each property according to a pattern.

For example:

```ts
type Readonly<T> = {
	readonly [K in keyof T]: T[K];
};
```

</details>

---

<details>
<summary><span>35. What utility types do you know?</span></summary>
<br />

- `Partial<T>` — makes all properties optional.
- `Required<T>` — makes all properties required.
- `Readonly<T>` — makes all properties read-only.
- `Pick<T, K>` — selects specified properties from a type.
- `Omit<T, K>` — excludes specified properties from a type.
- `Exclude<T, U>` — removes types from `T` that are assignable to `U`.
- `Extract<T, U>` — extracts types from `T` that are assignable to `U`.
- `Record<K, T>` — creates an object with keys `K` and values of type `T`.
- `NonNullable<T>` — removes `null` and `undefined` from a type.
- `ReturnType<T>` — gets the return type of a function.
- `Parameters<T>` — gets the parameter types of a function as a tuple.
- `Awaited<T>` — extracts the type from a `Promise` (or nested `Promise`).

</details>

---

<details>
<summary><span>36. What is <b>asserts</b>?</span></summary>
<br />

`asserts` is a keyword in TypeScript used in function signatures to indicate that if the function completes without error, a certain type condition is assumed to be true.

Such a function is called an **assertion function** and helps narrow types manually.
Example:

```ts
function assertIsString(value: unknown): asserts value is string {
	if (typeof value !== 'string') {
		throw new Error('Not a string');
	}
}
```

After calling `assertIsString(value)`, the compiler will treat `value` as a string.

</details>

---

<details>
<summary><span>37. What is function overloading?</span></summary>
<br />

**Function overloading** is the ability to declare multiple function signatures with the same name but different parameter types and/or counts, allowing TypeScript to pick the correct version based on the arguments provided.

Implementation is a single function body handling all cases.

Example:

```ts
function parse(input: string): number;
function parse(input: number): string;
function parse(input: any): any {
	if (typeof input === 'string') {
		return Number(input);
	}
	if (typeof input === 'number') {
		return String(input);
	}
}
```

</details>

---

<details>
<summary><span>37. What is <b>infer</b> used for?</span></summary><br />

The <code>infer</code> keyword is used in TypeScript’s conditional types to infer a type from the structure of another type.

It enables dynamically extracting nested types and reusing them.

Examples:

```ts
// Extract function parameter types
type Params<T> = T extends (...args: infer A) => any ? A : never;
// Result: [x: number, y: number]
type ExampleParams = Params<(x: number, y: number) => void>;

// Extract function return type
type Return<T> = T extends (...args: any[]) => infer R ? R : never;
// Result: string
type ExampleReturn = ReturnF<() => string>;
```

</details>

---

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->

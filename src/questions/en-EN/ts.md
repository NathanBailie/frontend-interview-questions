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

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->

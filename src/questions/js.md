<a href="../../README.md">← Back</a>

<div align="center">
  <h2 style="display: flex; align-items: center; justify-content: center; gap: 8px;">
    <img src="../assets/icons/icons-for-titles/js.png" style="vertical-align: middle;">
    JavaScript Questions
  </h2>
</div>

<details>
<summary><span>What is JavaScript?</span></summary>
<br />

JavaScript is a high-level, interpreted programming language used to create dynamic and interactive elements on web pages

</details>

---

<details>
<summary><span>Why do we use JS specifically for working with browsers?</span></summary>
<br />

- Only language supported by all browsers without plugins
- Dynamic content updates without page reloads
- Async capabilities with AJAX, Fetch API and Promises
- Flexible for both simple animations and complex web apps
- Rich ecosystem of libraries and frameworks
- Direct DOM manipulation and styling

</details>

---

<details>
<summary><span>What are the data types in JavaScript?</span></summary>
<br />

JavaScript has 8 data types: 7 primitive types and 1 object type.

**Primitive types (non-object):**

1. **Number** – for all numbers (integers and floats)
2. **String** – sequences of characters
3. **Boolean** – `true` or `false`
4. **Null** – special value representing "nothing" or "empty"
5. **Undefined** – variable declared but not assigned
6. **Symbol** – unique and immutable value, mostly for object keys
7. **BigInt** – for large integers beyond `Number.MAX_SAFE_INTEGER`

**Object type:**

8. **Object** – includes arrays, functions, dates, regexes, maps, sets, and custom objects.

</details>

---

<details>
<summary><span>What is the difference between null and undefined?</span></summary>
<br />

Both **null** and **undefined** represent "nothing" or absence of value, but they are used differently:

- **undefined** is automatically assigned by JavaScript to variables that are declared but not initialized
- **null** is a data type that programmer explicitly assigns to indicate an intentional absence of value

</details>

---

<details>
<summary><span>What are the ways to declare variables in JavaScript?</span></summary>
<br />

`var`:

- Function scope
- Can be reassigned
- Can be redeclared
- Has hoisting but value is undefined before initialization
- Implicit initialization is available

`let`:

- Block scope
- Can be reassigned
- Redeclaration leads to error
- No hoisting, reference error when called before initialization (temporal dead zone)
- Implicit initialization is available

`const`:

- Block scope
- Cannot be reassigned but object properties can be modified
- Redeclaration leads to error
- No hoisting, reference error when called before initialization (temporal dead zone)
- Implicit initialization leads to error

Undeclared variable:

- Global scope (if strict mode is not enabled)
- Can be reassigned without restrictions (x = 10; x = 20;)
- No explicit declaration (x = 5; instead of let x = 5;)
- Has hoisting but can lead to errors in strict mode
- Implicit initialization is possible but unpredictable (y; will create ReferenceError in strict mode)

</details>

---

<details>
<summary><span>What is scope in JavaScript?</span></summary>
<br />

Scope in JavaScript is the visibility and accessibility of variables, functions, and objects within the code. It determines where a variable can be referenced during program execution.

</details>

---

<details>
<summary><span>What types of scope exist in JavaScript?</span></summary>
<br />

- **Global Scope**: Variables declared outside any function or block are globally accessible throughout the code
- **Function/Local Scope**: Variables declared inside a function are only accessible within that function
- **Block Scope**: Variables declared with let and const are only accessible within the block they are declared in (like if statements or loops)
- **Lexical/Static Scope**: Inner functions have access to variables in their outer scope
- **Module Scope**: Variables declared in a module are only accessible within that module unless explicitly exported

</details>

---

<details>
<summary><span>What function creation methods do you know?</span></summary>
<br />

- **Function Declaration**

```javascript
function greet() {}
```

- **Function Expression**

```javascript
const greet = function () {};
```

- **Arrow Function**

```javascript
const greet = () => {};
```

- **Method in an object**

```javascript
const obj = {
	greet() {},
};
```

- **Method in an class**

```javascript
class Greeter {
	greet() {}
}
```

- **Function Constructor**

```javascript
const greet = new Function();
```

</details>

---

<details>
<summary><span>What is Function Declaration?</span></summary>
<br />

It is a way to declare a function in JavaScript using the `function` keyword.
Such a function can be called before its definition due to the hoisting mechanism.

Main features:

- Available anywhere in the code after declaration, even if called - before it
- Its name is mandatory
- Does not require assignment to a variable, unlike Function Expression

</details>

---

<details>
<summary><span>What is Function Expression?</span></summary>
<br />

It is a way to declare a function in JavaScript where the function is created within an expression and can be assigned to a variable. Unlike Function Declaration, it is not hoisted, so it can only be called after its declaration.

Main features:

- Anonymous functions (without a name) can be used
- The function cannot be called before its declaration; otherwise, an error will occur
- Convenient for passing into callbacks and using in arrow functions

</details>

---

<details>
<summary><span>What is an Arrow Function?</span></summary>
<br />

It is a compact syntax for defining functions in JavaScript

Key features:

- Does not have its own `this`, it takes the value from the outer context
- Does not have its own `arguments` object
- Cannot be used as a **constructor** (cannot be called with `new`)
- Does not have `super` or `new.target` properties
- Short and concise syntax
- Automatically returns the result of an expression if there are no curly braces
- If it takes a single parameter, parentheses around the argument can be omitted
</details>

---

<details>
<summary><span>What is a closure?</span></summary>
<br />

A closure is a mechanism that allows a function to remember a reference to its lexical environment, even if it no longer exists in the main call stack

</details>

---

<details>
<summary><span>What can we use closure for?</span></summary>
<br />

- Preserve state between function calls

```javascript
function debounce(fn, delay) {
	let timerId;
	return (...args) => {
		clearTimeout(timerId);
		timerId = setTimeout(() => fn(...args), delay);
	};
}
```

- Encapsulate data by hiding variables inside a closure, preventing external modification

```javascript
function createCounter(initialValue = 0) {
	let count = initialValue; // private state

	return {
		increment() {
			count++;
		},
		decrement() {
			count--;
		},
		get() {
			return count;
		},
	};
}
```

- Enable functional programming, such as using compose

```javascript
const compose =
	(...funcs) =>
	input =>
		funcs.reduceRight((acc, fn) => fn(acc), input);
```

- Create partially applied functions by fixing some arguments (currying)

```javascript
const add = a => b => a + b;
```

</details>

---

<details>
<summary><span>What does the keyword <b>this</b> do?</span></summary>
<br />

The keyword `this` in JavaScript refers to the execution context of a function that is, the object within which the function was called.

**Important:**

- In a regular function, `this` is determined by the function call location (who called it).
- In an arrow function, `this` is determined by the place where the function was declared and never changes, even when called in a different context.

Examples of `this` usage:

- **Object method -** `this` refers to the object itself where the method was called.
- **Regular function (in strict mode) -** `this` is undefined because the function was called outside the object context.
- **Arrow function -** `this` takes its value from the outer context—where the function was declared, not called.
- **Event handler -** `this` refers to the HTML element where the event occurred (e.g., a button).
- **Constructor function (new) -** `this` refers to the newly created object.
- **Class method -** `this` refers to the class instance on which the method was called.

</details>

---

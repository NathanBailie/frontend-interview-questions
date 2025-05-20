<a href="../../README.md">← Back</a>

<div align="center">
  <img src="../assets/icons/icons-for-titles/js.png">
  <h2>JS questions</h2>
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

<details>
<summary><span>List the array iteration methods in JavaScript?</span></summary>
<br />

- `map` – creates a new array by applying a function to each element
- `forEach` – executes a provided function once for each array element
- `filter` – creates a new array with elements that pass a given condition
- `reduce` – reduces the array to a single value by applying a function to each element
- `some` – checks if at least one element meets the specified condition
- `every` – checks if all elements meet the specified condition
- `find` – returns the first element that matches the given condition
- `findIndex` – returns the index of the first element that matches the condition
- `sort` – sorts the array elements based on a comparison function
- `reverse` – reverses the order of elements in the array
- `flatMap` – iterates over array elements, applies a callback to each one, creates a new array from the results, and removes one level of nesting from the final array

</details>

---

<details>
<summary><span>Tell about Event Loop?</span></summary>
<br />

**Event Loop** is a mechanism in JavaScript that ensures the correct execution sequence of tasks.

It consists of three key components:

1. **Call Stack** – the execution stack where synchronous code runs (works on the LIFO principle: last in, first out).
2. **Callback Queue** – stores macro tasks (timers, events, etc.) and operates on the FIFO principle.
3. **Web APIs** – browser or environment interfaces that handle asynchronous operations (`setTimeout`, events, etc.).

One cycle of the Event Loop proceeds as follows:

1. All synchronous code in the Call Stack is executed
2. All microtasks are processed
3. One macro task from the queue is executed

The cycle repeats as long as there are pending tasks.

Event Loop enables JavaScript's asynchronous nature, allowing operations with unknown execution times (such as server requests) to run without blocking the main code execution thread.

</details>

---

<details>
<summary><span>What belongs to microtasks?</span></summary>
<br />

- **Promise** - methods `.then()`, `.catch()`, `.finally()`
- **queueMicrotask()** - explicit invocation of a microtask
- **MutationObserver** - observing changes in the DOM

</details>

---

<details>
<summary><span>What observers exist in JavaScript?</span></summary>
<br />

1. **MutationObserver** – monitors changes in the DOM
2. **IntersectionObserver** – tracks when an element enters or exits in the viewport
3. **ResizeObserver** – observes changes in an element's size
4. **PerformanceObserver** – monitors performance-related events

</details>

---

<details>
<summary><span>What are the ways to work with asynchronous code?</span></summary>
<br />

1. **Callbacks** – a basic approach, but it can lead to "callback hell"
2. **Promises** – a more convenient method for handling asynchronous operations
3. **async/await** – a modern syntax for efficient asynchronous code management

</details>

---

<details>
<summary><span>What is async/await?</span></summary>
<br />

This is a syntax for working with asynchronous code, allowing you to write it as if it were synchronous, simplifying readability and error handling.

- **async** before a function means it always returns a Promise
- **await** forces JavaScript to wait for the Promise to resolve before continuing execution

</details>

---

<details>
<summary><span>What is Promise?</span></summary>
<br />

**Promise** is a syntax for handling asynchronous code.  
The name is reflecting its essence: a promise is an object that guarantees to return the result of an operation in the future
</br></br>

A promise has **three states**:

1. **pending** – waiting (initial state)
2. **fulfilled** – successfully completed
3. **rejected** – failed with an error
   </br></br>

Promises make it convenient to build **chains**:

- `.then()` – executes on successful completion (**fulfilled**)
- `.catch()` – handles errors (**rejected**)
- `.finally()` – runs regardless of the result
  </br></br>

`.then(resolve, reject)` – takes two optional callbacks.

1. **first** – a function called on successful execution (`resolve`)
2. **second** – a function called in case of an error (`reject`)

But errors are usually handled separately with `.catch()`.
</br></br>

**Promise** also has static methods:

- `Promise.all()` – waits for all promises to resolve or for one to reject
- `Promise.allSettled()` – waits for all promises to complete regardless of the result
- `Promise.race()` – returns the result of the first completed promise (success or failure)
- `Promise.any()` – returns the first **successful** result, ignoring errors

</details>

---

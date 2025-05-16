<a href="../../README.md">← Back</a>

<div align="center">
  <h2>📝 JavaScript Questions</h1>
</div>

<details>
<summary><h3 style="display: inline;">What is JavaScript?</h3></summary>
<br />

JavaScript is a high-level, interpreted programming language used to create dynamic and interactive elements on web pages

</details>

---

<details>
<summary><h3 style="display: inline;">Why do we use JS specifically for working with browsers?</h3></summary>
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
<summary><h3 style="display: inline;">What are the data types in JavaScript?</h3></summary>
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
<summary><h3 style="display: inline;">What is the difference between null and undefined?</h3></summary>
<br />

Both **null** and **undefined** represent "nothing" or absence of value, but they are used differently:

- **undefined** is automatically assigned by JavaScript to variables that are declared but not initialized
- **null** is a data type that programmer explicitly assigns to indicate an intentional absence of value

</details>

---

<details>
<summary><h3 style="display: inline;">What are the ways to declare variables in JavaScript?</h3></summary>
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
<summary><h3 style="display: inline;">What is scope in JavaScript?</h3></summary>
<br />

Scope in JavaScript is the visibility and accessibility of variables, functions, and objects within the code. It determines where a variable can be referenced during program execution.

</details>

---

<details>
<summary><h3 style="display: inline;">What types of scope exist in JavaScript?</h3></summary>
<br />

- **Global Scope**: Variables declared outside any function or block are globally accessible throughout the code
- **Function/Local Scope**: Variables declared inside a function are only accessible within that function
- **Block Scope**: Variables declared with let and const are only accessible within the block they are declared in (like if statements or loops)
- **Lexical/Static Scope**: Inner functions have access to variables in their outer scope
- **Module Scope**: Variables declared in a module are only accessible within that module unless explicitly exported

</details>

---

<details>
<summary><h3 style="display: inline;">What is Function Declaration?</h3></summary>
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
<summary><h3 style="display: inline;">What is Function Expression?</h3></summary>
<br />

It is a way to declare a function in JavaScript where the function is created within an expression and can be assigned to a variable. Unlike Function Declaration, it is not hoisted, so it can only be called after its declaration.

Main features:

- Anonymous functions (without a name) can be used
- The function cannot be called before its declaration; otherwise, an error will occur
- Convenient for passing into callbacks and using in arrow functions

</details>

---

<details>
<summary><h3 style="display: inline;">What is a closure?</h3></summary>
<br />

A closure is a mechanism that allows a function to remember a reference to its lexical environment, even if it no longer exists in the main call stack

</details>

---

<details>
<summary><h3 style="display: inline;">What can we use closure for?</h3></summary>
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
<summary><h3 style="display: inline;">What is recursion? Provide examples</h3></summary>
<br />

Recursion is when a function calls itself to solve a problem that can be broken down into smaller repetitive subproblems

Examples:

**Factorial calculation:**

```javascript
const factorial = n => (n === 1 ? 1 : n * factorial(n - 1));
```

**Euclidean algorithm:**

```javascript
const gcd = (a, b) => (b === 0 ? a : gcd(b, a % b));
```

**Quick sort:**

```javascript
function quickSort(array) {
	if (array.length <= 1) return array;
	let less = [],
		equal = [],
		more = [],
		pivot = array[Math.floor(array.length / 2)];

	array.forEach(n =>
		n < pivot ? less.push(n) : n === pivot ? equal.push(n) : more.push(n)
	);

	return [...quickSort(less), ...equal, ...quickSort(more)];
}
```

</details>

---

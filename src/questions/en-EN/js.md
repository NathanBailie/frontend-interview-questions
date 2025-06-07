<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/js.png">
  <h2>JS questions</h2>
</div>
<br />

<details>
<summary><span>1. What is JavaScript?</span></summary>
<br />

JavaScript is a high-level, interpreted programming language used to create dynamic and interactive elements on web pages

</details>

---

<details>
<summary><span>2. Why do we use JS specifically for working with browsers?</span></summary>
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
<summary><span>3. What are the data types in JavaScript?</span></summary>
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
<summary><span>4. What is the difference between null and undefined?</span></summary>
<br />

Both **null** and **undefined** represent "nothing" or absence of value, but they are used differently:

- **undefined** is automatically assigned by JavaScript to variables that are declared but not initialized
- **null** is a data type that programmer explicitly assigns to indicate an intentional absence of value

</details>

---

<details>
<summary><span>5. What are the ways to declare variables in JavaScript?</span></summary>
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
<summary><span>6. What is scope in JavaScript?</span></summary>
<br />

Scope in JavaScript is the visibility and accessibility of variables, functions, and objects within the code. It determines where a variable can be referenced during program execution.

</details>

---

<details>
<summary><span>7. What is Temporal Dead Zone?</span></summary>
<br />

This is the period of time during which a variable exists in the context but cannot be used until it is initialized. This applies to variables declared with `let` and `const`

```javascript
console.log(a); // ❌ ReferenceError (TDZ)
let a = 5;
```

</details>

---

<details>
<summary><span>8. What types of scope exist in JavaScript?</span></summary>
<br />

- **Global Scope**: Variables declared outside any function or block are globally accessible throughout the code
- **Function/Local Scope**: Variables declared inside a function are only accessible within that function
- **Block Scope**: Variables declared with let and const are only accessible within the block they are declared in (like if statements or loops)
- **Lexical/Static Scope**: Inner functions have access to variables in their outer scope
- **Module Scope**: Variables declared in a module are only accessible within that module unless explicitly exported

</details>

---

<details>
<summary><span>9. What function creation methods do you know?</span></summary>
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
<summary><span>10. What is Function Declaration?</span></summary>
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
<summary><span>11. What is Function Expression?</span></summary>
<br />

It is a way to declare a function in JavaScript where the function is created within an expression and can be assigned to a variable. Unlike Function Declaration, it is not hoisted, so it can only be called after its declaration.

Main features:

- Anonymous functions (without a name) can be used
- The function cannot be called before its declaration; otherwise, an error will occur
- Convenient for passing into callbacks and using in arrow functions

</details>

---

<details>
<summary><span>12. What is an Arrow Function?</span></summary>
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
<summary><span>13. What is a closure?</span></summary>
<br />

A closure is a mechanism that allows a function to remember a reference to its lexical environment, even if it no longer exists in the main call stack

</details>

---

<details>
<summary><span>14. What can we use closure for?</span></summary>
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
<summary><span>15. What does the keyword <b>this</b> do?</span></summary>
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
<summary><span>16. List the array iteration methods in JavaScript?</span></summary>
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
<summary><span>17. Tell about Event Loop?</span></summary>
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
<summary><span>18. What belongs to microtasks?</span></summary>
<br />

- **Promise** - methods `.then()`, `.catch()`, `.finally()`
- **queueMicrotask()** - explicit invocation of a microtask
- **MutationObserver** - observing changes in the DOM

</details>

---

<details>
<summary><span>19. What observers exist in JavaScript?</span></summary>
<br />

1. **MutationObserver** – monitors changes in the DOM
2. **IntersectionObserver** – tracks when an element enters or exits in the viewport
3. **ResizeObserver** – observes changes in an element's size
4. **PerformanceObserver** – monitors performance-related events

</details>

---

<details>
<summary><span>20. What are the ways to work with asynchronous code?</span></summary>
<br />

1. **Callbacks** – a basic approach, but it can lead to "callback hell"
2. **Promises** – a more convenient method for handling asynchronous operations
3. **async/await** – a modern syntax for efficient asynchronous code management

</details>

---

<details>
<summary><span>21. What is async/await?</span></summary>
<br />

This is a syntax for working with asynchronous code, allowing you to write it as if it were synchronous, simplifying readability and error handling.

- **async** before a function means it always returns a Promise
- **await** forces JavaScript to wait for the Promise to resolve before continuing execution

</details>

---

<details>
<summary><span>22. What is Promise?</span></summary>
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

<details>
<summary><span>23. What types of operators exist in JavaScript?</span></summary>
<br />

1. **Arithmetic operators**

   - `+` (addition)
   - `-` (subtraction)
   - `*` (multiplication)
   - `/` (division)
   - `%` (remainder)
   - `**` (exponentiation)
   - `++` (increment)
   - `--` (decrement)

2. **Assignment operators**

   - `=` (simple assignment)
   - `+=`, `-=`, `*=`, `/=`, `%=` (combined assignment operators)
   - `**=` (exponentiation assignment)

3. **Comparison operators**

   - `==` (equal, but without type checking)
   - `===` (strict equality, with type checking)
   - `!=` (not equal)
   - `!==` (strict inequality)
   - `>` (greater than)
   - `<` (less than)
   - `>=` (greater than or equal to)
   - `<=` (less than or equal to)

4. **Logical operators**

   - `&&` (logical "and")
   - `||` (logical "or")
   - `!` (logical "not")

5. **Bitwise operators**

   - `&` (bitwise "and")
   - `|` (bitwise "or")
   - `^` (bitwise "xor")
   - `~` (bitwise "not")
   - `<<` (left shift)
   - `>>` (right shift)
   - `>>>` (zero-fill right shift)

6. **Type operator**

   - `typeof` (returns a string indicating the type of a value)

7. **Nullish coalescing operator**

   - `??` (checks if the left operand is `null` or `undefined`. If so, it returns the right operand)

8. **Ternary Operator**

   - `? :` (conditional operator)

9. **String operators**

   - `+` (string concatenation, joining)
   - `+=` (appending to a string)

10. **Other operators**

- `delete` (removes an object's property)
- `in` (checks for the existence of a property in an object)
- `instanceof` (checks if an object belongs to a certain class)
- `await` (used inside `async` functions for handling promises)
- `new` (creates an instance of an object)

</details>

---

<details>
<summary><span>24. Which logical operator has the highest precedence?</span></summary>
<br />

The `!` (logical "NOT") operator has the highest precedence among logical operators in JavaScript

</details>

---

<details>
<summary><span>25. What is the difference between simple and strict comparison operators?</span></summary>
<br />

1. `==`

- Compares two values without considering their type
- Automatically converts data types if necessary
- Can lead to unexpected results due to implicit type conversion  
  <br /><br />

2. `===`

- Compares both value and type without conversion
- Returns `true` only if both operands have the same type and value
- Prevents errors related to implicit type conversions

</details>

---

<details>
<summary><span>26. How do postfix and prefix increment and decrement operators work?</span></summary>
<br />

- **Prefix increment (`++variable`) and decrement (`--variable`)**  
  Increases/decreases the variable's value first, then returns the updated value

- **Postfix increment (`variable++`) and decrement (`variable--`)**  
  Returns the old value first, then increases/decreases the variable

</details>

---

<details>
<summary><span>27. What is short-circuit evaluation in JavaScript?</span></summary>
<br />

This is a feature of the logical operators `&&` and `||`, where an expression **stops execution** as soon as the result is clear.

```js
let x = a || (b && c);
```

If `a` has a **true** value, the expression **resolves** at `a`, and `b && c` **is not evaluated**.

This helps **optimize code** and **avoid unnecessary computations**, especially in `if` conditions or complex logical expressions.

</details>

---

<details>
<summary><span>28. What does the <b>instanceof</b> operator do?</span></summary>
<br />

It is used to check whether an object belongs to a specific constructor or class

```javascript
class Animal {}
let dog = new Animal();

console.log(dog instanceof Animal); // true (dog was created through Animal)
console.log(dog instanceof Object); // true (all objects inherit from Object)
console.log(dog instanceof Array); // false (dog is not an array)
```

</details>

---

<details>
<summary><span>29. Which operator can be used to check if a property exists in an object?</span></summary>
<br />

The `in` operator checks for the existence of a property in an object, including properties inherited from its prototype

```javascript
let obj = { name: 'Alice' };

console.log('name' in obj); // true (the property exists)
console.log('toString' in obj); // true (inherited from Object.prototype)
```

</details>

---

<details>
<summary><span>30. How to check if a property belongs to an object itself, excluding inheritance?</span></summary>
<br />

The `hasOwnProperty()` method allows checking whether a property is an object's own, excluding inherited properties

```javascript
console.log(obj.hasOwnProperty('name')); // true (own property)
console.log(obj.hasOwnProperty('toString')); // false (inherited)
```

</details>

---

<details>
<summary><span>31. What is IIFE?</span></summary>
<br />

An Immediately Invoked Function Expression (**IIFE**) is a function that executes immediately after its definition. It is commonly used to create a local scope and avoid naming conflicts.

Examples of **IIFE**:

```javascript
// Standard syntax
(function () {
	console.log('IIFE executed!');
})();

// Arrow function
(() => {
	console.log('Arrow IIFE');
})();

// Passing a parameter
(name => {
	console.log(`Hello, ${name}!`);
})('Alex');
```

</details>

---

<details>
<summary><span>32. How does the garbage collector work?</span></summary>
<br />

The garbage collector operates based on the concept of **object reachability**.  
An object is considered reachable if it can be accessed via a chain of references starting from so-called **roots**—for example, global objects (`window`, `globalThis`), local variables of the current functions, parameters, variables in closures, etc.

If an object is reachable, it remains in memory. If not, it is considered unreachable and can be removed.

The most commonly used algorithm in JavaScript is called **"Mark-and-Sweep"**:

- **Mark**: The garbage collector traverses all reachable objects starting from the roots and marks them
- **Sweep**: All objects that were not marked are considered unreachable and are removed

</details>

---

<details>
<summary><span>33. <b>Map</b> and <b>Set</b> in JavaScript?</span></summary>
<br />

### **Map** – collection of key-value pairs

- Keys can be **any type** (unlike plain objects, where keys are only strings or symbols)
- **Maintains insertion order**
- **More optimized for property deletion** compared to plain objects
  <br /><br />

**Key methods:**
| Method | Description |
|--------|------------|
| `map.set(key, value)` | Sets a value by key |
| `map.get(key)` | Retrieves a value by key |
| `map.has(key)` | Checks if a key exists |
| `map.delete(key)` | Removes an entry by key |
| `map.clear()` | Clears the entire collection |
| `map.size` | Returns the number of elements |
<br />

### **Set** – collection of unique values

- **Values do not repeat**
- **Maintains insertion order**
- **Allows fast lookup of values**
  <br /><br />

**Key methods:**
| Method | Description |
|--------|------------|
| `set.add(value)` | Adds a value |
| `set.has(value)` | Checks if a value exists |
| `set.delete(value)` | Removes a value |
| `set.clear()` | Clears the entire set |
| `set.size` | Returns the count of unique values |

</details>

---

<details>
<summary><span>34. <b>WeakMap</b> and <b>WeakSet</b> in JavaScript?</span></summary>
<br />

WeakMap and WeakSet are **weakened** versions of Map and Set, designed for handling temporary data. They differ in memory management and garbage collection behavior.

### **WeakMap** – a collection of key-value pairs with special characteristics:

- **Keys can only be objects** (strings, numbers, and other primitives are not allowed)
- **Does not prevent garbage collection** – if an object is no longer used, it gets automatically removed
- **No `.size`, `.keys()`, `.values()`, or `.entries()` methods** – the data cannot be iterated over
  <br /><br />

✅ **Key Methods:**
| Method | Description |
|--------|------------|
| `weakMap.set(obj, value)` | Adds a key-value pair (`object → value`) |
| `weakMap.get(obj)` | Retrieves a value by object |
| `weakMap.has(obj)` | Checks if an object exists in the collection |
| `weakMap.delete(obj)` | Removes an object from the collection |
<br />

🔹 **Usage** – storing data that should be automatically removed, such as caching or metadata binding to objects.

```js
const weakMap = new WeakMap();
let user = { name: 'Nathan' };

weakMap.set(user, 'data');
console.log(weakMap.get(user)); // 'data'

user = null; // Now the object can be garbage collected
```

<br />

### **WeakSet** – a collection of **unique objects**:

- **Can only contain objects** (primitive values are not allowed)
- **Objects are automatically removed** when no longer used
- **No `.size` method or iteration capabilities**
  <br /><br />

✅ **Key Methods:**
| Method | Description |
|--------|------------|
| `weakSet.add(obj)` | Adds an object |
| `weakSet.has(obj)` | Checks if an object exists |
| `weakSet.delete(obj)` | Removes an object |
<br />

🔹 **Usage** – tracking objects without risking memory leaks, such as storing temporary markers for operations.

```js
const weakSet = new WeakSet();
let session = { id: 123 };

weakSet.add(session);
console.log(weakSet.has(session)); // true

session = null; // Now the object can be garbage collected
```

WeakMap and WeakSet are useful when objects should automatically **disappear from the collection** upon losing references, helping prevent **memory leaks**.

</details>

---

<details>
<summary><span>35. Why is the <b>Map</b> collection more optimized for deleting fields than a regular object?
</span></summary>
<br />

Regular objects are initially optimized for a **static structure**—when the set of keys does not change. This allows the V8 engine (in Chrome and Node.js) and other engines to use **hidden classes** and **inline caching** to speed up property access.
<br /><br />

When you use `delete obj.key`, the engine **breaks optimizations** associated with these hidden classes:

- The hidden class is changed
- Property access becomes slower
- The object is no longer considered "simple," reducing performance
  <br /><br />

With `Map`, the situation is different:

- `Map` is **designed** for frequent changes and operations on keys, including deletion
- Deleting keys in `Map` **does not cause de-optimization** in the JavaScript engine
- `Map` **does not have a prototype chain**, so there are no conflicts with inherited properties
- In `Map`, **removal works reliably and efficiently**, even with large amounts of data

</details>

---

<details>
<summary><span>36. What does the keyword <b>new</b> do?</span></summary>
<br />

The `new` keyword is primarily used to create an instance of an object based on a constructor function or class.

Here are the key cases where `new` is used in JavaScript:

1. **Creating objects using constructors** – Allows the creation of object instances:

   ```javascript
   function Person(name) {
   	this.name = name;
   }
   const user = new Person('Nathan');
   ```

2. **Creating built-in object types** – Generates wrapper objects:

   ```javascript
   const num = new Number(42); // an object, not a primitive number
   const str = new String('Hello'); // wrapper object for a string
   const bool = new Boolean(true); // wrapper object for a boolean value
   ```

3. **Creating class instances** – Used to create instances of a `class`:

   ```javascript
   class Car {
   	constructor(model) {
   		this.model = model;
   	}
   }
   const myCar = new Car('Tesla');
   ```

4. **Working with `Map`, `Set`, and `WeakMap`** – Creating collections:

   ```javascript
   const map = new Map();
   const set = new Set();
   const weakMap = new WeakMap();
   ```

5. **Creating objects using `Date`** – Allows working with dates:

   ```javascript
   const now = new Date();
   ```

6. **Using `RegExp` for regular expressions** – Creates a dynamic pattern:

   ```javascript
   const regex = new RegExp('\\d+');
   console.log(regex.test('123')); // true
   ```

7. **Working with `Promise`** – Creates a new promise:

   ```javascript
   const myPromise = new Promise(resolve => resolve('Done!'));
   myPromise.then(console.log); // "Done!"
   ```

8. **Creating `Error` objects** – Used for error handling:
   ```javascript
   const err = new Error('Something went wrong!');
   console.error(err.message);
   ```

</details>

---

<details>
<summary><span>37. What is prototype inheritance?</span></summary>
<br />

It is a mechanism in JavaScript that allows objects to inherit properties and methods from other objects.

Each object in JavaScript has a hidden property `[[Prototype]]`, which points to another object (the prototype). If a property is requested that does not exist in the current object, JavaScript looks for it in the prototype.

</details>

---

<details>
<summary><span>38. How to create an object with a given prototype?</span></summary>
<br />

In JavaScript, an object can be created with a specific prototype using several methods:

### 1. `Object.create(prototype)`

This is the most convenient way to create an object with a specified prototype:

```javascript
const person = {
	greet() {
		console.log('Hello!');
	},
};

const user = Object.create(person);
user.name = 'Nathan';

console.log(user.name); // "Nathan"
user.greet(); // "Hello!" (inherited from person)
```

### 2. Using `__proto__`

You can explicitly set a prototype using `__proto__`, but this method is poorly optimized, deprecated, and **not recommended**:

```javascript
const person = {
	greet() {
		console.log('Hello!');
	},
};

const user = { name: 'Nathan' };
user.__proto__ = person;

user.greet(); // "Hello!"
```

### 3. `Object.setPrototypeOf(obj, prototype)`

A safer way to change an object's prototype after creation:

```javascript
const person = {
	greet() {
		console.log('Hello!');
	},
};

const user = { name: 'Nathan' };
Object.setPrototypeOf(user, person);

user.greet(); // "Hello!"
```

### 4. Using a constructor function and `prototype`

This method is commonly used to create multiple instances:

```javascript
function Person(name) {
	this.name = name;
}

Person.prototype.greet = function () {
	console.log(`Hello, my name is ${this.name}`);
};

const user = new Person('Nathan');
user.greet(); // "Hello, my name is Nathan"
```

</details>

---

<details>
<summary><span>39. How to change an object's prototype after it's created?</span></summary>
<br />

This can be done using the following methods:

- `Object.setPrototypeOf()`
- `__proto__` (not recommended)

</details>

---

<details>
<summary><span>40. How to check if an object is the prototype of another object?</span></summary>
<br />

- **`Object.prototype.isPrototypeOf(obj)`**

  ```javascript
  const person = {};
  const user = Object.create(person);

  console.log(person.isPrototypeOf(user)); // true
  ```

- **`Object.getPrototypeOf()`** - this method returns the prototype of an object, which can be compared directly

  ```javascript
  const person = {};
  const user = Object.create(person);

  console.log(Object.getPrototypeOf(user) === person); // true
  ```

- **`__proto__` (not recommended)**

  ```javascript
  const person = {};
  const user = {};
  user.__proto__ = person;

  console.log(user.__proto__ === person); // true
  ```

</details>

---

<details>
<summary><span>41. What happens if a property is not found in an object or its prototype?</span></summary>
<br />

If a property is not found in an object or its prototype, JavaScript will return `undefined`.

</details>

---

<details>
<summary><span>42. What is the difference between <b>__proto__</b> and <b>prototype</b>?</span></summary>
<br />

### **`__proto__` (deprecated but still used)**

An instance property of an object that points to its prototype. It allows you to get or change the prototype, but **it's not recommended** due to performance issues.

#### **Example:**

```javascript
const person = {
	greet() {
		console.log('Hello!');
	},
};
const user = { name: 'Anton' };
user.__proto__ = person; // Changing the prototype

console.log(user.greet()); // "Hello!" (inherited)
```

---

### **`prototype` (used in constructor functions and classes)**

A property of a constructor function or class that defines the prototype for all objects created with `new`. It allows adding methods that are shared across all instances.

#### **Example:**

```javascript
function Person(name) {
	this.name = name;
}

Person.prototype.sayHello = function () {
	console.log(`Hello, my name is ${this.name}`);
};

const user = new Person('Anton');
user.sayHello(); // "Hello, my name is Anton"
```

</details>

---

<details>
<summary><span>43. How to remove an object's connection to its prototype?</span></summary>
<br />

- `Object.setPrototypeOf(obj, null)` - removes the prototype from an existing object
- `Object.create(null)` - creates an object without a prototype

</details>

---

<details>
<summary><span>44. What are template literals used for?</span></summary>
<br />

This is a convenient way to create strings, allowing you to embed variables and expressions directly into the text.

</details>

---

<details>
<summary><span>45. Which values in JavaScript are considered false?</span></summary>
<br />

- `false` — logical `false`.
- `0`, `-0`, `0n` — all zero variants, including BigInt `0n`.
- `""`, `''`, ```` — empty strings.
- `null` — absence of value.
- `undefined` — undefined value.
- `NaN` — "Not a Number", result of invalid mathematical operations.

</details>

---

<details>
<summary><span>46. What is destructuring?</span></summary>
<br />

**Destructuring** is a convenient way to extract values from objects and arrays and assign them to variables in JavaScript.

### **Examples:**

- **Objects:**
  ```js
  const user = { name: 'Nathan', age: 33 };
  const { name, age } = user;
  console.log(name, age); // "Nathan", 33
  ```
- **Arrays:**
  ```js
  const numbers = [10, 20, 30];
  const [first, second] = numbers;
  console.log(first, second); // 10, 20
  ```

</details>

---

<details>
<summary><span>47. What is a pure function?</span></summary>
<br />

**A pure function** is a function that always returns the same result for the same input and does not modify external state.

</details>

---

<details>
<summary><span>48. What is a higher-order function?</span></summary>
<br />

A higher-order function is a function that takes another function as an argument or returns a function as a result.

</details>

---

<details>
<summary><span>49. How to check if a value is specifically an array?</span></summary>
<br />

1. `Array.isArray()`

   ```js
   console.log(Array.isArray([1, 2, 3])); // true
   console.log(Array.isArray({ a: 1, b: 2 })); // false
   ```

2. `Object.prototype.toString.call(value)`
   ```js
   console.log(Object.prototype.toString.call([1, 2, 3])); // "[object Array]"
   ```

</details>

---

<details>
<summary><span>50. How to check if a value is specifically an object?</span></summary>
<br />

`Object.prototype.toString.call(value)`

```js
console.log(Object.prototype.toString.call({ a: 1 })); // "[object Object]"
```

</details>

---

<details>
<summary><span>51. What are the methods of objects?</span></summary>
<br />

### **Working with keys and values**

- `Object.keys(obj)` — returns an array of object keys.
- `Object.values(obj)` — returns an array of values.
- `Object.entries(obj)` — returns an array of `[key, value]` pairs.

### **Working with properties**

- `Object.assign(target, source)` — copies properties from one object to another.
- `Object.defineProperty(obj, key, descriptor)` — defines a new property with settings (`writable`, `configurable`, `enumerable`).
- `Object.defineProperties(obj, descriptors)` — similar to `defineProperty`, but for multiple properties.

### **Checks and prototypes**

- `Object.hasOwn(obj, key)` — checks if a key exists in the object **(excluding the prototype)**.
- `Object.prototype.hasOwnProperty(key)` — checks whether the object contains a specific property.
- `Object.getPrototypeOf(obj)` — returns the object's prototype.
- `Object.setPrototypeOf(obj, prototype)` — changes the object's prototype.

### **Creating and freezing objects**

- `Object.create(proto)` — creates a new object with the specified prototype.
- `Object.freeze(obj)` — makes an object **immutable** (properties can't be added or removed).
- `Object.seal(obj)` — prevents property deletion but allows modifications to existing properties.

</details>

---

<details>
<summary><span>52. How to bind a function to a context?</span></summary>
<br />

- **call** – invokes a function with the specified context and arguments passed separately
- **apply** – similar to `call`, but arguments are passed as an array
- **bind** – creates a new function with the bound context but does not invoke it immediately
- **arrow functions** – automatically bind `this` to the surrounding context where they are defined

</details>

---

<details>
<summary><span>53. What does the Spread operator do?</span></summary>
<br />

The Spread operator is used to copy or merge both arrays and objects.

Examples:

✅ **Merging arrays**:

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4, 5, 6]
```

✅ **Copying an object**:

```javascript
const person = { name: 'Alice', age: 25 };
const copiedPerson = { ...person };

console.log(copiedPerson); // { name: 'Alice', age: 25 }
```

</details>

---

<details>
<summary><span>54. What does the Rest operator do?</span></summary>
<br />

The Rest operator is used to collect implicitly passed function arguments into an array so they can be easily processed.

This technique is useful when the number of parameters is **unknown in advance**, but they still need to be handled.

### ✅ Example:

```javascript
function logArguments(first, second, ...rest) {
	console.log(`First: ${first}`);
	console.log(`Second: ${second}`);
	console.log(`Rest:`, rest);
}

logArguments(1, 2, 3, 4, 5);
// First: 1
// Second: 2
// Rest: [3, 4, 5]
```

</details>

---

<details>
<summary><span>55. What is <b>event bubbling</b>?</span></summary>
<br />

**Event bubbling** is the process in which an event that occurs on a nested element is first handled on that element and then propagates up the DOM hierarchy, triggering event handlers on its parent elements.

This happens because nested elements are part of their parent containers, and interacting with them affects the entire chain of nesting up to the root element.

</details>

---

<details>
<summary><span>56. What is <b>event capturing</b>?</span></summary>
<br />

**Event capturing** is the phase of event processing that is the opposite of bubbling. In this phase, the event starts propagating from the topmost element of the DOM tree and sequentially moves down the hierarchy to the target element.

By default, event capturing is disabled. To enable it, we need to pass `true` as the third argument in `addEventListener` or use an object `{ capture: true }`.

```javascript
element.addEventListener('click', handler, true);

element.addEventListener('click', handler, { capture: true });
```

</details>

---

<details>
<summary><span>57. How to stop event bubbling?</span></summary>
<br />

To stop event bubbling, call the `event.stopPropagation()` method inside the child element's event handler in `addEventListener`

</details>

---

<!--
<details>
<summary><span></span></summary>
<br />

</details>

--- -->

<!--
как отслеживать и обрабатывать ошибки
что такое дом
шадоу дом
почему мы можем вызывать методы у примитивов
как скопировать объект -->

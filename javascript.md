

# Javascript

JavaScript (JS) is a lightweight interpreted (or just-in-time compiled) programming language with first-class functions.

## 1. Variable 

- `var`: Function-scoped, hoisted, avoid in modern JS.
- `let`: Block-scoped, allows reassignment.
- `const`: Block-scoped, no reassignment (but object properties can change).

## 2. Hoisting 

**Hoisting** is JavaScript's default behavior of moving **declarations** to the top of the current scope (script or function).



### 📌 Key Points

- **Only declarations** are hoisted, not initializations.
- `var` is hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but stay in the **Temporal Dead Zone (TDZ)** — they cannot be accessed before the line of declaration.
- **Function declarations** are fully hoisted (can be used before definition).
- **Function expressions** (including arrow functions) are not hoisted.


### 🔧 Variable Hoisting Example

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ❌ ReferenceError
let b = 10;

console.log(c); // ❌ ReferenceError
const c = 15;
```

## 3. Scope

**Definition**: Scope determines where variables and functions are accessible in your code.

- **Global Scope**: Accessible anywhere in the code.
- **Function Scope**: Created with `function`. Variables are accessible only inside the function.
- **Block Scope**: Created with `{}` and applies to `let` and `const`.

```js
let globalVar = "I'm global";

function testScope() {
  let functionVar = "I'm inside function";

  if (true) {
    let blockVar = "I'm block-scoped";
    console.log(blockVar); // ✅
  }

  // console.log(blockVar); // ❌ ReferenceError
}
```

## 4. Closures

A **closure** is the combination of a function and the **lexical environment** within which that function was declared.

This means the inner function has access to:

- Its own scope
- The outer function’s variables
- The global scope


### 📌 Key Concepts

- Closures are created **every time** a function is created.
- They allow functions to "remember" variables from the outer scope even after the outer function has finished executing.
- Useful for **data privacy**, **function factories**, and **callbacks**.


###  Closure Example

```js
function outer() {
  let count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer();
counter(); // 1
counter(); // 2
counter(); // 3
```

##  5. Context (this)

This refers to the object that is executing the current function.

In the **global scope**, this refers to the global object (window in browsers).

In **object methods**, this refers to the object.

In **arrow functions**, this is lexically bound (inherits from the parent scope).

```js
const obj = {
  name: "Pedro",
  sayHi() {
    console.log(this.name); // Pedro
  },
};

const arrowObj = {
  name: "Maria",
  sayHi: () => {
    console.log(this.name); // undefined (inherits global this)
  },
};
```

## 6. Event Loop

JavaScript is **single-threaded**, meaning it can only execute one operation at a time. The **Event Loop** is what enables asynchronous behavior without blocking the main thread. This loop constantly checks to see if the **call stack** is empty. If it is empty, it takes the first task from the task queue and places it on the call stack for execution.

### 📌  Key Components

- **Call Stack**:This is where synchronous functions are executed. When one function calls another, it is stacked on the stack. If a function performs an asynchronous operation, such as a setTimeout, control is passed to the browser (or the Node.js environment) to handle it asynchronously, while the current function continues executing.
- **Callback Queue (MacroTask Queue)**: Completed asynchronous tasks, such as the results of a request or the time elapsed during a setTimeout, are placed in this queue.
- **Microtask Queue**: There is a special queue for microtasks, which have priority over regular tasks. Promises, for example, use the microtask queue. This ensures that promise operations are executed before regular task queue operations.


>The event loop coordinates the execution of asynchronous code, allowing JavaScript to efficiently handle multiple tasks without blocking the user interface or the execution of the main program.
>
###  How It Works

1. Executes code in the **Call Stack**.
2. When the stack is empty:
   - All tasks in the **Microtask Queue** are executed first.
   - Then one task is picked from the **Callback Queue**.


## ⏳ 7. Promises

A **Promise** represents a value that may be available now, in the future, or never.

### 📌 Promise States

- `pending`: Initial state, neither fulfilled nor rejected.
- `fulfilled`: The operation completed successfully.
- `rejected`: The operation failed.

### 🧪 Example

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("✅ Success!");
  }, 1000);
});

promise.then((result) => {
  console.log(result); // ✅ Success! (after 1 second)
});
```
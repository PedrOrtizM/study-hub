# Guia de Estudio

Guia de estudio para entrevistas de desarrollador Front End enfocado en Angular.

- HTML
- CSS
- JavaScript
- TypeScript
- Angular

## HTML

HTML (HyperText Markup Language) is the most basic building block of the Web. It defines the meaning and structure of web content.

### 🔹 Block Elements

- Start on a **new line** and take up the **full width** available.
- Can contain **other block and inline elements**.
- Common examples:
  - `<div>`
  - `<p>`
  - `<section>`
  - `<header>`
  - `<footer>`
  - `<article>`
  - `<ul>`, `<ol>`, `<li>`
- Used for **structuring** the page layout.

### 🔹 Inline Elements

- Do **not start on a new line**; they flow **within the text**.
- Only take up as much width as their content.
- Can contain **only other inline elements** (no block-level children).
- Common examples:
  - `<span>`
  - `<a>`
  - `<strong>`, `<em>`
  - `<img>`
  - `<label>`

### 🔹 Accessibility (a11y)

Accessibility ensures that web content is usable by everyone, including people with disabilities.

**Key Concepts:**

- **Semantic HTML**: Use elements according to their meaning (`<button>` instead of `<div onclick="">`).
- **Labels**: Always associate `<label>` with form controls using `for` or nesting.
- **Alternative Text**: Use `alt` on `<img>` to describe visual content for screen readers.
- **Keyboard Navigation**: Ensure all interactive elements are reachable via keyboard (use `tabindex`).
- **ARIA**: Use ARIA roles, states, and properties *only when semantic HTML is not sufficient*.

## CSS

### 1. The Box Model

Every HTML element is a box composed of:

- `content`
- `padding`
- `border`
- `margin`

**Box Sizing** By default, the total `size = content + padding + border`. You can change this using `box-sizing:` This makes the total `width/height` include padding and border, which is more intuitive for layout.

Use `box-sizing` to control how the total width and height are calculated:

```css
* {
  box-sizing: border-box;
}
  ```

### Positioning

CSS positioning controls how elements are placed in the layout.

### Position Values

- **`static`**: Default position. The element is placed in the normal document flow.
- **`relative`**: The element is positioned relative to its normal position.
- **`absolute`**: The element is removed from the document flow and positioned relative to the nearest positioned ancestor.
- **`fixed`**: Positioned relative to the viewport and stays in place when scrolling.
- **`sticky`**: Switches between `relative` and `fixed` depending on scroll position.

### Example

```css
.box {
  position: absolute;
  top: 20px;
  left: 0;
}
```

> 🧠 Tip: For `absolute` to work as expected, the parent element must have a position other than `static` (e.g., `relative`).

### 3. Specificity

Specificity determines which CSS rule is applied when multiple rules target the same element.

#### Specificity hierarchy (from lowest to highest)

- Inline styles (e.g., `style="..."`) → **1000**
- IDs (e.g., `#id`) → **100**
- Classes, attributes, pseudo-classes (e.g., `.class`, `[type]`, `:hover`) → **10**
- Elements and pseudo-elements (e.g., `div`, `h1`, `::before`) → **1**

**Example**:

```css
h1 { color: blue; }             /* specificity: 1 */
.title { color: green; }        /* specificity: 10 */
#main-title { color: red; }     /* specificity: 100 */
```

### 4. Cascade

The **cascade** determines which CSS rule takes precedence when multiple rules apply to the same element. It is based on the following order of importance:

1. **Importance**: Rules marked with `!important` override others.
2. **Origin**: Author styles override user and browser default styles.
3. **Specificity**: More specific selectors win over less specific ones.
4. **Order**: If all the above are equal, the last rule defined wins.

### Example

```css
p {
  color: blue;
}

p {
  color: red; /* This will apply because it comes later */
}

p.important {
  color: green !important; /* This will override all */
}
```

**Final color:**

- A `<p>` with class `important` will be green due to `!important`.

- Otherwise, it will be red, as it is the last defined rule.

> Avoid overusing `!important`, as it can make CSS harder to maintain.

### 3. Inheritance

**Inheritance** is the mechanism by which some CSS properties applied to a parent element are passed down to its children.

### Inherited Properties

Not all CSS properties are inherited. By default, **text-related properties** are inherited (e.g., `color`, `font-family`, `line-height`).

### Example

```css
body {
  color: #333;
  font-family: Arial, sans-serif;
}
```

## Pseudo-classes

Pseudo-classes allow you to style elements based on their **state or position** in the DOM. They are written with a single colon `:`.

### Common Pseudo-classes

- `:hover` – styles an element when the mouse is over it
- `:focus` – applies when an element gains focus (e.g., an input)
- `:active` – applies when an element is being clicked
- `:visited` – styles a visited link
- `:first-child` / `:last-child` – targets the first/last child of a parent
- `:nth-child(n)` – targets the nth child
- `:checked` – matches checked inputs like checkboxes or radios
- `:disabled` / `:enabled` – targets form elements based on their state
- `:not(selector)` – targets elements not matching the selector

### Examples

```css
button:hover {
  background-color: #007BFF;
  color: white;
  }
  ```

## Pseudo-elements

Pseudo-elements allow you to **style specific parts of an element** or **inject content**. They are written with a double colon `::`.

### Common Pseudo-elements

- `::before` – inserts content **before** the element’s content
- `::after` – inserts content **after** the element’s content
- `::first-letter` – targets the **first letter** of the element
- `::first-line` – targets the **first line** of the element
- `::placeholder` – styles placeholder text in input fields
- `::selection` – styles the part of text that is selected by the user

### Examples

```css

input::placeholder {
  color: gray;
  font-style: italic;
}

div::before {
  content: "★ ";
  color: gold;
}

div::after {
  content: " ✔";
  color: green;
}
```

## 4. Flexbox

- Layout one-dimensional content (row or column).
- Important properties: `display: flex`, `justify-content`, `align-items`, `flex-grow`, `flex-shrink`.

## 5. CSS Grid

- Two-dimensional layout.
- Key concepts: `grid-template-columns`, `grid-template-rows`, `gap`, `grid-area`.

## 📱 Responsive Design

Responsive Design ensures that your website looks and works well on **all screen sizes**: desktops, tablets, and smartphones.

---

### 🎯 Key Concepts

- **Fluid Layouts**: Use relative units like `%`, `vw`, `vh`, `em`, `rem` instead of fixed `px`.
- **Media Queries**: Apply styles conditionally based on device characteristics (e.g. screen width).
- **Mobile-First**: Start designing for small screens, then add enhancements for larger ones.
- **Flexible Media**: Images and videos scale with the layout (`max-width: 100%`).
- **Viewport Meta Tag**: Ensures proper scaling on mobile devices.

## Javascript

JavaScript (JS) is a lightweight interpreted (or just-in-time compiled) programming language with first-class functions.

## 1. Variable Declarations: `var`, `let`, `const`

- `var`: Function-scoped, hoisted, avoid in modern JS.
- `let`: Block-scoped, allows reassignment.
- `const`: Block-scoped, no reassignment (but object properties can change).

# 🔄 JavaScript Hoisting

**Hoisting** is JavaScript's default behavior of moving **declarations** to the top of the current scope (script or function).

---

## 📌 Key Points

- **Only declarations** are hoisted, not initializations.
- `var` is hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but stay in the **Temporal Dead Zone (TDZ)** — they cannot be accessed before the line of declaration.
- **Function declarations** are fully hoisted (can be used before definition).
- **Function expressions** (including arrow functions) are not hoisted.

---

## 🔧 Variable Hoisting Example

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ❌ ReferenceError
let b = 10;

console.log(c); // ❌ ReferenceError
const c = 15;
```

### 1. Scope

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

# 🔒 JavaScript Closures

A **closure** is the combination of a function and the **lexical environment** within which that function was declared.

This means the inner function has access to:

- Its own scope
- The outer function’s variables
- The global scope

---

## 📌 Key Concepts

- Closures are created **every time** a function is created.
- They allow functions to "remember" variables from the outer scope even after the outer function has finished executing.
- Useful for **data privacy**, **function factories**, and **callbacks**.

---

## 🧠 Closure Example

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

## 🧠 5. Context (this)

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

## 🌀 JavaScript Event Loop

JavaScript is **single-threaded**, meaning it can only execute one operation at a time. The **Event Loop** is what enables asynchronous behavior without blocking the main thread. This loop constantly checks to see if the **call stack** is empty. If it is empty, it takes the first task from the task queue and places it on the call stack for execution.

### 🧱 Key Components

- **Call Stack**:This is where synchronous functions are executed. When one function calls another, it is stacked on the stack. If a function performs an asynchronous operation, such as a setTimeout, control is passed to the browser (or the Node.js environment) to handle it asynchronously, while the current function continues executing.
- **Callback Queue (Task Queue)**: Completed asynchronous tasks, such as the results of a request or the time elapsed during a setTimeout, are placed in this queue.
- **Microtask Queue**: There is a special queue for microtasks, which have priority over regular tasks. Promises, for example, use the microtask queue. This ensures that promise operations are executed before regular task queue operations.
- **Web APIs**: Provided by the browser (e.g., `setTimeout`, `fetch`).

>The event loop coordinates the execution of asynchronous code, allowing JavaScript to efficiently handle multiple tasks without blocking the user interface or the execution of the main program.
>
### 🔁 How It Works

1. Executes code in the **Call Stack**.
2. When the stack is empty:
   - All tasks in the **Microtask Queue** are executed first.
   - Then one task is picked from the **Callback Queue**.

---

## ⏳ Promises

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

## TypeScript

### Interface

Used to define the **shape of an object**.

```ts
interface User {
  id: number;
  name: string;
}
```

**Pros:**

- Can be extended with extends or by re-declaring the same name.
- Preferred for object structures, especially in OOP and public APIs.

### Types

Used to define any type: primitives, unions, intersections, etc.

```ts
type User = {
  id: number;
  name: string;
};

type Status = 'active' | 'inactive';
type ID = number | string;
```

| Feature                | `interface`         | `type`              |
| ---------------------- | ------------------- | ------------------- |
| Extending              | ✅ Yes               | ✅ Yes               |
| Declaration merging    | ✅ Yes               | ❌ No                |
| Unions & intersections | ❌ No (only extends) | ✅ Yes               |
| Use with primitives    | ❌ No                | ✅ Yes               |
| Recommendation         | Use for objects     | Use for flexibility |

# 🅰️ Angular

Angular components go through a lifecycle managed by Angular. You can tap into specific moments of that lifecycle using lifecycle hooks.

## 📌 Lifecycle Hooks

`ngOnInit()`

- Called once after the first `ngOnChanges()`.
- Ideal for initialization logic (e.g. API calls, setting defaults).

`ngOnChanges(changes: SimpleChanges)`

- Called whenever an `@Input()` property changes.
- Receives a SimpleChanges object.

`ngDoCheck()`

- Called during every change detection run.
- Use for custom change detection (advanced use cases).

`ngAfterContentInit()`

- Called once after Angular projects external content into the component.

`ngAfterContentChecked()`

- Called after every check of projected content.

`ngAfterViewInit()`

- Called once after the component's view and child views have been initialized.

### 1. Components

Fundamental UI building blocks.

Each component has:

- A **TypeScript class**
- An **HTML template**
- A **CSS style**
- A **selector**

### 2. Structural Directives

Change the DOM layout.
Examples: `*ngIf`, `*ngFor`, `*ngSwitch`

### 3. Attribute Directives

Change the appearance or behavior of elements.

Example: `ngClass`, `ngStyle`, or `custom directives`.

### 3. Pipes

Transform data in templates.
Angular provides built-in pipes like `date`, `uppercase`, `async`.

You can also create custom pipes.

- **Pure**: efficient, only re-evaluates on input changes.
- **Impure**: always recalculates, watch for performance impact.

### 🧩 Template-Driven Forms

- Defined directly in the HTML using directives (`ngModel`, `#form="ngForm"`).
- **Two-way data binding** with `[(ngModel)]`.
- Suitable for **simple forms**.
- Logic is mostly in the **template**.
- Uses `FormsModule`.

### 📄 Example

```html
<form #form="ngForm" (ngSubmit)="onSubmit(form)">
  <input name="username" ngModel required />
  <button type="submit">Submit</button>
</form>
```

### Reactive Forms Forms

- Defined in the component class using FormControl, FormGroup, and FormBuilder.
- Uses explicit and immutable data structures.
- Ideal for complex, dynamic, or large-scale forms.
- Uses `ReactiveFormsModule`.

Defined in the component class using FormControl, FormGroup, and FormBuilder.

> Use **Template-driven** for simple forms like login, contact forms.

> Use **Reactive form** complex forms with dynamic validations, conditional fields, or large applications.

# 🔄 RxJS Essentials for Angular Senior Developers

## 📌 Core Concepts

- **Observables**: Lazy collections of multiple values over time.
- **Subjects**:
  - `Subject`: Multicast observable.
  - `BehaviorSubject`: Emits last value to new subscribers.
  - `ReplaySubject`: Replays past values.
  - `AsyncSubject`: Emits last value on complete.

## 🔧 Common Operators

- **Creation**: `of`, `from`, `interval`, `timer`.
- **Transformation**: `map`, `pluck`, `scan`.
- **Filtering**: `filter`, `debounceTime`, `distinctUntilChanged`.
- **Flattening**: `mergeMap`, `switchMap`, `concatMap`, `exhaustMap`.
- **Combining**: `combineLatest`, `withLatestFrom`, `forkJoin`, `zip`.
- **Error Handling**: `catchError`, `retry`, `retryWhen`, `throwError`.
- **Utility**: `tap`, `take`, `first`, `takeUntil`, `finalize`.

## 📈 Best Practices

- **Unsubscribe** properly using `takeUntil`, `async` pipe, or `untilDestroyed`.
- Prefer **`async` pipe** in templates to avoid manual subscriptions.
- Use **`switchMap`** for HTTP calls to cancel previous requests.
- Leverage **RxJS Marble Testing** for observables.
- Create custom observable services for shared streams.

---

# 🚀 Performance Optimization in Angular

## 🧠 Change Detection

- Use `ChangeDetectionStrategy.OnPush` for stateless or input-driven components.
- Combine with `async` pipe or **Signals** to reduce re-rendering.

## 🔁 TrackBy in *ngFor

```html
<li *ngFor="let item of list; trackBy: trackById">{{ item.name }}</li>

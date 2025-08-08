## High Order Functions (HOF)

A **High Order Function** is a function that either:

1. Takes one or more functions as arguments, or
2. Returns another function as its result.

This is a powerful feature in JavaScript and other functional programming languages, allowing functions to be more dynamic and reusable.

### Example 1: Passing a function as an argument

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

function processUserInput(callback) {
  const name = "Alice";
  console.log(callback(name));
}

processUserInput(greet); // Output: Hello, Alice!
```
### Why Use High Order Functions?
- Encourages code reuse
- Makes code more declarative
- Enables functional programming patterns like map, filter, reduce

### Common High Order Functions in JavaScript
- `map()`
- `filter()`
- `reduce()`
- `forEach()`
- `sort()`

## Pure Functions

A **Pure Function** is a function that:

1. **Always returns the same output** for the same input.
2. **Does not produce side effects**, such as modifying external variables, changing the DOM, logging to the console, or making API calls.

### Characteristics of Pure Functions

- Deterministic: given the same input, you always get the same output.
- No side effects: it does not change anything outside its scope.

### Example of a Pure Function

```javascript
function add(a, b) {
  return a + b;
}
add(2, 3); // Always returns 5
```


### Example of a Impure Function

```javascript 
let counter = 0;

function increment() {
  counter++;
}
```
In this case, `increment` modifies an external variable (`counter`), so **it's not pure**.


 ## SOLID Principles
 
### 📌 S — Single Responsibility Principle
A class/component should have **one reason to change**.

- Do one thing well.  
- **Example:** Separate data-fetching service from UI component.


### 📌 O — Open/Closed Principle
Software entities should be **open for extension, but closed for modification**.

- Add new behavior without changing existing code.  
- **Example:** Use polymorphism or strategy pattern for multiple form validators.


### 📌 L — Liskov Substitution Principle
Subtypes must be **replaceable** by their base types without breaking the app.

- Child class should honor parent contract.  
- **Example:** Avoid overriding a method in a way that breaks expected output.

### 📌 I — Interface Segregation Principle
Clients should not depend on **interfaces they don't use**.

- Create smaller, focused interfaces.  
- **Example:** Avoid bloated service interfaces; split into specific ones.

### 📌 D — Dependency Inversion Principle
Depend on **abstractions**, not on concrete implementations.

- Use interfaces or tokens for flexibility and testing.  
- **Example:** Inject services using Angular’s DI with `@Inject()` or interfaces.



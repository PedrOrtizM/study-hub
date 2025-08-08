## HTML

**HTML** (HyperText Markup Language) is the most basic building block of the Web. It defines the meaning and structure of web content.

###  📌 Block Elements

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

### 📌  Inline Elements

- Do **not start on a new line**; they flow **within the text**.
- Only take up as much width as their content.
- Can contain **only other inline elements** (no block-level children).
- Common examples:
  - `<span>`
  - `<a>`
  - `<strong>`, 
  - `<em>`
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



### 📄 DOM (Document Object Model)

- A tree-like structure representing the HTML content of a page.
- JavaScript can access and manipulate it using the `document` API.
- Dynamic: updates reflect instantly on the page.


### 🎨 CSSOM (CSS Object Model)

- A tree structure created from CSS files and `<style>` elements.
- Represents all styles associated with the DOM.
- Combined with the DOM to compute the **Render Tree**.



### 🌳 Render Tree

- Built by combining the **DOM** and **CSSOM**.
- Contains only **visible elements** (e.g., no `<head>`).
- Each node has style and layout info needed to paint on screen.


### 🔁 Render Flow

1. **Parse HTML → DOM**
2. **Parse CSS → CSSOM**
3. **DOM + CSSOM → Render Tree**
4. **Layout**: Calculate position & size for each node.
5. **Paint**: Draw pixels to screen.
6. **Composite**: Combine layers into the final image.


### Shadow DOM

- A web standard that allows encapsulation of HTML, CSS, and JS.
- Used in Web Components (e.g., `<video>` uses it).
- Prevents styles/scripts from leaking in or out.
- Example:

### Event Flow Summary 

When you click on an element, the event goes through three phases:


### 🔁 1. Capturing Phase
- Event travels **from `document` down to the target**.
- Listeners with `{ capture: true }` are triggered.
- Example flow: `document → html → body → div → button`


### 🎯 2. Target Phase
- The event reaches the **element you clicked** (e.g., `button`).
- Listeners on the target run.


### 🔼 3. Bubbling Phase
- Event **bubbles up from target to document**.
- Default phase for most events.
- Example flow: `button → div → body → html → document`


### 🧪 Example Scenarios

- **Click on button inside a div**:  
  Target is `button`. Event flows down to it (capture), runs on it (target), and bubbles up (bubbling).

- **Click on the div (outside the button)**:  
  Target is `div`. Same capture and bubbling pattern, but `div` is the target.

> - Use `event.stopPropagation()` to stop the flow.
> - Use `capture: true` to intercept during capturing phase. 




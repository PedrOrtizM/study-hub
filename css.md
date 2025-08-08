
# CSS

## 1. The Box Model

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

## 2. Positioning

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

## 3. Specificity

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

## 4. Cascade

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

## 4. Inheritance

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

## 5. Pseudo-classes

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

## 6. Pseudo-elements

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

## 7. Flexbox

- Layout one-dimensional content (row or column).
- Important properties: `display: flex`, `justify-content`, `align-items`, `flex-grow`, `flex-shrink`.

## 8. CSS Grid

- Two-dimensional layout.
- Key concepts: `grid-template-columns`, `grid-template-rows`, `gap`, `grid-area`.

## 9. 📱 Responsive Design

Responsive Design ensures that your website looks and works well on **all screen sizes**: desktops, tablets, and smartphones.

---

### 🎯 Key Concepts

- **Fluid Layouts**: Use relative units like `%`, `vw`, `vh`, `em`, `rem` instead of fixed `px`.
- **Media Queries**: Apply styles conditionally based on device characteristics (e.g. screen width).
- **Mobile-First**: Start designing for small screens, then add enhancements for larger ones.
- **Flexible Media**: Images and videos scale with the layout (`max-width: 100%`).
- **Viewport Meta Tag**: Ensures proper scaling on mobile devices.

## 10.  BEM: Block Element Modifier

**BEM** is a methodology for writing CSS class names in a clear, predictable, and scalable way. Its goal is to make code **more maintainable** and **less prone to conflicts**.


###  Structure

| Part       | Description                                | Example           |
|------------|--------------------------------------------|-------------------|
| `block`    | A standalone component or logical container | `button`          |
| `element`  | A part of the block that has no meaning on its own | `button__icon`    |
| `modifier` | A variant or extension of a block or element | `button--primary` |

---

###  Real Example

```html
<!-- HTML -->
<button class="button button--primary">
  <span class="button__icon"></span>
  Submit
</button>

```
```CSS
/* CSS */
.button {
  padding: 10px;
  border: none;
}

.button--primary {
  background-color: blue;
  color: white;
}

.button__icon {
  margin-right: 5px;
}
```



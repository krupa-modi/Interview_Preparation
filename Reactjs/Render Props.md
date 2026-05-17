# 📘 Render Props in React

---

# 📌 What is Render Props?

## 🔹 Definition

Render Props is a pattern in React where a component shares data or logic using a function prop.

That function returns JSX.

---

# 📌 Simple Meaning

Instead of hardcoding UI inside a component, we pass a function to decide what should render.

---

# 📌 Syntax

```jsx id="jlwm4d"
<Component render={(data) => <UI />} />
```

or

```jsx id="jlwm9r"
<Component>
  {(data) => <UI />}
</Component>
```

---

# 📌 Why Render Props is Used?

Render Props is used for:

✅ Logic Reusability
✅ Sharing state/behavior between components
✅ Avoiding duplicate code

---

# 📌 What Problem Does Render Props Solve?

---

# 🔥 Problem

Suppose multiple components need same logic.

Example:

* Mouse tracking
* Authentication
* API fetching
* Toggle functionality

Without Render Props:

❌ Same logic repeated in multiple components

---

# ✅ Solution

Move shared logic into one component and pass UI through a function.

This makes logic reusable.

---

# 📌 Example

---

# 🔥 MouseTracker Component

```jsx id="jlwm1v"
class MouseTracker extends React.Component {
  state = {
    x: 0,
    y: 0
  };

  handleMouseMove = (e) => {
    this.setState({
      x: e.clientX,
      y: e.clientY
    });
  };

  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}
```

---

# 🔥 Using Render Props

```jsx id="jlwm5h"
<MouseTracker
  render={({ x, y }) => (
    <h1>
      Mouse Position: {x}, {y}
    </h1>
  )}
/>
```

---

# 📌 How it Works?

---

# ✅ MouseTracker handles logic

* Mouse movement
* State updates

---

# ✅ Parent decides UI

Using:

```jsx id="jlwm7j"
render={({ x, y }) => ...}
```

---

# 📌 Main Benefit

Logic and UI become separate.

---

# 📌 Render Props vs HOC

| Render Props        | HOC                        |
| ------------------- | -------------------------- |
| Uses function prop  | Uses component wrapping    |
| Flexible UI control | Component enhancement      |
| Easier prop sharing | Can create wrapper nesting |

---

# 📌 Modern React

Nowadays many Render Props use cases are replaced with:

# 👉 Custom Hooks

because hooks are simpler.

---

# 📌 Example

Instead of:

```jsx id="jlwm0u"
<MouseTracker render={...} />
```

Modern React often uses:

```jsx id="jlwm8n"
const position = useMousePosition();
```

---

# 🎯 Interview Answers

---

# ❓ What is Render Props?

### ✅ Answer:

Render Props is a React pattern where a component shares logic using a function prop that returns JSX.

---

# ❓ What problem does Render Props solve?

### ✅ Answer:

Render Props solves the problem of code duplication and logic reuse by separating reusable logic from UI rendering.

---

# ❓ Difference Between HOC and Render Props?

### ✅ Answer:

HOC reuses logic by wrapping components, while Render Props reuse logic by passing a function that returns JSX.

---

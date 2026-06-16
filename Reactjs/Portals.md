# 📌 What are Portals?
## 🔹 Definition

Portals in React allow rendering a component outside the normal parent DOM hierarchy.

Using portals, a child component can be rendered into a different DOM node.

---

# 📌 Simple Meaning

Normally React components render inside their parent component.

But with Portals:

✅ Component can render somewhere else in the DOM.

---

# 📌 Why Portals are Used?

Portals are mainly used for:

* Modals
* Popups
* Tooltips
* Dropdowns
* Notifications

where UI should appear outside parent container.

---

# 📌 Problem Without Portals

Suppose a modal is inside a parent having:

```css id="jlwm8y"
overflow: hidden;
```

Then modal may get cut or hidden.

---

# ✅ Solution

Render modal outside parent using Portal.

---

# 📌 Real DOM Structure

---

## Without Portal

```txt id="jlwm0x"
<div id="root">
   <App>
      <Modal />
   </App>
</div>
```

---

## With Portal

```txt id="jlwm3n"
<div id="root"></div>

<div id="portal-root">
   <Modal />
</div>
```

Modal renders in separate DOM node.

---

# 📌 Syntax

React provides:

```jsx id="jlwm6v"
ReactDOM.createPortal()
```

---

# 📌 Syntax Structure

```jsx id="jlwm1m"
ReactDOM.createPortal(
  child,
  container
)
```

---

# 📌 Example

---

# 🔥 index.html

```html id="jlwm5f"
<div id="root"></div>

<div id="portal-root"></div>
```

---

# 🔥 Modal.jsx

```jsx id="jlwm2h"
import ReactDOM from "react-dom";

function Modal() {
  return ReactDOM.createPortal(
    <div>
      <h1>Modal Popup</h1>
    </div>,
    document.getElementById("portal-root")
  );
}

export default Modal;
```

---

# 📌 How it Works?

---

# ✅ React Component Hierarchy

```txt id="jlwm9q"
App
 └── Modal
```

---

# ✅ DOM Hierarchy

```txt id="jlwm4w"
#portal-root
 └── Modal
```

Even though Modal belongs to App component, DOM rendering happens elsewhere.

---

# 📌 Important Point

Portal changes:

✅ DOM placement

BUT NOT:

❌ React component hierarchy

---

# 📌 Event Bubbling Still Works

Even if component renders outside DOM tree:

React event bubbling still works normally.

---

# 📌 Example Use Cases

| Use Case | Why Portal Helps      |
| -------- | --------------------- |
| Modal    | Avoid overflow issues |
| Tooltip  | Render above UI       |
| Dropdown | Avoid clipping        |
| Popup    | Better positioning    |

---

# 📌 Benefits of Portals

✅ Better UI positioning
✅ Avoid CSS overflow problems
✅ Cleaner modal handling
✅ Improved user experience

---

# 📌 Interview Important Point

Portal only changes:

👉 Where component renders in DOM

It does NOT break React parent-child relationship.

---

# 🎯 Interview Answers

---

# ❓ What are Portals in React?

### ✅ Answer:

Portals in React allow rendering components outside the normal parent DOM hierarchy using `ReactDOM.createPortal()`.

---

# ❓ Why are Portals used?

### ✅ Answer:

Portals are used for modals, popups, tooltips, and overlays where components need to render outside the parent container to avoid styling and overflow issues.

---

# ❓ Which method is used to create Portals?

### ✅ Answer:

React uses:

```jsx id="jlwm7t"
ReactDOM.createPortal()
```

to create portals.

---

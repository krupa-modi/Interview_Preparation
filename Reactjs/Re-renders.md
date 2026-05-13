# 📌 How to Prevent Re-renders in React

## 🔹 What is Re-render in React?

A **re-render** happens when a component updates and React runs the component function again to update the UI.

React re-renders when:

* `state` changes
* `props` change
* Parent component re-renders
* Context value changes

---

# 🔥 Why Prevent Unnecessary Re-renders?

Too many unnecessary re-renders can:

* Slow down the application
* Reduce performance
* Make UI laggy
* Cause unnecessary API calls or calculations

That’s why React developers optimize rendering.

---

# ✅ Ways to Prevent Re-renders in React

---

# 1️⃣ Use `React.memo()`

## 📌 Purpose

Prevents a component from re-rendering if props do not change.

---

## ✅ Example

```jsx
import React from "react";

const Child = React.memo(({ name }) => {
  console.log("Child Rendered");

  return <h1>{name}</h1>;
});

export default Child;
```

---

## 📌 How it Works

React compares old props and new props.

If props are same → component will NOT re-render.

---

## ✅ Best Use Case

Use for:

* Reusable UI components
* Large lists
* Expensive rendering components

---

# 2️⃣ Use `useCallback()`

## 📌 Problem

Functions recreate on every render.

This can cause child components to re-render unnecessarily.

---

## ✅ Solution

`useCallback()` memoizes the function.

---

## ✅ Example

```jsx
import React, { useCallback, useState } from "react";

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>

      <Child onClick={handleClick} />
    </>
  );
}
```

---

## 📌 Benefit

Same function reference is reused.

So child component will not re-render unnecessarily.

---

# 3️⃣ Use `useMemo()`

## 📌 Purpose

Memoizes expensive calculations.

---

## ✅ Example

```jsx
import React, { useMemo, useState } from "react";

function App() {
  const [count, setCount] = useState(0);

  const expensiveCalculation = useMemo(() => {
    console.log("Calculating...");
    return count * 2;
  }, [count]);

  return (
    <>
      <h1>{expensiveCalculation}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </>
  );
}
```

---

## 📌 Benefit

Calculation runs only when dependency changes.

---

# 4️⃣ Keep State Local

## ❌ Wrong Practice

Putting all state in parent component.

This causes all child components to re-render.

---

## ✅ Better Practice

Keep state close to where it is needed.

---

## ✅ Example

Instead of:

```jsx
<App>
  <Navbar />
  <Sidebar />
  <Profile />
</App>
```

Keep Profile state inside `Profile` component only.

---

# 5️⃣ Avoid Inline Functions & Objects

## ❌ Bad

```jsx
<Child data={{ name: "Krupa" }} />
```

Every render creates a new object.

---

## ✅ Better

```jsx
const user = { name: "Krupa" };

<Child data={user} />
```

---

# 6️⃣ Use Proper `key` in Lists

## ❌ Wrong

```jsx
{items.map((item, index) => (
  <li key={index}>{item.name}</li>
))}
```

---

## ✅ Correct

```jsx
{items.map((item) => (
  <li key={item.id}>{item.name}</li>
))}
```

---

## 📌 Benefit

Helps React efficiently update only changed items.

---

# 7️⃣ Split Large Components

Large components re-render more often.

Break UI into smaller components.

---

## ✅ Benefit

Only affected components re-render.

---

# 8️⃣ Avoid Unnecessary State Updates

## ❌ Wrong

```jsx
setCount(count);
```

Updating same value still may trigger render checks.

---

## ✅ Better

Update only when value changes.

---

# 🎯 Interview Answer (Short Version)

## ❓ How to Prevent Re-renders in React?

### ✅ Answer:

We can prevent unnecessary re-renders in React by using:

* `React.memo()` for memoizing components
* `useCallback()` for memoizing functions
* `useMemo()` for memoizing expensive calculations
* Keeping state local
* Avoiding inline objects/functions
* Using proper keys in lists
* Splitting large components into smaller ones

This improves application performance and makes React apps faster.

---

---

# 📌 Why React is Fast?

React is fast because it uses:

* Virtual DOM
* Efficient diffing algorithm
* Component-based architecture
* Smart re-rendering

---

# 🔥 1️⃣ Virtual DOM

## 📌 What is Virtual DOM?

Virtual DOM is a lightweight copy of the real DOM.

React first updates the Virtual DOM instead of directly updating the real DOM.

---

## 📌 Process

1. State changes
2. React creates new Virtual DOM
3. React compares old and new Virtual DOM
4. Only changed parts update in real DOM

---

## ✅ Benefit

Direct DOM manipulation is slow.

React minimizes DOM updates, making it faster.

---

# 🔥 2️⃣ Diffing Algorithm

React uses a smart comparison algorithm called:

## 👉 Reconciliation

React compares old and new Virtual DOM trees.

It updates only changed elements.

---

## ✅ Example

If only button text changes:

```jsx
<h1>Hello</h1>
<button>Save</button>
```

React updates only the button.

Not the entire page.

---

# 🔥 3️⃣ Component-Based Architecture

React divides UI into small reusable components.

---

## ✅ Benefit

Only affected components re-render.

Entire application does not reload.

---

# 🔥 4️⃣ One-Way Data Flow

Data flows from parent → child.

This makes updates predictable and easier to optimize.

---

# 🔥 5️⃣ Batch Updates

React batches multiple state updates together.

---

## ✅ Example

```jsx
setCount(1);
setName("Krupa");
```

React may combine them into a single render.

---

# 🔥 6️⃣ React Fiber Architecture

React Fiber improves rendering performance.

It allows:

* Prioritized rendering
* Smooth UI updates
* Better user experience

---

# 🎯 Interview Answer (Short Version)

## ❓ Why React is Fast?

### ✅ Answer:

React is fast because it uses a Virtual DOM instead of directly updating the real DOM.

It compares old and new Virtual DOM using a diffing algorithm and updates only changed parts.

React also uses component-based architecture, batching, and optimized rendering techniques to improve performance.

---

# 📌 Important Interview Keywords

Remember these keywords:

* Virtual DOM
* Reconciliation
* Diffing Algorithm
* React.memo
* useMemo
* useCallback
* Component Re-rendering
* Memoization
* Fiber Architecture

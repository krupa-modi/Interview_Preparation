# Concurrent Rendering in React 18

## What is Concurrent Rendering?

Concurrent Rendering is a new feature introduced in React 18.

It allows React to **prepare multiple UI updates in the background** and **prioritize important updates first**.

React can:
* Pause rendering
* Resume rendering
* Cancel unnecessary rendering
* Keep UI responsive

This improves **performance** and **user experience** in heavy applications.

---

# Simple Interview Definition

> Concurrent Rendering allows React to work on multiple UI updates at the same time and prioritize urgent updates so the app stays fast and responsive.

---

# Why Concurrent Rendering Needed?

Before React 18:

* Rendering was **synchronous**
* Once rendering started, it could not stop
* Heavy UI updates could freeze the screen

React 18 solves this using concurrent rendering.

---

# Real Life Example

Imagine:

* User is typing in a search box
* At same time, a huge list is rendering

Without concurrent rendering:

* Typing becomes slow

With concurrent rendering:

* React prioritizes typing first
* Heavy list rendering happens in background

So UI feels smooth.

---

# Main Features Used with Concurrent Rendering

## 1. useTransition()

Used for **non-urgent updates**.

Urgent updates:

* typing
* button click

Non-urgent:

* filtering large list
* rendering big UI

---

# Easy Example

```jsx
import React, { useState, useTransition } from "react";

function App() {
  const [input, setInput] = useState("");
  const [list, setList] = useState([]);
  const [isPending, startTransition] = useTransition();

  const handleChange = (e) => {
    const value = e.target.value;

    // urgent update
    setInput(value);

    // non-urgent update
    startTransition(() => {
      const items = [];

      for (let i = 0; i < 10000; i++) {
        items.push(value);
      }

      setList(items);
    });
  };

  return (
    <div>
      <input type="text" value={input} onChange={handleChange} />

      {isPending && <p>Loading...</p>}

      {list.map((item, index) => (
        <p key={index}>{item}</p>
      ))}
    </div>
  );
}

export default App;
```

---

# How This Works

```jsx
setInput(value)
```

This is urgent → React updates immediately.

```jsx
startTransition(() => {
   setList(items)
})
```

This is low priority → React can delay it.

Result:

* Input stays smooth
* UI doesn't freeze

---

# Important Interview Points

## Concurrent Rendering does NOT mean multithreading

React still works on single thread.

It only manages rendering smarter using priority scheduling.

---

# Advantages

* Better UI responsiveness
* Faster user experience
* Prevents UI freezing
* Prioritizes important updates
* Improves large applications

---

# Interview Question

## Q: Is Concurrent Rendering enabled manually?

No.

In React 18, when using:

```jsx
createRoot()
```

Concurrent features become available automatically.

Example:

```jsx
import ReactDOM from "react-dom/client";

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<App />);
```

---

# Short Interview Answer

> Concurrent Rendering in React 18 allows React to interrupt and prioritize rendering work. Important updates like typing are rendered first, while heavy UI updates can happen in background using features like useTransition. This keeps applications fast and responsive.

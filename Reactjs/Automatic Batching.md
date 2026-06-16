# Automatic Batching in React (React 18)

## What is Automatic Batching?

Automatic batching means React groups multiple state updates together and does **only one re-render** instead of multiple re-renders.
* agar same state bar bar call kar rahe hai to bhi react 18 ke bad vale main ek hi bar render hoga.

This improves:

* Performance
* Speed
* User Experience

---
# Before React 18

React batched updates only inside:

* React event handlers (`onClick`, `onChange`)

But NOT inside:

* `setTimeout`
* `Promise`
* `fetch`
* async functions

So multiple `setState` calls caused multiple re-renders.

---

# React 18 Automatic Batching

In React 18, batching works everywhere:

* Event handlers
* setTimeout
* Promise
* API calls
* async/await

React combines all updates into a single render automatically.

---

# Simple Interview Definition

> Automatic batching in React 18 is a feature where React groups multiple state updates into a single re-render for better performance.

---

# Example Without Automatic Batching (Old Behavior)

```jsx
import { useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  const [age, setAge] = useState(20);

  const handleClick = () => {
    setTimeout(() => {
      setCount(c => c + 1);
      setAge(a => a + 1);
    }, 1000);
  };

  console.log("Re-render");

  return (
    <button onClick={handleClick}>
      Click
    </button>
  );
}

export default App;
```

## Old React Behavior

* `setCount()` → one render
* `setAge()` → second render

Total = **2 re-renders**

---

# React 18 Automatic Batching Behavior

Same code in React 18:

```jsx
setCount(c => c + 1);
setAge(a => a + 1);
```

React batches both updates together.

## Result

Only **1 re-render**

---

# Real-Life Example

Suppose:

* User clicks button
* You update loading state
* Update user data
* Update notification

Without batching:

* Multiple renders happen

With automatic batching:

* All updates happen together
* Faster UI

---

# Important Interview Point

React 18 automatic batching works when using:

```jsx
createRoot()
```

Example:

```jsx
import ReactDOM from "react-dom/client";

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<App />);
```

---

# When to Avoid Batching?

Sometimes you want immediate UI update.

Then use:

```jsx
flushSync()
```

Example:

```jsx
import { flushSync } from "react-dom";

flushSync(() => {
  setCount(count + 1);
});
```

This forces React to render immediately.

---

# Interview Quick Summary

| Feature                | React 17       | React 18       |
| ---------------------- | -------------- | -------------- |
| Event handler batching | ✅              | ✅              |
| setTimeout batching    | ❌              | ✅              |
| Promise batching       | ❌              | ✅              |
| API call batching      | ❌              | ✅              |
| Performance            | Less optimized | More optimized |

---

# Best 2-Line Interview Answer

> Automatic batching in React 18 groups multiple state updates into a single re-render automatically.
> It improves performance by reducing unnecessary renders.

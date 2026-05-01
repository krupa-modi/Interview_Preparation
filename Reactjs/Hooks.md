
# 🔹 1. useState Hook

## 📌 What is useState?

useState is a React Hook that allows functional components to manage **state (data)**.

👉 Before hooks, only class components had state. Now functional components can also handle state.

---

## 📌 Syntax

```js
const [state, setState] = useState(initialValue);
```

* `state` → current value
* `setState` → function to update state
* `initialValue` → starting value

---

## 📌 Example

```js
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

---

## 📌 Key Points (Interview Important)

* State updates trigger re-render
* useState is asynchronous
* Never mutate state directly
* You can use multiple useState hooks

---

## 📌 Functional Update

```js
setCount(prev => prev + 1);
```

👉 Use when new state depends on previous state

---

## 📌 When to Use?

* Forms
* Counters
* Toggle UI
* Dynamic UI updates

---

# 🔹 2. useEffect Hook

## 📌 What is useEffect?

useEffect is used to handle **side effects** in React.

👉 Side effects = API calls, DOM updates, timers, subscriptions

---

## 📌 Syntax

```js
useEffect(() => {
  // side effect logic
}, [dependencies]);
```

---

## 📌 Example

```js
import React, { useEffect, useState } from "react";

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Component Rendered");
  }, []);

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

---

## 📌 Dependency Array Cases

* `[]` → runs once (on mount)
* `[count]` → runs when count changes
* no dependency → runs on every render

---

## 📌 Cleanup Function

```js
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

👉 Prevents memory leaks

---

## 📌 Key Points

* Runs AFTER render
* Non-blocking
* Used for async operations
* Multiple useEffect allowed

---

# 🔹 3. useLayoutEffect Hook

## 📌 What is useLayoutEffect?

useLayoutEffect is similar to useEffect, but it runs **synchronously BEFORE the browser paints the screen**.

---

## 📌 Syntax

```js
useLayoutEffect(() => {
  // logic
}, [dependencies]);
```

---

## 📌 Example (Execution Order)

```js
import React, { useEffect, useLayoutEffect } from "react";

function LayoutExample() {

  useEffect(() => {
    console.log("run useEffect hook");
  }, []);

  useLayoutEffect(() => {
    console.log("run useLayoutEffect hook");
  }, []);

  return <div>Hello</div>;
}
```

### 📌 Output

```
run useLayoutEffect hook
run useEffect hook
```

---

## 📌 Example (DOM Measurement)

```js
import React, { useLayoutEffect, useRef } from "react";

function LayoutExample() {
  const boxRef = useRef();

  useLayoutEffect(() => {
    console.log(boxRef.current.getBoundingClientRect());
  }, []);

  return <div ref={boxRef}>Hello</div>;
}
```

---

## 📌 Key Points

* Runs BEFORE paint (blocking)
* Used for DOM measurements
* Prevents flickering
* Can impact performance

---

## 📌 When to Use?

* DOM measurement
* Scroll position
* Layout calculations
* Animations before paint

---

# 🔥 4. useEffect vs useLayoutEffect

## 📌 Main Difference

| Feature        | useEffect            | useLayoutEffect     |
| -------------- | -------------------- | ------------------- |
| Execution Time | After render (async) | Before paint (sync) |
| Blocking UI    | No                   | Yes                 |
| Performance    | Better               | Can be slower       |
| Use Case       | API calls, timers    | DOM measurement     |

---

## 📌 Flow Difference

👉 useEffect
Render → Paint → useEffect

👉 useLayoutEffect
Render → useLayoutEffect → Paint

---

## 📌 Example

```js
useEffect(() => {
  console.log("useEffect");
}, []);

useLayoutEffect(() => {
  console.log("useLayoutEffect");
}, []);
```

👉 Output:

```
useLayoutEffect
useEffect
```

---

## 📌 When to Use What?

✔️ useEffect:

* API calls
* Data fetching
* Logging

✔️ useLayoutEffect:

* DOM measurement
* Prevent UI flicker
* Layout calculations

---

## 📌 Interview Tip

👉 Default = useEffect
👉 Use useLayoutEffect only when necessary

---

## ⚠️ Important Note

Avoid overusing useLayoutEffect → it blocks rendering and can slow UI

---

# 🎯 Final Summary

* useState → manage state
* useEffect → side effects (after render)
* useLayoutEffect → layout work (before paint)
* Prefer useEffect in most cases

---


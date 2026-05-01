
# 🔹 useState Hook in React

## 📌 What is useState?
useState is a React Hook that allows functional components to manage **state (data)**.

Before hooks, only class components could handle state. Now functional components can too.

---

## 📌 Syntax
const [state, setState] = useState(initialValue);

- state → current value
- setState → function to update state
- initialValue → starting value

---

## 📌 Example

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

---

## 📌 Key Points (Interview Important)

- State updates trigger re-render
- useState is asynchronous
- You should NOT mutate state directly
- Multiple useState can be used in one component

---

## 📌 Functional Update

setCount(prev => prev + 1);

👉 Use this when new state d
epends on previous state

---

## 📌 When to Use?

- Form inputs
- Counters
- Toggle (show/hide)
- Any dynamic UI state

# 🔹 useEffect Hook in React

## 📌 What is useEffect?

useEffect is used to handle **side effects** in React.

👉 Side effects = API calls, DOM updates, timers, subscriptions

---

## 📌 Syntax

useEffect(() => {
  // side effect logic
}, [dependencies]);

---

## 📌 Example

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

---

## 📌 Dependency Array Cases

1️⃣ [] → runs only once (componentDidMount)

2️⃣ [count] → runs when count changes

3️⃣ no dependency → runs on every render

---

## 📌 Cleanup Function

useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);

👉 Used to avoid memory leaks

---

## 📌 Key Points

- Runs AFTER rendering
- Non-blocking
- Used for async operations
- Can have multiple useEffect

# 🔹 useLayoutEffect Hook in React

## 📌 What is useLayoutEffect?

useLayoutEffect is similar to useEffect, but it runs **synchronously BEFORE the browser paints the screen**.

---

## 📌 Syntax

useLayoutEffect(() => {
  // logic
}, [dependencies]);

---

## 📌 Example

import React, { useLayoutEffect } from "react";

function LayoutExample() {
 
  useEffect(() => {
  console.log("run useeffct hook")
  },[]);
  
  useLayoutEffect(() => {
    console.log("run uselayout hook");
  }, []);

  return <div>Hello</div>;
}

```
Output:-
run uselayout hook
run useeffct hook

```

---

## 📌 Key Points

- Runs BEFORE painting (blocking)
- Used for DOM measurements
- Prevents flickering
- Can impact performance if overused

---

## 📌 When to Use?

- Measuring DOM size
- Scroll position
- Animations before paint

# 🔹 useLayoutEffect Hook in React

## 📌 What is useLayoutEffect?

useLayoutEffect is similar to useEffect, but it runs **synchronously BEFORE the browser paints the screen**.

---

## 📌 Syntax

useLayoutEffect(() => {
  // logic
}, [dependencies]);

---

## 📌 Example

import React, { useLayoutEffect, useRef } from "react";

function LayoutExample() {
  const boxRef = useRef();

  useLayoutEffect(() => {
    console.log(boxRef.current.getBoundingClientRect());
  }, []);

  return <div ref={boxRef}>Hello</div>;
}

---

## 📌 Key Points

- Runs BEFORE painting (blocking)
- Used for DOM measurements
- Prevents flickering
- Can impact performance if overused

---

## 📌 When to Use?

- Measuring DOM size
- Scroll position
- Animations before paint


# 🔥 useEffect vs useLayoutEffect

## 📌 Main Difference

| Feature            | useEffect                          | useLayoutEffect                  |
|------------------|----------------------------------|--------------------------------|
| Execution Time    | After render (async)              | Before paint (sync)             |
| Blocking UI       | No                                | Yes                             |
| Performance       | Better                            | Can be slower                   |
| Use Case          | API calls, timers                 | DOM measurement, animations     |

---

## 📌 Flow Difference

👉 useEffect:
Render → Paint → useEffect runs

👉 useLayoutEffect:
Render → useLayoutEffect runs → Paint

---

## 📌 Example Comparison

useEffect(() => {
  console.log("useEffect");
}, []);

useLayoutEffect(() => {
  console.log("useLayoutEffect");
}, []);

👉 Output order:
useLayoutEffect → useEffect

---

## 📌 When to Use What?

✔️ useEffect:
- API calls
- Fetch data
- Logging

✔️ useLayoutEffect:
- DOM measurement
- Avoid flickering UI
- Layout calculations

---

## 📌 Interview Tip

👉 Default choice = useEffect  
👉 Use useLayoutEffect ONLY when needed

---

## 📌 Important Note

⚠️ Avoid overusing useLayoutEffect → it blocks rendering and can slow UI

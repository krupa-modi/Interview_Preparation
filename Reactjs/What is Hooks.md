## 🔹 What are Hooks in React?

**Hooks** are special functions introduced in **React 16.8** that allow you to use **state and lifecycle features inside functional components**.

👉 Before Hooks:

* Only **class components** could use state & lifecycle methods.

👉 After Hooks:

* Functional components became **powerful + cleaner + easier to manage**

---

## 🔹 Why Hooks are Used?

### ✅ 1. Avoid Class Components

Class components were:

* Complex
* Hard to understand (`this`, binding issues)
* Verbose

Hooks allow writing everything in **simple functions**.

---

### ✅ 2. Reusable Logic

Hooks let you extract logic into reusable functions (**Custom Hooks**).

👉 Example:

```js
function useFetch(url) {
  // reusable logic
}
```

---

### ✅ 3. Better Code Organization

Instead of splitting logic across lifecycle methods:

* Hooks group **related logic together**

---

### ✅ 4. Cleaner & Readable Code

Less boilerplate, more clarity.

---

## 🔹 Rules of Hooks (VERY IMPORTANT 🔥)

1. ❌ Don’t call hooks inside loops, conditions, or nested functions
2. ✅ Always call hooks at the top level
3. ❌ Don’t use hooks inside normal JS functions
4. ✅ Use hooks only in:

   * React components
   * Custom hooks

---

## 🔹 Types of Hooks

### 🔸 1. Basic Hooks

---

### 1️⃣ useState Hook

👉 Used to manage state in functional components

```js
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}
```

### 📌 Key Points:

* `useState()` returns an array:

  * Current state
  * Function to update state
* State updates trigger **re-render**

---

### 2️⃣ useEffect Hook

👉 Used for **side effects**

Examples:

* API calls
* DOM updates
* Event listeners

```js
import { useEffect } from "react";

useEffect(() => {
  console.log("Component Mounted");

  return () => {
    console.log("Cleanup (Unmount)");
  };
}, []);
```

### 📌 Dependency Array:

* `[]` → run once (mount)
* `[value]` → run when value changes
* no array → run on every render

---

### 3️⃣ useRef Hook

👉 Used to persist values without re-render

```js
import { useRef } from "react";

const inputRef = useRef();

inputRef.current.focus();
```

### 📌 Uses:

* Access DOM
* Store mutable values

---

## 🔸 2. Advanced Hooks

---

### 4️⃣ useMemo

👉 Optimizes performance by memoizing values

```js
const memoValue = useMemo(() => {
  return expensiveFunction(data);
}, [data]);
```

---

### 5️⃣ useCallback

👉 Memoizes functions

```js
const memoFunc = useCallback(() => {
  doSomething();
}, []);
```

---

### 6️⃣ useContext

👉 Access global data without prop drilling

```js
const value = useContext(MyContext);
```

---

### 7️⃣ useReducer

👉 Alternative to useState for complex state logic

```js
const [state, dispatch] = useReducer(reducer, initialState);
```

---

## 🔹 Custom Hooks (VERY IMPORTANT 🔥🔥)

👉 Custom hooks are functions that start with `use`

```js
function useCounter() {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);

  return { count, increment };
}
```

### 📌 Benefits:

* Reusability
* Clean code
* Separation of concerns

---

## 🔹 Hooks vs Class Components

| Feature         | Class Component   | Hooks (Functional)  |
| --------------- | ----------------- | ------------------- |
| State           | this.state        | useState            |
| Lifecycle       | lifecycle methods | useEffect           |
| Code Complexity | High              | Low                 |
| Reusability     | Hard              | Easy (Custom Hooks) |

---

## 🔹 Common Interview Questions 🔥

### ❓ What is a Hook?

👉 A function that lets you use React features in functional components.

---

### ❓ Why Hooks were introduced?

👉 To simplify code, remove classes, and enable reusable logic.

---

### ❓ Difference: useEffect vs componentDidMount?

👉 `useEffect(() => {}, [])` behaves like `componentDidMount`.

---

### ❓ Can we use Hooks in class components?

👉 ❌ No

---

### ❓ What is dependency array?

👉 Controls when `useEffect` runs.

---

### ❓ useMemo vs useCallback?

* useMemo → returns value
* useCallback → returns function

---

## 🔹 When NOT to Use Hooks

❌ Inside loops
❌ Inside conditions
❌ In normal JS functions

---

## 🔹 Summary

* Hooks = core feature of modern React
* Replace class components
* Make code:

  * Cleaner
  * Reusable
  * Easy to maintain

---

## 🔥 Final Line (Interview Ready)

👉 "Hooks allow functional components to manage state, lifecycle, and side effects, making React code cleaner, reusable, and easier to maintain."

---


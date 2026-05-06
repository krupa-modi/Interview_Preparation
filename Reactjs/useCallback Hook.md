# 📘 useCallback Hook in React (Complete Guide)

## 🔹 What is `useCallback`?

`useCallback` is a React Hook that **memoizes (caches) a function** so that it is **not recreated on every render**.

👉 Useful when passing functions to child components

👉 In simple words:
It **returns the same function reference** unless dependencies change.

📌 Key Points
Returns a function
Prevents unnecessary re-creation of functions
Helps avoid unnecessary re-renders in child components

| Hook        | Fixes Problem              |
| ----------- | -------------------------- |
| useMemo     | Avoids recalculation       |
| useCallback | Avoids function recreation |


---

## 🔹 Syntax

```js
const memoizedFunction = useCallback(() => {
  // function logic
}, [dependencies]);
```

---

## 🔹 Why `useCallback` is Needed?

### ❌ Problem without useCallback

In React:

* Every render → new function is created
* This causes:

  * Unnecessary re-renders of child components
  * Performance issues (especially with `React.memo`)

---

## 🔥 Key Idea

👉 Functions are **reference types** in JavaScript

```js
() => {}
() => {}
```

❌ These are **NOT equal** (different references)

So React thinks:

> "Function changed → re-render child"

---

# 🧠 Basic Example

## ❌ Without useCallback

```js
import React, { useState } from "react";

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    console.log("Clicked");
  };

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <Child onClick={handleClick} />
    </>
  );
}

const Child = React.memo(({ onClick }) => {
  console.log("Child Rendered");
  return <button onClick={onClick}>Child Button</button>;
});

export default Parent;
```

---

## 🔴 Problem

* Parent re-renders → new `handleClick` function created
* `Child` re-renders unnecessarily ❌

---

# ✅ With useCallback

```js
import React, { useState, useCallback } from "react";

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <Child onClick={handleClick} />
    </>
  );
}

const Child = React.memo(({ onClick }) => {
  console.log("Child Rendered");
  return <button onClick={onClick}>Child Button</button>;
});

export default Parent;
```

---

## ✅ Output Behavior

### 🔹 Initial Render

```
Child Rendered
```

### 🔹 Click "Increment"

```
(No Child Render)
```

👉 Because function reference is same ✔️

---

# 🔍 Deep Explanation

## 🧩 What useCallback Does Internally?

```js
useCallback(fn, deps)
```

👉 Same as:

```js
useMemo(() => fn, deps)
```

✔️ It **memoizes the function itself**
❌ Not the result (that’s useMemo)

---

# ⚡ useCallback vs useMemo

| Feature  | useCallback                 | useMemo                     |
| -------- | --------------------------- | --------------------------- |
| Returns  | Function                    | Value                       |
| Purpose  | Prevent function recreation | Prevent value recalculation |
| Use case | Event handlers              | Expensive calculations      |

---

# 🎯 When to Use useCallback?

## ✅ Use it when:

1. Passing function to **child component**
2. Child is wrapped with `React.memo`
3. Prevent unnecessary re-renders
4. Function is dependency in:

   * `useEffect`
   * `useMemo`

---

## ❌ Do NOT use when:

* Small/simple components
* No performance issue
* Not passing function to child

👉 Overuse = unnecessary complexity

---

# 🧠 Real-World Example

```js
const fetchData = useCallback(() => {
  console.log("Fetching data...");
}, []);
```

Used inside:

```js
useEffect(() => {
  fetchData();
}, [fetchData]);
```

👉 Prevents infinite loop ✔️

---

# 🚨 Common Mistakes (VERY IMPORTANT)

## ❌ 1. Missing Dependency

```js
const handleClick = useCallback(() => {
  console.log(count);
}, []); // ❌ WRONG
```

👉 `count` should be in dependency

```js
}, [count]); // ✅ Correct
```

---

## ❌ 2. Overusing useCallback

```js
const fn = useCallback(() => {}, []);
```

👉 No benefit here ❌

---

## ❌ 3. Thinking it improves performance always

👉 It **only helps in specific cases**

---

# 🧠 Interview Points (IMPORTANT)

✔️ `useCallback` memoizes function reference
✔️ Prevents unnecessary re-renders
✔️ Works well with `React.memo`
✔️ Similar to `useMemo` but for functions
✔️ Useful in dependency arrays

---

# 🎯 Final Summary

* `useCallback` = **memoize function**
* Prevents unnecessary child re-renders
* Returns same function unless dependencies change
* Use carefully — not everywhere


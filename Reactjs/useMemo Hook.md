
# 📘 useMemo Hook in React (Easy Explanation)

## 🔹 What is `useMemo`?

`useMemo` is a React Hook that **optimizes performance** by **memoizing (caching)** the result of a function.
`useMemo` is a React Hook used to memoize (cache) a computed value so that it is not recalculated on every render.

👉 It means:

* React will **NOT recompute the value** again and again
* It will only recompute **when dependencies change**

---

## 🔹 Syntax

```js
const memoizedValue = useMemo(() => {
  return computeValue();
}, [dependencies]);
```

📌 Key Points
* Returns a value
* Runs only when dependencies change
* Prevents expensive recalculation
---

## 🔹 Why we use `useMemo`?

Normally in React:

* Every time component re-renders ➝ all functions run again ❌
* Even if value didn’t change

👉 `useMemo` prevents unnecessary recalculations ✔️

---

# 🧠 Your Example (Simplified)

## ✅ Code

```js
import './App.css';
import React, { useState, useMemo } from 'react';

function App() {
  const [count, setCount] = useState(0);
  const [item, setItem] = useState(10);

  const multiCountMemo = useMemo(function multiCount() {
    console.warn("multiCount called");
    return count * 5;
  }, [count]);

  return (
    <div className="App">
      <h1>useMemo Hook in React</h1>

      <h2>Count: {count}</h2>
      <h2>Item: {item}</h2>

      <h2>{multiCountMemo}</h2>

      <button onClick={() => setCount(count + 1)}>
        Update Count
      </button>

      <button onClick={() => setItem(item * 10)}>
        Update Item
      </button>
    </div>
  );
}

export default App;
```

# 🖥️ Output Behavior

## 🔹 Initial Render

```
Count: 0
Item: 10
Result: 0
Console: multiCount called
```

---

## 🔹 Click "Update Item"

```
Count: 0
Item: 100
Result: 0
Console: ❌ (NO log)
```

👉 Because `count` didn’t change

---

## 🔹 Click "Update Count"

```
Count: 1
Item: 100
Result: 5
Console: multiCount called
```

👉 Because dependency `[count]` changed

---

# 🔥 Key Concept

| Action         | Re-render | Function Runs? |
| -------------- | --------- | -------------- |
| Update `count` | ✅ Yes     | ✅ Yes          |
| Update `item`  | ✅ Yes     | ❌ No           |

---

# 🚀 Without useMemo (Problem)

```js
const multiCount = () => {
  console.warn("multiCount called");
  return count * 5;
};
```

👉 Now:

* Every render → function runs ❌
* Even when `item` changes

---

# 🎯 Final Summary

* `useMemo` = **performance optimization hook**
* It **caches computed value**
* Runs only when **dependency changes**
* Useful for:

  * heavy calculations
  * preventing unnecessary re-renders

---


# 🔹 What is `useRef`?

`useRef` ek React hook hai jo:

👉 **Mutable value store karta hai**
👉 **Re-render trigger nahi karta**
👉 **DOM elements ko directly access karne ke liye use hota hai**
👉 **useRef is a React Hook that lets you reference a value that’s not needed for rendering.
👉 **useRef returns a ref object with a single current property initially set to the initial value you provided.

---

## 📌 Syntax

```js
const ref = useRef(initialValue);
```

👉 Ye return karta hai ek object:

```js
{
  current: initialValue
}
```

---

# 🔥 Why we use `useRef`?

### ✅ 1. DOM Access (Most Common Use)

```js
import { useRef } from "react";

function InputFocus() {
  const inputRef = useRef();

  const handleClick = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleClick}>Focus</button>
    </>
  );
}
```

---

### ✅ 2. Store Value Without Re-render

```js
const countRef = useRef(0);

function handleClick() {
  countRef.current++;
  console.log(countRef.current);
}
```

👉 UI update nahi hoga
👉 Value persist rahegi

---

### ✅ 3. Previous Value Store Karna

```js
import { useRef, useEffect } from "react";

function Example({ value }) {
  const prevRef = useRef();

  useEffect(() => {
    prevRef.current = value;
  });

  return (
    <div>
      Current: {value}, Previous: {prevRef.current}
    </div>
  );
}
```

---

### ✅ 4. Avoid Unnecessary Re-render

👉 `useState` change → re-render
👉 `useRef` change → NO re-render

---

# ⚡ `useRef` vs `useState`

| Feature   | useRef           | useState |
| --------- | ---------------- | -------- |
| Re-render | ❌ No             | ✅ Yes    |
| Mutable   | ✅ Yes            | ❌ No     |
| UI Update | ❌ No             | ✅ Yes    |
| Use Case  | DOM, store value | UI state |

---

# 🔥 Important Behavior

---

## 🧠 1. Value Persist Across Renders

```js
const ref = useRef(0);
```

👉 Har render me same object milega

---

## 🧠 2. Changing `.current` DOES NOT re-render

```js
ref.current = 10;
```

👉 UI update nahi hota

---

## 🧠 3. Direct DOM Manipulation Possible

```js
ref.current.style.color = "red";
```

---

# ⚠️ Common Mistakes

---

## ❌ Mistake 1: UI update expect karna

```js
ref.current++;
```

👉 UI change nahi hoga

---

## ❌ Mistake 2: Wrong use instead of state

👉 Agar UI update chahiye → use `useState`

---

# 🔥 Advanced Use Cases

---

## 🚀 1. Timer / Interval Store

```js
const timerRef = useRef();

useEffect(() => {
  timerRef.current = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => clearInterval(timerRef.current);
}, []);  // o/p Running...
// Running...
// Running...
// Running...
...
```

---

## 🚀 2. Avoid Stale Closures

```js
const latestValue = useRef(value);

useEffect(() => {
  latestValue.current = value;
});
```

---

## 🚀 3. Forwarding Refs

```js
const Input = React.forwardRef((props, ref) => {
  return <input ref={ref} />;
});
```

---

## 🚀 4. useRef with uncontrolled components

```js
function Form() {
  const inputRef = useRef();

  const handleSubmit = () => {
    console.log(inputRef.current.value);
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

---

# ⚔️ `useRef` vs `createRef`

| Feature              | useRef | createRef         |
| -------------------- | ------ | ----------------- |
| Functional Component | ✅ Yes  | ❌ No              |
| Persist value        | ✅ Yes  | ❌ New each render |
| Recommended          | ✅ Yes  | ❌ No              |

---

# 🎯 Interview Questions (VERY IMPORTANT 🔥)

---

## ❓ Q1: What is useRef?

👉 Hook to store mutable value without re-render and access DOM

---

## ❓ Q2: Does useRef cause re-render?

👉 ❌ No

---

## ❓ Q3: Difference between useRef and useState?

👉 `useState` → re-render
👉 `useRef` → no re-render

---

## ❓ Q4: When to use useRef?

👉 DOM access
👉 store previous value
👉 timers
👉 mutable data

---

## ❓ Q5: Can we update UI using useRef?

👉 ❌ No

---

## ❓ Q6: What is `.current`?

👉 Property jisme actual value store hoti hai

---

## ❓ Q7: useRef lifecycle behavior?

👉 Same object har render me return hota hai

---

## ❓ Q8: Can we store function in useRef?

👉 ✅ Yes

```js
const fnRef = useRef(() => {});
```

---

## ❓ Q9: Why useRef better than variable?

👉 Variable reset ho jata hai render pe
👉 useRef persist karta hai -> 👉 Persist = value render ke baad bhi survive kare (reset na ho)

Matlab:
Component jitni baar re-render ho, useRef ki value same rehti hai, reset nahi hoti.

```
import { useRef } from "react";

function App() {
  const countRef = useRef(0);

  countRef.current++;
  console.log(countRef.current);

  return <button>Click</button>;
}  // o/p 1,2,3,4....

```
👉 useRef persist karta hai ka matlab hai ki uski value component ke re-renders ke beech me retain hoti hai aur reset nahi hoti. Ye ek mutable object return karta hai jiska .current property render ke baad bhi same rehta hai.

---

## ❓ Q10: Real-world use case?

👉 Input focus
👉 timer
👉 previous state
👉 API cancel

---

# 🧠 Deep Concept (VERY IMPORTANT)

👉 `useRef` internally ek object banata hai jo React **preserve karta hai between renders**

```js
const ref = { current: value };
```

👉 React isko re-create nahi karta

---

# 💡 Best Practices

✅ DOM access ke liye use karo
✅ Previous value store karne ke liye use karo
❌ State replacement mat banao

---

# 🚀 Final Summary

* `useRef` = mutable container
* Re-render nahi karta
* DOM + persistent value ke liye use hota hai

---

# 🎯 Perfect Interview Answer

> useRef React ka ek hook hai jo mutable value ko store karta hai bina component ko re-render kiye. Iska main use DOM elements ko access karna, previous values store karna aur timers ya mutable data handle karna hota hai.

---

# 📌 inputRef.current.value
Current input value.

---
# 📌 inputRef.current.focus()
Input focus karta hai.

---
# 📌 inputRef.current.blur()
Input ka focus remove karta hai.

---
# 📌 inputRef.current.style
DOM style access/change.

---
# 📌 inputRef.current.checked
Checkbox checked status.

---
# 📌 inputRef.current.src
Image source access.

---
# 📌 divRef.current.scrollIntoView()
Element tak scroll karta hai.

---
# 📌 videoRef.current.play()
Video play karta hai.

---
# 📌 videoRef.current.pause()
Video pause karta hai.

---
# 📌 timerRef.current
Timer ID store karta hai.

---
# 📌 prevValue.current
Previous value store karta hai.

---






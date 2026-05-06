

# 📘 Difference Between `useMemo` and `useCallback` (In-Depth Guide)

---

# 🔹 Introduction

Both `useMemo` and `useCallback` are **performance optimization hooks** in React.

👉 They help to:

* Avoid unnecessary computations
* Prevent unnecessary re-renders

But they are used in **different situations**

---

# 🧠 Core Difference (1 Line)

👉 `useMemo` → **memoizes a VALUE**
👉 `useCallback` → **memoizes a FUNCTION**

---

# 🔹 Syntax

## ✅ useMemo

```js id="x1m1"
const memoizedValue = useMemo(() => {
  return expensiveCalculation(a, b);
}, [a, b]);
```

---

## ✅ useCallback

```js id="x2m2"
const memoizedFunction = useCallback(() => {
  console.log("Hello");
}, []);
```

---

# 🔍 Internal Working (VERY IMPORTANT)

👉 `useCallback` is actually built using `useMemo`

```js id="x3m3"
const memoizedFunction = useMemo(() => fn, deps);
```

✔️ So internally both are related

---

# 🧩 Key Differences Table

| Feature           | useMemo 🧠                    | useCallback ⚡                   |
| ----------------- | ----------------------------- | ------------------------------- |
| Returns           | Value                         | Function                        |
| Purpose           | Cache result of calculation   | Cache function reference        |
| Use case          | Expensive computations        | Passing functions to children   |
| Execution         | Runs function & stores result | Stores function, doesn’t run it |
| Performance focus | Avoid recalculation           | Avoid re-creation of functions  |

---

# 🧠 Example 1 — useMemo (Value Optimization)

```js id="x4m4"
const result = useMemo(() => {
  console.log("Calculating...");
  return count * 5;
}, [count]);
```

### 🔹 Behavior

| Action        | Function Runs? |
| ------------- | -------------- |
| count changes | ✅ Yes          |
| other state   | ❌ No           |

---

# 🧠 Example 2 — useCallback (Function Optimization)

```js id="x5m5"
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

### 🔹 Behavior

| Action            | Function Recreated? |
| ----------------- | ------------------- |
| re-render         | ❌ No                |
| dependency change | ✅ Yes               |

---

# 🔥 Real Comparison Example

## ❌ Without Optimization

```js id="x6m6"
const Parent = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    console.log("Clicked");
  };

  return <Child onClick={handleClick} />;
};
```

👉 Child re-renders every time ❌

---

## ✅ With useCallback

```js id="x7m7"
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

👉 Child re-render avoided ✔️

---

## ✅ With useMemo

```js id="x8m8"
const result = useMemo(() => count * 5, [count]);
```

👉 Expensive calculation optimized ✔️

---

# 🧠 When to Use What?

## ✅ Use `useMemo` when:

* Heavy calculations
* Derived data (filtered/sorted list)
* Avoid recalculating values

---

## ✅ Use `useCallback` when:

* Passing function to child component
* Using `React.memo`
* Function is dependency in hooks

---

# 🚨 Common Mistakes

## ❌ 1. Using useMemo for functions

```js id="x9m9"
const fn = useMemo(() => () => {}, []);
```

👉 ❌ Wrong
👉 Use `useCallback`

---

## ❌ 2. Using useCallback for values

```js id="x10m10"
const value = useCallback(() => count * 2, [count]);
```

👉 ❌ Wrong
👉 Use `useMemo`

---

## ❌ 3. Overusing both hooks

👉 Adds complexity without benefit

---

# 🧠 Mental Model (Easy Trick)

👉 Remember this:

* 📦 `useMemo` = **Store RESULT**
* 🔁 `useCallback` = **Store FUNCTION**

---

# 🎯 Interview Summary (Must Remember)

✔️ Both are optimization hooks
✔️ `useMemo` → memoizes value
✔️ `useCallback` → memoizes function
✔️ `useCallback` internally uses `useMemo`
✔️ Use only when needed (not everywhere)

---

# 🚀 Final Conclusion

* If you want to **avoid recalculating value** → useMemo
* If you want to **avoid recreating function** → useCallback

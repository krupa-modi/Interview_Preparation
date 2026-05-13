# 🔹 What is a Memory Leak?

A memory leak happens when:

```text id="n3f6ym"
Memory that is no longer needed is not released.
```

Because of this:

* RAM usage increases
* Application becomes slow
* Browser may freeze/crash

---

# 📌 Simple Definition

```text id="jj3g5s"
Unused objects remain in memory because references still exist.
```

---

# 🔥 Why Memory Leaks Are Dangerous?

## Problems:

* High memory consumption
* Slow performance
* UI lag
* Browser crash
* App freeze

---

# 🔹 How JavaScript Memory Works

JavaScript automatically allocates memory for:

* Objects
* Arrays
* Functions
* Variables

And automatically removes unused memory using:

```text id="jlwm1m"
Garbage Collection
```

But if references still exist,
Garbage Collector cannot remove memory.

---

# 🔥 Common Causes of Memory Leaks

---

# 1️⃣ Global Variables

## ❌ Problem

```js id="34sy0h"
data = new Array(1000000);
```

Without `let`, `const`, or `var`,
it becomes global.

Global variables stay in memory forever.

---

# ✅ Fix

```js id="1jlwm8"
const data = [];
```

---

# 2️⃣ Unremoved Event Listeners

## ❌ Problem

```js id="0dtzbq"
button.addEventListener("click", handleClick);
```

If element removed from DOM but listener still exists,
memory leak happens.

---

# ✅ Fix

```js id="f1h0l4"
button.removeEventListener("click", handleClick);
```

---

# 🔥 React Important Point

In React:

```js id="b8lm4v"
useEffect cleanup
```

is used to prevent leaks.

---

# 3️⃣ Closures Holding Memory

## ❌ Example

```js id="rbl57w"
function outer() {
  const largeData = new Array(1000000);

  return function inner() {
    console.log(largeData);
  };
}
```

`inner()` keeps reference to `largeData`.

Memory cannot be freed.

---

# 4️⃣ Timers Not Cleared

## ❌ Problem

```js id="rr1j4z"
setInterval(() => {
  console.log("Running");
}, 1000);
```

Runs forever.

---

# ✅ Fix

```js id="yqufcf"
clearInterval(intervalId);
```

---

# 5️⃣ Detached DOM Elements

DOM removed from page,
but JavaScript reference still exists.

---

# ❌ Example

```js id="qsdh2e"
const element = document.getElementById("box");

document.body.removeChild(element);
```

If `element` variable still exists,
memory leak possible.

---

# 🔥 How to Prevent Memory Leaks

| Solution           | Purpose                   |
| ------------------ | ------------------------- |
| Remove listeners   | Avoid unused references   |
| Clear timers       | Stop background execution |
| Avoid globals      | Prevent permanent memory  |
| Nullify references | Help GC                   |
| Cleanup closures   | Release memory            |

---

# ✅ Example

```js id="mzbjlwm"
let data = new Array(1000000);

data = null;
```

Now GC can remove memory.

---

# 🔥 Interview Questions

---

# ✅ Q1. What is a memory leak?

Unused memory not released due to existing references.

---

# ✅ Q2. Common causes?

* Global variables
* Event listeners
* Closures
* Timers
* Detached DOM

---

# ✅ Q3. How to avoid memory leaks?

* Remove listeners
* Clear intervals
* Use cleanup functions
* Remove references

---

# 🎯 Interview Line

```text id="hbdz6n"
Memory leaks occur when unused objects remain referenced and cannot be garbage collected.
```
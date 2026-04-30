
# Pure vs Impure Functions in JavaScript (Deep Interview Guide)

## 1. What is a Pure Function?

A **pure function** is a function that:

1. Always returns the **same output for the same input**
2. Has **no side effects** (does not change anything outside the function)

---

## Example of Pure Function ✅

```js id="pf1"
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
console.log(add(2, 3)); // 5 (same output every time)
```

👉 No external dependency
👉 No modification outside function

---

## Key Properties of Pure Functions

* Deterministic (same input → same output)
* No side effects
* Easier to test
* Predictable behavior

---

## 2. What is an Impure Function?

An **impure function**:

* May return **different outputs for same input**
* Causes **side effects**

---

## Example of Impure Function ❌

```js id="ip1"
let total = 0;

function addToTotal(value) {
  total += value;
  return total;
}

addToTotal(5); // 5
addToTotal(5); // 10 (different output for same input)
```

👉 Depends on external variable
👉 Modifies global state

---

## What are Side Effects? 🔥

Side effects = any change outside the function

### Examples:

* Modifying global variable
* Changing object/array
* API calls
* DOM manipulation
* Console logging (sometimes considered)

---

## Another Impure Example

```js id="ip2"
function getRandomNumber() {
  return Math.random();
}
```

👉 Same input → different output → impure

---

## Pure vs Impure (Comparison)

| Feature        | Pure Function       | Impure Function |
| -------------- | ------------------- | --------------- |
| Output         | Same for same input | Can change      |
| Side Effects   | ❌ No                | ✅ Yes           |
| Dependency     | Only input          | External data   |
| Testing        | Easy                | Difficult       |
| Predictability | High                | Low             |

---

## Real-World Example

### Impure Version ❌

```js id="real1"
let cart = [];

function addItem(item) {
  cart.push(item);
}
```

👉 Modifies external state

---

### Pure Version ✅

```js id="real2"
function addItem(cart, item) {
  return [...cart, item];
}
```

👉 Returns new data instead of modifying old

---

## Why Pure Functions are Important? 🔥

* Used in **React (state management)**
* Helps in **functional programming**
* Improves **code reliability**
* Easier debugging & testing

---

## How to Convert Impure → Pure

### Before ❌

```js id="conv1"
let count = 0;

function increment() {
  count++;
}
```

### After ✅

```js id="conv2"
function increment(count) {
  return count + 1;
}
```

---

## When Impure Functions are Needed?

👉 Sometimes required:

* API calls
* Database operations
* UI updates
* Logging

👉 But keep them **separate from business logic**

---

## Interview One-Liner

👉 "A pure function always returns the same output for the same input and has no side effects, whereas an impure function can depend on or modify external state."

---

## Final Tips (Interview Ready 🔥)

* Always give **definition + example**
* Mention **side effects**
* Explain **why pure is preferred**
* Give **real-world usage (React)**

---

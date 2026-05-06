# 🚀 forEach vs map in JavaScript (Complete Guide)

Understanding the difference between **`forEach()`** and **`map()`** is very important for JavaScript interviews.

---

# 🔥 1. forEach()

👉 **Purpose:**
Used to **loop over an array** and perform some action.

👉 **Important:**

* It **does NOT return anything** (`undefined`)
* Used when you **just want to iterate**

---

## ✅ Example:

```js
const arr = [1, 2, 3];

const result = arr.forEach((num) => {
  return num * 2;
});

console.log(result);
```

### 🧠 Output:

```js
undefined
```

👉 Even though we returned `num * 2`, it is **ignored**

---

## ✅ Real Use Case:

```js
const arr = [1, 2, 3];

arr.forEach((num) => {
  console.log(num * 2);
});
```

👉 Used for:

* Printing
* Side effects (API calls, logging, etc.)

---

# 🔥 2. map()

👉 **Purpose:**
Used to **transform array** and create a **new array**

👉 **Important:**

* It **returns a new array**
* Same length as original array

---

## ✅ Example:

```js
const arr = [1, 2, 3];

const result = arr.map((num) => {
  return num * 2;
});

console.log(result);
```

### 🧠 Output:

```js
[2, 4, 6]
```

👉 `map()` creates a new transformed array

---

# ⚡ Key Differences (VERY IMPORTANT 🔥)

| Feature                | forEach()           | map()                   |
| ---------------------- | ------------------- | ----------------------- |
| Return Value           | ❌ undefined         | ✅ New Array             |
| Use Case               | Iteration only      | Transformation          |
| Chainable              | ❌ No                | ✅ Yes                   |
| Mutation               | Can modify original | Usually does not modify |
| Functional Programming | ❌ Less preferred    | ✅ Preferred             |

---

# 🎯 Simple Understanding

👉 **forEach = Just loop (no return)**
👉 **map = Loop + return new array**

---

# 🔥 Example Comparison

```js
const arr = [1, 2, 3];

// forEach
let newArr1 = [];
arr.forEach((num) => {
  newArr1.push(num * 2);
});

// map
const newArr2 = arr.map((num) => num * 2);

console.log(newArr1); // [2,4,6]
console.log(newArr2); // [2,4,6]
```

👉 But:

* `forEach` → manual work
* `map` → cleaner & shorter

---

# 🧠 Interview Tip

👉 If interviewer asks:

* "Why map over forEach?"

💡 Answer:

* `map()` is **functional, clean, and returns new array**
* `forEach()` is for **side effects only**

---

# 🚀 Final Summary

* Use **forEach()** when you don’t need a return value
* Use **map()** when you want to transform data
* Prefer **map()** in modern JavaScript

---


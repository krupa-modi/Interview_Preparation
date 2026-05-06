# ⚡ JavaScript Core Concepts – Interview Master Guide (map, filter, reduce & more)

---

# 🔁 1. map()

## 👉 What is map()?

`map()` is used to **transform each element of an array** and returns a **new array**.

---

### 🔍 Syntax

```js
array.map((item, index) => {})
```

---

### 🔍 Example

```js
const nums = [1, 2, 3];

const result = nums.map(n => n * 2);
```

👉 Output:

```js
[2, 4, 6]
```

---

### 🔥 Key Points

* Returns **new array ✅**
* Does NOT modify original array
* Used for transformation

---

# 🔎 2. filter()

## 👉 What is filter()?

`filter()` is used to **select elements based on condition**

---

### 🔍 Example

```js
const nums = [1, 2, 3, 4];

const result = nums.filter(n => n > 2);
```

👉 Output:

```js
[3, 4]
```

---

### 🔥 Key Points

* Returns **new array ✅**
* Filters based on condition
* Can return empty array

---

# 🔥 3. reduce()

## 👉 What is reduce()?

`reduce()` is used to **convert array into single value**

---

### 🔍 Syntax

```js
array.reduce((acc, curr) => {}, initialValue)
```

---

### 🔍 Example (Sum)

```js
const nums = [1, 2, 3];

const sum = nums.reduce((acc, curr) => acc + curr, 0);
```

👉 Output:

```js
6
```

---

### 🔥 Key Points

* Returns **single value ✅**
* Very powerful (sum, object, grouping)

---

# ⚡ 4. map vs filter vs reduce

| Method | Purpose        | Returns      |
| ------ | -------------- | ------------ |
| map    | Transform data | New array    |
| filter | Select data    | New array    |
| reduce | Aggregate data | Single value |

---

# 🔁 5. forEach vs map

## 👉 forEach()

```js
const nums = [1, 2, 3];

nums.forEach(n => console.log(n));
```

---

## 🔥 Difference

| Feature   | forEach      | map            |
| --------- | ------------ | -------------- |
| Return    | ❌ undefined  | ✅ new array    |
| Use       | Side effects | Transformation |
| Chainable | ❌ No         | ✅ Yes          |

---

# 🧱 6. Object Methods

---

## 🔹 Object.keys()

👉 Returns keys

```js
const obj = { a: 1, b: 2 };

Object.keys(obj);
```

👉 Output:

```js
['a', 'b']
```

---

## 🔹 Object.values()

👉 Returns values

```js
Object.values(obj);
```

👉 Output:

```js
[1, 2]
```

---

## 🔹 Object.entries()

👉 Returns key-value pairs

```js
Object.entries(obj);
```

👉 Output:

```js
[['a', 1], ['b', 2]]
```

---

# 🎯 7. Destructuring

## 👉 What is Destructuring?

Extract values from arrays/objects easily

# 📦 Destructuring in JavaScript

👉 **Definition:**
Destructuring is a JavaScript feature that allows you to **extract values from arrays or objects and assign them to variables in a shorter way**.

---

## ✅ Array Destructuring

```js
const arr = [10, 20, 30];

const [a, b] = arr;

console.log(a); // 10
console.log(b); // 20
```

---

## ✅ Object Destructuring

```js
const user = {
  name: "Krupa",
  age: 22
};

const { name, age } = user;

console.log(name); // Krupa
console.log(age);  // 22
```

---

# 🎯 Summary

👉 Destructuring = **Extract values easily from array/object into variables**


---

### 🔍 Array Destructuring

```js
const arr = [1, 2, 3];

const [a, b] = arr;
```

👉 a = 1, b = 2

---

### 🔍 Object Destructuring

```js
const user = { name: "Krupa", age: 25 };

const { name, age } = user;
```

---

# 🔄 8. Spread vs Rest Operator

---

## 🔹 Spread Operator (...)

👉 Expands elements

```js
const arr = [1, 2];
const newArr = [...arr, 3];
```

👉 Output:

```js
[1, 2, 3]
```

---

## 🔹 Rest Operator (...)

👉 Collects values

```js
function sum(...nums) {
  return nums;
}
```

👉 Output:

```js
[1, 2, 3]
```

---

## 🔥 Difference: Spread vs Rest

| Feature  | Spread          | Rest            |
| -------- | --------------- | --------------- |
| Purpose  | Expand          | Collect         |
| Use      | Arrays, objects | Function params |
| Position | RHS             | LHS             |

---

# 🎯 Final Interview Summary (VERY IMPORTANT)

👉 `map()` → transform → returns array
👉 `filter()` → condition → returns array
👉 `reduce()` → single value

👉 `forEach()` → no return
👉 `map()` → returns new array

👉 `Object.keys()` → keys
👉 `Object.values()` → values
👉 `Object.entries()` → key-value

👉 Destructuring → extract values
👉 Spread → expand
👉 Rest → collect

---

💡 **Pro Tip (MNC Level Answer):**
👉 “map, filter, reduce are immutable array methods used for transformation, selection, and aggregation respectively” 🚀

# 🚀 Spread vs Rest Operator (JavaScript) — Complete Guide

Agar tumhe JavaScript interview crack karna hai, toh **spread (`...`)** aur **rest (`...`)** operators ka clear understanding bahut important hai. Dono ka syntax same hai, but **use-case alag hai**.

---

# 🔥 1. Spread Operator (`...`)

👉 **Spread ka kaam:**
Existing array ya object ko **expand (failana)**

---

## ✅ Example 1: Array Spread

```js
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

console.log(arr2);
```

### 🧠 Output:

```
[1, 2, 3, 4, 5]
```

👉 Explanation:

* `...arr1` ne array ke elements ko **spread kar diya**
* New values easily add ho gaye

---

## ✅ Example 2: Copy Array (Shallow Copy)

```js
const original = [10, 20, 30];
const copy = [...original];

console.log(copy);
```

👉 Yeh ek **new array** banata hai (reference same nahi hota)

---

## ✅ Example 3: Object Spread

```js
const user = { name: "Krupa", age: 22 };
const updatedUser = { ...user, city: "Pune" };

console.log(updatedUser);
```

### 🧠 Output:

```
{ name: "Krupa", age: 22, city: "Pune" }
```

---

## ✅ Example 4: Override Values

```js
const obj = { name: "A", age: 20 };

const newObj = { ...obj, age: 25 };

console.log(newObj);
```

👉 Last value override karega

---

## ✅ Example 5: Function Arguments Spread

```js
function sum(a, b, c) {
  return a + b + c;
}

const nums = [1, 2, 3];

console.log(sum(...nums));
```

👉 Array ko function arguments me convert kar diya

---

# 🔥 2. Rest Operator (`...`)

👉 **Rest ka kaam:**
Multiple values ko **collect (ikatha karna)**

---

## ✅ Example 1: Function Parameters

```js
function sum(...numbers) {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3, 4));
```

### 🧠 Output:

```
10
```

👉 Explanation:

* `...numbers` sab arguments ko array me convert kar deta hai

---

## ✅ Example 2: Array Destructuring

```js
const arr = [1, 2, 3, 4];

const [first, ...rest] = arr;

console.log(first); // 1
console.log(rest);  // [2, 3, 4]
```

👉 First value alag, baaki sab `rest` me

---

## ✅ Example 3: Object Destructuring

```js
const user = {
  name: "Krupa",
  age: 22,
  city: "Pune"
};

const { name, ...rest } = user;

console.log(name); // Krupa
console.log(rest); // { age: 22, city: "Pune" }
```

---

# ⚡ Spread vs Rest — Difference (VERY IMPORTANT 🔥)

| Feature      | Spread Operator               | Rest Operator                |
| ------------ | ----------------------------- | ---------------------------- |
| Kaam         | Expand karta hai              | Collect karta hai            |
| Use hota hai | Array/Object ko todne ke liye | Values ko ek me lene ke liye |
| Position     | Right side (usage me)         | Left side (definition me)    |
| Example      | `[...arr]`                    | `(...args)`                  |

---

# 🎯 Real-Life Simple Samajh

👉 **Spread = "failana"**

```
[1,2,3] → ... → 1,2,3
```

👉 **Rest = "ikatha karna"**

```
1,2,3 → ... → [1,2,3]
```

---

# 🧠 Interview Trick (IMPORTANT)

👉 SAME syntax (`...`)
👉 Meaning depends on **context**

* Function parameter me → REST
* Function call me → SPREAD
* Destructuring left side → REST
* Object/Array copy me → SPREAD

---

# 🚀 Final Summary

* Spread = Expand data
* Rest = Collect data
* Dono ka syntax same hai but use alag hai
* Arrays + Objects + Functions sab me use hota hai

---

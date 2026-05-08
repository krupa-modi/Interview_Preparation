## What is IIFE?

IIFE ka full form hai:

> **Immediately Invoked Function Expression**

Ye ek aisa function hota hai jo:

1. **Define hote hi turant execute ho jata hai**
2. Global scope ko pollute nahi karta
3. Private variables create karne ke liye use hota hai

---
# Basic Syntax

```js
(function () {
  console.log("IIFE Executed");
})();
````

## Output

```js
IIFE Executed
```
---


### Step-by-step samjho:

## 1. Function ko parentheses `()` me wrap kiya

```js
(function () {})
```

Isse JavaScript samajhta hai ki ye:

> "Function Declaration" nahi,
> "Function Expression" hai.

---

## 2. Last me `()` lagaya

```js
(function () {})();
```

Ye function ko immediately call karta hai.

---

# Normal Function vs IIFE

## Normal Function

```js
function greet() {
  console.log("Hello");
}

greet();
```

### Yaha:

* Pehle function define hua
* Fir manually call kiya

---

## IIFE

```js
(function () {
  console.log("Hello");
})();
```

### Yaha:

* Function define bhi hua
* Aur instantly execute bhi ho gaya

---

# Why Use IIFE?

## 1. Global Scope Pollution Avoid Karna

### Problem Without IIFE

```js
var message = "Hello";
```

Ye variable global ban gaya.
Large projects me ye issue create karta hai.

---

## Solution Using IIFE

```js
(function () {
  var message = "Hello";
  console.log(message);
})();
```

### Outside access nahi milega

```js
console.log(message); // Error
```

---

# 2. Private Variables Create Karna

```js
(function () {
  var count = 0;

  console.log(count);
})();
```

`count` sirf function ke andar accessible hai.

---

# IIFE with Parameters

```js
(function (name) {
  console.log("Hello " + name);
})("Krupa");
```

## Output

```js
Hello Krupa
```

---

# Arrow Function IIFE

```js
(() => {
  console.log("Arrow IIFE");
})();
```

---

# Named IIFE

```js
(function greet() {
  console.log("Named IIFE");
})();
```

## Note

Ye function outside accessible nahi hota.

```js
greet(); // Error
```

---

# IIFE Returning Value

```js
const result = (function () {
  return 10 + 20;
})();

console.log(result);
```

## Output

```js
30
```

---

# Real World Example

## Problem

Suppose multiple JS files me same variable name use ho raha hai.

```js
var user = "A";
```

Dusri file:

```js
var user = "B";
```

Conflict ho sakta hai.

---

# Solution with IIFE

```js
(function () {
  var user = "A";
  console.log(user);
})();

(function () {
  var user = "B";
  console.log(user);
})();
```

### Output

```js
A
B
```

No conflict.

---

# Important Interview Point

# Why do we use IIFE?

### Answer

* Avoid global scope pollution
* Create private scope
* Encapsulation
* Data hiding

---

# Q3. Difference Between Normal Function and IIFE?

| Normal Function                   | IIFE                           |
| --------------------------------- | ------------------------------ |
| Manual call required              | Automatically executes         |
| Global scope affect kar sakta hai | Private scope create karta hai |

---

# Advantages of IIFE

✅ Immediate execution
✅ Avoid global variables
✅ Data privacy
✅ Encapsulation
✅ Better code organization

---

# Disadvantages of IIFE

❌ Readability kabhi confusing ho sakti hai
❌ Overuse se debugging difficult ho sakti hai
❌ ES6 modules ke baad need kam ho gayi

---

> “IIFE is a function expression that executes immediately after being created and is mainly used to create a private scope and avoid global namespace pollution.”

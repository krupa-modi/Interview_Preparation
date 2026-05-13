# 📌 JavaScript Currying Function – Complete Interview Notes

## 🔹 What is Currying?

Currying ek technique hai jisme:

👉 Multiple arguments lene wale function ko
👉 Multiple single-argument functions me convert kiya jata hai.
👉 currying is a function where function take a one argument at a time and return another function until all arguments are received.

Simple words me:

```js
f(a, b, c)
```

ko convert karte hain:

```js
f(a)(b)(c)
```

---

# 🔥 Real Meaning

Normally:

```js
sum(1, 2, 3)
```

Currying ke baad:

```js
sum(1)(2)(3)
```

Har function next argument return karta hai.

---

# 🔹 Basic Example

```js
function add(a) {
  return function (b) {
    return a + b;
  };
}

console.log(add(2)(3));
```

## ✅ Output

```js
5
```
---

# 🔹 Example with 3 Arguments

```js
function multiply(a) {
  return function (b) {
    return function (c) {
      return a * b * c;
    };
  };
}

console.log(multiply(2)(3)(4));
```

## ✅ Output

```js
24
```

---

# 🔥 ES6 Arrow Function Version

```js
const multiply = (a) => (b) => (c) => a * b * c;

console.log(multiply(2)(3)(4));
```

---

# 📌 Why Currying is Used?

Currying ka main use:

## ✅ 1️⃣ Reusability

```js
function greet(greeting) {
  return function (name) {
    return `${greeting} ${name}`;
  };
}

const sayHello = greet("Hello");

console.log(sayHello("Krupa"));
console.log(sayHello("Rahul"));
```

## ✅ Output

```js
Hello Krupa
Hello Rahul
```

Yaha `"Hello"` baar baar pass nahi karna pada.

---

# ✅ 2️⃣ Function Reusability

```js
const add = (a) => (b) => a + b;

const add10 = add(10);

console.log(add10(5));
console.log(add10(20));
```

## ✅ Output

```js
15
30
```

---

# ✅ 3️⃣ Functional Programming

React aur advanced JavaScript libraries me currying bahot use hoti hai.

Examples:

* Redux
* Ramda
* Lodash
* Functional programming

---

# 🔹 Currying vs Normal Function

| Normal Function        | Curried Function      |
| ---------------------- | --------------------- |
| `sum(1,2,3)`           | `sum(1)(2)(3)`        |
| Multiple args ek saath | Ek argument at a time |
| Less reusable          | More reusable         |
| Simple syntax          | Functional style      |

---

# 🔥 Important Interview Example

## Without Currying

```js
function discount(price, percentage) {
  return price - price * percentage;
}

console.log(discount(1000, 0.1));
```

---

## With Currying

```js
function discount(percentage) {
  return function (price) {
    return price - price * percentage;
  };
}

const tenPercentDiscount = discount(0.1);

console.log(tenPercentDiscount(1000));
console.log(tenPercentDiscount(2000));
```

---

# 📌 Infinite Currying (Very Important 🔥)

Interview me bahot puchte hain.

Example:

```js
sum(1)(2)(3)(4)()
```

---

# ✅ Solution

```js
function sum(a) {
  return function (b) {
    if (b !== undefined) {
      return sum(a + b);
    }
    return a;
  };
}

console.log(sum(1)(2)(3)(4)());
```

## ✅ Output

```js
10
```
---

# 📌 Currying using bind()

JavaScript me `bind()` se bhi currying kar sakte hain.

```js
function multiply(a, b) {
  return a * b;
}

const double = multiply.bind(this, 2);

console.log(double(5));
```

## ✅ Output

```js
10
```

Yaha:

```js
multiply.bind(this, 2)
```

means:

```js
a = 2 fixed
```

---

# 🔥 Real World Example

## Event Handling

```js
function handleEvent(type) {
  return function (event) {
    console.log(`${type}: ${event}`);
  };
}

const clickHandler = handleEvent("click");

clickHandler("button clicked");
```

---

# 📌 Advantages of Currying

| Advantage              | Explanation                      |
| ---------------------- | -------------------------------- |
| Reusability            | Same function multiple jagah use |
| Cleaner code           | Repeated arguments avoid         |
| Functional programming | Advanced JS concepts me useful   |
| Better abstraction     | Logic reusable hota hai          |
| Partial application    | Some values pre-fill kar sakte   |

---

# 📌 Disadvantages

| Disadvantage       | Explanation                      |
| ------------------ | -------------------------------- |
| Complex syntax     | Beginners ko confusing lagta     |
| Too many functions | Readability kabhi kabhi kam hoti |
| Debugging hard     | Nested functions hote            |

---

# 🔥 Currying vs Partial Application

## Currying

```js
sum(1)(2)(3)
```

Every function ek hi argument leta hai.

---

## Partial Application

```js
sum(1, 2)(3)
```

Some arguments pehle pass karte hain.

---

# 📌 Most Important Interview Points

## ✅ Definition

> Currying is a technique where a function with multiple arguments is transformed into a sequence of functions each taking one argument at a time.

---

## ✅ Why use currying?

* Reusability
* Functional programming
* Partial application
* Cleaner code

---

## ✅ Difference from normal function?

Normal function multiple arguments ek saath leti hai, curried function ek-ek argument leti hai.

---

## ✅ Real-world uses

* React handlers
* Redux middleware
* Functional programming
* Reusable utilities

---

# 🔥 Advanced Interview Question

## Q) Output Predict karo

```js
function add(a) {
  return function (b) {
    return function (c) {
      console.log(a + b + c);
    };
  };
}

add(1)(2)(3);
```

## ✅ Output

```js
6
```

---

# 📌 Important One-Line Interview Answer

> Currying converts a function with multiple arguments into nested functions that take one argument at a time.

---

# 🔥 Final Summary

| Topic             | Key Point                                   |
| ----------------- | ------------------------------------------- |
| Currying          | Function → nested single argument functions |
| Syntax            | `fn(a)(b)(c)`                               |
| Main benefit      | Reusability                                 |
| Uses              | Functional programming                      |
| Important concept | Closure                                     |
| Advanced topic    | Infinite currying                           |

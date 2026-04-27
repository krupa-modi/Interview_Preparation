## 1. What is JavaScript?

JavaScript is a **high-level, interpreted programming language** used to make web pages interactive. It runs in the browser and on servers (via Node.js).

---

## 2. Difference between `let`, `const`, and `var`

| Feature    | var             | let       | const     |
| ---------- | --------------- | --------- | --------- |
| Scope      | Function        | Block     | Block     |
| Re-declare | ✅ Yes           | ❌ No      | ❌ No      |
| Re-assign  | ✅ Yes           | ✅ Yes     | ❌ No      |
| Hoisting   | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |

**Best Practice:**

* Use `const` by default
* Use `let` if value changes
* Avoid `var`

---

## 3. Difference between `==` and `===`

* `==` → **Loose equality** (does type conversion)
* `===` → **Strict equality** (no type conversion)

```js
5 == "5"   // true
5 === "5"  // false
```

**Best Practice:** Always use `===`

---

## 4. How to check type of a variable?

Use `typeof` operator:

```js
typeof "hello"   // "string"
typeof 10        // "number"
typeof true      // "boolean"
typeof {}        // "object"
typeof []        // "object"
```

👉 Note: Arrays return `"object"`

---

# `this` Keyword in JavaScript (Interview Notes)

## What is `this`?

`this` refers to the **object that is currently executing the function**.
Its value depends on **how the function is called**, not where it is written.

---

## 1. Global Context

```js
console.log(this);
```

* In browser → `window`
* In strict mode → `undefined`

---

## 2. Inside a Regular Function

```js
function show() {
  console.log(this);
}
show();
```

* Non-strict mode → `window`
* Strict mode → `undefined`

👉 **Why undefined?**
In strict mode, JavaScript avoids default binding to global object to prevent mistakes.

---

## 3. Inside an Object Method

```js
const user = {
  name: "Krupa",
  greet() {
    console.log(this.name);
  }
};
user.greet(); // Krupa
```

👉 Here, `this` refers to the **object (`user`) calling the method**

---

## 4. Inside Arrow Function ❗ (Important Interview Point)

```js
const user = {
  name: "Krupa",
  greet: () => {
    console.log(this.name);
  }
};
user.greet(); // undefined
```

👉 **Why `undefined` in arrow function?**

* Arrow functions **do NOT have their own `this`**
* They take `this` from **parent (lexical scope)**

In this case:

* Parent = global scope
* Global `this` → `window`
* `window.name` → usually `undefined`

---

## 5. Arrow Function inside Method (Correct Use)

```js
const user = {
  name: "Krupa",
  greet() {
    const inner = () => {
      console.log(this.name);
    };
    inner();
  }
};
user.greet(); // Krupa
```

👉 Arrow function inherits `this` from `greet()` method

---

## Key Differences (Regular vs Arrow)

| Feature        | Regular Function | Arrow Function    |
| -------------- | ---------------- | ----------------- |
| Own `this`     | ✅ Yes            | ❌ No              |
| `this` value   | Depends on call  | From parent scope |
| Use in objects | Good for methods | Not for methods   |

---

## Interview One-Line Answer

👉 "`this` refers to the object that calls the function, and its value is determined at runtime. In arrow functions, `this` is inherited from the surrounding scope."





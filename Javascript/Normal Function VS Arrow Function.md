# 📘 Difference Between Normal Function and Arrow Function in JavaScript

JavaScript provides two ways to create functions:

1. Normal Function
2. Arrow Function (ES6)

Both are used to write reusable code,
but they behave differently internally.

---

# 1️⃣ Normal Function

## ✅ Definition

A traditional way of creating functions in JavaScript.

---

# ✅ Syntax

```js id="r8tw88"
function greet() {
  console.log("Hello");
}
```

---

# ✅ Function Expression

```js id="v48jko"
const greet = function() {
  console.log("Hello");
};
```

---

# 2️⃣ Arrow Function

## ✅ Definition

Arrow functions are shorter syntax introduced in ES6.

---

# ✅ Syntax

```js id="0p6m2g"
const greet = () => {
  console.log("Hello");
};
```

---

# ✅ Short Syntax

```js id="e7cl4l"
const add = (a, b) => a + b;
```

---

# 🔥 Main Difference Overview

| Feature            | Normal Function | Arrow Function |
| ------------------ | --------------- | -------------- |
| Syntax             | Traditional     | Short          |
| Own `this`         | Yes             | No             |
| Constructor        | Yes             | No             |
| `arguments` object | Yes             | No             |
| Hoisting           | Fully hoisted   | Depends        |
| Best Use           | Object methods  | Callbacks      |
| `super`            | Yes             | No             |
| `new` keyword      | Works           | Error          |

---

# 3️⃣ Difference in Syntax

---

# ✅ Normal Function

```js id="l1e8cg"
function add(a, b) {
  return a + b;
}
```

---

# ✅ Arrow Function

```js id="djlwm5"
const add = (a, b) => {
  return a + b;
};
```

---

# ✅ Implicit Return

Arrow functions can return directly.

```js id="jlwm7d"
const add = (a, b) => a + b;
```

---

# 🎯 Interview Point

```text id="jlwm9e"
Arrow functions provide cleaner and shorter syntax.
```

---

# 4️⃣ Difference in `this`

# 🔥 MOST IMPORTANT INTERVIEW QUESTION

---

# ✅ Normal Function has its own `this`

```js id="jlwm1f"
const user = {
  name: "John",

  greet: function() {
    console.log(this.name);
  }
};

user.greet();
```

---

# ✅ Output

```js id="jlwm3g"
John
```

---

# 📌 Here

```js id="jlwm5h"
this = user object
```

---

# ❌ Arrow Function Does NOT Have Own `this`

```js id="jlwm7i"
const user = {
  name: "John",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

---

# ✅ Output

```js id="jlwm9j"
undefined
```

---

# 📌 Why?

Arrow functions inherit `this`
from surrounding scope.

---

# 🔥 Important Line

```text id="jlwm1k"
Arrow functions use lexical `this`.
```

---

# 📌 Lexical `this`

Means:

```text id="jlwm3l"
`this` comes from parent scope.
```

---

# 🔥 Real Interview Example

---

# ❌ Problem with Normal Function

```js id="jlwm5m"
const user = {
  name: "John",

  greet() {

    setTimeout(function() {
      console.log(this.name);
    }, 1000);

  }
};

user.greet();
```

---

# ❌ Output

```js id="jlwm7n"
undefined
```

---

# ✅ Solution Using Arrow Function

```js id="jlwm9o"
const user = {
  name: "John",

  greet() {

    setTimeout(() => {
      console.log(this.name);
    }, 1000);

  }
};
```

---

# ✅ Output

```js id="jlwm1p"
John
```

---

# 📌 Why?

Arrow function inherits `this`
from `greet()`.

---

# 5️⃣ Difference in `arguments` Object

---

# ✅ Normal Function has `arguments`

```js id="jlwm3q"
function test() {
  console.log(arguments);
}

test(1, 2, 3);
```

---

# ✅ Output

```js id="jlwm5r"
[1, 2, 3]
```

---

# ❌ Arrow Function has NO `arguments`

```js id="jlwm7s"
const test = () => {
  console.log(arguments);
};

test(1, 2, 3);
```

---

# ❌ Output

```text id="jlwm9t"
ReferenceError
```

---

# ✅ Alternative

Use rest operator.

```js id="jlwm1u"
const test = (...args) => {
  console.log(args);
};
```

---

# 6️⃣ Constructor Function Difference

---

# ✅ Normal Function Works with `new`

```js id="jlwm3v"
function User(name) {
  this.name = name;
}

const u1 = new User("John");
```

---

# ❌ Arrow Function Cannot Be Constructor

```js id="jlwm5w"
const User = (name) => {
  this.name = name;
};

const u1 = new User("John");
```

---

# ❌ Error

```text id="jlwm7x"
User is not a constructor
```

---

# 🎯 Interview Point

```text id="jlwm9y"
Arrow functions cannot be used as constructors.
```

---

# 7️⃣ Hoisting Difference

---

# ✅ Normal Function Hoisted Completely

```js id="jlwm1z"
sayHello();

function sayHello() {
  console.log("Hello");
}
```

Works successfully.

---

# ❌ Arrow Function Hoisting

```js id="jlwm3a"
sayHello();

const sayHello = () => {
  console.log("Hello");
};
```

---

# ❌ Error

```text id="jlwm5b"
Cannot access before initialization
```

---

# 📌 Why?

Arrow functions usually stored in:

```js id="jlwm7c"
const
```

which are not fully hoisted.

---

# 8️⃣ Difference in Methods

---

# ✅ Normal Function for Object Methods

```js id="jlwm9d"
const user = {
  name: "John",

  greet() {
    console.log(this.name);
  }
};
```

---

# ❌ Arrow Function Not Recommended

```js id="jlwm1e"
const user = {
  name: "John",

  greet: () => {
    console.log(this.name);
  }
};
```

---

# 📌 Because arrow functions don't bind object `this`.

---

# 9️⃣ Return Behavior

---

# ✅ Normal Function

Needs explicit return.

```js id="jlwm3f"
function add(a, b) {
  return a + b;
}
```

---

# ✅ Arrow Function

Can use implicit return.

```js id="jlwm5g"
const add = (a, b) => a + b;
```

---

# 🔟 Use Cases

---

# ✅ Use Normal Function When

* Object methods
* Constructors
* Dynamic `this`
* Prototype methods

---

# ✅ Use Arrow Function When

* Callbacks
* Array methods
* React functional components
* Short utility functions

---

# 📘 Array Method Example

```js id="jlwm7h"
const nums = [1, 2, 3];

const result = nums.map(num => num * 2);
```

---

# 📘 Event Listener Example

---

# ✅ Better with Normal Function

```js id="jlwm9i"
button.addEventListener("click", function() {
  console.log(this);
});
```

---

# ❌ Arrow Function Issue

```js id="jlwm1j"
button.addEventListener("click", () => {
  console.log(this);
});
```

`this` will not refer to button.

---

# 🔥 Internal Behavior Difference

| Feature               | Normal Function | Arrow Function |
| --------------------- | --------------- | -------------- |
| Own execution context | Yes             | No             |
| Own `this`            | Yes             | No             |
| Own `arguments`       | Yes             | No             |
| Prototype property    | Yes             | No             |

---

# 🔥 Performance Difference

Very small difference.

Usually not important in interviews.

Choice depends more on behavior.

---

# 🎯 Most Asked Interview Questions

---

# ✅ Q1. What is main difference between normal and arrow function?

Arrow functions do not have their own `this`.

---

# ✅ Q2. Can arrow functions be constructors?

❌ No.

---

# ✅ Q3. Do arrow functions have `arguments` object?

❌ No.

---

# ✅ Q4. Why arrow functions are used in callbacks?

Because they inherit `this` from parent scope.

---

# ✅ Q5. Are arrow functions hoisted?

Not like normal functions.

---

# 🔥 Common Mistakes

| Mistake                                    | Problem           |
| ------------------------------------------ | ----------------- |
| Arrow function as object method            | Wrong `this`      |
| Using `new` with arrow function            | Error             |
| Using arrow function in DOM event handlers | Unexpected `this` |

---

# 🎯 Golden Interview Lines

```text id="jlwm3k"
Arrow functions inherit `this` from their lexical scope.
```

---

```text id="jlwm5l"
Normal functions have their own `this`, while arrow functions do not.
```

---

```text id="jlwm7m"
Arrow functions are best for callbacks, while normal functions are better for object methods and constructors.
```

---

# 🚀 Final Summary

| Topic       | Normal Function      | Arrow Function            |
| ----------- | -------------------- | ------------------------- |
| Syntax      | Longer               | Shorter                   |
| Own `this`  | Yes                  | No                        |
| Constructor | Yes                  | No                        |
| `arguments` | Yes                  | No                        |
| Hoisting    | Full                 | Partial                   |
| Best For    | Methods/constructors | Callbacks/short functions |

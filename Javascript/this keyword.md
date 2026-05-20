# 📘 `this` Keyword in JavaScript – Complete Interview Notes

---

# 🔹 What is `this`?

`this` is a special keyword in JavaScript that refers to:

```text id="g2c6bo"
The object that is currently executing the function.
```

---

# 📌 Simple Definition

```text id="9zv02m"
`this` refers to the current execution context.
```

---

# 🔥 Important Point

The value of `this` depends on:

```text id="5jlwmu"
How the function is called
```

NOT where the function is written.

---

# 🔥 Why `this` is Important?

Used for:

* Accessing object properties
* Reusing functions
* OOP concepts
* Event handling
* Classes
* React class components

---

# 1️⃣ `this` in Global Scope

---

# ✅ Browser

```js id="1cd8gh"
console.log(this);
```

Output:

```js id="jszmxb"
window
```

Because global object in browser = `window`.

---

# ✅ Node.js

Output:

```js id="p9h7q4"
{}
```

(Node module object)

---

# 🔥 Global Example

```js id="xmq5wm"
var name = "John";

console.log(this.name);
```

Output in browser:

```js id="jlwmn4"
John
```

---

# 2️⃣ `this` Inside Normal Function

---

# ✅ Example

```js id="jlwm8x"
function show() {
  console.log(this);
}

show();
```

---

# 📌 Browser Output

```js id="jlwm4z"
window
```

---

# 📌 Strict Mode Output

```js id="qjlwm9"
undefined
```

---

# ✅ Strict Mode Example

```js id="jlwmn1"
"use strict";

function test() {
  console.log(this);
}

test();
```

Output:

```js id="9jlwmv"
undefined
```

---

# 🎯 Interview Point

```text id="jlwm4k"
In strict mode, `this` inside normal functions becomes undefined.
```

---

# 3️⃣ `this` Inside Object Method

---

# ✅ Example

```js id="jlwm7a"
const user = {
  name: "John",

  greet() {
    console.log(this.name);
  }
};

user.greet();
```

---

# ✅ Output

```js id="2jlwmf"
John
```

---

# 📌 Why?

Here:

```js id="jlwm8n"
this = user object
```

because function called using:

```js id="jlwmp3"
user.greet()
```

---

# 🔥 Important Rule

```text id="jlwme8"
Object before dot becomes `this`.
```

---

# 4️⃣ `this` in Arrow Functions

---

# 🔹 Most Important Interview Topic

Arrow functions do NOT have their own `this`.

They inherit `this` from parent scope.

---

# ✅ Example

```js id="zjlwm1"
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

```js id="jlwm0m"
undefined
```

---

# 📌 Why?

Arrow function gets `this` from surrounding/global scope.

NOT from object.

---

# ✅ Correct Approach

```js id="jlwm1z"
const user = {
  name: "John",

  greet() {
    console.log(this.name);
  }
};
```

---

# 🔥 Arrow Function Use Cases

✅ Best for:

* Callbacks
* setTimeout
* Array methods

---

# ❌ Avoid in:

* Object methods
* Constructors

---

# 5️⃣ `this` in Event Handlers

---

# ✅ Example

```html id="jlwm7m"
<button id="btn">Click</button>
```

```js id="jlwmm9"
document
.getElementById("btn")
.addEventListener("click", function() {
  console.log(this);
});
```

---

# ✅ Output

```text id="jlwm0w"
Clicked button element
```

---

# 📌 Rule

In event listener:

```text id="jlwmf2"
`this` refers to the element that triggered event.
```

---

# ❌ Arrow Function Problem

```js id="jlwmc8"
button.addEventListener("click", () => {
  console.log(this);
});
```

Arrow function does not bind button.

---

# 6️⃣ `this` in Constructor Functions

---

# ✅ Example

```js id="9jlwmm"
function User(name) {
  this.name = name;
}

const user1 = new User("John");

console.log(user1.name);
```

---

# 📌 Here

```js id="jlwmv8"
this = newly created object
```

---

# 🔥 `new` Keyword Does

1. Creates empty object
2. Sets `this`
3. Returns object

---

# 7️⃣ `this` in Classes

---

# ✅ Example

```js id="jlwmw2"
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(this.name);
  }
}

const p1 = new Person("John");

p1.greet();
```

---

# ✅ Output

```js id="3jlwmx"
John
```

---

# 📌 In Classes

`this` refers to class instance.

---

# 8️⃣ Explicit Binding of `this`

JavaScript allows manual control of `this`.

Using:

* call()
* apply()
* bind()

# 🔥 Real Interview Example

---

# ❌ Problem

```js id="9jlwmk"
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

```js id="jlwmc5"
undefined
```

---

# ✅ Solution Using Arrow Function

```js id="jlwme0"
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

```js id="jlwmz1"
John
```

---

# 📌 Why?

Arrow function inherits `this`
from `greet()`.

---

# 🔥 Most Asked Interview Questions

---

# ✅ Q1. What is `this` in JavaScript?

It refers to current execution context/object.

---

# ✅ Q2. Does arrow function have its own `this`?

❌ No.

---

# ✅ Q3. What determines value of `this`?

How function is called.

---

# ✅ Q4. What is `this` in object method?

The object before dot.

---

# ✅ Q5. Difference between normal and arrow function `this`?

| Normal Function | Arrow Function   |
| --------------- | ---------------- |
| Own `this`      | Inherited `this` |

---

# ✅ Q6. What is explicit binding?

Manually setting `this` using call/apply/bind.

---

# 🔥 Common Mistakes

| Mistake                             | Problem        |
| ----------------------------------- | -------------- |
| Arrow methods in objects            | Wrong `this`   |
| Forgetting bind                     | Lost context   |
| Using normal function in setTimeout | `this` changes |

---

# 🎯 Golden Interview Lines

```text id="jlwm3c"
The value of `this` depends on how a function is invoked.
```

---

```text id="jlwmu1"
Arrow functions inherit `this` from their lexical scope.
```

---

# 🚀 Final Summary

| Situation       | Value of `this`    |
| --------------- | ------------------ |
| Global scope    | window/global      |
| Normal function | window / undefined |
| Object method   | Object itself      |
| Arrow function  | Parent scope       |
| Constructor     | New object         |
| Event listener  | Triggered element  |
| Class method    | Class instance     |

````md id="k8x2qp"
# ✅ JavaScript `this` Keyword (Interview Notes)

# ✅ What is `this`?

`this` refers to the object that is currently executing the function.

Its value depends on how the function is called.

---

# ✅ 1. `this` in Global Scope

In browser global scope,
`this` refers to the `window` object.

---

# ✅ Example

```js
console.log(this);
````

## ✅ Output (Browser)

```js id="m7p2vx"
window
```

---

# 🎯 Interview Definition

> In global scope, `this` refers to the global object (`window` in browsers).

---

# ✅ 2. `this` in Function

In a normal function,
`this` refers to the global object in non-strict mode.

---

# ✅ Example

```js id="p4m8tw"
function test() {
  console.log(this);
}

test();
```

## ✅ Output (Browser)

```js id="v7q1la"
window
```

---

# ⚠️ Strict Mode

```js id="k5r2vt"
"use strict";

function test() {
  console.log(this);
}

test();
```

## ✅ Output

```js id="x2m9pw"
undefined
```

---

# 🎯 Interview Definition

> In a regular function, `this` refers to the global object in non-strict mode and `undefined` in strict mode.

---

# ✅ 3. `this` in Object Method

Inside an object method,
`this` refers to the current object.

---

# ✅ Example

```js id="f8x2lm"
const user = {

  name: "Aman",

  greet: function() {
    console.log(this.name);
  }
};

user.greet();
```

## ✅ Output

```js id="r4p7qa"
Aman
```

---

# 🔍 Explanation

```js id="z6m1tw"
this = user object
```

---

# 🎯 Interview Definition

> Inside an object method, `this` refers to the object calling the method.

---

# ✅ 4. `this` in Arrow Function

Arrow functions do NOT have their own `this`.

They inherit `this` from the parent scope.

---

# ✅ Example

```js id="c2q8vp"
const user = {

  name: "Aman",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

## ✅ Output

```js id="j7p3lx"
undefined
```

---

# 🔍 Explanation

Arrow function ka own `this` nahi hota.

It uses lexical `this`
(from parent scope).

---

# ✅ Best Example

```js id="m9q2wr"
const user = {

  name: "Aman",

  greet: function() {

    setTimeout(() => {
      console.log(this.name);
    }, 1000);

  }
};

user.greet();
```

## ✅ Output

```js id="s5x8tv"
Aman
```

---

# 🎯 Interview Definition

> Arrow functions do not bind their own `this`; they inherit it from the surrounding scope.

---

# 🚀 Quick Revision Table

| Situation       | Value of `this`        |
| --------------- | ---------------------- |
| Global scope    | `window`               |
| Normal function | `window` / `undefined` |
| Object method   | Current object         |
| Arrow function  | Parent scope `this`    |

---

# 💡 One-Line Memory Trick

```js id="w1m4qp"
Normal function → own this

Arrow function → parent this
```


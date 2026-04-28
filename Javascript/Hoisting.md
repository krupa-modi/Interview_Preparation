
# Hoisting in JavaScript

## What is Hoisting?

Hoisting is JavaScript's default behavior of **moving declarations to the top of their scope** during the memory creation phase.
Hoisting means JavaScript moves variable and function declarations to the top of their scope before execution.

Note:- function expression and class expression is not hoistinh.
Example:- var greet = function(){
console.log("hello")
}
 Note:- this is the fubction expression using = and variable

---

## How it Works

Before execution, JS engine:

1. Allocates memory
2. Stores variables & functions

---

## Example

```js
console.log(a); // undefined
var a = 10;
```

👉 Internally:

```js
var a;
console.log(a); // undefined
a = 10;
```

---

## let & const (Temporal Dead Zone)

```js
console.log(a); // ReferenceError
let a = 10;
```

👉 They are hoisted but **not initialized** → TDZ

---

## Function Hoisting

```js
greet(); // Works

function greet() {
  console.log("Hello");
}
```

👉 Function declarations are fully hoisted

---

## Key Points

* `var` → hoisted (initialized with undefined)
* `let/const` → hoisted but in TDZ
* Functions → fully hoisted

---

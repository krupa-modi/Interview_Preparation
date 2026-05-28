
# Hoisting in JavaScript

## What is Hoisting?

Hoisting is JavaScript's default behavior of **moving declarations to the top of their scope** during the memory creation phase.
Hoisting means JavaScript moves variable and function declarations to the top of their scope before execution.

Note:- function expression and class expression is not hoisting.
Example:- var greet = function(){
console.log("hello")
}
 Note:- this is the function expression using = and variable

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
var a; // Declaration
console.log(a); // undefined
a = 10; // Assignment / Execution
```

---

## let & const (Temporal Dead Zone)

Temporal Dead Zone (TDZ)
* The time between variable hoisting and variable initialization is called Temporal Dead Zone.

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

* In hoisting, only declarations are hoisted, not assignments or execution. Variables declared with var are initialized as undefined during the memory creation phase, while the actual value assignment happens later during execution.

# Declaration vs Initialization vs Assignment vs Execution

# 1. Declaration

Variable banana (create karna) ko declaration bolte hai.

## Example

```js
var a;
````

Yaha:

* `a` variable declare hua hai
* Value abhi nahi di

---

# 2. Initialization

Variable ko first time value dena initialization hota hai.

## Example

```js
var a = 10;
```

Yaha:

```js
a = 10
```

first value assign hui → initialization

---

# 3. Assignment

Already existing variable ki value change karna assignment hota hai.

## Example

```js
var a = 10;

a = 20;
```

Yaha:

```js
a = 20
```

assignment hai.

---

# 4. Execution

Code run hona execution hota hai.

## Example

```js
console.log("Hello");
```

Browser is line ko run karega.

---

# Full Example

```js
var a;       // Declaration
a = 10;      // Initialization
a = 20;      // Assignment
console.log(a); // Execution
```

---

# Output

```js
20
```

---

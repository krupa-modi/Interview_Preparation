# 🚀 JavaScript Scope (Complete Interview Notes)

# 📌 What is Scope?

Scope defines where variables are accessible in JavaScript.

---

# 🔹 Types of Scope

1. Global Scope
2. Function Scope
3. Block Scope
4. Lexical Scope
5. Scope Chain

---

# ✅ 1. Global Scope

Variables declared outside any function or block are called global variables.

👉 Accessible from anywhere in the program.

---

# ✅ Example

```js
let name = "Krupa";

function show() {
  console.log(name);
}

show();
````

# ✅ Output

```js
Krupa
```

---

# 🎯 Interview Definition

> Global scope variables are accessible throughout the entire program.

---

# ✅ 2. Function Scope

Variables declared inside a function are accessible only inside that function.

👉 Applies to:

* `var`
* `let`
* `const`

---

# ✅ Example

```js
function test() {
  let age = 25;

  console.log(age);
}

test();

console.log(age); // ❌ ReferenceError
```

# ✅ Output

```js
25
```

---

# 🎯 Interview Definition

> Variables declared inside a function are function scoped and cannot be accessed outside the function.

---

# 🔥 Important Point About `var`

`var` is function scoped.

Even if declared inside `if`, it is accessible inside the whole function.

---

# ✅ Example

```js
function demo() {
  if (true) {
    var x = 100;
  }

  console.log(x);
}

demo();
```

# ✅ Output

```js
100
```

---

# ✅ 3. Block Scope

Variables declared with `let` and `const` inside `{}` are block scoped.

👉 Accessible only inside that block.

---

# ✅ Example

```js
{
  let city = "Pune";
  const country = "India";

  console.log(city);
  console.log(country);
}

console.log(city); // ❌ ReferenceError
console.log(country); // ❌ ReferenceError
```

# ✅ Output

```js
Pune
India
```

---

# ✅ Block Scope with if

```js
if (true) {
  let x = 50;
}

console.log(x); // ❌ ReferenceError
```

---

# ⚡ `var` vs Block Scope

```js
if (true) {
  var y = 100;
}

console.log(y);
```

# ✅ Output

```js
100
```

👉 Because `var` ignores block scope.

---

# 🎯 Interview Definition

> Variables declared using `let` and `const` inside a block are accessible only within that block.

---

# ✅ 4. Lexical Scope (VERY IMPORTANT 🔥)

Inner functions can access variables of their parent function.

---

# ✅ Example

```js
function outer() {
  let name = "Aman";

  function inner() {
    console.log(name);
  }

  inner();
}

outer();
```

# ✅ Output

```js
Aman
```

---

# 🔍 Explanation

`inner()` function can access `name`
because it is written inside `outer()`.

This is called lexical scope.

---

# 🎯 Interview Definition

> Lexical scope means a function can access variables from its parent scope.

---

# 💡 Interview One-Liner

> Lexical scope means scope is determined by where functions are written, not where they are called.

---

# ✅ 5. Scope Chain

When JavaScript cannot find a variable in the current scope,
it searches in parent scopes.

This process is called scope chain.

---

# ✅ Example

```js
let a = 10;

function outer() {
  let b = 20;

  function inner() {
    let c = 30;

    console.log(a, b, c);
  }

  inner();
}

outer();
```

# ✅ Output

```js
10 20 30
```

---

# 🔍 How JS Searches

`inner()` searches variables like this:

1. First → current scope (`c`)
2. Then → parent scope (`b`)
3. Then → global scope (`a`)

This searching process is called scope chain.

---

# 🎯 Interview Definition

> Scope chain is the process of searching variables from current scope to parent scopes until found.

---

# ⚡ TDZ (Temporal Dead Zone)

TDZ happens with `let` and `const`.

Variables are hoisted,
but cannot be accessed before initialization.

---

# ✅ Example

```js
{
  console.log(a); // ❌ ReferenceError

  let a = 10;
}
```

---

# 🔍 Explanation

👉 `a` exists in memory

👉 But not initialized yet

👉 So JavaScript throws TDZ error

---

# 🎯 Interview Definition

> Temporal Dead Zone is the time between variable hoisting and initialization where `let` and `const` cannot be accessed.

---

# ⚔️ Block Scope vs Function Scope

| Feature        | Block Scope (`let`, `const`) | Function Scope (`var`) |
| -------------- | ---------------------------- | ---------------------- |
| Scope Type     | Block `{}`                   | Function               |
| Accessibility  | Inside block only            | Entire function        |
| Hoisting       | Yes (TDZ applies)            | Yes (`undefined`)      |
| Re-declaration | ❌ Not allowed                | ✅ Allowed              |
| Best Practice  | ✅ Recommended                | ❌ Avoid                |

---

# 🔥 Combined Example (VERY IMPORTANT)

```js
function example() {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }

  console.log(a); // ✅ 1
  console.log(b); // ❌ ReferenceError
  console.log(c); // ❌ ReferenceError
}

example();
```

---

# 🚀 Quick Revision Table

| Scope Type     | Meaning                         |
| -------------- | ------------------------------- |
| Global Scope   | Accessible everywhere           |
| Function Scope | Accessible inside function only |
| Block Scope    | Accessible inside block only    |
| Lexical Scope  | Child accesses parent variables |
| Scope Chain    | JS searches variables upward    |

---

# 💡 Golden Rule

```js
Inner function can access outer variables,
but outer function cannot access inner variables.
```

---

# ✅ Best Practice

✅ Always use:

```js
let
const
```

❌ Avoid:

```js
var
```

because:

* causes confusion
* ignores block scope
* allows re-declaration
* creates bugs

---

# 🎯 Final Interview Summary

## 🔥 Global Scope

Accessible everywhere.

## 🔥 Function Scope

Variables accessible only inside function.

## 🔥 Block Scope

`let` and `const` work only inside `{}`.

## 🔥 Lexical Scope

Child function can access parent variables.

## 🔥 Scope Chain

JS searches variables from current scope to parent scopes.

## 🔥 TDZ

`let` and `const` cannot be accessed before initialization.

---



# 🚀 2. Scope in JavaScript

Scope defines **where variables are accessible**

---

# 🔹 Types of Scope

1. Global Scope
2. Function Scope
3. Block Scope

---

# 🔥 3. Function Scope

## 📌 Definition

Variables declared inside a function are accessible **only within that function**

👉 Applies to:

* `var`
* `let`
* `const`

---

## ⚙️ Example

```js
function test() {
  var a = 10;
  console.log(a); // ✅ 10
}

test();
console.log(a); // ❌ ReferenceError
```

---

## 🧠 Key Concept

👉 `var` is **function scoped**

```js
function demo() {
  if (true) {
    var x = 100;
  }

  console.log(x); // ✅ 100
}
```

👉 Even though inside `if`, still accessible (because function scoped)

---

# 🔥 4. Block Scope

## 📌 Definition

Variables declared inside `{}` are accessible **only within that block**

👉 Applies to:

* `let`
* `const`

---

## ⚙️ Example

```js
{
  let a = 10;
  const b = 20;
}

console.log(a); // ❌ ReferenceError
console.log(b); // ❌ ReferenceError
```

---

## 🔥 Block Scope with if

```js
if (true) {
  let x = 50;
}

console.log(x); // ❌ ReferenceError
```

---

## ⚡ Difference from var

```js
if (true) {
  var y = 100;
}

console.log(y); // ✅ 100
```

👉 Because `var` ignores block scope

---

# ⚔️ 5. Block Scope vs Function Scope (Comparison)

| Feature        | Block Scope (`let`, `const`) | Function Scope (`var`) |
| -------------- | ---------------------------- | ---------------------- |
| Scope Type     | Block `{}`                   | Function               |
| Accessibility  | Only inside block            | Entire function        |
| Hoisting       | Yes (TDZ applies)            | Yes (`undefined`)      |
| Re-declaration | ❌ Not allowed                | ✅ Allowed              |
| Best Practice  | ✅ Recommended                | ❌ Avoid                |

---

# 🧠 6. Combined Example (VERY IMPORTANT 🔥)

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
```

---

# ⚡ 7. TDZ + Scope Together

```js
{
  console.log(a); // ❌ TDZ
  let a = 10;
}
```

👉 `a` exists in scope
👉 But not initialized → TDZ error

---

# 🎯 Final Summary (Interview Ready)

## 🔥 TDZ

* Exists between hoisting & initialization
* Only for `let` and `const`
* Throws ReferenceError

## 🔥 Function Scope

* `var` is function scoped
* Accessible anywhere inside function

## 🔥 Block Scope

* `let` and `const` are block scoped
* Restricted to `{}`

---

# 💡 Best Practice

✅ Always use:

```js
let / const
```

❌ Avoid:

```js
var
```

---

If you want, I can also give:

* 🔥 tricky interview questions on TDZ & scope
* 🔥 real-world debugging examples
* 🔥 MCQs for practice

Just tell me 👍
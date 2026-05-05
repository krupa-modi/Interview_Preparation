Here’s a **clean, interview-ready Markdown file** with **in-depth explanation** of **Temporal Dead Zone (TDZ)** and **Block Scope vs Function Scope in JavaScript** 👇

---

# 📘 JavaScript: TDZ & Scope (In-Depth Guide)

---

# 🔥 1. Temporal Dead Zone (TDZ)

## 📌 Definition

The **Temporal Dead Zone (TDZ)** is the time between:

* **Variable declaration is hoisted**
* **AND variable is initialized**

During this time, accessing the variable results in a **ReferenceError**.

---

## 🧠 Key Point

👉 TDZ only applies to:

* `let`
* `const`

👉 TDZ does **NOT apply to `var`**

---

## ⚙️ How it Works Internally

JavaScript Execution Phases:

### 1. Memory Phase (Hoisting)

* Variables are allocated memory
* `let` and `const` are **not initialized**

### 2. Execution Phase

* Values are assigned

---

## ❗ Example of TDZ

```js
console.log(a); // ❌ ReferenceError

let a = 10;
```

### 💡 Why?

* `a` is hoisted
* But NOT initialized
* So it's inside TDZ

---

## ✅ Correct Usage

```js
let a = 10;
console.log(a); // ✅ 10
```

---

## 🔥 TDZ with Block Scope

```js
{
  console.log(x); // ❌ ReferenceError (TDZ)
  let x = 5;
}
```

---

## ⚡ TDZ vs var

```js
console.log(a); // ✅ undefined
var a = 10;
```

👉 `var` is:

* Hoisted
* Initialized with `undefined`

---

## 🧩 Important Interview Points

* TDZ prevents accessing variables before initialization
* Makes code safer and predictable
* Applies only to `let` and `const`
* Happens due to hoisting but no initialization

---



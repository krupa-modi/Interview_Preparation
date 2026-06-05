# JavaScript: Declaration, Initialization, and Accessibility

## 🔹 1. Declaration

### 👉 Definition:
Declaration means **creating a variable** in memory.  
At this stage, JavaScript **reserves space** for the variable but does not assign a value (in most cases).

### 📌 Syntax:
```js
var a;
let b;
const c; // ❌ Error (must initialize)
````

### 🧠 Key Points:

* `var` → hoisted and initialized with `undefined`
* `let` and `const` → hoisted but not initialized (Temporal Dead Zone)
* `const` → must be initialized at declaration

---

## 🔹 2. Initialization

### 👉 Definition:

Initialization means **assigning a value** to a declared variable.

### 📌 Syntax:

```js
var a = 10;
let b = 20;
const c = 30;
```

### 🧠 Key Points:

* Happens after declaration
* `const` requires initialization immediately
* `let` and `var` can be initialized later

---

## 🔹 3. Accessibility (Scope)

### 👉 Definition:

Accessibility defines **where a variable can be used** in the code.

---

## 🔸 Types of Scope:

### 1. Global Scope

Accessible anywhere in the program.

```js
var a = 10;

function test() {
  console.log(a); // ✅ Accessible
}
```

---

### 2. Function Scope (`var`)

Accessible only inside the function.

```js
function test() {
  var x = 100;
}
console.log(x); // ❌ Error
```

---

### 3. Block Scope (`let`, `const`)

Accessible only inside `{ }`

```js
{
  let y = 200;
  const z = 300;
}
console.log(y); // ❌ Error
```

---

## 🔹 Hoisting + Accessibility Connection

### Example:

```js
console.log(a); // undefined
var a = 10;
```

```js
console.log(b); // ❌ ReferenceError
let b = 20;
```

### 🧠 Explanation:

* `var` → hoisted + initialized (`undefined`)
* `let` & `const` → hoisted but in **Temporal Dead Zone (TDZ)**

---

## 🔹 Full Example (Combined)

```js
// Declaration
let a;

// Initialization
a = 10;

// Accessibility
function test() {
  let b = 20;
  console.log(a); // ✅ Accessible (outer scope)
  console.log(b); // ✅ Accessible (inside function)
}

test();

console.log(a); // ✅
console.log(b); // ❌ Error (not accessible outside)
```

---

## 🔹 Summary Table

| Concept        | Meaning                    | Example     |
| -------------- | -------------------------- | ----------- |
| Declaration    | Variable creation          | `let a;`    |
| Initialization | Assign value               | `a = 10;`   |
| Accessibility  | Where variable can be used | Scope rules |

---

## 🔹 Important Notes

* `var` → function scoped + hoisted (safe but outdated)
* `let` → block scoped + TDZ (recommended)
* `const` → block scoped + must initialize (best for constants)

---

## 🚀 Final Understanding

* **Declaration** → "Variable ban gaya"
* **Initialization** → "Value assign ho gaya"
* **Accessibility** → "Kahan use kar sakte ho"

---

```

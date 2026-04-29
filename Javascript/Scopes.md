
# JavaScript Scopes (Quick Interview Notes)

## 1. Global Scope

Variables declared outside any function/block → accessible everywhere

```js
let name = "Krupa";

function show() {
  console.log(name);
}

show(); // Krupa
```

👉 `name` is global → can be used inside functions

---

## 2. Function Scope

Variables declared inside a function → accessible **only inside that function**

```js
function test() {
  let a = 10;
  console.log(a);
}

test(); // 10
console.log(a); // ❌ ReferenceError
```

👉 `a` is not accessible outside the function

---

## 3. Lexical Scope (Important 🔥)

Inner functions can access variables of their **outer (parent) functions**

```js
function outer() {
  let x = 10;

  function inner() {
    console.log(x);
  }

  inner();
}

outer(); // 10
```

👉 `inner()` can access `x` because of lexical scope

---

## Key Difference Summary

| Scope Type | Access                 |
| ---------- | ---------------------- |
| Global     | Everywhere             |
| Function   | Inside function only   |
| Lexical    | Inner can access outer |

---

## Interview One-Liner

👉 "Lexical scope means scope is determined by where functions are written, not where they are called."

---

If you want, I can give you **tricky scope-based interview questions** (very common in interviews 🔥).

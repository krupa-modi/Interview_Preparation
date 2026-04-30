## 🔹 1. What is `any`?

* which allows variable to hold value of any type.

`any` is a type in TypeScript that **disables type checking completely**.
When a variable is of type `any`, you can assign **any value** to it and perform **any operation** without errors.

### ✅ Key Points:

* Opt-out of type safety
* Can assign any type (string, number, object, etc.)
* No compile-time errors (even if code is wrong)

### 📌 Example:

```ts
let value: any = 10;

value = "Hello";   // ✅ allowed
value = true;      // ✅ allowed

console.log(value.toUpperCase()); // ❌ No error at compile time, but may crash at runtime
```

👉 Problem:
TypeScript does **not check anything**, so errors can occur at runtime.

---

## 🔹 2. What is `unknown`?

`unknown` is a **type-safe alternative to `any`**.
It can store any value, but **you cannot use it directly** without checking its type first.

### ✅ Key Points:

* Safer than `any`
* Requires **type checking (narrowing)** before usage
* Prevents runtime errors

### 📌 Example:

```ts
let value: unknown = 10;

value = "Hello";
value = true;

// ❌ Error
// console.log(value.toUpperCase()); 

// ✅ Correct way (type check)
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

👉 TypeScript forces you to **verify type before using it**.

---

## 🔥 3. Difference Between `any` and `unknown`

| Feature          | `any` 🚫 (Unsafe) | `unknown` ✅ (Safe) |
| ---------------- | ----------------- | ------------------ |
| Type Safety      | ❌ No checking     | ✅ Strict checking  |
| Assign any value | ✅ Yes             | ✅ Yes              |
| Use directly     | ✅ Yes             | ❌ No (need check)  |
| Runtime errors   | ⚠️ Possible       | ✅ Reduced          |
| Recommended      | ❌ Avoid           | ✅ Prefer           |

---

### ✅ Use `unknown` when:

* You don’t know the type in advance
* Handling API responses
* Want **safe code**

### ❌ Avoid `any` unless:

* You are migrating old JavaScript code
* Temporary usage during development

---

## 🎯 Final Interview Summary

* `any` → turns off TypeScript safety ❌
* `unknown` → safe version of `any` ✅
* Always prefer `unknown` over `any`
* `unknown` requires **type checking before use**

---

## 🧠 One-Line Difference

👉 `any` = "I don’t care about type"
👉 `unknown` = "I don’t know the type yet, but I’ll check it"

---

If you want, I can also give you **interview questions + tricky scenarios on `any` vs `unknown`** 🔥

## 🔹 What is Type Inference?

### 👉 Definition

**Type Inference** means TypeScript automatically **guesses the type** of a variable based on its value — so you don’t always need to explicitly define types.

---

## 🔹 Basic Example

```ts
let name = "John";
```

👉 TypeScript infers:

```ts
name: string
```

```ts
let age = 25;
```

👉 Inferred as:

```ts
age: number
```

---

## 🔹 Why Type Inference is Important?

* Reduces boilerplate code
* Improves readability
* Still provides type safety
* Makes development faster

---

# 🔹 Types of Type Inference

---

## 🔹 1. Variable Initialization Inference

```ts
let isActive = true;
```

👉 Inferred as:

```ts
boolean
```

⚠️ If no value is assigned:

```ts
let data;
```

👉 Inferred as:

```ts
any ❗ (unsafe)
```

---

## 🔹 2. Function Return Type Inference

```ts
function add(a: number, b: number) {
  return a + b;
}
```

👉 TypeScript infers:

```ts
function add(a: number, b: number): number
```

## 🔹 4. Array Inference

```ts
let numbers = [1, 2, 3];
```

👉 Inferred as:

```ts
number[]
```

---

### 👉 Mixed Array

```ts
let mixed = [1, "hello", true];
```

👉 Inferred as:

```ts
(string | number | boolean)[]
```

---

## 🔹 5. Object Inference

```ts
let user = {
  name: "John",
  age: 25
};
```

👉 Inferred as:

```ts
{
  name: string;
  age: number;
}
```

---

## 🔹 6. Literal Type Inference

```ts
let status = "success";
```

👉 Inferred as:

```ts
string ❗ (not "success")
```

# 🔹 Limitations of Type Inference

## ❌ 1. Too Generic (`any`)

## ❌ 2. Complex Logic

## ❌ 3. Narrowing Issues


# 🔹 Type Inference vs Explicit Typing

| Feature     | Type Inference | Explicit Typing |
| ----------- | -------------- | --------------- |
| Code Length | Shorter        | Longer          |
| Readability | Cleaner        | More clear      |
| Control     | Less control   | Full control    |
| Safety      | Good           | Best            |

---

# 🔹 When to Use Type Inference?

✅ Use when:

* Type is obvious
* Simple variables
* Short functions

---

# 🔹 When NOT to Use?

❌ Avoid when:

* Complex logic
* Public APIs
* Large applications
* Ambiguous values

---

# 🔥 Advanced Tip (Interview Level)

👉 Combine inference + explicit typing:

```ts
const users: string[] = ["A", "B"];
```

👉 OR let TS infer:

```ts
const users = ["A", "B"];
```
# 🔥 Final Summary

* TypeScript automatically guesses types
* Works for variables, functions, arrays, objects
* Saves time and reduces code
* But not always perfect → sometimes use explicit types
* Use `as const` for literal types

---

## 💡 Pro Tip

👉 Good developers:

* Use inference for **clean code**
* Use explicit types for **clarity & safety**

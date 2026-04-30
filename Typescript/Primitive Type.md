
# TypeScript Interview Notes – Core Types

---

## 1. Primitive Types in TypeScript

TypeScript provides basic built-in types similar to JavaScript, but with type safety.

### 1. string

Used for text values.

```ts
let name: string = "Krupa";
```

✔ Only string values allowed
❌ `name = 10` → Error

---

### 2. number

Represents all numeric values (integer, float, etc.)

```ts
let age: number = 25;
let price: number = 99.99;
```

✔ Supports all numbers
❌ `age = "twenty"` → Error

---

### 3. boolean

Represents true/false values.

```ts
let isLoggedIn: boolean = true;
```

✔ Only `true` or `false`

---

### 🔥 Key Interview Point:

> TypeScript enforces type safety on primitive types, preventing invalid assignments.

---


---

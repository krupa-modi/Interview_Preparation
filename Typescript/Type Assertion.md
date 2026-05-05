## 🔹 What is Type Assertion?

### 👉 Definition

**Type Assertion** is a way to tell TypeScript:

> “Trust me — I know the type better than you.”

It **overrides TypeScript’s inferred type** without changing the actual runtime value.

---

## 🔹 Syntax

### 👉 1. `as` syntax (Recommended ✅)

```ts id="1kq7f2"
let value: unknown = "Hello";

let strLength = (value as string).length;
```

---

### 👉 2. Angle Bracket syntax (Old ❌ not recommended in React)

```ts id="8u9l2m"
let value: unknown = "Hello";

let strLength = (<string>value).length;
```

⚠️ Not used in JSX (React) because of syntax conflicts.

---

# 🔹 Why Type Assertions are Used?

* When TypeScript **cannot infer correctly**
* When working with **DOM elements**
* When using **third-party libraries**
* When dealing with `unknown` or `any`

---

# 🔹 Basic Examples

---

## 🔹 Example 1: Unknown Type

```ts id="m6b2w8"
let data: unknown = "TypeScript";

let length = (data as string).length;
```

---

## 🔹 Example 2: DOM Handling (Very Important 🔥)

```ts id="7c0w2v"
const input = document.getElementById("username") as HTMLInputElement;

console.log(input.value);
```

👉 Without assertion:

```ts id="a8r3jh"
document.getElementById("username").value; // ❌ Error
```

---

## 🔹 Example 3: API Response

```ts id="f0x7d1"
type User = {
  name: string;
  age: number;
};

let response = {} as User;

response.name = "John";
response.age = 25;
```

---

# 🔹 Type Assertion vs Type Casting

👉 Important Interview Point

* TypeScript does **NOT perform real casting**
* It only **informs the compiler**

```ts id="4y2t9q"
let num = "123" as unknown as number;
```

👉 This does NOT convert string → number at runtime ❗

---

# 🔹 Double Assertion

```ts id="u2w9k0"
let value: unknown = "Hello";

let num = value as unknown as number;
```

👉 Used when:

* Direct assertion is not allowed
* But should be used carefully ⚠️

---

# 🔹 Type Assertion with Union Types

```ts id="3s8yq4"
let value: string | number = "Hello";

let length = (value as string).length;
```

---

# 🔹 Non-Null Assertion (`!`)

### 👉 Definition

Tells TypeScript that value is **not null or undefined**

```ts id="z1k8m7"
let input = document.getElementById("username")!;

input.innerHTML = "Hello";
```

⚠️ Dangerous if wrong — may cause runtime error.

---

# 🔹 Const Assertion (`as const`)

```ts id="g4p2x1"
let status = "success" as const;
```

👉 Inferred as:

```ts id="t7y8n3"
"success" (literal type)
```

---

# 🔹 Differences: Assertion vs Annotation

| Feature        | Type Assertion         | Type Annotation        |
| -------------- | ---------------------- | ---------------------- |
| Purpose        | Override inferred type | Define type explicitly |
| Safety         | Less safe ⚠️           | More safe ✅            |
| Syntax         | `as type`              | `: type`               |
| Runtime Impact | None                   | None                   |

---

# 🔹 When to Use Type Assertions?

✅ Use when:

* Working with DOM
* Handling `unknown`
* Interacting with external APIs
* TypeScript cannot infer properly

---

# 🔹 When NOT to Use?

❌ Avoid when:

* You are unsure of type
* It can cause runtime errors
* Better type definitions exist

---

# 🔥 Best Practices

* Prefer **type inference** when possible
* Use assertions only when necessary
* Avoid `any`
* Validate data before asserting

---

# 🔥 Final Summary

* Type Assertion = “Trust me, I know the type”
* Does NOT change runtime behavior
* Useful for DOM, APIs, unknown types
* Use `as` syntax (modern)
* Avoid overuse ⚠️

---

## 💡 Pro Tip (Interview Level)

👉 Safer alternative:

```ts id="n3q8w1"
if (typeof value === "string") {
  console.log(value.length);
}
```

✔ Uses **type narrowing instead of assertion**
✔ Safer and recommended


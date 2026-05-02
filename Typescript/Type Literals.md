## 🔹 What is a Type Literal?

A **Type Literal** is a way to define a type **inline (directly)** without giving it a separate name.

👉 Instead of creating a reusable alias, you define the structure **on the spot**.

---

## 🔹 Basic Syntax

```ts
let variable: { property: type };
```

---

## 🔹 Example: Object Type Literal

```ts
let user: { name: string; age: number };

user = {
  name: "Krupa",
  age: 22
};
```

👉 Here:

* `{ name: string; age: number }` is a **type literal**
* No separate `type` or `interface` is created

---

## 🔹 Type Literal in Function Parameter

```ts
function greet(user: { name: string; age: number }): string {
  return `Hello ${user.name}`;
}
```

👉 Used when:

* Type is small
* Not reused elsewhere

---

## 🔹 Type Literal with Optional Properties

```ts
let product: { name: string; price?: number };

product = {
  name: "Laptop"
};
```

👉 `price?` means optional

---

## 🔹 Type Literal with Readonly

```ts
let config: { readonly apiKey: string } = {
  apiKey: "123ABC"
};

// ❌ Error
config.apiKey = "456DEF";
```

---

## 🔹 Type Literal with Function Type

```ts
let add: (a: number, b: number) => number;

add = (x, y) => x + y;
```

---

## 🔹 Type Literal with Union

```ts
let status: "success" | "error" | "loading";

status = "success";
```

👉 This is also called a **string literal type**

---

## 🔹 Type Literal vs Type Alias 🔥

| Feature     | Type Literal        | Type Alias         |
| ----------- | ------------------- | ------------------ |
| Reusability | ❌ No                | ✅ Yes              |
| Naming      | ❌ No name           | ✅ Named            |
| Use Case    | Small, one-time use | Reusable structure |
| Readability | ❌ Can get messy     | ✅ Cleaner          |

---

## 🔹 When to Use Type Literal?

Use type literals when:

* Type is **simple and used once**
* You don’t want to create extra types
* Quick inline definitions

---

## 🔹 When NOT to Use?

Avoid when:

* Type is reused multiple times
* Structure is complex
* Code readability matters

👉 In those cases → use **type alias or interface**

## 🔹 Key Interview Points

* Type literal = **inline type definition**
* No separate name
* Common in:
  * Function parameters
  * Small objects
  * Can include:

  * Optional (`?`)
  * Readonly
  * Nested types
  * Union types

---

## 🔚 Conclusion

Type Literals are useful for:

* Quick definitions
* Small, non-reusable types

But for **scalability and clean code**, prefer:
👉 `type` or `interface`

---

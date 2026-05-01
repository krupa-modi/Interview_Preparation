
# 🔹 1. What is Type Narrowing?

## ✅ Definition

**Type Narrowing** is the process of **reducing a broad type into a more specific type**.

👉 TypeScript does this using conditions so it can safely determine:

## ✅ Why is Narrowing Needed?

When we use **Union Types (`|`)**, TypeScript doesn't know the exact type.

```ts id="kz1w2m"
function print(value: string | number) {
  // ❌ Error without narrowing
  console.log(value.toUpperCase());
}
```

👉 Problem:

* `toUpperCase()` works only on string
* But `value` can also be number

---

## ✅ Solution → Type Narrowing

```ts id="2wpxd4"
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase()); // ✅ string
  } else {
    console.log(value.toFixed(2)); // ✅ number
  }
}
```

👉 Now TypeScript understands the type correctly.

---

## 🔥 Key Idea

* Narrowing = **filtering down type**
* Happens at runtime using conditions
* Makes code **safe and predictable**

---

# 🔹 2. What is a Type Guard?

## ✅ Definition

A **Type Guard** is a **technique used to narrow down types**.

👉 It tells TypeScript:

> "Inside this block, the type is specific."

---

## 🔥 Simple Understanding

👉 Type Guard = Tool
👉 Narrowing = Result

---

# 🔹 3. Types of Type Guards

---

# ✅ 1. `typeof` Type Guard

👉 Used for **primitive types**

```ts id="5ktm2p"
function check(value: string | number | boolean) {
  if (typeof value === "string") {
    console.log("String:", value.toUpperCase());
  } else if (typeof value === "number") {
    console.log("Number:", value.toFixed(2));
  } else {
    console.log("Boolean:", value);
  }
}
```

---

# ✅ 2. `instanceof` Type Guard

👉 Used for **classes / objects**

```ts id="0lfnkj"
class Dog {
  bark() {
    console.log("Woof");
  }
}

class Cat {
  meow() {
    console.log("Meow");
  }
}

function speak(animal: Dog | Cat) {
  if (animal instanceof Dog) {
    animal.bark();
  } else {
    animal.meow();
  }
}
```

---

# ✅ 3. `in` Operator Type Guard

👉 Used to check **property existence**

```ts id="7i6y0l"
type Dog = { bark: () => void };
type Cat = { meow: () => void };

function speak(animal: Dog | Cat) {
  if ("bark" in animal) {
    animal.bark();
  } else {
    animal.meow();
  }
}
```

---

## What is narrowing?

👉 Process of converting a broad type into a specific type.

---

## What is a type guard?

👉 A method used to perform narrowing.

---

## Difference between narrowing & type guard?

👉 Narrowing = result
👉 Type guard = method

---

##  Types of type guards?

* `typeof`
* `instanceof`
* `in`
* Equality check
* User-defined


## What is discriminated union?

👉 Union with a common property for safe narrowing

---

## Why is narrowing important?

👉 Prevents runtime errors and ensures type safety

---

# 🔥 7. Summary

* Narrowing → makes type more specific
* Type Guard → technique to narrow type
* Most used:

  * `typeof`
  * `in`
  * `instanceof`
* Advanced:

  * User-defined type guards
  * Discriminated unions

---


# 📘 Discriminated Unions in TypeScript

---

# 🔹 1. What is a Discriminated Union?

## ✅ Definition

A **Discriminated Union** is a pattern where:

* Multiple types are combined using **Union (`|`)**
* Each type has a **common property (called discriminator)**
* That property has **unique literal values**

👉 This helps TypeScript **automatically narrow types safely**

---

## 🔥 Key Idea

👉 Union + Common Property + Literal Values = Discriminated Union

---

# 🔹 2. Basic Example

```ts id="2t4l2g"
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "square"; size: number };
```

👉 Here:

* `kind` = discriminator
* `"circle"` & `"square"` = literal types

---

## ✅ Usage Example

```ts id="rtsqnj"
function area(shape: Shape) {
  if (shape.kind === "circle") {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.size ** 2;
  }
}
```

👉 TypeScript automatically narrows:

* `"circle"` → radius available
* `"square"` → size available

---

# 🔹 3. Why Use Discriminated Union?

## ❌ Without Discriminated Union

```ts id="zqqi3s"
type Shape = {
  radius?: number;
  size?: number;
};

function area(shape: Shape) {
  // ❌ Unsafe (may be undefined)
}
```

👉 Problem:

* No type safety
* Possible runtime errors

---

## ✅ With Discriminated Union

✔ Safe
✔ Clear
✔ Predictable

---
# 🔹 6. Real World Example

## ✅ API Response Handling

```ts id="4npn4w"
type ApiResponse =
  | { status: "loading" }
  | { status: "success"; data: string }
  | { status: "error"; message: string };

function handleResponse(res: ApiResponse) {
  switch (res.status) {
    case "loading":
      return "Loading...";

    case "success":
      return res.data;

    case "error":
      return res.message;
  }
}
```

---

# 🔥 8. Rules of Discriminated Union

* Must have a **common property**
* Property must have **literal types**
* Each type must have **unique value**

## What is a discriminated union?

👉 A union of types with a common property used for type narrowing.

---

##  What is a discriminator?

👉 A common property (like `kind`, `type`, `status`)

---

## Why use discriminated union?

👉 For safe and predictable type narrowing

---

## Difference between union & discriminated union?

| Feature   | Union Type         | Discriminated Union |
| --------- | ------------------ | ------------------- |
| Safety    | Low                | High                |
| Narrowing | Manual             | Automatic           |
| Structure | No common property | Has common property |

---

## What is exhaustive checking?

👉 Ensuring all cases are handled using `never`

# 🔥 12. Summary

* Discriminated Union = **Safe Union**
* Uses a **common property**
* Helps TypeScript auto-narrow types
* Best used with:

  * `switch`
  * `never` (exhaustive check)

---


# 📘 Type Narrowing & Type Guards in TypeScript (Interview Guide)

---

# 🔹 1. What is Type Narrowing?

## ✅ Definition

**Type Narrowing** is the process of **reducing a broad type into a more specific type**.

👉 TypeScript does this using conditions so it can safely determine:

> "Which exact type are we dealing with right now?"

---

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

# ✅ 4. Equality Narrowing

```ts id="l1jkkd"
function example(value: string | null) {
  if (value !== null) {
    console.log(value.toUpperCase());
  }
}
```

---

# ✅ 5. Truthiness Narrowing

```ts id="c2e8m3"
function printLength(text?: string) {
  if (text) {
    console.log(text.length);
  }
}
```

👉 Removes:

* `undefined`
* `null`
* `false`
* `0`
* `""`

---

# 🔥 4. User-Defined Type Guard (VERY IMPORTANT 🔥)

## ✅ Definition

Custom function that tells TypeScript about type.

---

## ✅ Syntax

```ts id="z3fuv1"
function isType(value: any): value is Type {
  return condition;
}
```

---

## ✅ Example

```ts id="k8nv4s"
type Dog = { bark: () => void };
type Cat = { meow: () => void };

function isDog(animal: Dog | Cat): animal is Dog {
  return (animal as Dog).bark !== undefined;
}

function speak(animal: Dog | Cat) {
  if (isDog(animal)) {
    animal.bark(); // ✅
  } else {
    animal.meow(); // ✅
  }
}
```

---

# 🔥 5. Discriminated Union (BEST PRACTICE 🔥)

## ✅ Definition

Using a **common property** to narrow types safely.

---

## ✅ Example

```ts id="8q2zbf"
type Shape =
  | { type: "circle"; radius: number }
  | { type: "square"; size: number };

function area(shape: Shape) {
  if (shape.type === "circle") {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.size ** 2;
  }
}
```

👉 Most recommended in real projects

---

# 🔥 6. Common Interview Questions

---

## ❓ Q1: What is narrowing?

👉 Process of converting a broad type into a specific type.

---

## ❓ Q2: What is a type guard?

👉 A method used to perform narrowing.

---

## ❓ Q3: Difference between narrowing & type guard?

👉 Narrowing = result
👉 Type guard = method

---

## ❓ Q4: Types of type guards?

* `typeof`
* `instanceof`
* `in`
* Equality check
* User-defined

---

## ❓ Q5: What is user-defined type guard?

👉 Custom function using `value is Type`

---

## ❓ Q6: What is discriminated union?

👉 Union with a common property for safe narrowing

---

## ❓ Q7: Why is narrowing important?

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

# 🚀 Final Interview Tip

👉 MOST IMPORTANT:

* `typeof`
* `in`
* User-defined type guard
* Discriminated union

---

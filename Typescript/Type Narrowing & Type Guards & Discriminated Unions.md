
# Type Narrowing in TypeScript

## What is Type Narrowing?

Type Narrowing means:

> TypeScript kisi variable ka exact type identify karta hai based on conditions.

Simple words mein:

Agar variable multiple types hold kar sakta hai, to TypeScript conditions laga ke uska actual type samajhta hai.

---

# Why Type Narrowing Needed?

Example:

```ts id="f2s5qa"
function print(value: string | number) {
  console.log(value.toUpperCase());
}
```

## Error

```ts id="v5c9cz"
Property 'toUpperCase' does not exist on type 'string | number'
```

Why?

Because:

* `string` ke paas `toUpperCase()` hai
* `number` ke paas nahi hai

TypeScript ko exact type nahi pata.

---

# Solution → Type Narrowing

```ts id="ff4xxg"
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  }
}
```

Now TypeScript samaj gaya:

```ts id="8z6wqk"
value = string
```

inside if block.

This is called:

# Type Narrowing

---

# How Type Narrowing Works

TypeScript conditions check karta hai:

* typeof
* instanceof
* in operator
* equality checking
* truthy/falsy checking
* custom type guards

---

# 1. typeof Narrowing

Primitive types check karne ke liye.

---

# Syntax

```ts id="b1lch7"
typeof variable === "string"
```

---

# Example

```ts id="d4i4rb"
function print(value: string | number) {

  if (typeof value === "string") {
    console.log(value.toUpperCase());
  }

  if (typeof value === "number") {
    console.log(value.toFixed(2));
  }
}
```

---

# Internally

Inside:

```ts id="ehp7kw"
typeof value === "string"
```

TypeScript narrow karta hai:

```ts id="6r8s91"
value → string
```

---

# typeof Supports

| Type      | Value         |
| --------- | ------------- |
| string    | `"string"`    |
| number    | `"number"`    |
| boolean   | `"boolean"`   |
| undefined | `"undefined"` |
| function  | `"function"`  |
| object    | `"object"`    |

---

# 2. instanceof Narrowing

Classes ke sath use hota hai.

---

# Example

```ts id="l8fz7g"
class Dog {
  bark() {
    console.log("Bark");
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
  }

  if (animal instanceof Cat) {
    animal.meow();
  }
}
```

---

# Why?

`instanceof` check karta hai object kis class ka instance hai.

---

# 3. in Operator Narrowing

Object property check karne ke liye.

---

# Example

```ts id="p8c1lt"
type User = {
  name: string;
};

type Admin = {
  role: string;
};

function check(person: User | Admin) {

  if ("name" in person) {
    console.log(person.name);
  }

  if ("role" in person) {
    console.log(person.role);
  }
}
```

---

# Meaning

```ts id="x5d23z"
"name" in person
```

means:

> kya object ke andar name property hai?

---

# 4. Equality Narrowing

Comparison se narrowing.

---

# Example

```ts id="wwn0qv"
function check(a: string | number,
               b: string) {

  if (a === b) {
    // a becomes string
    console.log(a.toUpperCase());
  }
}
```

Why?

Because:

```ts id="10b28n"
b = string
```

to agar:

```ts id="2f48ya"
a === b
```

then `a` bhi string hi hoga.

---

# 5. Truthy/Falsy Narrowing

Null or undefined remove karne ke liye.

---

# Example

```ts id="5b3tqy"
function print(value?: string) {

  if (value) {
    console.log(value.toUpperCase());
  }
}
```

Inside if block:

```ts id="bs1a79"
value = string
```

because:

* undefined remove ho gaya
* empty values ignore ho gaye

---

# Type Guards in TypeScript

## What is Type Guard?

Type Guard ek technique hai jo TypeScript ko batati hai:

> Variable ka exact type kya hai.

Simple words:

> Type ko safely identify karna.

---

# Types of Type Guards

| Type Guard        | Purpose         |
| ----------------- | --------------- |
| typeof            | Primitive check |
| instanceof        | Class check     |
| in                | Property check  |
| Custom Type Guard | Custom logic    |

---

# Custom Type Guard

Most important interview topic.

---

# Syntax

```ts id="8mxn1h"
function isType(value): value is Type
```

---

# Example

```ts id="yyg81r"
type Dog = {
  bark: () => void;
};

type Cat = {
  meow: () => void;
};
```

---

# Custom Type Guard Function

```ts id="md0k8n"
function isDog(animal: Dog | Cat): animal is Dog {
  return "bark" in animal;
}
```

---

# Usage

```ts id="nq4u7f"
function speak(animal: Dog | Cat) {

  if (isDog(animal)) {
    animal.bark();
  } else {
    animal.meow();
  }
}
```

---

# Important Part

```ts id="lbh3h8"
animal is Dog
```

means:

> agar function true return kare,
> to animal ko Dog treat karo.

---

# How Type Guard Works

```ts id="bzhv54"
return "bark" in animal;
```

If true:

```ts id="3ydc3f"
animal = Dog
```

Else:

```ts id="4e18r7"
animal = Cat
```

---

# Real World Example

## API Response

```ts id="vjj8xq"
type Success = {
  success: true;
  data: string;
};

type ErrorResponse = {
  success: false;
  error: string;
};
```

---

# Type Guard

```ts id="f9o0q1"
function isSuccess(
  response: Success | ErrorResponse
): response is Success {

  return response.success;
}
```

---

# Usage

```ts id="1x1a0z"
function handleResponse(
  response: Success | ErrorResponse
) {

  if (isSuccess(response)) {
    console.log(response.data);
  } else {
    console.log(response.error);
  }
}
```

---

# Difference Between Narrowing and Type Guard

| Type Narrowing                  | Type Guard                 |
| ------------------------------- | -------------------------- |
| General process                 | Technique for narrowing    |
| Automatic bhi hota hai          | Mostly custom function     |
| TypeScript internally karta hai | Developer define karta hai |

---

# Interview Definition

## Type Narrowing

> Type Narrowing process hai jisme TypeScript conditions ke basis pe variable ka exact type identify karta hai.

---

## Type Guard

> Type Guard ek technique/function hai jo TypeScript ko variable ka exact type batata hai.

---

# Quick Revision

| Concept       | Use                   |
| ------------- | --------------------- |
| typeof        | Primitive types       |
| instanceof    | Classes               |
| in            | Object property       |
| truthy/falsy  | Remove undefined/null |
| Custom Guard  | Custom type checking  |
| value is Type | Type predicate        |


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

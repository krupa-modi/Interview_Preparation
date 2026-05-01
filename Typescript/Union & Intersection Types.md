

# 🔹 1. Union Types (`|`)

A **Union Type** allows a variable to hold **multiple possible types**.

👉 Syntax:

```ts
type MyType = string | number;
```

---

## ✅ Basic Example

```ts
let value: string | number;

value = "Hello"; // ✅
value = 100;     // ✅
value = true;    // ❌ Error
```

---

## ✅ Function Example

```ts
function printId(id: string | number) {
  console.log(id);
}

printId(101);
printId("ABC");
```

---

## ✅ Type Narrowing (IMPORTANT 🔥)

TypeScript needs to **figure out the exact type at runtime**.

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id.toFixed(2));
  }
}
```

---

## ✅ Union with Objects

```ts
type Dog = { bark: () => void };
type Cat = { meow: () => void };

function pet(animal: Dog | Cat) {
  // ❌ Cannot directly call both
}
```

👉 Need narrowing:

```ts
function pet(animal: Dog | Cat) {
  if ("bark" in animal) {
    animal.bark();
  } else {
    animal.meow();
  }
}
```

---

## 🔥 Key Points (Interview)

* Only **common properties** are accessible without narrowing
* Requires **type guards**
* Used when value can be **one of many types**

---

# 🔹 2. Intersection Types (`&`)

## ✅ Definition

An **Intersection Type** combines multiple types into **one**.

👉 Syntax:

```ts
type MyType = TypeA & TypeB;
```

---

## ✅ Basic Example

```ts
type Person = {
  name: string;
};

type Employee = {
  empId: number;
};

type Staff = Person & Employee;

const user: Staff = {
  name: "Krupa",
  empId: 101
};
```

---

## ✅ Function Example

```ts
function getStaff(staff: Person & Employee) {
  console.log(staff.name, staff.empId);
}
```

---

## ✅ Real World Example

```ts
type Admin = {
  role: string;
};

type User = {
  email: string;
};

type AdminUser = Admin & User;

const obj: AdminUser = {
  role: "admin",
  email: "test@gmail.com"
};
```

---

## 🔥 Key Points (Interview)

* Must satisfy **ALL types**
* Combines properties
* Often used for **mixing multiple interfaces**

---

# 🔥 3. Union vs Intersection (IMPORTANT 🔥)

| Feature            | Union (`|`)                     | Intersection (`&`)            |
|-------------------|--------------------------------|-------------------------------|
| Meaning           | OR                             | AND                           |
| Value must match  | Any one type                   | All types                     |
| Use case          | Flexible input                 | Combine objects               |
| Access properties | Only common properties         | All properties available      |

---

## ✅ Example Comparison

```ts
type A = { a: number };
type B = { b: string };

// Union
let obj1: A | B = { a: 10 }; // OR

// Intersection
let obj2: A & B = { a: 10, b: "hello" }; // AND
```

---


## Difference between Union & Intersection?

👉 Union = OR
👉 Intersection = AND

---
## Why Type Narrowing is needed?

👉 Because TypeScript cannot determine exact type in unions.

---

## What is Type Guard?

👉 A technique to narrow type using:

* `typeof`
* `in`
* `instanceof`

## What happens if Intersection conflicts?

```ts
type A = { id: string };
type B = { id: number };

type C = A & B; // ❌ id becomes never
```

👉 Result:

```ts
type C = {
  id: never;
}
```

---

## What is Discriminated Union? 🔥

```ts
type Shape =
  | { type: "circle"; radius: number }
  | { type: "square"; size: number };

function area(shape: Shape) {
  if (shape.type === "circle") {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.size * shape.size;
  }
}
```

👉 Used for **safe type narrowing**

## ✅ Union with Literal Types

```ts
type Status = "success" | "error" | "loading";
```

---

## ✅ Intersection with Functions

```ts
type A = { a: () => void };
type B = { b: () => void };

type C = A & B;
```

---



# 🔥 6. Summary

* `|` → Union → OR → Flexible
* `&` → Intersection → AND → Combined
* Union needs **type narrowing**
* Intersection merges properties
* Discriminated unions are **very important for interviews**

---


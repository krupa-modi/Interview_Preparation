Here’s a clean **Markdown (.md) file** you can directly use 👇

---

# 📘 TypeScript: Union, Intersection, Type, Interface & Type Alias

## 🔹 1. Union Type (`|`)

### 👉 Definition

Union allows a variable to hold **multiple possible types**.

### 👉 Syntax

```ts
let value: string | number;
```

### 👉 Example

```ts
let id: string | number;

id = 101;       // ✅ valid
id = "ABC123";  // ✅ valid
id = true;      // ❌ invalid
```

### 👉 Key Points

* Uses `|`
* Represents **OR relationship**
* Flexible but needs type checking

---

## 🔹 2. Intersection Type (`&`)

### 👉 Definition

Intersection combines multiple types into **one single type**.

### 👉 Syntax

```ts
type A = { name: string };
type B = { age: number };

type Person = A & B;
```

### 👉 Example

```ts
type Employee = { name: string };
type Manager = { department: string };

type Lead = Employee & Manager;

const lead: Lead = {
  name: "John",
  department: "IT"
};
```

### 👉 Key Points

* Uses `&`
* Represents **AND relationship**
* Must satisfy all types

---

## 🔹 3. Type Alias (`type`)

### 👉 Definition

A **custom name for any type** (primitive, object, union, etc.)

### 👉 Syntax

```ts
type User = {
  name: string;
  age: number;
};
```

### 👉 Example

```ts
type ID = string | number;

let userId: ID = 123;
```

### 👉 Key Points

* Can define:

  * Objects
  * Unions
  * Intersections
  * Functions
* More flexible than interface

---

## 🔹 4. Interface

### 👉 Definition

Interface defines the **structure of an object**

### 👉 Syntax

```ts
interface User {
  name: string;
  age: number;
}
```

### 👉 Example

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  salary: number;
}

const emp: Employee = {
  name: "John",
  salary: 50000
};
```

### 👉 Key Points

* Mainly used for **objects**
* Supports **extends (inheritance)**
* Can be merged (declaration merging)

---

## 🔹 5. Type vs Interface (Difference)

| Feature             | Type Alias (`type`) | Interface           |
| ------------------- | ------------------- | ------------------- |
| Usage               | Any type            | Object structure    |
| Union               | ✅ Yes               | ❌ No                |
| Intersection        | ✅ Yes               | ❌ No                |
| Extend              | Limited (`&`)       | ✅ `extends` keyword |
| Declaration Merging | ❌ No                | ✅ Yes               |
| Flexibility         | More flexible       | More strict         |

---

## 🔹 6. Union vs Intersection

| Feature        | Union (`|`)                | Intersection (`&`)         |
|----------------|---------------------------|----------------------------|
| Meaning        | One of many types         | All types combined         |
| Relationship   | OR                        | AND                        |
| Example        | `string | number`         | `{a: string} & {b: number}`|
| Usage          | Flexible input            | Strict combined object     |

---

## 🔹 7. Quick Real Example (Interview Level)

```ts
type Admin = {
  name: string;
  role: string;
};

type User = {
  email: string;
};

// Intersection
type SuperUser = Admin & User;

// Union
type Input = string | number;
```

---

## 🔹 8. When to Use What?

### 👉 Use **Union (`|`)**

* When value can be multiple types
  👉 Example: API response

### 👉 Use **Intersection (`&`)**

* When combining multiple objects
  👉 Example: user + permissions

### 👉 Use **Interface**

* For object structure (preferred in large apps)

### 👉 Use **Type**

* For complex types (union, intersection, functions)

---

## 🔥 Final Summary

* `|` → OR → Union
* `&` → AND → Intersection
* `type` → Flexible custom type
* `interface` → Object structure
* Interface = cleaner for objects
* Type = powerful for complex logic


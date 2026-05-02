
## 🔹 What is a Type Alias?

A **Type Alias** in TypeScript allows you to create a **custom name (alias)** for any type.

👉 It helps improve:

* Readability
* Reusability
* Maintainability of code

---

## 🔹 Syntax

```ts
type AliasName = Type;
```

---

## 🔹 Basic Example

```ts
type UserID = number;

let id: UserID = 101;
```

👉 Here:

* `UserID` is just another name for `number`

---

## 🔹 Type Alias with Object

```ts
type User = {
  name: string;
  age: number;
  isAdmin: boolean;
};

const user1: User = {
  name: "Krupa",
  age: 22,
  isAdmin: false
};
```

---

## 🔹 Type Alias with Union Types

```ts
type Status = "success" | "error" | "loading";

let currentStatus: Status = "success";
```

👉 Useful for:

* API states
* Enums-like behavior

---

## 🔹 Type Alias with Array

```ts
type Numbers = number[];

let arr: Numbers = [1, 2, 3, 4];
```

---


## 🔹 Type Alias with Intersection Types

```ts
type Employee = {
  id: number;
};

type Person = {
  name: string;
};

type Staff = Employee & Person;

const staff1: Staff = {
  id: 1,
  name: "Krupa"
};
```

👉 Combines multiple types into one

---

## 🔹 Difference: Type Alias vs Interface 🔥

| Feature         | Type Alias    | Interface        |
| --------------- | ------------- | ---------------- |
| Extend          | Using `&`     | Using `extends`  |
| Union Types     | ✅ Supported   | ❌ Not supported  |
| Primitive Types | ✅ Yes         | ❌ No             |
| Reopen          | ❌ No          | ✅ Yes            |
| Best Use        | Complex types | Object structure |

---

## 🔹 When to Use Type Alias?

Use **type** when:

* You need **union or intersection**
* You want to define **primitive or function types**
* You need **flexibility**

Use **interface** when:

* You define **object shapes**
* You want **extensibility**

---

## 🔹 Advantages

✅ Improves readability
✅ Reduces code duplication
✅ Helps in strict type checking
✅ Supports complex types (union, intersection, generics)

---

## 🔹 Limitations

❌ Cannot be reopened (unlike interface)
❌ Less flexible for large-scale extension

---

* `type` = alias (nickname for a type)
* Can represent:

  * Primitive
  * Object
  * Function
  * Union
  * Intersection
* Cannot be re-declared
* More powerful than interface in complex cases

---

## 🔚 Conclusion

Type Aliases are a **powerful feature of TypeScript** that allow you to:

* Create reusable type definitions
* Handle complex type combinations
* Write cleaner and more scalable code

---

If you want, I can also give:
✅ Interview questions on Type vs Interface
✅ Real-world coding problems
✅ Tricky edge cases asked in interviews


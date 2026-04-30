
# Type vs Interface in TypeScript (Interview Guide)

## 🔹 What is `type` in TypeScript?

A `type` is used to define a custom data type. It can represent primitives, objects, unions, tuples, functions, and more.

### ✅ Example:

```ts
type User = {
  name: string;
  age: number;
};
```

### 👉 Using type:

```ts
const user: User = {
  name: "Krupa",
  age: 22
};
```

---

## 🔹 What is `interface` in TypeScript?

An `interface` is used to define the structure of an object. It is mainly used for object shapes and supports extension (inheritance).

### ✅ Example:

```ts
interface User {
  name: string;
  age: number;
}
```

### 👉 Using interface:

```ts
const user: User = {
  name: "Krupa",
  age: 22
};
```

---

# 🔥 Difference Between `type` and `interface`

| Feature              | `type`                                            | `interface`                    |
| -------------------- | ------------------------------------------------- | ------------------------------ |
| Basic Usage          | Define any type (primitive, union, object, tuple) | Define object structure        |
| Extend / Inheritance | Uses `&` (intersection)                           | Uses `extends`                 |
| Declaration Merging  | ❌ Not supported                                   | ✅ Supported                    |
| Use for Primitives   | ✅ Yes                                             | ❌ No                           |
| Use for Union Types  | ✅ Yes                                             | ❌ No                           |
| Flexibility          | More flexible                                     | More structured                |
| Performance          | Slightly slower in large apps                     | Slightly better for large apps |

---

## 🔹 Example: Extension

### 👉 Using `interface`

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  salary: number;
}
```

---

### 👉 Using `type`

```ts
type Person = {
  name: string;
};

type Employee = Person & {
  salary: number;
};
```

---

## 🔹 Declaration Merging (Important Interview Point)

👉 Only `interface` supports merging

* Interface merging means:
👉 If you declare the same interface multiple times with the same name, TypeScript automatically combines (merge) them into one.

📌 This is a special feature of interface only
❌ type does NOT support this

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

// Final User:
const user: User = {
  name: "Krupa",
  age: 22
};

✔️ Final structure:

interface User {
  name: string;
  age: number;
}
```

🔹 Why is Interface Merging Useful?
Extend existing types without modifying original code
Helpful in large applications
Commonly used in libraries & frameworks

❌ This is NOT possible with `type`

---

## 🔹 Advanced Use Case (Only `type`)

### 👉 Union Types:

```ts
type Status = "success" | "error" | "loading";
```

### 👉 Function Type:

```ts
type Add = (a: number, b: number) => number;
```

### 👉 Tuple:

```ts
type Tuple = [string, number];
```

---

# 🎯 When to Use What?

## ✅ Use `interface` when:

* You are defining **object structure**
* You need **inheritance (extends)**
* You want **declaration merging**
* Working in **large-scale applications**

👉 Example:

```ts
interface APIResponse {
  data: string;
  status: number;
}
```

---

## ✅ Use `type` when:

* You need **union / intersection types**
* You are defining **primitives, tuples, functions**
* You want **more flexibility**

👉 Example:

```ts
type ID = string | number;
```

---

# 🔥 Interview Summary (Must Remember)

* `interface` = best for **objects & extensibility**
* `type` = best for **complex types (union, tuple, function)**
* `interface` supports **declaration merging**, `type` does not
* Both can define object shapes, but **interface is preferred in real projects**

---

# 💡 Final Tip

👉 In real-world projects:

* Use **interface by default**
* Use **type when interface can't handle the case**

---

If you want, I can also give you **tricky interview questions on this topic** or **real-world examples from React projects** 👍

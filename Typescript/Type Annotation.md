## 🔹 What is Type Annotation?

### 👉 Definition

**Type Annotation** means **explicitly specifying the type** of a variable, function, parameter, or return value in TypeScript.

👉 In simple words:
Instead of letting TypeScript guess (inference), **you tell TypeScript what the type should be**.

---

## 🔹 Basic Syntax

```ts
let variableName: type = value;
```

### 👉 Example

```ts
let name: string = "John";
let age: number = 25;
let isActive: boolean = true;
```

---

# 🔹 Why Type Annotation is Important?

* Ensures **type safety**
* Prevents bugs early
* Improves code readability
* Helps in large-scale applications
* Better IntelliSense (auto-suggestions)

---

# 🔹 Types of Type Annotation

---

## 🔹 1. Variable Type Annotation

```ts
let username: string = "Alice";
let score: number = 100;
```

---

## 🔹 2. Function Parameter Annotation

```ts
function greet(name: string) {
  return "Hello " + name;
}
```

👉 Here `name` must be a string.

---

## 🔹 3. Function Return Type Annotation

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

👉 `: number` ensures function returns a number.

---

## 🔹 4. Object Type Annotation

```ts
let user: { name: string; age: number } = {
  name: "John",
  age: 30
};
```

---

## 🔹 5. Array Type Annotation

```ts
let numbers: number[] = [1, 2, 3];

let names: Array<string> = ["A", "B"];
```

---

## 🔹 6. Union Type Annotation

```ts
let id: string | number;

id = 101;
id = "ABC";
```

---

## 🔹 7. Type Alias Annotation

```ts
type User = {
  name: string;
  age: number;
};

let user: User = {
  name: "John",
  age: 25
};
```

---

## 🔹 8. Interface Annotation

```ts
interface Person {
  name: string;
  age: number;
}

let p: Person = {
  name: "Alice",
  age: 28
};
```

---

# 🔹 Type Annotation vs Type Inference

| Feature     | Type Annotation      | Type Inference     |
| ----------- | -------------------- | ------------------ |
| Definition  | Explicit type        | Type guessed by TS |
| Example     | `let x: number = 10` | `let x = 10`       |
| Code Length | Longer               | Shorter            |
| Control     | Full control         | Less control       |
| Use Case    | Complex cases        | Simple cases       |

---

# 🔹 When to Use Type Annotation?

✅ Use when:

* Function parameters
* Function return values
* Complex objects
* Public APIs
* When type is unclear

---

# 🔹 When NOT to Use?

❌ Avoid when:

* Type is obvious

```ts
let count = 10; // no need: let count: number = 10
```

# 🔹 Real-World Example

```ts
type Product = {
  name: string;
  price: number;
};

function getProduct(p: Product): string {
  return `${p.name} costs ₹${p.price}`;
}
```

---

# 🔹 Advanced Concept: Optional & Default Values

```ts
function greet(name: string, age?: number): string {
  return `Hello ${name}`;
}
```

👉 `age` is optional.

---

# 🔹 Readonly Annotation

```ts
type User = {
  readonly id: number;
  name: string;
};
```

👉 `id` cannot be changed.

---

# 🔥 Final Summary

* Type Annotation = Explicitly defining types
* Helps in **safety + readability**
* Used in variables, functions, objects, arrays
* Prefer inference for simple cases
* Use annotation for complex & critical logic

---

## 💡 Pro Tip (Interview Level)

👉 Best practice:

* **Use inference + annotation together smartly**

```ts
const users: string[] = ["A", "B"];
```

✔ Clean
✔ Safe
✔ Readable

---



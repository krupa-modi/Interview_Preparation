

# 🔹 1. Function Return Type

## ✅ Definition

A **Function Return Type** defines **what type of value a function will return**.

👉 It ensures:

* Type safety
* Predictable output
* Better readability

---

## ✅ Syntax

```ts
function functionName(): returnType {
  // logic
  return value;
}
```

---

## ✅ Basic Example

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

👉 Return type is `number`

---

## ✅ Type Inference (IMPORTANT 🔥)

TypeScript can automatically infer return type:

```ts
function add(a: number, b: number) {
  return a + b; // inferred as number
}
```

👉 But in interviews → **explicit return type is preferred**

---

## ✅ Function Returning String

```ts
function greet(name: string): string {
  return "Hello " + name;
}
```

---

## ✅ Function Returning Object

```ts
function getUser(): { name: string; age: number } {
  return {
    name: "Krupa",
    age: 22
  };
}
```

---

## ✅ Function Returning Array

```ts
function getNumbers(): number[] {
  return [1, 2, 3];
}
```

---

## ✅ Void Return Type

👉 When function **does not return anything**

```ts
function logMessage(msg: string): void {
  console.log(msg);
}
```

---

## ✅ Never Return Type (IMPORTANT 🔥)

👉 Used when function **never returns**

* Throws error
* Infinite loop

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

---

## ✅ Union Return Type

```ts
function getValue(value: string | number): string | number {
  return value;
}
```

---

## 🔥 Key Points (Interview)

* Explicit return types improve **code clarity**
* `void` → no return
* `never` → function never completes
* Type inference works, but **avoid in interviews**

---

# 🔹 2. Optional Parameters

## ✅ Definition

Optional parameters are parameters that **may or may not be passed** when calling a function.

👉 Marked using `?`

---

## ✅ Syntax

```ts
function functionName(param1: type, param2?: type) {
  // logic
}
```

---

## ✅ Basic Example

```ts
function greet(name: string, age?: number) {
  if (age) {
    return `Hello ${name}, Age: ${age}`;
  }
  return `Hello ${name}`;
}

greet("Krupa");        // ✅
greet("Krupa", 22);    // ✅
```

---

## ⚠️ Important Rule (VERY IMPORTANT 🔥)

👉 Optional parameters must be **at the end**

❌ Wrong:

```ts
function test(a?: number, b: number) {} // Error
```

✅ Correct:

```ts
function test(a: number, b?: number) {}
```

---

## ✅ Default Parameters (Related Concept)

👉 Instead of optional, you can assign default value:

```ts
function greet(name: string, age: number = 18) {
  return `Hello ${name}, Age: ${age}`;
}

greet("Krupa"); // age = 18
```

---

## ✅ Optional Parameters with Function Types

```ts
type Func = (a: number, b?: number) => number;

const add: Func = (a, b = 0) => a + b;
```

---

## ✅ Optional Chaining with Parameters

```ts
function printLength(text?: string) {
  console.log(text?.length);
}
```

---

## 🔥 Key Points (Interview)

* `?` makes parameter optional
* Must always be **last parameter**
* Value can be `undefined`
* Useful for **flexible functions**

---

# 🔥 3. Difference: Optional vs Default Parameter

| Feature       | Optional Parameter (`?`) | Default Parameter |
| ------------- | ------------------------ | ----------------- |
| Required?     | No                       | No                |
| Default value | undefined                | Predefined value  |
| Syntax        | `param?: type`           | `param = value`   |

---

## ✅ Example Comparison

```ts
// Optional
function test1(a: number, b?: number) {
  return a + (b || 0);
}

// Default
function test2(a: number, b: number = 0) {
  return a + b;
}
```

---

## ❓ Difference between optional & default parameter?

👉 Optional → undefined
👉 Default → predefined value



## ❓  What is benefit of optional parameters?

👉 Flexible and reusable functions

---

# 🔥 5. Summary

* Function return type defines **output type**
* `void` → no return
* `never` → no completion
* Optional parameter → `?`
* Must be placed at **end**
* Default parameters are better when you want fallback values

---


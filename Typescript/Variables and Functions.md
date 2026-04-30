
# 📘 Variables & Functions in TypeScript

## 🔹 Variables in TypeScript

TypeScript allows you to define variables with **specific types**, which helps catch errors at compile time.

### ✅ Syntax

```ts
let variableName: type = value;
```

### 📌 Examples

```ts
let name: string = "Krupa";
let age: number = 22;
let isStudent: boolean = true;
```

### 🔸 Type Inference

TypeScript can automatically detect the type:

```ts
let city = "Pune"; // inferred as string
```

### 🔸 Special Types

```ts
let anything: any = "Hello"; // can hold any type
anything = 10;

let unknownValue: unknown = "Test"; // safer than any

let notSure: null = null;
let nothing: undefined = undefined;
```

---

## 🔹 Variable Declarations

### 1️⃣ `var` (Avoid using)

```ts
var x = 10;
```

* Function-scoped
* Can be redeclared
* ❌ Not recommended

---

### 2️⃣ `let`

```ts
let x = 20;
```

* Block-scoped
* Can be reassigned
* ✅ Preferred

---

### 3️⃣ `const`

```ts
const pi = 3.14;
```

* Block-scoped
* Cannot be reassigned
* ✅ Use for fixed values

---

## 🔹 Functions in TypeScript

Functions can have **typed parameters** and **return types**.

---

### ✅ Basic Function

```ts
function greet(name: string): string {
  return "Hello " + name;
}
```

---

### 🔸 Arrow Function

```ts
const add = (a: number, b: number): number => {
  return a + b;
};
```

---

### 🔸 Optional Parameters

```ts
function greetUser(name: string, age?: number): string {
  return age ? `Hello ${name}, age ${age}` : `Hello ${name}`;
}
```

---

### 🔸 Default Parameters

```ts
function multiply(a: number, b: number = 2): number {
  return a * b;
}
```

---

### 🔸 Function with No Return (`void`)

```ts
function logMessage(message: string): void {
  console.log(message);
}
```

---

### 🔸 Function with `never`

```ts
function throwError(msg: string): never {
  throw new Error(msg);
}
```

* `never` means function **never returns**
* Used for errors or infinite loops

---

### 🔸 Function Type

```ts
let myFunc: (a: number, b: number) => number;

myFunc = (x, y) => x + y;
```

---

## 🔹 Summary

* Use `let` and `const` instead of `var`
* Always define types for clarity
* TypeScript helps prevent runtime errors
* Functions support:

  * Typed parameters
  * Optional/default values
  * Special return types (`void`, `never`)

---

## 🚀 Pro Tip

Prefer **strict typing** instead of `any` for better code quality and easier debugging.



Just tell me 👍

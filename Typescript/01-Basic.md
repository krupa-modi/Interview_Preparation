# TypeScript Basics

---

## **1) What is TypeScript?**

TypeScript is an open-source programming language developed by Microsoft. It is a **superset of JavaScript** that adds **static typing** and advanced features.

* Any valid JavaScript code is also valid TypeScript
* TypeScript is compiled (transpiled) into JavaScript

### ✅ One-line Answer:

> TypeScript is a superset of JavaScript that adds static typing and better tooling.

---

## **2) Why do we use TypeScript?**

TypeScript is used to write **safer, scalable, and maintainable code** by catching errors early.

### ✅ Key Points:

* Early error detection (compile-time)
* Static typing → fewer bugs
* Better readability & maintainability
* Excellent IDE support
* Suitable for large-scale applications

### ✅ One-line Answer:

> TypeScript helps catch errors early and improves code quality and scalability.

---

## **3) What is Static Typing?**

Static typing means defining variable types at **compile time**, so errors are caught before execution.

### ✅ Example:

```ts
let age: number = 25;
age = "hello"; // ❌ Error
```

### ✅ One-line Answer:

> Static typing ensures variables are checked at compile time, reducing runtime errors.

---

## **4) What are the Advantages & Disadvantages of TypeScript?**

### ✅ Advantages:

* Static typing → early error detection
* Better maintainability
* Strong IDE support
* Scalable for large apps

### ❌ Disadvantages:

* Requires compilation (TS → JS)
* Learning curve
* More setup
* Can be verbose

### ✅ One-line Answer:

> TypeScript improves code quality and scalability but adds compilation and setup overhead.

---

## **5) TypeScript vs JavaScript**

| Feature   | JavaScript | TypeScript     |
| --------- | ---------- | -------------- |
| Typing    | Dynamic    | Static         |
| Errors    | Runtime    | Compile-time   |
| Execution | Direct     | Compiled to JS |

### ✅ One-line Answer:

> TypeScript is a statically typed superset of JavaScript that provides better error handling and scalability.


## 6. What is Type Inference?

TypeScript automatically detects the type of a variable based on its value.

### Example:

```ts
let name = "Krupa"; // inferred as string
```

👉 No need to explicitly define types every time

**One-line:**

> Type inference is when TypeScript automatically determines the variable type.

---

## 7. What is Transpilation?

Transpilation is the process of converting TypeScript code into JavaScript.

👉 Browsers understand JavaScript, not TypeScript

**One-line:**

> Transpilation converts TypeScript into JavaScript so it can run in browsers.

---

## 8. What is `tsc`?

`tsc` stands for **TypeScript Compiler**

* Converts `.ts` files → `.js` files
* Checks for type errors

### Example:

```bash
tsc app.ts
```

**One-line:**

> tsc is the TypeScript compiler used to compile TS code into JavaScript.

---

## 9. What is `tsconfig.json`?

A configuration file for TypeScript projects.

* Defines compiler options
* Controls how TypeScript compiles code

### Example:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "strict": true
  }
}
```

**One-line:**

> tsconfig.json is used to configure how TypeScript compiles your project.

---

## 10. What is Strict Mode?

Strict mode enables all strict type-checking options in TypeScript.

* Helps catch more errors
* Makes code safer

### Example:

```json
"strict": true
```

**One-line:**

> Strict mode enforces stricter type checking to reduce bugs.

---

## 11. What are Type Annotations?

Type annotations are explicit type definitions for variables, functions, etc.

### Example:

```ts
let age: number = 25;
```

**One-line:**

> Type annotations explicitly define the type of a variable or function.



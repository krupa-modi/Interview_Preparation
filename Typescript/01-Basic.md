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

Here’s your **proper interview-ready MD file with clear explanations + examples** 👇

---

# TypeScript Interview Notes (Advanced Basics)

---

## 12. What does `noImplicitAny` do?

`noImplicitAny` prevents variables from having an implicit `any` type.

👉 If TypeScript cannot infer a type, it throws an error instead of assigning `any`.

### Example:

```ts
function greet(name) {
  return "Hello " + name;
}
```

❌ Error (when `noImplicitAny: true`)
Because `name` has implicit `any`

✔ Fix:

```ts
function greet(name: string) {
  return "Hello " + name;
}
```

**Why important in interview:**

* Avoids unsafe code
* Forces proper typing

**One-line:**

> noImplicitAny ensures TypeScript does not allow variables with implicit `any` type.

---

## 13. Does TypeScript affect performance?

👉 **Short Answer:** No (in runtime)

### Explanation:

* TypeScript runs only during development (compile time)
* It converts into JavaScript
* Final output is plain JS → same performance as JS

### Example:

```ts
let num: number = 10;
```

Compiled JS:

```js
var num = 10;
```

👉 No type exists in runtime

**One-line:**

> TypeScript does not affect runtime performance because it compiles to plain JavaScript.

---

## 14. Compile-time vs Runtime Validation

### Compile-time (TypeScript)

* Errors detected before execution
* Safer code

```ts
let age: number = "hello"; // ❌ Error
```

---

### Runtime (JavaScript)

* Errors occur while running code

```js
let age = "hello";
console.log(age.toFixed()); // ❌ Runtime error
```

---

### Key Difference:

| Feature           | Compile-time     | Runtime          |
| ----------------- | ---------------- | ---------------- |
| When error occurs | Before execution | During execution |
| Language          | TypeScript       | JavaScript       |
| Safety            | High             | Lower            |

**One-line:**

> Compile-time validation catches errors before execution, while runtime validation catches errors during execution.

---

## 15. How does TypeScript compilation work?

### Steps:

1. Write `.ts` file
2. TypeScript compiler (`tsc`) checks types
3. Converts TS → JS
4. Browser/Node runs JS

### Flow:

```
TypeScript Code → tsc → JavaScript Code → Execution
```

### Example:

```ts
let msg: string = "Hello";
```

Compiled JS:

```js
var msg = "Hello";
```

**Key Point:**

* Types are removed during compilation

**One-line:**

> TypeScript compilation checks types and converts TS code into executable JavaScript.

---

## 16. What is the output of TypeScript code?

👉 Output is always **JavaScript**

### Example:

TypeScript:

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

JavaScript Output:

```js
function add(a, b) {
  return a + b;
}
```

👉 Notice:

* Types are removed
* Only logic remains

---

## 🔥 Final Interview Summary

* `noImplicitAny` → prevents unsafe `any` types
* TypeScript performance → no runtime impact
* Compile vs Runtime → before vs during execution
* Compilation → TS → JS using `tsc`
* Output → always plain JavaScript



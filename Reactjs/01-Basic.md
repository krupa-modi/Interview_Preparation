
# ⚛️ React Interview Notes

## 1. What is React?

React is a **JavaScript library** used to build **user interfaces (UI)**, especially for **single-page applications (SPA)**.

- Developed by Facebook
- Component-based architecture
- Reusable UI pieces

👉 In short: React helps you build fast, interactive web apps using components.

---

## 2. Why React over JavaScript?

React is preferred over plain JavaScript because:

- **Component-Based** → Reusable code, better structure
- **Virtual DOM** → Faster updates
- **Declarative UI** → Easy to understand and debug
- **State Management** → Dynamic UI updates easily
- **Large Ecosystem** → Strong community support

👉 JS can do everything, but React makes it **faster, cleaner, and scalable**.

---

## 3. What is SPA (Single Page Application)?

SPA is a web app that loads **only one HTML page** and updates content dynamically **without reloading the page**.

### Features:
- Fast navigation
- No full page reload
- Better user experience

### Example:
- Gmail
- Instagram
- React apps

👉 React is mainly used to build SPAs.

---

## 4. What is Virtual DOM? 🔥

Virtual DOM is a **lightweight copy of the real DOM**.

### How it works:
1. React creates a Virtual DOM
2. When state changes → new Virtual DOM is created
3. React compares old vs new (Diffing)
4. Updates only changed parts in real DOM

👉 This makes React **very fast**.

### Example:
If only one list item changes → React updates only that item, not the whole page.

---

## 5. How React works internally?

### Step-by-step flow:

1. **Component Render**
   - React converts JSX → Virtual DOM

2. **State/Props Change**
   - Triggers re-render

3. **Diffing Algorithm**
   - Compares old vs new Virtual DOM

4. **Reconciliation**
   - Finds minimal changes

5. **DOM Update**
   - Updates only required parts in real DOM

👉 Key concept: React follows **"Update only what changed"**



6. What is Type Inference?

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






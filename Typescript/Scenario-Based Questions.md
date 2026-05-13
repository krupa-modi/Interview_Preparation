# TypeScript Scenario-Based Interview Questions

## 1. `any` vs `unknown`

### 👉 Kab use karoge?

| `any`                              | `unknown`                                     |
| ---------------------------------- | --------------------------------------------- |
| Type checking disable kar deta hai | Safe type checking deta hai                   |
| Kuch bhi assign/use kar sakte ho   | Use karne se pehle type check karna padta hai |
| Unsafe                             | Safe                                          |

### Interview Answer

* `any` tab use karte hain jab quick migration ho ya temporary code likhna ho.
* `unknown` tab use karte hain jab API/data ka type pata nahi ho but safety maintain karni ho.

### Example

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

✅ Large projects me `unknown` prefer karte hain because it prevents runtime errors.

---

# 2. Strict Mode Benefits

### 👉 Errors kaise reduce hote hain?

### Interview Answer

`strict mode` TypeScript ka safety feature hai jo compile time pe errors catch karta hai.

### Benefits

* Null/undefined errors reduce hote hain
* Wrong type assignments detect hote hain
* Better IntelliSense milta hai
* Runtime bugs kam hote hain

### Example

```ts
let name: string;

// Error because value assign nahi hui
console.log(name);
```

### Important Strict Options

```json
"strict": true
```

Includes:

* `noImplicitAny`
* `strictNullChecks`
* `strictFunctionTypes`

✅ Large production apps me strict mode highly recommended hai.

---

# 3. Large Project Structure

### 👉 Types kaha rakhte ho?

### Interview Answer

Large projects me reusable types ko separate folders/files me rakhte hain for maintainability.

### Common Structure

```bash
src/
 ├── types/
 │    ├── user.types.ts
 │    ├── api.types.ts
 │    └── common.types.ts
```

### Scenario

* API response types → `api.types.ts`
* User/Auth related → `user.types.ts`
* Shared interfaces → `common.types.ts`

✅ Isse code reusable aur scalable banta hai.

---

# 4. Third-party Library Typing

### 👉 Agar types available nahi ho to kya karoge?

### Interview Answer

### Option 1: Install types

```bash
npm install --save-dev @types/library-name
```

### Option 2: Custom declaration file

```ts
// custom.d.ts
declare module "my-library";
```

### Option 3: Manual typing

```ts
declare module "my-library" {
  export function test(value: string): void;
}
```

✅ Production me proper typings likhna better practice hai instead of using `any`.

---

# 5. Error Handling in TypeScript

### 👉 Type-safe error handling kaise karte ho?

### Interview Answer

Type-safe error handling ke liye `unknown` use karte hain inside `catch`.

### Example

```ts
try {
  throw new Error("Something went wrong");
} catch (error: unknown) {
  if (error instanceof Error) {
    console.log(error.message);
  }
}
```

### Why?

* `catch` me exact error type pata nahi hota
* `unknown` safety provide karta hai
* Runtime crashes reduce hote hain

✅ Interview me bolo:

> “I avoid using `any` in catch blocks and prefer `unknown` with proper type guards.”

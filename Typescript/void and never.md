## 🔹 1. What is `void` in TypeScript?

### ✅ Definition:

`void` represents the **absence of a value**.
It is commonly used as a return type for functions that **do not return anything**.

---

### 🧠 Key Points:

* Function executes but **does not return a value**
* Implicitly returns `undefined`
* Mostly used in functions like logging, printing, etc.

---

### ✅ Example:

```ts
function logMessage(message: string): void {
  console.log(message);
}
```

👉 This function prints the message but **returns nothing**.

---

### ⚠️ Important:

Even though `void` means no return, technically it returns `undefined`.

```ts
function test(): void {
  return; // OK
}
```

---

## 🔹 2. What is `never` in TypeScript?

### ✅ Definition:

`never` represents a value that **never occurs**.
It is used for functions that **never complete execution**.

---

### 🧠 Key Points:

* Function **never returns**
* Used in:

  * Infinite loops
  * Functions that throw errors
* Indicates **unreachable code**

---

### ✅ Example 1: Function that throws error

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

👉 This function **never returns** because it always throws an error.

---

### ✅ Example 2: Infinite loop

```ts
function infiniteLoop(): never {
  while (true) {}
}
```

👉 This function **never ends**, so it never returns.

---

## 🔥 3. Key Differences: `void` vs `never`

| Feature           | `void`                | `never`                  |
| ----------------- | --------------------- | ------------------------ |
| Meaning           | No return value       | Never returns            |
| Execution         | Function completes    | Function never completes |
| Return            | `undefined`           | No value at all          |
| Use case          | Logging, side effects | Errors, infinite loops   |
| Code reachability | Reachable             | Unreachable              |

---

## 🎯 4. Real Interview Trick Question

### ❓ What happens here?

```ts
function demo(): void {
  return undefined;
}
```

✅ Valid — because `void` allows `undefined`

---

```ts
function demo2(): never {
  return; // ❌ Error
}
```

❌ Invalid — because `never` means **no return at all**

---


## 🚀 6. Quick Summary

* `void` → Function runs but returns nothing
* `never` → Function never finishes execution

---

## 💡 Easy Way to Remember

* `void` = "No return value"
* `never` = "No return ever"

---

## ✅ Interview Tip

If interviewer asks:

👉 **“Difference between void and never?”**

Say:

> "`void` is used when a function does not return a value, while `never` is used when a function never returns at all, such as in cases of errors or infinite loops."


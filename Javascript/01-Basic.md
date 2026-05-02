## 1. What is JavaScript?

JavaScript is a **high-level, interpreted programming language** used to make web pages interactive. It runs in the browser and on servers (via Node.js)..

---

## 2. Difference between `let`, `const`, and `var`

| Feature    | var             | let       | const     |
| ---------- | --------------- | --------- | --------- |
| Scope      | Function        | Block     | Block     |
| Re-declare | ✅ Yes           | ❌ No      | ❌ No      |
| Re-assign  | ✅ Yes           | ✅ Yes     | ❌ No      |
| Hoisting   | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |

**Best Practice:**

* Use `const` by default
* Use `let` if value changes
* Avoid `var`

---

## 3. Difference between `==` and `===`

* `==` → **Loose equality** (does type conversion)
* `===` → **Strict equality** (no type conversion)

```js
5 == "5"   // true
5 === "5"  // false
```

**Best Practice:** Always use `===`

---

## 4. How to check type of a variable?

Use `typeof` operator:

```js
typeof "hello"   // "string"
typeof 10        // "number"
typeof true      // "boolean"
typeof {}        // "object"
typeof []        // "object"
```

👉 Note: Arrays return `"object"`

---

# `this` Keyword in JavaScript (Interview Notes)

## What is `this`?

`this` refers to the **object that is currently executing the function**.
Its value depends on **how the function is called**, not where it is written.

this refers to the current context and changes based on how a function is called.
In object
const obj = {
  name: "Amit",
  show() {
    console.log(this.name);
  }
};

obj.show(); // "Amit"

In global scope (browser)
console.log(this === window); // true



---

## 1. Global Context

```js
console.log(this);
```

* In browser → `window`
* In strict mode → `undefined`

---

## 2. Inside a Regular Function

```js
function show() {
  console.log(this);
}
show();
```

* Non-strict mode → `window`
* Strict mode → `undefined`

👉 **Why undefined?**
In strict mode, JavaScript avoids default binding to global object to prevent mistakes.

---

## 3. Inside an Object Method

```js
const user = {
  name: "Krupa",
  greet() {
    console.log(this.name);
  }
};
user.greet(); // Krupa
```

👉 Here, `this` refers to the **object (`user`) calling the method**

---

## 4. Inside Arrow Function ❗ (Important Interview Point)

```js
const user = {
  name: "Krupa",
  greet: () => {
    console.log(this.name);
  }
};
user.greet(); // undefined
```

👉 **Why `undefined` in arrow function?**

* Arrow functions **do NOT have their own `this`**
* They take `this` from **parent (lexical scope)**

In this case:

* Parent = global scope
* Global `this` → `window`
* `window.name` → usually `undefined`

---

## 5. Arrow Function inside Method (Correct Use)

```js
const user = {
  name: "Krupa",
  greet() {
    const inner = () => {
      console.log(this.name);
    };
    inner();
  }
};
user.greet(); // Krupa
```

👉 Arrow function inherits `this` from `greet()` method

---

## Key Differences (Regular vs Arrow)

| Feature        | Regular Function | Arrow Function    |
| -------------- | ---------------- | ----------------- |
| Own `this`     | ✅ Yes            | ❌ No              |
| `this` value   | Depends on call  | From parent scope |
| Use in objects | Good for methods | Not for methods   |

---

## Interview One-Line Answer

👉 "`this` refers to the object that calls the function, and its value is determined at runtime. In arrow functions, `this` is inherited from the surrounding scope."



# ⚙️ Interpreter vs Compiler (Interview Ready)


* **Interpreter** → Executes code **line by line**
* **Compiler** → Converts entire code into **machine code at once**

---

## 🔄 Working Flow

### 🟢 Interpreter Flow

```text
Source Code → Interpreter → Execute line by line → Output
```

### 🔵 Compiler Flow

```text
Source Code → Compiler → Machine Code → Execute → Output
```

---

## 📊 Comparison Table

| Feature           | Interpreter 🟢       | Compiler 🔵                    |
| ----------------- | -------------------- | ------------------------------ |
| Execution         | Line by line         | Whole program at once          |
| Speed             | Slower               | Faster                         |
| Error Handling    | Stops at first error | Shows all errors after compile |
| Output            | No separate file     | Generates executable file      |
| Example Languages | JavaScript, Python   | C, C++                         |

---

## 💻 Example

### 🟢 Interpreter (JavaScript)

```javascript
console.log("Hello");
console.log(a); // Error here
console.log("World");
```

👉 Output:

```
Hello
Error → stops here ❌
```

---

### 🔵 Compiler (C)

```c
#include <stdio.h>
int main() {
    printf("Hello");
    printf("%d", a); // Error
    printf("World");
}
```

👉 Output:

* Compilation fails ❌
* Shows all errors before running

---

## ⚡ Real-World Understanding

* Interpreter = Like reading instructions and cooking **step by step**
* Compiler = Like preparing full recipe first, then cooking

---

## 🧠 Key Points (Interview Quick Notes)

* Interpreter executes **immediately**
* Compiler needs **compile step**
* Interpreter is **flexible but slower**
* Compiler is **fast but less flexible**
* JavaScript uses **Interpreter + JIT Compiler (Modern Engines)**

---

## 🧾 One-Line Difference

👉 *Interpreter runs code line-by-line, while Compiler translates entire code before execution.*







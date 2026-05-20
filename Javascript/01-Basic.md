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


# 📌 Why JavaScript is Single-Threaded?

JavaScript is called **single-threaded** because it has:

* **One Call Stack**
* Executes **one task at a time**

This means JavaScript can perform only **one operation in a single thread** at a given moment.

---

# 🔹 Why was JavaScript designed as Single-Threaded?

JavaScript was originally created for browsers to handle:

* User interactions
* DOM manipulation
* Events

If multiple threads changed the DOM at the same time, it could create:

* Race conditions
* Data inconsistency
* Unexpected UI behavior

So JavaScript uses a single thread to keep execution simple and predictable.

---

# 📌 Example

```js id="yc3x7l"
console.log("Start");

console.log("Middle");

console.log("End");
```

## ✅ Output

```js id="g2tydx"
Start
Middle
End
```

JavaScript executes code **line by line** using a single call stack.

---

# 📌 How Browser Executes JavaScript?

Browser does not run only JavaScript.

Browser has:

* JS Engine
* Web APIs
* Callback Queue
* Event Loop

Together they execute asynchronous JavaScript.

---

# 🔥 Execution Flow

## 1️⃣ Call Stack

JavaScript code first goes into the **Call Stack**.

Example:

```js id="ehy6p6"
console.log("Hello");
```

The function is pushed into stack and executed.

---

## 2️⃣ Web APIs

Browser provides Web APIs like:

* `setTimeout`
* `fetch`
* `DOM events`

Example:

```js id="1hz0pf"
setTimeout(() => {
  console.log("Timer Done");
}, 2000);
```

`setTimeout` is handled by browser Web APIs, not directly by JS engine.

---

## 3️⃣ Callback Queue

After timer completes, callback moves to:

```txt id="mxjv1v"
Callback Queue
```

---

## 4️⃣ Event Loop

Event Loop checks:

* Is Call Stack empty?

If yes:

👉 Callback from queue moves to Call Stack.

Then it executes.

---

# 📌 Complete Example

```js id="j8n8j2"
console.log("Start");

setTimeout(() => {
  console.log("Inside Timeout");
}, 0);

console.log("End");
```

## ✅ Output

```js id="9zc6qb"
Start
End
Inside Timeout
```

---

# 🔥 Why?

Even though timeout is `0ms`:

* `setTimeout` goes to Web APIs
* Callback waits in queue
* Event Loop pushes it later

So synchronous code executes first.

---

# 📌 Important Components

| Component      | Work                        |
| -------------- | --------------------------- |
| Call Stack     | Executes JS functions       |
| Web APIs       | Browser handles async tasks |
| Callback Queue | Stores completed callbacks  |
| Event Loop     | Moves callbacks to stack    |

---

# 📌 Interview One-Line Answer

> JavaScript is single-threaded because it uses a single call stack and executes one task at a time. The browser handles asynchronous operations using Web APIs, Callback Queue, and the Event Loop.


````md id="j5k2xp"
# ✅ JavaScript Engine (V8)

## 🎯 Definition
JavaScript Engine code ko execute karta hai.

Chrome aur Node.js me mostly **V8 Engine** use hota hai.

---

# 🔥 V8 Engine Kya Karta Hai?

- JavaScript code ko machine code me convert karta hai
- Fast execution provide karta hai
- Google ne develop kiya hai

---

# ✅ Interview Answer

> V8 JavaScript engine hai jo Chrome aur Node.js me use hota hai.  
> Ye JavaScript code ko machine code me convert karta hai for fast execution.

---

# ✅ Dynamic Typing

## 🎯 Definition
JavaScript dynamically typed language hai.

Matlab:
```js
variable ka type runtime par decide hota hai
````

---

# ✅ Example

```js id="k7p2wm"
let data = 10;

data = "Hello";
```

Same variable me:

* pehle number
* baad me string

store ho gaya ✅

---

# ✅ Interview Answer

> JavaScript dynamically typed language hai because variable type runtime par automatically change ho sakta hai.

---

# ✅ Type Coercion

## 🎯 Definition

JavaScript automatically ek type ko dusre type me convert karta hai.

---

# ✅ Example

```js id="m4x9qa"
console.log("5" + 2);
```

## ✅ Output

```js id="n2v8lk"
52
```

Number `2` string me convert ho gaya.

---

# ✅ Another Example

```js id="y7r3pd"
console.log("5" - 2);
```

## ✅ Output

```js id="q1t6mv"
3
```

String `"5"` number me convert ho gaya.

---

# ✅ Interview Answer

> Type coercion me JavaScript automatically data types convert karta hai during operations.

---

# ✅ NaN

## 🎯 Definition

NaN means:

```js
Not a Number
```

Jab invalid mathematical operation hota hai tab NaN aata hai.

---

# ✅ Example

```js id="w8k2zt"
console.log("hello" * 2);
```

## ✅ Output

```js id="e5m7qx"
NaN
```

---

# ⚡ Important Point

```js id="v4n1pk"
typeof NaN
```

## ✅ Output

```js id="b7r9tw"
number
```

Interview me bahot puchte hain ✅

---

# ✅ Interview Answer

> NaN ka meaning "Not a Number" hai.
> Ye invalid numeric operations me aata hai.

---

# ✅ Comments in JavaScript

Comments ignored hote hain by JavaScript engine.

Used for:

* explanation
* notes
* debugging

---

# ✅ Single Line Comment

```js id="x3q8lm"
// This is comment
```

---

# ✅ Multi Line Comment

```js id="f6p2wr"
/*
Multi line
comment
*/
```

---

# ✅ Interview Answer

> Comments readable code likhne aur explanation dene ke liye use hote hain.
> JavaScript engine comments ko execute nahi karta.

---

# 🚀 Quick Revision Table

| Topic          | Meaning                     |
| -------------- | --------------------------- |
| V8 Engine      | JS code execute karta       |
| Dynamic Typing | Type runtime pe change hota |
| Type Coercion  | Automatic type conversion   |
| NaN            | Invalid number result       |
| Comments       | Non-executable notes        |

````md

# JavaScript Notes

## continue
- `continue` → skip current loop(iteration)

```js
for(let i = 1; i <= 5; i++) {
  if(i === 3) continue;

  console.log(i);
}
````

Output:
1 2 4 5

---

## return

* `return` function se value wapas bhejne ke liye use hota hai.
* Function execution bhi stop ho jata hai.
* `return` ke baad ka code execute nahi hota.

### Example

```js
function add(a, b) {
  return a + b;

  console.log("Hello"); // execute nahi hoga
}

console.log(add(2, 3));
```

---

# while Loop

* Condition true tak loop chalta hai.

## Syntax

```js
while(condition) {

}
```

## Example

```js
let i = 1;

while(i <= 5) {
  console.log(i);
  i++;
}
```

Output:
1 2 3 4 5

---

# do while Loop

* Pehle code execute hota hai
* Phir condition check hoti hai
* `do while` minimum 1 baar execute hota hai

## Syntax

```js
do {

} while(condition);
```

## Example

```js
let i = 1;

do {
  console.log(i);
  i++;
} while(i <= 5);
```

Output:
1 2 3 4 5

---

# forEach()

* Array method hai
* Har element par callback function run karta hai

## Example

```js
const arr = [1, 2, 3];

arr.forEach((item) => {
  console.log(item);
});
```

Output:
1 2 3

---

# Important Point

* `forEach()` sirf arrays par use hota hai

| Loop                         | forEach             |
| ---------------------------- | ------------------- |
| Arrays & objects dono        | Sirf arrays         |
| break/continue use kar sakte | break/continue nahi |
| Faster                       | Slightly slower     |
| More control                 | Easy syntax         |


# ✅ Generators in JavaScript

# 🎯 Definition

Generators are special functions that can pause and resume execution.

They use:
```js
function*
````

and

```js
yield
```

---

# ✅ Example

```js
function* numbers() {

  yield 1;
  yield 2;
  yield 3;
}

const gen = numbers();

console.log(gen.next());
console.log(gen.next());
```

## ✅ Output

```js id="p4m8tw"
{ value: 1, done: false }

{ value: 2, done: false }
```

---

# 🎯 Interview Answer

> Generators are special functions that can pause execution using `yield` and continue later using `next()`.

---

# ✅ Shadow DOM

# 🎯 Definition

Shadow DOM creates a separate hidden DOM tree for an element.

It provides:

* encapsulation
* isolated styles/components

---

# ✅ Example

```js id="v7q1la"
const element = document.querySelector("#box");

const shadow = element.attachShadow({ mode: "open" });
```

---

# 🎯 Interview Answer

> Shadow DOM is used to create isolated DOM and CSS for reusable components.

---

# ✅ Benefits

✅ Style isolation
✅ Encapsulation
✅ Reusable components

---

# ✅ Service Workers

# 🎯 Definition

Service Workers are scripts that run in the background of the browser.

Used for:

* caching
* offline support
* push notifications

---

# ✅ Example

```js id="k5r2vt"
navigator.serviceWorker.register("sw.js");
```

---

# 🎯 Interview Answer

> Service Workers run in the background and are mainly used for caching, offline functionality, and push notifications.

---

# ✅ Real Uses

✅ Progressive Web Apps (PWA)
✅ Offline websites
✅ Background sync

---

# 🚀 Quick Revision Table

| Concept         | Purpose                    |
| --------------- | -------------------------- |
| Generators      | Pause/resume functions     |
| Shadow DOM      | Isolated DOM & styles      |
| Service Workers | Background tasks & caching |

---

# 💡 One-Line Memory Trick

```js id="x2m9pw"
Generator → pause function

Shadow DOM → isolated component

Service Worker → background browser worker
```














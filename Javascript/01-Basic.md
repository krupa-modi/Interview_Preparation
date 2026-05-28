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


# find() vs filter()

---

# find()

## Definition
`find()` first matching element return karta hai.

Agar match nahi mila:
```js id="o1p2q3"
undefined
````

---

# Example

```js id="f1g2h3"
const arr = [1,2,3,4,5]

const result = arr.find(num => num > 3)

console.log(result)
```

## Output

```js id="i4j5k6"
4
```

---

# filter()

## Definition

`filter()` saare matching elements return karta hai in array form.

Agar match nahi mila:

```js id="l7m8n9"
[]
```

---

# Example

```js id="a1b2c3"
const arr = [1,2,3,4,5]

const result = arr.filter(num => num > 3)

console.log(result)
```

## Output

```js id="d4e5f6"
[4,5]
```

---

# Main Difference

| find()                          | filter()                      |
| ------------------------------- | ----------------------------- |
| First match return karta hai    | All matches return karta hai  |
| Single value return             | Array return                  |
| Match milte hi stop ho jata hai | Pure array traverse karta hai |

---

# Kaun Fast Hai?

## Answer

`find()` generally faster hota hai because:

* First match milte hi loop stop ho jata hai

`filter()` slower ho sakta hai because:

* Pure array check karta hai

---

# Example

```js id="g7h8i9"
const arr = [1,2,3,4,5]

arr.find(num => num === 2)
```

Yaha:

* `find()` 2 milte hi stop ho jayega

But:

```js id="j1k2l3"
arr.filter(num => num === 2)
```

Ye pura array traverse karega.

---

# Time Complexity

| Method   | Complexity |
| -------- | ---------- |
| find()   | O(n)       |
| filter() | O(n)       |

But practical performance me:

* `find()` usually faster hota hai

---

# Interview Answer

“find() first matching element return karta hai while filter() all matching elements array me return karta hai.

find() generally faster hota hai because it stops after first match, while filter() entire array traverse karta hai.”

---

# map() vs forEach()

---

# map()

## Definition

`map()` new array return karta hai.

Mostly use hota hai:

* Data transformation
* UI rendering

---

# Example

```js id="m4n5o6"
const arr = [1,2,3]

const result = arr.map(num => num * 2)

console.log(result)
```

## Output

```js id="p7q8r9"
[2,4,6]
```

---

# forEach()

## Definition

`forEach()` sirf iterate karta hai.

Ye:

* New array return nahi karta

Mostly use hota hai:

* Logging
* Side effects

---

# Example

```js id="s1t2u3"
const arr = [1,2,3]

arr.forEach(num => {
  console.log(num)
})
```

---

# Main Difference

| map()                       | forEach()              |
| --------------------------- | ---------------------- |
| New array return karta hai  | Kuch return nahi karta |
| Data transformation ke liye | Iteration ke liye      |
| Chaining possible           | Chaining possible nahi |

---

# Example Difference

## map()

```js id="v4w5x6"
const result = arr.map(num => num * 2)
```

Returns:

```js id="y7z8a9"
[2,4,6]
```

---

## forEach()

```js id="b1c2d3"
const result = arr.forEach(num => num * 2)
```

Returns:

```js id="e4f5g6"
undefined
```

---

# Interview Answer

“map() is used when we need a transformed new array, while forEach() is used only for iteration or side effects.

map() returns a new array but forEach() does not return anything.”

# What is the difference between slice() and splice()?

---

# slice()

## Definition

`slice()` array ka selected portion copy karta hai and new array return karta hai.

Original array change nahi hota ❌

---

# Syntax

```js id="slice1"
array.slice(start, end)
````

---

# Example

```js id="slice2"
const arr = [1,2,3,4,5]

const result = arr.slice(1,4)

console.log(result)
```

## Output

```js id="slice3"
[2,3,4]
```

---

# Important Point

✅ Original array unchanged

---

# splice()

## Definition

`splice()` array me:

* add
* remove
* replace

kar sakta hai.

Original array change hota hai ✅

---

# Syntax

```js id="splice1"
array.splice(start, deleteCount, item)
```

---

# Example

```js id="splice2"
const arr = [1,2,3,4,5]

arr.splice(1,2)

console.log(arr)
```

## Output

```js id="splice3"
[1,4,5]
```

---

# Main Difference

| slice()                         | splice()                        |
| ------------------------------- | ------------------------------- |
| New array return karta hai      | Original array modify karta hai |
| Original array change nahi hota | Original array change hota hai  |
| Copy/extract ke liye            | Add/remove/update ke liye       |

---

# Interview Answer

“slice() array ka portion copy karke new array return karta hai without modifying original array, while splice() original array ko modify karta hai for adding, removing, or replacing elements.”

---


# Map

```js id="n0z7va"
let map = new Map();
```

Ye JavaScript me ek new `Map` object create karta hai.

`Map` ek special data structure hai jo:

```txt id="96mybc"
key → value
```

format me data store karta hai.

---

# Easy Example

```js id="vjlwm0"
let map = new Map();

map.set("name", "Rahul");
map.set("age", 25);

console.log(map);
```

---

# Output

```js id="6gvjlwm"
Map(2) {
  'name' => 'Rahul',
  'age' => 25
}
```

---

# Understanding

Here:

| Key      | Value     |
| -------- | --------- |
| `"name"` | `"Rahul"` |
| `"age"`  | `25`      |

---

# Important Methods

| Method     | Meaning          |
| ---------- | ---------------- |
| `set()`    | value add/update |
| `get()`    | value get        |
| `has()`    | check key exists |
| `delete()` | remove key       |

---

# Example

## Add Value

```js id="jlwm1a"
map.set("city", "Mumbai");
```

---

## Get Value

```js id="jlwm2b"
console.log(map.get("city"));
```

Output:

```js id="jlwm3c"
Mumbai
```

---

## Check Key

```js id="jlwm4d"
console.log(map.has("city"));
```

Output:

```js id="jlwm5e"
true
```

---

# Why Use Map?

Because:

* fast searching
* key-value storage
* any datatype as key allowed

---

# Difference Between Object and Map

| Object           | Map                |
| ---------------- | ------------------ |
| `{}`             | `new Map()`        |
| normal key-value | advanced key-value |
| limited features | extra methods      |

---

# Interview Line

> `new Map()` creates a Map object used to store data in key-value pair format.



## 1. Difference Between `substring()`, `substr()`, and `slice()`

| Method        | Syntax                      | Negative Index Support | Second Parameter Meaning | Notes                       |
| ------------- | --------------------------- | ---------------------- | ------------------------ | --------------------------- |
| `substring()` | `str.substring(start, end)` | ❌ No                   | Ending index             | Swaps values if start > end |
| `substr()`    | `str.substr(start, length)` | ✅ Yes                  | Length                   | Deprecated                  |
| `slice()`     | `str.slice(start, end)`     | ✅ Yes                  | Ending index             | Most commonly used          |

---

# A. `substring()`

## Syntax

```js
string.substring(start, end)
```

* `start` → starting index
* `end` → ending index (not included)

---

## Example

```js
let str = "JavaScript";

console.log(str.substring(0, 4));
```

### Output

```js
Java
```

---

## Important Points

### 1. End index is NOT included

```js
let str = "Hello";

console.log(str.substring(0, 2));
```

### Output

```js
He
```

---

### 2. Negative values become 0

```js
let str = "Hello";

console.log(str.substring(-2, 3));
```

### Output

```js
Hel
```

---

### 3. If start > end, values are swapped

```js
let str = "JavaScript";

console.log(str.substring(7, 4));
```

### Output

```js
Scr
```

---

# B. `substr()` (Deprecated)

## Syntax

```js
string.substr(start, length)
```

* `start` → starting index
* `length` → number of characters

---

## Example

```js
let str = "JavaScript";

console.log(str.substr(4, 6));
```

### Output

```js
Script
```

---

## Negative Index Supported

```js
let str = "JavaScript";

console.log(str.substr(-6, 6));
```

### Output

```js
Script
```

---

# Important Interview Point

`substr()` is deprecated.

👉 Modern projects mainly use:

* `slice()`
* `substring()`

---

# C. `slice()`

## Syntax

```js
string.slice(start, end)
```

* `start` → starting index
* `end` → ending index (not included)

---

## Example

```js
let str = "JavaScript";

console.log(str.slice(4, 10));
```

### Output

```js
Script
```

---

## Negative Index Supported

```js
let str = "JavaScript";

console.log(str.slice(-6));
```

### Output

```js
Script
```

---

# Important Difference

## `slice()` DOES NOT swap values

```js
let str = "JavaScript";

console.log(str.slice(7, 4));
```

### Output

```js
```

(Empty string)

---

# Quick Interview Comparison

| Feature               | substring() | substr() | slice()       |
| --------------------- | ----------- | -------- | ------------- |
| Negative Index        | ❌           | ✅        | ✅             |
| Deprecated            | ❌           | ✅        | ❌             |
| Swaps Start & End     | ✅           | ❌        | ❌             |
| Most Used in Projects | Medium      | Rare     | ✅ Very Common |

---

# Which One Should You Use?

## Best Practice

### Use `slice()` in modern applications

Why?

* Supports negative indexes
* Cleaner behavior
* Most common in React/JavaScript projects
* Preferred in interviews

---

# Interview Question

## Q: Why is `substr()` avoided nowadays?

### Answer

`substr()` is deprecated, meaning it may be removed in future JavaScript versions. Modern applications mainly use `slice()` or `substring()`.

---

# Real Project Examples

## 1. Extract File Extension

```js
let file = "photo.png";

console.log(file.slice(file.lastIndexOf(".")));
```

### Output

```js
.png
```

---

## 2. Get Last 4 Digits of Card

```js
let card = "1234567890123456";

console.log(card.slice(-4));
```

### Output

```js
3456
```

---

# Valid Parentheses Problem (Using Stack)

# Problem Statement

Given a string containing:

```txt
() {} []
```

Check if the parentheses are valid.

A string is valid if:

* Every opening bracket has a closing bracket
* Correct order is maintained

---

# Example

## Input

```js
"()[]{}"
```

## Output

```js
true
```

---

## Input

```js
"(]"
```

## Output

```js
false
```

# Is JavaScript Tightly Coupled or Loosely Coupled?

JavaScript is a **loosely coupled language**.

---

# What is Loosely Coupled?

In a loosely coupled system:

* Components/modules depend less on each other.
* One module can change without affecting others much.
* Code becomes flexible and reusable.

JavaScript supports:

* Functions
* Objects
* Modules
* Event-driven programming

Because of this, JavaScript applications are generally loosely coupled.

---

# Why is JavaScript Loosely Coupled?

## 1. Dynamic Typing

Variables can store any type of value.

Example:

```js id="h7x0dl"
let data = 10;
data = "Hello";
```

No strict dependency on data types.

---

## 2. Functions are Independent

Functions can work separately and can be passed as arguments.

```js id="9rwjlwm"
function greet(name) {
  return "Hello " + name;
}
```

---

## 3. Modules can be Separate

JavaScript allows splitting code into different files/modules.

Example:

```js id="fxx13x"
export function add(a, b) {
  return a + b;
}
```

Different modules communicate only when needed.

---

## 4. Event-Driven Nature

JavaScript uses events and callbacks, reducing direct dependency between components.

Example:

```js id="ecoj69"
button.addEventListener("click", handleClick);
```

Button does not need to know internal logic of `handleClick`.

---

# Can JavaScript be Tightly Coupled?

Yes, if developers write code where modules heavily depend on each other.

Example:

* Direct object dependency
* Global variable dependency
* Hardcoded logic

But by nature, JavaScript supports loose coupling.

---

# Interview Short Answer

“JavaScript is generally considered a loosely coupled language because its components, functions, and modules can work independently with minimal dependency on each other. Features like dynamic typing, first-class functions, and modular programming help achieve loose coupling.”


# localeCompare() in JavaScript

## Definition

`localeCompare()` is a string method used to compare two strings.

It is mainly used for:

* Sorting strings
* Alphabetical order
* Case-sensitive comparison

---

# Syntax

```js id="q1mx3u"
string1.localeCompare(string2)
```

---

# Return Values

| Value         | Meaning                |
| ------------- | ---------------------- |
| Negative (-1) | string1 comes first    |
| Positive (1)  | string2 comes first    |
| 0             | Both strings are equal |

---

# Example 1

```js id="w0xgj1"
console.log("Amit".localeCompare("Rahul"));
```

## Output

```js id="ny3i67"
-1
```

### Explanation

`Amit` comes before `Rahul`.

---

# Example 2

```js id="z8r3x5"
console.log("Rahul".localeCompare("Amit"));
```

## Output

```js id="p5h2w9"
1
```

### Explanation

`Rahul` comes after `Amit`.

---

# Example 3

```js id="v9l2d4"
console.log("Amit".localeCompare("Amit"));
```

## Output

```js id="t8g7e1"
0
```

---

# Used in Sorting Array of Objects

## Program

```js id="k3n8y2"
const users = [
  { name: "Rahul" },
  { name: "Amit" },
  { name: "Neha" }
];

users.sort((a, b) => a.name.localeCompare(b.name));

console.log(users);
```

---

# Output

```js id="d4m1q7"
[
  { name: "Amit" },
  { name: "Neha" },
  { name: "Rahul" }
]
```

---

# Descending Order

```js id="x7w5f2"
users.sort((a, b) => b.name.localeCompare(a.name));
```

---

# Interview Points

* `localeCompare()` is used for string comparison.
* Mostly used inside `sort()`.
* Helpful for alphabetical sorting.
* Works better than normal string comparison.

---

# Simple Interview Answer

`localeCompare()` is a JavaScript string method used to compare two strings and mainly used for sorting strings alphabetically.

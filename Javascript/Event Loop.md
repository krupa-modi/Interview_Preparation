
# Event Loop in JavaScript

## What is Event Loop?

Event loop is a mechanism that allows JavaScript to handle **asynchronous operations** despite being single-threaded.

JavaScript is single-threaded, but the event loop allows it to handle asynchronous tasks without blocking the main thread.

Note:
  * setTimeout(), DOM APis, fetch() , console, location, localstorage ye sab browser ki property hai javascript ki nae isko call  stack main access karne ke liye window(Global Object) keyword use hota hai.
  * function ya jo bhi code pehle excute hota hai to wo call stack main pegle global execution context banta hai than code line by line execute hota hai . abhi call stack main jo bhi chize hogi wo immediatly execute ho jayegi.
  * jab settimeout ka function hoga wo wait krega webapis main jayega wo directly call stack main nae ja sakta to pehle wo callback queue main jayega and event loop dono side check karega call stack empty hai to wo callback queue ko call stack main push krega and call stack usko execute kar dega.
  * jo b call back function promise throuth hoga usko wo microtask queue main dalega and priority micotask queue ki rahegi pehle wo execute hoga then mcallback queue.
  * callback queue ko macrotask queue bhi bolte hia.

---

## Components

1. Call Stack (Synchronous code runs first)
2. Web APIs
3. Callback Queue
4. Event Loop


---

## Flow Example

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

### Output:

```
Start
End
Timeout
```

---

## How it Works

1. `Start` → Call Stack
2. `setTimeout` → Web API
3. `End` → executed
4. Callback → moves to queue
5. Event loop → pushes to stack

## How it works:
Code runs in call stack
Asynchronous tasks (setTimeout, fetch) move to Web APIs
Their callbacks move to callback queue
Event loop pushes them back to the stack when empty




---

## Key Concept

👉 JS executes **sync first**, then async

---

## Important

Even `setTimeout(..., 0)` is not immediate

---

## Key Points

* Event loop manages async tasks
* Stack must be empty before queue executes
* Makes JS non-blocking

---

# 🧠 JavaScript Execution: setTimeout with 0ms (Step-by-Step)

## 🔹 Example Code

```js
setTimeout(() => {
  console.log("Hi");
}, 0);

console.log("Hello");
```

---

## 🔹 Actual Output

```bash
Hello
Hi
```

---

## 🧠 Step-by-Step Execution

### 1️⃣ Call Stack (Synchronous Code Runs First)

```js
console.log("Hello");
```

✔ Runs immediately → prints:

```bash
Hello
```

---

### 2️⃣ setTimeout Behavior

```js
setTimeout(() => {
  console.log("Hi");
}, 0);
```

* It does **NOT run immediately** ❌
* It is sent to **Web APIs (Browser environment)**
* Timer starts (0 ms)

---

### 3️⃣ Callback Queue

After timer completes (0 ms):

* The callback:

```js
() => console.log("Hi")
```

* Moves to 👉 **Callback Queue**

---

### 4️⃣ Event Loop Checks

The Event Loop continuously checks:

> “Is the Call Stack empty?”

✔ If YES → it takes the callback from queue and pushes it into the Call Stack

---

### 5️⃣ Final Execution

```js
console.log("Hi");
```

✔ Output:

```bash
Hi
```

---

## 🎯 Key Concept

👉 `setTimeout(fn, 0)` does **NOT mean run immediately**
👉 It means:

> "Run this after all synchronous code is finished"

---

## ⚡ Important Notes (Interview Focus)

* JavaScript is **single-threaded**
* Synchronous code runs first
* Async callbacks wait in queue
* Event Loop controls execution order

---

## 🧪 One More Example

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

### Output:

```bash
Start
End
Timeout
```

---

## 📦 Simple Analogy

* Call Stack = Current work
* setTimeout = Task waiting in line
* Event Loop = Manager checking when to execute next task

---

## ✅ Final Summary

✔ Synchronous → First
✔ setTimeout → Goes to queue
✔ Event Loop → Executes later
✔ Order → Always predictable

---


# Event Loop + Microtask Queue in JavaScript

Tumne Event Loop ka basic part sahi likha hai 👍
Ab isme sabse important concept aata hai:

# 🔥 Microtask Queue

Ye interview me bahut pucha jata hai because promises internally isi queue ko use karte hain.

---

# 📌 Queues in JavaScript

JavaScript me mainly 2 queues hoti hain:

| Queue Type                       | Contains                                                       |
| -------------------------------- | -------------------------------------------------------------- |
| Callback Queue (Macrotask Queue) | setTimeout, setInterval, DOM Events                            |
| Microtask Queue                  | Promise.then, catch, finally, queueMicrotask, MutationObserver |

---

# ⚡ Priority Rule

👉 **Microtask Queue always executes BEFORE Callback Queue**

Matlab:

```txt
Call Stack Empty
   ↓
Run All Microtasks
   ↓
Run One Callback Queue Task
```

---

# 🧠 Important Flow

```txt
Synchronous Code
↓
Microtask Queue
↓
Callback Queue (Macrotask)
```

---

# 🔥 Example 1 — Promise vs setTimeout

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

---

# ✅ Output

```bash
Start
End
Promise
Timeout
```

---

# 🧠 Step-by-Step Execution

---

## 1️⃣ `console.log("Start")`

Runs immediately

```bash
Start
```

---

## 2️⃣ `setTimeout`

```js
setTimeout(() => {
  console.log("Timeout");
}, 0);
```

* Goes to Web APIs
* After 0ms → callback goes to **Callback Queue**

---

## 3️⃣ Promise

```js
Promise.resolve().then(() => {
  console.log("Promise");
});
```

👉 `.then()` callback goes to:

# ✅ Microtask Queue

NOT callback queue.

---

## 4️⃣ `console.log("End")`

Runs immediately

```bash
End
```

---

## 5️⃣ Event Loop Checks

Call Stack empty now.

First Event Loop checks:

# ✅ Microtask Queue First

Runs:

```bash
Promise
```

---

## 6️⃣ Then Callback Queue

Runs:

```bash
Timeout
```

---

# 🎯 Final Order

```txt
Sync Code
↓
Microtasks
↓
Macrotasks
```

---

# 🔥 Why Promise Executes First?

Because:

```txt
Microtask Queue > Callback Queue
```

Microtasks have HIGHER PRIORITY.

---

# 📦 Things That Go Inside Microtask Queue

## ✅ 1. Promise callbacks

```js
Promise.then()
Promise.catch()
Promise.finally()
```

Example:

```js
Promise.resolve().then(() => {
  console.log("Microtask");
});
```

---

## ✅ 2. queueMicrotask()

Special API for directly creating microtasks.

```js
queueMicrotask(() => {
  console.log("Microtask");
});
```

---

## ✅ 3. MutationObserver

Used in DOM changes.

Mostly advanced/frontend internal usage.

---

# 📦 Things That Go Inside Callback Queue (Macrotask Queue)

| API             | Queue                              |
| --------------- | ---------------------------------- |
| setTimeout      | Callback Queue                     |
| setInterval     | Callback Queue                     |
| DOM Events      | Callback Queue                     |
| click events    | Callback Queue                     |
| fetch callbacks | Microtask after promise resolution |
| message events  | Callback Queue                     |

---

# 🔥 fetch() Important Interview Point

```js
fetch()
```

Actually browser API hai.

When response arrives:

```js
.then()
```

goes to:

# ✅ Microtask Queue

Example:

```js
fetch("url")
  .then(() => {
    console.log("Fetched");
  });
```

`.then()` is always microtask.

---

# 🔥 Example 2 (Very Important Interview Question)

```js
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
```

---

# ✅ Output

```bash
1
4
3
2
```

---

# 🧠 Execution Flow

| Step | Action                         |
| ---- | ------------------------------ |
| 1    | print 1                        |
| 2    | setTimeout → callback queue    |
| 3    | Promise.then → microtask queue |
| 4    | print 4                        |
| 5    | microtask executes → 3         |
| 6    | callback queue executes → 2    |

---

# 🔥 Another Advanced Example

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise 1");
}).then(() => {
  console.log("Promise 2");
});

console.log("End");
```

---

# ✅ Output

```bash
Start
End
Promise 1
Promise 2
Timeout
```

---

# 🧠 Why?

Because Event Loop:

## ✅ Executes ALL microtasks completely first

Only after microtask queue becomes empty:

👉 Then callback queue starts.

---

# 📌 Golden Interview Rule

# ✅ Entire Microtask Queue executes before next Macrotask

Very important.

---

# 🧠 Visual Flow

```txt
Call Stack
   ↓
Microtask Queue
(Promise.then)
   ↓
Callback Queue
(setTimeout)
```

---

# 🔥 Difference Between Microtask & Callback Queue

| Feature  | Microtask Queue             | Callback Queue   |
| -------- | --------------------------- | ---------------- |
| Priority | Higher                      | Lower            |
| Executes | Immediately after sync code | After microtasks |
| Examples | Promise.then                | setTimeout       |
| Speed    | Faster                      | Slower           |

---

# ⚡ Tricky Interview Question

```js
setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("Hello");
```

# ✅ Output

```bash
Hello
Promise
Timeout
```

---

# 🔥 Super Important Interview Notes

## ✅ JavaScript is Single Threaded

Only one thing runs at a time.

---

## ✅ Browser Provides Web APIs

Like:

* setTimeout
* fetch
* DOM
* localStorage
* console

These are NOT pure JavaScript features.

---

## ✅ Event Loop Job

Event Loop checks:

```txt
Is Call Stack Empty?
```

If yes:

1. Execute all microtasks
2. Then execute callback queue tasks

---

# 🎯 Final Summary

## Execution Order

```txt
1. Synchronous Code
2. Microtask Queue
3. Callback Queue
```

---

# 📦 Microtask Queue Contains

✔ Promise.then
✔ Promise.catch
✔ Promise.finally
✔ queueMicrotask
✔ MutationObserver

---

# 📦 Callback Queue Contains

✔ setTimeout
✔ setInterval
✔ DOM Events
✔ Click Handlers

---

# 🔥 Most Important Interview Line

> Promise callbacks always execute before setTimeout callbacks.

---

# 🧠 One-Line Memory Trick

```txt
Sync → Microtask → Macrotask
```

Ye line yaad rakhoge to Event Loop kabhi nahi bhoologe 🚀



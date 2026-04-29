
# Event Loop in JavaScript

## What is Event Loop?

Event loop is a mechanism that allows JavaScript to handle **asynchronous operations** despite being single-threaded.

JavaScript is single-threaded, but the event loop allows it to handle asynchronous tasks without blocking the main thread.


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


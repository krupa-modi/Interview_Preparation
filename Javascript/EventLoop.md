
# Event Loop in JavaScript

## What is Event Loop?

Event loop is a mechanism that allows JavaScript to handle **asynchronous operations** despite being single-threaded.

JavaScript is single-threaded, but the event loop allows it to handle asynchronous tasks without blocking the main thread.


---

## Components

1. Call Stack
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

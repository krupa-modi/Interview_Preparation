# setTimeout in JavaScript (Deep Dive for Interview)

## What is `setTimeout`?

`setTimeout` is a **Web API function** used to execute a callback function **after a specified delay (in milliseconds)**.

```js id="syn1"
setTimeout(callback, delay);
```

---

## Basic Example

```js id="ex1"
console.log("Start");

setTimeout(() => {
  console.log("Hello after 2 sec");
}, 2000);

console.log("End");
```

### Output:

```
Start
End
Hello after 2 sec
```

👉 Even though delay is 2 sec, JS doesn’t block execution.

---

## How setTimeout Works Internally 🔥

### Step-by-step flow:

1. Code runs → goes into **Call Stack**
2. `setTimeout` → sent to **Web API (Browser)**
3. Timer starts
4. After delay → callback goes to **Callback Queue**
5. **Event Loop** checks:

   * If call stack is empty → pushes callback to stack

---

## Important Concept: It is Asynchronous

```js id="ex2"
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
```

### Output:

```
A
C
B
```

👉 Even `0ms` delay is **not immediate**

---

## Why Delay is Not Exact?

* `setTimeout` gives **minimum delay**
* Actual execution depends on:

  * Call stack status
  * Event loop
  * System performance

---

## Blocking Example

```js id="ex3"
setTimeout(() => {
  console.log("Timeout");
}, 1000);

for (let i = 0; i < 1e9; i++) {} // blocking loop
```

👉 Output will be delayed more than 1 sec
Because call stack is busy

---

## clearTimeout (Cancel Execution)

```js id="ex4"
const id = setTimeout(() => {
  console.log("Will not run");
}, 2000);

clearTimeout(id);
```

👉 Stops execution before timer completes

---

## setTimeout with Arguments

```js id="ex5"
function greet(name) {
  console.log("Hello " + name);
}

setTimeout(greet, 1000, "Krupa");
```

---

## setTimeout vs setInterval

| Feature | setTimeout | setInterval         |
| ------- | ---------- | ------------------- |
| Runs    | Once       | Repeatedly          |
| Control | Easy       | Needs clearInterval |

---

## Common Interview Trap 🔥

```js id="ex6"
for (var i = 1; i <= 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

### Output:

```
4
4
4
```

👉 Why?

* `var` is function scoped
* All callbacks share same `i`

### Fix using `let`

```js id="ex7"
for (let i = 1; i <= 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

### Output:

```
1
2
3
```

---

## Interview One-Liner

👉 "`setTimeout` schedules a callback to run after a delay using the Web API and event loop; it is asynchronous and non-blocking."



If you want, I can give you **event loop + setTimeout tricky questions (very important 🔥)** that are frequently asked in interviews.


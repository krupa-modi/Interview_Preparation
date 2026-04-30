# Callback Function in JavaScript (Interview Guide)

## What is a Callback Function?

A callback is a **function passed as an argument to another function**, which is executed later.

👉 In simple words:
"Function ko kisi aur function ke andar pass karna aur baad me call karna"

---

## Basic Example

```js id="cb1"
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}

function sayBye() {
  console.log("Goodbye!");
}

greet("Krupa", sayBye);
```

### Output:

```id="cbout1"
Hello Krupa
Goodbye!
```

👉 `sayBye` is a callback function

---

## Why Callbacks are Used?

* To handle **asynchronous operations**
* To execute code **after a task completes**

---

## Asynchronous Example (Important 🔥)

```js id="cb2"
console.log("Start");

setTimeout(() => {
  console.log("Inside callback");
}, 2000);

console.log("End");
```

### Output:

```id="cbout2"
Start
End
Inside callback
```

👉 Callback runs after delay (async behavior)

---

## Callback with Array Methods

```js id="cb3"
const nums = [1, 2, 3];

nums.forEach(function(num) {
  console.log(num);
});
```

👉 Here function inside `forEach` is callback

---

## Types of Callbacks

### 1. Synchronous Callback

```js id="cb4"
[1,2,3].map(num => num * 2);
```

👉 Executes immediately

---

### 2. Asynchronous Callback

```js id="cb5"
setTimeout(() => {
  console.log("Async");
}, 1000);
```

👉 Executes later

---

## Callback Hell ❗ (Interview Important)

```js id="cb6"
setTimeout(() => {
  console.log("Step 1");
  setTimeout(() => {
    console.log("Step 2");
    setTimeout(() => {
      console.log("Step 3");
    }, 1000);
  }, 1000);
}, 1000);
```

👉 Problems:

* Hard to read
* Hard to maintain

---

## Solution to Callback Hell

* Promises
* Async/Await

---

## Error Handling in Callbacks

```js id="cb7"
function fetchData(callback) {
  let error = false;

  if (error) {
    callback("Error occurred", null);
  } else {
    callback(null, "Data received");
  }
}

fetchData((err, data) => {
  if (err) {
    console.log(err);
  } else {
    console.log(data);
  }
});
```

👉 Standard pattern: `(error, data)`

---

## Key Points

* Callback = function passed to another function
* Used heavily in async programming
* Can lead to callback hell
* Improved with Promises & async/await

---

## Interview One-Liner

👉 "A callback function is a function passed as an argument to another function and executed later, commonly used for asynchronous operations."

---


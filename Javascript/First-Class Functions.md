# 1. What are First-Class Functions?

In JavaScript, functions are treated like normal values.

👉 This means functions can:

* Be assigned to variables
* Be passed as arguments
* Be returned from another function

Because of this, JavaScript functions are called **First-Class Functions**.

---

# 🔥 Example 1: Assign Function to Variable

```js
const greet = function() {
  console.log("Hello");
};

greet();
```

👉 Function stored inside variable.

---

# 🔥 Example 2: Pass Function as Argument

```js
function sayHello() {
  console.log("Hello");
}

function execute(fn) {
  fn();
}

execute(sayHello);
```

👉 Function passed as parameter.

---

# 🔥 Example 3: Return Function

```js
function outer() {
  return function inner() {
    console.log("Inside inner");
  };
}

const result = outer();
result();
```

👉 Function returned from another function.

---

# 🎯 Real-World Use Case

Used heavily in:

* Event handlers
* Callbacks
* Promises
* React Hooks

---

# 🎯 Final Interview Answer

👉 JavaScript functions are called first-class functions because they can be treated like values — assigned to variables, passed as arguments, and returned from other functions.

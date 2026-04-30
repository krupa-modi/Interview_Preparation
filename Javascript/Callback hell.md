
# Callback Hell in JavaScript (Interview Guide)

## What is Callback Hell?

Callback Hell is a situation where **multiple nested callbacks** are used, making code:

* Hard to read 😵
* Hard to maintain
* Difficult to debug

👉 Also called **"Pyramid of Doom"** because of its shape

---

## Example of Callback Hell 🔥

```js id="ch1"
setTimeout(() => {
  console.log("Step 1");

  setTimeout(() => {
    console.log("Step 2");

    setTimeout(() => {
      console.log("Step 3");

      setTimeout(() => {
        console.log("Step 4");
      }, 1000);

    }, 1000);

  }, 1000);

}, 1000);
```

👉 Structure becomes deeply nested (like pyramid)

---

## Problems with Callback Hell

* ❌ Poor readability
* ❌ Hard to manage logic
* ❌ Difficult error handling
* ❌ Not scalable

---

## Real-Life Example

```js id="ch2"
loginUser(user, (userData) => {
  getOrders(userData, (orders) => {
    getOrderDetails(orders, (details) => {
      console.log(details);
    });
  });
});
```

👉 Each step depends on previous → nesting increases

---

## How to Avoid Callback Hell ✅

### 1. Using Promises

```js id="ch3"
loginUser(user)
  .then(getOrders)
  .then(getOrderDetails)
  .then(console.log)
  .catch(console.error);
```

---

### 2. Using Async/Await (Best 🔥)

```js id="ch4"
async function process() {
  try {
    const user = await loginUser();
    const orders = await getOrders(user);
    const details = await getOrderDetails(orders);

    console.log(details);
  } catch (err) {
    console.error(err);
  }
}
```

---

## Key Points

* Happens due to **nested callbacks**
* Makes code messy and unmaintainable
* Solved using **Promises / Async-Await**

---

## Interview One-Liner

👉 "Callback hell is a situation where deeply nested callbacks make code difficult to read and maintain, often solved using Promises or async/await."

---

If you want, I can give you **real interview questions on callback hell + promises conversion** (very common 🔥).

# Promise.all vs Promise.race vs Promise.allSettled

# 1. Promise.all()

## What is Promise.all()?

Runs multiple Promises in parallel.

Returns result only when:
- ALL Promises are successful

If one Promise fails:
- entire Promise fails

---

# Why Use It?

Used when:
- all tasks are required
- all API responses needed together

---

# Syntax

```js
Promise.all([promise1, promise2, promise3])
````

---

# Example

```js
const p1 = Promise.resolve("API 1");
const p2 = Promise.resolve("API 2");
const p3 = Promise.resolve("API 3");

Promise.all([p1, p2, p3])

.then((res) => {
    console.log(res);
})

.catch((err) => {
    console.log(err);
});
```

---

# Output

```js
["API 1", "API 2", "API 3"]
```

---

# Important Point

If one Promise rejects:

```js
Promise.all() -> immediately reject
```

---

# Real-world Use Cases

* Dashboard data loading
* Multiple APIs together
* Product + User + Order fetch

---

# 2. Promise.race()

# What is Promise.race()?

Returns result of:

* first completed Promise

Can be:

* resolved
* rejected

---

# Why Use It?

Used when:

* fastest response needed
* timeout handling

---

# Syntax

```js
Promise.race([promise1, promise2])
```

---

# Example

```js
const p1 = new Promise((resolve) =>
    setTimeout(() => resolve("First"), 1000)
);

const p2 = new Promise((resolve) =>
    setTimeout(() => resolve("Second"), 2000)
);

Promise.race([p1, p2])

.then((res) => {
    console.log(res);
});
```

---

# Output

```js
First
```

---

# Real-world Use Cases

* API timeout
* Fastest server response
* CDN requests

---

# 3. Promise.allSettled()

# What is Promise.allSettled()?

Waits for all Promises to complete.

Does not fail if one Promise fails.

Returns:

* success status
* failure status

for every Promise.

---

# Why Use It?

Used when:

* all results needed
* even failed ones important ho

---

# Syntax

```js
Promise.allSettled([promise1, promise2])
```

---

# Example

```js
const p1 = Promise.resolve("Success");

const p2 = Promise.reject("Failed");

Promise.allSettled([p1, p2])

.then((res) => {
    console.log(res);
});
```

---

# Output

```js
[
  { status: "fulfilled", value: "Success" },
  { status: "rejected", reason: "Failed" }
]
```

---

# Real-world Use Cases

* Multiple independent APIs
* Analytics requests
* Notifications system

---

# Difference Table

| Feature                  | Promise.all       | Promise.race     | Promise.allSettled |
| ------------------------ | ----------------- | ---------------- | ------------------ |
| Waits for all?           | Yes               | No               | Yes                |
| Fails if one fails?      | Yes               | Depends on first | No                 |
| Returns first completed? | No                | Yes              | No                 |
| Best Use Case            | All data required | Fastest result   | Need all results   |

---

# Interview Questions

## Q1. Which Promise method fails immediately?

`Promise.all()`

---

## Q2. Which method returns first completed Promise?

`Promise.race()`

---

## Q3. Which method gives both success and failure results?

`Promise.allSettled()`

---

## Q4. Which method is best for multiple independent APIs?

`Promise.allSettled()`

---

# Quick Revision

## Promise.all()

All success required.

---

## Promise.race()

First completed result.

---

## Promise.allSettled()

All results needed, even failed ones.


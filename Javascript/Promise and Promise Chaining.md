# What is Promise in JavaScript?

## Definition
A **Promise** is a JavaScript object that handles **asynchronous operations**.

It represents a value that may:
- be available now
- come later
- or fail

Promise helps avoid:
- callback hell
- messy async code
- deeply nested callbacks

---

# Why Promise is Used?

Promise is used when a task takes time to complete.

## Common Use Cases
- API calls
- Database requests
- File upload/download
- Timer functions
- Fetching data from server

---

# Syntax

```js
const promise = new Promise((resolve, reject) => {
    
    let success = true;

    if(success){
        resolve("Data fetched successfully");
    } else {
        reject("Error while fetching data");
    }

});
````

---

# Promise States

A Promise has 3 states:

---

## 1. Pending

Initial state.

Meaning:

* operation is still running
* result not available yet

```js
Promise { <pending> }
```

---

## 2. Fulfilled (Resolved)

Operation completed successfully.

```js
resolve("Success")
```

---

## 3. Rejected

Operation failed.

```js
reject("Error")
```

---

# .then()

## What is .then()?

`.then()` runs when Promise is successfully resolved.

## Why Use It?

Used to handle success response.

## Syntax

```js
promise.then((result) => {
    console.log(result);
});
```

## Example

```js
const data = Promise.resolve("API Success");

data.then((res) => {
    console.log(res);
});
```

## Output

```js
API Success
```

---

# .catch()

## What is .catch()?

`.catch()` handles Promise errors.

## Why Use It?

Used for error handling.

## Syntax

```js
promise.catch((error) => {
    console.log(error);
});
```

## Example

```js
const data = Promise.reject("API Failed");

data.catch((err) => {
    console.log(err);
});
```

## Output

```js
API Failed
```

---

# .finally()

## What is .finally()?

`.finally()` runs always:

* success ho ya
* error ho

## Why Use It?

Used for cleanup work.

## Common Uses

* loader hide karna
* connection close karna
* cleanup task

## Syntax

```js
promise.finally(() => {
    console.log("Completed");
});
```

## Example

```js
fetch("api/data")
    .then((res) => console.log(res))
    .catch((err) => console.log(err))
    .finally(() => {
        console.log("Request Finished");
    });
```

---

# Complete Promise Example

```js
const myPromise = new Promise((resolve, reject) => {

    let success = true;

    if(success){
        resolve("Data Loaded");
    } else {
        reject("Something went wrong");
    }

});

myPromise
    .then((res) => {
        console.log(res);
    })
    .catch((err) => {
        console.log(err);
    })
    .finally(() => {
        console.log("Promise Completed");
    });
```

---

# Important Interview Points

## Promise Advantages

* Better async handling
* Avoid callback hell
* Cleaner code
* Better error handling

---

# Interview Questions

## Q1. What is Promise?

Promise is an object used to handle asynchronous operations.

---

## Q2. How many states are there in Promise?

3 states:

* Pending
* Fulfilled
* Rejected

---

## Q3. Difference between resolve and reject?

| resolve()       | reject()         |
| --------------- | ---------------- |
| Success case    | Error case       |
| Goes to .then() | Goes to .catch() |

---

## Q4. Does finally receive data?

No.

`.finally()` does not receive resolved/rejected data.

---

## Q5. Can multiple .then() be used?

Yes.

That is called Promise Chaining.

````

---

```md
# Promise Chaining in JavaScript

# What is Promise Chaining?

Promise chaining means:
- multiple `.then()` methods connected together
- output of one `.then()` becomes input of next `.then()`

---

# Why Use Promise Chaining?

Used when:
- one async task depends on previous task
- sequential operations needed
- API flow step-by-step execute karna ho

---

# Syntax

```js
promise
    .then()
    .then()
    .then()
    .catch()
````

---

# Example

```js
Promise.resolve(10)

    .then((num) => {
        return num + 10;
    })

    .then((num) => {
        return num * 2;
    })

    .then((result) => {
        console.log(result);
    })

    .catch((err) => {
        console.log(err);
    });
```

---

# Output

```js
40
```

---

# How It Works?

## Step 1

First Promise resolved with:

```js
10
```

---

## Step 2

First `.then()`

```js
10 + 10 = 20
```

Returns:

```js
20
```

---

## Step 3

Second `.then()`

```js
20 * 2 = 40
```

---

## Step 4

Final result printed.

---

# Important Rule

## Always return value from .then()

Correct:

```js
.then((data) => {
    return data;
})
```

Wrong:

```js
.then((data) => {
    data;
})
```

---

# Error Handling in Chaining

If any `.then()` fails:

* control goes directly to `.catch()`

Example:

```js
Promise.resolve(5)

.then((num) => {
    throw new Error("Something Wrong");
})

.catch((err) => {
    console.log(err.message);
});
```

---

# Where Promise Chaining is Used?

## Common Real-world Uses

* Login → Fetch User → Fetch Orders
* API request flow
* Payment processing
* Authentication systems

---

# Promise Chaining vs Callback Hell

## Callback Hell

```js
a(()=>{
   b(()=>{
      c(()=>{
      })
   })
})
```

Hard to read.

---

## Promise Chaining

```js
a()
.then(()=> b())
.then(()=> c())
```

Cleaner and maintainable.

---

# Interview Questions

## Q1. What is Promise Chaining?

Connecting multiple `.then()` methods together.

---

## Q2. Why Promise Chaining is used?

To execute async tasks sequentially.

---

## Q3. What happens if error occurs?

Control moves to `.catch()`.

---

## Q4. What should .then() return?

It should return:

* value
* or another Promise

```


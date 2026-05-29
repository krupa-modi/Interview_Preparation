
# JavaScript Polyfills - Complete Interview Preparation Guide

# 📌 What is a Polyfill?

Polyfill ek custom implementation hota hai jo modern JavaScript feature ko old browsers ya unsupported environments me support deta hai.

Simple words:

> Agar browser me koi built-in JavaScript feature available nahi hai, to hum uska custom version bana dete hain.

Us custom implementation ko Polyfill kehte hain.

---

# 📌 Real Example

Suppose:

```js
Array.prototype.map()
```

Old browsers me support nahi karta.

To hum khud uska implementation likhenge.

Ye implementation hi polyfill hai.

---

# 📌 Interview Definition

> Polyfill is a custom implementation of a modern JavaScript feature that provides support in environments where that feature is not available.

---

# 📌 Why Polyfills Are Needed?

## Reasons

* Browser compatibility
* Old browser support
* JavaScript internals understanding
* Interview machine coding rounds
* Missing functionality support

---

# 📌 Polyfill vs Transpiler

| Polyfill                        | Transpiler               |
| ------------------------------- | ------------------------ |
| Missing functionality add karta | Syntax convert karta     |
| Runtime pe work karta           | Build time pe work karta |
| Example: Promise polyfill       | Example: Babel           |
| Feature implement karta         | Syntax transform karta   |

---

# 📌 Most Asked Polyfills in Interviews

# Function Polyfills

| Polyfill   | Use                                    |
| ---------- | -------------------------------------- |
| bind()     | Function ka this bind karta hai        |
| call()     | Function immediately execute karta hai |
| apply()    | call jaisa but array arguments         |
| debounce() | Repeated calls control                 |
| throttle() | Limited interval execution             |

---

# 📌 Array Polyfills

| Polyfill  | Use                       |
| --------- | ------------------------- |
| map()     | Array transform           |
| filter()  | Condition based filtering |
| reduce()  | Single value generate     |
| forEach() | Loop                      |
| find()    | First matched element     |
| some()    | At least one true         |
| every()   | All true check            |
| flat()    | Nested array flatten      |

---

# 📌 Promise Polyfills

| Polyfill           | Use                      |
| ------------------ | ------------------------ |
| Promise            | Async handling           |
| Promise.all        | Multiple promises        |
| Promise.race       | First completed promise  |
| Promise.any        | First successful promise |
| Promise.allSettled | All results              |

---

# 📌 String Polyfills

| Polyfill     | Use            |
| ------------ | -------------- |
| includes()   | String check   |
| startsWith() | Starting check |
| endsWith()   | Ending check   |
| repeat()     | Repeat string  |
| trim()       | Remove spaces  |

---

# 📌 Object Polyfills

| Polyfill       | Use             |
| -------------- | --------------- |
| Object.create  | Object creation |
| Object.assign  | Merge objects   |
| Object.keys    | Get keys        |
| Object.values  | Get values      |
| Object.entries | Key-value pairs |

---

# 📌 Most Important Interview Polyfills 🔥

```js
bind
call
apply
map
filter
reduce
debounce
throttle
Promise
Promise.all
```

---

# 📌 map() Polyfill

# Native map()

```js
const arr = [1,2,3];

const result = arr.map((item) => item * 2);

console.log(result);
```

Output:

```js
[2,4,6]
```

---

# 📌 map() Polyfill

```js
Array.prototype.myMap = function(callback) {

    const result = [];

    for(let i = 0; i < this.length; i++) {

        result.push(callback(this[i], i, this));

    }

    return result;
};
```

Usage:

```js
const arr = [1,2,3];

const data = arr.myMap((item) => item * 2);

console.log(data);
```

---

# 📌 Important Interview Explanation

```js
this
```

Current array ko represent karta hai.

---

# 📌 filter() Polyfill

```js
Array.prototype.myFilter = function(callback) {

    const result = [];

    for(let i = 0; i < this.length; i++) {

        if(callback(this[i], i, this)) {
            result.push(this[i]);
        }

    }

    return result;
};
```

---

# 📌 reduce() Polyfill

```js
Array.prototype.myReduce = function(callback, initialValue) {

    let accumulator = initialValue;

    for(let i = 0; i < this.length; i++) {

        accumulator = callback(
            accumulator,
            this[i],
            i,
            this
        );

    }

    return accumulator;
};
```

---

# 📌 forEach() Polyfill

```js
Array.prototype.myForEach = function(callback) {

    for(let i = 0; i < this.length; i++) {

        callback(this[i], i, this);

    }

};
```

---

# 📌 call() Polyfill

```js
Function.prototype.myCall = function(context, ...args) {

    context.fn = this;

    context.fn(...args);

};
```

---

# 📌 apply() Polyfill

```js
Function.prototype.myApply = function(context, args = []) {

    context.fn = this;

    context.fn(...args);

};
```

Difference:

```js
call -> separate arguments
apply -> array arguments
```

---

# 📌 bind() Polyfill

```js
Function.prototype.myBind = function(context, ...args) {

    const fn = this;

    return function(...newArgs) {

        return fn.apply(context, [...args, ...newArgs]);

    };

};
```

---

# 📌 Debounce Polyfill

# What is Debounce?

Continuous function calls ko delay karta hai.

Used in:

* search input
* API optimization
* resize event

---

# 📌 Debounce Polyfill

```js
function debounce(fn, delay) {

    let timer;

    return function(...args) {

        clearTimeout(timer);

        timer = setTimeout(() => {

            fn.apply(this, args);

        }, delay);

    };

}
```

---

# 📌 Throttle Polyfill

# What is Throttle?

Specific interval ke baad hi function execute hota hai.

Used in:

* scroll events
* mouse movement
* resize

---

# 📌 Throttle Polyfill

```js
function throttle(fn, delay) {

    let lastCall = 0;

    return function(...args) {

        const now = new Date().getTime();

        if(now - lastCall >= delay) {

            lastCall = now;

            fn.apply(this, args);

        }

    };

}
```

---

# 📌 Promise Polyfill in JavaScript

# What is Promise Polyfill?

Agar browser me native Promise support nahi hai to hum custom Promise behavior create karte hain.

Usko Promise Polyfill bolte hain.

---

# 📌 Basic Promise Polyfill

```js
function MyPromise(executor) {
  let onResolve;
  let value;
  let isResolved = false;

  function resolve(val) {
    value = val;
    isResolved = true;

    if (onResolve) {
      onResolve(value);
    }
  }

  executor(resolve);

  this.then = function(callback) {
    onResolve = callback;

    if (isResolved) {
      onResolve(value);
    }
  };
}
```

---

# 📌 Usage

```js
const promise = new MyPromise((resolve) => {
  setTimeout(() => {
    resolve("Promise Resolved");
  }, 1000);
});

promise.then((data) => {
  console.log(data);
});
```

---

# 📌 Better Promise Polyfill with Reject

```js
function MyPromise(executor) {
  let onResolve;
  let onReject;
  let isFulfilled = false;
  let isRejected = false;
  let value;

  function resolve(val) {
    isFulfilled = true;
    value = val;

    if (onResolve) {
      onResolve(value);
    }
  }

  function reject(val) {
    isRejected = true;
    value = val;

    if (onReject) {
      onReject(value);
    }
  }

  this.then = function(callback) {
    onResolve = callback;

    if (isFulfilled) {
      onResolve(value);
    }

    return this;
  };

  this.catch = function(callback) {
    onReject = callback;

    if (isRejected) {
      onReject(value);
    }

    return this;
  };

  executor(resolve, reject);
}
```

---

# 📌 Promise States

```js
pending
fulfilled
rejected
```

---

# 📌 Important Concepts Used

| Concept        | Purpose               |
| -------------- | --------------------- |
| Closure        | Value store           |
| Callback       | then() handling       |
| Async          | setTimeout simulation |
| State handling | resolved/rejected     |

---

# 📌 Limitations of Simple Promise Polyfill

Missing features:

* catch()
* finally()
* chaining
* Promise.all()
* Promise.race()

---

# 📌 Common Interview Questions

# Beginner Level

## Q1. Polyfill kya hota hai?

## Q2. map() ka polyfill likho

## Q3. filter() ka polyfill likho

## Q4. reduce() ka polyfill likho

## Q5. bind() aur call() me difference?

---

# 📌 Intermediate Questions

## Q6. this keyword polyfill me kya hota?

## Q7. bind immediate execute kyu nahi karta?

## Q8. debounce vs throttle difference?

## Q9. call vs apply difference?

## Q10. map() new array return kyu karta?

---

# 📌 Advanced Questions

## Q11. Promise internally kaise work karta?

## Q12. Event loop ka relation promises se?

## Q13. Microtask queue kya hoti?

## Q14. Native methods faster kyu hote?

## Q15. Polyfills performance impact karte hai?

---

# 📌 Machine Coding Questions

Most common:

* custom map
* custom filter
* custom reduce
* custom bind
* debounce
* throttle
* Promise

---

# 📌 Common Mistakes

## Mistake 1

Arrow function prototype me use karna.

Wrong:

```js
Array.prototype.myMap = () => {}
```

Reason:

Arrow functions ka own this nahi hota.

---

# 📌 Mistake 2

return statement bhool jana.

---

# 📌 Mistake 3

Original array mutate kar dena.

---

# 📌 Why Companies Ask Polyfills?

Because it checks:

* JavaScript fundamentals
* prototypes
* this keyword
* callbacks
* closures
* execution flow
* problem solving

---

# 📌 Best Revision Plan

## Day 1

map/filter/reduce

## Day 2

call/apply/bind

## Day 3

debounce/throttle

## Day 4

Promise basics

## Day 5

Machine coding practice

---

# 📌 Final Interview Advice

Agar aap:

* code likh pao
* line by line explain kar pao
* real use case bata pao
* interviewer ke follow-up answer kar pao

to aapka JavaScript round bahut strong ho jayega 🚀


# JavaScript Polyfills - Complete Interview Preparation Guide

# 📌 What is a Polyfill?

Polyfill ek custom implementation hota hai jo modern JavaScript feature ko old browsers ya unsupported environments me support deta hai.

Simple words:

> Agar browser me koi built-in JavaScript feature available nahi hai, to hum uska custom version bana dete hain. Us custom implementation ko Polyfill kehte hain.

---

# 📌 Real Example

Suppose:

```js
Array.prototype.map()

JavaScript me sabhi arrays internally Array.prototype se methods inherit karti hain.
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

### Answer

Polyfill ek custom implementation hoti hai jo JavaScript ke naye features ko purane browsers me support karne ke liye banayi jati hai.

---

## Q2. map() ka polyfill likho

### Answer

```js
Array.prototype.myMap = function(callback) {
  let result = [];

  for(let i = 0; i < this.length; i++) {
    result.push(callback(this[i], i, this));
  }

  return result;
};
```

---

## Q3. filter() ka polyfill likho

### Answer

```js
Array.prototype.myFilter = function(callback) {
  let result = [];

  for(let i = 0; i < this.length; i++) {
    if(callback(this[i], i, this)) {
      result.push(this[i]);
    }
  }

  return result;
};
```

---

## Q4. reduce() ka polyfill likho

### Answer

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

## Q5. bind() aur call() me difference?

### Answer

| bind()                        | call()                                 |
| ----------------------------- | -------------------------------------- |
| New function return karta hai | Function immediately execute karta hai |
| Baad me call kar sakte hain   | Turant execute hota hai                |
| Reusable hai                  | One-time execution                     |

---

# Intermediate Questions

## Q6. this keyword polyfill me kya hota?

### Answer

`this` us object ko refer karta hai jisne function ko call kiya hai.

---

## Q7. bind immediate execute kyu nahi karta?

### Answer

`bind()` sirf new function return karta hai. Execution tab hota hai jab returned function ko call karte hain.

---

## Q8. debounce vs throttle difference?

### Answer

| Debounce                     | Throttle                              |
| ---------------------------- | ------------------------------------- |
| User stop kare tab execute   | Fixed interval par execute            |
| Search bar me use            | Scroll/Resize me use                  |
| Last action execute hota hai | Regular interval par execute hota hai |

---

## Q9. call vs apply difference?

### Answer

| call()                    | apply()              |
| ------------------------- | -------------------- |
| Arguments comma separated | Arguments array me   |
| fn.call(obj, 1, 2)        | fn.apply(obj, [1,2]) |

---

## Q10. map() new array return kyu karta?

### Answer

Original array ko modify kiye bina transformed values ke saath ek naya array return karne ke liye.

---

# Advanced Questions

## Q11. Promise internally kaise work karta?

### Answer

Promise asynchronous operation ko handle karta hai aur uski state:

```text
Pending
 ↓
Fulfilled / Rejected
```

maintain karta hai.

---

## Q12. Event loop ka relation promises se?

### Answer

Promise callbacks Microtask Queue me jate hain aur Event Loop unhe Call Stack empty hone ke baad execute karta hai.

---

## Q13. Microtask queue kya hoti?

### Answer

Microtask Queue ek high-priority queue hai jahan Promise callbacks, `queueMicrotask()` aur `MutationObserver` execute hote hain.

---

## Q14. Native methods faster kyu hote?

### Answer

Kyuki native methods browser engine (V8, SpiderMonkey) ke optimized internal code me likhe hote hain.

---

## Q15. Polyfills performance impact karte hai?

### Answer

Haan, polyfills native methods se thode slow ho sakte hain kyuki wo JavaScript me manually implement kiye jate hain.

---

# Quick Interview Revision

### Polyfill

> Browser me missing feature ka custom implementation.

### bind()

> New function return karta hai.

### call()

> Function immediately execute karta hai.

### apply()

> Array ke form me arguments leta hai.

### Debounce

> User stop kare tab execute.

### Throttle

> Fixed interval par execute.

### Promise

> Async operations handle karta hai.

### Microtask Queue

> Promise callbacks store karti hai.

### Event Loop

> Call Stack aur Queues ko manage karta hai.


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


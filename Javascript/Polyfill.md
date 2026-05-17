# Promise Polyfill in JavaScript

# 📌 What is Polyfill?

Polyfill ek custom implementation hota hai jo modern JavaScript feature ko old browsers me support deta hai.

Simple words:

> Agar browser me Promise support nahi hai, to hum khud Promise jaisa behavior create karte hain → usko Promise Polyfill bolte hain.

---

# 📌 Why Promise Polyfill Needed?

Old browsers:

* Internet Explorer
* Purane mobile browsers

Promise support nahi karte the.

Isliye developers Promise ka custom version banate the.

---

# 📌 Real Promise Example

```js id="9kqpr0"
const p = new Promise((resolve, reject) => {
  resolve("Success");
});

p.then((data) => {
  console.log(data);
});
```

---

# 📌 Promise Polyfill Basic Idea

Promise ke andar mainly 3 cheeze hoti hain:

* state
* resolve
* reject
* then()

---

# 📌 Basic Promise Polyfill

```js id="opvhcu"
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

```js id="aj5m8e"
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

# 📌 Output

```js id="4v6hm5"
Promise Resolved
```

---

# 📌 How It Works

## Step 1

Executor function call hota hai.

```js id="vv6t4o"
new MyPromise((resolve) => {})
```

---

## Step 2

`resolve()` value store karta hai.

---

## Step 3

`.then()` callback ko execute karta hai.

---

# 📌 Important Concepts Used

| Concept        | Purpose                     |
| -------------- | --------------------------- |
| Closure        | Value store karne ke liye   |
| Callback       | then() handle karne ke liye |
| Async          | setTimeout simulation       |
| State handling | resolved/rejected           |

---

# 📌 Limitations of This Simple Polyfill

Ye full Promise implementation nahi hai.

Missing features:

* catch()
* finally()
* chaining
* reject()
* Promise.all()
* Promise.race()

---

# 📌 Interview Important Point

Real Promise internally:

* microtask queue use karta hai
* async handling karta hai
* state maintain karta hai

States:

```js id="7y5qgr"
pending
fulfilled
rejected
```

---

# 📌 Better Polyfill with Reject

```js id="im0frs"
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

# 📌 Usage

```js id="q9q53q"
const p = new MyPromise((resolve, reject) => {
  reject("Error");
});

p.catch((err) => {
  console.log(err);
});
```

---

# 📌 Interview Definition

> Promise Polyfill is a custom implementation of JavaScript Promise used to mimic Promise behavior in environments where native Promise support is unavailable.

---

# 📌 Interview Important Points 🔥

| Topic           | Important                        |
| --------------- | -------------------------------- |
| Polyfill        | Feature support for old browsers |
| Promise States  | pending, fulfilled, rejected     |
| Main Methods    | then, catch                      |
| Uses            | Async handling                   |
| Internally Uses | callbacks + closures             |

---

# 📌 Very Short Interview Answer

> Promise Polyfill is a custom implementation of Promise that provides Promise-like functionality in browsers that do not support native Promises. It handles async operations using resolve, reject, and then/catch methods.


# Common JavaScript Polyfills 🔥

Polyfill kisi bhi modern JavaScript feature ka custom implementation hota hai.

Interview me mostly ye polyfills puche jate hain 👇

---

# 📌 Function Polyfills

| Polyfill   | Use                                    |
| ---------- | -------------------------------------- |
| bind()     | Function ka `this` bind karta hai      |
| call()     | Function ko immediately call karta hai |
| apply()    | call jaisa but array arguments         |
| debounce() | Repeated calls control                 |
| throttle() | Limited interval me execute            |

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

# 📌 Important Browser Polyfills

| Polyfill              | Use             |
| --------------------- | --------------- |
| fetch()               | API calls       |
| localStorage          | Storage         |
| requestAnimationFrame | Animation       |
| setImmediate          | Async execution |

---

# 📌 Most Important Interview Polyfills 🔥

Ye sabse jyada puche jate hain:

```js id="jybv9t"
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

# 📌 Example → map Polyfill

```js id="r5r9pr"
Array.prototype.myMap = function(cb) {
  let result = [];

  for (let i = 0; i < this.length; i++) {
    result.push(cb(this[i], i, this));
  }

  return result;
};
```

---

# 📌 Example → bind Polyfill

```js id="h4s7ta"
Function.prototype.myBind = function(context, ...args) {
  let fn = this;

  return function(...newArgs) {
    return fn.apply(context, [...args, ...newArgs]);
  };
};
```

---

# 📌 Example → reduce Polyfill

```js id="13j4jf"
Array.prototype.myReduce = function(cb, initialValue) {
  let acc = initialValue;

  for (let i = 0; i < this.length; i++) {
    acc = acc ? cb(acc, this[i]) : this[i];
  }

  return acc;
};
```

---

# 📌 Interview Important Line

> Polyfills are custom implementations of modern JavaScript features used to provide support in older browsers.

---

# 📌 Interview Tip 🔥

Agar interviewer bole:

```js id="7kp6ul"
Implement map polyfill
```

To mostly wo check karta hai:

* Prototype knowledge
* Callback understanding
* this keyword
* Loop logic
* Closures

---

# 📌 Most Asked Polyfill Order in Interviews

1. bind()
2. debounce()
3. throttle()
4. map()
5. reduce()
6. Promise
7. call/apply
8. filter()

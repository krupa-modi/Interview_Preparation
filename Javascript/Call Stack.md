
## 📌 What is Call Stack?

👉 **Call Stack** is a data structure used by JavaScript to keep track of function execution.

It follows **LIFO (Last In, First Out)**:

* Last function added → executed first

---

## 🧠 Simple Definition

👉 *Call Stack is where JavaScript manages function calls — adding (push) and removing (pop) them during execution.*

---

## ⚙️ How It Works

1. Global Execution Context is pushed first
2. When a function is called → pushed to stack
3. When function finishes → popped from stack

---

## 📊 Flow Chart

```text
Start
  ↓
[ Global Execution Context ]
  ↓
Call function A()
  ↓
[ A() ]
  ↓
Call function B()
  ↓
[ B() ]
  ↓
B() finishes → POP
  ↓
A() finishes → POP
  ↓
Global finishes → POP
```

---

## 💻 Example

```javascript
function one() {
    console.log("One");
    two();
}

function two() {
    console.log("Two");
    three();
}

function three() {
    console.log("Three");
}

one();
```

---

## 🔍 Step-by-Step Execution

### Initial Stack

```text
[ Global ]
```

### Call `one()`

```text
[ one() ]
[ Global ]
```

### Call `two()`

```text
[ two() ]
[ one() ]
[ Global ]
```

### Call `three()`

```text
[ three() ]
[ two() ]
[ one() ]
[ Global ]
```

### Now popping (execution completes)

```text
[ two() ]
[ one() ]
[ Global ]

[ one() ]
[ Global ]

[ Global ]
```

---

## ⚠️ Stack Overflow

If too many function calls happen without finishing:

```javascript
function test() {
    test();
}
test();
```

👉 Result:

```
RangeError: Maximum call stack size exceeded ❌
```

---

## ⚡ Key Points (Interview Quick Notes)

* Uses **LIFO**
* Manages **Execution Context**
* Functions are **pushed & popped**
* Helps in tracking program flow
* Too many calls → **Stack Overflow**

---

## 🧾 One-Line Definition

👉 *Call Stack is a structure that keeps track of function calls in JavaScript using LIFO order.*

---

If you want next → I can explain **Event Loop + Callback Queue + Microtask Queue** (very important combo for interviews) 🔥

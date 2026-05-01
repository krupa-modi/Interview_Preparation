
## 📌 What is Execution Context?

**Execution Context** is the environment in which JavaScript code is executed.

It decides:

* Which variables are accessible
* What the value of `this` is
* How functions are executed

👉 JavaScript runs code inside **Execution Contexts**.

---

## ⚙️ Types of Execution Context

1. **Global Execution Context (GEC)**

   * Created when JS file runs
   * Only one exists
   * `this = window` (in browser)

2. **Function Execution Context (FEC)**

   * Created whenever a function is called
   * Each function gets its own context

3. **Eval Execution Context** (rarely used)

---

## 🔄 Phases of Execution Context

Each context has **2 phases**:

### 1. Memory Creation Phase (Creation Phase)

* Variables → `undefined`
* Functions → full definition stored

### 2. Code Execution Phase

* Code runs line by line
* Values get assigned

---

## 📊 Flow Chart (Execution Context Working)

```
Global Execution Context (GEC)
        |
        ↓
Memory Phase:
  a → undefined
  b → undefined
  sum → function()

        ↓
Execution Phase:
  a = 10
  b = 20
  sum() called
        |
        ↓
Function Execution Context (FEC)
        |
Memory Phase:
  x → undefined
  y → undefined

        ↓
Execution Phase:
  x = 10
  y = 20
  return 30
```

---

## 💻 Example

```javascript
var a = 10;
var b = 20;

function sum(x, y) {
    var result = x + y;
    return result;
}

var output = sum(a, b);
console.log(output);
```

---

## 🔍 Step-by-Step Execution

### 🧩 Global Execution Context Created

#### Memory Phase:

```
a → undefined
b → undefined
sum → function definition
output → undefined
```

#### Execution Phase:

```
a = 10
b = 20
output = sum(10, 20)
```

---

### 🧩 Function Execution Context (sum)

#### Memory Phase:

```
x → undefined
y → undefined
result → undefined
```

#### Execution Phase:

```
x = 10
y = 20
result = 30
return 30
```

---

## 🧠 Call Stack (Important for Interview)

```
|-------------------|
|   sum()           |  ← pushed
|-------------------|
|   Global Context  |
|-------------------|

(after execution)

|-------------------|
|   Global Context  |
|-------------------|
```

👉 Functions go **in and out** of the call stack.

---

## ⚡ Key Points (Interview Quick Notes)

* JS is **single-threaded**
* Runs inside **Execution Context**
* Has **2 phases** → Memory + Execution
* Functions create **new execution contexts**
* Managed using **Call Stack**

---

## 🧾 One-Line Definition

👉 *Execution Context is the environment where JavaScript code is evaluated and executed.*

---

If you want, I can also give **interview tricky questions on Execution Context + Hoisting + Call Stack** — those are very commonly asked 🔥


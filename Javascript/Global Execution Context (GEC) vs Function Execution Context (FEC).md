## 📌 1. Global Execution Context (GEC) vs Function Execution Context (FEC)

### 🌍 Global Execution Context (GEC)

👉 Created **once** when the JavaScript file starts running.

**Key points:**

* Only **one GEC**
* `this` → points to **global object** (`window` in browser, `global` in Node)
* All global variables & functions live here

---

### 🔧 Function Execution Context (FEC)

👉 Created **every time a function is invoked**

**Key points:**

* Multiple FECs can exist
* Each function call gets its **own separate environment**
* Deleted after execution

---

## 📊 GEC vs FEC Comparison

| Feature  | Global Execution Context 🌍 | Function Execution Context 🔧  |
| -------- | --------------------------- | ------------------------------ |
| Created  | Once                        | Every function call            |
| Count    | Only one                    | Many possible                  |
| Lifetime | Till program ends           | Till function finishes         |
| Scope    | Global                      | Local (function scope)         |
| `this`   | Global object               | Depends on how function called |

---

## 📌 2. Phases of Execution Context

Each execution context (GEC & FEC) runs in **2 phases**:

---

## 🧩 Phase 1: Memory Creation Phase (Creation Phase)

👉 JavaScript scans code before execution.

**What happens:**
* allocate memory to variable.
* store function defination.
* variable are initialize with undefined
* Functions → stored completely in memory

---

## ⚡ Phase 2: Code Execution Phase

👉 Code runs line by line.

**What happens:**
* javascript excute code line by line and assign real value.
* Values assigned to variables
* Functions executed
* New execution contexts created

---

## 🔥 Important Concept: Hoisting

👉 Happens in **Memory Phase**

* Variables hoisted → `undefined`
* Functions hoisted → full definition

---

## 💻 Detailed Example

```javascript
var a = 10;
var b = 20;

function add(x, y) {
    var result = x + y;
    return result;
}

var total = add(a, b);
```

---

## 🔍 Step-by-Step Breakdown

---

### 🟢 Step 1: Global Execution Context Created

---

### 🧠 Memory Phase (GEC)

```text
a → undefined
b → undefined
add → function definition
total → undefined
```

---

### ⚡ Execution Phase (GEC)

```text
a = 10
b = 20
total = add(10, 20)  → function call
```

👉 Now a **new Function Execution Context (FEC)** is created

---

### 🔧 Step 2: Function Execution Context (add)

---

### 🧠 Memory Phase (FEC)

```text
x → undefined
y → undefined
result → undefined
```

---

### ⚡ Execution Phase (FEC)

```text
x = 10
y = 20
result = 30
return 30
```

👉 Value goes back to GEC → `total = 30`

---

## 📊 Execution Flow Diagram

```text
Global Execution Context (GEC)
        |
        ↓
Memory Phase:
  a → undefined
  b → undefined
  add → function
  total → undefined

        ↓
Execution Phase:
  a = 10
  b = 20
  call add()

        ↓
Function Execution Context (FEC)
        |
Memory Phase:
  x → undefined
  y → undefined
  result → undefined

        ↓
Execution Phase:
  x = 10
  y = 20
  result = 30
  return 30
```

---

## 📦 Call Stack Relation

```text
|-------------------|
|   add()           |  ← pushed
|-------------------|
|   Global Context  |
|-------------------|

(after execution)

|-------------------|
|   Global Context  |
|-------------------|
```

---

## ⚡ Key Interview Points

* JS creates **GEC first**
* Every function call → **new FEC**
* Each context has **2 phases**
* Memory Phase = **Hoisting happens**
* Execution Phase = **Actual code runs**
* Managed by **Call Stack**

---

## 🧾 Final One-Line Summary

👉 *Global Execution Context runs the whole program, while Function Execution Context runs individual functions — both go through Memory and Execution phases.*

---


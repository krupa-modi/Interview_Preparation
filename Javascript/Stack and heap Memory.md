# 📘 Stack and Heap Memory in JavaScript – Interview Notes

---

# 🔹 What is Memory in JavaScript?

JavaScript stores data in memory while program runs.

Mainly memory is divided into:

```text id="3y1jcf"
1. Stack Memory (ismain copy hota hai primitive value ka so original value change nae hoti)
2. Heap Memory (ismain referbce pass hota hai nonprimitive main so original value bhi change ho jati hai)
```

---

# 1️⃣ Stack Memory

# 🔹 Definition

Stack memory stores:

* Primitive values
* Function calls
* Execution context

---

# 📌 Primitive Data Types Stored in Stack

```js id="93m9gz"
String
Number
Boolean
null
undefined
BigInt
Symbol
```

---

# ✅ Example

```js id="cyrb8g"
let name = "John";
let age = 25;
```

These values are stored directly in stack memory.

---

# 🔥 Characteristics of Stack Memory

| Feature           | Stack Memory             |
| ----------------- | ------------------------ |
| Stores            | Primitive values         |
| Speed             | Fast                     |
| Size              | Small                    |
| Access            | Direct                   |
| Memory Management | Automatic                |
| Order             | LIFO (Last In First Out) |

---

# 📌 What is LIFO?

```text id="pjjlwm"
Last In First Out
```

Last added item removes first.

Like:

```text id="jlwm0x"
Plate Stack
```

---

# 🔥 Function Calls in Stack

Every function call creates a:

```text id="jlwmm7"
Call Stack Frame
```

---

# ✅ Example

```js id="jlwm1t"
function one() {
  two();
}

function two() {
  console.log("Hello");
}

one();
```

---

# 📌 Call Stack Flow

```text id="jlwm2u"
Global Execution
   ↓
one()
   ↓
two()
```

After execution:

```text id="jlwm0y"
two() removed
one() removed
```

---

# ⚠️ Stack Overflow

Too many function calls cause:

```text id="jlwmkp"
Maximum call stack size exceeded
```

---

# ✅ Example

```js id="jlwmg9"
function test() {
  test();
}

test();
```

Infinite recursion → stack overflow.

---

# 2️⃣ Heap Memory

# 🔹 Definition

Heap memory stores:

* Objects
* Arrays
* Functions

---

# ✅ Example

```js id="jjlwmf"
const user = {
  name: "John"
};
```

Object stored in heap memory.

---

# 🔥 Important Point

In stack:

```js id="jlwm47"
user
```

stores reference/address of object.

Actual object lives in heap.

---

# 📌 Visualization

```text id="jlwmm4"
STACK                 HEAP

user  ----------->   { name: "John" }
```

---

# 🔥 Characteristics of Heap Memory

| Feature           | Heap Memory       |
| ----------------- | ----------------- |
| Stores            | Objects & arrays  |
| Speed             | Slower            |
| Size              | Large             |
| Access            | By reference      |
| Memory Management | Garbage Collector |

---

# 🔥 Objects Are Stored by Reference

## ✅ Example

```js id="jlwm3f"
const obj1 = {
  name: "John"
};

const obj2 = obj1;
```

---

# 📌 Memory Diagram

```text id="jlwm2d"
STACK                  HEAP

obj1  -----------\
                   ----> { name: "John" }
obj2  -----------/
```

Both point to same object.

---

# 🔥 Changing One Object

```js id="0jlwmz"
obj2.name = "Peter";

console.log(obj1.name);
```

Output:

```js id="jlwm81"
Peter
```

Because both share same heap object.

---

# 🔥 Primitive vs Reference Copy

---

# ✅ Primitive Copy

```js id="jlwm8r"
let a = 10;
let b = a;

b = 20;

console.log(a);
```

Output:

```js id="jlwm2q"
10
```

Independent copies.

---

# ✅ Reference Copy

```js id="hjlwm2"
const obj1 = {
  city: "Delhi"
};

const obj2 = obj1;

obj2.city = "Mumbai";

console.log(obj1.city);
```

Output:

```js id="9jlwm8"
Mumbai
```

Shared reference.

---

# 🔥 Stack vs Heap Memory

| Feature        | Stack            | Heap              |
| -------------- | ---------------- | ----------------- |
| Stores         | Primitive values | Objects & arrays  |
| Access Speed   | Faster           | Slower            |
| Allocation     | Static           | Dynamic           |
| Size           | Smaller          | Larger            |
| Access Type    | Direct value     | Reference         |
| Memory Cleanup | Automatic        | Garbage Collector |

---

# 🔥 Real Interview Example

```js id="9jlwmn"
let name = "John";

let user = {
  city: "Delhi"
};
```

---

# 📌 Memory Storage

```text id="jlwmb5"
STACK:
name → "John"
user → memory reference

HEAP:
{ city: "Delhi" }
```

---

# 🔥 Important Interview Points

---

# ✅ Primitive Types

Stored directly in stack.

---

# ✅ Reference Types

Stored in heap, reference in stack.

---

# ✅ Why Heap is Slower?

Because objects are dynamically allocated.

---

# ✅ Why Stack is Faster?

Because memory allocation is sequential.

---

# 🎯 Most Asked Interview Questions

---

# ✅ Q1. What is stack memory?

Stores primitive values and function execution contexts.

---

# ✅ Q2. What is heap memory?

Stores objects, arrays, and functions dynamically.

---

# ✅ Q3. Why objects are copied by reference?

Because actual objects are stored in heap memory.

---

# ✅ Q4. Difference between stack and heap?

Stack stores primitive values directly, while heap stores reference types dynamically.

---

# ✅ Q5. What causes stack overflow?

Too many nested/infinite function calls.

---

# 🎯 Final Interview Summary

| Topic              | Meaning                                  |
| ------------------ | ---------------------------------------- |
| Stack Memory       | Stores primitive values & function calls |
| Heap Memory        | Stores objects & arrays                  |
| Primitive Copy     | By value                                 |
| Object Copy        | By reference                             |
| Stack Overflow     | Too many function calls                  |
| Garbage Collection | Cleans heap memory                       |

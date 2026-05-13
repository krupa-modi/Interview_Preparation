--

# 📘 2. Garbage Collection in JavaScript – Interview Notes

---

# 🔹 What is Garbage Collection?

Garbage Collection (GC) is an automatic memory management process in JavaScript.

It removes unused memory automatically.

---

# 📌 Simple Definition

```text id="qzbfx4"
Garbage Collector frees memory occupied by unreachable objects.
```

---

# 🔥 Why Needed?

Without GC:

* Developers would manually free memory
* Memory management becomes difficult
* Applications crash more often

---

# 🔹 How JavaScript Stores Memory

## Stack Memory

Stores:

* Primitive values
* Function calls

Example:

```js id="zjlwmj"
let a = 10;
```

---

## Heap Memory

Stores:

* Objects
* Arrays
* Functions

Example:

```js id="qjlwm4"
const user = {
  name: "John"
};
```

---

# 🔥 What is Reachability?

GC checks whether object is reachable or not.

If unreachable → remove from memory.

---

# ✅ Reachable Example

```js id="9g0f5r"
let user = {
  name: "John"
};
```

`user` is reachable.

---

# ❌ Unreachable Example

```js id="9jlwm0"
let user = {
  name: "John"
};

user = null;
```

Old object becomes unreachable.

GC removes it.

---

# 🔥 Mark and Sweep Algorithm

JavaScript mainly uses:

```text id="h3jlwm"
Mark and Sweep
```

---

# 📌 Steps

## 1️⃣ Mark

GC marks reachable objects.

---

## 2️⃣ Sweep

Unreachable objects are deleted.

---

# 🔥 Example

```js id="wr9t6k"
let obj1 = {
  name: "A"
};

let obj2 = obj1;

obj1 = null;
obj2 = null;
```

Now object has no references.

GC removes it.

---

# 🔥 Circular Reference

Older languages had issues:

```js id="jlwmu7"
obj1.ref = obj2;
obj2.ref = obj1;
```

Modern JS GC handles this properly.

---

# 🔥 Manual Garbage Collection?

JavaScript does NOT allow direct manual memory freeing.

GC runs automatically.

---

# 🔥 How to Help Garbage Collector

## ✅ Best Practices

* Remove unused references
* Clear intervals
* Remove listeners
* Avoid global variables

---

# 🔥 WeakMap and WeakSet

Weak references allow GC to clean objects.

---

# ✅ Example

```js id="jlwmh1"
let weakMap = new WeakMap();
```

Used for memory-efficient storage.

---

# 🎯 Interview Questions

---

# ✅ Q1. What is garbage collection?

Automatic removal of unused memory.

---

# ✅ Q2. Which algorithm does JavaScript use?

Mark and Sweep.

---

# ✅ Q3. What are unreachable objects?

Objects with no references.

---

# ✅ Q4. Difference between stack and heap memory?

| Stack          | Heap             |
| -------------- | ---------------- |
| Primitive data | Objects & arrays |
| Fast           | Larger memory    |

---

# 🎯 Interview Line

```text id="jlwm7y"
JavaScript uses automatic garbage collection to remove unreachable objects from memory.
```



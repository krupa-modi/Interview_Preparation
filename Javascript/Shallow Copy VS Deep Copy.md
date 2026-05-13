# 📘 3. Shallow Copy vs Deep Copy – Interview Notes

---

# 🔹 What is Copying?

Copying means creating another variable/object from existing data.

---

# 🔥 Primitive Copy

Primitive values copy by value.

```js id="jlwm0p"
let a = 10;
let b = a;
```

Independent copies.

---

# 🔥 Object Copy

Objects copy by reference.

```js id="i6bt3z"
const obj1 = { name: "John" };

const obj2 = obj1;
```

Both point to same memory.

---

# 1️⃣ Shallow Copy

# 🔹 Definition

Creates copy of only first level properties.

Nested objects still share reference.

---

# ✅ Example

```js id="qjlwmv"
const user1 = {
  name: "John",
  address: {
    city: "Delhi"
  }
};

const user2 = { ...user1 };

user2.name = "Peter";

console.log(user1.name);
```

Output:

```js id="jlwm18"
John
```

Independent primitive property.

---

# ❌ Nested Problem

```js id="jlwmj6"
user2.address.city = "Mumbai";

console.log(user1.address.city);
```

Output:

```js id="lcy4zq"
Mumbai
```

Because nested object reference is shared.

---

# 🔥 Ways to Create Shallow Copy

---

# ✅ Object.assign()

```js id="jlwm18"
const copy = Object.assign({}, obj);
```

---

# ✅ Spread Operator

```js id="f3jlwm"
const copy = { ...obj };
```

---

# ✅ Array Shallow Copy

```js id="jlwm0x"
const arr2 = [...arr1];
```

---

# 📌 Use Cases

* Flat objects
* Simple state updates

---

# 2️⃣ Deep Copy

# 🔹 Definition

Creates completely independent copy including nested objects.

---

# ✅ Example

```js id="jlwm77"
const user1 = {
  name: "John",
  address: {
    city: "Delhi"
  }
};

const user2 = structuredClone(user1);

user2.address.city = "Mumbai";

console.log(user1.address.city);
```

---

# ✅ Output

```js id="hsvjlwm"
Delhi
```

Completely independent.

---

# 🔥 Ways to Create Deep Copy

---

# ✅ structuredClone()

Modern and best approach.

```js id="jlwmn5"
const copy = structuredClone(obj);
```

---

# ✅ JSON Method

```js id="4jlwmf"
const copy =
JSON.parse(JSON.stringify(obj));
```

---

# ⚠️ Limitation of JSON Method

Cannot copy:

* Functions
* undefined
* Dates properly
* Map/Set

---

# 🔥 Shallow Copy vs Deep Copy

| Feature        | Shallow Copy     | Deep Copy        |
| -------------- | ---------------- | ---------------- |
| Nested Objects | Shared           | Independent      |
| Memory Usage   | Less             | More             |
| Performance    | Faster           | Slower           |
| Copy Level     | First level only | Full nested copy |

---

# 🔥 Real Interview Example

```js id="jlwm7t"
const obj1 = {
  user: {
    name: "John"
  }
};

const obj2 = { ...obj1 };

obj2.user.name = "Peter";

console.log(obj1.user.name);
```

Output:

```js id="njlwmr"
Peter
```

Because spread operator creates shallow copy.

---

# 🎯 Important Interview Point

```text id="yjlwmf"
Spread operator creates only shallow copy, not deep copy.
```

---

# 🎯 Most Asked Interview Questions

---

# ✅ Q1. Difference between shallow and deep copy?

Shallow copy shares nested references, deep copy creates fully independent copies.

---

# ✅ Q2. Is spread operator deep copy?

❌ No, only shallow copy.

---

# ✅ Q3. Best way for deep copy?

```js id="jlwm4e"
structuredClone()
```

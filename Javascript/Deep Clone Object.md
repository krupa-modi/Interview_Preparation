# Deep Clone Object in JavaScript

# 📌 What is Deep Clone?

Deep clone ka matlab hota hai:

> Object ki completely independent copy banana including nested objects and arrays.

Agar original object change ho:

✅ copied object affect nahi hona chahiye.

---

# 📌 Why Deep Clone Needed?

JavaScript me objects reference type hote hain.

```js id="1r6j7f"
const obj1 = {
  name: "Krupa"
};

const obj2 = obj1;
```

---

## ❌ Problem

```js id="sxk3x0"
obj2.name = "Modi";

console.log(obj1.name);
```

### Output

```js id="k4y4gh"
Modi
```

Kyuki dono same reference point kar rahe hain.

---

# 📌 Shallow Copy vs Deep Copy

| Shallow Copy         | Deep Copy                 |
| -------------------- | ------------------------- |
| Top-level copy       | Full nested copy          |
| Nested object shared | Nested object independent |
| Faster               | Slightly slower           |

---

# 📌 Shallow Copy Example

```js id="db2gqf"
const obj1 = {
  name: "Krupa",
  address: {
    city: "Pune"
  }
};

const obj2 = { ...obj1 };

obj2.address.city = "Mumbai";

console.log(obj1.address.city);
```

---

# ❌ Output

```js id="9m4qxh"
Mumbai
```

Nested object shared tha.

---

# 📌 Deep Clone Example

```js id="4kj0p6"
const obj1 = {
  name: "Krupa",
  address: {
    city: "Pune"
  }
};

const obj2 = structuredClone(obj1);

obj2.address.city = "Mumbai";

console.log(obj1.address.city);
```

---

# ✅ Output

```js id="8vh4cl"
Pune
```

Now both objects independent hain.

---

# 📌 Methods to Deep Clone

## ✅ 1. structuredClone() (Modern Best Way)

```js id="stcz6p"
const clone = structuredClone(obj);
```

### Advantages

* Fast
* Modern
* Nested objects handle karta hai
* Arrays handle karta hai

---

# 📌 Example

```js id="u5bwml"
const user = {
  name: "Krupa",
  skills: ["React", "JS"]
};

const copy = structuredClone(user);

copy.skills.push("Node");

console.log(user.skills);
```

---

# ✅ Output

```js id="wzvvkj"
["React", "JS"]
```

---

# 📌 2. JSON Method

```js id="l0lbpr"
const clone = JSON.parse(JSON.stringify(obj));
```

---

# ✅ Example

```js id="7zb7zn"
const obj = {
  name: "Krupa",
  age: 25
};

const copy = JSON.parse(JSON.stringify(obj));
```

---

# ❌ Limitations of JSON Method

Ye handle nahi karta:

* functions
* undefined
* Date
* Map
* Set
* circular reference

---

# 📌 Example Problem

```js id="b1y1v1"
const obj = {
  date: new Date()
};

const copy = JSON.parse(JSON.stringify(obj));

console.log(copy.date);
```

---

# ❌ Output

```js id="mk6v7n"
String ban jayega
```

---

# 📌 3. Recursive Deep Clone (Interview Important 🔥)

## Custom Deep Clone Function

```js id="hn9c95"
function deepClone(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj;
  }

  let copy = Array.isArray(obj) ? [] : {};

  for (let key in obj) {
    copy[key] = deepClone(obj[key]);
  }

  return copy;
}
```

---

# 📌 Usage

```js id="e4nmzi"
const user = {
  name: "Krupa",
  address: {
    city: "Pune"
  }
};

const copy = deepClone(user);

copy.address.city = "Mumbai";

console.log(user.address.city);
```

---

# ✅ Output

```js id="y5wjlwm"
Pune
```

---

# 📌 How Recursive Deep Clone Works

## Step 1

Check karta hai:

```js id="0l1myn"
Primitive hai ya object
```

---

## Step 2

Agar object hai:

```js id="w8l8rn"
New object/array create karo
```

---

## Step 3

Har property recursively copy karo.

---

# 📌 Important Interview Concepts

| Concept             | Important                          |
| ------------------- | ---------------------------------- |
| Reference Type      | Objects reference share karte hain |
| Recursion           | Nested cloning                     |
| Array.isArray       | Array check                        |
| Primitive vs Object | Base condition                     |

---

# 📌 Circular Reference Problem

```js id="2bvxv4"
const obj = {};
obj.self = obj;
```

Recursive function infinite loop me chala jayega.

---

# 📌 Advanced Solution

Real libraries:

* lodash.cloneDeep()

WeakMap use karti hain circular reference avoid karne ke liye.

---

# 📌 Lodash Example

```js id="85b1be"
import cloneDeep from "lodash/cloneDeep";

const copy = cloneDeep(obj);
```

---

# 📌 Best Interview Answer

> Deep cloning means creating a completely independent copy of an object including all nested objects and arrays. Unlike shallow copy, changes in the cloned object do not affect the original object. In JavaScript, deep cloning can be done using structuredClone(), JSON methods, recursion, or libraries like lodash.cloneDeep().

---

# 📌 Interview Important Points 🔥

| Topic              | Important               |
| ------------------ | ----------------------- |
| Deep Clone         | Full independent copy   |
| Shallow Copy       | Nested reference shared |
| Best Modern Way    | structuredClone()       |
| Interview Favorite | Recursive deep clone    |
| Common Problem     | Circular references     |

---

# 📌 Short Interview Answer

> Deep clone creates a completely separate copy of an object including nested objects. Any changes made in the copied object do not affect the original object. Common methods are structuredClone(), JSON.parse(JSON.stringify()), and recursive cloning.

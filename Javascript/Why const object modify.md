# ✅ Why `const` Object Modify Ho Sakta Hai?

# 🔥 Interview Question

```js
const user = {
  name: "Aman"
};

user.name = "Rahul";

console.log(user.name);
````

## ✅ Output

```js id="r8kp3m"
Rahul
```

---

# 🤔 But `const` to change nahi hota na?

Haan ✅
Lekin yaha ek important concept hai:

```js id="r7q2vf"
const variable ko reassign nahi kar sakte
```

Object ko modify kar sakte ho.

---

# 🎯 Simple Definition

> `const` object ka reference fix karta hai,
> object ki values nahi.
> ham object ko change nahi kar rahe uski properties ko modify kar rahe hai so possible hai.

---

# 🔍 Easy Explanation

## `const` kya lock karta hai?

```js id="d7j0ws"
memory address / reference
```

Example:

```js id="gtp0lb"
const user = {
  name: "Aman"
};
```

`user` variable ek object ka reference hold karta hai.

---

# ✅ Allowed (Modify Property)

```js id="hn9t4v"
user.name = "Rahul";
```

Kyuki:

* object same hai
* sirf property change hui

---

# ❌ Not Allowed (Reassign Object)

```js id="4gbq24"
user = {
  name: "Neha"
};
```

## ❌ Error

```js id="w2clxy"
TypeError: Assignment to constant variable
```

Kyuki:

* ab pura naya object assign ho raha hai
* reference change ho raha hai

---

# 🚀 Memory Example

## Initial

```js id="t6fd4s"
user ---> { name: "Aman" }
```

---

## After Modify

```js id="pz1xbx"
user ---> { name: "Rahul" }
```

Reference same hai ✅

---

## After Reassign

```js id="m0kjlwm"
user ---> new object
```

Reference change ho gaya ❌

---

# ⚡ Array Example

```js id="olbovw"
const arr = [1, 2];

arr.push(3);

console.log(arr);
```

## ✅ Output

```js id="kzn8ul"
[1, 2, 3]
```

Because array bhi object hi hota hai.

---

# ❌ But This is Not Allowed

```js id="f4o5db"
const arr = [1, 2];

arr = [10, 20];
```

## ❌ Error

```js id="d8k7th"
Assignment to constant variable
```

---

# 🎯 Interview Definition

> `const` object ko immutable nahi banata.
> Ye sirf variable reference ko fixed karta hai.

---

# 🔥 Important Interview Point

## `const` ≠ immutable object

Agar object fully immutable banana ho:

```js id="w6hy40"
Object.freeze(obj)
```

---

# ✅ Example

```js id="9g36hu"
const user = Object.freeze({
  name: "Aman"
});

user.name = "Rahul";

console.log(user.name);
```

## ✅ Output

```js id="xyckhf"
Aman
```

Modification nahi hua.

---

# 🚀 Quick Revision

| Concept         | Meaning                 |
| --------------- | ----------------------- |
| const           | Reference fix karta hai |
| Object Modify   | Allowed                 |
| Reassign Object | Not Allowed             |
| Fully Immutable | Object.freeze()         |

---

# 💡 One-Line Memory Trick

```js id="uh58s4"
const object change ho sakta hai,
lekin object ka reference nahi.
```

```


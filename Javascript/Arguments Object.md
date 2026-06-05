# ✅ arguments Object in JavaScript (Interview Notes)

# ✅ What is `arguments` Object?

`arguments` is a special object available inside normal functions.

It contains all arguments passed to the function.

---
# 🎯 Interview Definition

> The `arguments` object stores all arguments passed to a function, even if parameters are not defined.

---

# ✅ Example

```js
function test() {

  console.log(arguments);

}

test(10, 20, 30);
````

## ✅ Output

```js id="p4m8tw"
{
  0: 10,
  1: 20,
  2: 30
}
```

---

# 🔍 Access Arguments

```js id="v7q1la"
function test() {

  console.log(arguments[0]);
  console.log(arguments[1]);

}

test(10, 20);
```

## ✅ Output

```js id="k5r2vt"
10
20
```

---

# ✅ Example: Sum All Arguments

```js id="x2m9pw"
function sum() {

  let total = 0;

  for(let i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }

  return total;
}

console.log(sum(1, 2, 3, 4));
```

## ✅ Output

```js id="f8x2lm"
10
```

---

# ⚠️ Important Points

| Point                         | Explanation |
| ----------------------------- | ----------- |
| Available in normal functions | ✅ Yes       |
| Available in arrow functions  | ❌ No        |
| Array?                        | ❌ No        |
| Array-like object             | ✅ Yes       |

---

# ❌ arguments in Arrow Function

```js id="r4p7qa"
const test = () => {
  console.log(arguments);
};

test(1, 2);
```

## ❌ Error

Because arrow functions do not have their own `arguments` object.

---

# ✅ Modern Alternative → Rest Parameter

```js id="z6m1tw"
function sum(...nums) {
  console.log(nums);
}

sum(1, 2, 3);
```

## ✅ Output

```js id="c2q8vp"
[1, 2, 3]
```

---

# 🎯 Interview Difference

| arguments              | Rest Parameter           |
| ---------------------- | ------------------------ |
| Array-like object      | Real array               |
| Old method             | Modern method            |
| Not in arrow functions | Works in arrow functions |

---

# 🚀 Quick Revision

| Concept            | Meaning                   |
| ------------------ | ------------------------- |
| arguments          | Stores function arguments |
| Type               | Array-like object         |
| Available In       | Normal functions          |
| Modern Alternative | Rest parameter            |

---

# 💡 One-Line Memory Trick

```js id="j7p3lx"
arguments stores all passed values inside a normal function.
```

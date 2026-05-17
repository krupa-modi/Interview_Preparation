# ✅ for...in vs for...of Loop in JavaScript

# 🔥 1. for...in Loop

`for...in` loop object keys iterate karta hai.

---

# ✅ Object Example

```js id="s7k2vt"
const user = {
  name: "Aman",
  age: 25
};

for (let key in user) {
  console.log(key);
}
````

## ✅ Output

```js id="n2v8ym"
name
age
```

---

# 🔍 Value Access

```js id="c5p1la"
const user = {
  name: "Aman",
  age: 25
};

for (let key in user) {
  console.log(user[key]);
}
```

## ✅ Output

```js id="d8q3wr"
Aman
25
```



# 🎯 Important Point

```js id="z6f0mt"
for...in → keys/indexes deta hai
```

```
const user = {
  name:"hello",
  age:20
}

for(let key in user){
   console.log(key) // name,age
  console.log(user[key]) // hello,20
}   

```

---

# ✅ Array Example

```js id="j3l8dx"
const arr = [10, 20, 30];

for (let index in arr) {
  console.log(index);
}
```

## ✅ Output

```js id="l4x9pw"
0
1
2
```

👉 Ye indexes deta hai.

```js id="j3l8dx"
const arr = [10,20, , 30]

for(let key in arr){
  console.log(key) // 0,1,3
} 
```

---

# 🔥 2. for...of Loop

`for...of` values iterate karta hai.

---

# ✅ Array Example

```js id="y8q1st"
const arr = [10, 20, 30];

for (let value of arr) {
  console.log(value);
}
```

## ✅ Output

```js id="q2n7vl"
10
20
30
```

---

# 🎯 Important Point

```js id="u7m5hc"
for...of → values deta hai
```

---

# ✅ String Example

```js id="f6t3rx"
const str = "JS";

for (let char of str) {
  console.log(char);
}
```

## ✅ Output

```js id="h1v0ka"
J
S
```

---

# ⚠️ Important Difference

## for...in

Mostly objects ke liye use hota hai.

---

## for...of

Arrays, strings, maps, sets ke liye use hota hai.

---

# ❌ Object with for...of

```js id="w7r8pl"
const user = {
  name: "Aman"
};

for (let val of user) {
  console.log(val);
}
```

## ❌ Error

```js id="m0n6qt"
user is not iterable
```

Because normal object iterable nahi hota.

```js id="w7r8pl"
const arr = [10,20, , 30]
for(let key of arr){
  console.log(key) // 10,20,undefined,30
}
```

---

# 🚀 Main Difference Table

| for...in               | for...of                |
| ---------------------- | ----------------------- |
| Keys/indexes deta hai  | Values deta hai         |
| Mostly objects         | Arrays & iterables      |
| Object pe kaam karta   | Object pe directly nahi |
| Returns property names | Returns values          |

---

# 🔥 Quick Example Together

```js id="k5j9wp"
const arr = ["A", "B", "C"];

for (let i in arr) {
  console.log(i);
}

for (let val of arr) {
  console.log(val);
}
```

---

# ✅ Output

## for...in

```js id="g9x1dl"
0
1
2
```

## for...of

```js id="b4m7ra"
A
B
C
```

---

# 🎯 Interview Definition

## for...in

> Used to iterate object keys or array indexes.

---

## for...of

> Used to iterate values of iterable objects.

---

# ⚡ When to Use?

| Situation         | Best Loop |
| ----------------- | --------- |
| Object keys       | for...in  |
| Array values      | for...of  |
| String characters | for...of  |

---

# 🚀 Most Asked Interview Question

## Q:

Can we use `for...of` on objects?

## ❌ Answer:

No, because objects are not iterable by default.

---

# 💡 One-Line Memory Trick

```js id="n7f2vq"
for...in → index/key

for...of → value
```

```
```

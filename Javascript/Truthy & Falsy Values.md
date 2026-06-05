# ✅ JavaScript Truthy & Falsy Values (Interview Notes)
# 🔥 Falsy Values in JavaScript
These values become `false` when converted to boolean.

## 📌 Total 7 Falsy Values

```js
false
0
-0
0n
""
null
undefined
NaN
````

---

# ✅ Examples of Falsy Values

```js
Boolean(false)      // false
Boolean(0)          // false
Boolean("")         // false
Boolean(null)       // false
Boolean(undefined)  // false
Boolean(NaN)        // false
```

---

# 🔥 Truthy Values in JavaScript

Except falsy values, EVERYTHING else is truthy.

## 📌 Common Truthy Values

```js
true
1
-1
[]
{}
"0"
"false"
" "
function(){}
```

---

# ✅ Examples of Truthy Values

```js
Boolean("hello")    // true
Boolean([])         // true
Boolean({})         // true
Boolean("false")    // true
Boolean("0")        // true
```

---

# ⚡ Important Interview Points

## 1. Empty Array is Truthy

```js
if ([]) {
  console.log("true")
}
```

✅ Output:

```js
true
```

---

## 2. Empty Object is Truthy

```js
if ({}) {
  console.log("true")
}
```

✅ Output:

```js
true
```

---

## 3. String `"false"` is Truthy

```js
Boolean("false")
```

✅ Output:

```js
true
```

Because it is a non-empty string.

---

# 🔥 Double NOT (`!!`) Trick

Used to convert any value into boolean.

```js
!!"hello"   // true
!!0         // false
!![]        // true
!!null      // false
```

---

# 🎯 Most Asked Interview Question

## Q1:

```js
Boolean([])
```

✅ Answer:

```js
true
```

---

## Q2:

```js
Boolean({})
```

✅ Answer:

```js
true
```

---

## Q3:

```js
Boolean("")
```

✅ Answer:

```js
false
```

---

## Q4:

```js
Boolean(" ")
```

✅ Answer:

```js
true
```

Because space is also a character.

---

# 🚀 Quick Revision Table

| Value     | Type   |
| --------- | ------ |
| false     | Falsy  |
| 0         | Falsy  |
| ""        | Falsy  |
| null      | Falsy  |
| undefined | Falsy  |
| NaN       | Falsy  |
| []        | Truthy |
| {}        | Truthy |
| "false"   | Truthy |
| "0"       | Truthy |


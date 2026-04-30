# 🔁 Reverse a String in JavaScript

---

## ✅ Using Method (Built-in Functions)

### 🔹 Using Function

```javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}

// Example
console.log(reverseString("hello")); // "olleh"
```

---

### 🔹 Direct Approach

```javascript
const string = "hello javascript";
const output = string.split("").reverse().join("");

console.log("output:", output); // "tpircsavaj olleh"
```

---


---

## 🚀 Summary

* `sort()` method → simple but slower (O(n log n))
* `for` loop method → faster and best for interviews (O(n))

---


### 🔹 Reverse Each Word (Same Space Maintained)

```javascript
const string = "hello javascript";

const output = string
  .split(" ")
  .map(word => word.split("").reverse().join(""))
  .join(" ");

console.log("output:", output); // "olleh tpircsavaj"
```

---

## ✅ Without Using Method (Manual Approach)

### 🔹 Using Function

```javascript
function reverseString(str) {
  let reversed = "";

  for (let i = str.length - 1; i >= 0; i--) {
    reversed += str[i];
  }

  return reversed;
}

// Example
console.log(reverseString("hello")); // "olleh"
```

---

### 🔹 Using Loop (Without Function)

```javascript
let string = "hello javascript";
let result = "";

for (let i = string.length - 1; i >= 0; i--) {
  result += string[i];
}

console.log("reverse string:", result); // "tpircsavaj olleh"
```

---


---

# 🔥 Remove Duplicates (Array + String) — JavaScript

---

# 📌 1. Array Duplicate Remove

## ✅ Using Method (`Set`)

### 💡 Concept:

`Set` automatically unique values store karta hai.

### 🧠 Code:

```js
let arr = [1, 2, 3, 2, 4, 1, 5];

const uniqueArr = [...new Set(arr)];

console.log("Unique Array:", uniqueArr);
```

### ⚡ Output:

```
Unique Array: [1, 2, 3, 4, 5]
```

---

## ✅ Without Method (Manual Logic)

### 💡 Concept:

Loop + `includes()` use karke manually duplicate remove karte hai.

### 🧠 Code:

```js
let arr = [1, 2, 3, 2, 4, 1, 5];
let result = [];

for (let i = 0; i < arr.length; i++) {
  if (!result.includes(arr[i])) {
    result.push(arr[i]);
  }
}

console.log("Unique Array:", result);
```

### ⚡ Output:

```
Unique Array: [1, 2, 3, 4, 5]
```

---

# 📌 2. String Duplicate Remove

## ✅ Using Method (`Set`)

### 💡 Concept:

String → Array → Set → String

### 🧠 Code:

```js
let str = "programming";

let uniqueStr = [...new Set(str)].join("");

console.log("Unique String:", uniqueStr);
```

### ⚡ Output:

```
Unique String: progamin
```

---

## ✅ Without Method (Manual Logic)

### 🧠 Code:

```js
let str = "programming";
let resultStr = "";

for (let i = 0; i < str.length; i++) {
  if (!resultStr.includes(str[i])) {
    resultStr += str[i];
  }
}

console.log("Unique String:", resultStr);
```

### ⚡ Output:

```
Unique String: progamin

```

# 🔹 Find Second Largest Number 

---

## ✅ 1. Using Method

```js
const number = [10,20,30,50,80,20,90,11,4,48,566]

const uniqueNumber = [...new Set(number)]

const sorted = uniqueNumber.sort((a, b) => b - a)

const secondLargest = sorted[1]

console.log("secondLargest", secondLargest)
```

### 📊 Output

```
secondLargest 90
```

---

## ✅ 2. Without Method (Using `for` loop)
## Infinity means: sabse chhota possible number
```js
const number = [10,20,30,50,80,20,90,11,4,48,566]

const uniqueNumber = [...new Set(number)]

let firstLargest = -Infinity
let secondlargest = -Infinity

for(let i = 0; i < uniqueNumber.length; i++){
  let num = uniqueNumber[i]

  if(num > firstLargest){
    secondlargest = firstLargest
    firstLargest = num
  } else if(num > secondlargest && num !== firstLargest){
    secondlargest = num
  }
}

console.log("secondlargest", secondlargest)
```

### 📊 Output

```
secondlargest 90
``

# Find Largest Number in an Array (JavaScript)

## 🔹 Method 1: Using `Math.max()`

```js
const arr = [10, 20, 90, 50, 30, 70, 80];
const largestData = Math.max(...arr);

console.log("largestData", largestData);
```

---

## 🔹 Method 2: Using Loop

```js
let arr1 = [10, 20, 90, 50, 30, 70, 80];
let largestNumber = arr1[0];

for (let i = 1; i < arr1.length; i++) {
  if (arr1[i] > largestNumber) {
    largestNumber = arr1[i];
  }
}

console.log("largestNumber", largestNumber);
```

---

## ✅ Output

```
90
```


# 🔁 Reverse a String in JavaScript.

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


# 📌 Array Duplicate Remove

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
# using filter
```
let arr = [1, 2, 2, 3, 4, 4, 5];
let result = arr.filter((ele,index,arr) => arr.indexOf(ele) == index )
console.log("result",result) // [1,2,3,4,5]

| Parameter | Meaning                  |
| --------- | ------------------------ |
| ele       | Current element          |
| index     | Current element ka index |
| arr       | Original array           |


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
```
### 📊 Output -> secondlargest 90
```

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

# 📌 Find Even Numbers in JavaScript 

## ✅ 1. Using Array Method 

```js
let arr = [1, 2, 3, 4, 5, 6, 8, 8];

let evenNumber = arr.filter((num) => num % 2 === 0);

let countEvenNumber = arr.filter((num) => num % 2 === 0).length;

console.log("EvenNumber Output", evenNumber); 
// [2, 4, 6, 8, 8]

console.log("Count EvenNumber Output", countEvenNumber); 
// 5
```



## ✅ 2. Without Using Method

```
let arr1 = [2,3,4,6,8,9,10,11,15,8];
let result = [];

for(let i = 0; i < arr1.length; i++){
  if(arr1[i] % 2 === 0){
    result.push(arr1[i]);
  }
}

console.log("EvenNumber Output", [...new Set(result)]); //  [ 2, 4, 6, 8, 10 ]

```


# 📌 Convert Array to Object in JavaScript

let arr = ["a", "1", "b", "2", "c", "3"];

## ✅ Code

```js
let arr = ["a", "1", "b", "2", "c", "3"];

let obj = {};

for (let i = 0; i < arr.length; i += 2) {
obj[arr[i]] = Number(arr[i + 1]);
}

console.log("Output", obj); //  { a: 1, b: 2, c: 3 }
```


# 📌Find Smallest Value in Array (JavaScript)

## 1. Using Method

```javascript
function smallvalue(ele) {
  return Math.min(...ele)
}

console.log(smallvalue([1,2,3,4,5,1]))
```

### Output

```
1
```

---

## 2. Without Method (Using Function)

```javascript
function findSmallest(arr) {
  let small = arr[0]

  for(let i = 1; i < arr.length; i++){
    if(arr[i] < small){
      small = arr[i]
    }
  }

  return small
}

console.log(findSmallest([3,5,7,1,9]))
```

### Output

```
1
```

#  📌 JavaScript Array Sum Program 

```javascript
function sum(val){
  let result = 0

  for(let ele = 0; ele < val.length; ele++){
    result += val[ele]
  }

  return result
}

console.log("Sum output", sum([1,2,3,4,5,6]))
```

## Output

```javascript
Sum output 21
```

---

# JavaScript Array Sum Program Using reduce() Method

```javascript
let arr = [1,2,3,4,5,6]

const result = arr.reduce((acc, cur) => acc + cur, 0)

console.log("result", result)
```

## Output

```javascript
result 21
```

# 📌 JavaScript Program to Find Average of Array Elements

---

# 1. Average Program Without Method (Using for loop)

```javascript
function average(arr){
  let sum = 0

  for(let i = 0; i < arr.length; i++){
    sum += arr[i]
  }

  return sum / arr.length
}

console.log("Average Output", average([10,20,30,40,50]))
```

## Output

```javascript
Average Output 30
```

---

# 2. Average Program Using reduce() Method

```javascript
let arr = [10,20,30,40,50]

let sum = arr.reduce((acc, cur) => acc + cur, 0)

let average = sum / arr.length

console.log("Average Output", average)
```

## Output

```javascript
Average Output 30
```

-

# 📌Even and Odd Numbers Separate Program in JavaScript

---

# 1. Without Method (Using Loop)

```js
const arr = [1,2,3,4,5,6,7,8,9,10];
function OddEvenfilter(arr){
  let odd = [];
  let even = [];

  for(let i = 0 ; i < arr.length ; i++){
    if(arr[i] % 2 === 0){
      even.push(arr[i]);
    } else {
      odd.push(arr[i]);
    }

  }

  return {odd, even};

}

const result = OddEvenfilter(arr);

console.log("Odd Data:", result.odd); // [ 1, 3, 5, 7, 9 ]
console.log("Even Data:", result.even); // [ 2, 4, 6, 8, 10 ]
```

---

# 2. Using Method (`filter()`)

```js
const arr = [1,2,3,4,5,6,7,8,9,10];
const evenData = arr.filter((ele) => ele % 2 === 0);
const oddData = arr.filter((ele) => ele % 2 !== 0);

console.log("Odd Data:", oddData); // [ 1, 3, 5, 7, 9 ]
console.log("Even Data:", evenData); // [ 2, 4, 6, 8, 10 ]
```


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

OR

const data = arr.filter((ele,index,arr) => arr.indexOf(ele) === index)
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

# 📌 JavaScript Array Sorting Program

```js 
let arr = [1,6,3,4,2,9,8];


// ================= ASCENDING ORDER =================

let ascending = [...arr].sort((a,b) => a - b);

console.log("Ascending Result:", ascending); // [1, 2, 3, 4, 6, 8, 9]


// ================= DESCENDING ORDER =================

let descending = [...arr].sort((a,b) => b - a);

console.log("Descending Result:", descending); // [9, 8, 6, 4, 3, 2, 1]
```


# 📌 Prime Number Program in JavaScript

Prime Number Kya Hota Hai?

```
  Prime number wo number hota hai jo:

  1 se bada ho
  Sirf 2 numbers se divide ho
  * 1
  * khud number

```

```
0 → Not Prime
1 → Not Prime
negative → Not Prime
```

```js id="n8r0zv"
function prime(num){

  if(num <= 1){
    return "Not a Prime Number";
  }

  for(let i = 2; i < num; i++){
    // OR  for(let i = 2; i < Math.sqrt(num); i++){

    if(num % i === 0){
      return "Not a Prime Number";
    }

  }

  return "Prime Number";
}

console.log(prime(7));
```

---

# ✅ Output

```txt id="e7w9c8"
Prime Number
```

# 📌Print Duplicate Value

```js id="5wz6pt"
// With Method

const arr = [1,2,2,3,4,4,5,6,6,7,8,8,9,1];

const data = arr.filter((ele,index,arr) => 
    arr.indexOf(ele) !== index
);

console.log("Print Duplicate Value", data); //[ 2, 4, 6, 8, 1 ]



// Without Method

let arr1 = [1,2,2,3,4,4,5,6,6,7,8,8,9,1];

let element = [];

for(let i = 0 ; i < arr1.length ; i++){

    for(let j = i + 1 ; j < arr1.length ; j++){

        if(arr1[i] === arr1[j]){
            element.push(arr1[i]);
        }

    }
}

console.log("Print Duplicate Value", element); //[ 2, 4, 6, 8, 1 ]
```

# String Palindrome Program

## Program

```js id="3sz4yy"
const str = "madam";

const reverseStr = str.split("").reverse().join("");

if(str === reverseStr){
  console.log("Palindrome");
}else{
  console.log("Not Palindrome");
}

*************************************************************OR**********************************************

function palindromeString(ele) {

  let lowerCase = ele.toLowerCase();
  let reverse = "";

  for(let i = lowerCase.length - 1; i >= 0; i--) {
    reverse += lowerCase[i];
  }

  if(lowerCase === reverse) {
    console.log("Palindrome");
  } else {
    console.log("Not Palindrome");
  }
}

palindromeString("Madam");
```

## Output

```js id="jlwmd1"
Palindrome
```

---

# Number Palindrome Program

## Program

```js id="jlwmf3"
const num = 121;

const reverseNumber = Number(
  num.toString().split("").reverse().join("")
);

if(num === reverseNumber){
  console.log("Palindrome");
}else{
  console.log("Not Palindrome");
}


*********************************************************OR*********************************************************

function palindromeNumber(num) {

  let convertNumber = num.toString();

  let reverse = "";

  for(let i = convertNumber.length - 1; i >= 0; i--) {
    reverse += convertNumber[i];
  }

  if(convertNumber === reverse) {
    console.log("Palindrome");
  } else {
    console.log("Not Palindrome");
  }
}

palindromeNumber(121);
```

## Output

```js id="jlwmg7"
Palindrome
```

# 📌 Factorial Program Using Recursion

```javascript id="t8m2x5"
function factorialOne(n){
  if(n === 0){
    return 1
  }else{
    return n * factorialOne(n - 1) 
  }
}

console.log(factorialOne(5)) 
```

## ✅ Output

```javascript id="q4n7m1"
120
```

---

# Factorial Program Using Loop

```javascript id="k1x8m4"
function factorialTwo(num){

  let result = 1

  // i = 1 liya because 0 se start karte to
  // 1 * 0 = 0 ho jata

  for(let i = 1 ; i <= num ; i++){

    // num ek number hai
    // number me length nahi hoti
    // length sirf string aur array me hoti hai

    result = result * i
  }

  console.log(result)
}

factorialTwo(5)
```

## ✅ Output

```javascript id="w6m3q9"
120
```

````md
# 📌 Flatten Array in JavaScript

---

# 1. Using flat() Method

## Program

```js
const arr = [1, [2, 3], [4, [5, 6]]];

const result = arr.flat(Infinity); 
// const result = arr.flat(1);
// const result = arr.flat(2);

console.log(result);
````

## Output

```js
[1, 2, 3, 4, 5, 6]
```

---

# 2. Without Method (Using Recursion)

* Jab koi function khud ko hi call karta hai usko Recursive Function bolte hai.

## Program

```js
function flattenArray(arr) {

  let result = [];

  for (let item of arr) {

    if (Array.isArray(item)) {

      result = result.concat(flattenArray(item));

    } else {

      result.push(item);
    }
  }

  return result;
}

console.log(flattenArray([1, [2, 3], [4, [5, 6]]]));

******************************************************OR******************************************************

let result = [];
function flattenArray(arr){
  for(let i = 0 ; i<arr.length ; i++){

    if(Array.isArray(arr[i])){
      flattenArray(arr[i]) // recursion function 
    }else{
      result.push(arr[i])
    }
    
  }
}

flattenArray([1, [2, 3], [4, [5, 6]]])
console.log("result",result)
```

## Output

```js
[1, 2, 3, 4, 5, 6]
```


# 📌 String में Vowels Count और Print Program

## 1. Using `includes()` Method

```js id="xkn9e1"
// Using includes() method

function checkVowel(e) {
  let ele = e.toLowerCase();
  let count = 0;
  let vowel = "aeiou";
  let result = "";

  for (let i = 0; i < ele.length; i++) {
    if (vowel.includes(ele[i])) {
      count++;
      result += ele[i];
    }
  }

  console.log("count", count);   // 7
  console.log("result", result); // eooaeou

  return count;
}

console.log(checkVowel("hello how are yoU"));
```

# 2. Without Using Any Method

```js id="qf7t0g"
// Without using includes() method

function checkVowelOne(e) {
  let ele = e.toLowerCase();
  let count = 0;
  let result = "";

  for (let i = 0; i < ele.length; i++) {
    let ch = ele[i];

    if ( ch === "a" || ch === "e" || ch === "i" || ch === "o" || ch === "u") 
    {
      count++;
      result += ele[i];
    }
  }

  console.log("count", count);   // 7
  console.log("result", result); // eooaeou

  return count;
}

console.log(checkVowelOne("hello how are yoU"));
```

# Union of Array in JavaScript

## 1. Union With Method (`Set`)

```javascript
// union(+) combine two arrays with removing duplicates

const arr1 = [1, 2, 3];
const arr2 = [3, 4, 5];

const resultData = [...new Set([...arr1, ...arr2])];

console.log("Union Result With Method:", resultData);
```

### Output

```javascript
Union Result With Method: [1, 2, 3, 4, 5]
```

---

## 2. Union Without Method (`includes` + loop)

* Union combines all unique elements from multiple arrays.

```javascript
const arr3 = [1, 2, 3];
const arr4 = [3, 4, 5];

let result = [];

// First array values
for (let i = 0; i < arr3.length; i++) {
  if (!result.includes(arr3[i])) {
    result.push(arr3[i]);
  }
}

// Second array values
for (let i = 0; i < arr4.length; i++) {
  if (!result.includes(arr4[i])) {
    result.push(arr4[i]);
  }
}

console.log("Union Result Without Method:", result);
```

### Output

```javascript
Union Result Without Method: [1, 2, 3, 4, 5]
```


# Intersection of Array in JavaScript

## 1. Intersection With Method (`filter` + `includes`)

* Intersection(&) returns only common elements between arrays.

```javascript id="0q6c8f"

const arr1 = [1, 2, 3];
const arr2 = [3, 4, 5];

const result = arr1.filter((ele) => arr2.includes(ele));

console.log("Intersection With Method:", result);
```

### Output

```javascript id="s7n2kx"
Intersection With Method: [3]
```

---

## 2. Intersection Without Method (`for loop`)

```javascript id="z5v1mc"
const arr3 = [1, 2, 3, 4];
const arr4 = [3, 4, 5, 1];

let result2 = [];

for (let i = 0; i < arr3.length; i++) {
  for (let j = 0; j < arr4.length; j++) {
    if (arr3[i] === arr4[j]) {
      result2.push(arr3[i]);
    }
  }
}

console.log("Intersection Without Method:", result2);
```

### Output

```javascript id="v3f8qa"
Intersection Without Method: [1, 3, 4]
```


# Word Count in JavaScript

---

# 1. Using Method

```javascript
const str = "hello How are you all";
const result = str.trim().split(" ").length;

console.log("result", result);
````

## Output

```javascript
result 5
```

---

# 2. Without Method (Using For Loop)

```javascript
function wordCount(word) {
  let count = 0;

  for (let i = 0; i < word.length; i++) {

    // Agar current character space hai
    // aur previous character space nahi hai
    // to word complete hua
    if (word[i] === " " && word[i - 1] !== " ") {
      count++;
    }
  }

  return count + 1;
}

console.log(wordCount("hello How are you all"));
```

## Output

```javascript
5
```

# Double Array Elements Using map() in JavaScript - (map() का use करके array को double करना)

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.map((item) => item * 2);

console.log(result);
````

## Output

```javascript
[2, 4, 6, 8, 10]
```

# Filter Positive Numbers in JavaScript - (filter() से positive numbers निकालना)

```javascript
const numbers = [-5, 10, -2, 7, -1, 15];

const positiveNumbers = numbers.filter((num) => num > 0);

console.log(positiveNumbers);
````

## Output

```javascript id="c9r2n5"
[10, 7, 15]
```


# find() से first matching value ढूंढना

`find()` method array me se first matching value return karta hai.

```javascript id="zmnl0m"
const numbers = [10, 20, 30, 40];

const result = numbers.find((num) => num > 20);

console.log(result);
```

## Output

```javascript id="8llhhn"
30
```


# Example 2

```javascript id="e8t9bc"
const users = [
  { id: 1, name: "Krupa" },
  { id: 2, name: "Rahul" }
];

const result = users.find((user) => user.id === 2);

console.log(result);
```

## Output

```javascript id="bx6y3x"
{ id: 2, name: "Rahul" }
```


# includes() से value exist करती है या नहीं check करना

`includes()` method check karta hai ki value array ya string me exist karti hai ya nahi.

# Example 1 (Array)

```javascript id="4q2zwd"
const numbers = [10, 20, 30, 40];

const result = numbers.includes(20);

console.log(result);
```

## Output

```javascript id="9shd7r"
true
```

# Example 2 (String)

```javascript id="gx99mk"
const str = "Hello JavaScript";

const result = str.includes("Java");

console.log(result);
```

## Output

```javascript id="70we4r"
true
```


# Swap Two Numbers in JavaScript

# 1. With Method (Using Destructuring)

```javascript
let a = 10;
let b = 20;

[a, b] = [b, a];

console.log("a =", a);
console.log("b =", b);
````

## Output

```javascript id="t8u0m7"
a = 20
b = 10
```

---

# 2. Without Method (Using Third Variable)

```javascript id="o3r8fy"
let a = 10;
let b = 20;

let temp = a;
a = b;
b = temp;

console.log("a =", a);
console.log("b =", b);
```

## Output

```javascript id="h5m7qp"
a = 20
b = 10
```









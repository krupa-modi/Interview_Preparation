# program list
# 📋 Programs List

1. Reverse a String
2. Reverse Each Word
3. Remove Duplicate from Array
4. Remove Duplicate from String
5. Find Second Largest Number
6. Find Largest Number in Array
7. Find Even Numbers
8. Convert Array to Object
9. Find Smallest Value in Array
10. Array Sum Program
11. Find Average of Array Elements
12. Separate Even and Odd Numbers
13. Array Sorting Program
14. Prime Number Program
15. Print Duplicate Values
16. String Palindrome Program
17. Number Palindrome Program
18. Factorial Program Using Recursion
19. Factorial Program Using Loop
20. Flatten Nested Array
21. Count and Print Vowels
22. Union of Arrays
23. Intersection of Arrays
24. Word Count Program
25. Double Array Elements using map()
26. Filter Positive Numbers
27. find() Method Example
28. includes() Method Example
29. Swap Two Numbers
30. Missing Number in Array
31. First Non-Repeating Character
32. Non-Repeating Characters
33. Merge Two Arrays
34. Two Sum Problem
35. Move All Zeros To End
36. Fibonacci Series Program
37. Longest Substring Without Repeating Characters
38. String Compression
39. String Character Count
40. Anagram Program
41. Binary Search Program
42. Armstrong number
43. Positive or Negative
44. Prime numbers in range
45. Swap Two Numbers Without Using Third Variable
46. Specific Character Count in String
47. Count Digits
48. Character Count Using Map
49. Power of Number
50. Random Number
51. Array Rotate(Left/Right)
52. Find Common Elements in Array
53. Separate Unique and Duplicate Values in Array
54. Remove False Values from Array
55. Find Largest and Smallest Number in Array
56. Frequency Count in Array
57. Most Repeated Character in string
58. Remove Special Characters from String
59. First Letter Capital of Every Word
60. Frequency Count in Array
61. Longest Word in Sentence
62.  Count Spaces in String
63. Toggle Case in String
64. Sort Array of Objects
65. Object Key with Highest Value
66. Convert Object to Array
67. Two Objects Equal or Not
68. Remove Duplicate Words From Sentence
69. Count Vowels & Consonants
70. Star Pattern Printing
71. Number Pattern Printing
72. Remove spaces
73. Reverse Words
74. Replace Characters / Words in JavaScript
75. Check Sorted Array
76. Merge Sorted Arrays
77. Method Chaining Calculator Program
78. Merge Sort basic
79. Maximum Subarray Sum



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


# Program: Missing Number in Array Using for Loop

## Program 1

```js
let arr = [1,2,3,5,6,7,8,9]; // ismain ek hi number missing hai 

let n = arr.length + 1;
let totalSum = (n * (n + 1)) / 2;// formula hai
let arrSum = 0;

for(let i = 0; i < arr.length ; i++){
  arrSum += arr[i];
}

let missingNumber = totalSum - arrSum;

console.log("Missing Number" , missingNumber);
````

## Output

```js
Missing Number 4
```

---

# Program: Missing Number in Array Using reduce()

## Program 2

```js
let arr1 = [1,2,3,5,6,8,9]; // ismian 2 number mssing hai so o/p main dono value ka sum hai but total sum ka formula one missing value ke liye use hota hai

let n1  = arr1.length + 2;

let totalSum1 = (n1 * (n1 + 1)) / 2;

let result = arr1.reduce((acc,curr) => acc + curr,0);

let missingNumber1 = totalSum1 - result;

console.log("Missing Number1" , missingNumber1);
```

## Output

```js
Missing Number1 11
```

## Why Output is 11?

Because array has two missing numbers:

```js
4 and 7
```

Formula approach adds both missing numbers:

```js
4 + 7 = 11
```

So output becomes:

```js
11
```


# First Non-Repeating Character in JavaScript

# 1. Using String Methods (`indexOf` and `lastIndexOf`)

## Program

```javascript
const str = "aabbbcddef";
let result = [];

for (let char of str) {
  if (str.indexOf(char) === str.lastIndexOf(char)) {
    result.push(char);
    break;
  }
}

console.log(result.join(","));
```

## Output

```javascript
c
```
---

# 2. Without Using String Methods (Nested Loop)

## Program

```javascript
function strCount(str) {
  for (let i = 0; i < str.length; i++) {
    let count = 0;

    for (let j = 0; j < str.length; j++) {
      if (str[i] === str[j]) {
        count++;
      }
    }

    if (count === 1) {
      return str[i];
    }
  }
}

console.log(strCount("aabbbcddef"));
```

## Output

```javascript
c
```


# Non-Repeating Characters in JavaScript

# 1. Using `indexOf()` and `lastIndexOf()`

## Program

```javascript id="vf1qpn"
const str = "aabbbcddef";
let result = [];

for (let char of str) {

  if (str.indexOf(char) === str.lastIndexOf(char)) {
    result.push(char);
  }

}

console.log(result.join(","));
```

## Output

```javascript id="v4uw86"
c,e,f
```

---

# 2. Without Using Methods (Nested Loop)

## Program

```javascript id="v0y3bm"
function strCount(str) {

  let total = 0;

  for (let i = 0; i < str.length; i++) {

    let count = 0;

    for (let j = 0; j < str.length; j++) {

      if (str[i] === str[j]) {
        count++;
      }

    }

    if (count === 1) {
      console.log(str[i]);
      total++;
    }

  }

  console.log("Total Length", total);

}

strCount("aabbbcddef");
```

## Output

```javascript id="t1s1mk"
c
e
f

Total Length 3
```


# Merge Two Arrays in JavaScript

Example:

```js id="8r0e5m"
[1,2,3,4] + [5,6,7,8]
```

Merged Array:

```js id="7c4m2n"
[1,2,3,4,5,6,7,8]
```

---

# 1. Using Methods

## Using `concat()`

### Program

```javascript id="1g5m9v"
const arr = [1,2,3,4];
const arr1 = [5,6,7,8];

const result = arr.concat(arr1);

console.log("Merged Two Arrays:", result);
```

### Output

```javascript id="x5m3z7"
Merged Two Arrays: [1,2,3,4,5,6,7,8]
```

---

## Using Spread Operator

### Program

```javascript id="q4z2lm"
const arr = [1,2,3,4];
const arr1 = [5,6,7,8];

const result = [...arr, ...arr1];

console.log("Merged Two Arrays:", result);
```

### Output

```javascript id="6l7p1v"
Merged Two Arrays: [1,2,3,4,5,6,7,8]
```

---

# 2. Without Using Methods

## Program

```javascript id="n3v9xq"
const arr = [1,2,3,4];
const arr1 = [5,6,7,8];

let result = [];

// First Array Elements
for(let i = 0; i < arr.length; i++) {
  result.push(arr[i]);
}

// Second Array Elements
for(let i = 0; i < arr1.length; i++) {
  result.push(arr1[i]);
}

console.log("Merged Two Arrays:", result);
```

### Output

```javascript id="p9m4tw"
Merged Two Arrays: [1,2,3,4,5,6,7,8]
```



# Two Sum problem 
* Two sum probelm me hume array ke andar aise 2 numbers find karne hote hai jinka sum target ke equal ho.  
Agar sum match ho jaye to unke indexes aur values return karte hai.


```js
function twoSum(num, target) {

  for (let i = 0; i < num.length; i++) {

    for (let j = i + 1; j < num.length; j++) {

      if (num[i] + num[j] === target) {
        // return [i,j] // [0,2]
        return {
          indexes: [i, j],
          values: [num[i], num[j]]
        }

      }

    }

  }

}

console.log(twoSum([2, 7, 11, 15], 13))
```

---

# Output

```js
{
  indexes: [0, 2],
  values: [2, 11]
}
```


# Move All Zeros To End

# 1. With Method

```js
function zeroOne(arr){

  const withoutZero = arr.filter((num) => num !== 0);
  const withZero = arr.filter((num) => num === 0);
  
  const result = withoutZero.concat(withZero)
  
  return result
}

console.log(zeroOne([1, 0, 2, 0, 3, 0, 4]))
```

## Output

```js
[1, 2, 3, 4, 0, 0, 0]
```

---

# 2. Without Method

```js
function zeroTwo(arr){

  let count = 0;
  let emptyArr = [];
  
  for(let i = 0 ; i < arr.length ; i++){

    if(arr[i] !== 0){
      emptyArr.push(arr[i])

    }else{
      count ++ 
    }

  }

  for(let i = 0 ; i < count ; i++){
    emptyArr.push(0)
  }

  return emptyArr
}

console.log(zeroTwo([1, 0, 2, 0, 3, 0, 4]))
```

## Output

```js
[1, 2, 3, 4, 0, 0, 0]
```


# Fibonacci Series Program

Fibonacci series me har next number pichle 2 numbers ka sum hota hai.

```js
function fibonacci(num){

  let a  = 0;
  let b = 1;
  
  console.log(a)
  console.log(b)
  
  for(let i = 2 ; i < num ; i++){
    let c = a + b 
    console.log(c)
    a = b;
    b = c
  }
}

fibonacci(9)
```

---

# Output

```js
0
1
1
2
3
5
8
13
21
```

# Longest Substring Without Repeating Characters

Is program me string ka longest substring find kiya jata hai jisme koi bhi character repeat na ho.

---

# Program

```js
function strData(str){

  let max = 0;
  let temp = ""

  for(let i = 0 ; i < str.length ; i++){ // starting point choose karta hai

    for(let j = i ; j < str.length ; j++){ // remaining elements check karta hai

      if(temp.includes(str[j])){
        break;
      }

      temp += str[j]
      
      if(temp.length > max){
        max = temp.length
      }

    }

  }

  // return {temp,max};//{ temp: 'abc', max: 3 }
  // return [temp,max] // [ 'abc', 3 ]
  // return [temp,max].join(",") // abc,3
  // return temp // abc
  return max // 3
}

console.log(strData("abcabcbb"))
```

---

# Output

```js
3
```

# String Compression OR String compression 

Is program me string ke repeated characters ko count karke compressed format me convert kiya jata hai.

```js
function strData(str){

  let temp = "";
  let count = 1;
  
  for(let i = 0 ; i < str.length ; i++){

    if(str[i] === str[i+1]){
      count++
    }else{
      temp += str[i] + count
      count = 1
    }

  }

  return temp
}

console.log(strData("aaabbcc"))
```

---

# Output

```js
a3b2c2
```


# String Character Count(different sequence)

Is program me string ke har character ka total count find karke compressed format me return kiya jata hai.

# Program

```js
function strData(str){

  let temp = "";
  for(let i = 0 ; i < str.length ; i++){
    let count = 0;
    for(let j = 0 ; j < str.length ; j++){
      if(str[i] === str[j]){
        count++
      }
    }

    if(!temp.includes(str[i])){
      temp += str[i] + count
    }

  }

  return temp
}

console.log(strData("aabbaccabc"))
```

---

# Output

```js
a4b3c3
```

# Anagram Program in JavaScript

Two strings are called anagrams if they contain:

- Same characters
- Same number of times
- Order can be different

---

# 1. Anagram Using Method

```js
function Anagram(str1, str2) {

  const result1 = str1.toLowerCase().split("").sort().join("");

  const result2 = str2.toLowerCase().split("").sort().join("");

  if (result1 === result2) {
    console.log("This is Anagram");
  } else {
    console.log("Not Anagram");
  }
}

Anagram("listen", "silent");
```

---

## Output

```js
This is Anagram
```

# 2. Anagram Without Method (Using for Loop)

## Program

```js
function Anagram(str1, str2) {

  let count = 0;

  if (str1.length !== str2.length) {
    console.log("Not Anagram");
    return;
  }

  for (let i = 0; i < str1.length; i++) {

    for (let j = 0; j < str2.length; j++) {

      if (str1[i] === str2[j]) {

        count++;

        str2 = str2.substring(0, j) + str2.substring(j + 1);// remove same character

        break;
      }
    }
  }

  if (count === str1.length) {
    console.log("Anagram");
  } else {
    console.log("Not Anagram");
  }
}

Anagram("listen", "silent");
```

---

## Output

```js
Anagram
```


# Binary Search in JavaScript

Binary Search is a searching algorithm used to find an element in a sorted array.


```js
function binary(arr,target){
  
  let low = 0;
  let high = arr.length - 1;
  
  while(low <= high){
    
    let mid = Math.floor((low + high) / 2);
    
    if(arr[mid] === target){
      return mid;
    }
    
    else if(arr[mid] < target){
      low = mid + 1;
    }
    
    else{
      high = mid - 1;
    }
  }
  
  return -1;
}

console.log(binary([1,2,3,4,5,6,7,8,9],6)); // means jo target hai 6 uska index find karna
```

---

# Output

```js
5
```

# Armstrong Number

Armstrong Number woh number hota hai jisme har digit ka power total digits se karke add karne par same original number milta hai.

### Example

```javascript id="5m2x8q"
153
```

```javascript id="2q7v1m"
1³ + 5³ + 3³ = 153
```

✅ Isliye `153` Armstrong Number hai.

---

# Program

```javascript id="8x1m4q"
function armStrong(num) {
  let originalNum = num;
  let digit = num.toString().length;
  let sum = 0;

  while (num > 0) {
    // let val = 153 % 10; = 3
    // let val = 153 / 10; = 15.3

    let val = num % 10; 
    sum = sum + val ** digit
    num = Math.floor(num / 10);
  }

  if (sum === originalNum) {
    console.log("Armstrong");
  } else {
    console.log("Not Armstrong");
  }
}

armStrong(153);
```

---

# Output

```javascript id="6q2m9x"
Armstrong
```

# Positive, Negative, Zero Program in JavaScript

## Code

```js id="j7tqww"
function checkNumber(num){

  if(num > 0){
    console.log("positive")
  }
  else if(num < 0){
    console.log("negative")
  }
  else{
    console.log("zero")
  }

}

checkNumber(10)
checkNumber(-10)
checkNumber(0)
```
---

## Output

```txt id="9c2ryv"
positive
negative
zero
```

# Program 2: Arrange Positive, Negative, and Zero

## Code

```js id="6xvffr"
function arrangeNumbers(arr){

  let positive = [];
  let negative = [];
  let zero = [];

  for(let i = 0; i < arr.length; i++){

    if(arr[i] > 0){
      positive.push(arr[i]);
    }
    else if(arr[i] < 0){
      negative.push(arr[i]);
    }
    else{
      zero.push(arr[i]);
    }

  }

  return [...positive, ...negative, ...zero];
}

console.log(arrangeNumbers([2,0,3,4,6,-4]));
```

---

## Output

```js id="3brdmg"
[2, 3, 4, 6, -4, 0]
```


# Prime Numbers in Range

```javascript
function primeCount(start,end){

  for(let num = start ; num < end ; num++){

    let isPrime = true;

    if(num < 2){
      isPrime = false
    }

    for(let i = 2 ; i < num ; i++ ){

      if(num % i === 0){
        isPrime = false
        break;
      }

    }

    if(isPrime){
      console.log(num)
    }

  }

}

primeCount(1, 10)
````

---

## Output

```javascript
2
3
5
7
```

# Count Digits

```javascript
function digitCount(num){

  let count = 0;

  while(num > 0){

    num = Math.floor(num / 10)

    count++

  }

  return count
}

console.log(digitCount(123498867676))
````

---

## Output

```javascript
12
```

# Swap Two Numbers Without Using Third Variable

## Question

```js
a = 10
b = 5
````

```js
let a = 10;
let b = 5;

a = a + b; // 15
b = a - b; // 10
a = a - b; // 5

console.log("a =", a);
console.log("b =", b);
```

---

# Output

```js
a = 5
b = 10
```

---

# Method 2 → Best Modern JavaScript Way (Most Asked)

## Using Destructuring

```js
let a = 10;
let b = 5;

[a, b] = [b, a];

console.log(a);
console.log(b);
```

---

# Output

```js
5
10
```


# Find common numbers from given array

```js
function commonNumber(arr){
  return arr[0].filter(
    (ele1) => arr.every(
      (ele2) => ele2.includes(ele1)
    )
  )
}

console.log(commonNumber([[2, 4, 5, 3],[2, 3, 5],[4, 2, 5]]))
```

## Output

```js
[2, 5]
```

# Method 2 — Using Loops

```js
function commonNumber(arr){
  let result = [];

  for(let i = 0 ; i < arr[0].length ; i++){

    let num = arr[0][i]; // arr[0] means [2, 4, 5, 3] and arr[0][i] means 2
    let isCommon = true;

    for(let j = 1 ; j < arr.length ; j++){

      if(!arr[j].includes(num)){
        isCommon = false;
        break;
      }

    }

    if(isCommon){
      result.push(num);
    }

  }

  return result;

}

console.log(
  commonNumber([[2, 4, 5, 3],[2, 3, 5],[4, 2, 5]])
)
```

## Output

```js
[2, 5]
```


# Specific Character Count in String

```js id="dfm71t"
function specificCharCount(str, target){

  let count = 0;

  for(let i = 0; i < str.length; i++){

    if(str[i] === target){
      count++;
    }

  }

  return count;
}

*****************************************************OR*************************************************************
function specificCharCount(str, target){

  let count = 0;
  for(let char of str){
    if(char === target){
      count++;
    }
  }

  return count;
}

console.log(specificCharCount("apple", "a"));

console.log(specificCharCount("apple", "p"));
```
---

# Final Output

```js id="js9j4q"
2
```

# Character Count Using Map
---

# Program

```js id="jlwmz1"
function CharCount(str){

  const map = new Map();

  for(let i = 0; i < str.length; i++){

    let char = str[i];

    if(map.has(char)){
      map.set(char, map.get(char) + 1);
    }else{
      map.set(char, 1);
    }

  }

  return map;
}

console.log(CharCount("apple"));
```

---

# Output

```js id="jlwmz2"
Map(4) {
  'a' => 1,
  'p' => 2,
  'l' => 1,
  'e' => 1
}
```

# Power of Number

## Definition
Power of number means किसी number को कितनी बार multiply करना है।

Example:
2^4 = 2 × 2 × 2 × 2 = 16
---

```javascript
function powerDigit(val, power){
  let result = 1;

  for(let i = 1; i <= power; i++){
    result = result * val;
  }

  return result;
}

console.log(powerDigit(2,4));

```

# Random Number
`Math.random()` 0 से 1 के बीच random decimal value देता है।
`Math.floor()` decimal value को integer में convert करता है।

---

```javascript
function randomNum(num){
  const result = Math.floor(Math.random() * 10);

  console.log(result);
}

randomNum(123);
````

---

## Output

```javascript
7 // randomly output change
```


# Array Rotate

# 1. LEFT ROTATE — WITH METHOD

```js
function leftRotate(arr){
  let first = arr.shift();
  arr.push(first);
  return arr;
}

console.log(leftRotate([1,2,3,4,5]))
````

## Output

```js
[2,3,4,5,1]
```

---

# 2. LEFT ROTATE — WITHOUT METHOD

## Program

```js
function leftRotate(arr){

  let first = arr[0];

  for(let i = 0; i < arr.length - 1; i++){
    arr[i] = arr[i + 1];
  }

  arr[arr.length - 1] = first;
  return arr;
}

console.log(leftRotate([1,2,3,4,5]))
```

## Output

```js
[2,3,4,5,1]
```

---

# Right Rotate

# 1. RIGHT ROTATE — WITH METHOD

## Program

```js
function rightRotate(arr){
  let last = arr.pop();
  arr.unshift(last);
  return arr;
}

console.log(rightRotate([1,2,3,4,5]))
````

## Output

```js
[5,1,2,3,4]
```

---

# 2. RIGHT ROTATE — WITHOUT METHOD

## Program

```js
function rightRotate(arr){

  let last = arr[arr.length - 1];
  
  for(let i = arr.length - 1; i > 0; i--){
    arr[i] = arr[i - 1];
  }

  arr[0] = last;
  return arr;
}

console.log(rightRotate([1,2,3,4,5]))
```

## Output

```js
[5,1,2,3,4]
```


# Find Common Elements in Array


# 1. Without Method (Using `for` Loop)

```js
function commonArray(arr1, arr2) {
  let result = [];

  for (let i = 0; i < arr1.length; i++) {

    for (let j = 0; j < arr2.length; j++) {

      if (arr1[i] === arr2[j]) {
        result.push(arr1[i]);
      }

    }
  }

  return result;
}

console.log(commonArray([1,2,3,4], [3,4,5,6]));
````

---

## Output

```js
[3, 4]
```

# 2. Using Method (`filter()` + `includes()`)

```js
let arr1 = [1,2,3,4];
let arr2 = [3,4,5,6];

const result = arr1.filter(ele => arr2.includes(ele));

console.log(result);
```

---

## Output

```js
[3, 4]
```


# Separate Unique and Duplicate Values in Array

# 1. Without Method (Using `for` Loop)

```js
function uniqueDuplicate(arr){
  let unique = [];
  let duplicate = [];
  
  for(let i = 0 ; i < arr.length ; i++){
    let count = 0;
    
    for(let j = 0 ; j < arr.length ; j++){
      
      if(arr[i] === arr[j]){
        count++;
      }
    }

    if(count === 1){
      unique.push(arr[i]);
    }else{
      if(!duplicate.includes(arr[i])){ // agar ye use nae karte to duplicate value repeat hoti like [1,2,2,1]
        duplicate.push(arr[i]); // [1,2]
      }

    }
  }

  console.log("unique", unique);
  console.log("duplicate", duplicate);
}

uniqueDuplicate([1,2,3,2,4,5,1,6]);
````
## Output

```js id="kk1hri"
unique [3,4,5,6]
duplicate [1,2]
```

# 2. With Method (`filter()`)

```js id="o9m1yv"
let arr = [1,2,3,2,4,5,1,6];

let unique = arr.filter(
  ele => arr.indexOf(ele) === arr.lastIndexOf(ele)
);

console.log(unique);

let duplicate = arr.filter(
  (ele, index) => arr.indexOf(ele) !== index
);

console.log(duplicate);
```

## Output

```js id="p7z9x4"
[3,4,5,6]
[2,1]
```


# Remove False Values from Array

to remove falsy values from array.

`Boolean` converts values into:
- `true`
- `false`

Only truthy values are returned.

```js
const arr = [1,0,false,2,"",null,3,undefined];

const result = arr.filter(Boolean);

console.log("result", result);
````
---

## Output

```js id="y8m1qv"
result [1,2,3]
```

---

# 2. Without Method (Using `for` Loop)

```js id="k7x2pd"
function truthyValue(arr){
  let result = [];
  
  for(let i = 0 ; i < arr.length ; i++){

    if(arr[i]){
      result.push(arr[i]);
    }

  }

  return result;
}

console.log(
  truthyValue([1,0,false,2,"",null,3,undefined])
);
```

---

## Output

```js id="n5v8ra"
[1,2,3]
```


# Find Largest and Smallest Number in Array


# 1. Without Method (Using `for` Loop)

```js
function bigsmallValue(arr){
  let largest = arr[0];
  let smallest = arr[0];
  
  for(let i = 1 ; i < arr.length ; i++){

    if(arr[i] > largest){
      largest = arr[i];
    }

    if(arr[i] < smallest){
      smallest = arr[i];
    }

  }

  console.log("largest", largest);
  console.log("smallest", smallest);
}

bigsmallValue([2,44,67,84,90,0]);
````

---

## Output

```js id="j3m8vq"
largest 90
smallest 0
```

---

# 2. With Method (`Math.max()` and `Math.min()`)

---

## Program

```js id="x5p2rk"
let arr = [2,44,67,84,90,0];

let largest = Math.max(...arr);
let smallest = Math.min(...arr);

console.log("largest", largest);
console.log("smallest", smallest);
```

---

## Output

```js id="w8n4qy"
largest 90
smallest 0
```

---


# Frequency Count in Array

## Program

```js
function countArray(arr){
  let obj = {};
  
  for(let ele of arr){
    obj[ele] = (obj[ele] || 0) + 1;
  }

  return obj;
}

console.log(countArray([1,2,2,3,1,1,4]));

```
## Output

  1: 3,
  2: 2,
  3: 1,
  4: 1
}
```
```
# Most Repeated Character Program

```js
function repeatedStr(str){

  let maxcount = 0;
  let maxchar = "";
  
  for(let i = 0 ; i < str.length ; i++){ // ek ek character check karti hi 
    
    let count = 0;

    for(let j = 0 ; j < str.length ; j++){ // pura string check karta hai

        if(str[i] === str[j]){
          count++;
        }
    }

    if(count > maxcount){
      maxcount = count;
      maxchar = str[i]
    }
  }

  return maxchar
}

console.log(repeatedStr("aabbddbbbbdedfddadudidod"))
````

# Output

```js
d
```


# Remove Special Characters from String

# Program Using Method

```js
function specialChar(str){
  return str.replace(/[^a-zA-Z0-9]/g,"")
}

console.log(specialChar("he@llo#12$3"))
````

---

# Output

```js
hello123
```

---

# Program Without Method

```js
function removeSpecialChar(str){

  let char = ""
  
  for(let i = 0 ; i < str.length ; i++){

    let ch = str[i];
    
    if(
      (ch >= "a" && ch <= "z") || 
      (ch >= "A" && ch <= "Z") ||
      (ch >= "0" && ch <= "9")
    )
    {
      char += ch
    }
  }

  return char
}

console.log(removeSpecialChar("he@llo#12$3"))
```

---

# Output

```js
hello123
```

# First Letter Capital of Every Word

# Program Using Method

```js
function firstCharUpperCase(str){

  return str
    .split(" ")// ["hello", "world"]
    .map(ele => ele.charAt(0).toUpperCase() + ele.slice(1))
    .join(" ")
}

console.log(firstCharUpperCase("hello world"));
````

---

# Output

```js
Hello World
```

---

# Program Without Method

```js
function firstCharUpperCase(str){

  let result = "";
  
  for(let i = 0 ; i < str.length ; i++){

    if(i === 0){
      result += str[i].toUpperCase();
    }
    else if(str[i - 1] === " "){
      result += str[i].toUpperCase();
    }
    else{
      result += str[i]
    }
  }

  return result
}

console.log(firstCharUpperCase("hello world"))
```

---

# Output

```js
Hello World
```

# Character Frequency in String

# Program Using Method

```js
function frequencyString(str){

  let count = {}
  
  str.split("").map((ele) => {

    count[ele] = (count[ele] || 0) + 1
  })

  return count;
}

console.log(frequencyString("abcdabfdee"))
````

---

# Output

```js
{
  a: 2,
  b: 2,
  c: 1,
  d: 2,
  f: 1,
  e: 2
}
```

# Program Without Method

```js
function frequencyStringCount(str){

  let obj = {};

  for(let i = 0 ; i < str.length ; i++){

    let ch = str[i]

    if(obj[ch]){
      obj[ch]++
    }
    else{
      obj[ch] = 1
    }
  }

  return obj
}

console.log(frequencyStringCount("abcdabfdee"))
```

---

# Output

```js
{
  a: 2,
  b: 2,
  c: 1,
  d: 2,
  f: 1,
  e: 2
}
```

# Longest Word in Sentence

```js
function longestString(str){

  let words = str.split(" ")
  let longsestWord = ""
  
  for(let word of words){

    if(word.length > longsestWord.length){
      longsestWord = word
    }
  }

  return longsestWord
}

console.log(longestString("I love javascript programming"))
````

---

# Output

```js
programming
```


# Count Spaces in String

# Program Without Method

```js
function spaceCount(str){

  let count = 0;

  for(let i = 0 ; i < str.length ; i++){

    if(str[i] === " "){
      count++
    }
  }

  return count;
}

console.log(spaceCount("I love javascript programming"))
````

---

# Output

```js
3
```

---

# Program Using Method

```js
function spaceCount(str){

  return str.split(" ").length - 1
}

console.log(spaceCount("I love javascript programming"))
```

---

# Output

```js
3
```

# Toggle Case in String

# Program

```js
function toggleCase(str){

  let result = "";

  for(let i = 0 ; i < str.length ; i++){

    let chr = str[i]

    if(chr === chr.toUpperCase()){
      result += chr.toLowerCase()
    }
    else{
      result += chr.toUpperCase()
    }
  }

  return result;
}

console.log(toggleCase("HeLlO"))
````

---

# Output

```js
hElLo
```

# Sort Array of Objects by ID

# Program

```js
const users = [
  { id: 3, name: "Rahul", age: 25 },
  { id: 1, name: "Amit", age: 20 },
  { id: 2, name: "Neha", age: 22 },
];

const result = users.sort((a, b) => a.id - b.id);

console.log(result);
```
---

# Output

```js
[
  { id: 1, name: "Amit", age: 20 },
  { id: 2, name: "Neha", age: 22 },
  { id: 3, name: "Rahul", age: 25 }
]
```

# 26. Object Key with Highest Value

```js id="d1f8g4"
const marks = { math: 70,english: 90,science: 80};

---
let maxKey = Object.keys(marks).reduce((a, b) => {
  return marks[a] > marks[b] ? a : b;
});

console.log(maxKey);
```

# Output

```js id="x7t4k9"
english
```
---

# Without Method (Easy Way)

```js id="c3y7u2"
const marks = {math: 70, english: 90,science: 80};

let max = 0;
let maxKey = "";

for (let key in marks) {
  if (marks[key] > max) {
    max = marks[key];
    maxKey = key;
  }
}

console.log(maxKey);
```
---
# Output

```js id="m6r1v8"
english
```

# 27. Convert Object to Array

```js id="n4k2x7"
const user = {
  name: "Rahul",
  age: 25
};
```

---

## Object.entries()

```js id="q7p5s1"
const result = Object.entries(user);

console.log(result);
```
---

# Output

```js id="u3h9e6"
[
  ["name", "Rahul"],
  ["age", 25]
]
```

---

# Without Method

```js id="f6m1w8"
const user = {
  name: "Rahul",
  age: 25
};

let result = [];

for (let key in user) {
  result.push([key, user[key]]);
}

console.log(result);
```

---

# Output

```js id="b2x7q5"
[
  ["name", "Rahul"],
  ["age", 25]
]
```

# Two Objects Equal or Not

## Method Way

```js id="o1x7k4"
const obj1 = {
  name: "Rahul"
};

const obj2 = {
  name: "Rahul"
};

const result = JSON.stringify(obj1) === JSON.stringify(obj2);
console.log(result);
```

---

# Output

```js id="r6m8v3"
true
```

---

# Without Method

```js id="g2w5p9"
const obj1 = {
  name: "Rahul",
  age: 25
};

const obj2 = {
  name: "Rahul",
  age: 25
};

let isEqual = true;

for (let key in obj1) {
  if (obj1[key] !== obj2[key]) {
    isEqual = false;
  }
}

console.log(isEqual);
```

---

# Output

```js id="l4t9x6"
true
```


# Remove Duplicate Words From Sentence

```js
const str = "hello world hello react react";

const result = [...new Set(str.split(" "))].join(" ");

console.log(result);
```

### Output

```js
hello world react
```
---

# ✅ Program Without Method (`Set`)


```js
function removeDuplicateword(str) {
  const splitWord = str.split(" "); // word main split karta hai means divide
  const result = [];

  for (let i = 0; i < splitWord.length; i++) {
    if (!result.includes(splitWord[i])) {
      result.push(splitWord[i]);
    }
  }

  return result.join(" ");
}

console.log(removeDuplicateword("hello world hello react react"));
```

### Output

```js
hello world react
```


# Count Vowels & Consonants

---

# ✅ Using Method (`includes()`)

```js id="ew6fwj"
function dataCount(str) {

  let vowel = 0;
  let constant = 0;

  let vowelStr = "aeiou";

  for (let char of str.toLowerCase()) {

    if (vowelStr.includes(char)) {
      vowel++;

    } else if (char >= "a" && char <= "z") {
      constant++;
    }
  }

  return { vowel, constant };
}

console.log(dataCount("hello"));
```

---

## Output

```js id="n20wdu"
{ vowel: 2, constant: 3 }
```

---

# ✅ Without Method (`includes`)

## Program

```js id="p04c7w"
function dataCount(str) {

  let vowel = 0;
  let constant = 0;

  for (let i = 0; i < str.length; i++) {

    let char = str[i].toLowerCase();

    if (char >= "a" && char <= "z") {

      if (
        char === "a" ||
        char === "e" ||
        char === "i" ||
        char === "o" ||
        char === "u"
      ) {
        vowel++;

      } else {
        constant++;
      }
    }
  }

  return { vowel, constant };
}

console.log(dataCount("hello"));
```

---

## Output

```js id="z2jlwm"
{ vowel: 2, constant: 3 }
```


# Star Pattern Printing
---

# ✅ Method Using `repeat()`

## Program

```js id="eg3gmq"
function starPattern(num){

  for(let i = 1; i <= num; i++){
    console.log("*".repeat(i));
  }

}

starPattern(5);
```

---

## Output

```js id="7gq0h4"
*
**
***
****
*****
```
---

# ✅ Without Method (`repeat`)

## Program

```js id="8r1t8q"
function starPattern(num){

  for(let i = 1; i <= num; i++){ // row

    let result = "";

    for(let j = 1; j <= i; j++){ // column
      result += "*";
    }

    console.log(result);
  }
}

starPattern(5);
```

---

## Output

```js id="c8n9p4"
*
**
***
****
*****
```

---

# ✅ Explanation

## Outer Loop (`i`)

```js id="vnrm2z"
for(let i = 1; i <= num; i++)
```

* Rows control karta hai
* Kitni lines print hongi decide karta hai

---

## Inner Loop (`j`)

```js id="5vfgrs"
for(let j = 1; j <= i; j++)
```

* Har row me kitne stars print honge decide karta hai

---

## `+=`

```js id="wrr1m7"
result += "*"
```

* String me ek-ek star add karta hai

---

# ✅ Easy Understanding

| Loop     | Work             |
| -------- | ---------------- |
| `i` loop | Rows             |
| `j` loop | Stars inside row |

---


# Number Pattern Printing

# ✅ Method Using `repeat()`

## Program

```js id="g9t6v4"
function starPattern(num){

  for(let i = 1; i <= num; i++){
    console.log((i + " ").repeat(i));
  }

}

starPattern(5);
```

---

## Output

```js id="a8u7q2"
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
```

# ✅ Without Method (`repeat`)

## Program

```js id="f5m9n1"
function starPattern(num){

  for(let i = 1; i <= num; i++){

    let result = "";

    for(let j = 1; j <= i; j++){

      result += (i + " ");

    }

    console.log(result);
  }
}

starPattern(5);
```

---

## Output

```js id="k7u3p5"
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
```

---

# ✅ Easy Understanding

| Loop     | Work               |
| -------- | ------------------ |
| `i` loop | Rows               |
| `j` loop | Numbers inside row |



# Remove Spaces in JavaScript

```js
let str = "Hello World";

let result = str.replace(/\s/g, "");

console.log(result);
```

## Output

```js
HelloWorld
```

# 2️⃣ Without Method (Manual Logic)

```js
let str = "Hello World";

let result = "";

for (let i = 0; i < str.length; i++) {
  if (str[i] !== " ") {
    result += str[i];
  }
}

console.log(result);
```

## Output

```js
HelloWorld
```

---

# Remove Spaces From Array Strings

```js
let arr = ["Hello ", " World"];

let result = arr.map((ele) => ele.trim());

console.log(result);
```

# Reverse Words in JavaScript

## Program

```js id="h7md3m"
let str = "Hello World JavaScript";

const result = str.split(" ").reverse().join(" ");

console.log(result);
```

---

## Output

```js id="d7kr6w"
JavaScript World Hello
```

---

## Program

```js id="6l9ny7"
function reverseWord(str) {
  let splitData = str.split(" ");

  let result = "";

  for (let i = splitData.length - 1; i >= 0; i--) {
    result += splitData[i] + " ";
  }

  return result;
}

console.log(reverseWord("Hello World JavaScript"));
```

---

## Output

```js id="nvcw70"
JavaScript World Hello
```



# Replace Characters / Words in JavaScript

---

## Program

```js id="p7l2kd"
const str = "hello world";

const result = str.replace("world", "everyone");

console.log(result);
```

---

## Output

```js id="x3q8vn"
hello everyone
```

---

# 2️⃣ Without Method

---

## Program

```js id="u5m9rt"
function replaceChar(str) {
  let result = "";

  let word = str.split(" ");

  for (let i = 0; i < word.length; i++) {
    if (word[i] === "world") {
      result += "everyone";
    } else {
      result += word[i] + " ";
    }
  }

  return result;
}

console.log(replaceChar("hello world"));
```

---

## Output

```js id="d8n4yk"
hello everyone
```


# Check Sorted Array

```
Ye sorted array hai because:

```js
1 < 2 < 3 < 4 < 5
```

---

# Program

```js
function checkSortedArray(arr){ 

  for(let i = 0 ; i < arr.length - 1 ; i++){

    if(arr[i] > arr[i+1]){

      return false

    }
  }

  return true
}

console.log(checkSortedArray([1,22,3,55,5]));
```

---

# Output

```js
false
```

---


# Merge Sorted Arrays

---

# With Method

```javascript id="jlwmfq"
let arr1 = [1,3,5]; 
let arr2 = [2,4,6];

let mergedSortedArray = arr1.concat(arr2).sort((a,b) => a - b);

console.log(mergedSortedArray);
```

## Output

```javascript id="3rfygi"
[1, 2, 3, 4, 5, 6]
```

---

# Without Method

```javascript id="td06qs"
function twoSortedArray(arr1, arr2){
  let result = [];
  
  for(let i = 0 ; i < arr1.length ; i++){
    result.push(arr1[i]);
  }
  
  for(let j = 0 ; j < arr2.length ; j++){
    result.push(arr2[j]);
  }
  
  // Sorting
  for(let i = 0 ; i < result.length ; i++){
    for(let j = i + 1 ; j < result.length ; j++){
      
      if(result[i] > result[j]){
        let temp = result[i];
        result[i] = result[j];
        result[j] = temp;
      }
      
    }
  }
  
  return result;
}

console.log(twoSortedArray([1,3,5],[2,4,6]));
```

## Output

```javascript id="33dgg0"
[1, 2, 3, 4, 5, 6]
```


# Method Chaining Calculator Program

## Definition

This program demonstrates the concept of **Method Chaining** in JavaScript.

Method chaining means calling multiple methods one after another on the same object using the dot (`.`) operator.
This is possible because each method returns the same object using:

```js
return this;
```

---

# Program

```js
function createCalc() {
  return {
    total: 0,

    add(num) {
      this.total += num;
      return this;
    },

    multiply(num) {
      this.total *= num;
      return this;
    },

    subtract(num) {
      this.total -= num;
      return this;
    }
  };
}

const calc = createCalc();

const result = calc
  .add(10)
  .multiply(5)
  .subtract(30)
  .add(10);

console.log(result.total);
```

---

# Output

```js
30
```

---

# Why `return this` is Used?

```js
return this;
```

returns the current object again.
Because of this, we can write:

```js
calc.add(10).multiply(5).subtract(30)
```

without creating separate variables.

---

# What is `this`?

Inside object methods:

```js
this
```

refers to the current object.

So:

```js
this.total
```

means:

```js
calc.total
```

---

# Method Chaining

Method chaining means:

```js
object.method1().method2().method3()
```

Each method returns the same object so the next method can be called immediately.

---

## Array Methods

```js
arr.filter().map().sort()
```

---

## Express.js

```js
res.status(200).json(data)
```
---

# Important Interview Point

This pattern is called:

## Fluent Interface / Method Chaining

Used to perform multiple operations on the same object in a clean and readable way.

---

# Final Summary

* `this` refers to current object
* `return this` returns same object
* Returning object enables chaining
* Multiple methods can run in one statement



# Merge Sort basic

---

# Program

```js
function mergeSort(arr){
  for(let i = 0 ; i < arr.length ; i++){

    for(let j = i + 1 ; j < arr.length ; j++){

      if(arr[i] > arr[j]){

        let temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
      }
    }
  }

  return arr;
}

console.log(mergeSort([5, 33, 8, 1]));
```

---

# Output

```js
[1, 5, 8, 33]
```


# Maximum Subarray Sum

* Array ke andar continuous numbers ka sabse bada sum find karne ke liye.

---

# Program

```js id="4twnby"
function maxSumArray(arr){

  let maxSum = arr[0];
  let currSum = arr[0];
  
  for(let i = 1 ; i < arr.length ; i++){

    currSum = Math.max(arr[i],currSum + arr[i]);

    maxSum = Math.max(currSum,maxSum);
  }

  return maxSum;
}

console.log(
  maxSumArray([-2,1,-3,4,-1,2,1,-5,4])
);
```

---

# Output

```js id="jjlwm2"
6
```


# Bubble Sort

---

```js id="3a1n7p"
function bubbleSort(arr){

  for(let i = 0 ; i < arr.length ; i++){

    for(let j = 0 ; j < arr.length - 1 ; j++){ // j+1 se kar rahe so arr.length-1 le rahe hai

      if(arr[j] > arr[j + 1]){

        // Swap
        let temp = arr[j];

        arr[j] = arr[j + 1];

        arr[j + 1] = temp;
      }
    }
  }

  return arr;
}

console.log(
  bubbleSort([5,3,8,1])
);
```

---

# Output

```js id="qg6m6v"
[1, 3, 5, 8]
```

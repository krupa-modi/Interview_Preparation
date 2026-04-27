
# Reverse a String in JavaScript

## ✅ Using Method (Built-in Functions)

//using function
function reverseString(str) {
  return str.split('').reverse().join('');
}

// Example
console.log(reverseString("hello")); // "olleh"

const string = "hello javascript"
const output = string.split("").reverse().join("")
console.log("output",output) // tpircsavaj olleh


// Dame space reverse
const string = "hello javascript";
const output = string.split(" ").map(ele =>ele.split("").reverse().join("")).join(" ")
console.log("output",output) // olleh tpircsavaj

## ✅ Without Using Method (Manual Approach)

// using function

function reverseString(str) {
  let reversed = "";

  for (let i = str.length - 1; i >= 0; i--) {
    reversed += str[i];
  }

  return reversed;
}

// Example
console.log(reverseString("hello")); // "olleh"


// using loop
let string = "hello javascript";
let result = "";
for(i = string.length - 1 ; i >= 0 ; i--){
  result += string[i]
}
console.log("reverse string" , result)// tpircsavaj olleh



* **Method approach** is quick and readable.
* **Manual approach** shows your understanding of loops and string handling (preferred in interviews).

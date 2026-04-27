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

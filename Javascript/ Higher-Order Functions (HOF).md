## What is a Higher-Order Function?

A **Higher-Order Function (HOF)** is a function that:

1. **Takes another function as an argument**, OR
2. **Returns another function**

JavaScript main functions ko first-class citizens treat karta hai, iska matlab:

- Function ko variable me store kar sakte ho
- Function ko argument me pass kar sakte ho
- Function ko return kar sakte ho

Isi wajah se Higher-Order Functions possible hote hain.

---

# Simple Definition

```js
A function that works with another function is called a Higher-Order Function.
````

---

# Why Higher-Order Functions are Important?

* Functional programming understanding
* Clean coding style
* Reusability
* Code optimization
* JavaScript fundamentals strong hain ya nahi

---

# Example 1 — Function as Argument

```js
function greet(name) {
  return "Hello " + name;
}

function processUser(callback) {
  console.log(callback("Krupa"));
}

processUser(greet);
```

## Output

```js
Hello Krupa
```

---

# Explanation

### Step 1

```js
function greet(name)
```

Ye ek normal function hai.

---

### Step 2

```js
function processUser(callback)
```

Ye function dusre function ko receive kar raha hai.

Isliye:

```js
processUser
```

is a **Higher-Order Function**

---

### Step 3

```js
processUser(greet);
```

Hum `greet` function pass kar rahe hain.

---

# Example 2 — Function Returning Another Function

```js
function multiplyBy(num) {
  return function (x) {
    return x * num;
  };
}

const double = multiplyBy(2);

console.log(double(5));
```

## Output

```js
10
```

---

# Explanation

### Step 1

```js
multiplyBy(2)
```

Ye ek function return karta hai.

---

### Step 2

Returned function:

```js
function (x) {
   return x * num;
}
```

---

### Step 3

```js
double(5)
```

Actually ye run hota hai:

```js
5 * 2
```

Output:

```js
10
```

---

# Real-Life Analogy

Socho:

```js
Swiggy(orderFunction)
```

Swiggy khud ek system hai jo dusri function ko use karta hai.

Example:

* Payment function
* Delivery function
* Notification function

Ye sab callback functions hote hain.

---

# Callback Function vs Higher-Order Function

Bahot important interview question.

---

## Callback Function

Jo function argument ke roop me pass hota hai.

```js
function greet() {
   console.log("Hello");
}

setTimeout(greet, 2000);
```

Yaha:

```js
greet
```

is callback function.

---

## Higher-Order Function

Jo callback ko receive karta hai.

```js
setTimeout(greet, 2000);
```

Yaha:

```js
setTimeout
```

is Higher-Order Function.

---

# Most Important HOFs in JavaScript

Interview me mostly ye puchte hain:

| Method    | Purpose                |
| --------- | ---------------------- |
| map()     | Transform array        |
| filter()  | Filter values          |
| reduce()  | Reduce to single value |
| forEach() | Iterate array          |
| sort()    | Sorting                |
| find()    | Find first element     |
| some()    | Check condition        |
| every()   | Check all conditions   |

---

# Custom Higher-Order Function

Interview me kabhi custom HOF banane ko bol sakte hain.

---

## Example

```js
function calculator(a, b, callback(give any name)) {
  return callback(a, b);
}

function add(x, y) {
  return x + y;
}

function multiply(x, y) {
  return x * y;
}

console.log(calculator(2, 3, add));
console.log(calculator(2, 3, multiply));
```

## Output

```js
5
6
```

---

# Explanation

`calculator()` ek HOF hai because:

* Function receive kar raha hai
* Dynamic behavior provide kar raha hai

---



```js
Every callback-based function is usually a Higher-Order Function.
```

---

# HOFs Used in React

React me bahot jagah HOFs use hote hain:

* map()
* Event handlers
* Custom hooks
* HOCs (Higher-Order Components)

## HOF always:

✅ Takes function as argument
OR
✅ Returns function


# Common Mistakes

## Mistake 1

```js
processUser(greet());
```

Wrong in many cases.

Because:

```js
greet()
```

immediately execute ho jayega.

Correct:

```js
processUser(greet);
```

---

# Mistake 2

Confusing callback with HOF.

Remember:

| Callback        | HOF               |
| --------------- | ----------------- |
| Passed function | Receiver function |

---

# Memory Trick

```js
Function inside function = Higher-Order Function concept
```

---

# Final Interview Definition

```js
A Higher-Order Function is a function that accepts another function as an argument or returns a function. JavaScript supports this because functions are first-class citizens.
```


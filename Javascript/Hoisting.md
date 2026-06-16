
# Hoisting in JavaScript

## What is Hoisting?

Hoisting is JavaScript's default behavior of **moving declarations to the top of their scope** during the memory creation phase.
Hoisting means JavaScript moves variable and function declarations to the top of their scope before execution.

Note:- function expression and class expression is not hoisting.
Example:- var greet = function(){
console.log("hello")
}
 Note:- this is the function expression using = and variable

---

## How it Works

Before execution, JS engine:

1. Allocates memory
2. Stores variables & functions

---

## Example

```js
console.log(a); // undefined
var a = 10;
```

👉 Internally:

```js
var a; // Declaration
console.log(a); // undefined
a = 10; // Assignment / Execution
```

---

## let & const (Temporal Dead Zone)

Temporal Dead Zone (TDZ)
* The time between variable hoisting and variable initialization is called Temporal Dead Zone.

```js
console.log(a); // ReferenceError
let a = 10;
```

👉 They are hoisted but **not initialized** → TDZ

---

## Function Hoisting

```js
greet(); // Works

function greet() {
  console.log("Hello");
}
```

👉 Function declarations are fully hoisted

---

## Key Points

* `var` → hoisted (initialized with undefined)
* `let/const` → hoisted but in TDZ
* Functions → fully hoisted

* In hoisting, only declarations are hoisted, not assignments or execution. Variables declared with var are initialized as undefined during the memory creation phase, while the actual value assignment happens later during execution.

# Declaration vs Initialization vs Assignment vs Execution

# 1. Declaration

Variable banana (create karna) ko declaration bolte hai.

## Example

```js
var a;
````

Yaha:

* `a` variable declare hua hai
* Value abhi nahi di

---

# 2. Initialization

Variable ko first time value dena initialization hota hai.

## Example

```js
var a = 10;
```

Yaha:

```js
a = 10
```

first value assign hui → initialization

---

# 3. Assignment

Already existing variable ki value change karna assignment hota hai.

## Example

```js
var a = 10;

a = 20;
```

Yaha:

```js
a = 20
```

assignment hai.

---

# 4. Execution

Code run hona execution hota hai.

## Example

```js
console.log("Hello");
```

Browser is line ko run karega.

---

# Full Example

```js
var a;       // Declaration
a = 10;      // Initialization
a = 20;      // Assignment
console.log(a); // Execution
```

---

# Output

```js
20
```
---

Aap bol rahe ho:

```js
console.log(a);

var a = 10;
```

Agar:

```js
console.log(a)
```

pehle execute ho raha hai,

to declaration upar kaise gaya?

---

# Actual Reality

JavaScript code ko:

```text id="6jlwm1"
2 phases
```

me chalata hai.

---

# 1. Memory Creation Phase

Pehle sirf memory allocate hoti hai.

Execution nahi hota.

---

# 2. Execution Phase

Fir line-by-line code execute hota hai.

---

# Important Thing

Hoisting me:

```text id="7jlwm2"
Sirf declaration upar jata hai
```

NOT assignment.

---

# Example

```js id="8jlwm3"
console.log(a);

var a = 10;
```

---

# Memory Creation Phase

JavaScript internally karta hai:

```js id="9jlwm4"
var a = undefined;
```

So memory me:

```js id="0jlwm5"
a → undefined
```

---

# Execution Phase Starts

Now actual code runs line by line.

---

# Line 1

```js id="1jlwm6"
console.log(a);
```

At this moment:

```js id="2jlwm7"
a = undefined
```

So output:

```js id="3jlwm8"
undefined
```

---

# Line 2

```js id="4’wini9"
a = 10;
```

Now value update:

```js id="5jlwm0"
a = 10
```

---

# Important Understanding

JavaScript internally aise treat karta hai:

```js id="6’wini1"
var a;

console.log(a);

a = 10;
```

---

# Variable Declaration vs Initialization

## Declaration

```js id="7’wini2"
var a;
```

---

## Initialization / Assignment

```js id="8’wini3"
a = 10;
```

---

# Hoisting Me Kya Hota Hai?

Only:

```js id="9’wini4"
var a;
```

upar jata hai.

NOT:

```js id="0’wini5"
a = 10;
```

---

# Same for Functions

## Function Declaration

```js id="1’wini6"
hello();

function hello(){
  console.log("Hi");
}
```

Works ✅

---

# Why?

Memory phase me pura function store ho jata hai.

Internally:

```js id="2’wini7"
function hello(){
  console.log("Hi");
}

hello();
```

---

# Function Declaration Fully Hoist Hota Hai

Variables:

```text id="3’wini8"
Only declaration hoist
```

Functions:

```text id="4’wini9"
Complete function hoist
```

---

# Easy Memory Trick

# Variables (`var`)

```text id="5’wini0"
Name upar jata hai
Value nahi
```

---

# Functions

```text id="6’wini1"
Pura function upar jata hai
```

---

# Final Easy Definition

Hoisting means during the memory creation phase, JavaScript stores variable and function declarations in memory before executing the code.



# Why are Function and Variable Declarations Moved to the Top? (Hoisting)

## Answer

In JavaScript, function and variable declarations appear to be moved to the top of their scope before the code executes. This behavior is called **Hoisting**.

Hoisting is JavaScript's default behavior during the **Creation Phase** of the Execution Context, where memory is allocated for variables and functions before code execution starts.

## Why Does Hoisting Exist?

JavaScript first scans the code and allocates memory for variables and functions before executing it. This allows functions to be called before their declaration and helps JavaScript manage memory and execution efficiently.

---

## Interview Answer (Short)

Function and variable declarations are moved to the top of their scope because of JavaScript's hoisting behavior. During the creation phase, JavaScript allocates memory for variables and functions before executing the code. Function declarations are fully hoisted, while `var` variables are hoisted with an initial value of `undefined`. `let` and `const` are also hoisted but remain in the Temporal Dead Zone until their declaration is executed.

### One-Line Interview Answer

> Function and variable declarations are "moved to the top" due to hoisting. During the creation phase, JavaScript allocates memory for them before code execution begins, allowing functions to be called before they are declared and `var` variables to be accessed as `undefined`.



# What is the Purpose of Hoisting?

## Answer

The purpose of **Hoisting** is to allow JavaScript to allocate memory for variables and functions before the code starts executing.

During the **Creation Phase** of the Execution Context, JavaScript scans the code and stores function and variable declarations in memory. This helps JavaScript know what identifiers exist before execution begins.

---

## Benefits of Hoisting

### 1. Functions Can Be Called Before Declaration

```javascript
greet();

function greet() {
  console.log("Hello");
}
```

Output:

```javascript
Hello
```

---

### 2. Memory Allocation Before Execution

JavaScript creates memory for variables and functions before running the code.

```javascript
console.log(a);

var a = 10;
```

Output:

```javascript
undefined
```

Because memory was already allocated for `a`.

---

## Interview Answer (Short)

The purpose of hoisting is to allocate memory for variables and functions before code execution begins. During the creation phase, JavaScript scans the code and stores declarations in memory, allowing function declarations to be called before they appear in the code and enabling JavaScript to create the execution context efficiently.

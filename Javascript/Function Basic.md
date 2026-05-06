
# 1. What is Function Statement?

Function Statement means defining a function directly using the `function` keyword.

👉 It is also called **Function Declaration**.

---

## 🔍 Syntax

```js id="x8r2mk"
function greet() {
  console.log("Hello");
}
```

👉 Here:

* `greet` = function name
* Function created directly

---

# 🔥 Characteristics of Function Statement

* Fully hoisted ✅
* Can call before declaration ✅
* Reusable

---

## 🔍 Example

```js id="s4w7zn"
sayHello();

function sayHello() {
  console.log("Hello");
}
```

👉 Output:

```js id="k1v8xp"
Hello
```

✅ Works because function statement is fully hoisted.

---

# 2. What is Function Expression?

Function Expression means storing a function inside a variable.

---

## 🔍 Syntax

```js id="y3m6rt"
const greet = function () {
  console.log("Hello");
};
```

👉 Here:

* Function assigned to variable
* Function may be anonymous or named

---

# 🔥 Characteristics of Function Expression

* NOT fully hoisted ❌
* Cannot call before initialization ❌
* Behaves like variable

---

## 🔍 Example

```js id="p9t2qw"
sayHello();

const sayHello = function () {
  console.log("Hello");
};
```

👉 Output:

```js id="r5z8yn"
ReferenceError
```

❌ Because function assignment happens later.

---

# 3. Hoisting Difference (VERY IMPORTANT 🔥)

---

## ✅ Function Statement

```js id="g7x2ms"
greet();

function greet() {
  console.log("Hi");
}
```

👉 During memory creation:

```text id="k4v9tp"
greet → complete function stored
```

---

## ❌ Function Expression

```js id="j3w6nm"
greet();

var greet = function () {
  console.log("Hi");
};
```

👉 During memory creation:

```text id="n2x8ql"
greet → undefined
```

❌ Function body not stored initially.

---

# 4. Visual Difference

---

## Function Statement

```js id="v7m4qs"
function add(a, b) {
  return a + b;
}
```

---

## Function Expression

```js id="t8z3pr"
const add = function(a, b) {
  return a + b;
};
```


# 6. Real-World Usage

---

## Function Statement

Used for:

* Utility functions
* Reusable logic

```js id="n5r1wx"
function calculateTotal() {}
```

---

## Function Expression

Used for:

* Event handlers
* React callbacks
* Closures

```js id="d6q2vt"
const handleClick = function () {};
```

# 🎯 Final Interview Answer

👉 Function Statement directly declares a function and is fully hoisted.
👉 Function Expression stores a function inside a variable and is not fully hoisted.

---

# 💡 Pro Tip for Interview

Say this 👇

👉 “Function expressions behave like variables during hoisting, while function statements are completely hoisted with their function body.” 🚀

---

# 3. What is Named Function Expression?

A Named Function Expression is a function expression where the function has its own name.

👉 Function is assigned to a variable AND also has an internal function name.

---

# 🔍 Syntax

```js id="x8q2nm"
const greet = function sayHello() {
  console.log("Hello");
};
```

👉 Here:

* `greet` → variable name
* `sayHello` → function name

---

# 2. Why is it Called Function Expression?

Because function is stored inside a variable.

```js id="k4m7zp"
const greet = ...
```

👉 Hence:
✅ Function Expression

---

# 3. Why “Named”?

Because function itself has a name:

```js id="m2r9vx"
function sayHello()
```

👉 So this becomes:
✅ Named Function Expression

---

# 4. How It Works

```js id="w5q8nt"
const greet = function sayHello() {
  console.log("Hello");
};

greet();
```

👉 Output:

```js id="j1z4py"
Hello
```

---

# 5. Important Interview Point 🔥

👉 The internal function name:

```js id="q9m3vr"
sayHello
```

is ONLY accessible inside the function itself.

---

# 🔍 Example

```js id="s7x2kp"
const greet = function sayHello() {
  console.log(sayHello);
};

greet();
```

👉 Works inside function.

---

## ❌ Outside Access

```js id="n4v8qw"
sayHello();
```

👉 Output:

```js id="r6m2tz"
ReferenceError
```

❌ Because `sayHello` is not available globally.


# 🔍 Anonymous Function Expression

An Anonymous Function is a function without a name.

```
👉 Normal function:

function greet() {
  console.log("Hello");
}

👉 Anonymous function:

function () {
  console.log("Hello");
}

❗ No function name here.

```

```
2. Why Use Anonymous Functions?


Anonymous functions are mainly used:

* As callback functions
* Inside event handlers
* In higher-order functions
* In IIFE

```

👉 Useful when function is needed only once.

```js id="p2w7zx"
const greet = function () {
  console.log("Hello");
};
```

---

# 🔍 Named Function Expression

```js id="f5m9qt"
const greet = function sayHello() {
  console.log("Hello");
};
```

---

# 7. Advantage of Named Function Expression

## ✅ Better Debugging

👉 Error stack traces show function name.

---

## ✅ Useful in Recursion

```js id="z8x3vn"
const factorial = function fact(n) {
  if (n === 1) return 1;

  return n * fact(n - 1);
};
```

👉 Internal function name helps recursion.

---

# 8. Hoisting Behavior

Named Function Expression behaves like normal function expression.

---

## ❌ Example

```js id="d3q7wm"
greet();

const greet = function sayHello() {
  console.log("Hello");
};
```

👉 Output:

```js id="v2m8yr"
ReferenceError
```

❌ Not fully hoisted.

---

# 9. Real-World Usage

Used for:

* Recursion
* Better debugging
* Complex callbacks

---

# 🎯 Final Interview Answer

👉 Named Function Expression is a function expression where the function has its own name.
👉 The function name is accessible only inside the function and helps in debugging and recursion.


# 🔥 Difference Between Function Parameters and Function Arguments in JavaScript

---

# 1. What are Function Parameters?

👉 Parameters are the variables listed in the function definition.

They act as placeholders to receive values.

---

## 🔍 Example

```js id="k3x9pa"
function greet(name) {
  console.log(name);
}
```

👉 Here:

```js id="g7m2qo"
name
```

is a **parameter**.

---

# 🔥 Key Points of Parameters

* Defined while creating function
* Placeholder variables
* Receive values later

---

# 4. What are Function Arguments?

👉 Arguments are the actual values passed to the function when calling it.

---

## 🔍 Example

```js id="j8v4tp"
greet("Krupa");
```

👉 Here:

```js id="x9n1qz"
"Krupa"
```

is an **argument**.

---

# 🔥 Full Example

```js id="r6d3pk"
function add(a, b) {
  console.log(a + b);
}

add(10, 20);
```

---

## 👉 Parameters:

```js id="m5z8qx"
a, b
```

---

## 👉 Arguments:

```js id="v2w9nl"
10, 20
```

---

# 🔥 Easy Analogy

👉 Parameters = Empty boxes 📦
👉 Arguments = Actual items placed inside boxes 🎁

---

# 3. Difference Between Parameters and Arguments

| Feature | Parameters          | Arguments     |
| ------- | ------------------- | ------------- |
| Defined | Function definition | Function call |
| Purpose | Receive values      | Pass values   |
| Type    | Variables           | Actual values |

---

# 🔥 Example with Multiple Arguments

```js id="c8p2xr"
function multiply(x, y) {
  return x * y;
}

multiply(5, 4);
```

---

## 👉 Parameters:

```js id="e4m6ty"
x, y
```

---

## 👉 Arguments:

```js id="y1n7zp"
5, 4
```

---

# 4. Default Parameters

```js id="q7r3mv"
function greet(name = "Guest") {
  console.log(name);
}

greet();
```

👉 Output:

```js id="b2v8qn"
Guest
```

---

# 5. Extra Arguments

```js id="d4n9zt"
function test(a, b) {
  console.log(a, b);
}

test(1, 2, 3, 4);
```

👉 Output:

```js id="k6p5xr"
1 2
```

👉 Extra arguments ignored (normally).

---

# 6. Missing Arguments

```js id="v9m3pw"
function test(a, b) {
  console.log(a, b);
}

test(1);
```

👉 Output:

```js id="u2z8tn"
1 undefined
```

## 👉 Are parameters and arguments same?

❌ No

* Parameters → variables in function definition
* Arguments → actual values passed during function call

---

# 🎯 Final Interview Answer

👉 Parameters are variables defined in the function declaration to receive values.
👉 Arguments are the actual values passed to the function during function call.

---

# 💡 Pro Tip for Interview

Say this 👇

👉 “Parameters are placeholders, arguments are real values supplied to those placeholders.” 🚀



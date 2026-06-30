# Program

for(var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
---
# Output

```js id="3v8kpn"
3
3
3
```

---

# Why Output is 3 3 3 ?

## Step 1

Loop start hua:

```js id="5t1zlw"
for(var i = 0; i < 3; i++)
```

`var` function scoped hota hai.
Matlab pura loop ek hi `i` variable share karta hai.

---

# Step 2

Loop fast execute ho jata hai

Values:

```js id="0j7ycv"
i = 0
i = 1
i = 2
```

Loop finish hone ke baad:

```js id="8n2dfr"
i = 3
```

---

# Step 3

`setTimeout` callback immediately execute nahi hota.

Ye 1 second baad chalega:

```js id="7m4xqs"
setTimeout(() => console.log(i), 1000);
```

Tab tak loop complete ho chuka hota hai.

---

# Step 4

Ab callback run hua.

Sab callbacks same `i` variable ko access karte hai.

Current value:

```js id="2p6vka"
i = 3
```

Isliye output:

```js id="1w8lry"
3
3
3
```

---

# Important Point

```js id="0f3qws"
var = function scope
```

Sab callbacks same variable reference use kar rahe hai.

---

# Agar let use kare to?

```js id="5q7nmd"
for(let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
```

## Output

```js id="8k2vpl"
0
1
2
```

Because:

```js id="9z4xhc"
let = block scope
```

Har iteration ka alag `i` banta hai.


# Program

const obj = {
  name: "JS",

  getName: () => console.log(this.name)
}

obj.getName()

---

# Output

```js id="7n2vka"
undefined
```
# Explanation

## Arrow Function ka `this`

Arrow function apna khud ka `this` nahi banata.

Ye parent scope ka `this` use karta hai.

---

# Yaha kya hua?

```js id="1m5zqr"
getName: () => console.log(this.name)
```

Ye arrow function hai.

To iska `this` object (`obj`) ko point nahi karega.

---

# Current `this`

Browser me:

```js id="8p3xlu"
this = window
```

Node.js me:

```js id="0v7kds"
this = {}
```

---

# Check

```js id="6y2nfh"
window.name
```

Ya

```js id="4t9qwe"
{}.name
```

Dono me `name` nahi hai.

Isliye:

```js id="2j8vpc"
undefined
```

print hota hai.

---

# Correct Way

```js id="5r1xzn"
const obj = {
  name: "JS",

  getName() {
    console.log(this.name)
  }
}

obj.getName()
```

---

# Correct Output

```js id="9k4mqt"
JS
```

Because normal function me:

```js id="8c1vpy"
this = current object
```

Yani:

```js id="7f3xld"
obj
```

# JavaScript Trick Questions For Interview

---

# 1. typeof null

```js
console.log(typeof null)
```

## Output

```js
object
```

## Why?

JavaScript ka old bug hai.  
`null` ka type actually object show hota hai.

---

# 2. [] == false

```js
console.log([] == false)
```

## Output

```js
true
```

## Why?

Loose equality (`==`) type conversion karta hai.

```js
[] -> ""
"" -> 0
false -> 0
```

Isliye:
```js
0 == 0
```

---

# 3. {} + []

```js
console.log({} + [])
```

## Output

```js
0
```

---

# 4. NaN === NaN

```js
console.log(NaN === NaN)
```

## Output

```js
false
```

## Why?

`NaN` kabhi bhi kisi ke equal nahi hota, even khud ke bhi nahi.

Correct check:
```js
console.log(isNaN(NaN))
```

Output:
```js
true
```

---

# 5. var vs let in loop

```js
for(var i=0;i<3;i++){
 setTimeout(()=>console.log(i),1000)
}
```

## Output

```js
3
3
3
```

Because `var` function scoped hota hai.

---

```js
for(let i=0;i<3;i++){
 setTimeout(()=>console.log(i),1000)
}
```

## Output

```js
0
1
2
```

Because `let` block scoped hota hai.

---

# 6. Addition with String

```js
console.log(1 + "2" + 3)
```

## Output

```js
123
```

## Why?

String aate hi sab string ban jata hai.

---

# 7. true + true

```js
console.log(true + true)
```

## Output

```js
2
```

## Why?

```js
true = 1
```

So:
```js
1 + 1 = 2
```

---

# 8. Empty Array Truthy

```js
if([]){
 console.log("Hello")
}
```

## Output

```js
Hello
```

## Why?

Empty array truthy hota hai.

---

# 9. 0.1 + 0.2

```js
console.log(0.1 + 0.2)
```

## Output

```js
0.30000000000000004
```

## Why?

Floating point precision issue.

---

# 10. parseInt with map

```js
console.log(["1","2","3"].map(parseInt))
```

## Output

```js
[1, NaN, NaN]
```

## Why?

`map` second parameter index bhejta hai.

Actually:
```js
parseInt("1",0)
parseInt("2",1)
parseInt("3",2)
```

---

# 11. this in Arrow Function

```js
const obj = {
 name:"JS",
 getName:()=>console.log(this.name)
}

obj.getName()
```

## Output

```js
undefined
```

Because arrow function apna `this` nahi banata.

---

# 12. typeof NaN

```js
console.log(typeof NaN)
```

## Output

```js
number
```

---

# 13. Boolean of Empty String

```js
console.log(Boolean(""))
```

## Output

```js
false
```

---

# 14. Boolean of Empty Array

```js
console.log(Boolean([]))
```

## Output

```js
true
```

---

# 15. Double Equals vs Triple Equals

```js
console.log(5 == "5")
```

## Output

```js
true
```

Because type conversion hota hai.

---

```js
console.log(5 === "5")
```

## Output

```js
false
```
# JavaScript Type Conversion Tricks

---

# 1. parseInt()

## Definition

`parseInt()` string ko integer number me convert karta hai. and type of number ayega

---

## Example

```js
console.log(parseInt("123"))
```

## Output

```js
123
```

---

## Example 2

```js
console.log(parseInt("123abc"))
```

## Output

```js
123
```

---

## Example 3

```js
console.log(parseInt("abc123"))
```

## Output

```js
NaN
```

---

# 2. Number()

## Definition

`Number()` kisi value ko pure number me convert karta hai.

---

## Example

```js
console.log(Number("10"))
```

## Output

```js
10
```

---

## Example

```js
console.log(Number(true))
```

## Output

```js
1
```

---

## Example

```js
console.log(Number(false))
```

## Output

```js
0
```

---

# 3. String()

## Definition

`String()` kisi bhi value ko string me convert karta hai.

---

## Example

```js
console.log(String(100))
```

## Output

```js
"100"
```

---

# 4. Boolean()

## Definition

`Boolean()` value ko true ya false me convert karta hai.

---

## Example

```js
console.log(Boolean(1))
```

## Output

```js
true
```

---

## Example

```js
console.log(Boolean(0))
```

## Output

```js
false
```

---

# 5. Unary Plus (+)

## Definition

Single `+` value ko number me convert karta hai.

---

## Example

```js
console.log(+"10")
```

## Output

```js
10
```

---

## Example

```js
console.log(+true)
```

## Output

```js
1
```

---

## Example

```js
console.log(+"")
```

## Output

```js
0
```

---

# 6. Empty Array Conversion

## Example

```js
console.log([])
```

## Output

```js
[]
```

---

## String Conversion

```js
console.log(String([]))
```

## Output

```js
""
```

Empty array empty string me convert hota hai.

---

# 7. Empty Object Conversion

## Example

```js
console.log(String({}))
```

## Output

```js
"[object Object]"
```

---

# 8. [] == false

## Example

```js
console.log([] == false)
```

## Output

```js
true
```

---

## Why?

```js
[] -> ""
"" -> 0
false -> 0
```

Final:
```js
0 == 0
```

---

# 9. {} + []

## Example

```js
console.log({} + [])
```

## Output

```js
0
```

---

## Why?

```js
[] -> ""
+""
```

Final:
```js
0
```

---

# 10. Plus (+) Operator Uses

# A. Addition

```js
console.log(10 + 20)
```

## Output

```js
30
```

---

# B. String Join

```js
console.log("Hello" + " JS")
```

## Output

```js
Hello JS
```

---

# C. Number Conversion

```js
console.log(+"50") //50

console.log(+"hello") // NaN
```

## Output

```js
50
```

---

# 11. true and false Conversion

```js
true = 1
false = 0
```

---

## Example

```js
console.log(true + true)
```

## Output

```js
2
```

---

# 12. null Conversion

```js
console.log(Number(null))
```

## Output

```js
0
```

---

# 13. undefined Conversion

```js
console.log(Number(undefined))
```

## Output

```js
NaN
```
# 14 prototype 
```
function User() {}

const user1 = new User();

console.log(user1.__proto__ === User.prototype); // true
```

---

# 1. NaN === NaN

```js
console.log(NaN === NaN);
````

## Output

```js
false
```

## Explanation

`NaN` means **Not a Number**.

In JavaScript:

* `NaN` is not equal to anything
* Even `NaN` is not equal to itself

```js
NaN === NaN // false
```

This behavior comes from IEEE floating-point rules.

---

## Correct Way to Check NaN

Use:

```js
Number.isNaN(value)
```

## Example

```js
Number.isNaN(NaN) // true
```

---

# 2. 1 < 2 < 3

```js
console.log(1 < 2 < 3);
```

## Output

```js
true
```

## Step-by-Step Evaluation

JavaScript evaluates expressions from **left to right**.

---

### Step 1

```js
1 < 2
```

Result:

```js
true
```

---

### Step 2

```js
true < 3
```

JavaScript converts:

```js
true → 1
```

Now expression becomes:

```js
1 < 3
```

Result:

```js
true
```

---

## Final Output

```js
true
```

---

# 3. 3 > 2 > 1

```js
console.log(3 > 2 > 1);
```

## Output

```js
false
```

## Step-by-Step Evaluation

---

### Step 1

```js
3 > 2
```

Result:

```js
true
```

---

### Step 2

```js
true > 1
```

JavaScript converts:

```js
true → 1
```

Now expression becomes:

```js
1 > 1
```

Result:

```js
false
```

---

## Final Output

```js
false
```

---

# Quick Interview Trick

## Boolean Conversion in Comparison

```js
true  → 1
false → 0
```

Example:

```js
true < 3   // 1 < 3  → true
false < 1  // 0 < 1  → true
```

---

# Important Interview Point

Expressions like:

```js
1 < 2 < 3
3 > 2 > 1
```

## 1.
```js
let a = null
let b = null

let c = a + b
console.log(c)
```

### Output:
```js
0
```

### Why?
`null` is converted to `0` in numeric operations.

---

## 2.
```js
typeof "5 " === " 5"
```

### Output:
```js
false
```

### Why?
`typeof "5 "` returns `"string"` not `" 5"`.

---

## 3.
```js
for(;;) {
  console.log("Loop")
}
```

### Output:
```js
Infinite Loop
```

### Why?
No condition is given, so it always remains `true`.

---

## 4.
```js
console.log(typeof function(){});
```

### Output:
```js
function
```

### Why?
Functions have special type `"function"` in JavaScript.

---

## 5.
```js
console.log(typeof function(){}());
```

### Output:
```js
undefined
```

### Why?
Function executes immediately and returns nothing, so default return is `undefined`.

---

## 6.
```js
console.log(..."Hello");
```

### Output:
```js
H e l l o
```

### Why?
Spread operator breaks string into individual characters.

---

## 7.
```js
console.log(parseInt("10px"));
```

### Output:
```js
10
```

### Why?
`parseInt()` reads numbers until a non-number character appears.

---

## 8.
```js
console.log([] == false);
```

### Output:
```js
true
```

### Why?
`[]` converts to empty string `""` and `false` converts to `0`.  
Both become `0`.

---

## 9.
```js
async function foo() {
    return "Hello";
}

console.log(foo());
```

### Output:
```js
Promise { 'Hello' }
```

### Why?
`async` function always returns a Promise.


# 1. Output of

```js
{ "a": "b" } === { "c": "d" }
```

## Answer

```js
false
```

## Why?

Objects compare by **reference**, not by value.

Both objects are different memory locations.

Example:

```js
const obj1 = { a: "b" };
const obj2 = { c: "d" };

console.log(obj1 === obj2);
```

Even though both are objects, references are different.

---

# 2. Result of

```js
typeof { "a": "Hey" } === typeof ["a", "Hey"]
```

## Answer

```js
true
```

---

# Why?

## Object Type

```js
typeof { "a": "Hey" }
```

Output:

```js
"object"
```

---

## Array Type

```js
typeof ["a", "Hey"]
```

Output:

```js
"object"
```

Because in JavaScript arrays are also objects.

So:

```js
"object" === "object"
```

Result:

```js
true
```

# JavaScript Hoisting Example

```js
var x = 21;

var print = function() {
  console.log(x);
  
  var x = 11;
}

print();
```

# Output

```js
undefined
```

# Explanation

Inside the `print()` function, JavaScript sees:

```js
var x = 11;
```

Because `var` is **hoisted**, JavaScript internally treats the function like this:

```js
var x = 21;

var print = function() {

  var x; // hoisted

  console.log(x);

  x = 11;
}

print();
```

## Step-by-Step Execution

### Global Variable

```js
var x = 21;
```

A global variable `x` is created with value `21`.

---

### Function Call

```js
print();
```

When the function runs:

```js
var x;
```

is created first because of hoisting.

So inside the function, there is a **local variable `x`**.

---

### Console Execution

```js
console.log(x);
```

At this moment:

* local `x` exists
* but value is not assigned yet

So its value is:

```js
undefined
```

---

### Assignment Happens

```js
x = 11;
```

Now local `x` becomes `11`, but console already executed before this.

# Important Concept

`var` declarations are hoisted, but assignments are not hoisted.

So:

```js
var x = 11;
```

becomes:

```js
var x;
x = 11;
```

# Final Output

```js
undefined
```

# JavaScript Interview Question: var + setTimeout

## Question

```javascript
for (var i = 1; i <= 3; i++) {
    setTimeout(() => {
        console.log(i);
    }, 1000);
}
```

### Output

```javascript
4
4
4
```

---

## Why?

### 1. `var` is Function Scoped

`var` creates only **one shared variable**.

```javascript
for (var i = 1; i <= 3; i++)
```

The loop runs immediately:

```javascript
i = 1
i = 2
i = 3
i = 4  // loop ends
```

---

### 2. `setTimeout` is Asynchronous

`setTimeout` does not execute immediately.

All callbacks are stored and wait for 1 second.

By the time callbacks execute:

```javascript
i === 4
```

---

### 3. All Callbacks Reference the Same Variable

```javascript
callback1 -> i
callback2 -> i
callback3 -> i
```

Since `i` is already `4`, output becomes:

```javascript
4
4
4
```

---

## Using `let`

```javascript
for (let i = 1; i <= 3; i++) {
    setTimeout(() => {
        console.log(i);
    }, 1000);
}
```

### Output

```javascript
1
2
3
```

### Why?

`let` is block scoped.

Each iteration gets its own copy:

```javascript
Iteration 1 -> i = 1
Iteration 2 -> i = 2
Iteration 3 -> i = 3
```

So callbacks remember different values.

---

## Interview Answer (Short)

`var` is function-scoped, so all `setTimeout` callbacks share the same variable `i`. The loop finishes before the callbacks execute, making `i = 4`. Therefore, all callbacks print `4`. With `let`, a new variable is created for each iteration, so the output becomes `1 2 3`.



# Why Are Object Keys Strings in JavaScript?

## Example

```javascript
const obj = {
  1: "One",
  2: "Two"
};

console.log(Object.keys(obj));
```

Output:

```javascript
["1", "2"]
```

---

## Why?

In JavaScript, **all object keys are stored as strings** (except Symbols).

Even if you write:

```javascript
const obj = {
  1: "One"
};
```

JavaScript internally converts it to:

```javascript
const obj = {
  "1": "One"
};
```

Therefore:

```javascript
console.log(Object.keys(obj));
```

returns:

```javascript
["1"]
```

and not:

```javascript
[1]
```

---

## What If We Want Numeric Keys?

### Option 1: Convert Keys to Numbers

```javascript
const obj = {
  1: "One",
  2: "Two"
};

const numericKeys = Object.keys(obj).map(Number);

console.log(numericKeys);
```

Output:

```javascript
[1, 2]
```

---

### Option 2: Use Map

```javascript
const map = new Map();

map.set(1, "One");
map.set(2, "Two");

console.log(map.keys());
```

`Map` preserves the original key type.

Numeric keys remain numbers.

---

## Interview Answer (Short)

Object keys are strings because JavaScript automatically converts object property names to strings (except Symbols). Therefore, `Object.keys()` always returns an array of strings. If numeric keys are required, we can convert them using `map(Number)` or use a `Map`, which preserves the original key type.

### One-Line Interview Answer

> JavaScript objects store keys as strings, so `Object.keys()` returns strings. To keep keys as numbers, use `Map` or convert the returned keys using `map(Number)`.


## tricky output 

let a = 10;

const fn = () => console.log(a);

a = 20;

fn();

Output

20

Kyuki closure reference hold karta hai, value nahi.

# 1. JavaScript Event Loop (Microtask vs Macrotask)

## Code

```javascript
setTimeout(() => console.log("A"), 0);

Promise.resolve().then(() => {
  setTimeout(() => console.log("A"), 0);

  Promise.resolve().then(() => {
    console.log("B");

    setTimeout(() => {
      console.log("C");
    }, 0);
  });

  Promise.resolve().then(() => {
    console.log("D");
  });

  console.log("E");
});
```

---

## Output

```
E
B
D
A
A
C
```

---

## Small Explanation

### Step 1 (Call Stack)

- `setTimeout(A)` → goes to **Macrotask Queue**
- `Promise.then()` → goes to **Microtask Queue**

Call Stack becomes empty.

---

### Step 2 (Microtasks execute first)

Inside first Promise:

```javascript
setTimeout(A)
```

→ Added to Macrotask Queue

```javascript
Promise.then(B)
```

→ Added to Microtask Queue

```javascript
Promise.then(D)
```

→ Added to Microtask Queue

```javascript
console.log("E")
```

Prints immediately.

Output:

```
E
```

---

Next Microtask:

```javascript
console.log("B")
```

Prints:

```
B
```

Schedules

```javascript
setTimeout(C)
```

---

Next Microtask:

```javascript
console.log("D")
```

Prints:

```
D
```

---

### Step 3 (Macrotasks)

Macrotask Queue contains

```
A
A
C
```

They execute one by one.

Final Output

```
E
B
D
A
A
C
```

---

## Interview Rule

✅ All Microtasks execute before any Macrotask.

Priority:

```
Call Stack
   ↓
Microtasks (Promise, queueMicrotask)
   ↓
Macrotasks (setTimeout, setInterval)
```
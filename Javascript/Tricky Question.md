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
console.log(+"50")
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
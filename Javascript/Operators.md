# ✅ JavaScript Operators (Interview Notes)
# ✅ 1. Arithmetic Operators

Math operations ke liye use hote hain.

| Operator | Meaning |
|---|---|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus |
| `++` | Increment |
| `--` | Decrement |

---

# ✅ Example

```js id="u4m7kp"
let a = 10;
let b = 5;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
````

---

# ✅ 2. Assignment Operators

Variable me value assign karne ke liye.

| Operator | Example  |
| -------- | -------- |
| `=`      | `a = 10` |
| `+=`     | `a += 5` |
| `-=`     | `a -= 5` |
| `*=`     | `a *= 2` |

---

# ✅ Example

```js id="w7r2la"
let a = 10;

a += 5;

console.log(a);
```

## ✅ Output

```js id="m1q8vt"
15
```

---

# ✅ 3. Comparison Operators

Values compare karte hain.

| Operator | Meaning         |
| -------- | --------------- |
| `==`     | Loose equality  |
| `===`    | Strict equality |
| `!=`     | Not equal       |
| `>`      | Greater than    |
| `<`      | Less than       |

---

# 🔥 `==` vs `===`

## `==`

Only value compare karta hai.

```js id="q5t2wr"
console.log(5 == "5");
```

## ✅ Output

```js id="c7p9mx"
true
```

Because type coercion hua.

---

## `===`

Value + type dono compare karta hai.

```js id="g4n8ka"
console.log(5 === "5");
```

## ✅ Output

```js id="r8m1tv"
false
```

---

# 🎯 Interview Answer

> `==` only values compare karta hai,
> while `===` values aur data types dono compare karta hai.

---

# ✅ 4. Logical Operators

Conditions combine karne ke liye.

| Operator | Meaning |   |    |
| -------- | ------- | - | -- |
| `&&`     | AND     |   |    |
| `||`     | OR      |   |    |
| `!`      | NOT     |   |    |

---

# ✅ AND (`&&`)

```js id="k2q7pw"
console.log(true && true);
```

## ✅ Output

```js id="t9m4vx"
true
```

---

# ✅ OR (`||`)

```js id="n5p8la"
console.log(false || true);
```

## ✅ Output

```js id="f1r2mk"
true
```

---

# ✅ NOT (`!`)

```js id="x7v3qt"
console.log(!true);
```

## ✅ Output

```js id="b4k9wp"
false
```

---

# ✅ 5. Ternary Operator

Short form of if-else.

---

# ✅ Syntax

```js id="m6x1tr"
condition ? trueValue : falseValue
```

---

# ✅ Example

```js id="d8p4lw"
let age = 18;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

## ✅ Output

```js id="u2q9mv"
Adult
```

---

# 🎯 Interview Answer

> Ternary operator short syntax hai if-else ka.

---

# ✅ 6. Nullish Coalescing (`??`)

Null ya undefined hone par default value deta hai.

---

# ✅ Example

```js id="e3m7kp"
let name = null;

console.log(name ?? "Guest");
```

## ✅ Output

```js id="v8r1tx"
Guest
```

---

# 🔥 Difference Between `||` and `??`

## `||`

Falsy values bhi check karta.

```js id="a5n2qw"
console.log(0 || 100);
```

## ✅ Output

```js id="k9m4vr"
100
```

---

## `??`

Sirf null/undefined check karta.

```js id="j4p7lx"
console.log(0 ?? 100);
```

## ✅ Output

```js id="n1q8wt"
0
```

---

# 🎯 Interview Answer

> `??` operator sirf `null` aur `undefined` ke liye default value deta hai.

---

# ✅ 7. Optional Chaining (`?.`)

Nested properties safely access karne ke liye.

---

# ✅ Example

```js id="z6t2pm"
const user = {};

console.log(user.address?.city);
```

## ✅ Output

```js id="r4m8kx"
undefined
```

Error nahi aayega ✅

---

# ❌ Without Optional Chaining

```js id="q1x9la"
console.log(user.address.city);
```

## ❌ Error

```js id="v7p3tw"
Cannot read properties of undefined
```

---

# 🎯 Interview Answer

> Optional chaining safely nested properties access karne ke liye use hota hai without throwing errors.

---

# 🚀 Quick Revision Table

| Operator   | Purpose                    |
| ---------- | -------------------------- |
| Arithmetic | Math operations            |
| Assignment | Value assign               |
| Comparison | Compare values             |
| Logical    | Combine conditions         |
| Ternary    | Short if-else              |
| `??`       | Default for null/undefined |
| `?.`       | Safe property access       |

---

# 💡 One-Line Memory Trick

```js id="s8k4mp"
== → value compare

=== → value + type compare
```


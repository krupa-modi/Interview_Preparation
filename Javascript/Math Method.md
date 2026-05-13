````md
# 🔥 Math Object in JavaScript

👉 `Math` ek built-in object hai  
👉 Ye constructor nahi hai (`new Math()` nahi bana sakte)  
👉 Saare methods static hote hain → `Math.methodName()`

---

# 🔹 1️⃣ Rounding Methods (Most Asked 🔥)

| Method         | Kya karta hai     | Example         | Output |
| -------------- | ----------------- | --------------- | ------ |
| `Math.round()` | Nearest integer   | Math.round(4.6) | 5      |
| `Math.floor()` | Neeche round      | Math.floor(4.9) | 4      |
| `Math.ceil()`  | Upar round        | Math.ceil(4.1)  | 5      |
| `Math.trunc()` | Decimal hata deta | Math.trunc(4.9) | 4      |

🧠 Interview Trick:

```javascript
Math.floor(-4.2)  // -5
Math.trunc(-4.2)  // -4
```

---

# 🔹 2️⃣ Power & Root

| Method          | Example       | Output |
| --------------- | ------------- | ------ |
| `Math.pow(a,b)` | Math.pow(2,3) | 8      |
| `Math.sqrt()`   | Math.sqrt(16) | 4      |
| `Math.cbrt()`   | Math.cbrt(27) | 3      |

👉 Modern way:

```javascript
2 ** 3   // 8
```

---

# 🔹 3️⃣ Absolute & Sign

| Method        | Example       | Output |
| ------------- | ------------- | ------ |
| `Math.abs()`  | Math.abs(-5)  | 5      |
| `Math.sign()` | Math.sign(-5) | -1     |

---

# 🔹 4️⃣ Min / Max

| Method       | Example         | Output |
| ------------ | --------------- | ------ |
| `Math.max()` | Math.max(1,5,3) | 5      |
| `Math.min()` | Math.min(1,5,3) | 1      |

👉 Array me use:

```javascript
Math.max(...arr)
```

---

# 🔹 5️⃣ Random Number (🔥 Very Important)

| Method          | Example                |
| --------------- | ---------------------- |
| `Math.random()` | 0 se 1 ke beech number |

Random 1–10 number:

```javascript
Math.floor(Math.random() * 10) + 1
```

---

# 🔹 6️⃣ Logarithmic

| Method         | Example     |
| -------------- | ----------- |
| `Math.log()`   | Natural log |
| `Math.log10()` | Base 10 log |
| `Math.log2()`  | Base 2 log  |

---

# 🔹 7️⃣ Trigonometry

| Method       | Example         |
| ------------ | --------------- |
| `Math.sin()` | Math.sin(angle) |
| `Math.cos()` | Math.cos(angle) |
| `Math.tan()` | Math.tan(angle) |
| `Math.PI`    | 3.14159         |

Example (Circle Area Formula):

```javascript
let area = Math.PI * r * r;
```

---

# 🔹 8️⃣ Constants

| Constant     | Value        |
| ------------ | ------------ |
| `Math.PI`    | 3.14159      |
| `Math.E`     | Euler number |
| `Math.LN2`   | ln(2)        |
| `Math.SQRT2` | √2           |

---

# 🔥 Common Interview Questions

### ❓ Random 1–100 number?

```javascript
Math.floor(Math.random() * 100) + 1
```

### ❓ Decimal ko 2 places tak round?

```javascript
Number(num.toFixed(2))
```

### ❓ Largest number in array?

```javascript
Math.max(...arr)
```

---

# 🎯 Quick Revision (One Line)

Round → round, floor, ceil, trunc  
Power → pow, sqrt  
Compare → max, min  
Random → random  
Constant → PI
````

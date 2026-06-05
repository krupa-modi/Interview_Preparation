# 🔥 What is Memoization?

Memoization is an optimization technique.

👉 It stores previous function results in cache so same calculation dubara na karna pade.

---
# 🎯 Simple Definition

> Memoization means caching function results to improve performance.

---

# ✅ Why We Use Memoization?

Suppose ek heavy calculation baar baar same input ke saath call ho raha hai.

Without memoization:
```js
sum(10, 20)
sum(10, 20)
sum(10, 20)
````

हर बार calculation hoga ❌

Memoization:

* First time calculate karega
* Next time cache se result dega ✅

---

# 🚀 Easy Real Example

## Without Memoization

```js id="5gm3jg"
function square(n) {
  console.log("Calculating...");
  return n * n;
}

console.log(square(4));
console.log(square(4));
```

### Output

```js id="w6hcrj"
Calculating...
16

Calculating...
16
```

👉 Same calculation 2 baar hua.

---

# ✅ With Memoization

```js id="9ix7k3"

//index.html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello, World!</title>
  </head>
  <body>
      <button onClick = "memorize(2,3)">Calculation</button>
      <script src="script.js"></script>
  </body>
</html>

//script.js

function calculation(a,b){
    let result =  a * b
    alert("fisrt time calling",result)
    return result
}

let cache ={}
function memorize(a,b){
    let key = a + ":" + b;
    if(!cache[key]){
        let result = calculation(a,b)
        cache[key] = result
        return result
    }else{
        alert("data storeddd",cache[key])
        return cache[key]
    }
}

******************************************************OR**************************************************************
function memoizedSquare() {

  const cache = {};

  return function(n) {

    // agar result cache me hai
    if (cache[n]) {
      console.log("From Cache");
      return cache[n];
    }

    // warna calculate karo
    console.log("Calculating...");
    const result = n * n;

    // cache me store karo
    cache[n] = result;

    return result;
  };
}

const square = memoizedSquare();

console.log(square(4));
console.log(square(4));
console.log(square(5));
console.log(square(5));
```

---

# ✅ Output

```js id="0c7jlwm"
Calculating...
16

From Cache
16

Calculating...
25

From Cache
25
```

---

# 🔍 Easy Explanation

## `cache`

Object hai jisme previous results store hote hain.

```js id="7f3zbi"
{
  4: 16,
  5: 25
}
```

---

# 🚀 Interview Flow Explain

### First Call

```js id="p7k5ng"
square(4)
```

* cache me nahi mila
* calculate hua
* cache me save hua

---

### Second Call

```js id="kkv4rk"
square(4)
```

* cache me mil gaya
* directly return ho gaya
* calculation nahi hua

---

# ⚡ Benefits of Memoization

| Benefit            | Explanation                           |
| ------------------ | ------------------------------------- |
| Faster Performance | Repeated calculations avoid hote hain |
| Optimization       | Heavy functions fast ho jate hain     |
| Saves Time         | Cached result milta hai               |

---

# ⚠️ Disadvantage

More memory use hoti hai because results cache me store hote hain.

---

# 🔥 Real Use Cases

## 1. API Caching

Same API call repeat avoid karna

---

## 2. React

```js id="jvvzzx"
useMemo()
```

Performance optimization ke liye.

---

## 3. Expensive Calculations

Factorial, Fibonacci etc.

---

# 🚀 Most Asked Interview Question

## Q: Difference between Memoization and Caching?

## Answer:

* Memoization specifically function results cache karta hai.
* Caching general data storage technique hai.

---

# 🎯 Short Interview Answer

> Memoization ek optimization technique hai jisme function ke previous results cache me store kiye jate hain taki same input par dubara calculation na karna pade.

---

# 💡 Quick Revision

| Concept        | Meaning                     |
| -------------- | --------------------------- |
| Memoization    | Function result cache karna |
| Purpose        | Performance improve karna   |
| Mostly Used    | Heavy calculations          |
| Data Stored In | Cache/Object                |

```


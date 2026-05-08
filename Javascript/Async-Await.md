
## 1. `async / await` kya hota hai?

`async / await` JavaScript me **Promises ko handle karne ka modern aur readable tarika** hai.

* `async` function **hamesha Promise return karta hai**
* `await` Promise ke resolve hone ka wait karta hai
* Code **synchronous jaisa dikhta hai**, par hota asynchronous hai

---

## 2. Basic Syntax

```js
async function myFunc() {
  let result = await somePromise
  console.log(result)
}
```

### Yaad rakhne wali baat:

* `await` **sirf async function ke andar** use hota hai
* `await` program ko block nahi karta, sirf us function ko pause karta hai

---

## 3. Aapka Example Code (With Explanation)

### Weather Promise Creation

```js
let delhiWeather = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("27 Deg")
  }, 2000)
})
```

✔️ 2 seconds baad Promise resolve ho jayega

```js
let bangaloreWeather = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("21 Deg")
  }, 5000)
})
```

✔️ 5 seconds baad Promise resolve ho jayega

---

## 4. `harry()` async function

```js
async function harry() {
  console.log("Fetching Delhi Weather Please wait ...")
  let delhiW = await delhiWeather
  console.log("Fetched Delhi Weather: " + delhiW)

  console.log("Fetching Bangalore Weather Please wait ...")
  let bangaloreW = await bangaloreWeather
  console.log("Fetched Bangalore Weather: " + bangaloreW)

  return [delhiW, bangaloreW]
}
```

### Explanation:

* `await delhiWeather` → jab tak Promise resolve nahi hota, function pause
* Pehle Delhi ka result milega (2 sec)
* Phir Bangalore ka result milega (5 sec)
* Last me function **array return karta hai**

👉 `async function` return karta hai:

```js
Promise<[delhiW, bangaloreW]>
```

---

## 5. `cherry()` async arrow function

```js
const cherry = async () => {
  console.log("Hey I am cherry and I am not waiting")
}
```

### Important Point:

* Ye bhi Promise return karega
* Lekin isme `await` nahi hai
* Isliye ye turant execute ho jata hai

---

## 6. `main1()` – Program Flow Control

```js
const main1 = async () => {
  console.log("Welcome to weather control room")
  let a = await harry()
  let b = await cherry()
}
```

### Execution Flow:

1. `Welcome to weather control room`
2. `harry()` call → wait karega (total ~7 sec)
3. `cherry()` call → turant execute

---

## 7. ❌ Common Mistake (Important)

```js
a.then((value) => {
  console.log(value)
})
```

### ❌ Galat kyu?

* `a` already **resolved value** hai (array)
* `.then()` sirf Promise pe lagta hai

### ✅ Correct Ways

#### Option 1: Direct use

```js
console.log(a)
```

#### Option 2: Promise handle karna ho to

```js
harry().then(value => console.log(value))
```

# 5. Internal Flow Example
```

console.log("Start");

async function demo() {
  console.log("Inside function");

  await Promise.resolve();

  console.log("After await");
}

demo();

console.log("End");
```

```
Output:

Start
Inside function
End
After await
```
---

## 8. Interview Important Questions ⭐

### Q1. `async` function kya return karta hai?

**Answer:** Hamesha ek Promise return karta hai.

---

### Q2. `await` kya karta hai?

**Answer:** Promise resolve hone tak async function ko pause karta hai.

---

### Q3. Kya `await` main file ko block karta hai?

**Answer:** Nahi, sirf us async function ko block karta hai.

---

### Q4. `async/await` vs `.then()`

**Answer:** `async/await` zyada readable aur clean syntax deta hai.

---

## 9. One‑Line Interview Explanation

> "Async/await JavaScript me Promises ko handle karne ka modern tarika hai jisme async function Promise return karta hai aur await uske resolve hone ka wait karta hai bina main thread block kiye."

---

## 10. Quick Revision Sheet 📝

* `async` → Promise return
* `await` → Promise ka result
* `await` sirf async ke andar
* Multiple awaits → sequence me execute
* `.then()` aur `await` mix mat karo

---

## 11. Internal Working of `async / await` ⭐ (Very Important for Interview)

### Jab `async` function call hota hai:

```js
async function demo() {
  return 10
}
```

Actually internally JavaScript isko convert karta hai:

```js
function demo() {
  return Promise.resolve(10)
}
```

👉 Matlab `async` keyword automatically normal value ko Promise me wrap kar deta hai.

---

### `await` internally kya karta hai?

```js
let result = await promise
```

Internally ye `.then()` jaisa behave karta hai:

```js
promise.then((result) => {
  // next line execution
})
```

👉 `await` event loop aur microtask queue ka use karta hai.

---

# SUPER IMPORTANT INTERVIEW THEORY
```
    Internal Architecture

    async function starts
            ↓
    returns Promise immediately
            ↓
    await encountered
            ↓
    function paused
            ↓
    remaining code moved to Microtask Queue
            ↓
    event loop waits
            ↓
    promise resolves
            ↓
    microtask pushed to Call Stack
            ↓
    execution resumes
```


## 12. Event Loop Connection (Interview Favorite Topic)

JavaScript single threaded language hai.

Phir bhi async kaam kaise hota hai?

Because of:

* Call Stack
* Web APIs
* Callback Queue
* Microtask Queue
* Event Loop

### Important:

✅ Promise callbacks aur `await` → Microtask Queue me jate hain

✅ `setTimeout` → Callback Queue me jata hai

👉 Microtask Queue ki priority zyada hoti hai.

---

## 13. Important Interview Output Question ⭐

```js
console.log("Start")

setTimeout(() => {
  console.log("Timeout")
}, 0)

Promise.resolve().then(() => {
  console.log("Promise")
})

console.log("End")
```

### Output:

```js
Start
End
Promise
Timeout
```

### Reason:

* Synchronous code pehle execute hota hai
* Promise → Microtask Queue
* setTimeout → Callback Queue
* Event loop pehle Microtask Queue execute karta hai

---

## 14. Parallel Execution Using `Promise.all()` ⭐

Aapke current code me awaits sequential hain.

Matlab:

* Delhi → 2 sec
* Bangalore → 5 sec
* Total ≈ 7 sec

### Better Approach:

```js
async function weather() {
  let results = await Promise.all([
    delhiWeather,
    bangaloreWeather
  ])

  console.log(results)
}
```

### Benefit:

✅ Dono promises parallel execute honge

✅ Total time ≈ 5 sec only

---

## 15. Error Handling Using `try...catch`

```js
async function test() {
  try {
    let result = await Promise.reject("Error aa gaya")
    console.log(result)
  } catch (error) {
    console.log(error)
  }
}
```

### Interview Point:

* Async/await ke sath error handling ke liye `try...catch` use hota hai
* Promise rejection ko catch karta hai

---

## 16. Real Life Example ⭐

```js
async function getUsers() {
  let response = await fetch("https://jsonplaceholder.typicode.com/users")

  let data = await response.json()

  console.log(data)
}
```

### Yaha kya ho raha hai?

1. `fetch()` API call karta hai
2. `await` response ka wait karta hai
3. `response.json()` bhi Promise return karta hai
4. Final data mil jata hai

---

## 17. Most Asked Interview Difference Table ⭐

| Feature           | Promise `.then()` | `async/await` |
| ----------------- | ----------------- | ------------- |
| Syntax            | Complex           | Clean         |
| Readability       | Kam               | Zyada         |
| Chaining          | Required          | Nahi          |
| Error Handling    | `.catch()`        | `try/catch`   |
| Beginner Friendly | Thoda difficult   | Easy          |

---

## 18️⃣ Complete Working Code (As It Is)

```js
async function harry() {
  let delhiWeather = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("27 Deg")
    }, 2000)
  })

  let bangaloreWeather = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("21 Deg")
    }, 5000)
  })

  console.log("Fetching Delhi Weather Please wait ...")
  let delhiW = await delhiWeather
  console.log("Fetched Delhi Weather: " + delhiW)

  console.log("Fetching Bangalore Weather Please wait ...")
  let bangaloreW = await bangaloreWeather
  console.log("Fetched Bangalore Weather: " + bangaloreW)

  return [delhiW, bangaloreW]
}

const cherry = async () => {
  console.log("Hey I am cherry and I am not waiting")
}

const main1 = async () => {
  console.log("Welcome to weather control room")

  let a = await harry()
  let b = await cherry()

  console.log(a)
}

main1();

// Output:
// Welcome to weather control room
// Fetching Delhi Weather Please wait ...
// Fetched Delhi Weather: 27 Deg
// Fetching Bangalore Weather Please wait ...
// Fetched Bangalore Weather: 21 Deg
// Hey I am cherry and I am not waiting
// [ '27 Deg', '21 Deg' ]
```

---

## 19. Final Interview Revision Notes ⭐

* `async` → Promise return karta hai
* `await` → Promise resolve hone ka wait karta hai
* `await` sirf async function me use hota hai
* `await` main thread ko block nahi karta
* Promise callbacks → Microtask Queue
* `try/catch` → async errors handle karne ke liye
* `Promise.all()` → parallel execution
* Async/await internally `.then()` par based hai
* Event Loop async programming ka core concept hai

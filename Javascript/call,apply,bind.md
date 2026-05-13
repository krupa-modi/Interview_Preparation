JavaScript में `call()`, `apply()` और `bind()` methods का use
function के `this` keyword को manually control करने के लिए किया जाता है।

👉 ये तीनों methods JavaScript के **Function Prototype** का हिस्सा हैं।

---

# 🧠 Simple Rule (Easy Memory Trick)

> **call / apply / bind → function ko kisi aur object ke `this` ke sath chalana**

---

# 📌 Why We Need Them?

Normally:

```js
obj.method()
```

👉 यहाँ `this` उस object को refer करता है जो function call कर रहा है।

लेकिन कई बार हमें:

* किसी दूसरे object का function use करना होता है
* `this` manually set करना होता है
* function borrowing करनी होती है
* callbacks में `this` maintain रखना होता है

तब हम use करते हैं:

✅ `call()`
✅ `apply()`
✅ `bind()`

---

# 🔥 Important Interview Line

> call, apply, and bind are used to explicitly control the value of `this` in JavaScript functions.

---

# 📌 What is `this`?

`this` उस object को refer करता है जो function को call करता है।

## Example

```js
const user = {
  name: "Krupa",

  greet() {
    console.log(this.name);
  }
};

user.greet();
```

## ✅ Output

```bash
Krupa
```

यहाँ:

```js
this === user
```

---

# 📌 Common Function Example

```js
function greet(city, country) {
  console.log(
    "Hello " + this.name + " from " + city + ", " + country
  );
}
```

---

# 📌 Example Object

```js
let person = {
  name: "Rahul"
};
```

---

# 🔥 1️⃣ call()

## ✅ Definition

`call()` function को **immediately execute** करता है
और arguments **comma separated** pass होते हैं।

---

# 📌 Syntax

```js
function.call(thisArg, arg1, arg2, ...)
```

---

# 📦 Example

```js
greet.call(person, "Delhi", "India");
```

---

# ✅ Output

```bash
Hello Rahul from Delhi, India
```

---

# 🧠 How It Works

```js
greet.call(person)
```

Means:

```js
this = person
```

inside the function.

---

# 📌 Important Points of call()

✔ Function immediately execute होता है
✔ Arguments individually pass होते हैं
✔ `this` change करता है
✔ Function borrowing में useful

---

# 🔥 Real Interview Example (Function Borrowing)

```js
const person1 = {
  name: "Krupa"
};

const person2 = {
  name: "Rahul"
};

function intro() {
  console.log(`Hi I am ${this.name}`);
}

intro.call(person1);
intro.call(person2);
```

---

# ✅ Output

```bash
Hi I am Krupa
Hi I am Rahul
```

---

# 🔥 2️⃣ apply()

## ✅ Definition

`apply()` भी function को **immediately execute** करता है
लेकिन arguments **array format** में pass होते हैं।

---

# 📌 Syntax

```js
function.apply(thisArg, [arg1, arg2, ...])
```

---

# 📦 Example

```js
greet.apply(person, ["Mumbai", "India"]);
```

---

# ✅ Output

```bash
Hello Rahul from Mumbai, India
```

---

# 🧠 Difference from call()

## call()

```js
fn.call(obj, a, b)
```

## apply()

```js
fn.apply(obj, [a, b])
```

---

# 📌 Important Points of apply()

✔ Function immediately execute होता है
✔ Arguments array में pass होते हैं
✔ Array data available होने पर useful

---

# 🔥 Real Interview Use Case (`Math.max`)

```js
let arr = [5, 8, 2, 10];

let max = Math.max.apply(null, arr);

console.log(max);
```

---

# ✅ Output

```bash
10
```

---

# 🔥 Modern Alternative

आजकल spread operator use होता है:

```js
Math.max(...arr)
```

लेकिन interview में `apply()` example अभी भी important है।

---

# 🔥 3️⃣ bind()

## ✅ Definition

`bind()` function को तुरंत execute नहीं करता।

👉 यह एक **new function return** करता है
जिसमें `this` permanently bind हो जाता है।

---

# 📌 Syntax

```js
function.bind(thisArg, arg1, arg2, ...)
```

---

# 📦 Example

```js
let newGreet = greet.bind(person, "Pune", "India");

newGreet();
```

---

# ✅ Output

```bash
Hello Rahul from Pune, India
```

---

# 🧠 Important Point

```js
bind()
```

returns a NEW function.

It does NOT execute immediately.

---

# 🔥 Why bind() Important?

बहुत useful होता है:

* Event handlers
* React class components
* `setTimeout`
* Callbacks
* `this` maintain रखने में

---

# 📦 Example with setTimeout

## ❌ Without bind()

```js
const user = {
  name: "Krupa",

  greet() {
    console.log(this.name);
  }
};

setTimeout(user.greet, 1000);
```

---

# ❌ Output

```bash
undefined
```

Because:

```js
this !== user
```

---

# ✅ Solution Using bind()

```js
const user = {
  name: "Krupa",

  greet() {
    console.log(this.name);
  }
};

setTimeout(user.greet.bind(user), 1000);
```

---

# ✅ Output

```bash
Krupa
```

---

# 🔥 call vs apply vs bind (Difference Table)

| Feature              | call       | apply | bind       |
| -------------------- | ---------- | ----- | ---------- |
| Executes Immediately | ✅ Yes      | ✅ Yes | ❌ No       |
| Returns Function     | ❌ No       | ❌ No  | ✅ Yes      |
| Arguments            | Individual | Array | Individual |
| Changes `this`       | ✅ Yes      | ✅ Yes | ✅ Yes      |

---

# 🎯 Easy Memory Trick

## call()

👉 Call now

---

## apply()

👉 Apply with array

---

## bind()

👉 Bind and use later

---

# 🔥 Most Important Interview Questions

---

# ❓ Difference Between call() and apply()

## ✅ Answer

Both functions:

* execute immediately
* change `this`

Difference:

* `call()` → arguments individually
* `apply()` → arguments in array

---

# ❓ Difference Between call() and bind()

## ✅ Answer

* `call()` executes immediately
* `bind()` returns a new function

---

# ❓ What is Function Borrowing?

Using one object's method for another object.

## Example

```js
intro.call(user2)
```

---

# ❓ Can We Chain bind()?

```js
const fn = greet.bind(obj1).bind(obj2);
```

## ✅ Answer

No.

Once function is bound:

```js
this cannot be changed
```

---

# 🔥 Common Interview Question

```js
let obj = {
  name: "Amit",

  greet: function () {
    console.log(this.name);
  }
};

let fn = obj.greet;

fn();
```

---

# ❌ Output

```bash
undefined
```

---

# ❓ Why?

Because function detached हो गया object से।

So:

```js
this lost ho gaya
```

---

# ✅ Fix using bind()

```js
let fixed = obj.greet.bind(obj);

fixed();
```

---

# ✅ Output

```bash
Amit
```

---

# 🔥 Advanced Example

```js
const person = {
  firstName: "Krupa",
  lastName: "Modi"
};

function fullName(city) {
  console.log(
    `${this.firstName} ${this.lastName} from ${city}`
  );
}

fullName.call(person, "Pune");

fullName.apply(person, ["Mumbai"]);

const bindFunc = fullName.bind(person, "Delhi");

bindFunc();
```

---

# ✅ Output

```bash
Krupa Modi from Pune
Krupa Modi from Mumbai
Krupa Modi from Delhi
```
---

# ⚠️ Important Notes (Interview)

✔ `call()` / `apply()` → one-time execution
✔ `bind()` → reusable function
✔ Arrow functions में `bind()` काम नहीं करता
✔ `apply()` useful when arguments array में हों
✔ `bind()` callbacks में बहुत important है

---

# 🧠 One-Line Summary

* **call** → अभी call (comma arguments)
* **apply** → अभी call (array arguments)
* **bind** → बाद में call

---

# ✅ Perfect Short Interview Answer

> call, apply aur bind ka use function ke `this` context ko control karne ke liye hota hai.
> call aur apply function ko turant execute karte hain,
> jabki bind ek new function return karta hai jo baad me execute hota hai.

---

# ✅ Final Combined Example

```javascript
function greet(city, country) {
  console.log(
    "Hello " + this.name + " from " + city + ", " + country
  );
}

let person = {
  name: "Rahul"
};

// call
greet.call(person, "Delhi", "India");

// apply
greet.apply(person, ["Mumbai", "India"]);

// bind
let newFunc = greet.bind(person, "Pune", "India");

newFunc();
```

---

# 🚀 Most Important Interview Line

> `call()`, `apply()`, and `bind()` are used to explicitly control the value of `this` in JavaScript functions.



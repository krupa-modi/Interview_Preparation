
## What is try...catch?

`try...catch` JavaScript ka error handling mechanism hai.

Agar code me koi error aa jaye to application crash na ho, uske liye `try...catch` use karte hain.

---

# Syntax

```js
try {
   // risky code
} catch(error) {
   // error handle
}
````

---

# Why We Use try...catch?

* Application crash hone se bachane ke liye
* Runtime errors handle karne ke liye
* User ko proper message dikhane ke liye
* API calls / JSON parsing / async code me errors handle karne ke liye

---

# How it Works

## 1. try block

Yaha wo code likhte hain jisme error aane ke chances hote hain.

## 2. catch block

Agar `try` block me error aata hai to control `catch` block me chala jata hai.

---

# Basic Example

```js
try {
   console.log(a);
} catch(error) {
   console.log("Error aa gaya");
}
```

## Output

```js
Error aa gaya
```

### Explanation

`a` variable define nahi hai, isliye error aaya.
Wo error `catch` ne handle kar liya.

---

# Error Object

`catch(error)` me jo `error` aata hai usme error ki information hoti hai.

```js
try {
   console.log(a);
} catch(error) {
   console.log(error);
}
```

---

# Important Error Properties

```js
error.name
error.message
```

## Example

```js
try {
   console.log(a);
} catch(error) {
   console.log(error.name);
   console.log(error.message);
}
```

## Output

```js
ReferenceError
a is not defined
```

---

# Real Interview Example

## JSON Parse

```js
try {
   let data = JSON.parse("abc");
   console.log(data);
} catch(error) {
   console.log("Invalid JSON");
}
```

## Output

```js
Invalid JSON
```

### Why Important?

API response handle karte time bahot use hota hai.

---

# try...catch...finally

`finally` block hamesha chalega chahe error aaye ya na aaye.

```js
try {
   console.log("Try block");
} catch(error) {
   console.log("Catch block");
} finally {
   console.log("Finally block");
}
```

## Output

```js
Try block
Finally block
```

---

# Example with Error

```js
try {
   console.log(a);
} catch(error) {
   console.log("Error handled");
} finally {
   console.log("Always execute");
}
```

## Output

```js
Error handled
Always execute
```

---

# throw Keyword

Custom error create karne ke liye `throw` use hota hai.

```js
try {
   let age = 15;

   if(age < 18) {
      throw "Not eligible";
   }

   console.log("Eligible");
} catch(error) {
   console.log(error);
}
```

## Output

```js
Not eligible
```

---

# Where We Use try...catch?

## 1. API Calls

```js
try {
   let data = await fetch(url);
} catch(error) {
   console.log(error);
}
```

---

## 2. JSON Parsing

```js
JSON.parse()
```

---

## 3. Database Operations

---

## 4. File Handling

---

# Important Interview Points

## 1. try without catch possible?

Yes

```js
try {
   console.log("Hello");
} finally {
   console.log("Done");
}
```

---

## 2. finally kab execute hota hai?

Always.

---

## 3. try...catch synchronous errors handle karta hai ya asynchronous?

Mainly synchronous errors.

Async me mostly:

* `.catch()`
* `try...catch with async-await`

---

# Async Await Example

```js
async function getData() {
   try {
      let res = await fetch("url");
      let data = await res.json();

      console.log(data);
   } catch(error) {
      console.log("API Error");
   }
}
```

---

# Common Interview Questions

## 1. Difference between throw and catch?

| throw                  | catch                  |
| ---------------------- | ---------------------- |
| Error create karta hai | Error handle karta hai |

---

## 2. finally block ka use kya hai?

Cleanup code ke liye.

Example:

* Database close
* Loader hide
* File close

---

## 3. Can finally run without catch?

Yes.

---

# Short Summary

* `try` → risky code
* `catch` → error handle
* `finally` → always execute
* `throw` → custom error create

---

# Most Important Line for Interview

> "try...catch is used to handle runtime errors gracefully so the application does not crash."



## What is Custom Error?

Jab hum apni requirement ke according khud ka error create karte hain usko **Custom Error** bolte hain.

JavaScript me already built-in errors hote hain:
- ReferenceError
- TypeError
- SyntaxError

But kabhi kabhi hume business logic ke according apna error banana padta hai.

---

# Why We Use Custom Error?

- Better error messages dene ke liye
- Validation handle karne ke liye
- Debugging easy banane ke liye
- Application ka control improve karne ke liye

---

# Basic Example

```js
try {
   let age = 15;

   if(age < 18) {
      throw "You are not eligible";
   }

   console.log("Eligible");
} catch(error) {
   console.log(error);
}
````

## Output

```js
You are not eligible
```

---

# Explanation

Yaha humne manually error throw kiya using `throw`.

Agar age 18 se kam hai to custom message show hoga.

---

# Using Error Object (Best Practice)

Interview me ye approach jyada preferred hota hai.

```js
try {
   let age = 15;

   if(age < 18) {
      throw new Error("Age must be 18+");
   }

   console.log("Eligible");
} catch(error) {
   console.log(error.message);
}
```

## Output

```js
Age must be 18+
```

---

# Why use new Error()?

Kyuki ye proper error object create karta hai.

Isme milta hai:

* name
* message
* stack trace

---

# Real Interview Example

## Login Validation

```js
function login(password) {
   try {

      if(password.length < 8) {
         throw new Error("Password too short");
      }

      console.log("Login Success");

   } catch(error) {
      console.log(error.message);
   }
}

login("123");
```

## Output

```js
Password too short
```

# Where We Use Custom Errors?

* Form validation
* API validation
* Authentication
* Payment systems
* Database validation

---

# Important Interview Points

## 1. Difference between throw and Error?

| throw                 | Error                         |
| --------------------- | ----------------------------- |
| Error throw karta hai | Error object create karta hai |

---

## 2. Best Practice?

```js
throw new Error("Message")
```

---

## 3. Why Custom Errors Important?

Readable code aur better debugging ke liye.

---

# Short Summary

* `throw` → manually error throw karta hai
* `new Error()` → proper error object create karta hai
* Custom Error → apni requirement ke according error banana

---

# Most Important Interview Line

> "Custom errors are used to create meaningful and application-specific error handling."

```
```

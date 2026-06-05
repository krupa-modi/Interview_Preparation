# Async/Await vs Promise

# Promise

## What is Promise?

Promise ek object hota hai jo future value ko represent karta hai.

## Syntax

* `.then()`
* `.catch()`
* `.finally()`

## Kab Use Kare?

* Jab chaining karni ho
* Multiple async operations handle karne ho
* Parallel execution karna ho
* Promise APIs use ho rahi ho (`Promise.all`, `Promise.race`)
* Fine-grained control chahiye ho

## Advantages

* Older JavaScript environments me supported
* Multiple promises ko manage karna easy
* Parallel tasks ke liye useful

## Disadvantages

* Zyada `.then()` chaining se callback hell jaisa lag sakta hai
* Readability kam ho sakti hai
* Complex code difficult ho jata hai

---
# Async/Await

## What is Async/Await?

Async/Await promises ko easy aur synchronous style me likhne ka modern way hai.

## Syntax

* `async`
* `await`

## Kab Use Kare?

* Readable code chahiye ho
* Sequential async operations ho
* API calls simple aur clean way me likhni ho
* Interview ya production code me maintainability important ho

## Advantages

* Code synchronous jaisa dikhta hai
* Readability better
* Debugging easy
* Clean error handling with `try/catch`

## Disadvantages

* Internally promises hi use karta hai
* Incorrect usage se sequential waiting ho sakti hai
* Parallel execution manually handle karna padta hai

---

# Main Difference

| Promise                                | Async/Await                       |
| -------------------------------------- | --------------------------------- |
| `.then()` and `.catch()` use karta hai | `async` and `await` use karta hai |
| Chain based syntax                     | Synchronous-like syntax           |
| Readability kam ho sakti hai           | Readability better hoti hai       |
| Complex lag sakta hai                  | Clean aur easy lagta hai          |
| Parallel tasks me useful               | Sequential flow me useful         |
| Older style                            | Modern style                      |

---

# Interview Important Points

## Promise

* Base asynchronous mechanism hai
* Async/Await internally promises par hi based hai

## Async/Await

* Promise ka modern wrapper hai
* Cleaner syntax provide karta hai
* Better readability aur maintenance deta hai

---

# Kab Kya Use Kare?

## Promise Use Kare

* Multiple async tasks parallel me chalani ho
* Promise utilities use karni ho
* Existing promise-based codebase ho

## Async/Await Use Kare

* Clean and readable code chahiye ho
* API calls sequential ho
* Easy debugging chahiye ho
* Production level maintainable code likhna ho

---

# Short Interview Answer

"Promise asynchronous operations ko handle karne ka original way hai using `.then()` and `.catch()`.
Async/Await promises ka modern syntax hai jo code ko synchronous jaisa readable banata hai.
Readable and maintainable code ke liye mostly async/await use kiya jata hai, while parallel execution aur promise utilities ke liye promises useful hote hain."


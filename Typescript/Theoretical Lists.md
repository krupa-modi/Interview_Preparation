# TypeScript Function Parameters Interview Notes

# 1. Optional Parameters

## 👉 Meaning

Optional parameters wo hote hain jo function call karte waqt dena mandatory nahi hota.

`?` symbol use hota hai.

---

## Example

```ts id="q4m8tp"
function greet(name?: string) {
  console.log(name);
}

greet();
greet("Krupa");
```

---

## Interview Point

* Optional values handle karne ke liye useful
* Mostly forms aur optional configs me use hote hain

---

# 2. Default Parameters

## 👉 Meaning

Default parameters me agar value pass nahi karo to predefined value use hoti hai.

---

## Example

```ts id="j7v2kc"
function greet(name: string = "Guest") {
  console.log(name);
}

greet();
greet("Krupa");
```

---

## Interview Point

* Undefined issues avoid hote hain
* Cleaner fallback values milti hain

---

# 3. Rest Parameters

## 👉 Meaning

Rest parameters multiple values ko ek array me collect karte hain.

`...` operator use hota hai.

---

## Example

```ts id="x9p3lf"
function total(...numbers: number[]) {
  return numbers.reduce((a, b) => a + b, 0);
}

console.log(total(10, 20, 30));
```

---

## Interview Point

* Dynamic arguments handle karne ke liye useful
* Array methods directly use kar sakte hain

---

# 🔥 Quick Difference

| Feature            | Purpose                           |
| ------------------ | --------------------------------- |
| Optional Parameter | Value dena optional               |
| Default Parameter  | Default value provide karta hai   |
| Rest Parameter     | Multiple values collect karta hai |

---

# 🔥 Interview Line

> “Optional parameters are not mandatory, default parameters provide fallback values, and rest parameters allow handling multiple dynamic arguments.”


# Function Overloading in TypeScript

## 👉 What is Function Overloading?

Function overloading ka matlab hai:

> Same function ke multiple type definitions banana with different parameters or return types.

Lekin actual implementation sirf ek hoti hai.

---

# Example

```ts id="k4m8xp"
function greet(name: string): string;
function greet(age: number): string;

function greet(value: string | number): string {
  if (typeof value === "string") {
    return `Hello ${value}`;
  }

  return `Age is ${value}`;
}

console.log(greet("Krupa"));
console.log(greet(22));
```

---

# Interview Explanation

* Same function different types handle kar sakta hai
* Better type safety provide karta hai
* IntelliSense improve hota hai

---

# Real-world Use Case

✅ APIs
✅ Utility functions
✅ Form handlers
✅ Search/filter functions

---

# Interview Line

> “Function overloading allows a function to support multiple parameter types while keeping a single implementation.”



# TypeScript Function Interview Questions

# 1. How do you type arrow functions?

## 👉 Answer

Arrow functions me parameters aur return type define karte hain.

---

## Example

```ts id="m8x2pa"
const add = (a: number, b: number): number => {
  return a + b;
};
```

---

## Interview Point

* Parameters type-safe hote hain
* Return value check hoti hai
* IntelliSense improve hota hai

---

# 2. How do you type callback functions?

## 👉 Answer

Callback function ka parameter type function signature se define karte hain.

---

## Example

```ts id="q5v7tn"
function process(
  callback: (value: string) => void
) {
  callback("Hello");
}
```

---

## Usage

```ts id="z1k4wc"
process((msg) => {
  console.log(msg);
});
```

---

## Interview Point

* Callback expected parameter aur return type clearly define karta hai
* Runtime errors reduce hote hain

---

# 3. What is contextual typing?

## 👉 Answer

Jab TypeScript automatically context se type infer karta hai usko contextual typing bolte hain.

---

## Example

```ts id="n3u8ry"
const names = ["A", "B", "C"];

names.forEach((name) => {
  console.log(name.toUpperCase());
});
```

Yaha `name` automatically `string` infer hua.

---

## Interview Point

* Explicit types likhne ki need kam hoti hai
* Cleaner code milta hai

---

# 4. What is return type annotation?

## 👉 Answer

Function kya return karega uska type explicitly define karna return type annotation kehlata hai.

---

## Example

```ts id="p7d2mx"
function greet(): string {
  return "Hello";
}
```

---

## Benefits

* Wrong return values detect hote hain
* Better readability
* Safer functions

---

# 5. What is `never` return type?

## 👉 Answer

`never` type un functions ke liye use hota hai jo kabhi value return nahi karte.

---

## Example 1: Error Throw

```ts id="x9r4kb"
function throwError(message: string): never {
  throw new Error(message);
}
```

---

## Example 2: Infinite Loop

```ts id="h2m6qw"
function infiniteLoop(): never {
  while (true) {}
}
```

---

## Interview Point

* `never` means function execution complete hi nahi hota
* Mostly error handling me use hota hai



# 1. What is an Interface?

## Definition

Interface TypeScript mein object structure define karne ke liye use hota hai.

Simple words mein:

> object kaisa dikhega uska blueprint.

---

## Example

```ts id="a1"
interface User {
  name: string;
  age: number;
}
```

---

## Usage

```ts id="a2"
const user: User = {
  name: "Krupa",
  age: 25
};
```

---

## Benefits

* reusable
* readable
* object typing easy
* class contracts define kar sakte

---

# 2. Difference Between Type and Interface

| Feature             | Interface       | Type           |
| ------------------- | --------------- | -------------- |
| Object define       | ✅               | ✅              |
| Primitive types     | ❌               | ✅              |
| Union types         | ❌               | ✅              |
| Declaration merging | ✅               | ❌              |
| Extend              | extends         | & intersection |
| Mostly used for     | Objects/classes | Complex types  |

---

## Interface Example

```ts id="b1"
interface User {
  name: string;
}
```

---

## Type Example

```ts id="b2"
type User = {
  name: string;
};
```

---

## Type Special Feature

```ts id="b3"
type Status =
  "success" | "error";
```

Interface ye nahi kar sakta.

---

# 3. When Should You Use Interface?

Use interface when:

* object structures define karne ho
* classes implement karni ho
* scalable project ho
* APIs/models define karne ho

---

## Example

```ts id="c1"
interface User {
  id: number;
  name: string;
}
```

---

# Interview Answer

> Interface mostly objects aur class contracts define karne ke liye use hota hai.

---

# 4. When Should You Use Type Alias?

Use type when:

* union types chahiye
* tuples use karne ho
* primitives define karne ho
* advanced types banana ho

---

## Example

```ts id="d1"
type ID = string | number;
```

---

## Tuple Example

```ts id="d2"
type User = [string, number];
```

---

# Interview Answer

> Type alias advanced typings jaise union, tuple aur conditional types ke liye use hota hai.

---

# 5. How Do You Extend an Interface?

`extends` keyword use hota hai.

---

## Example

```ts id="e1"
interface User {
  name: string;
}

interface Admin extends User {
  role: string;
}
```

---

## Result

```ts id="e2"
const admin: Admin = {
  name: "Krupa",
  role: "Admin"
};
```

---

# Meaning

Admin interface:

* User ke properties inherit karega
* plus extra properties add karega

---

# 6. Can Interface Extend Multiple Interfaces?

## Yes ✅

---

## Example

```ts id="f1"
interface Person {
  name: string;
}

interface Employee {
  company: string;
}

interface Manager
  extends Person, Employee {

  role: string;
}
```

---

## Usage

```ts id="f2"
const manager: Manager = {
  name: "Krupa",
  company: "Google",
  role: "Manager"
};
```

---

# Interview Point

> Interface multiple inheritance support karta hai.

---

# 7. What is Declaration Merging?

Same interface ko multiple times likhne pe TypeScript automatically merge karta hai.

---

# Example

```ts id="g1"
interface User {
  name: string;
}

interface User {
  age: number;
}
```

---

# Final Result

```ts id="g2"
interface User {
  name: string;
  age: number;
}
```

---

# Usage

```ts id="g3"
const user: User = {
  name: "Krupa",
  age: 25
};
```

---

# Important

Declaration merging:

```ts id="g4"
Only interfaces support karti hain
```

Type aliases nahi.

---

# Interview Definition

> Declaration merging mein same interface automatically combine ho jata hai.

---

# 8. What is Structural Typing?

TypeScript structure check karta hai, exact type name nahi.

Simple words:

> Agar structure same hai to compatible hai.

---

# Example

```ts id="h1"
interface User {
  name: string;
}
```

---

# Example Object

```ts id="h2"
const person = {
  name: "Krupa",
  age: 25
};
```

---

# Allowed

```ts id="h3"
const user: User = person;
```

Why?

Because:

```ts id="h4"
name property match kar rahi hai
```

---

# Interview Definition

> TypeScript structure-based typing use karta hai, jise structural typing kehte hain.

---

# 9. What is Index Signature?

Dynamic object properties define karne ke liye use hota hai.

---

# Example

```ts id="i1"
interface Users {
  [key: string]: string;
}
```

---

# Usage

```ts id="i2"
const users: Users = {
  name: "Krupa",
  city: "Pune"
};
```

---

# Meaning

```ts id="i3"
[key: string]: string
```

Means:

* key string hogi
* value string hogi

---

# Number Example

```ts id="i4"
interface Marks {
  [roll: number]: number;
}
```

---

# Interview Use Case

* dynamic objects
* API responses
* dictionaries/maps

---

# 10. Can a Class Implement Multiple Interfaces?

## Yes ✅

Class multiple interfaces implement kar sakti hai.

---

# Example

```ts id="j1"
interface Person {
  name: string;
}

interface Employee {
  salary: number;
}
```

---

# Class

```ts id="j2"
class Manager
  implements Person, Employee {

  name = "Krupa";
  salary = 50000;
}
```

---

# Meaning

Class ko:

* dono interfaces ki properties deni padengi

---

# Important Interview Point

```ts id="j3"
implements
```

class contract enforce karta hai.

---

# Quick Revision Table

| Topic               | Important Point       |
| ------------------- | --------------------- |
| Interface           | Object blueprint      |
| Type                | Advanced typing       |
| extends             | Interface inheritance |
| Multiple extends    | Supported             |
| Declaration merging | Interface only        |
| Structural typing   | Structure matters     |
| Index signature     | Dynamic keys          |
| implements          | Class contract        |


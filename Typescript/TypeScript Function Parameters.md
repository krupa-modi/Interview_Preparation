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


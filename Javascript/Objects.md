# JavaScript Objects Complete Interview Notes

# 1. What is an Object in JavaScript?

Object is a collection of **key-value pairs**.

```js
const user = {
  name: "Krupa",
  age: 25,
  city: "Pune"
};
```
* `name`, `age`, `city` → keys
* `"Krupa"`, `25`, `"Pune"` → values

---

# 2. Why Objects are Used?

Objects are used to store related data together.

Example:

```js
const student = {
  name: "Rahul",
  rollNo: 101,
  course: "BCA"
};
```

Instead of creating separate variables:

```js
let name = "Rahul";
let rollNo = 101;
let course = "BCA";
```

---

# 3. How to Create Object

## Method 1 → Object Literal (Most Used)

```js
const person = {
  name: "Amit",
  age: 22
};
```

---

## Method 2 → Using new Object()

```js
const person = new Object();

person.name = "Amit";
person.age = 22;
```

---

# 4. How to Access Object Values

# A. Dot Notation

```js
const user = {
  name: "Krupa",
  age: 25
};

console.log(user.name);
console.log(user.age);
```

Output:

```js
Krupa
25
```

---

# B. Bracket Notation

```js
console.log(user["name"]);
console.log(user["age"]);
```

---

# 5. Dot vs Bracket Notation

| Dot Notation      | Bracket Notation      |
| ----------------- | --------------------- |
| Easy to write     | Flexible              |
| Mostly used       | Used for dynamic keys |
| No spaces allowed | Spaces allowed        |
| Faster readable   | Useful in loops       |

---

## Dot Notation Example

```js
const user = {
  name: "Krupa"
};

console.log(user.name);
```

---

## Bracket Notation Example

```js
const user = {
  "first name": "Krupa"
};

console.log(user["first name"]);
```

---

## Dynamic Key Example

```js
const key = "age";

const user = {
  age: 25
};

console.log(user[key]);
```

---

# 6. How to Add New Property

```js
const user = {
  name: "Krupa"
};

user.age = 25;

console.log(user);
```

Output:

```js
{
  name: "Krupa",
  age: 25
}
```

---

# 7. How to Update Object Value

```js
const user = {
  name: "Krupa",
  age: 25
};

user.age = 30;

console.log(user);
```

---

# 8. How to Delete Property

```js
const user = {
  name: "Krupa",
  age: 25
};

delete user.age;

console.log(user);
```

---

# 9. How to Check Property Exists or Not

## Using in Operator

```js
const user = {
  name: "Krupa"
};

console.log("name" in user);
```

Output:

```js
true
```

---

## Using hasOwnProperty()

```js
console.log(user.hasOwnProperty("name"));
```

---

# 10. Loop Through Object

# for...in Loop

```js
const user = {
  name: "Krupa",
  age: 25,
  city: "Pune"
};

for (let key in user) {
  console.log(key, user[key]);
}
```

Output:

```js
name Krupa
age 25
city Pune
```

---

# 11. Object Destructuring

Used to extract values from object.

---

## Basic Example

```js
const user = {
  name: "Krupa",
  age: 25
};

const { name, age } = user;

console.log(name);
console.log(age);
```

---

## Rename Variable

```js
const user = {
  name: "Krupa"
};

const { name: userName } = user;

console.log(userName);
```

---

## Default Value

```js
const user = {
  name: "Krupa"
};

const { age = 18 } = user;

console.log(age);
```

---

# 12. Nested Object

```js
const user = {
  name: "Krupa",
  address: {
    city: "Pune",
    state: "MH"
  }
};

console.log(user.address.city);
```

---

# 13. Object Methods

When function is inside object → called method.

```js
const user = {
  name: "Krupa",

  greet: function () {
    console.log("Hello");
  }
};

user.greet();
```

---

# 14. Important Object Methods (VERY IMPORTANT)

# 1. Object.keys()

Returns all keys.

```js
const user = {
  name: "Krupa",
  age: 25
};

console.log(Object.keys(user));
```

Output:

```js
["name", "age"]
```

---

# 2. Object.values()

Returns all values.

```js
console.log(Object.values(user));
```

Output:

```js
["Krupa", 25]
```

---

# 3. Object.entries()

Returns key-value pairs.

```js
console.log(Object.entries(user));
```

Output:

```js
[
  ["name", "Krupa"],
  ["age", 25]
]
```

---

# 4. Object.assign()

Used to copy or merge objects.

```js
const obj1 = {
  a: 1
};

const obj2 = {
  b: 2
};

const result = Object.assign({}, obj1, obj2);

console.log(result);
```

Output:

```js
{
  a: 1,
  b: 2
}
```

---

# 5. Object.freeze()

Cannot add/update/delete properties.

```js
const user = {
  name: "Krupa"
};

Object.freeze(user);

user.name = "Amit";

console.log(user.name);
```

Output:

```js
Krupa
```

---

# 6. Object.seal()

Can update existing values but cannot add/delete.

```js
const user = {
  name: "Krupa"
};

Object.seal(user);

user.name = "Amit";

console.log(user.name);
```

---

# 7. Object.hasOwn()

Checks property exists or not.

```js
const user = {
  name: "Krupa"
};

console.log(Object.hasOwn(user, "name"));
```

---

# 8. Object.create()

Creates new object.

```js
const person = {
  greet() {
    console.log("Hello");
  }
};

const user = Object.create(person);

user.greet();
```

---

# 9. Object.fromEntries()

Converts array into object.

```js
const arr = [
  ["name", "Krupa"],
  ["age", 25]
];

console.log(Object.fromEntries(arr));
```

---

# 10. Object.is()

Checks values are same or not.

```js
console.log(Object.is(10, 10));
```

Output:

```js
true
```

---

# 15. Spread Operator with Object

Used for copying and merging.

---

## Copy Object

```js
const user = {
  name: "Krupa"
};

const copy = { ...user };

console.log(copy);
```

---

## Merge Objects

```js
const obj1 = {
  a: 1
};

const obj2 = {
  b: 2
};

const result = {
  ...obj1,
  ...obj2
};

console.log(result);
```

---

# 16. Optional Chaining

Avoids errors in nested objects.

```js
const user = {
  address: {
    city: "Pune"
  }
};

console.log(user.address?.city);
console.log(user.contact?.phone);
```

---

# 17. Object Interview Questions

# Q1. Difference between Object.freeze() and Object.seal()

| freeze                   | seal             |
| ------------------------ | ---------------- |
| Cannot update/add/delete | Can update only  |
| Fully locked             | Partially locked |

---

# Q2. Difference between Object.keys() and Object.entries()

| keys              | entries                 |
| ----------------- | ----------------------- |
| Returns only keys | Returns key-value pairs |

---

# Q3. Difference between Dot and Bracket Notation

| Dot         | Bracket                 |
| ----------- | ----------------------- |
| Simple      | Dynamic                 |
| No spaces   | Supports spaces         |
| Mostly used | Used for dynamic access |

---

# Q4. What is Object Destructuring?

Object destructuring is a feature used to extract values from objects into variables.

Example:

```js
const user = {
  name: "Krupa",
  age: 25
};

const { name, age } = user;
```

---

# 18. Real Interview Coding Examples

# Example 1 → Count Object Keys

```js
const user = {
  name: "Krupa",
  age: 25,
  city: "Pune"
};

console.log(Object.keys(user).length);
```

---

# Example 2 → Convert Object to Array

```js
const user = {
  name: "Krupa",
  age: 25
};

console.log(Object.entries(user));
```

---

# Example 3 → Merge Two Objects

```js
const obj1 = {
  a: 1
};

const obj2 = {
  b: 2
};

const result = {
  ...obj1,
  ...obj2
};

console.log(result);
```

---

# 19. Important Points for Interview

* Object stores data in key-value format
* Dot notation is mostly used
* Bracket notation used for dynamic keys
* Objects are reference type
* Object.keys(), values(), entries() very important
* Destructuring is frequently asked
* Spread operator important
* freeze vs seal interview favorite question

---

# 20. Quick Revision (Most Important)

```js
Object.keys()
Object.values()
Object.entries()
Object.assign()
Object.freeze()
Object.seal()
Object.create()
Object.fromEntries()
Object.hasOwn()
Object.is()
```

---

# Final Interview Line

> "Objects in JavaScript are used to store data in key-value pairs. We can access properties using dot or bracket notation, update values dynamically, loop through objects using for...in, and use built-in methods like Object.keys(), Object.values(), and Object.entries() for object manipulation."

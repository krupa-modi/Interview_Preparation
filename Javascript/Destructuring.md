## What is Destructuring?

Destructuring is a JavaScript feature used to extract values from:
- Arrays
- Objects

and store them into variables easily.

It makes code cleaner and shorter.

---

# 1. Array Destructuring

## Without Destructuring
```js
const arr = [10, 20, 30];

const a = arr[0];
const b = arr[1];

console.log(a, b);
````

## With Destructuring

```js
const arr = [10, 20, 30];

const [a, b] = arr;

console.log(a, b);
```

### Output

```js
10 20
```

---

# Skip Values in Array

```js
const arr = [10, 20, 30];

const [a, , c] = arr;

console.log(a, c);
```

### Output

```js
10 30
```

---

# Default Values

```js
const arr = [10];

const [a, b = 50] = arr;

console.log(a, b);
```

### Output

```js
10 50
```

---

# 2. Object Destructuring

## Without Destructuring

```js
const user = {
  name: "Krupa",
  age: 25
};

const name = user.name;
const age = user.age;

console.log(name, age);
```

## With Destructuring

```js
const user = {
  name: "Krupa",
  age: 25
};

const { name, age } = user;

console.log(name, age);
```

### Output

```js
Krupa 25
```

---

# Rename Variables

```js
const user = {
  name: "Krupa"
};

const { name: userName } = user;

console.log(userName);
```

### Output

```js
Krupa
```

---

# Default Values in Object

```js
const user = {
  name: "Krupa"
};

const { name, city = "Pune" } = user;

console.log(name, city);
```

### Output

```js
Krupa Pune
```

---

# Nested Destructuring

Nested destructuring means extracting values from nested objects or arrays.

---

# Nested Object Destructuring

## Example

```js
const user = {
  name: "Krupa",
  address: {
    city: "Pune",
    state: "Maharashtra"
  }
};

const {
  address: { city, state }
} = user;

console.log(city, state);
```

### Output

```js
Pune Maharashtra
```

---

# Nested Array Destructuring

```js
const arr = [10, [20, 30]];

const [a, [b, c]] = arr;

console.log(a, b, c);
```

### Output

```js
10 20 30
```

---

# Mixed Nested Destructuring

```js
const user = {
  name: "Krupa",
  skills: ["JS", "React"]
};

const {
  skills: [firstSkill, secondSkill]
} = user;

console.log(firstSkill, secondSkill);
```

### Output

```js
JS React
```

---

# Destructuring in Function Parameters

```js
function printUser({ name, age }) {
  console.log(name, age);
}

printUser({
  name: "Krupa",
  age: 25
});
```

### Output

```js
Krupa 25
```

---

# Interview Advantages

* Cleaner code
* Less repetition
* Easy extraction of data
* Mostly used in:

  * React props
  * API responses
  * Arrays and objects handling

---

# Important Interview Points

## Array Destructuring

Uses `[]`

```js
const [a, b] = arr;
```

## Object Destructuring

Uses `{}`

```js
const { name, age } = user;
```

## Nested Destructuring

Used to extract deeply nested values.

---

# Short Interview Summary

* Destructuring extracts values from arrays/objects
* Makes code shorter and readable
* Array destructuring uses `[]`
* Object destructuring uses `{}`
* Nested destructuring extracts nested values easily

```
```

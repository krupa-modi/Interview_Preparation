# Tuple vs Array (TypeScript)

## Array

An Array is a collection of elements of the **same type**.

### Example

```ts
let numbers: number[] = [1, 2, 3, 4];

let names: string[] = ["Ram", "Shyam", "Mohan"];
```

### Features

- Stores multiple values of the same type.
- Size can grow or shrink.
- Order matters.
- Easy to iterate using map(), filter(), reduce(), etc.

### Example

```ts
let users: string[] = ["Ram", "Shyam"];

users.push("Mohan");

console.log(users);
// ["Ram", "Shyam", "Mohan"]
```

---

## Tuple

A Tuple is an array with a **fixed number of elements** where each element can have a **different type**.

### Example

```ts
let user: [string, number] = ["Ram", 25];
```

Here:

- First value must be string
- Second value must be number

### Valid

```ts
let employee: [string, number, boolean] = [
  "Krupa",
  5,
  true
];
```

### Invalid

```ts
let employee: [string, number] = [25, "Krupa"];
// Error
```

---

# Difference Between Tuple and Array

| Feature | Array | Tuple |
|----------|--------|--------|
| Data Type | Same type values | Different types allowed |
| Length | Dynamic | Fixed |
| Order | Not strict | Strict |
| Type Safety | Less | More |
| Use Case | List of similar items | Fixed structure data |

---

## Example Comparison

### Array

```ts
let userData: string[] = ["Ram", "25", "Pune"];
```

No information about what each index represents.

---

### Tuple

```ts
let userData: [string, number, string] = [
  "Ram",
  25,
  "Pune"
];
```

Clearly defines:

```ts
[Name, Age, City]
```

---

# When to Use Array?

✅ List of users

```ts
const users: string[] = ["Ram", "Shyam", "Mohan"];
```

✅ Product names

```ts
const products: string[] = ["Mobile", "Laptop"];
```

---

# When to Use Tuple?

✅ API response with fixed structure

```ts
const response: [number, string] = [200, "Success"];
```

✅ Coordinates

```ts
const location: [number, number] = [18.5204, 73.8567];
```

✅ User info

```ts
const user: [string, number] = ["Krupa", 25];
```

---

# Interview Answer (Short)

**Array** stores multiple values of the same type and its size can change dynamically.

**Tuple** is a special type of array where the number of elements, their order, and their types are fixed.

Example:

```ts
// Array
let arr: number[] = [1, 2, 3];

// Tuple
let user: [string, number] = ["Ram", 25];
```

**Use Array for lists of similar data and Tuple for fixed structured data.**


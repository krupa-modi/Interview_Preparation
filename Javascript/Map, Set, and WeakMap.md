# Map, Set, and WeakMap in JavaScript

# 1. Map in JavaScript

## Definition

`Map` is a collection of key-value pairs where:

* Keys can be of any data type
* Order is maintained
* Duplicate keys are not allowed

---
# Syntax

```js id="sjb8mh"
const map = new Map();
```

---

# Example

```js id="8p5hvv"
const user = new Map();

user.set("name", "Krupa");
user.set("age", 22);

console.log(user.get("name"));
```

---

# Output

```js id="c5z5q8"
Krupa
```

---

# Important Methods

| Method   | Purpose      |
| -------- | ------------ |
| set()    | Add value    |
| get()    | Get value    |
| delete() | Remove value |
| has()    | Check key    |
| clear()  | Remove all   |

---

# Interview Points

* Stores key-value pairs
* Any datatype can be key
* Maintains insertion order
* Better than object for dynamic data

---

# 2. Set in JavaScript

# Definition

`Set` is a collection of unique values.

Duplicate values are automatically removed.

---

# Syntax

```js id="ndxjlwm"
const set = new Set();
```

---

# Example

```js id="0fb4dn"
const numbers = new Set();

numbers.add(1);
numbers.add(2);
numbers.add(2);
numbers.add(3);

console.log(numbers);
```

---

# Output

```js id="p0i8iq"
Set(3) {1, 2, 3}
```

---

# Important Methods

| Method   | Purpose      |
| -------- | ------------ |
| add()    | Add value    |
| delete() | Remove value |
| has()    | Check value  |
| clear()  | Remove all   |

---

# Use Cases

* Remove duplicates
* Unique data storage
* Fast lookup

---

# Remove Duplicates Example

```js id="qjfdpn"
const arr = [1, 2, 2, 3, 3];

const unique = [...new Set(arr)];

console.log(unique);
```

---

# Output

```js id="1th63y"
[1, 2, 3]
```

---

# Interview Points

* Stores only unique values
* Duplicate values not allowed
* Maintains insertion order

---

# 3. WeakMap in JavaScript

# Definition

`WeakMap` is similar to `Map` but:

* Keys must be objects
* Keys are weakly referenced
* Garbage collection possible

---

# Syntax

```js id="l9mhf0"
const weakMap = new WeakMap();
```

---

# Example

```js id="zlz5pp"
const obj = {};

const weakMap = new WeakMap();

weakMap.set(obj, "Hello");

console.log(weakMap.get(obj));
```

---

# Output

```js id="jq5ebh"
Hello
```

---

# Important Points

* Only objects allowed as keys
* Not iterable
* Used for memory optimization

---

# Why Called WeakMap?

If object reference is removed:

```js id="sx7ye1"
obj = null;
```

JavaScript automatically clears memory.

---

# Use Cases

* Private data
* Caching
* Memory management

---

# Difference Between Map and WeakMap

| Feature            | Map          | WeakMap      |
| ------------------ | ------------ | ------------ |
| Key Type           | Any datatype | Only objects |
| Iterable           | Yes          | No           |
| Garbage Collection | No           | Yes          |
| Memory Efficient   | Less         | More         |

---

# Difference Between Map and Object

| Map                | Object            |
| ------------------ | ----------------- |
| Any datatype key   | String/Symbol key |
| Ordered            | Not guaranteed    |
| Better performance | Less flexible     |

---

# Quick Interview Revision

# Map

```text id="pm5gpd"
Key-value collection
Any datatype as key
```

---

# Set

```text id="r7k5t2"
Stores unique values
No duplicates
```

---

# WeakMap

```text id="i0yiyf"
Only object keys
Garbage collection supported
```

---

# Interview Answer

## What is Map?

Map is a collection of key-value pairs where keys can be of any datatype.

---

## What is Set?

Set is a collection that stores only unique values.

---

## What is WeakMap?

WeakMap is similar to Map but allows only object keys and supports garbage collection for better memory management.

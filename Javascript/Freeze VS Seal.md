## 1. Object.freeze()

`Object.freeze()` makes an object completely immutable.

### Features
- Cannot add new properties
- Cannot delete properties
- Cannot modify existing property values

### Syntax
```js
Object.freeze(obj)
````

### Example

```js
const user = {
  name: "Krupa",
  age: 25
};

Object.freeze(user);

user.age = 30;      // Not allowed
user.city = "Pune"; // Not allowed
delete user.name;   // Not allowed

console.log(user);
```

### Output

```js
{ name: "Krupa", age: 25 }
```

### Interview Point

* Used when data should never change
* Highest level of object protection

---

# 2. Object.seal()

`Object.seal()` partially protects an object.

### Features

* Cannot add new properties
* Cannot delete properties
* CAN modify existing property values

### Syntax

```js
Object.seal(obj)
```

### Example

```js
const user = {
  name: "Krupa",
  age: 25
};

Object.seal(user);

user.age = 30;      // Allowed
user.city = "Pune"; // Not allowed
delete user.name;   // Not allowed

console.log(user);
```

### Output

```js
{ name: "Krupa", age: 30 }
```

### Interview Point

* Structure remains fixed
* Existing values can still change

---

# Difference Between freeze() and seal()

| Feature                | Object.freeze() | Object.seal() |
| ---------------------- | --------------- | ------------- |
| Add properties         | ❌ No            | ❌ No          |
| Delete properties      | ❌ No            | ❌ No          |
| Modify existing values | ❌ No            | ✅ Yes         |
| Object fully immutable | ✅ Yes           | ❌ No          |

---

# Easy Interview Answer

## Object.freeze()

* Completely locks the object
* Nothing can be changed

## Object.seal()

* Locks object structure
* Existing values can still be updated

---

# Important Note

Both methods work only on the first level (Shallow Copy).

### Example

```js
const obj = {
  user: {
    name: "Krupa"
  }
};

Object.freeze(obj);

obj.user.name = "Modi";

console.log(obj.user.name);
```

### Output

```js
Modi
```

Because nested objects are not automatically frozen.

---

# Extra Interview Question

## How to check object is frozen or sealed?

### isFrozen()

```js
Object.isFrozen(obj)
```

### isSealed()

```js
Object.isSealed(obj)
```

---

# Short Interview Summary

* `freeze()` → No add, delete, update
* `seal()` → No add/delete, but update allowed
* `freeze()` gives stronger security than `seal()`

```
```

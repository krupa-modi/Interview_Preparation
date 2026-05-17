# ✅ WeakMap vs Map in JavaScript

# ✅ What is Map?

`Map` ek collection hai jisme:
- key-value pairs store hote hain
- kisi bhi type ki key use kar sakte hain

---

# ✅ Map Example

```js id="p4m8tx"
const map = new Map();

map.set("name", "Aman");
map.set(1, "Number Key");

console.log(map.get("name"));
````

## ✅ Output

```js id="k7q2vl"
Aman
```

---

# ✅ Important Features of Map

✅ Any datatype as key
✅ Ordered data
✅ Iterable hota hai
✅ Size property hoti hai

---

# 🚀 Map Methods

| Method     | Purpose      |
| ---------- | ------------ |
| `set()`    | Add value    |
| `get()`    | Get value    |
| `delete()` | Remove value |
| `has()`    | Check key    |
| `clear()`  | Remove all   |

---
````md id="m8x2qp"
# ✅ JavaScript Map Methods

# 🔥 Create a Map

```js
const map = new Map();
````

---

# ✅ 1. set() → Add Value

Map me key-value pair add karta hai.

## ✅ Example

```js
const map = new Map();

map.set("name", "Aman");

console.log(map);
```

## ✅ Output

```js
Map(1) { 'name' => 'Aman' }
```

---

# ✅ Multiple Values Add

```js
map.set("age", 25);
map.set("city", "Pune");
```

---

# ✅ 2. get() → Get Value

Specific key ki value return karta hai.

## ✅ Example

```js
const map = new Map();

map.set("name", "Aman");

console.log(map.get("name"));
```

## ✅ Output

```js
Aman
```

---

# ❌ Key not found

```js
console.log(map.get("email"));
```

## ✅ Output

```js
undefined
```

---

# ✅ 3. delete() → Remove Value

Specific key remove karta hai.

## ✅ Example

```js
const map = new Map();

map.set("name", "Aman");

map.delete("name");

console.log(map);
```

## ✅ Output

```js
Map(0) {}
```

---

# ✅ delete() Return Value

```js
console.log(map.delete("age"));
```

## ✅ Output

```js
false
```

Because key exist nahi karti.

---

# ✅ 4. has() → Check Key

Check karta hai key present hai ya nahi.

## ✅ Example

```js
const map = new Map();

map.set("name", "Aman");

console.log(map.has("name"));
```

## ✅ Output

```js
true
```

---

# ❌ Key not present

```js
console.log(map.has("age"));
```

## ✅ Output

```js
false
```

---

# ✅ 5. clear() → Remove All

Map ka sara data remove karta hai.

## ✅ Example

```js
const map = new Map();

map.set("name", "Aman");
map.set("age", 25);

map.clear();

console.log(map);
```

## ✅ Output

```js
Map(0) {}
```

---

# 🚀 Complete Example

```js
const map = new Map();

// set
map.set("name", "Aman");

// get
console.log(map.get("name"));

// has
console.log(map.has("name"));

// delete
map.delete("name");

// clear
map.clear();

// size(length)
map.size();
```

# ✅ WeakMap

`WeakMap` bhi key-value pair store karta hai.

BUT:
sirf object keys allow karta hai


# ✅ WeakMap Example

```js id="x8p2la"
const weakMap = new WeakMap();

const obj = {};

weakMap.set(obj, "Hello");

console.log(weakMap.get(obj));
```

## ✅ Output

```js id="q5m7vr"
Hello
```

---

# ❌ Invalid Example

```js id="t1k8wp"
weakMap.set("name", "Aman");
```

## ❌ Error

Because string key allowed nahi hai.

---

# 🔥 Main Difference

# ✅ Map

```js id="f9q2mt"
Any type key allowed
```

---

# ✅ WeakMap

```js id="e4r7lx"
Only object keys allowed
```

---

# 🔥 Garbage Collection Difference

## Map

Object delete hone ke baad bhi memory me reh sakta hai.

---

## WeakMap

Agar object ka reference remove ho gaya:

```js id="a7m1vp"
automatically garbage collect ho jata hai
```

Memory optimization better hota hai ✅

---

# ⚡ Iterable Difference

## Map

```js id="n2x8tk"
for...of use kar sakte
```

---

## WeakMap

```js id="b6p4qw"
iterable nahi hota
```

---

# ❌ WeakMap Loop Example

```js id="r5m9vx"
for (let item of weakMap) {
}
```

## ❌ Error

Because WeakMap iterable nahi hai.

---

# 🚀 Main Difference Table

| Feature            | Map                  | WeakMap           |
| ------------------ | -------------------- | ----------------- |
| Key Type           | Any type             | Only objects      |
| Iterable           | Yes                  | No                |
| Size property      | Yes                  | No                |
| Garbage Collection | No automatic cleanup | Automatic cleanup |
| Memory Efficient   | Less                 | More              |

---

# 🎯 Interview Definition

## Map

> Map key-value collection hai jisme any datatype key use kar sakte hain.

---

## WeakMap

> WeakMap sirf object keys support karta hai aur unused objects automatically garbage collect ho jate hain.

---

# 🔥 Real Use Case

## Map

```js id="c7t2mr"
General data storage
```

---

## WeakMap

```js id="w4q8lp"
Private object data
memory optimization
```

---

# 🎯 Most Asked Interview Question

## Q:

Why WeakMap is called "Weak"?

## ✅ Answer:

Because object references weakly held hote hain,
isliye unused objects garbage collection me remove ho jate hain.

---

# 💡 One-Line Memory Trick

```js id="y9m3qt"
Map → any key

WeakMap → only object key
```


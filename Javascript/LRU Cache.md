# 📌 What is LRU Cache?

LRU ka full form hai:

# 🔥 Least Recently Used

LRU Cache ek data structure/design pattern hai jo:

> Most recently used data ko cache me rakhta hai aur least recently used data ko remove kar deta hai.

---
# 📌 Real Life Example

Suppose browser cache.

Aap recently visited pages ko fast access kar sakte ho.

Agar cache full ho gaya:

✅ Sabse purana/least used page remove ho jayega.

---

# 📌 Why LRU Cache Used?

Performance improve karne ke liye.

Mostly use hota hai:

* Browser caching
* API caching
* Database caching
* React query caching
* Redux persistence
* Node.js applications

---

# 📌 Main Idea

## Rules

### ✅ Recently used item

cache me rahega.

### ❌ Least recently used item

remove ho jayega when limit exceeded.

---

# 📌 Example

Cache size:

```js id="0hkv56"
2
```

Operations:

```js id="g8k7ua"
put(1)
put(2)
get(1)
put(3)
```

---

# 📌 Explanation

## Step 1

```js id="4db80h"
[1]
```

---

## Step 2

```js id="6l7ct1"
[1, 2]
```

---

## Step 3

```js id="7uc9dc"
get(1)
```

Now `1` recently used ho gaya:

```js id="bfqzdu"
[2, 1]
```

---

## Step 4

```js id="ij1wws"
put(3)
```

Cache full hai.

Least recently used:

```js id="u0c0o4"
2
```

remove ho jayega.

Final:

```js id="hy7vdh"
[1, 3]
```

---

# 📌 LRU Cache Operations

| Operation       | Work              |
| --------------- | ----------------- |
| get(key)        | Value fetch       |
| put(key, value) | Insert/update     |
| remove oldest   | Least used delete |

---

# 📌 JavaScript LRU Cache Using Map 🔥

`Map` insertion order maintain karta hai.

Isliye LRU implement karna easy ho jata hai.

---

# 📌 LRU Cache Implementation

```js id="jlwm6f"
class LRUCache {
  constructor(limit) {
    this.limit = limit;
    this.cache = new Map();
  }

  get(key) {
    if (!this.cache.has(key)) {
      return -1;
    }

    const value = this.cache.get(key);

    // recently used banane ke liye delete + reinsert
    this.cache.delete(key);
    this.cache.set(key, value);

    return value;
  }

  put(key, value) {
    // agar already present hai
    if (this.cache.has(key)) {
      this.cache.delete(key);
    }

    // cache full ho gaya
    else if (this.cache.size === this.limit) {
      // first inserted remove karo
      const firstKey = this.cache.keys().next().value;
      this.cache.delete(firstKey);
    }

    this.cache.set(key, value);
  }
}
```

---

# 📌 Usage

```js id="rr6a8g"
const lru = new LRUCache(2);

lru.put(1, "A");
lru.put(2, "B");

console.log(lru.get(1));

lru.put(3, "C");

console.log(lru.get(2));
```

---

# 📌 Output

```js id="w0d8wb"
A
-1
```

---

# 📌 How This Works

## ✅ Map maintains insertion order

```js id="dtn9rq"
Map()
```

---

## ✅ Recently used item ko last me move karte hain

```js id="kw9l2k"
delete + set
```

---

## ✅ First item = least recently used

```js id="mgk0v9"
map.keys().next().value
```

---

# 📌 Time Complexity

| Operation | Complexity |
| --------- | ---------- |
| get()     | O(1)       |
| put()     | O(1)       |

---

# 📌 Why Interviewers Ask LRU Cache?

Ye concepts test karta hai:

* Data structures
* HashMap/Map
* Optimization
* Caching logic
* Problem solving

---

# 📌 Advanced Real Implementation

Real-world LRU Cache mostly use karta hai:

* HashMap
* Doubly Linked List

Kyuki dono operations O(1) me ho jate hain.

---

# 📌 Difference Between Cache & LRU Cache

| Cache               | LRU Cache               |
| ------------------- | ----------------------- |
| Stores data         | Stores recent data      |
| No removal strategy | Removes least used item |

---

# 📌 Real Interview Definition

> LRU Cache (Least Recently Used Cache) is a caching mechanism that removes the least recently accessed item when the cache reaches its limit. It is used to optimize performance and memory usage.

---

# 📌 Interview Important Points 🔥

| Topic       | Important                |
| ----------- | ------------------------ |
| Full Form   | Least Recently Used      |
| Removes     | Least recently used item |
| Best DS     | Map + Doubly Linked List |
| JS Easy Way | Map                      |
| Complexity  | O(1)                     |

---

# 📌 Short Interview Answer

> LRU Cache is a caching mechanism where the least recently used data is removed first when the cache becomes full. In JavaScript, it can be efficiently implemented using Map because Map maintains insertion order.

# JavaScript String Methods Notes (Interview Quick Revision)

## 📌 String kya hota hai?

String text data ko store karta hai.

```js
let str = "Hello";
```

---

# 🔹 String Access Methods

## 1. charAt()

Character access karta hai index se.

```js
let str = "Hello";

console.log(str.charAt(1)); // e
```

### Use Case:

* Specific character nikalna.

---

## 2. at()

Positive aur negative index support karta hai.

```js
let str = "Hello";

console.log(str.at(-1)); // o
```

### Use Case:

* Last character access karna.

---

## 3. indexOf()

Character/string ka first index deta hai.

```js
let str = "JavaScript";

console.log(str.indexOf("S")); // 4
```

### Use Case:

* Value exist karti hai ya nahi check karna.

---

## 4. lastIndexOf()

Last occurrence ka index deta hai.

```js
let str = "hello hello";

console.log(str.lastIndexOf("hello")); // 6
```

### Use Case:

* Last matching position find karna.

---

## 5. includes()

Check karta hai string present hai ya nahi.

```js
let str = "JavaScript";

console.log(str.includes("Script")); // true
```

### Use Case:

* Search functionality.

---

## 6. startsWith()

Starting check karta hai.

```js
let str = "JavaScript";

console.log(str.startsWith("Java")); // true
```

### Use Case:

* URL/path validation.

---

## 7. endsWith()

Ending check karta hai.

```js
let str = "image.png";

console.log(str.endsWith(".png")); // true
```

### Use Case:

* File extension check.

---

# 🔹 Add / Combine String Methods

## 8. concat()

Strings join karta hai.

```js
let a = "Hello";
let b = "World";

console.log(a.concat(" ", b)); // Hello World
```

### Use Case:

* Multiple strings combine karna.

---

## 9. repeat()

String repeat karta hai.

```js
let str = "Hi ";

console.log(str.repeat(3)); // Hi Hi Hi
```

### Use Case:

* Pattern generate karna.

---

## 10. padStart()

Start me value add karta hai.

```js
let num = "5";

console.log(num.padStart(3, "0")); // 005
```

### Use Case:

* OTP / ID formatting.

---

## 11. padEnd()

End me value add karta hai.

```js
let num = "5";

console.log(num.padEnd(3, "0")); // 500
```

### Use Case:

* Table formatting.

---

# 🔹 Remove / Delete / Extract Methods

## 12. slice()

Part extract karta hai.

```js
let str = "JavaScript";

console.log(str.slice(0, 4)); // Java
```

### Use Case:

* Substring nikalna.

---

## 13. substring()

Slice jaisa hi hai.
```js
let str = "JavaScript";

console.log(str.substring(4, 10)); // Script
```

### Use Case:

* Text extraction.

---

## 14. substr() ❌ (Old)

```js
let str = "JavaScript";

console.log(str.substr(4, 6)); // Script
```

### Note:

* Deprecated method.

---

## 15. replace()

Single value replace karta hai.

```js
let str = "Hello World";

console.log(str.replace("World", "JS")); // Hello JS
```

### Use Case:

* Text update karna.

---

## 16. replaceAll()

Saare matches replace karta hai.

```js
let str = "a-b-c";

console.log(str.replaceAll("-", " ")); // a b c
```

### Use Case:

* Global replacement.

---

## 17. trim()

Start/end spaces remove karta hai.

```js
let str = "  hello  ";

console.log(str.trim()); // hello
```

### Use Case:

* Form input cleanup.

---

## 18. trimStart()

Starting spaces remove karta hai.

```js
let str = "   hello";

console.log(str.trimStart());
```

---

## 19. trimEnd()

Ending spaces remove karta hai.

```js
let str = "hello   ";

console.log(str.trimEnd());
```

---

# 🔹 Convert Methods

## 20. toUpperCase()

Uppercase me convert karta hai.

```js
let str = "hello";

console.log(str.toUpperCase()); // HELLO
```

### Use Case:

* Case insensitive comparison.

---

## 21. toLowerCase()

Lowercase me convert karta hai.

```js
let str = "HELLO";

console.log(str.toLowerCase()); // hello
```

### Use Case:

* Search/filter.

---

## 22. split()

String ko array me convert karta hai.

```js
let str = "a,b,c";

console.log(str.split(",")); // ['a','b','c']
```

### Use Case:

* CSV/string parsing.

---

# 🔹 Search Methods

## 23. search()

Pattern search karta hai.

```js
let str = "JavaScript";

console.log(str.search("Script")); // 4
```

### Use Case:

* Regex searching.

---

## 24. match()

Matching values return karta hai.

```js
let str = "abc123";

console.log(str.match(/[0-9]/g)); // ['1','2','3']
```

### Use Case:

* Regex validation.

---

## 25. matchAll()

All matches iterator return karta hai.

```js
let str = "test1 test2";

console.log([...str.matchAll(/test/g)]);
```

### Use Case:

* Advanced regex matching.

---

# 🔹 Comparison Methods

## 26. localeCompare()

2 strings compare karta hai.

```js
console.log("a".localeCompare("b")); // -1
```

### Use Case:

* Sorting strings.

---

# 🔹 Character Code Methods

## 27. charCodeAt()

ASCII/Unicode value deta hai.

```js
let str = "A";

console.log(str.charCodeAt(0)); // 65
```

### Use Case:

* Encoding logic.

---

## 28. fromCharCode()

Code se character banata hai.

```js
console.log(String.fromCharCode(65)); // A
```

### Use Case:

* Character generation.

---

# 🔹 Template Literals

## 29. Template String (` `)

Dynamic string banata hai.

```js
let name = "Krupa";

console.log(`Hello ${name}`);
```

### Use Case:

* Dynamic UI messages.

---

# 🔹 Important Interview Points

## ✅ String Immutable hoti hai

Original string change nahi hoti.

```js
let str = "hello";

str.replace("h", "H");

console.log(str); // hello
```

---

# 🔥 Most Important Methods for Interview

* slice()
* split()
* replace()
* replaceAll()
* includes()
* indexOf()
* trim()
* toUpperCase()
* toLowerCase()
* startsWith()
* endsWith()

---

# 🚀 Real Project Use Cases

| Method        | Real Use                |
| ------------- | ----------------------- |
| trim()        | Form validation         |
| split()       | CSV/Data parsing        |
| replace()     | Text cleanup            |
| includes()    | Search feature          |
| startsWith()  | Route validation        |
| endsWith()    | File checking           |
| toLowerCase() | Case insensitive search |
| slice()       | Masking data            |

---

# 📌 Quick Difference

| Method       | Difference             |
| ------------ | ---------------------- |
| slice()      | Negative index support |
| substring()  | Negative support nahi  |
| replace()    | Single replace         |
| replaceAll() | All replace            |
| charAt()     | Positive index         |
| at()         | Negative bhi support   |

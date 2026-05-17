# ✅ localStorage vs sessionStorage vs Cookies

# 🔥 What are these?

Ye browser storage mechanisms hain.

Used for:
- data store karna
- user info save karna
- login/session manage karna

---

# ✅ 1. localStorage

## 📌 Definition

Data permanently browser me store hota hai  
until manually delete na karo.

---

# 🚀 Example

```js id="4w8s2m"
localStorage.setItem("name", "Aman");
````

## Get Data

```js id="4t6m9a"
localStorage.getItem("name");
```

## Remove Data

```js id="n2l7dx"
localStorage.removeItem("name");
```

## Clear All

```js id="g1u9vp"
localStorage.clear();
```

---

# ⚡ Key Points

✅ Data browser close hone ke baad bhi rahta hai
✅ Expiry nahi hoti
✅ Around 5MB storage

---

# 🎯 Use Cases

* Theme save karna
* Cart items
* Remember me feature

---

# ✅ 2. sessionStorage

## 📌 Definition

Data sirf current browser tab/session tak rahta hai.

Tab close → data delete ❌

---

# 🚀 Example

```js id="m9j4zt"
sessionStorage.setItem("user", "Rahul");
```

## Get Data

```js id="2f0h1v"
sessionStorage.getItem("user");
```

---

# ⚡ Key Points

✅ Tab-specific storage
✅ Browser/tab close hone par delete
✅ Around 5MB storage

---

# 🎯 Use Cases

* Temporary form data
* OTP/session data
* Multi-step forms

---

# ✅ 3. Cookies

## 📌 Definition

Cookies small data pieces hote hain
jo browser aur server dono access kar sakte hain.

---

# 🚀 Example

```js id="2j7s0k"
document.cookie = "username=Aman";
```

---

# ⚡ Key Points

✅ Automatically server ko send hote hain
✅ Expiry set kar sakte hain
✅ Small storage (~4KB)

---

# 🎯 Use Cases

* Authentication
* Session management
* Tracking

---

# 🚀 Main Difference Table

| Feature       | localStorage | sessionStorage | Cookies    |
| ------------- | ------------ | -------------- | ---------- |
| Storage Limit | ~5MB         | ~5MB           | ~4KB       |
| Expiry        | No expiry    | Tab close      | Can expire |
| Server Access | No           | No             | Yes        |
| Persistent    | Yes          | No             | Depends    |
| Browser Close | Data stays   | Data removed   | Depends    |

---

# 🔥 Important Interview Question

## Q:

Difference between localStorage and sessionStorage?

## ✅ Answer:

| localStorage                         | sessionStorage       |
| ------------------------------------ | -------------------- |
| Permanent storage                    | Temporary storage    |
| Browser close ke baad bhi data rahta | Tab close par delete |
| Shared across tabs                   | Tab specific         |

---

# 🔥 Important Interview Question

## Q:

Why cookies are used for authentication?

## ✅ Answer:

Because cookies automatically server ke saath send hote hain in every request.

---

# ⚠️ Security Point

## localStorage

```js id="1f4z0y"
More vulnerable to XSS attacks
```

Sensitive token store avoid karna chahiye.

---

## Cookies

```js id="eq3w1v"
HttpOnly cookies more secure
```

---

# 🚀 Real Example

## localStorage

```js id="x4r7dp"
Save dark mode preference
```

---

## sessionStorage

```js id="l8k6qw"
Temporary form data
```

---

## Cookies

```js id="j9p2na"
JWT authentication token
```

---

# 🎯 Short Interview Answer

> localStorage permanent browser storage hai,
> sessionStorage temporary tab-based storage hai,
> aur cookies small data storage hai jo server ke saath automatically send hota hai.

---

# 💡 Quick Revision

| Storage        | Best For               |
| -------------- | ---------------------- |
| localStorage   | Permanent data         |
| sessionStorage | Temporary session data |
| Cookies        | Authentication         |

---

# 🚀 One-Line Memory Trick

```js id="y2d9qt"
localStorage → permanent

sessionStorage → tab tak

cookies → server communication
```

# 🔑 `keyof` & `typeof` in TypeScript – Interview Guide

---

## 1. What is `typeof` in TypeScript?

`typeof` is used to **get the type of a variable or object** and reuse it.

👉 Helps avoid rewriting types manually.

---

### 🔍 Example

```ts
const user = {
  name: "Krupa",
  age: 25,
};

type UserType = typeof user;
```

👉 Result:

```ts
type UserType = {
  name: string;
  age: number;
};
```

---

### 🔥 Use Case

* Reuse existing object types
* Keep types in sync with data

---

## 2. What is `keyof` in TypeScript?

`keyof` is used to get **all keys of a type as a union**

---

### 🔍 Example

```ts
type User = {
  name: string;
  age: number;
};

type UserKeys = keyof User;
```

👉 Result:

```ts
type UserKeys = "name" | "age";
```

---

### 🔥 Use Case

* Restrict keys
* Dynamic property access

---

## 3. Using `keyof` with Functions

```ts
function getValue<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}

const user = { name: "Krupa", age: 25 };

getValue(user, "name"); // ✅
getValue(user, "age");  // ✅
```

👉 Type-safe key access

---

## 4. Combining `typeof` + `keyof` 🔥

👉 Very important for interviews

```ts
const user = {
  name: "Krupa",
  age: 25,
};

type Keys = keyof typeof user;
```

👉 Result:

```ts
type Keys = "name" | "age";
```

---

## 5. Real-World Example

```ts
const roles = {
  admin: "ADMIN",
  user: "USER",
};

type RoleKeys = keyof typeof roles;
```

👉 Output:

```ts
type RoleKeys = "admin" | "user";
```

---

## 6. Difference: `keyof` vs `typeof`

| Feature  | `typeof`             | `keyof`          |
| -------- | -------------------- | ---------------- |
| Purpose  | Get type of variable | Get keys of type |
| Output   | Object type          | Union of keys    |
| Use Case | Reuse types          | Restrict keys    |

---

# 🎯 Final Interview Answer (Short)

👉 `typeof` is used to extract the type of a variable.
👉 `keyof` is used to get all keys of a type as a union.

👉 Together, they help create **dynamic and type-safe code**.

---

💡 **Pro Tip:**
Say this 👇
👉 “keyof with typeof is commonly used for type-safe object key access” 🚀

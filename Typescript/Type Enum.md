
# 📘 TypeScript Enums: Numeric vs String Enum (In-Depth)

## 🔹 What is an Enum?

### 👉 Definition

An **enum (enumeration)** is a special TypeScript feature that allows you to define a set of named constants.

### 👉 Example

```ts
enum Role {
  Admin,
  User
}
```

👉 Behind the scenes:

```ts
Role.Admin = 0
Role.User = 1
```

---

# 🔹 1. Numeric Enum

## 👉 Definition

By default, TypeScript assigns **numeric values** starting from `0`.

## 👉 Example

```ts
enum Status {
  Pending,
  InProgress,
  Completed
}

console.log(Status.Pending);     // 0
console.log(Status[0]);          // "Pending"
```

## 👉 Custom Numeric Values

```ts
enum Status {
  Pending = 1,
  InProgress,
  Completed
}
```

👉 Output:

```ts
Pending = 1
InProgress = 2
Completed = 3
```

---

## 🔥 Reverse Mapping (Important)

Numeric enums support **reverse mapping**:

```ts
enum Role {
  Admin,
  User
}

console.log(Role.Admin); // 0
console.log(Role[0]);    // "Admin"
```

👉 This is useful for debugging.

---

## ⚠️ Problem with Numeric Enum

```ts
enum Role {
  Admin,
  User
}

let userRole: Role = 10; // ❗ Allowed (unsafe)
```

👉 TypeScript allows **any number**, which can cause bugs.

---

# 🔹 2. String Enum

## 👉 Definition

String enums assign **explicit string values**.

## 👉 Example

```ts
enum Role {
  Admin = "ADMIN",
  User = "USER"
}

console.log(Role.Admin); // "ADMIN"
```

---

## ❌ No Reverse Mapping

```ts
console.log(Role["ADMIN"]); // ❌ undefined
```

👉 String enums do NOT support reverse mapping.

---

## ✅ Safer than Numeric Enum

```ts
let role: Role = Role.Admin;   // ✅
role = "ADMIN";                // ❌ Error
```

👉 Only defined values are allowed.

---

# 🔹 Numeric vs String Enum (Comparison)

| Feature         | Numeric Enum              | String Enum             |
| --------------- | ------------------------- | ----------------------- |
| Default Values  | Numbers (0,1,2...)        | Must define manually    |
| Reverse Mapping | ✅ Yes                     | ❌ No                    |
| Type Safety     | ❌ Less safe               | ✅ More safe             |
| Debugging       | Hard (numbers)            | Easy (readable strings) |
| Runtime Output  | Object with both mappings | Simple object           |
| Flexibility     | Auto increment            | No auto increment       |

---

# 🔹 Internal JavaScript Output

## 👉 Numeric Enum Compiles To:

```js
var Role;
(function (Role) {
  Role[Role["Admin"] = 0] = "Admin";
  Role[Role["User"] = 1] = "User";
})(Role || (Role = {}));
```

---

## 👉 String Enum Compiles To:

```js
var Role;
(function (Role) {
  Role["Admin"] = "ADMIN";
  Role["User"] = "USER";
})(Role || (Role = {}));
```

---

# 🔹 When to Use What?

## 👉 Use Numeric Enum

* When performance matters
* When values don’t need to be human-readable
* Example: internal flags, indexes

## 👉 Use String Enum (Recommended)

* For APIs
* For debugging
* For readability
* For strict type safety

---

# 🔹 Real Interview Example

```ts
enum API_STATUS {
  SUCCESS = "SUCCESS",
  ERROR = "ERROR",
  LOADING = "LOADING"
}

function handleResponse(status: API_STATUS) {
  if (status === API_STATUS.SUCCESS) {
    console.log("Data loaded");
  }
}
```

---

# 🔥 Final Summary

* Numeric Enum:

  * Auto values (0,1,2)
  * Supports reverse mapping
  * Less safe

* String Enum:

  * Explicit values
  * No reverse mapping
  * More safe & readable ✅

---

## 💡 Pro Tip (Important for Interviews)

👉 In modern TypeScript:

* Prefer **string enums** OR
* Use **union types instead of enums**

```ts
type Role = "ADMIN" | "USER";
```


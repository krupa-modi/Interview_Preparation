# Difference Between `Exclude` and `Extract` in TypeScript

`Exclude` aur `Extract` TypeScript ke built-in utility types hain.

Dono mostly **union types** ke saath use hote hain.

* `Exclude` → unwanted types remove karta hai
* `Extract` → matching/common types select karta hai

---

# 1. `Exclude<Type, Union>`

## 👉 Meaning

Union type me se specific types remove karta hai.

---

## Syntax

```ts id="o8j3nf"
Exclude<Type, RemovedType>
```

---

## Example

```ts id="m4t7xp"
type Roles = "admin" | "user" | "guest";

type NewRoles = Exclude<Roles, "guest">;
```

### Result

```ts id="f1k9we"
type NewRoles = "admin" | "user"
```

✅ `"guest"` remove ho gaya.

---

# Real-world Use Case

## Example: API Status

```ts id="u5n2qy"
type Status =
  | "loading"
  | "success"
  | "error";

type ActiveStatus = Exclude<
  Status,
  "loading"
>;
```

### Result

```ts id="d8r4mh"
"success" | "error"
```

---

# 2. `Extract<Type, Union>`

## 👉 Meaning

Sirf matching/common types ko pick karta hai.

---

## Syntax

```ts id="w6p1za"
Extract<Type, MatchingType>
```

---

## Example

```ts id="q9x7lv"
type Roles =
  | "admin"
  | "user"
  | "guest";

type SelectedRole = Extract<
  Roles,
  "admin" | "user"
>;
```

### Result

```ts id="s3v8kt"
type SelectedRole = "admin" | "user"
```

✅ Sirf matching values retain hui.

---

# Real-world Use Case

## Example: Filter Specific Events

```ts id="g7n2uc"
type Events =
  | "click"
  | "scroll"
  | "hover";

type MouseEvents = Extract<
  Events,
  "click" | "hover"
>;
```

---

# Main Difference

| Feature    | Exclude                | Extract                         |
| ---------- | ---------------------- | ------------------------------- |
| Purpose    | Types remove karta hai | Matching types select karta hai |
| Works Like | Filter OUT             | Filter IN                       |
| Output     | Remaining types        | Common types                    |

---

# Easy Trick to Remember

## `Exclude`

👉 “Ye hata do”

```ts id="y2p6df"
Exclude<"a" | "b", "a">
```

Result:

```ts id="r5m8xj"
"b"
```

---

## `Extract`

👉 “Ye nikal lo”

```ts id="h1q4nc"
Extract<"a" | "b", "a">
```

Result:

```ts id="t7k3pe"
"a"
```

---

# Advanced Example

```ts id="p8z2mw"
type Data =
  | string
  | number
  | boolean;

type OnlyString = Extract<Data, string>;

type WithoutBoolean = Exclude<
  Data,
  boolean
>;
```

---

# Interview Perspective

## When to Use `Exclude`

* Restricted values remove karna
* Unwanted states avoid karna
* Feature permissions filter karna

---

## When to Use `Extract`

* Specific matching types pick karna
* Event filtering
* API response narrowing

---

# Interview Line

> “Exclude removes types from a union, while Extract keeps only matching types from a union.”

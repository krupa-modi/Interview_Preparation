## What are Conditional Types?

Conditional Types TypeScript mein types ke upar conditions apply karne ke liye use hote hain.

Simple language mein:

> Agar ek type dusre type ko follow karta hai to ek type return karo, warna dusra.

Ye bilkul JavaScript ke ternary operator jaisa hota hai.

---

# JavaScript Example

```js id="ph0z7e"
let result = age >= 18 ? "Adult" : "Minor";
```

Yaha:

* condition true → `"Adult"`
* condition false → `"Minor"`

---

# TypeScript Conditional Type

```ts id="jjlwm8"
type Result<T> =
  T extends string
    ? "Yes"
    : "No";
```

Yaha:

* agar `T` string hai → `"Yes"`
* warna → `"No"`

---

# Basic Syntax

```ts id="x8b6ul"
T extends U ? X : Y
```

## Meaning

| Part      | Meaning       |
| --------- | ------------- |
| T         | Type to check |
| extends U | Condition     |
| X         | True case     |
| Y         | False case    |

---

# First Example

```ts id="g1x4ls"
type CheckString<T> =
  T extends string
    ? "It is string"
    : "Not string";
```

---

# Usage

```ts id="20pnuv"
type A = CheckString<string>;
type B = CheckString<number>;
```

---

# Result

```ts id="kvhyv7"
type A = "It is string"

type B = "Not string"
```

---

# Step-by-Step Working

## Example

```ts id="gz8b2j"
type Check<T> =
  T extends string
    ? true
    : false;
```

Now:

```ts id="3m5wm6"
type Result = Check<string>;
```

Internally TypeScript check karta hai:

```ts id="ns9q1d"
string extends string
```

Condition true hai.

So result:

```ts id="7u9u5g"
type Result = true
```

---

# Example 2 — Number Check

```ts id="l7t67v"
type IsNumber<T> =
  T extends number
    ? "Number"
    : "Other";
```

## Usage

```ts id="w9gf7d"
type A = IsNumber<10>;
type B = IsNumber<boolean>;
```

## Result

```ts id="4n24f4"
type A = "Number"

type B = "Other"
```

---

# Real Need of Conditional Types

Conditional Types mostly use hote hain:

* type filtering
* type extraction
* utility types
* API response handling
* reusable generic logic
* infer keyword ke sath type nikalne mein

---

# Example 3 — Array Check

```ts id="h3ay0n"
type IsArray<T> =
  T extends any[]
    ? true
    : false;
```

---

# Usage

```ts id="mhmv78"
type A = IsArray<string[]>;
type B = IsArray<number>;
```

---

# Result

```ts id="vj5f4w"
type A = true

type B = false
```

---

# Example 4 — Function Check

```ts id="pq3cl4"
type IsFunction<T> =
  T extends Function
    ? true
    : false;
```

---

# Usage

```ts id="czn08m"
type A = IsFunction<() => void>;
type B = IsFunction<string>;
```

---

# Result

```ts id="yrpjv7"
type A = true

type B = false
```

---

# infer Keyword

`infer` Conditional Types ka bahut important part hai.

Ye type ko extract karne ke liye use hota hai.

Simple words mein:

> infer hidden type ko pakad leta hai.

---

# Example 5 — Extract Function Return Type

```ts id="u2qfhj"
type GetReturnType<T> =
  T extends (...args: any[]) => infer R
    ? R
    : never;
```

---

# Breakdown

```ts id="f3w4kz"
(...args: any[]) => infer R
```

Means:

* function ka return type nikal lo
* usko `R` mein store karo

---

# Usage

```ts id="rkqbhf"
type Result =
  GetReturnType<() => string>;
```

---

# Result

```ts id="u9n3g5"
type Result = string
```

---

# Another Example

```ts id="yknshx"
type Result =
  GetReturnType<() => number>;
```

## Result

```ts id="8m83cz"
type Result = number
```

---

# Example 6 — Extract Array Element Type

```ts id="ys6tfx"
type ElementType<T> =
  T extends (infer U)[]
    ? U
    : never;
```

---

# Usage

```ts id="w02jup"
type A = ElementType<string[]>;
type B = ElementType<number[]>;
```

---

# Result

```ts id="1i9jxl"
type A = string

type B = number
```

---

# How It Works

For:

```ts id="yzbx3z"
string[]
```

TypeScript checks:

```ts id="rw8p6v"
(infer U)[]
```

Yaha:

```ts id="xgtfvi"
U = string
```

---

# never in Conditional Types

`never` means:

> kuch bhi nahi

Mostly filtering ke liye use hota hai.

---

# Example 7 — Remove String

```ts id="2evih1"
type RemoveString<T> =
  T extends string
    ? never
    : T;
```

---

# Usage

```ts id="vf57vs"
type Result =
  RemoveString<
    string | number | boolean
  >;
```

---

# Result

```ts id="ppc7j9"
type Result = number | boolean
```

---

# Why?

Because:

```ts id="pybgg0"
string → never
number → number
boolean → boolean
```

Final:

```ts id="v70n4u"
number | boolean
```

---

# Distributive Conditional Types

Bahut important concept.

Conditional Types union pe automatically loop karte hain.

---

# Example

```ts id="kh6v0t"
type Example<T> =
  T extends string
    ? T
    : never;
```

---

# Usage

```ts id="lz0v1n"
type Result =
  Example<
    string | number | boolean
  >;
```

---

# Internal Working

TypeScript internally karta hai:

```ts id="2b12d0"
string extends string
  ? string
  : never

number extends string
  ? number
  : never

boolean extends string
  ? boolean
  : never
```

---

# Final Result

```ts id="iqmb6l"
type Result = string
```

---

# Real World Example

# API Response

```ts id="i8k55u"
type ApiResponse<T> =
  T extends string
    ? { message: T }
    : { data: T };
```

---

# Usage

```ts id="g5vj1y"
type A =
  ApiResponse<string>;

type B =
  ApiResponse<number>;
```

---

# Result

```ts id="zlwtvt"
type A = {
  message: string;
}

type B = {
  data: number;
}
```

---

# Built-in Utility Types Using Conditional Types

---

# Exclude

```ts id="yqf5ry"
type Exclude<T, U> =
  T extends U
    ? never
    : T;
```

## Example

```ts id="uc30q2"
type Result =
  Exclude<
    string | number,
    string
  >;
```

## Result

```ts id="jlwmz7"
type Result = number
```

---

# Extract

```ts id="1on6bw"
type Extract<T, U> =
  T extends U
    ? T
    : never;
```

## Example

```ts id="kkcf5g"
type Result =
  Extract<
    string | number,
    string
  >;
```

## Result

```ts id="mkxg12"
type Result = string
```

---

# NonNullable

```ts id="tlf7ll"
type NonNullable<T> =
  T extends null | undefined
    ? never
    : T;
```

---

# Example

```ts id="kgd07m"
type Result =
  NonNullable<
    string | null | undefined
  >;
```

---

# Result

```ts id="6m3j49"
type Result = string
```

---

# Important Interview Points

| Topic               | Important                            |
| ------------------- | ------------------------------------ |
| extends             | Condition check karta hai            |
| infer               | Type extract karta hai               |
| never               | Filtering mein use hota hai          |
| Distributive Nature | Union pe automatically loop hota hai |
| Mostly Used With    | Generics                             |

---

# Easy Definition for Interview

> Conditional Types TypeScript mein type ke upar conditions apply karne ke liye use hote hain.
> Agar condition true ho to ek type return hota hai, warna dusra.

---

# Final Quick Revision

| Concept          | Meaning              |
| ---------------- | -------------------- |
| T extends U      | Type condition       |
| ?                | True case            |
| :                | False case           |
| infer            | Type extract         |
| never            | Remove/filter type   |
| Conditional Type | Condition based type |

## What are Mapped Types?

Mapped Types are used to create a new type by looping through properties of an existing type.

Simple words mein:

> Ek existing type ke sabhi properties ko modify karke naya type banana.

Mapped Types mostly use hote hain:

* optional banane ke liye
* readonly banane ke liye
* property type change karne ke liye
* custom utility types banane ke liye

---

# Basic Syntax

```ts id="eb56wh"
type NewType<T> = {
  [Key in keyof T]: T[Key];
};
```

---

# Important Keywords

| Keyword | Meaning                                 |
| ------- | --------------------------------------- |
| keyof   | Object ki keys nikalta hai              |
| in      | Loop chalata hai                        |
| T[Key]  | Property ki value type access karta hai |

---

# Example 1 — Basic Mapped Type

```ts id="qsmwq0"
type User = {
  name: string;
  age: number;
};

type CopyUser = {
  [Key in keyof User]: User[Key];
};
```

## Result

```ts id="4trct1"
type CopyUser = {
  name: string;
  age: number;
}
```

Yah basically User ka copy bana raha hai.

---

# Example 2 — Make All Properties Optional

```ts id="yjlwm4"
type Optional<T> = {
  [Key in keyof T]?: T[Key];
};
```

## Use

```ts id="a6l7pp"
type User = {
  name: string;
  age: number;
};

type OptionalUser = Optional<User>;
```

## Result

```ts id="25z5zl"
type OptionalUser = {
  name?: string;
  age?: number;
}
```

---

# Example 3 — Make All Properties Readonly

```ts id="1eehwd"
type ReadOnlyType<T> = {
  readonly [Key in keyof T]: T[Key];
};
```

## Use

```ts id="4m4h6u"
type User = {
  name: string;
};

type ReadonlyUser = ReadOnlyType<User>;
```

Now properties modify nahi hongi.

---

# Example 4 — Change Property Types

```ts id="z8dj7h"
type ConvertToString<T> = {
  [Key in keyof T]: string;
};
```

## Use

```ts id="6w7jz8"
type User = {
  age: number;
  salary: number;
};

type StringUser = ConvertToString<User>;
```

## Result

```ts id="cf1u4d"
type StringUser = {
  age: string;
  salary: string;
}
```

---

# Example 5 — Custom Nullable Type

```ts id="7wq81v"
type Nullable<T> = {
  [Key in keyof T]: T[Key] | null;
};
```

## Use

```ts id="s1qjcx"
type User = {
  name: string;
  age: number;
};

type NullableUser = Nullable<User>;
```

## Result

```ts id="n7e7w9"
type NullableUser = {
  name: string | null;
  age: number | null;
}
```

---

# How Built-in Utility Types Use Mapped Types

## Partial Internally

```ts id="9q0v3r"
type Partial<T> = {
  [P in keyof T]?: T[P];
};
```

---

## Readonly Internally

```ts id="d4jlwm"
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
```

---

# Real World Example

## API Response

```ts id="ft4ym0"
type User = {
  id: number;
  name: string;
  email: string;
};
```

## Update API Payload

```ts id="mvtn6o"
type UpdateUser = {
  [Key in keyof User]?: User[Key];
};
```

Now all fields optional ho gaye because update mein sab fields bhejna zaruri nahi hota.

---

# Key Points

| Concept         | Meaning                          |
| --------------- | -------------------------------- |
| keyof           | Object keys nikalta hai          |
| in              | Loop karta hai                   |
| Mapped Type     | Existing type se new type banana |
| Mostly Used For | Optional, Readonly, Nullable etc |

---

# Easy Definition

> Mapped Types ka use existing object type ki properties ko loop karke modify karne ke liye hota hai.

---


## What are Utility Types?

Utility Types are **built-in TypeScript types** that help us modify existing types easily.

They are mostly used to:

* make properties optional
* make properties readonly
* select only required fields
* remove fields
* filter types

They help reduce duplicate code and make types reusable.

---

# 1. Partial<T>

Makes **all properties optional**.

## Use Case

When updating form data or API update payloads.

```ts
type User = {
  name: string;
  age: number;
};

type UpdateUser = Partial<User>;
```

## Result

```ts
type UpdateUser = {
  name?: string;
  age?: number;
}
```

## Example

```ts
const user: UpdateUser = {
  name: "Krupa"
};
```

---

# 2. Required<T>

Makes **all properties required**.

## Use Case

When all fields must be compulsory.

```ts
type User = {
  name?: string;
  age?: number;
};

type FullUser = Required<User>;
```

## Result

```ts
type FullUser = {
  name: string;
  age: number;
}
```

---

# 3. Readonly<T>

Makes properties **read-only**.

## Use Case

When data should not be changed.

```ts
type User = {
  name: string;
};

const user: Readonly<User> = {
  name: "Krupa"
};

user.name = "Modi"; // Error
```

---

# 4. Pick<T, K>

Select only specific properties from a type.

## Use Case

When only some fields are needed.

```ts
type User = {
  name: string;
  age: number;
  email: string;
};

type UserBasic = Pick<User, "name" | "email">;
```

## Result

```ts
type UserBasic = {
  name: string;
  email: string;
}
```

---

# 5. Omit<T, K>

Removes specific properties.

## Use Case

When some fields should not be included.

```ts
type User = {
  name: string;
  age: number;
  password: string;
};

type SafeUser = Omit<User, "password">;
```

## Result

```ts
type SafeUser = {
  name: string;
  age: number;
}
```

---

# 6. Exclude<T, U>

Removes types from a union.

## Use Case

Filtering unwanted values.

```ts
type Status = "success" | "error" | "loading";

type NewStatus = Exclude<Status, "loading">;
```

## Result

```ts
type NewStatus = "success" | "error"
```

---

# 7. Extract<T, U>

Extracts matching types from a union.

## Use Case

Getting only needed values.

```ts
type Status = "success" | "error" | "loading";

type Result = Extract<Status, "success" | "error">;
```

## Result

```ts
type Result = "success" | "error"
```

---

# 8. Record<K, T>

Creates an object type with keys and values.

## Use Case

Dynamic object creation.

```ts
type Users = Record<string, number>;
```

## Result

```ts
const users: Users = {
  krupa: 1,
  rahul: 2
};
```

Here:

* key = string
* value = number

---

# 9. NonNullable<T>

Removes `null` and `undefined`.

## Use Case

When value should never be null.

```ts
type Data = string | null | undefined;

type SafeData = NonNullable<Data>;
```

## Result

```ts
type SafeData = string
```

---

# Quick Revision Table

| Utility Type | Purpose                       |
| ------------ | ----------------------------- |
| Partial      | Makes all properties optional |
| Required     | Makes all properties required |
| Readonly     | Prevents modification         |
| Pick         | Select specific properties    |
| Omit         | Remove specific properties    |
| Exclude      | Remove types from union       |
| Extract      | Get matching types            |
| Record       | Create object type            |
| NonNullable  | Remove null and undefined     |

---

# Real Interview Example

```ts
type User = {
  id: number;
  name: string;
  email: string;
  password: string;
};

// API Update
type UpdateUser = Partial<User>;

// Hide password
type PublicUser = Omit<User, "password">;

// Only basic details
type UserCard = Pick<User, "name" | "email">;
```

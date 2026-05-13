# TypeScript Coding Questions

# 🔹 Basic

## 1. Function with Types

### Question

Function banao jo 2 numbers add kare.

### Answer

```ts id="iqyho5"
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(10, 20));
```

### Interview Point

* Parameters aur return type dono define karte hain.
* Runtime bugs reduce hote hain.

---

# 2. Object Typing

### Question

User object ka type define karo.

### Answer

```ts id="srp17h"
type User = {
  name: string;
  age: number;
  isAdmin: boolean;
};

const user: User = {
  name: "Krupa",
  age: 22,
  isAdmin: false,
};
```

### Interview Point

* Object structure predictable hota hai.
* Missing/wrong properties compile time pe detect hoti hain.

---

# 3. Array Typing

### Question

String array aur number array define karo.

### Answer

```ts id="9fcbcg"
const names: string[] = ["A", "B", "C"];

const numbers: number[] = [1, 2, 3];
```

### Alternative Syntax

```ts id="kns8si"
const marks: Array<number> = [90, 80, 70];
```

### Interview Point

* Arrays me same type values ensure hoti hain.

---

# 🔹 Medium

# 4. Generic Function Banana

### Question

Generic function banao jo kisi bhi type ka value return kare.

### Answer

```ts id="ebghr5"
function identity<T>(value: T): T {
  return value;
}

console.log(identity<string>("Hello"));
console.log(identity<number>(100));
```

### Interview Point

* Generics reusable aur type-safe code banate hain.
* Multiple types support kar sakte hain.

---

# 5. Union Type Use Case

### Question

Function string ya number dono accept kare.

### Answer

```ts id="gb3xss"
function printId(id: string | number) {
  console.log(id);
}

printId(101);
printId("EMP101");
```

### Real Use Case

* API IDs kabhi string aur kabhi number hote hain.

### Interview Point

* Union types flexibility provide karte hain.

---

# 6. Type Guard Banana

### Question

Check karo value string hai ya number.

### Answer

```ts id="lv5e2k"
function printValue(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else {
    console.log(value.toFixed(2));
  }
}
```

### Interview Point

* Type guards runtime pe actual type identify karte hain.
* Safe operations perform karne me help milti hai.


# 1. Custom Utility Type Likna

### 👉 What is Utility Type?

Utility types reusable type transformations ke liye use hote hain.

---

## Example: Custom `Partial` Type

### Question

Ek custom utility type banao jo saari properties optional kare.

### Answer

```ts id="j2x3ka"
type MyPartial<T> = {
  [P in keyof T]?: T[P];
};
```

### Usage

```ts id="i0j7pa"
type User = {
  name: string;
  age: number;
};

const user: MyPartial<User> = {
  name: "Krupa",
};
```

### Interview Point

* `keyof` object keys nikalta hai
* `mapped types` properties transform karte hain
* Reusable typings banane me useful

---

# 2. Deep Readonly Type

### 👉 Problem

Normal `Readonly` sirf first level properties ko readonly banata hai.

---

## Custom DeepReadonly

### Answer

```ts id="h15t7e"
type DeepReadonly<T> = {
  readonly [P in keyof T]:
    T[P] extends object
      ? DeepReadonly<T[P]>
      : T[P];
};
```

---

## Usage

```ts id="z9ul5q"
type User = {
  name: string;
  address: {
    city: string;
  };
};

const user: DeepReadonly<User> = {
  name: "Krupa",
  address: {
    city: "Pune",
  },
};

// Error
user.address.city = "Mumbai";
```

### Interview Point

* Recursive types use hote hain
* Large projects me immutable state maintain karne ke liye useful
* Redux/React state safety me helpful

---

# 3. API Response Type Handling

### 👉 API response ko type-safe kaise handle karte ho?

---

## Basic API Response Type

### Answer

```ts id="mbm4yh"
type ApiResponse<T> = {
  success: boolean;
  data: T;
  message: string;
};
```

---

## Usage

```ts id="7ld6t9"
type User = {
  id: number;
  name: string;
};

const response: ApiResponse<User> = {
  success: true,
  data: {
    id: 1,
    name: "Krupa",
  },
  message: "User fetched",
};
```

---

## API Error Handling

```ts id="9lg7vt"
async function fetchUser(): Promise<ApiResponse<User>> {
  const res = await fetch("/api/user");

  return res.json();
}
```

### Interview Point

* Generics reusable API typings provide karte hain
* Type-safe API handling se runtime errors reduce hote hain
* Autocomplete aur IntelliSense improve hota hai

---

# 🔥 Interview Tips

### Important Lines

* “I prefer generics for reusable API response handling.”
* “Custom utility types help in large scalable applications.”
* “DeepReadonly is useful for immutable data structures.”


# 1. React App me TypeScript kaise integrate kiya?

### Interview Answer

### Existing React Project me

```bash id="b4g8qm"
npm install typescript @types/react @types/react-dom
```

### Then

* Files `.js` → `.tsx` me convert ki
* Components ke props/types define kiye
* API responses ko type-safe banaya
* ESLint + strict mode enable kiya

### Example

```tsx id="m7u2kp"
type Props = {
  title: string;
};

function Header({ title }: Props) {
  return <h1>{title}</h1>;
}
```

### Interview Point

* Better IntelliSense mila
* Compile-time error checking start hua
* Code maintainability improve hui

---

# 2. Migration JS → TS kaise kiya?

### Interview Answer

### Step-by-Step Migration

1. First TypeScript install kiya
2. `allowJs` enable kiya in `tsconfig.json`
3. Important files ko gradually `.ts/.tsx` me convert kiya
4. `any` se start kiya where needed
5. Slowly proper interfaces/types add kiye

---

## Example Config

```json id="k5v9dx"
{
  "compilerOptions": {
    "allowJs": true,
    "strict": true
  }
}
```

---

## Migration Strategy

* Small modules first
* Shared components later
* API layers properly typed

### Interview Point

> “We used gradual migration instead of converting the whole project at once.”

---

# 3. Bugs kaise reduce hue?

### Interview Answer

TypeScript use karne ke baad:

* Undefined/null issues kam hue
* Wrong prop passing errors detect hue
* API response mismatch errors reduce hue
* Refactoring safer ho gaya

---

## Example

### Before (JS)

```js id="uw7i4m"
user.name.toUpperCase()
```

Agar `name` undefined hua → runtime crash.

---

### After (TS)

```ts id="x8t6lr"
type User = {
  name?: string;
};

user.name?.toUpperCase();
```

TypeScript pehle hi warning de deta hai.

---

# 🔥 Strong Interview Lines

### Important Points

* “TypeScript helped catch errors during development instead of runtime.”
* “Strict typing improved code quality and maintainability.”
* “Gradual migration strategy worked best for large projects.”


# 1. TypeScript Strict Mode

### 👉 What is Strict Mode?

Strict mode TypeScript ka safety feature hai jo compile-time pe errors detect karta hai.

---

## Enable Strict Mode

```json id="p6v3na"
{
  "compilerOptions": {
    "strict": true
  }
}
```

---

## Benefits

* Null/undefined issues reduce
* `any` usage avoid hota hai
* Safer function calls
* Better type checking

---

## Example

```ts id="r2m8jc"
let username: string;

console.log(username);
```

❌ Error because variable initialize nahi hui.

---

## Important Strict Features

* `strictNullChecks`
* `noImplicitAny`
* `strictFunctionTypes`

---

## Interview Line

> “Strict mode helps catch bugs during development and improves overall code quality.”

---

# 2. Type Safety in APIs

### 👉 Why Important?

API response mismatch runtime crashes cause kar sakta hai.

TypeScript API data ko type-safe banata hai.

---

## Example

```ts id="x4q9tb"
type User = {
  id: number;
  name: string;
};

async function getUser(): Promise<User> {
  const res = await fetch("/api/user");

  return res.json();
}
```

---

## Benefits

* Autocomplete milta hai
* Wrong field access detect hota hai
* API integration safer hota hai

---

## Generic API Response

```ts id="k9u5ef"
type ApiResponse<T> = {
  success: boolean;
  data: T;
};
```

---

## Interview Line

> “I use typed API responses with generics to improve maintainability and reduce runtime issues.”

---

# 3. Zod / Schema Validation (Basic Idea)

### 👉 What is Zod?

[Zod Official Website](https://zod.dev?utm_source=chatgpt.com)

Zod ek TypeScript-first schema validation library hai.

Runtime validation + type safety provide karta hai.

---

## Why Use Zod?

TypeScript sirf compile-time pe check karta hai.

External API/user data runtime pe invalid ho sakta hai.

Zod runtime validation karta hai.

---

## Example

```ts id="f7y2ql"
import { z } from "zod";

const UserSchema = z.object({
  name: z.string(),
  age: z.number(),
});

const result = UserSchema.safeParse({
  name: "Krupa",
  age: 22,
});
```

---

## Benefits

* Form validation
* API validation
* Runtime safety
* Better error handling

---

## Interview Line

> “Zod is useful for validating external data and ensuring runtime type safety.”

---

# 4. Type-safe Forms

### 👉 What are Type-safe Forms?

Forms jisme fields properly typed ho aur validation safe ho.

Mostly:

* React Hook Form
* Zod
* TypeScript

saath me use hote hain.

---

## Example

```ts id="n8d1wc"
type LoginForm = {
  email: string;
  password: string;
};
```

---

## React Hook Form Example

```tsx id="u3s7mv"
const {
  register,
  handleSubmit,
} = useForm<LoginForm>();
```

---

## Benefits

* Wrong field names detect hote hain
* Validation safer hoti hai
* Better IntelliSense

---

## Real-world Usage

* Login forms
* Signup forms
* Payment forms
* Dashboard forms

---

# 🔥 Important Interview Tips

### Most Asked Modern TS Topics

* Strict mode
* API typing
* Zod validation
* React Hook Form + TS
* Generics
* Type guards

---

# 🔥 Strong Interview Closing Line

> “I focus on type safety across APIs, forms, and reusable components to reduce runtime bugs and improve maintainability.”



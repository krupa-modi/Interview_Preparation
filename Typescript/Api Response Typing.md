# What is API Response Typing?

API Response Typing means:

> API se jo data aa raha hai uska proper type define karna.

Isse:

* autocomplete milta hai
* errors kam hote hain
* safe coding hoti hai
* interview mein important concept hai

---

# Why API Typing Important?

Without typing:

```ts id="r1k4kl"
const data = await response.json();

console.log(data.name);
```

Problem:

* data ka structure pata nahi
* typo errors ho sakte hain
* TypeScript help nahi karega

---

# With Typing

```ts id="8g7vbi"
type User = {
  id: number;
  name: string;
  email: string;
};
```

Now TypeScript knows:

```ts id="s11ozv"
data.name
```

exists.

---

# Basic API Response Typing

---

# Example

```ts id="w1bw2v"
type User = {
  id: number;
  name: string;
  email: string;
};
```

---

# Fetch API

```ts id="jlwmvu"
async function getUser(): Promise<User> {

  const response = await fetch(
    "https://api.com/user"
  );

  const data: User =
    await response.json();

  return data;
}
```

---

# Important Points

| Part            | Meaning                     |
| --------------- | --------------------------- |
| Promise<User>   | Function User return karega |
| data: User      | API response ka type        |
| response.json() | JSON data                   |

---

# Array Response Typing

Bahut common interview question.

---

# Example

```ts id="g9l6k4"
type User = {
  id: number;
  name: string;
};
```

---

# API

```ts id="6zvr5q"
async function getUsers():
Promise<User[]> {

  const response = await fetch(
    "https://api.com/users"
  );

  const data: User[] =
    await response.json();

  return data;
}
```

---

# Meaning

```ts id="v0u8z6"
User[]
```

means:

> array of users

---

# Nested API Response Typing

Real APIs mostly nested hoti hain.

---

# Example Response

```json id="2e3vfm"
{
  "user": {
    "id": 1,
    "name": "Krupa"
  }
}
```

---

# Type

```ts id="i1fh9k"
type ApiResponse = {
  user: {
    id: number;
    name: string;
  };
};
```

---

# Usage

```ts id="phhrqg"
const data: ApiResponse =
  await response.json();

console.log(data.user.name);
```

---

# Generic API Response Typing

Very important interview topic.

---

# Problem

Har API ka data different hota hai.

---

# Solution → Generic Type

```ts id="4fjlwm"
type ApiResponse<T> = {
  success: boolean;
  data: T;
  message: string;
};
```

---

# Usage with User

```ts id="wtl5sv"
type User = {
  id: number;
  name: string;
};
```

---

# API Type

```ts id="5zjlwm"
type UserResponse =
  ApiResponse<User>;
```

---

# Result

```ts id="6om4ls"
{
  success: boolean;
  data: {
    id: number;
    name: string;
  };
  message: string;
}
```

---

# Array Example

```ts id="u4k00u"
type UsersResponse =
  ApiResponse<User[]>;
```

---

# Real Fetch Example

```ts id="gmn6ik"
type ApiResponse<T> = {
  success: boolean;
  data: T;
};

type User = {
  id: number;
  name: string;
};

async function getUser():
Promise<ApiResponse<User>> {

  const response = await fetch(
    "https://api.com/user"
  );

  return response.json();
}
```

---

# Axios API Typing

Interview mein bahut puchte hain.

---

# Example

```ts id="pmu8g7"
import axios from "axios";

type User = {
  id: number;
  name: string;
};
```

---

# Axios Request

```ts id="5mbmsb"
const getUser = async () => {

  const response =
    await axios.get<User>(
      "https://api.com/user"
    );

  console.log(response.data.name);
};
```

---

# Important

```ts id="h59ivj"
axios.get<User>()
```

Means:

> response.data ka type User hoga

---

# Error Response Typing

Real APIs success/error dono bhejti hain.

---

# Example

```ts id="i83yya"
type SuccessResponse<T> = {
  success: true;
  data: T;
};

type ErrorResponse = {
  success: false;
  error: string;
};
```

---

# Combined Type

```ts id="lfxvnl"
type ApiResponse<T> =
  | SuccessResponse<T>
  | ErrorResponse;
```

---

# Usage

```ts id="vgz8dz"
function handleResponse(
  response: ApiResponse<string>
) {

  if (response.success) {
    console.log(response.data);
  } else {
    console.log(response.error);
  }
}
```

---

# Optional API Fields

Kabhi API mein fields optional hoti hain.

---

# Example

```ts id="5klllh"
type User = {
  id: number;
  name: string;
  phone?: string;
};
```

---

# Meaning

```ts id="dks8ee"
phone?
```

optional hai.

---

# API Loading State Typing

React interviews mein important.

---

# Example

```ts id="qdljlwm"
type ApiState<T> = {
  loading: boolean;
  data: T | null;
  error: string | null;
};
```

---

# Usage

```ts id="abdbje"
type UserState =
  ApiState<User>;
```

---

# Best Practices

| Best Practice        | Why                |
| -------------------- | ------------------ |
| Use interfaces/types | Safe structure     |
| Use generics         | Reusable typing    |
| Handle errors        | Real-world APIs    |
| Use optional fields  | Flexible responses |
| Type arrays properly | Avoid mistakes     |

---

# Common Interview Questions

---

# Q1. Why API Response Typing Important?

## Answer

* type safety
* autocomplete
* fewer runtime errors
* better maintainability

---

# Q2. Why Generics Used in API Typing?

## Answer

Because different APIs different data return karti hain, generics reusable response structure banane mein help karte hain.

---

# Q3. Difference Between any and Proper Typing?

| any             | Proper Typing |
| --------------- | ------------- |
| No safety       | Full safety   |
| No autocomplete | Autocomplete  |
| Runtime errors  | Safer code    |

---

# Interview Definition

> API Response Typing ka use API se aane wale data ka structure define karne ke liye hota hai taaki TypeScript type safety aur autocomplete provide kar sake.

---

# Quick Revision

| Concept          | Example             |
| ---------------- | ------------------- |
| Single Object    | User                |
| Array Response   | User[]              |
| Generic Response | ApiResponse<T>      |
| Error Handling   | Success/Error union |
| Axios Typing     | axios.get<User>()   |
| Optional Field   | phone?: string      |

## 1. What are Generics in TypeScript?

Generics allow you to create **reusable, type-safe components/functions** that can work with **any data type** while preserving type information.

👉 Instead of using `any`, generics keep type safety intact.

---

## 2. Why do we need Generics?

👉 Problem without generics:

```ts id="g1"
function identity(value: any): any {
  return value;
}
```

❌ Issues:

* No type safety
* No autocomplete
* Errors at runtime

---

👉 Solution using Generics:

```ts id="g2"
function identity<T>(value: T): T {
  return value;
}
```

✅ Benefits:

* Type safety
* Better IntelliSense
* Reusable logic

---

## 3. Basic Example

```ts id="g3"
function getValue<T>(val: T): T {
  return val;
}

getValue<number>(10);      // number
getValue<string>("hello"); // string
```

👉 Type `T` is decided at runtime usage

---

## 4. Generic with Multiple Types

```ts id="g4"
function pair<T, U>(a: T, b: U): [T, U] {
  return [a, b];
}

pair<number, string>(1, "hello");
```

---

## 5. Generics in Arrays

```ts id="g5"
function getFirst<T>(arr: T[]): T {
  return arr[0];
}

getFirst<number>([1, 2, 3]);
```

---

## 6. Generics in Interfaces

```ts id="g6"
interface ApiResponse<T> {
  data: T;
  success: boolean;
}

const response: ApiResponse<string> = {
  data: "Hello",
  success: true,
};
```

---

## 7. Generics in Classes

```ts id="g7"
class Box<T> {
  value: T;

  constructor(value: T) {
    this.value = value;
  }
}

const numBox = new Box<number>(10);
```

---

## 8. Generic Constraints

👉 Restrict types using `extends`

```ts id="g8"
function printLength<T extends { length: number }>(item: T): void {
  console.log(item.length);
}

printLength("hello"); // works
printLength([1, 2]);  // works
```

---

## 9. Default Generics

```ts id="g9"
function createArray<T = string>(value: T): T[] {
  return [value];
}
```

👉 Default type is `string` if not specified

---

## 10. Real-World Example (API Call)

```ts id="g10"
async function fetchData<T>(url: string): Promise<T> {
  const res = await fetch(url);
  return res.json();
}

// Usage
interface User {
  id: number;
  name: string;
}

const data = await fetchData<User[]>('/api/users');
```

👉 Strong typing for API responses

---

## 11. Generics vs Any

| Feature      | Generics | Any   |
| ------------ | -------- | ----- |
| Type Safety  | ✅ Yes    | ❌ No  |
| Reusability  | ✅ High   | ❌ Low |
| IntelliSense | ✅ Yes    | ❌ No  |

---

# 🎯 Final Interview Answer (Short)

👉 Generics in TypeScript allow writing reusable and type-safe code by using type variables like `<T>`.
👉 They maintain type information while working with different data types.

---

💡 **Pro Tip:**
Say this 👇
👉 “Generics provide flexibility like `any` but with full type safety” 🚀

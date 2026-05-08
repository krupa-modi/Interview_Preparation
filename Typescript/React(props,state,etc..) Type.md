# What is Props Typing?

Props Typing ka matlab:

> React component ke props ka type define karna using TypeScript.

Isse:

* type safety milti hai
* wrong data pass nahi hota
* autocomplete milta hai
* interview mein bahut important hai

---

# Why We Need Props Typing?

Without TypeScript:

```jsx id="jlwmfc"
<User name={10} />
```

Ye galat hai but JavaScript allow karega.

TypeScript error dega because:

```ts id="vr1mh9"
name should be string
```

---

# Basic Syntax

```ts id="j6o8e5"
type Props = {
  name: string;
};
```

Then:

```tsx id="r4q3nl"
function User(props: Props) {
  return <h1>{props.name}</h1>;
}
```

---

# Example 1 — Basic Props Typing

## User Component

```tsx id="qarfh8"
type Props = {
  name: string;
  age: number;
};

function User({ name, age }: Props) {
  return (
    <div>
      <h1>{name}</h1>
      <h2>{age}</h2>
    </div>
  );
}

export default User;
```

---

# Usage

```tsx id="5pjx5j"
<User name="Krupa" age={22} />
```

---

# Wrong Usage

```tsx id="9ml4tz"
<User name={10} age="22" />
```

## Error

Because:

```ts id="1llx2p"
name → string hona chahiye
age → number hona chahiye
```

---

# Optional Props

`?` use hota hai optional props ke liye.

---

# Example

```tsx id="xvg6lh"
type Props = {
  name: string;
  age?: number;
};

function User({ name, age }: Props) {
  return (
    <div>
      {name} {age}
    </div>
  );
}
```

---

# Usage

```tsx id="8vlx9p"
<User name="Krupa" />
```

Allowed hai because:

```ts id="tqvpmv"
age optional hai
```

---

# Function Props Typing

Interview mein bahut important.

---

# Example

```tsx id="h7jigp"
type Props = {
  handleClick: () => void;
};

function Button({ handleClick }: Props) {
  return (
    <button onClick={handleClick}>
      Click
    </button>
  );
}
```

---

# Function with Parameters

```tsx id="s3p5zt"
type Props = {
  getData: (id: number) => void;
};
```

---

# Usage

```tsx id="jlwmut"
<Button getData={(id) => console.log(id)} />
```

---

# Array Props Typing

```tsx id="jlwmz1"
type Props = {
  users: string[];
};
```

---

# Example

```tsx id="t3hvyy"
function UserList({ users }: Props) {
  return (
    <>
      {users.map((user) => (
        <h1 key={user}>{user}</h1>
      ))}
    </>
  );
}
```

---

# Object Props Typing

```tsx id="g8vk2g"
type Props = {
  user: {
    name: string;
    age: number;
  };
};
```

---

# Example

```tsx id="g2rkhk"
function Profile({ user }: Props) {
  return <h1>{user.name}</h1>;
}
```

---

# Using Interface for Props

Type aur interface dono use kar sakte ho.

---

# Example

```tsx id="xvfxw2"
interface Props {
  name: string;
  age: number;
}

function User({ name, age }: Props) {
  return <h1>{name}</h1>;
}
```

---

# type vs interface

| type                                  | interface           |
| ------------------------------------- | ------------------- |
| Mostly modern React mein use hota hai | Old/common approach |
| unions support karta hai              | object focused      |
| flexible                              | extend easily       |

Interview mein dono acceptable hain.

---

# Children Props Typing

Bahut important topic.

---

# Example

```tsx id="jlwm81"
type Props = {
  children: React.ReactNode;
};

function Card({ children }: Props) {
  return <div>{children}</div>;
}
```

---

# Usage

```tsx id="jlwm82"
<Card>
  <h1>Hello</h1>
</Card>
```

---

# Event Props Typing

---

# Input Change Event

```tsx id="jlwm83"
const handleChange = (
  e: React.ChangeEvent<HTMLInputElement>
) => {
  console.log(e.target.value);
};
```

---

# Button Click Event

```tsx id="jlwm84"
const handleClick = (
  e: React.MouseEvent<HTMLButtonElement>
) => {
  console.log("Clicked");
};
```

---

# Destructuring with Props Typing

Most common pattern.

---

# Correct Way

```tsx id="jlwm85"
type Props = {
  name: string;
};

function User({ name }: Props) {
  return <h1>{name}</h1>;
}
```

---

# Wrong Way

```tsx id="jlwm86"
function User({ name }: string)
```

Because:

```ts id="jlwm87"
name object ke andar hai
```

---

# Generic Props Example

Advanced + interview useful.

---

# Example

```tsx id="jlwm88"
type Props<T> = {
  data: T;
};

function Display<T>({ data }: Props<T>) {
  return <h1>{JSON.stringify(data)}</h1>;
}
```

---

# Usage

```tsx id="jlwm89"
<Display data="Hello" />
<Display data={10} />
```

---

# Real Interview Example

```tsx id="jlwm90"
type ButtonProps = {
  text: string;
  disabled?: boolean;
  onClick: () => void;
};

function Button({
  text,
  disabled,
  onClick,
}: ButtonProps) {

  return (
    <button
      disabled={disabled}
      onClick={onClick}
    >
      {text}
    </button>
  );
}
```

---

# Interview Important Points

| Topic             | Important        |
| ----------------- | ---------------- |
| Optional Props    | `?`              |
| Function Props    | Commonly asked   |
| Children Typing   | Very important   |
| Event Typing      | Important        |
| Destructuring     | Mostly used      |
| type vs interface | Frequently asked |

---

# Common Mistake

## Wrong

```tsx id="jlwm91"
const User = ({ name }: string)
```

## Correct

```tsx id="jlwm92"
type Props = {
  name: string;
};

const User = ({ name }: Props)
```

---

# Easy Interview Definition

> Props Typing ka use React components ke props ka type define karne ke liye hota hai taaki correct data pass ho aur type safety maintain rahe.




# What is useState Typing?

TypeScript mein `useState` ke andar state ka type define karna hi useState typing kehlata hai.

Isse:

* state type safe hoti hai
* wrong value assign nahi kar sakte
* autocomplete milta hai
* errors jaldi milte hain

---

# Basic Syntax

```tsx id="u2o1rz"
const [state, setState] = useState<Type>(initialValue);
```

---

# Example 1 — String State

```tsx id="7n6z3f"
import { useState } from "react";

function App() {

  const [name, setName] =
    useState<string>("");

  return (
    <div>
      {name}
    </div>
  );
}
```

---

# Meaning

```tsx id="v4rxdr"
useState<string>("")
```

means:

```tsx id="s6n7xw"
name can only store string
```

---

# Example 2 — Number State

```tsx id="w2otvb"
const [count, setCount] =
  useState<number>(0);
```

Only number values allowed.

```tsx id="gc2e6j"
setCount(10); // Correct

setCount("hello"); // Error
```

---

# Example 3 — Boolean State

```tsx id="m9mrzq"
const [loading, setLoading] =
  useState<boolean>(false);
```

---

# Example 4 — Array State

```tsx id="iy8n2f"
const [users, setUsers] =
  useState<string[]>([]);
```

---

# Meaning

```tsx id="tt1u9s"
users = array of strings
```

---

# Usage

```tsx id="3nn2jn"
setUsers(["Krupa", "Rahul"]);
```

Wrong:

```tsx id="l84v8r"
setUsers([1, 2]); // Error
```

---

# Example 5 — Object State

Very important for interviews.

---

# Object Type

```tsx id="7uh7l5"
type User = {
  name: string;
  age: number;
};
```

---

# useState with Object

```tsx id="jlwm0m"
const [user, setUser] =
  useState<User>({
    name: "",
    age: 0
  });
```

---

# Usage

```tsx id="g7u5bo"
setUser({
  name: "Krupa",
  age: 22
});
```

---

# Example 6 — Nullable State

API data ya async data mein bahut use hota hai.

```tsx id="o0f8pk"
type User = {
  name: string;
};
```

---

# State

```tsx id="qqf4ga"
const [user, setUser] =
  useState<User | null>(null);
```

---

# Why?

Initially data nahi hota.

So:

```tsx id="q1dr5r"
null
```

later:

```tsx id="3kdh5t"
User object
```

---

# Example 7 — Union Types

```tsx id="shc23n"
const [status, setStatus] =
  useState<"loading" | "success" | "error">(
    "loading"
  );
```

---

# Allowed Values

```tsx id="t7qfvy"
setStatus("success"); // Correct

setStatus("done"); // Error
```

---

# Type Inference in useState

Sometimes TypeScript automatically type detect kar leta hai.

```tsx id="n7f49m"
const [count, setCount] =
  useState(0);
```

TypeScript samaj jata hai:

```tsx id="5a7u1l"
count = number
```

---

# But Explicit Typing Better Hai

Interview aur large projects mein mostly explicit types use karte hain.

```tsx id="1b8j6t"
useState<number>(0)
```

---

# Common Interview Question

# Why use Generic in useState?

```tsx id="4vvjlwm"
useState<Type>()
```

Because:

> React ko batana padta hai state kis type ki hogi.

---

# Common Mistake

```tsx id="ayjlwm"
const [user, setUser] =
  useState(null);
```

Problem:

TypeScript type infer karega:

```tsx id="hz7r7s"
user = null
```

Then:

```tsx id="j6e1h6"
setUser({ name: "Krupa" });
```

Error de sakta hai.

---

# Correct Way

```tsx id="r0trpx"
const [user, setUser] =
  useState<User | null>(null);
```

---

# Real World Example

```tsx id="8f0dbn"
import { useState } from "react";

type User = {
  name: string;
  email: string;
};

function App() {

  const [user, setUser] =
    useState<User | null>(null);

  return (
    <div>

      <button
        onClick={() =>
          setUser({
            name: "Krupa",
            email: "test@gmail.com"
          })
        }
      >
        Set User
      </button>

      {user?.name}

    </div>
  );
}
```

---

# Important Interview Points

| Topic            | Important                |
| ---------------- | ------------------------ |
| useState<Type>() | Generic typing           |
| Array typing     | `string[]`               |
| Object typing    | Custom types/interfaces  |
| Nullable state   | `Type \| null`           |
| Union types      | Multiple allowed values  |
| Type inference   | Automatic type detection |

---

# Quick Revision

| State Type | Example                        |
| ---------- | ------------------------------ |
| String     | `useState<string>("")`         |
| Number     | `useState<number>(0)`          |
| Boolean    | `useState<boolean>(false)`     |
| Array      | `useState<string[]>([])`       |
| Object     | `useState<User>({...})`        |
| Nullable   | `useState<User \| null>(null)` |

---

# Easy Interview Definition

> useState typing ka use React state ka type define karne ke liye hota hai taaki state type-safe rahe aur wrong values assign na ho sake.



# What is Event Typing?

Event Typing ka matlab hai:

> Event object ka proper type define karna.

TypeScript ko batana padta hai ki event kis element se aa raha hai.

Without typing TypeScript ko proper information nahi milti.

---

# Why Event Typing Needed?

Without typing:

```tsx id="6h8g2e"
const handleChange = (e) => {
  console.log(e.target.value);
};
```

Error aa sakta hai:

```ts id="p08qu7"
Parameter 'e' implicitly has an 'any' type
```

---

# Solution

```tsx id="8n2r67"
const handleChange = (
  e: React.ChangeEvent<HTMLInputElement>
) => {
  console.log(e.target.value);
};
```

Now TypeScript samaj gaya:

* event input field se aa raha hai
* value string hogi

---

# Basic Syntax

```tsx id="u9u9ek"
(event: React.EventType<HTMLElement>)
```

---

# Most Common Event Types

| Event      | Type                |
| ---------- | ------------------- |
| onClick    | React.MouseEvent    |
| onChange   | React.ChangeEvent   |
| onSubmit   | React.FormEvent     |
| onKeyboard | React.KeyboardEvent |
| onFocus    | React.FocusEvent    |

---

# 1. onClick Event Typing

Used for button clicks.

---

# Example

```tsx id="9h0bmx"
const handleClick = (
  e: React.MouseEvent<HTMLButtonElement>
) => {
  console.log("Button Clicked");
};

<button onClick={handleClick}>
  Click
</button>
```

---

# Breakdown

```tsx id="eh7e4g"
React.MouseEvent<HTMLButtonElement>
```

Means:

* Mouse event hai
* button element se aa raha hai

---

# 2. onChange Event Typing

Most important interview topic.

Used in forms and inputs.

---

# Example

```tsx id="x1cfaj"
const handleChange = (
  e: React.ChangeEvent<HTMLInputElement>
) => {
  console.log(e.target.value);
};

<input
  type="text"
  onChange={handleChange}
/>
```

---

# Why Important?

Because:

```tsx id="c71n7p"
e.target.value
```

properly typed ho jata hai.

---

# Textarea Example

```tsx id="m6jiv7"
const handleText = (
  e: React.ChangeEvent<HTMLTextAreaElement>
) => {
  console.log(e.target.value);
};
```

---

# Select Example

```tsx id="5ksk9f"
const handleSelect = (
  e: React.ChangeEvent<HTMLSelectElement>
) => {
  console.log(e.target.value);
};
```

---

# 3. onSubmit Event Typing

Forms submit karne ke liye.

---

# Example

```tsx id="iv6f4j"
const handleSubmit = (
  e: React.FormEvent<HTMLFormElement>
) => {

  e.preventDefault();

  console.log("Form Submitted");
};

<form onSubmit={handleSubmit}>
  <button type="submit">
    Submit
  </button>
</form>
```

---

# Important

```tsx id="4s60w2"
e.preventDefault()
```

page reload stop karta hai.

---

# 4. Keyboard Event Typing

Keyboard key detect karne ke liye.

---

# Example

```tsx id="pdj7mz"
const handleKey = (
  e: React.KeyboardEvent<HTMLInputElement>
) => {

  console.log(e.key);
};

<input onKeyDown={handleKey} />
```

---

# Useful Keys

| Property  | Meaning             |
| --------- | ------------------- |
| e.key     | Pressed key         |
| e.code    | Physical key        |
| e.ctrlKey | Ctrl pressed or not |

---

# 5. Focus Event Typing

Input focus/blur detect karne ke liye.

---

# Example

```tsx id="djlwm8"
const handleFocus = (
  e: React.FocusEvent<HTMLInputElement>
) => {
  console.log("Focused");
};

<input onFocus={handleFocus} />
```

---

# Inline Event Typing

Directly inline bhi likh sakte ho.

---

# Example

```tsx id="h35eb7"
<input
  onChange={(
    e: React.ChangeEvent<HTMLInputElement>
  ) => {
    console.log(e.target.value);
  }}
/>
```

---

# Best Practice

Mostly handler function alag banana better hota hai.

```tsx id="gl7v3m"
const handleChange = (
  e: React.ChangeEvent<HTMLInputElement>
) => {};
```

Readable hota hai.

---

# How to Find Correct Event Type

Easy trick:

Hover over event in VS Code.

```tsx id="rmn4y4"
onChange={(e) => {}}
```

VS Code automatically type bata deta hai.

---

# Real Interview Example

```tsx id="yjlwm5"
import { useState } from "react";

const Login = () => {

  const [email, setEmail] =
    useState("");

  const handleChange = (
    e: React.ChangeEvent<HTMLInputElement>
  ) => {
    setEmail(e.target.value);
  };

  const handleSubmit = (
    e: React.FormEvent<HTMLFormElement>
  ) => {

    e.preventDefault();

    console.log(email);
  };

  return (
    <form onSubmit={handleSubmit}>

      <input
        type="email"
        value={email}
        onChange={handleChange}
      />

      <button type="submit">
        Login
      </button>

    </form>
  );
};

export default Login;
```

---

# Commonly Used HTML Element Types

| Element  | Type                |
| -------- | ------------------- |
| input    | HTMLInputElement    |
| textarea | HTMLTextAreaElement |
| form     | HTMLFormElement     |
| button   | HTMLButtonElement   |
| select   | HTMLSelectElement   |

---

# Interview Important Points

| Topic               | Important        |
| ------------------- | ---------------- |
| React.ChangeEvent   | Form inputs      |
| React.MouseEvent    | Click events     |
| React.FormEvent     | Form submit      |
| React.KeyboardEvent | Keyboard events  |
| e.target.value      | Input value      |
| preventDefault      | Form reload stop |

---

# Quick Revision

| Event     | Type                |
| --------- | ------------------- |
| onClick   | React.MouseEvent    |
| onChange  | React.ChangeEvent   |
| onSubmit  | React.FormEvent     |
| onKeyDown | React.KeyboardEvent |
| onFocus   | React.FocusEvent    |

---

# Easy Interview Definition

> Event Typing ka use TypeScript mein event object ka proper type define karne ke liye hota hai taaki event properties safely access ki ja sake.



# useRef Typing in TypeScript

# What is useRef?

`useRef` React hook hai jo:

* DOM elements access karne
* value store karne
* re-render bina data save karne

ke liye use hota hai.

---

# Basic Syntax

```tsx id="n5y14l"
const ref = useRef<Type>(initialValue);
```

---

# Why Typing Needed?

TypeScript ko batana padta hai:

> ref kis type ka element/value hold karega.

Warna errors aate hain.

---

# 1. Typing DOM Elements

Most common interview question.

---

# Input Ref Example

```tsx id="kwm8zf"
import { useRef } from "react";

const App = () => {

  const inputRef =
    useRef<HTMLInputElement>(null);

  const handleFocus = () => {
    inputRef.current?.focus();
  };

  return (
    <div>
      <input ref={inputRef} />

      <button onClick={handleFocus}>
        Focus
      </button>
    </div>
  );
};

export default App;
```

---

# Explanation

```tsx id="8b4q2n"
useRef<HTMLInputElement>(null)
```

Means:

* ref HTML input element hold karega
* initial value = null

---

# Why `null`?

Starting mein DOM render nahi hua hota.

Isliye:

```tsx id="m2dkl9"
current = null
```

---

# Optional Chaining

```tsx id="eu5fwa"
inputRef.current?.focus();
```

Why?

Because:

```tsx id="d5r1bi"
current
```

kabhi null bhi ho sakta hai.

---

# Common DOM Ref Types

| Element  | Type                |
| -------- | ------------------- |
| input    | HTMLInputElement    |
| button   | HTMLButtonElement   |
| div      | HTMLDivElement      |
| form     | HTMLFormElement     |
| textarea | HTMLTextAreaElement |

---

# Example — Button Ref

```tsx id="tr1vcc"
const buttonRef =
  useRef<HTMLButtonElement>(null);
```

---

# Example — Div Ref

```tsx id="lye2r0"
const divRef =
  useRef<HTMLDivElement>(null);
```

---

# 2. useRef for Mutable Values

DOM ke alawa values store karne ke liye bhi use hota hai.

---

# Example

```tsx id="0tvksr"
import { useRef } from "react";

const App = () => {

  const countRef = useRef<number>(0);

  const increase = () => {
    countRef.current++;
    console.log(countRef.current);
  };

  return (
    <button onClick={increase}>
      Increase
    </button>
  );
};
```

---

# Important Point

```tsx id="tn01y6"
countRef.current
```

change hone pe component re-render nahi hota.

---

# Difference Between useRef and useState

| useRef                    | useState              |
| ------------------------- | --------------------- |
| Re-render nahi karta      | Re-render karta       |
| Mutable value store       | UI state store        |
| current property hoti hai | direct value hoti hai |

---

# useRef Return Type

```tsx id="55ibwf"
MutableRefObject<T>
```

Internally:

```tsx id="p0gq6m"
{
  current: T;
}
```

---

# Common Error

```tsx id="s6nq61"
Property 'focus' does not exist on type 'never'
```

Reason:

Type define nahi kiya.

---

# Wrong

```tsx id="91is6w"
const inputRef = useRef(null);
```

---

# Correct

```tsx id="gxg3x2"
const inputRef =
  useRef<HTMLInputElement>(null);
```

---

# Forward Ref Typing

Interview mein kabhi puchte hain.

---

# Example

```tsx id="m8gjia"
import {
  forwardRef
} from "react";

type Props = {
  placeholder: string;
};

const Input = forwardRef<
  HTMLInputElement,
  Props
>((props, ref) => {

  return (
    <input
      ref={ref}
      placeholder={props.placeholder}
    />
  );
});
```

---

# Meaning

```tsx id="5x5l7u"
forwardRef<
  HTMLInputElement,
  Props
>
```

* first type → ref type
* second type → props type

---

# Interview Important Points

| Topic             | Important           |
| ----------------- | ------------------- |
| DOM Access        | Main use            |
| current           | Actual value        |
| null              | Initial DOM value   |
| Optional Chaining | Null safety         |
| Mutable Value     | Re-render nahi hota |
| Generic Typing    | Important in TS     |

---

# Quick Revision

## DOM Ref

```tsx id="a9u3q7"
const ref =
  useRef<HTMLInputElement>(null);
```

---

## Mutable Value Ref

```tsx id="33vdv7"
const countRef =
  useRef<number>(0);
```

---

# Interview Definition

> `useRef` React hook hai jo mutable values aur DOM elements ko store/access karne ke liye use hota hai without causing re-render.

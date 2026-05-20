# Lifting State Up in React

## What is Lifting State Up?

Lifting state up means:
- Moving state from child component to parent component
- So multiple child components can share the same data

---

## Why Use It?

Used when:
- Two or more components need same state
- Components need synchronized data

---

## Example

### Parent Component

```jsx
function Parent() {
  const [name, setName] = useState("");

  return (
    <>
      <InputComponent name={name} setName={setName} />
      <DisplayComponent name={name} />
    </>
  );
}
````

---

## Child Component 1

```jsx id="2zwnrc"
function InputComponent({ name, setName }) {
  return (
    <input
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}
```

---

## Child Component 2

```jsx id="3yrjlwm"
function DisplayComponent({ name }) {
  return <h1>{name}</h1>;
}
```

---

## Flow

```text
Child → Parent State → Other Child
```

---

## Benefits

* Shared data between components
* Single source of truth
* Easier state management

---

## Interview One-Line Answer

> Lifting state up means moving state to the closest common parent component so multiple child components can access and share the same data.


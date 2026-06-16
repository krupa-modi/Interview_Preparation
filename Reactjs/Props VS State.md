# Props vs State in React

## Props

Props (Properties) are used to pass data from a parent component to a child component.

- Read-only (cannot be modified directly)
- Used for communication between components
- Controlled by the parent component
- Re-renders when parent passes new props

### Example

```jsx
function Child(props) {
  return <h1>Hello {props.name}</h1>;
}

function App() {
  return <Child name="Krupa" />;
}
```

👉 Props = Data passed from Parent

---

## State

State is used to store and manage dynamic data inside a component.

- Mutable (can be updated)
- Managed inside the component
- Used for changing or dynamic data
- Re-renders when state changes

### Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}
```

👉 State = Data stored inside Component

---

## Difference Between Props and State

| Feature | Props | State |
|----------|--------|--------|
| Meaning | Properties passed to component | Internal component data |
| Data Source | Parent Component | Same Component |
| Mutability | Read-only | Mutable |
| Control | External | Internal |
| Usage | Component communication | Dynamic data management |
| Update | Changed by parent | Changed using state setter |
| Re-render | When new props are received | When state changes |

---

## Interview Answer

Props are used to pass data from a parent component to a child component and are read-only. State is used to manage a component's internal data and can be updated over time. Both props and state cause the component to re-render when their values change.

---

## Easy Memory Trick

```text
Props = Passed from Parent

State = Stored inside Component
```

---

## Quick Revision

- Functional Components → Modern components using Hooks
- Class Components → Older components using lifecycle methods
- Controlled Components → React manages form data
- Uncontrolled Components → DOM manages form data
- Props → Data passed from parent to child
- State → Internal dynamic data of component


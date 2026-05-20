# 📘 Complete Jest + React Testing Library (RTL) Interview Notes

> Beginner to Advanced Interview Revision Notes

---

# 📌 What is Testing?

Testing is the process of checking whether software works correctly and is free from bugs.

### Why Testing is Important?

* Finds bugs early
* Prevents breaking old features
* Improves code quality
* Makes production stable

---

# 📌 Types of Testing

## 1️⃣ Manual Testing

Testing done manually by a tester.

### Example

* Clicking buttons manually
* Filling forms manually
* Checking UI manually

---

## 2️⃣ Automation Testing

Testing using tools/frameworks.

### Tools

* Jest
* Vitest
* Cypress
* Playwright

---

# 📌 Testing Types Used by Developers

---

## ✅ Unit Testing

Testing a single function/component.

### Example

```js
function sum(a, b) {
  return a + b;
}
```

### Test

```js
test("adds numbers", () => {
  expect(sum(2, 3)).toBe(5);
});
```

---

## ✅ Integration Testing

Testing interaction between multiple components.

### Example

* Login form + API
* Parent + Child component

---

## ✅ End-to-End Testing (E2E)

Testing complete application flow.

### Example

* Login → Dashboard → Logout

### Tools

* Cypress
* Playwright

---

# 📌 What is Jest?

Jest is a JavaScript testing framework created by Facebook.

### Jest is used for:

* Running tests
* Assertions
* Mocking
* Snapshot testing

---

# 📌 Basic Jest Example

```js
function sum(a, b) {
  return a + b;
}

test("adds two numbers", () => {
  expect(sum(2, 3)).toBe(5);
});
```

---

# 📌 What is React Testing Library (RTL)?

React Testing Library is used to test React components from the user’s perspective.

### RTL focuses on:

* UI behavior
* User interactions
* Accessibility

### RTL does NOT focus on:

* Internal state
* Internal methods
* Implementation details

---

# 📌 RTL Example

```tsx
import { render, screen } from "@testing-library/react";
import App from "./App";

test("renders heading", () => {
  render(<App />);

  const text = screen.getByText("Hello World");

  expect(text).toBeInTheDocument();
});
```

---

# 📌 Jest vs RTL

| Feature | Jest               | RTL                |
| ------- | ------------------ | ------------------ |
| Type    | Testing Framework  | UI Testing Library |
| Purpose | Runs tests         | Tests React UI     |
| Focus   | Logic & assertions | User behavior      |

---

# 📌 What is Vitest?

Vitest is a testing framework made for Vite projects.

---

# 📌 Jest vs Vitest

| Jest                 | Vitest                |
| -------------------- | --------------------- |
| Used in CRA projects | Used in Vite projects |
| Older standard       | Modern & fast         |
| More setup           | Easy setup            |

---

# 📌 Install Testing Libraries

```bash
npm install -D vitest @testing-library/react @testing-library/jest-dom jsdom @testing-library/user-event
```

---

# 📌 Package Purpose

| Package                   | Purpose                 |
| ------------------------- | ----------------------- |
| vitest                    | Test runner             |
| @testing-library/react    | React component testing |
| @testing-library/jest-dom | Extra DOM matchers      |
| jsdom                     | Fake browser            |
| user-event                | Real user interactions  |

---

# 📌 What is jsdom?

Node.js does not have:

* document
* window
* DOM

jsdom creates a fake browser environment for testing.

---

# 📌 Setup File

## setupTests.ts

```ts
import "@testing-library/jest-dom/vitest";
```

Used for matchers like:

* toBeInTheDocument()
* toHaveValue()
* toBeDisabled()

---

# 📌 render()

Used to mount component into virtual DOM.

```tsx
render(<App />);
```

---

# 📌 screen

Used to query DOM elements.

```tsx
screen.getByText("Hello");
```

---

# 📌 RTL Query Types

| Query   | Use                   | Behavior     |
| ------- | --------------------- | ------------ |
| getBy   | Element must exist    | Throws error |
| queryBy | Element may not exist | Returns null |
| findBy  | Async elements        | Waits        |

---

# 📌 getBy Example

```tsx
screen.getByText("Submit");
```

Used when element must exist.

---

# 📌 queryBy Example

```tsx
screen.queryByText("Submit");
```

Used when checking absence.

---

# 📌 findBy Example

```tsx
await screen.findByText("Loaded");
```

Used for:

* API calls
* Delayed rendering

---

# 📌 Important RTL Queries

---

# ✅ getByRole (BEST PRACTICE)

Most recommended query.

```tsx
screen.getByRole("button", { name: "Submit" });
```

---

# 📌 Common Roles

| Element         | Role     |
| --------------- | -------- |
| button          | button   |
| input type=text | textbox  |
| checkbox        | checkbox |
| h1              | heading  |
| a               | link     |

---

# 📌 getByText

```tsx
screen.getByText("Hello");
```

Finds visible text.

---

# 📌 getByLabelText

Best for forms.

```tsx
screen.getByLabelText("Name");
```

---

# 📌 getByPlaceholderText

```tsx
screen.getByPlaceholderText("Enter name");
```

Less preferred than label.

---

# 📌 getByTestId

```tsx
screen.getByTestId("title");
```

Use only if no better query exists.

---

# 📌 RTL Query Priority Order

1. getByRole ✅
2. getByLabelText
3. getByText
4. getByPlaceholderText
5. getByTestId ❌

---

# 📌 getByRole vs getAllByRole

| Method       | Returns        | Use                        |
| ------------ | -------------- | -------------------------- |
| getByRole    | Single element | One element expected       |
| getAllByRole | Array          | Multiple elements expected |

---

# 📌 Example

```tsx
const buttons = screen.getAllByRole("button");

expect(buttons).toHaveLength(3);
```

---

# 📌 getByLabelText Example

```tsx
<label htmlFor="name">Name</label>
<input id="name" />
```

### Test

```tsx
screen.getByLabelText("Name");
```

---

# 📌 getAllByLabelText

Used when multiple inputs share same label.

```tsx
const inputs = screen.getAllByLabelText("Skill");
```

---

# 📌 getByPlaceholderText vs getAllByPlaceholderText

| Method                  | Use      |
| ----------------------- | -------- |
| getByPlaceholderText    | Single   |
| getAllByPlaceholderText | Multiple |

---

# 📌 Important Matchers

| Matcher           | Purpose         |
| ----------------- | --------------- |
| toBeInTheDocument | Element exists  |
| toHaveValue       | Input value     |
| toBeDisabled      | Disabled state  |
| toHaveTextContent | Text content    |
| toHaveAttribute   | HTML attributes |
| toBeChecked       | Checkbox state  |

---

# 📌 toHaveValue Example

```tsx
expect(input).toHaveValue("Krupa");
```

---

# 📌 toBeDisabled Example

```tsx
expect(button).toBeDisabled();
```

---

# 📌 toHaveAttribute Example

```tsx
expect(input).toHaveAttribute("type", "email");
```

---

# 📌 fireEvent vs userEvent

| fireEvent      | userEvent          |
| -------------- | ------------------ |
| Low-level      | High-level         |
| Direct event   | Real user behavior |
| Less realistic | More realistic     |

---

# 📌 fireEvent Example

```tsx
fireEvent.change(input, {
  target: { value: "Hello" }
});
```

---

# 📌 userEvent Example

```tsx
await userEvent.type(input, "Hello");
```

Preferred in real projects.

---

# 📌 Input Testing Example

## Component

```tsx
import React, { useState } from "react";

const Input = () => {
  const [value, setValue] = useState("");

  return (
    <input
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
};
```

---

## Test

```tsx
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";

test("typing works", async () => {
  render(<Input />);

  const input = screen.getByRole("textbox");

  await userEvent.type(input, "Krupa");

  expect(input).toHaveValue("Krupa");
});
```

---

# 📌 Checkbox Testing

```tsx
const checkbox = screen.getByRole("checkbox");

await userEvent.click(checkbox);

expect(checkbox).toBeChecked();
```

---

# 📌 Button Click Testing

```tsx
await userEvent.click(button);
```

---

# 📌 Mock Functions (VERY IMPORTANT)

## jest.fn()

Used to create fake/mock functions.

```tsx
const mockFn = jest.fn();
```

---

# 📌 Function Call Assertions

```tsx
expect(mockFn).toHaveBeenCalled();

expect(mockFn).toHaveBeenCalledTimes(1);

expect(mockFn).toHaveBeenCalledWith("hello");
```

---

# 📌 Async API Testing

```tsx
expect(await screen.findByText("API Data")).toBeInTheDocument();
```

---

# 📌 describe()

Used to group related test cases.

---

# 📌 Example

```tsx
describe("Login Component", () => {
  test("renders input", () => {});
  test("submits form", () => {});
});
```

---

# 📌 describe.only()

Runs only one group.

```tsx
describe.only("Payment", () => {});
```

---

# 📌 describe.skip()

Skips group.

```tsx
describe.skip("Payment", () => {});
```

---

# 📌 Jest Hooks

| Hook       | Runs                  |
| ---------- | --------------------- |
| beforeEach | Before every test     |
| afterEach  | After every test      |
| beforeAll  | Once before all tests |
| afterAll   | Once after all tests  |

---

# 📌 beforeEach Example

```tsx
beforeEach(() => {
  console.log("Runs before every test");
});
```

---

# 📌 afterEach Example

```tsx
afterEach(() => {
  jest.clearAllMocks();
});
```

---

# 📌 Snapshot Testing

Snapshot testing checks whether UI changed unexpectedly.

---

# 📌 Snapshot Example

```tsx
import { render } from "@testing-library/react";

test("matches snapshot", () => {
  const { asFragment } = render(<App />);

  expect(asFragment()).toMatchSnapshot();
});
```

---

# 📌 Update Snapshot

```bash
npm test -- -u
```

OR press:

```bash
u
```

---

# 📌 Snapshot Best Practices

✅ Keep snapshots small

✅ Use for stable UI

❌ Avoid huge snapshots

❌ Don’t blindly update snapshots

---

# 📌 Virtual DOM

React creates a lightweight copy called Virtual DOM.

### Process

1. Component renders
2. Virtual DOM created
3. State changes
4. React compares old vs new DOM
5. Only changed parts update

This makes React fast.

---

# 📌 How RTL Works

RTL:

* Uses render()
* Mounts into jsdom
* Simulates user behavior
* Tests UI behavior

RTL does NOT:

* Test implementation details
* Test internal state directly

---

# 📌 Naming Convention

## File Naming

```bash
ComponentName.test.js
```

OR

```bash
ComponentName.spec.js
```

---

# 📌 Recommended Folder Structure

```bash
src/
 └── components/
      └── Button/
           ├── Button.jsx
           ├── Button.test.js
           └── Button.css
```

---

# 📌 Test Naming Convention

```tsx
test("should render button", () => {});
```

Preferred pattern:

```tsx
should + expected behavior
```

---

# 📌 Test Run Commands

## Run all tests

```bash
npm run test
```

---

## Run specific file

```bash
npx jest Button.test.js
```

---

# 📌 Watch Mode Shortcuts

| Key | Purpose      |
| --- | ------------ |
| f   | Failed tests |
| a   | Run all      |
| q   | Quit         |
| p   | Filter file  |
| t   | Filter test  |

---

# 📌 What Should We Test?

✅ Component rendering

✅ UI behavior

✅ Events

✅ API calls

✅ Forms

✅ Props behavior

---

# 📌 What Should We Avoid Testing?

❌ External libraries

❌ React internals

❌ JS built-in functionality

❌ Implementation details

---

# 📌 Functional Component Testing

❌ Don’t test internal functions directly

✅ Simulate user actions

✅ Verify UI behavior

---

# 📌 Example

```tsx
await userEvent.click(button);

expect(count).toHaveTextContent("1");
```

---

# 📌 Class Component Testing

Modern RTL approach:

✅ Test behavior

❌ Don’t directly test class methods

---

# 📌 Important Interview Questions

---

# ❓ Difference between getBy and findBy?

### ✅ Answer

getBy is synchronous and throws error immediately.

findBy is asynchronous and waits for element.

---

# ❓ Difference between fireEvent and userEvent?

### ✅ Answer

fireEvent triggers events directly while userEvent simulates real user behavior.

---

# ❓ Why use React Testing Library?

### ✅ Answer

Because it promotes testing user behavior instead of implementation details.

---

# ❓ Why is getByRole preferred?

### ✅ Answer

Because it reflects how users and assistive technologies interact with the application.

---

# ❓ What is Snapshot Testing?

### ✅ Answer

Snapshot testing stores UI output and compares future renders to detect unexpected changes.

---

# ❓ What is jsdom?

### ✅ Answer

jsdom provides a fake browser environment inside Node.js.

---

# ❓ Why use userEvent over fireEvent?

### ✅ Answer

Because userEvent simulates real browser behavior more accurately.

---

# 📌 Complete RTL Query List

---

# ✅ Single Element Queries

| Query                | Purpose               |
| -------------------- | --------------------- |
| getByRole            | Best accessible query |
| getByText            | Visible text          |
| getByLabelText       | Forms                 |
| getByPlaceholderText | Placeholder           |
| getByDisplayValue    | Input value           |
| getByAltText         | Images                |
| getByTitle           | Title                 |
| getByTestId          | Last option           |

---

# ✅ Multiple Element Queries

| Query                   | Purpose               |
| ----------------------- | --------------------- |
| getAllByRole            | Multiple roles        |
| getAllByText            | Multiple texts        |
| getAllByLabelText       | Multiple labels       |
| getAllByPlaceholderText | Multiple placeholders |
| getAllByTestId          | Multiple test ids     |

---

# ✅ queryBy Queries

| Query            | Purpose               |
| ---------------- | --------------------- |
| queryByRole      | Optional element      |
| queryByText      | Optional text         |
| queryByLabelText | Optional form element |

---

# ✅ findBy Queries

| Query           | Purpose    |
| --------------- | ---------- |
| findByRole      | Async role |
| findByText      | Async text |
| findByLabelText | Async form |

---

# 📌 Best Practices

✅ Prefer getByRole

✅ Prefer userEvent

✅ Test behavior not implementation

✅ Use accessibility-friendly queries

✅ Keep tests readable

✅ Use mock functions

---

# 📌 Common Mistakes

❌ Using getByTestId everywhere

❌ Testing internal state directly

❌ Calling internal functions directly

❌ Forgetting await with userEvent

❌ Using getBy when element does not exist

---

# 📌 Final Interview Summary

* Jest/Vitest = Test Runner
* RTL = UI Testing Library
* userEvent = Real user simulation
* getByRole = Best query
* findBy = Async query
* jest.fn() = Mock function
* Snapshot = UI comparison
* Hooks = Setup & Cleanup

---

# 📌 Golden Interview Line

> “In React Testing Library, we test the application from the user’s perspective by simulating real interactions and verifying UI behavior instead of implementation details.”


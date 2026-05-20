# 🚀 Jest + React Testing Library Interview Questions & Answers (2–3.5 Years Experience)

> Complete A to Z Interview Preparation Notes
> For Small Companies + Medium Companies + MNC Interviews

---

# 📌 1. What is Jest?

## ✅ Answer

Jest is a JavaScript testing framework created by Facebook.

It is used for:

* Running test cases
* Assertions
* Mocking
* Snapshot testing
* Code coverage

---

# 📌 2. What is React Testing Library?

## ✅ Answer

React Testing Library is used to test React components from the user’s perspective.

It focuses on:

* User interaction
* UI behavior
* Accessibility

It avoids testing implementation details.

---

# 📌 3. Difference Between Jest and RTL?

| Jest               | RTL                      |
| ------------------ | ------------------------ |
| Testing framework  | UI testing library       |
| Runs tests         | Tests React UI           |
| Handles assertions | Handles DOM interactions |

---

# 📌 4. What is Unit Testing?

## ✅ Answer

Unit testing means testing a single function or component independently.

### Example

```js id="hgw7ai"
function sum(a, b) {
  return a + b;
}
```

### Test

```js id="0ukbq0"
test("adds numbers", () => {
  expect(sum(2, 3)).toBe(5);
});
```

---

# 📌 5. What is Integration Testing?

## ✅ Answer

Integration testing checks whether multiple components/modules work correctly together.

### Example

* Form + API
* Parent + Child component

---

# 📌 6. What is Snapshot Testing?

## ✅ Answer

Snapshot testing stores rendered UI output and compares future renders to detect unexpected UI changes.

---

# 📌 Snapshot Example

```tsx id="owg7x4"
import { render } from "@testing-library/react";

test("matches snapshot", () => {
  const { asFragment } = render(<App />);

  expect(asFragment()).toMatchSnapshot();
});
```

---

# 📌 7. What is jsdom?

## ✅ Answer

jsdom creates a fake browser environment in Node.js so React components can be tested.

---

# 📌 8. What is render() in RTL?

## ✅ Answer

render() mounts a React component into a virtual DOM for testing.

---

# 📌 Example

```tsx id="fjeb06"
render(<App />);
```

---

# 📌 9. What is screen in RTL?

## ✅ Answer

screen is used to query elements from the rendered DOM.

---

# 📌 Example

```tsx id="jlwmfr"
screen.getByText("Hello");
```

---

# 📌 10. What is getByRole?

## ✅ Answer

getByRole finds elements using accessibility roles.

It is the recommended query in RTL.

---

# 📌 Example

```tsx id="7t2ax5"
screen.getByRole("button", { name: "Submit" });
```

---

# 📌 11. Why is getByRole Preferred?

## ✅ Answer

Because it reflects how users and screen readers interact with the UI.

It also improves accessibility testing.

---

# 📌 12. Difference Between getBy, queryBy and findBy?

| Query   | Use                   |
| ------- | --------------------- |
| getBy   | Element must exist    |
| queryBy | Element may not exist |
| findBy  | Async elements        |

---

# 📌 13. Difference Between fireEvent and userEvent?

## ✅ Answer

fireEvent directly triggers DOM events.

userEvent simulates real user interactions like typing and clicking.

userEvent is preferred.

---

# 📌 Example

```tsx id="58ob55"
await userEvent.type(input, "Krupa");
```

---

# 📌 14. What is Mocking?

## ✅ Answer

Mocking means creating fake versions of functions/modules for testing.

Used to:

* Avoid real API calls
* Isolate components
* Control behavior

---

# 📌 15. What is jest.fn()?

## ✅ Answer

jest.fn() creates a mock function.

---

# 📌 Example

```tsx id="kz3d32"
const mockFn = jest.fn();
```

---

# 📌 16. Important Mock Assertions

```tsx id="j2k03q"
expect(mockFn).toHaveBeenCalled();

expect(mockFn).toHaveBeenCalledTimes(1);

expect(mockFn).toHaveBeenCalledWith("hello");
```

---

# 📌 17. How to Test Button Click?

## Component

```tsx id="szj0uh"
<button onClick={handleClick}>Click</button>
```

---

## Test

```tsx id="6y8x0y"
await userEvent.click(button);
```

---

# 📌 18. How to Test Input Field?

## Component

```tsx id="7lb3qf"
<input value={value} onChange={(e) => setValue(e.target.value)} />
```

---

## Test

```tsx id="pzk8ha"
await userEvent.type(input, "Krupa");

expect(input).toHaveValue("Krupa");
```

---

# 📌 19. How to Test Checkbox?

```tsx id="h88i7y"
await userEvent.click(checkbox);

expect(checkbox).toBeChecked();
```

---

# 📌 20. How to Test API Calls?

## Example

```tsx id="v1qvpa"
expect(await screen.findByText("API Data")).toBeInTheDocument();
```

---

# 📌 21. What is describe()?

## ✅ Answer

describe() is used to group related test cases.

---

# 📌 Example

```tsx id="1bpp6n"
describe("Login Component", () => {
  test("renders input", () => {});
});
```

---

# 📌 22. What are beforeEach and afterEach?

| Hook       | Purpose                |
| ---------- | ---------------------- |
| beforeEach | Runs before every test |
| afterEach  | Runs after every test  |

---

# 📌 Example

```tsx id="jlwmu0"
beforeEach(() => {
  jest.clearAllMocks();
});
```

---

# 📌 23. What Should We Test?

✅ UI rendering

✅ User interactions

✅ Form behavior

✅ API calls

✅ State-based UI

---

# 📌 24. What Should We Avoid Testing?

❌ Internal state directly

❌ React internal functionality

❌ External library internals

---

# 📌 25. What is Virtual DOM?

## ✅ Answer

React creates a lightweight copy of the DOM called Virtual DOM.

React compares old vs new virtual DOM and updates only changed parts.

---

# 📌 26. What is Accessibility Testing?

## ✅ Answer

Accessibility testing ensures applications work correctly for all users including screen reader users.

RTL encourages accessibility-friendly testing.

---

# 📌 27. What is toBeInTheDocument?

## ✅ Answer

Checks whether element exists in DOM.

---

# 📌 Example

```tsx id="3on2s2"
expect(button).toBeInTheDocument();
```

---

# 📌 28. What is toHaveValue?

## Example

```tsx id="g6j5a4"
expect(input).toHaveValue("Krupa");
```

Used for input values.

---

# 📌 29. What is toBeDisabled?

## Example

```tsx id="3v4l4s"
expect(button).toBeDisabled();
```

Used for disabled elements.

---

# 📌 30. What is toHaveAttribute?

## Example

```tsx id="hjlwmc"
expect(input).toHaveAttribute("type", "email");
```

---

# 📌 31. What is toBeChecked?

## Example

```tsx id="c6wg5k"
expect(checkbox).toBeChecked();
```

---

# 📌 32. Difference Between getByRole and getAllByRole?

| getByRole       | getAllByRole      |
| --------------- | ----------------- |
| Single element  | Multiple elements |
| Returns element | Returns array     |

---

# 📌 33. Why Avoid getByTestId?

## ✅ Answer

Because RTL encourages testing from the user perspective using accessible queries.

---

# 📌 34. Best RTL Query Order

1. getByRole ✅
2. getByLabelText
3. getByText
4. getByPlaceholderText
5. getByTestId ❌

---

# 📌 35. How to Test Forms?

## Example

```tsx id="u7g0qa"
await userEvent.type(nameInput, "Krupa");

await userEvent.click(submitButton);

expect(screen.getByText("Success")).toBeInTheDocument();
```

---

# 📌 36. How to Test Conditional Rendering?

## Example

```tsx id="hij8c9"
expect(screen.queryByText("Error")).not.toBeInTheDocument();
```

---

# 📌 37. How to Test Loading State?

## Example

```tsx id="l3sj44"
expect(screen.getByText("Loading...")).toBeInTheDocument();
```

---

# 📌 38. How to Test Error State?

## Example

```tsx id="o5qg1m"
expect(screen.getByText("Something went wrong")).toBeInTheDocument();
```

---

# 📌 39. What is Async Testing?

## ✅ Answer

Testing asynchronous operations like:

* API calls
* Timers
* Delayed rendering

---

# 📌 40. Async Testing Example

```tsx id="4avt7n"
const text = await screen.findByText("Loaded");
```

---

# 📌 41. How to Mock API?

## Example

```tsx id="vtx4d1"
global.fetch = jest.fn(() =>
  Promise.resolve({
    json: () => Promise.resolve({ data: "Hello" }),
  })
);
```

---

# 📌 42. What is Code Coverage?

## ✅ Answer

Code coverage shows how much application code is tested.

---

# 📌 43. What is Watch Mode?

## ✅ Answer

Watch mode reruns tests automatically when files change.

---

# 📌 44. Important Watch Mode Commands

| Key | Purpose       |
| --- | ------------- |
| a   | Run all tests |
| f   | Failed tests  |
| p   | Filter files  |
| q   | Quit          |

---

# 📌 45. File Naming Convention

```bash id="0vs2su"
Button.test.js
```

OR

```bash id="h3ttls"
Button.spec.js
```

---

# 📌 46. Recommended Folder Structure

```bash id="n55m1o"
src/
 └── components/
      └── Button/
           ├── Button.jsx
           ├── Button.test.js
```

---

# 📌 47. Common Interview Coding Questions

---

# ✅ Question 1: Counter App Testing

## Component

```tsx id="1qkt4q"
import React, { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
};

export default Counter;
```

---

## Test

```tsx id="mqxwl3"
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import Counter from "./Counter";

test("increments counter", async () => {
  render(<Counter />);

  const button = screen.getByRole("button");

  await userEvent.click(button);

  expect(screen.getByText("1")).toBeInTheDocument();
});
```

---

# ✅ Question 2: Input Field Testing

## Component

```tsx id="q21kpw"
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

```tsx id="ghyfjf"
test("updates input value", async () => {
  render(<Input />);

  const input = screen.getByRole("textbox");

  await userEvent.type(input, "React");

  expect(input).toHaveValue("React");
});
```

---

# ✅ Question 3: API Fetch Testing

## Component

```tsx id="bq6s8m"
const Data = () => {
  const [data, setData] = useState("");

  useEffect(() => {
    fetch("/api")
      .then((res) => res.json())
      .then((res) => setData(res.message));
  }, []);

  return <h1>{data}</h1>;
};
```

---

## Test

```tsx id="1vqj3h"
test("fetches data", async () => {
  global.fetch = jest.fn(() =>
    Promise.resolve({
      json: () =>
        Promise.resolve({
          message: "Hello",
        }),
    })
  );

  render(<Data />);

  expect(await screen.findByText("Hello")).toBeInTheDocument();
});
```

---

# ✅ Question 4: Checkbox Testing

```tsx id="wdx0pr"
test("checkbox works", async () => {
  render(<input type="checkbox" />);

  const checkbox = screen.getByRole("checkbox");

  await userEvent.click(checkbox);

  expect(checkbox).toBeChecked();
});
```

---

# ✅ Question 5: Disabled Button Testing

```tsx id="j1w89n"
test("button disabled", () => {
  render(<button disabled>Submit</button>);

  const button = screen.getByRole("button");

  expect(button).toBeDisabled();
});
```

---

# 📌 MOST IMPORTANT INTERVIEW QUESTIONS

---

# ❓ Why use React Testing Library?

## ✅ Best Answer

RTL encourages testing from the user’s perspective and avoids testing implementation details.

---

# ❓ Why use userEvent instead of fireEvent?

## ✅ Best Answer

Because userEvent simulates real browser behavior more accurately.

---

# ❓ Why is getByRole preferred?

## ✅ Best Answer

Because it improves accessibility and reflects how users interact with UI.

---

# ❓ Difference Between Unit and Integration Testing?

## ✅ Best Answer

Unit testing checks individual components/functions, while integration testing checks interaction between multiple modules.

---

# ❓ What is Mocking?

## ✅ Best Answer

Mocking means replacing real dependencies with fake versions during testing.

---

# ❓ What is Snapshot Testing?

## ✅ Best Answer

Snapshot testing compares rendered UI with previously saved output to detect unexpected changes.

---

# 📌 Final Interview Tips

✅ Prefer userEvent

✅ Prefer getByRole

✅ Test behavior not implementation

✅ Use accessibility-friendly queries

✅ Keep tests readable

✅ Practice async testing

✅ Know mocking properly

---

# 📌 Golden Interview Line

> “In React Testing Library, we test applications the same way users interact with them instead of testing internal implementation details.”


# 🚀 Additional Jest + React Testing Library Interview Questions & Answers (Advanced + Hidden Questions)

> Extra Questions that Interviewers Ask in Small Companies, Medium Companies & MNCs
> These are the topics many candidates miss during preparation.

---

# 📌 1. What is Code Coverage?

## ✅ Answer

Code coverage shows how much application code is covered by tests.

It helps identify untested parts of the application.

---

# 📌 Run Coverage

```bash id="mq8m9n"
npm test -- --coverage
```

---

# 📌 2. What is Test Driven Development (TDD)?

## ✅ Answer

TDD is a development approach where tests are written before writing actual code.

### Process

1. Write failing test
2. Write code
3. Make test pass
4. Refactor

---

# 📌 3. What is Behavior Driven Development (BDD)?

## ✅ Answer

BDD focuses on testing application behavior from the user perspective.

Usually uses:

* describe()
* it()

---

# 📌 Example

```tsx id="6isw9u"
describe("Login", () => {
  it("should login successfully", () => {});
});
```

---

# 📌 4. Difference Between test() and it()

## ✅ Answer

There is no functional difference.

Both are aliases.

---

# 📌 Example

```tsx id="30kztt"
test("works", () => {});
```

```tsx id="rw5d6w"
it("works", () => {});
```

---

# 📌 5. What is cleanup()?

## ✅ Answer

cleanup() removes rendered components from DOM after each test.

RTL automatically handles cleanup in latest versions.

---

# 📌 Example

```tsx id="5nuj76"
afterEach(() => {
  cleanup();
});
```

---

# 📌 6. What is waitFor()?

## ✅ Answer

waitFor() waits until condition becomes true.

Used for async operations.

---

# 📌 Example

```tsx id="z9shux"
await waitFor(() => {
  expect(screen.getByText("Loaded")).toBeInTheDocument();
});
```

---

# 📌 7. Difference Between waitFor and findBy?

| waitFor               | findBy                      |
| --------------------- | --------------------------- |
| Generic async waiting | Specifically finds element  |
| More flexible         | Cleaner for element queries |

---

# 📌 8. What is act()?

## ✅ Answer

act() ensures all React state updates are processed before assertions.

RTL usually handles act() automatically.

---

# 📌 Example

```tsx id="c98tki"
await act(async () => {
  render(<App />);
});
```

---

# 📌 9. What is screen.debug()?

## ✅ Answer

screen.debug() prints DOM structure during testing.

Used for debugging failing tests.

---

# 📌 Example

```tsx id="ah3spn"
screen.debug();
```

---

# 📌 10. What is Testing Pyramid?

## ✅ Answer

Testing pyramid suggests:

* More unit tests
* Some integration tests
* Few E2E tests

---

# 📌 Structure

```txt id="t2w0jq"
       E2E
   Integration
      Unit
```

---

# 📌 11. What is Regression Testing?

## ✅ Answer

Regression testing ensures new changes do not break old functionality.

Snapshot testing helps in regression testing.

---

# 📌 12. What is Smoke Testing?

## ✅ Answer

Smoke testing checks whether critical application features work correctly.

Example:

* Login
* Navigation
* Dashboard

---

# 📌 13. What is Shallow Rendering?

## ✅ Answer

Shallow rendering was mainly used in Enzyme.

RTL does NOT recommend shallow rendering because it prefers full user behavior testing.

---

# 📌 14. Difference Between Enzyme and RTL?

| Enzyme                     | RTL            |
| -------------------------- | -------------- |
| Tests internals            | Tests behavior |
| Supports shallow rendering | Full rendering |
| Implementation-focused     | User-focused   |

---

# 📌 15. What is Memory Leak in Testing?

## ✅ Answer

Memory leaks happen when components/resources are not cleaned properly after tests.

---

# 📌 Solution

```tsx id="cvthj7"
afterEach(() => {
  jest.clearAllMocks();
});
```

---

# 📌 16. What is jest.spyOn()?

## ✅ Answer

jest.spyOn() watches existing methods/functions.

---

# 📌 Example

```tsx id="s6kz0v"
const spy = jest.spyOn(console, "log");
```

---

# 📌 17. Difference Between jest.fn and jest.spyOn?

| jest.fn               | jest.spyOn                |
| --------------------- | ------------------------- |
| Creates fake function | Watches existing function |
| New mock              | Existing method           |

---

# 📌 18. What is Mock Implementation?

## ✅ Answer

Mock implementation defines custom behavior for mocks.

---

# 📌 Example

```tsx id="75x1ks"
const mockFn = jest.fn(() => "Hello");
```

---

# 📌 19. What is mockReturnValue?

## Example

```tsx id="3wjlwm"
mockFn.mockReturnValue("Success");
```

---

# 📌 20. What is mockResolvedValue?

## Example

```tsx id="h6i8tv"
fetch.mockResolvedValue({
  json: async () => ({ message: "Hello" }),
});
```

Used for async APIs.

---

# 📌 21. What is mockRejectedValue?

## Example

```tsx id="hf2f0g"
fetch.mockRejectedValue(new Error("API Error"));
```

---

# 📌 22. What is Module Mocking?

## ✅ Answer

Module mocking replaces imported modules with fake versions.

---

# 📌 Example

```tsx id="5wlddn"
jest.mock("./api");
```

---

# 📌 23. What is Partial Mocking?

## Example

```tsx id="50cmy9"
jest.mock("./utils", () => ({
  ...jest.requireActual("./utils"),
  sum: jest.fn(),
}));
```

---

# 📌 24. What is Timer Mocking?

## ✅ Answer

Timer mocking controls setTimeout and setInterval during tests.

---

# 📌 Example

```tsx id="yzlgj4"
jest.useFakeTimers();
```

---

# 📌 25. Timer Example

```tsx id="01m0qh"
setTimeout(() => {
  console.log("Hello");
}, 1000);

jest.runAllTimers();
```

---

# 📌 26. What is Accessibility Testing in RTL?

## ✅ Answer

RTL promotes accessible queries like:

* getByRole
* getByLabelText

to improve accessibility testing.

---

# 📌 27. What is Semantic HTML?

## ✅ Answer

Semantic HTML uses meaningful tags like:

* button
* nav
* header
* main

instead of generic divs.

---

# 📌 28. Why Avoid querySelector in RTL?

## ✅ Answer

Because RTL focuses on user behavior and accessibility instead of DOM implementation.

---

# 📌 29. What is data-testid?

## ✅ Answer

data-testid is a custom attribute used to select elements in tests.

Use only as last option.

---

# 📌 Example

```tsx id="a4z98k"
<div data-testid="title">Hello</div>
```

---

# 📌 30. How to Test Dropdowns?

## Example

```tsx id="71aj2u"
await userEvent.selectOptions(select, "react");

expect(select).toHaveValue("react");
```

---

# 📌 31. How to Test Radio Buttons?

## Example

```tsx id="mo40qm"
await userEvent.click(radio);

expect(radio).toBeChecked();
```

---

# 📌 32. How to Test Keyboard Events?

## Example

```tsx id="a0g1mq"
await userEvent.keyboard("{Enter}");
```

---

# 📌 33. How to Test Hover Events?

## Example

```tsx id="5u6x7e"
await userEvent.hover(element);
```

---

# 📌 34. How to Test Unhover?

## Example

```tsx id="mrk52c"
await userEvent.unhover(element);
```

---

# 📌 35. How to Test Double Click?

## Example

```tsx id="t0jixx"
await userEvent.dblClick(button);
```

---

# 📌 36. How to Test Right Click?

## Example

```tsx id="m2vdy5"
await userEvent.pointer({
  keys: "[MouseRight]",
  target: button,
});
```

---

# 📌 37. How to Test File Upload?

## Example

```tsx id="3t4xtg"
await userEvent.upload(input, file);
```

---

# 📌 38. How to Test Drag and Drop?

## ✅ Answer

Usually tested using fireEvent because drag-drop events are low-level.

---

# 📌 Example

```tsx id="fdmyga"
fireEvent.dragStart(element);
```

---

# 📌 39. What is Custom Render in RTL?

## ✅ Answer

Custom render wraps components with providers like:

* Redux
* Router
* Theme

---

# 📌 Example

```tsx id="mfcsl0"
const customRender = (ui) =>
  render(
    <Provider store={store}>
      {ui}
    </Provider>
  );
```

---

# 📌 40. How to Test React Router?

## Example

```tsx id="1j7dnf"
render(
  <MemoryRouter>
    <App />
  </MemoryRouter>
);
```

---

# 📌 41. How to Test Redux Components?

## Example

```tsx id="l2vjlwm"
render(
  <Provider store={store}>
    <Component />
  </Provider>
);
```

---

# 📌 42. How to Test Context API?

## Example

```tsx id="g3nk5u"
render(
  <UserContext.Provider value={value}>
    <Component />
  </UserContext.Provider>
);
```

---

# 📌 43. What is MemoryRouter?

## ✅ Answer

MemoryRouter is used in tests for simulating routing without browser navigation.

---

# 📌 44. What is renderHook?

## ✅ Answer

renderHook is used to test custom hooks.

---

# 📌 Example

```tsx id="vnn9h8"
const { result } = renderHook(() => useCounter());
```

---

# 📌 45. Hook Testing Example

```tsx id="0jxj9m"
expect(result.current.count).toBe(0);
```

---

# 📌 46. How to Test useEffect?

## ✅ Answer

Usually by checking rendered UI after side effects.

---

# 📌 Example

```tsx id="wlr2cr"
expect(await screen.findByText("Loaded")).toBeInTheDocument();
```

---

# 📌 47. How to Test useState?

## ✅ Answer

Do not test state directly.

Test UI behavior after state changes.

---

# 📌 48. How to Test Custom Hooks?

## Example

```tsx id="1u2h72"
const { result } = renderHook(() => useToggle());
```

---

# 📌 49. What is AAA Pattern?

| Step    | Meaning     |
| ------- | ----------- |
| Arrange | Setup       |
| Act     | User action |
| Assert  | Verify      |

---

# 📌 Example

```tsx id="7u8a2y"
render(<Button />);

await userEvent.click(button);

expect(text).toBeInTheDocument();
```

---

# 📌 50. Most Common Real Interview Coding Questions

✅ Counter App

✅ Todo App

✅ Login Form Testing

✅ API Fetch Testing

✅ Search Filter Testing

✅ Modal Testing

✅ Accordion Testing

✅ Table Rendering

✅ Pagination Testing

✅ Debounce Search Testing

---

# 📌 51. Debounce Testing Example

```tsx id="l8dn11"
jest.useFakeTimers();
```

---

# 📌 52. How to Test Modal?

## Example

```tsx id="u9od7m"
expect(screen.getByRole("dialog")).toBeInTheDocument();
```

---

# 📌 53. How to Test Table?

## Example

```tsx id="ndb6rq"
expect(screen.getAllByRole("row")).toHaveLength(3);
```

---

# 📌 54. How to Test Pagination?

## Example

```tsx id="i6hnfe"
await userEvent.click(nextButton);
```

---

# 📌 55. How to Test Search Filter?

## Example

```tsx id="fr6dlw"
await userEvent.type(input, "React");
```

---

# 📌 56. How to Test Error Boundary?

## ✅ Answer

By rendering component with crashing child component.

---

# 📌 57. How to Improve Test Performance?

## ✅ Answer

* Avoid unnecessary rendering
* Use mock APIs
* Keep tests isolated
* Avoid huge snapshots

---

# 📌 58. What Makes a Good Test?

## ✅ Answer

Good tests are:

* Readable
* Independent
* Reliable
* Fast
* User-focused

---

# 📌 59. What is Flaky Test?

## ✅ Answer

A flaky test passes sometimes and fails sometimes inconsistently.

Usually caused by:

* Async timing issues
* Shared state
* Improper cleanup

---

# 📌 60. Golden Advanced Interview Line

> “In React Testing Library, the goal is not to test implementation details but to ensure the application behaves correctly from the user’s perspective.”

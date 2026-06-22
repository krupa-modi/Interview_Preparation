# Latest React Features & Updates (Interview Notes)

## 1. React Server Components (RSC)

### What is it?
Server Components render on the server and send only the required HTML/data to the client.

### Benefits
- Smaller bundle size
- Faster page load
- Better performance
- Reduced client-side JavaScript

### Example
```jsx
async function UserProfile() {
  const data = await fetch("/api/user");
  const user = await data.json();

  return <h1>{user.name}</h1>;
}
```

---

## 2. React Compiler (New)

### What is it?
React Compiler automatically optimizes components and reduces unnecessary re-renders.

### Benefits
- Less need for `useMemo`
- Less need for `useCallback`
- Better performance automatically

### Before

```jsx
const memoizedValue = useMemo(() => calculate(), [data]);
```

### After

React Compiler handles many optimizations automatically.

---

## 3. Actions

### What is it?
Actions simplify handling async operations like form submissions.

### Benefits
- Cleaner code
- Easier async handling
- Better error management

### Example

```jsx
async function submitForm(formData) {
  "use server";

  await saveUser(formData);
}
```

---

## 4. use() Hook

### What is it?
Allows components to directly read promises and async data.

### Example

```jsx
function User() {
  const user = use(fetchUser());

  return <h1>{user.name}</h1>;
}
```

### Benefits
- Less loading state management
- Cleaner async code

---

## 5. useOptimistic()

### What is it?
Provides optimistic UI updates before server confirmation.

### Example

```jsx
const [messages, addOptimistic] = useOptimistic(
  initialMessages,
  (state, newMessage) => [...state, newMessage]
);
```

### Benefits
- Instant UI updates
- Better user experience

---

## 6. useFormStatus()

### What is it?
Tracks form submission status.

### Example

```jsx
const { pending } = useFormStatus();

return (
  <button disabled={pending}>
    {pending ? "Submitting..." : "Submit"}
  </button>
);
```

### Benefits
- Easy loading states
- Better UX

---

## 7. useFormState()

### What is it?
Manages form state and validation results.

### Example

```jsx
const [state, formAction] = useFormState(
  submitAction,
  initialState
);
```

### Benefits
- Cleaner form handling
- Easier validation

---

## 8. Automatic Batching

### What is it?
React groups multiple state updates into a single render.

### Example

```jsx
setCount(c => c + 1);
setName("Krupa");
```

Only one re-render occurs.

### Benefits
- Better performance
- Fewer renders

---

## 9. Concurrent Rendering

### What is it?
React can interrupt rendering and prioritize important updates.

### Benefits
- Smooth UI
- Faster interactions
- Better responsiveness

---

## 10. startTransition()

### What is it?
Marks non-urgent updates.

### Example

```jsx
startTransition(() => {
  setSearchResults(data);
});
```

### Benefits
- UI remains responsive
- Better user experience

---

## 11. useTransition()

### What is it?
Tracks pending transitions.

### Example

```jsx
const [isPending, startTransition] =
  useTransition();
```

### Benefits
- Loading indicators
- Better UX

---

## 12. Suspense Improvements

### What is it?
Handles loading states while waiting for data.

### Example

```jsx
<Suspense fallback={<Loader />}>
  <ProductList />
</Suspense>
```

### Benefits
- Better loading experience
- Cleaner code

---

## 13. Streaming SSR

### What is it?
Server sends HTML in chunks instead of waiting for the entire page.

### Benefits
- Faster first paint
- Better SEO
- Improved performance

---

## 14. Improved Hydration

### What is it?
React hydrates only necessary parts of the page.

### Benefits
- Faster page interaction
- Better performance

---

## 15. Better Error Handling

### Error Boundaries

```jsx
<ErrorBoundary>
  <App />
</ErrorBoundary>
```

### Benefits
- Prevents application crashes
- Better user experience

---

# Most Important React Features for Interviews

1. React Server Components
2. React Compiler
3. use() Hook
4. useOptimistic()
5. useFormStatus()
6. useFormState()
7. Automatic Batching
8. Concurrent Rendering
9. startTransition()
10. useTransition()
11. Suspense
12. Streaming SSR

---

# One-Line Interview Answer

"Recent React updates focus on performance, server-side rendering, concurrent features, automatic optimizations, and improved form/data handling through features like React Server Components, React Compiler, use(), useOptimistic(), Suspense, and Concurrent Rendering."


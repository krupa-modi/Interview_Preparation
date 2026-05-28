# 📘 React Router Scenario Based Interview Questions

# 📌 Agar User Login Nahi Hai To Route Access Kaise Rokoge?

## 🔹 Solution

Protected Routes use karte hain.

Authentication check karte hain before rendering route.

Agar user logged in nahi hai:

✅ Redirect to Login Page

---

# 📌 Example

```jsx id="jlwm1m"
import {
  Navigate
} from "react-router-dom";

function ProtectedRoute({
  children
}) {
  const token =
    localStorage.getItem("token");

  return token
    ? children
    : <Navigate to="/login" />;
}
```

---

# 📌 Usage

```jsx id="jlwm7n"
<Route
  path="/dashboard"
  element={
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

---

# 📌 How it Works?

If token exists:

✅ Route access allowed

Else:

❌ Redirect to login page

---

# 🎯 Interview Answer

## ❓ Agar user login nahi hai to route access kaise rokoge?

### ✅ Answer:

Protected routes create karke authentication check karenge. Agar user authenticated nahi hoga to `Navigate` component se login page par redirect karenge.

---

# 📘 Page Refresh Pe State Kaise Maintain Karoge?

---

# 📌 Problem

React state refresh hone par reset ho jati hai.

---

# 📌 Common Solutions

✅ localStorage
✅ sessionStorage
✅ Redux Persist
✅ Context + Storage

---

# 📌 Example

## Save State

```jsx id="jlwm4d"
localStorage.setItem(
  "token",
  token
);
```

---

## Get State After Refresh

```jsx id="jlwm9f"
const token =
  localStorage.getItem("token");
```

---

# 📌 Why localStorage?

Because browser refresh ke baad bhi data persist rehta hai.

---

# 📌 Real Example

Login token save karte hain taaki refresh ke baad user logout na ho.

---

# 🎯 Interview Answer

## ❓ Page refresh pe state kaise maintain karoge?

### ✅ Answer:

State ko localStorage, sessionStorage, ya Redux Persist me store karke refresh ke baad restore karte hain.

---

# 📘 URL Change Hone Pe API Call Kaise Trigger Karoge?

---

# 📌 Solution

`useLocation` ya `useParams` ke saath `useEffect` use karte hain.

---

# 📌 Example Using useParams

```jsx id="jlwm2s"
import {
  useParams
} from "react-router-dom";

import {
  useEffect
} from "react";

function Product() {
  const { id } = useParams();

  useEffect(() => {
    fetchProduct(id);
  }, [id]);

  return <h1>Product</h1>;
}
```

---

# 📌 How it Works?

Whenever URL param changes:

```txt id="jlwm6x"
id changes
```

then:

```txt id="’winijlwm"
API call triggers
```

---

# 📌 Example URL

```txt id="’winiijlwm5"
/product/1
/product/2
```

---

# 🎯 Interview Answer

## ❓ URL change hone pe API call kaise trigger karoge?

### ✅ Answer:

useEffect ke dependency array me route params ya location add karte hain. URL change hone par API call automatically trigger hoti hai.

---

# 📘 Breadcrumb Navigation Kaise Banaoge?

---

# 📌 What is Breadcrumb?

Breadcrumb current page path show karta hai.

---

# 📌 Example

```txt id="’winiijlwm8"
Home > Products > Mobile
```

---

# 📌 Solution

`useLocation` use karke pathname split karte hain.

---

# 📌 Example

```jsx id="’winiijlwm2"
import {
  useLocation
} from "react-router-dom";

function Breadcrumb() {
  const location = useLocation();

  const paths =
    location.pathname.split("/");

  return (
    <div>
      {paths.map((path, index) => (
        <span key={index}>
          {path} /
        </span>
      ))}
    </div>
  );
}
```

---

# 📌 How it Works?

For URL:

```txt id="’winiijlwm0"
/products/mobile
```

Output:

```txt id="’winiijlwm7"
products / mobile
```

---

# 🎯 Interview Answer

## ❓ Breadcrumb navigation kaise banaoge?

### ✅ Answer:

Breadcrumb navigation useLocation hook ke pathname ko split karke dynamic links generate karke banaya jata hai.

---

# 📘 Deep Linking Kaise Handle Karte Ho?

---

# 📌 What is Deep Linking?

Deep linking means directly opening a specific page using URL.

---

# 📌 Example

```txt id="’winiijlwm1"
/product/10
```

User directly product page open kar sakta hai.

---

# 📌 How React Router Handles It?

React Router automatically route match karta hai.

---

# 📌 Important Requirement

Server configuration required hota hai.

Otherwise refresh pe:

❌ 404 error aa sakta hai.

---

# 📌 BrowserRouter Fix

Server ko configure karte hain to always serve:

```txt id="’winiijlwm4"
index.html
```

---

# 📌 Example

```jsx id="’winiijlwm9"
<Route
  path="/product/:id"
  element={<Product />}
/>
```

---

# 📌 Benefits

✅ Shareable URLs
✅ Bookmark support
✅ Better user experience

---

# 🎯 Interview Answer

## ❓ Deep linking kaise handle karte ho?

### ✅ Answer:

Deep linking React Router routes ke through handle hota hai. BrowserRouter use karte waqt server configuration bhi required hoti hai taaki page refresh par 404 error na aaye.


# 📘 Redux Scenario Based Interview Questions

---

# 📘 API Calls Kaise Manage Karte Ho Redux Me?

---

# 📌 Common Ways

Redux me API calls mostly handle karte hain using:

✅ createAsyncThunk
✅ Redux Thunk
✅ RTK Query
✅ Redux Saga

---

# 📌 Most Common Approach

Redux Toolkit me:

# 👉 createAsyncThunk

most commonly use hota hai.

---

# 📌 Example

```js id="’winiijlwm"
export const fetchUsers =
  createAsyncThunk(
    "users/fetchUsers",

    async () => {
      const response =
        await fetch("/users");

      return response.json();
    }
  );
```

---

# 📌 Why Use createAsyncThunk?

✅ Async handling easy
✅ Loading/error states easy
✅ Less boilerplate

---

# 📌 API Flow

```txt id="’winiijlwm7"
Dispatch Async Action
        ↓
API Call
        ↓
pending / fulfilled / rejected
        ↓
Store Update
        ↓
UI Re-render
```

---

# 🎯 Interview Answer

## ❓ How do you manage API calls in Redux?

### ✅ Answer:

API calls in Redux are commonly managed using createAsyncThunk, Redux Thunk, RTK Query, or Redux Saga. In Redux Toolkit, createAsyncThunk is the most commonly used approach.

---

# 📘 Multiple API Calls Ko Kaise Sync Karoge?

---

# 📌 Problem

Kabhi multiple APIs ek saath call karni hoti hain.

---

# 📌 Solution 1 — Promise.all

```js id="’winiijlwm2"
const [users, posts] =
  await Promise.all([
    fetch("/users"),
    fetch("/posts")
  ]);
```

---

# 📌 Benefit

Both APIs parallel run karti hain.

---

# 📌 Solution 2 — Multiple Async Thunks

```js id="’winiijlwm5"
dispatch(fetchUsers());

dispatch(fetchPosts());
```

---

# 📌 Solution 3 — Redux Saga

Complex API synchronization me Saga use hota hai.

---

# 📌 Example Use Cases

✅ Dashboard APIs
✅ Multiple widgets
✅ Analytics data

---

# 🎯 Interview Answer

## ❓ How do you synchronize multiple API calls in Redux?

### ✅ Answer:

Multiple API calls can be synchronized using Promise.all, multiple async thunks, or Redux Saga for more complex workflows.

---

# 📘 Loading, Error State Kaise Manage Karte Ho?

---

# 📌 Best Practice

Redux state me:

✅ loading
✅ error
✅ data

store karte hain.

---

# 📌 Example State

```js id="’winiijlwm0"
initialState: {
  users: [],
  loading: false,
  error: null
}
```

---

# 📌 Handling States

```js id="’winiijlwm8"
extraReducers: (builder) => {
  builder

    .addCase(
      fetchUsers.pending,
      (state) => {
        state.loading = true;
      }
    )

    .addCase(
      fetchUsers.fulfilled,
      (state, action) => {
        state.loading = false;

        state.users =
          action.payload;
      }
    )

    .addCase(
      fetchUsers.rejected,
      (state, action) => {
        state.loading = false;

        state.error =
          action.error.message;
      }
    );
}
```

---

# 📌 UI Example

```jsx id="’winiijlwm3"
{
  loading && <h1>Loading...</h1>
}
```

---

# 🎯 Interview Answer

## ❓ How do you manage loading and error states in Redux?

### ✅ Answer:

Loading and error states are usually managed inside Redux state using loading, error, and data properties handled through async actions like createAsyncThunk.

---

# 📘 Large Scale App Me State Structure Kaise Design Karte Ho?

---

# 📌 Best Practice

Feature-based structure use karte hain.

---

# 📌 Example

```txt id="’winiijlwm6"
src
 ├── app
 │    └── store.js
 │
 ├── features
 │    ├── auth
 │    ├── products
 │    ├── cart
 │    └── users
```

---

# 📌 Why Feature-Based Structure?

✅ Scalable
✅ Maintainable
✅ Easy debugging
✅ Better organization

---

# 📌 Important Point

Large apps me:

# 👉 Separate slices per feature

best practice hai.

---

# 📌 Example Store Structure

```js id="’winiijlwm1"
{
  auth: {},
  cart: {},
  products: {},
  users: {}
}
```

---

# 🎯 Interview Answer

## ❓ How do you design Redux state structure for large applications?

### ✅ Answer:

In large applications, Redux state is usually organized feature-wise using separate slices for better scalability and maintainability.

---

# 📘 Duplicate API Calls Kaise Avoid Karte Ho?

---

# 📌 Problem

Same API multiple times call ho sakti hai.

---

# 📌 Solutions

---

# 🔥 1️⃣ RTK Query Caching

Automatically duplicate requests avoid karta hai.

---

# 🔥 2️⃣ Existing State Check

```js id="’winiijlwm9"
if (state.users.length > 0) {
  return;
}
```

---

# 🔥 3️⃣ Memoized Selectors

Using:

# 👉 Reselect

---

# 🔥 4️⃣ useEffect Dependency Control

Proper dependency array use karna.

---

# 📌 RTK Query Benefit

Same request dubara API hit nahi karega if cache available hai.

---

# 🎯 Interview Answer

## ❓ How do you avoid duplicate API calls in Redux?

### ✅ Answer:

Duplicate API calls can be avoided using RTK Query caching, checking existing Redux state before fetching, and controlling component re-renders properly.

---

# 📘 Data Caching Kaise Implement Karte Ho?

---

# 📌 What is Data Caching?

Already fetched data ko store karna taaki repeated API calls avoid ho.

---

# 📌 Best Solution

# 👉 RTK Query

---

# 📌 Example

```js id="’winiijlwm4"
const {
  data,
  isLoading
} = useGetUsersQuery();
```

---

# 📌 RTK Query Features

✅ Automatic caching
✅ Auto refetching
✅ Cache invalidation
✅ Better performance

---

# 📌 Manual Caching Example

Redux store me API response save karte hain.

---

# 📌 Benefit

✅ Faster UI
✅ Less API calls
✅ Better performance

---

# 🎯 Interview Answer

## ❓ How do you implement data caching in Redux?

### ✅ Answer:

Data caching in Redux is commonly implemented using RTK Query, which automatically caches API responses and prevents unnecessary API calls.

# 📘 Redux + Routing Scenario Based Interview Questions

---

# 📘 Route Change Hone Pe Redux State Kaise Update Karte Ho?

---

# 📌 Solution

React Router hooks + Redux dispatch use karte hain.

Mostly:

# 👉 useLocation()

---

# 📌 Example

```jsx id="’winiijlwm"
import {
  useLocation
} from "react-router-dom";

import {
  useEffect
} from "react";

const location = useLocation();

useEffect(() => {
  dispatch(setRoute(location.pathname));
}, [location]);
```

---

# 📌 What Happens?

Jab route change hota hai:

✅ Redux state update ho jata hai.

---

# 🎯 Interview Answer

Route changes ko detect karne ke liye useLocation use karte hain aur Redux dispatch se state update karte hain.

---

# 📘 URL Params Ko Redux Store Me Kaise Sync Karte Ho?

---

# 📌 Solution

Using:

# 👉 useParams()

---

# 📌 Example

```jsx id="’winiijlwm7"
const { id } = useParams();

useEffect(() => {
  dispatch(setProductId(id));
}, [id]);
```

---

# 📌 Why Use?

URL params ko globally access karna easy ho jata hai.

---

# 🎯 Interview Answer

URL params ko useParams se read karke Redux store me dispatch karte hain.

---

# 📘 Navigation Ke Time API Call Kaise Trigger Karte Ho?

---

# 📌 Solution

Route/params change detect karke API call trigger karte hain.

---

# 📌 Example

```jsx id="’winiijlwm2"
const { id } = useParams();

useEffect(() => {
  dispatch(fetchProduct(id));
}, [id]);
```

---

# 📌 What Happens?

URL change:

```txt id="’winiijlwm5"
/product/1 → /product/2
```

then:

✅ New API call trigger hoti hai.

---

# 🎯 Interview Answer

Navigation ke time useEffect aur route params/location changes ke through API calls trigger karte hain.

---

# 📘 Redux State Reset On Logout Kaise Karte Ho?

---

# 📌 Solution

Logout action pe Redux state clear karte hain.

---

# 📌 Example

```js id="’winiijlwm0"
const rootReducer =
  (state, action) => {
    if (
      action.type ===
      "user/logout"
    ) {
      state = undefined;
    }

    return appReducer(
      state,
      action
    );
  };
```

---

# 📌 Why Use?

✅ Old user data remove
✅ Secure logout
✅ Fresh session

---

# 🎯 Interview Answer

Logout action dispatch hone par Redux state ko undefined set karke reset karte hain.

---

# 📘 Persisted State (redux-persist) Ka Use Kya Hai?

---

# 📌 Definition

Redux state ko browser storage me save karta hai.

---

# 📌 Why Needed?

Page refresh ke baad bhi:

✅ Login state
✅ Cart data
✅ User info

maintain rehta hai.

---

# 📌 Example

```js id="’winiijlwm8"
persistReducer(
  persistConfig,
  rootReducer
)
```

---

# 📌 Storage Used

Usually:

# 👉 localStorage

---

# 🎯 Interview Answer

redux-persist Redux state ko localStorage/sessionStorage me save karta hai taaki refresh ke baad state maintain rahe.


# React application slow हो तो कैसे optimize करेंगे?

## Answer:

```text id="z9q2mk"
If React application is slow, I optimize it by:
- Using React.memo to prevent unnecessary re-renders
- Using useMemo and useCallback for expensive calculations and functions
- Lazy loading components using React.lazy and Suspense
- Virtualization for large lists
- Optimizing API calls and state updates
- Code splitting and bundle optimization
- Using proper keys in list rendering
````

---

# 2. Bundle size कैसे reduce करते हैं?

## Answer:

```text id="7x1mjq"
Bundle size can be reduced by:
- Using code splitting
- Lazy loading components
- Removing unused libraries
- Tree shaking
- Dynamic imports
- Compressing images/assets
- Using lightweight libraries
- Avoiding unnecessary dependencies
```

---

# Example of Lazy Loading

```jsx id="b0r8xu"
const Home = React.lazy(() => import("./Home"));
```

---

# 3. Caching Strategies क्या होती हैं?

## Answer:

```text id="x2g8pn"
Caching strategies are used to store data temporarily for faster performance and fewer API calls.
```

---

# Common Caching Strategies

| Strategy             | Purpose                          |
| -------------------- | -------------------------------- |
| Browser Cache        | Stores static files in browser   |
| API Cache            | Stores API responses             |
| React Query Cache    | Prevents repeated API calls      |
| CDN Cache            | Delivers files faster globally   |
| Service Worker Cache | Offline support and fast loading |

---

# React Query Example

```jsx id="0m2dwa"
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  staleTime: 5000
});
```

---

# Short Interview Line

```text id="1w0jzn"
Performance optimization in React is done using memoization, lazy loading, code splitting, caching and reducing unnecessary re-renders.
```

# React Architecture & Design System (Interview Notes)

# 1. Large React application architecture कैसे design करेंगे?

## Answer

```text id="w5q8zn"
For large React applications, I use feature-based folder structure, reusable components, proper state management, API service layer, lazy loading and clean separation of concerns.
````

---

# Common Structure

```text id="v1p6rm"
src/
 ├── components
 ├── pages
 ├── features
 ├── services
 ├── hooks
 ├── store
 ├── utils
```

---

# Important Points

* Reusable components
* Scalable folder structure
* Centralized state management
* API separation
* Performance optimization

---

# 2. Reusable component library कैसे बनाएंगे?

## Answer

```text id="m7x2qp"
Reusable component library is created by building common UI components like Button, Input, Modal and Card which can be reused across application.
```

---

# Best Practices

* Keep components generic
* Use props for customization
* Follow consistent styling
* Write proper documentation
* Use TypeScript for type safety

---

# Example

```jsx id="u3k9rx"
<Button
  variant="primary"
  size="large"
>
  Submit
</Button>
```

---

# 3. What is Design System?

## Answer

```text id="r6p1vz"
Design system is a collection of reusable components, design rules, colors, typography and UI guidelines used to maintain consistency across application.
```

---

# Includes

* Colors
* Typography
* Buttons
* Forms
* Spacing
* Icons

---

# Examples

* Material UI
* Ant Design
* Chakra UI

---

# 4. State management tools कौन-से use किये हैं?

## Answer

```text id="n4q7bx"
I have used useState and useReducer for local state, Context API for shared state, Redux Toolkit and Zustand for global state management, and React Query/TanStack Query for server state management.
```

# 1. आपने किसी difficult bug को कैसे solve किया?

## Answer

```text id="m2q7vn"
In one project, component was re-rendering continuously and API was calling multiple times. 
I checked React DevTools and found useEffect dependency issue. 
I optimized dependencies and used memoization which fixed the issue and improved performance.
````

---

# 2. Team conflict कैसे handle किया?

## Answer

```text id="r8x1pm"
I first understand both sides calmly, focus on project goals instead of personal opinions and discuss the best technical solution with proper communication and teamwork.
```

---

# 3. Junior developer को mentor कैसे करते हैं?

## Answer

```text id="w6p4zt"
I help juniors by explaining concepts in simple way, doing code reviews, sharing best practices and helping them debug issues instead of directly giving answers.
```

---

# 4. Production issue आया तो क्या process follow करेंगे?

## Answer

```text id="q3v8ns"
First I identify issue impact, check logs and monitoring tools, reproduce the issue, fix it in staging, test properly and then deploy hotfix safely with team communication.
```

---

# 5. React में infinite re-render क्यों होता है?

## Answer

```text id="u7m2qx"
Infinite re-render happens when state updates continuously during rendering or inside useEffect without proper dependency array.
```

---

# Wrong Example

```jsx id="d8x3pl"
useEffect(() => {
  setCount(count + 1);
});
```

---

# Correct Example

```jsx id="g1n7vr"
useEffect(() => {
  setCount(count + 1);
}, []);
```

---

# 6. React key prop क्यों important है?

## Answer

```text id="n4q8zm"
Key prop helps React identify which list items changed, added or removed. 
It improves rendering performance and prevents unnecessary re-renders.
```

---

# Example

```jsx id="z2p6kt"
users.map((user) => (
  <li key={user.id}>{user.name}</li>
))
```

---

# 7. React app में API error handling कैसे करते हैं?

## Answer

```text id="f5x9qn"
API error handling is done using try-catch, proper error messages, loading states and fallback UI. 
I also handle 401, 404 and server errors separately.
```

---

# Example

```jsx id="c7v3mp"
try {
  const data = await axios.get("/users");
} catch (error) {
  console.log(error);
}
```

---

# 8. Reusable component example explain करें.

## Answer

```text id="k8q2pw"
A reusable component is a generic component that can be used in multiple places with different props.
```

---

# Example

```jsx id="p6x1zr"
<Button
  text="Submit"
  color="blue"
/>

<Button
  text="Delete"
  color="red"
/>
```

---

# Short Interview Line

```text id="y4n7qx"
I focus on reusable components, proper debugging, performance optimization, clean communication and structured problem solving in real projects.
```













````md id="react-system-design-interview"
# React System Design / Architecture Interview Answers

---

# 1. Large-scale React app कैसे structure करेंगे?

## Interview Answer

“For large-scale React applications, I prefer modular or feature-based architecture.

I separate:
- Components
- Pages
- API services
- State management
- Hooks
- Utilities

This improves:
- Scalability
- Maintainability
- Team collaboration
- Reusability”

---

# Example Folder Structure

```text id="f7xk1p"
src/
 ├── features/
 │    ├── auth/
 │    ├── dashboard/
 │    └── users/
 │
 ├── components/
 ├── services/
 ├── hooks/
 ├── routes/
 ├── utils/
 ├── store/
 └── App.js
````

---

# Important Points

✅ Reusable components

✅ Separate business logic

✅ API layer separation

✅ Global state management

✅ Lazy loading

✅ Proper routing

---

# 2. Authentication Flow Explain Kare

## Interview Answer

“User login karta hai using email/password.

Frontend credentials backend ko send karta hai.
Backend token (JWT) return karta hai.

Frontend:

* Token store karta hai
* Protected routes check karta hai
* API requests me token pass karta hai

Agar token invalid ho:

* User logout ho jata hai
* Login page pe redirect kar dete hain.”

---

# Authentication Flow

```text id="mjlwm9"
Login
   ↓
API Call
   ↓
JWT Token
   ↓
Store Token
   ↓
Protected Routes
   ↓
Authorized Access
```

---

# Token Storage

| Storage          | Use         |
| ---------------- | ----------- |
| localStorage     | Simple apps |
| HttpOnly Cookies | More secure |

---

# 3. Role-Based Access Control (RBAC) Kaise Implement Karenge?

## Interview Answer

“After login, backend user role send karta hai like:

* Admin
* User
* Manager

Frontend route access and UI rendering role ke basis par control karta hai.”

---

# Example

```jsx id="czm2qx"
if(user.role === "admin"){
  return <AdminPanel />
}
```

---

# Protected Route Example

```jsx id="qfs7k4"
if(user.role !== "admin"){
  return <Navigate to="/unauthorized" />
}
```

---

# Best Practice

✅ Role validation backend me bhi hona chahiye

Frontend security alone enough nahi hoti.

---

# 4. API Failure Handling Strategy

## Interview Answer

“If API fails:

* Proper error handling use karta hu
* User-friendly messages show karta hu
* Retry mechanism use kar sakte hain
* Loaders and fallback UI maintain karta hu

I also log errors for debugging.”

---

# Example

```jsx id="6r7l6t"
try{
  const res = await api()
}catch(error){
  console.log(error)
}
```

---

# Common API Handling

✅ Loading state
✅ Error state
✅ Retry button
✅ Timeout handling
✅ Fallback UI

---

# 5. How Do You Secure Frontend Application?

## Interview Answer

“To secure frontend applications, I follow:

* Authentication & authorization
* Protected routes
* Secure token handling
* Input validation
* Environment variables
* HTTPS APIs
* Avoid exposing sensitive data

I also avoid storing confidential information directly in frontend code.”

---

# Example Environment Variable

```env id="0g4pqs"
VITE_API_URL=https://api.example.com
```

---

# One-Line Professional Answers

## Large-scale Architecture

“I prefer feature-based scalable architecture with separated business logic and reusable components.”

---

## Authentication

“We use JWT-based authentication with protected routes.”

---

## RBAC

“UI and routes are controlled based on user roles.”

---

## API Failure

“I handle loading, error, and retry states properly.”

---

## Security

“I focus on authentication, secure token handling, HTTPS, and role-based authorization.”


# Q51. 👉 Parent component unnecessary re-render ho raha hai – kaise fix karoge?

## Interview Answer

“I first identify why the component is re-rendering using React DevTools.

Then I optimize using:
- React.memo
- useCallback
- useMemo
- State lifting reduction
- Avoid inline functions/objects

This helps prevent unnecessary re-renders and improves performance.”

---

# Example

```jsx id="q51example"
const Child = React.memo(({handleClick}) => {
  return <button onClick={handleClick}>Click</button>
})

const handleClick = useCallback(() => {
  console.log("clicked")
}, [])
````

---

# Q52. 👉 Ek button pe multiple API calls ja rahi ho – kaise stop karoge?

## Interview Answer

“I prevent multiple API calls by:

* Disabling button during loading
* Debouncing/throttling
* Using loading state
* Canceling previous requests if needed”

---

# Example

```jsx id="q52example"
const [loading, setLoading] = useState(false)

const handleSubmit = async () => {
  if(loading) return

  setLoading(true)

  await apiCall()

  setLoading(false)
}
```

---

# Q53. 👉 Form submit pe duplicate request ja rahi ho – kaise handle karoge?

## Interview Answer

“I handle duplicate form requests using:

* Loading state
* Button disable
* Debounce
* Prevent multiple clicks
* Request tracking

This avoids duplicate API submissions.”

---

# Example

```jsx id="q53example"
<button disabled={loading}>
  Submit
</button>
```

---

# Q54. 👉 Authentication & Authorization React me kaise manage karte ho?

## Interview Answer

“For authentication, we use JWT/token-based login.

After login:

* Token store karte hain
* Protected routes use karte hain
* Unauthorized users ko redirect karte hain

For authorization:

* Role-based access control implement karte hain
* Admin/User roles ke basis pe routes and UI control karte hain.”

---

# Example

```jsx id="q54example"
if(user.role !== "admin"){
  return <Navigate to="/login" />
}
```

---

# Short Professional One-Liners

## Re-render

“I optimize unnecessary re-renders using React.memo and memoization hooks.”

## Multiple API Calls

“I use loading state and debouncing to prevent duplicate API calls.”

## Duplicate Form Submit

“I disable the submit button during API processing.”

## Authentication

“I use JWT authentication with protected routes and role-based authorization.”



# कैसे पता करोगे कि कोई screen optimized है या नहीं?

## Interview Answer

“I check screen optimization using:
- Chrome DevTools
- Lighthouse
- Performance tab
- Network tab
- React DevTools

I analyze:
- Loading time
- Re-renders
- Bundle size
- API response time
- FPS and rendering performance”

---

# What I Usually Check

✅ Slow rendering
✅ Unnecessary re-renders
✅ Large images
✅ Heavy API calls
✅ Large JS bundle
✅ Memory usage

---

# Tools Used

| Tool | Purpose |
|---|---|
| Lighthouse | Performance audit |
| Network Tab | API & asset loading |
| React DevTools | Re-render analysis |
| Performance Tab | Rendering performance |

---

# Optimization Indicators

## Good Optimized Screen

✅ Fast loading
✅ Smooth scrolling
✅ Minimal re-renders
✅ Small bundle size
✅ Optimized images
✅ Lazy loaded components

---

# Short Professional Answer

“I use Lighthouse and DevTools to analyze rendering performance, API timing, bundle size, and unnecessary re-renders to identify whether a screen is optimized or not.”

---

# Image Optimization कैसे करते हो?

## Interview Answer

“I optimize images by:
- Compressing images
- Using modern formats like WebP
- Lazy loading images
- Serving responsive images
- Avoiding oversized images
- Using CDN if needed”

---

# Common Techniques

| Technique | Purpose |
|---|---|
| WebP Format | Smaller size |
| Lazy Loading | Load only when needed |
| Compression | Reduce image size |
| Responsive Images | Different screen sizes |
| CDN | Faster delivery |

---

# Lazy Loading Example

```jsx id="imglazy1"
<img src="image.webp" loading="lazy" alt="image" />
````

---

# Responsive Image Example

```jsx id="imgresponsive1"
<img
  src="small.jpg"
  srcSet="small.jpg 480w, medium.jpg 768w, large.jpg 1200w"
  alt="image"
/>
```

---

# Important Optimization Points

✅ Use proper dimensions
✅ Avoid huge PNG files
✅ Compress before upload
✅ Use SVG for icons
✅ Lazy load below-fold images

---

# Short Professional Answer

“I reduce image size using compression and WebP format, and improve loading performance using lazy loading and responsive images.”



# Large list render ho rahi hai — optimize kaise karoge?

## Interview Answer

“If a large list is causing performance issues, I optimize it using:
- Pagination
- Virtualization
- Lazy loading
- Memoization
- Proper key usage

This reduces unnecessary DOM rendering and improves performance.”

---

# Optimization Techniques

| Technique | Purpose |
|---|---|
| Pagination | Limited data render |
| Virtualization | Render only visible items |
| React.memo | Prevent re-renders |
| useMemo | Memoize filtered data |
| Lazy Loading | Load data when needed |

---

# Virtualization Libraries

```text id="vlist1"
react-window
react-virtualized
````

---

# Example

```jsx id="largelist1"
import { FixedSizeList } from "react-window"
```

---

# Important Points

✅ Avoid rendering thousands of items at once

✅ Use unique keys

✅ Avoid unnecessary re-renders

✅ Paginate API data

---

# Short Professional Answer

“I optimize large lists using virtualization, pagination, memoization, and lazy loading to reduce DOM rendering and improve UI performance.”

---

# API call multiple times ho rahi hai — fix kaise karoge?

## Interview Answer

“I first identify why repeated API calls are happening.

Common fixes:

* Correct useEffect dependencies
* Debouncing
* Throttling
* Caching
* Prevent duplicate requests
* Memoizing functions using useCallback”

---

# Common Cause

## Wrong Dependency

```jsx id="apibug1"
useEffect(() => {
  fetchData()
})
```

Ye every render pe API call karega ❌

---

# Correct Example

```jsx id="apifix1"
useEffect(() => {
  fetchData()
}, [])
```

---

# Debounce Example

```jsx id="debounce1"
const debouncedSearch = debounce(searchApi, 500)
```

---

# Other Fixes

✅ Disable button during request

✅ Use React Query / TanStack Query caching

✅ Avoid inline functions

✅ Check dependency array carefully

---

# React Query Benefit

```text id="rqcache1"
Caching
Deduplication
Retry handling
```

---

# Short Professional Answer

“I fix multiple API calls by checking useEffect dependencies, using debouncing, caching, and preventing duplicate requests.”


# Promise APIs Real Use Cases

# 1. Promise.all()

## Use Case

Multiple APIs parallel में call करनी हो।

## Real Production Example

```txt id="4f3t8k"
Dashboard Data Load
- User Profile API
- Notifications API
- Orders API
```

## Example

```js id="n7h2qx"
Promise.all([
  fetchUser(),
  fetchOrders(),
  fetchNotifications()
])
.then((data) => console.log(data))
.catch((err) => console.log(err));
```

## Important Point

* सभी promises successful होने चाहिए
* एक fail → पूरा fail

---

# 2. Promise.allSettled()

## Use Case

सभी API results चाहिए चाहे success हो या fail।

## Real Production Example

```txt id="4m7jda"
E-commerce Page
- Reviews API fail हो जाए
- Product details फिर भी दिखाने हैं
```

## Example

```js id="k1v7rw"
Promise.allSettled([
  fetchUser(),
  fetchOrders(),
  fetchReviews()
])
.then((result) => console.log(result));
```

## Important Point

* Success + Failure दोनों return करता है

---

# 3. Promise.race()

## Use Case

जो promise पहले complete हो वही चाहिए।

## Real Production Example

```txt id="s1n8oe"
API Timeout Handling
```

## Example

```js id="7p9xre"
Promise.race([
  fetchData(),
  timeoutPromise()
])
.then((data) => console.log(data))
.catch((err) => console.log(err));
```

## Important Point

* First completed promise return होता है

---

# 4. Promise.any()

## Use Case

पहला successful promise चाहिए।

## Real Production Example

```txt id="gr5vba"
Multiple Server Requests
- Fastest successful server response लेना
```

## Example

```js id="9t4wqe"
Promise.any([
  fetchServer1(),
  fetchServer2(),
  fetchServer3()
])
.then((data) => console.log(data));
```

## Important Point

* पहला success return करता है
* सभी fail → error

---

# Quick Difference Table

| API                  | Return          |
| -------------------- | --------------- |
| Promise.all()        | सभी success     |
| Promise.allSettled() | सभी result      |
| Promise.race()       | पहला completed  |
| Promise.any()        | पहला successful |

---

# Interview One-Line Answers

## Why Promise.all()?

```txt id="v8f2pk"
Parallel API calls fast बनाने के लिए
```

## Why Promise.allSettled()?

```txt id="d3m9lx"
Partial failure handle करने के लिए
```

## Why Promise.race()?

```txt id="f7n2za"
Timeout handling के लिए
```

## Why Promise.any()?

```txt id="t6w1ey"
Fastest successful response के लिए
```
E-commerce website open करते समय:

Profile API, 
Cart API,  
Product API, 
Notification API,  

इन सभी को parallel चलाने के लिए Promise.all() use करते हैं ताकि performance fast हो जाए।
### 1. Core Web Vitals (MD File)

# Core Web Vitals - Interview Notes

## What are Core Web Vitals?

Core Web Vitals are a set of metrics introduced by Google to measure real user experience and website performance.

They focus on:

1. Loading Performance
2. Interactivity
3. Visual Stability

Google uses these metrics as part of page experience ranking signals.

---

# Three Core Web Vitals

## 1. LCP (Largest Contentful Paint)

Measures loading performance.

### What does it track?

Time taken for the largest visible content element to appear on screen.

Examples:

```text
Hero Image
Banner
Large Heading
Main Content
```

### Good Score

```text
≤ 2.5 seconds
```

### Improve LCP

* Optimize images
* Use CDN
* Lazy load non-critical images
* Reduce render-blocking CSS/JS
* Use caching

---

## 2. INP (Interaction to Next Paint)

Measures responsiveness.

### What does it track?

How quickly the UI responds after a user interaction.

Examples:

```text
Button Click
Dropdown Open
Search Input
Form Submission
```

### Good Score

```text
≤ 200ms
```

### Improve INP

* Avoid heavy computations
* Use useMemo and useCallback
* Code splitting
* Reduce unnecessary re-renders

---

## 3. CLS (Cumulative Layout Shift)

Measures visual stability.

### What does it track?

Unexpected movement of elements while page is loading.

Example:

```text
User clicks button
Image loads
Button suddenly shifts
```

Bad user experience.

### Good Score

```text
≤ 0.1
```

### Improve CLS

* Set image width and height
* Reserve space for ads
* Avoid dynamic content shifting

---

# How to Measure Core Web Vitals?

Tools:

* Lighthouse
* Chrome DevTools
* Google PageSpeed Insights
* Web Vitals Extension

---

# React Optimization for Core Web Vitals

* Lazy Loading
* React.memo
* useMemo
* useCallback
* Code Splitting
* Image Optimization
* Caching

---

# Interview Answer

"Core Web Vitals are Google's performance metrics used to measure user experience. They include LCP for loading performance, INP for responsiveness, and CLS for visual stability. I usually monitor them using Lighthouse and optimize them through lazy loading, code splitting, caching, image optimization, and preventing unnecessary React re-renders."

---

### 2. Storybook (MD File)

# Storybook - Interview Notes

## What is Storybook?

Storybook is a tool used to build, test, and document UI components in isolation.

It allows developers to develop components without running the entire application.

---

# Why Use Storybook?

Suppose we have:

```text
Button
Input
Modal
Table
Dropdown
```

Instead of running the full application every time:

```bash
npm start
```

We can open Storybook and test components individually.

---

# Example

Button Component

```jsx
function Button({ label }) {
  return <button>{label}</button>;
}
```

Story

```jsx
export const Primary = {
  args: {
    label: "Save"
  }
};
```

Storybook displays the component independently.

---

# Benefits

## Component Isolation

Develop components separately.

---

## Documentation

Acts as a living component library.

---

## Reusability

Design system components become easier to maintain.

---

## Testing

Can perform:

* Visual Testing
* Interaction Testing
* Accessibility Testing

---

# Real Project Usage

Example:

```text
Design System
│
├── Button
├── Input
├── Modal
├── Table
```

Each component has its own Story.

Developers can view and test components without running the application.

---

# Interview Answer

"Storybook is a UI component development environment that allows us to build, test, and document components in isolation. It is commonly used in design systems and large-scale React applications to improve component reusability, documentation, and collaboration between developers and designers."

---

### 3. Module Federation (MD File)

# Module Federation - Interview Notes

## What is Module Federation?

Module Federation is a Webpack 5 feature that allows one application to load components, modules, or pages from another application at runtime.

Simply put:

> One application can consume code from another application without redeploying everything.

---

# Problem Before Module Federation

Suppose we have:

```text
Admin App
Customer App
Shared UI Library
```

Whenever UI changes:

```text
Build Shared UI
Publish Package
Update Apps
Redeploy Apps
```

Many steps.

---

# Module Federation Solution

Applications share code directly at runtime.

Example:

```text
Admin App
      ↓
Shared Button
      ↓
Remote Application
```

No package publishing required.

---

# Architecture

## Host Application

Consumes remote modules.

```text
Main App
```

---

## Remote Application

Exposes modules.

```text
Button
Table
Modal
```

---

# Example

Remote App exposes:

```javascript
Button
Table
Modal
```

Host App loads:

```javascript
import Button from "remoteApp/Button";
```

At runtime.

---

# Micro Frontend Architecture

Module Federation is commonly used in:

```text
Micro Frontends
```

Example:

```text
E-commerce
│
├── Product Team
├── Cart Team
├── Checkout Team
└── Profile Team
```

Each team deploys independently.

---

# Benefits

## Independent Deployment

Teams deploy separately.

---

## Code Sharing

Share components between applications.

---

## Faster Development

No package publishing process.

---

## Scalability

Ideal for large organizations.

---

# Drawbacks

* More complex setup
* Version management challenges
* Runtime dependency handling

---

# Real World Example

```text
Host Application
│
├── Dashboard
│
├── Remote App A
│     └── Product Module
│
├── Remote App B
│     └── Cart Module
│
└── Remote App C
      └── Checkout Module
```

Each module can be deployed independently.

---

# Interview Answer

"Module Federation is a Webpack 5 feature that enables applications to share modules at runtime. It is widely used in micro frontend architectures where different teams own different applications. A host application can dynamically load components or modules exposed by remote applications, allowing independent deployments and better scalability."

### Quick Interview Summary

| Topic             | One-Line Definition                                                                                         |
| ----------------- | ----------------------------------------------------------------------------------------------------------- |
| Core Web Vitals   | Google's metrics for measuring loading performance, responsiveness, and visual stability.                   |
| Storybook         | A tool for building, testing, and documenting UI components in isolation.                                   |
| Module Federation | A Webpack 5 feature that allows applications to share modules at runtime, commonly used in micro frontends. |

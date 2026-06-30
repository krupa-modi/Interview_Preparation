Bilkul. Ye interview preparation ke liye complete MD notes hain.

# Monorepo Complete Interview Notes

## What is a Monorepo?

A **Monorepo (Monolithic Repository)** is a repository structure where multiple applications, libraries, and shared packages are maintained in a single Git repository.

### Simple Definition

> Monorepo is a repository strategy where multiple projects live inside one repository instead of maintaining separate repositories for each project.

---

# Without Monorepo

Every project has its own repository.

```text
frontend-app
backend-app
admin-panel
design-system
shared-utils
```

Problems:

* Multiple repositories to maintain
* Difficult code sharing
* Dependency management becomes difficult
* Version synchronization issues

---

# With Monorepo

All projects are maintained inside one repository.

```text
company-repo
│
├── apps
│   ├── web
│   ├── admin
│   └── mobile
│
├── packages
│   ├── ui
│   ├── hooks
│   └── utils
│
└── package.json
```

Benefits:

* Easier code sharing
* Centralized dependency management
* Easier refactoring
* Consistent development standards

---

# Real World Example

Suppose a company has:

```text
Customer Portal
Admin Portal
Design System
Shared Utilities
```

Without Monorepo:

```text
customer-portal
admin-portal
design-system
shared-utils
```

4 separate repositories.

With Monorepo:

```text
company-repo
│
├── apps
│   ├── customer
│   └── admin
│
└── packages
    ├── ui
    └── utils
```

Everything in one place.

---

# Can We Create Monorepo Without Tools?

YES ✅

Monorepo is just a folder structure.

Example:

```text
my-company
│
├── web-app
├── admin-app
├── mobile-app
└── shared-ui
```

This is technically a Monorepo.

---

# Then Why Do We Need Tools?

As projects grow:

```text
web-app
admin-app
mobile-app
shared-ui
shared-utils
```

Problems appear:

* Dependency management
* Package linking
* Faster builds
* Faster testing
* Shared package versioning
* CI/CD optimization

This is where tools help.

---

# Popular Monorepo Tools

## 1. Yarn Workspaces

## 2. NPM Workspaces

## 3. Turborepo

## 4. Nx

## 5. Lerna

---

# Yarn Workspaces

Workspaces allow multiple packages to share dependencies.

### Example Structure

```text
repo
│
├── apps
│   ├── web
│   └── admin
│
└── packages
    ├── ui
    └── utils
```

Root package.json

```json
{
  "private": true,
  "workspaces": [
    "apps/*",
    "packages/*"
  ]
}
```

### Benefits

* Shared node_modules
* Shared dependencies
* Easier package linking

Without Workspaces:

```text
web/node_modules
admin/node_modules
```

With Workspaces:

```text
repo/node_modules
```

Single dependency installation.

---

# Shared Package Example

UI Package

```jsx
packages/ui/Button.jsx
```

Web App

```jsx
import { Button } from "@company/ui";
```

Admin App

```jsx
import { Button } from "@company/ui";
```

Same component reused everywhere.

---

# Turborepo

Turborepo is a high-performance build system for monorepos.

Created by Vercel.

### Main Purpose

Optimize:

```text
Build
Lint
Test
Deploy
```

---

# Problem Without Turborepo

Suppose:

```text
web
admin
mobile
```

You modify:

```text
web
```

Normally:

```text
Build web
Build admin
Build mobile
```

Everything rebuilds.

---

# Turborepo Solution

Only build affected projects.

```text
web changed
```

Result:

```text
Build web ✅
Skip admin ✅
Skip mobile ✅
```

Build becomes much faster.

---

# Turborepo Caching

Suppose yesterday:

```text
npm run build
```

already executed.

Nothing changed today.

Turborepo uses cache.

```text
Build Result Retrieved From Cache
```

No rebuild needed.

Huge CI/CD speed improvement.

---

# Nx

Nx is a powerful monorepo framework.

Used in enterprise applications.

---

# What Extra Does Nx Provide?

### Dependency Graph

Example:

```text
web
 ↓
shared-ui
 ↓
shared-utils
```

Nx understands relationships.

---

# Affected Project Detection

Suppose:

```text
shared-utils
```

changes.

Nx automatically knows:

```text
web affected
admin affected
```

Only affected projects are tested and built.

---

# Visualization

Nx can generate dependency graphs.

Example:

```text
web
 ├── ui
 └── utils

admin
 ├── ui
 └── utils
```

Very useful in large organizations.

---

# Monorepo Folder Structure

Typical React Monorepo

```text
repo
│
├── apps
│   ├── web
│   ├── admin
│   └── mobile
│
├── packages
│   ├── ui
│   ├── hooks
│   ├── utils
│   └── api
│
├── package.json
│
└── turbo.json
```

---

# Advantages of Monorepo

## 1. Code Reusability

```text
Button
Input
Modal
Table
```

Shared across applications.

---

## 2. Single Source of Truth

One design system.

One utility package.

One shared configuration.

---

## 3. Easier Refactoring

Change:

```text
shared-ui/Button
```

All apps receive updates.

---

## 4. Consistent Development Standards

Same:

```text
ESLint
Prettier
TypeScript
Testing Rules
```

Across all projects.

---

## 5. Easier Collaboration

Teams work in the same repository.

---

## 6. Better CI/CD Performance

Using:

```text
Nx
Turborepo
```

Only affected projects are built.

---

# Disadvantages of Monorepo

## Large Repository Size

```text
Many apps
Many packages
```

Repository can become huge.

---

## Learning Curve

Requires understanding:

```text
Workspaces
Package Linking
Caching
Build Pipelines
```

---

## More Complex Setup

Compared to single application repositories.

---

# Common Interview Questions

## What is Monorepo?

A repository containing multiple applications and shared packages in a single codebase.

---

## Why Use Monorepo?

* Code sharing
* Dependency management
* Easier refactoring
* Better collaboration

---

## Difference Between Monorepo and Multi Repo?

### Monorepo

```text
One Repository
Many Projects
```

### Multi Repo

```text
One Repository
One Project
```

---

## Does Monorepo Require Nx or Turborepo?

No.

A Monorepo can be created manually.

Nx and Turborepo help with:

* Caching
* Dependency Graph
* Faster Builds
* Affected Project Detection

---

# Best Interview Answer

> "A Monorepo is a repository structure where multiple applications and shared libraries are maintained within a single Git repository. It improves code sharing, dependency management, and consistency across projects. While a monorepo can be created manually, tools like Yarn Workspaces, Turborepo, and Nx provide advanced capabilities such as package linking, build caching, dependency graph management, and affected-project detection, making large-scale applications easier to maintain."

# What is Design System?

A **Design System** is a collection of **reusable UI components, design rules, styles, and guidelines** that help developers and designers build applications with a **consistent look and feel**.

It works like a **single source of truth** for the entire application.

---
# Simple Definition

> A Design System is a set of reusable components and rules used to create consistent UI across an application.

---

# Why Design System is Used?

Without a design system:

* Every developer creates buttons differently
* Colors and fonts become inconsistent
* UI looks messy
* Development becomes slow

With a design system:

* Same UI everywhere
* Faster development
* Easy maintenance
* Better user experience

---

# Real Example

Suppose a company has:

* Login page
* Dashboard
* Profile page
* Admin panel

If every page uses different:

* Button colors
* Font sizes
* Input styles

Then application looks inconsistent.

So company creates a design system with:

* Standard buttons
* Standard colors
* Typography rules
* Reusable components

Now all pages look same.

---

# Design System Contains

## 1. Colors

```js
Primary Color: Blue
Secondary Color: Gray
Success Color: Green
Error Color: Red
```

---

## 2. Typography

```js
Heading Font Size
Paragraph Font Size
Font Family
Line Height
```

---

## 3. Spacing

```js
margin
padding
gap
```

---

## 4. Reusable Components

Examples:

* Button
* Input
* Modal
* Card
* Navbar
* Table

---

## 5. Design Rules / Guidelines

Examples:

* Button radius should be 8px
* Use same shadow everywhere
* Error messages should be red

---

# Example in React

## Reusable Button Component

```jsx
function Button({ title }) {
  return (
    <button className="bg-blue-500 text-white px-4 py-2 rounded">
      {title}
    </button>
  );
}

export default Button;
```

Now entire application can use same button:

```jsx
<Button title="Login" />
<Button title="Submit" />
<Button title="Save" />
```

---

# Benefits of Design System

| Benefit              | Explanation                              |
| -------------------- | ---------------------------------------- |
| Consistency          | Same UI everywhere                       |
| Faster Development   | Reusable components save time            |
| Easy Maintenance     | Update one component everywhere          |
| Better Collaboration | Designers & developers follow same rules |
| Scalability          | Easy to grow large applications          |

---

# Popular Design Systems

| Company | Design System              |
| ------- | -------------------------- |
| Google  | Material Design            |
| Apple   | Human Interface Guidelines |
| IBM     | Carbon Design System       |
| Shopify | Polaris                    |

---

# Difference Between UI Library and Design System

| UI Library      | Design System                    |
| --------------- | -------------------------------- |
| Only components | Components + Rules + Guidelines  |
| Focus on code   | Focus on complete UI consistency |
| Example: MUI    | Example: Material Design         |

---

# In Interview (Short Answer)

> A Design System is a collection of reusable components, styles, and guidelines used to maintain consistent UI and improve development speed across an application.


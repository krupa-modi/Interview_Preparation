# React Validation Libraries

React me form validation ke liye bahot sari libraries use hoti hai.  
Ye libraries form handling, validation, error messages aur performance improve karti hai.

---
# Popular Validation Libraries

| Library | Use |
|---|---|
| Formik | Form handling + validation |
| Yup | Schema based validation |
| React Hook Form | Fast & optimized form handling |
| Zod | TypeScript friendly validation |
| Joi | Backend + frontend validation |
| Validator.js | Email, URL, phone validation |
| Custom Error State | Manual validation using useState |

---

# 1. Formik

## What is Formik?

Formik React me forms handle karne ke liye popular library hai.

### Features
- Form state manage karta hai
- Validation easy banata hai
- Error handling
- Form submit handling

---

# Install Formik

```bash
npm install formik
````

---

# Basic Formik Example

```jsx
import React from "react";
import { Formik, Form, Field, ErrorMessage } from "formik";

function App() {
  return (
    <Formik
      initialValues={{
        name: "",
        email: "",
      }}
      validate={(values) => {
        const errors = {};

        if (!values.name) {
          errors.name = "Name is required";
        }

        if (!values.email) {
          errors.email = "Email is required";
        }

        return errors;
      }}
      onSubmit={(values) => {
        console.log(values);
      }}
    >
      <Form>
        <div>
          <label>Name</label>
          <Field type="text" name="name" />
          <ErrorMessage name="name" component="p" />
        </div>

        <div>
          <label>Email</label>
          <Field type="email" name="email" />
          <ErrorMessage name="email" component="p" />
        </div>

        <button type="submit">Submit</button>
      </Form>
    </Formik>
  );
}

export default App;
```

---

# 2. Yup

## What is Yup?

Yup ek schema validation library hai.

Formik ke sath mostly use hoti hai.

---

# Install Yup

```bash
npm install yup
```

---

# Formik + Yup Validation Example

```jsx
import React from "react";
import { Formik, Form, Field, ErrorMessage } from "formik";
import * as Yup from "yup";

function App() {

  const validationSchema = Yup.object({
    name: Yup.string()
      .min(3, "Minimum 3 characters")
      .required("Name is required"),

    email: Yup.string()
      .email("Invalid email")
      .required("Email is required"),

    password: Yup.string()
      .min(6, "Minimum 6 characters")
      .required("Password is required"),
  });

  return (
    <Formik
      initialValues={{
        name: "",
        email: "",
        password: "",
      }}
      validationSchema={validationSchema}
      onSubmit={(values) => {
        console.log(values);
      }}
    >
      <Form>

        <div>
          <label>Name</label>
          <Field type="text" name="name" />
          <ErrorMessage name="name" component="p" />
        </div>

        <div>
          <label>Email</label>
          <Field type="email" name="email" />
          <ErrorMessage name="email" component="p" />
        </div>

        <div>
          <label>Password</label>
          <Field type="password" name="password" />
          <ErrorMessage name="password" component="p" />
        </div>

        <button type="submit">Submit</button>

      </Form>
    </Formik>
  );
}

export default App;
```

---

# 3. React Hook Form

## What is React Hook Form?

React Hook Form ek fast aur optimized form library hai.

### Features

* Performance better
* Re-render kam hota hai
* Easy validation
* Small bundle size

---

# Install React Hook Form

```bash
npm install react-hook-form
```

---

# Basic React Hook Form Example

```jsx
import React from "react";
import { useForm } from "react-hook-form";

function App() {

  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>

      <div>
        <label>Name</label>

        <input
          type="text"
          {...register("name", {
            required: "Name is required",
            minLength: {
              value: 3,
              message: "Minimum 3 characters",
            },
          })}
        />

        <p>{errors.name?.message}</p>
      </div>

      <div>
        <label>Email</label>

        <input
          type="email"
          {...register("email", {
            required: "Email is required",
          })}
        />

        <p>{errors.email?.message}</p>
      </div>

      <button type="submit">Submit</button>

    </form>
  );
}

export default App;
```

---

# 4. Zod

## What is Zod?

Zod TypeScript friendly validation library hai.

React Hook Form ke sath bahot use hoti hai.

---

# Install Zod

```bash
npm install zod
npm install @hookform/resolvers
```

---

# React Hook Form + Zod Example

```jsx
import React from "react";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { zodResolver } from "@hookform/resolvers/zod";

const schema = z.object({
  name: z.string().min(3, "Minimum 3 characters"),

  email: z.string().email("Invalid email"),

  password: z.string().min(6, "Password too short"),
});

function App() {

  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm({
    resolver: zodResolver(schema), // Validation manually mat karo, Zod schema use karo
  });

* schema → validation rules
* zodResolver() → React Hook Form aur Zod ko connect karta hai
* resolver → form validation handle karta hai

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>

      <div>
        <label>Name</label>

        <input type="text" {...register("name")} />

        <p>{errors.name?.message}</p>
      </div>

      <div>
        <label>Email</label>

        <input type="email" {...register("email")} />

        <p>{errors.email?.message}</p>
      </div>

      <div>
        <label>Password</label>

        <input type="password" {...register("password")} />

        <p>{errors.password?.message}</p>
      </div>

      <button type="submit">Submit</button>

    </form>
  );
}

export default App;
```

---

# 5. Custom Error State Validation

## What is Custom Validation?

Jab hum manually validation logic likhte hai using useState.

---

# Custom Validation Example

```jsx
import React, { useState } from "react";

function App() {

  const [formData, setFormData] = useState({
    name: "",
    email: "",
  });

  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value,
    });
  };

  const validate = () => {

    let newErrors = {};

    if (!formData.name) {
      newErrors.name = "Name is required";
    }

    if (!formData.email) {
      newErrors.email = "Email is required";
    }

    setErrors(newErrors);

    return Object.keys(newErrors).length === 0; // Ye object hai jisme validation errors store hote hai.
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    if (validate()) {
      console.log(formData);
    }
  };

  return (
    <form onSubmit={handleSubmit}>

      <div>
        <label>Name</label>

        <input
          type="text"
          name="name"
          value={formData.name}
          onChange={handleChange}
        />

        <p>{errors.name}</p>
      </div>

      <div>
        <label>Email</label>

        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
        />

        <p>{errors.email}</p>
      </div>

      <button type="submit">Submit</button>

    </form>
  );
}

export default App;
```

---

# Interview Questions

## Why use validation?

* Invalid data prevent karne ke liye
* Better user experience
* Secure data handling

---

## Difference Between Formik and React Hook Form

| Formik                     | React Hook Form              |
| -------------------------- | ---------------------------- |
| Re-render more             | Better performance           |
| Easy for beginners         | More optimized               |
| Uses controlled components | Uses uncontrolled components |

---

## Difference Between Yup and Zod

| Yup                   | Zod                            |
| --------------------- | ------------------------------ |
| Mostly Formik ke sath | Mostly React Hook Form ke sath |
| JavaScript focused    | TypeScript friendly            |
| Old & popular         | Modern library                 |

---

# Which Validation Library Should You Use?

| Situation          | Best Choice       |
| ------------------ | ----------------- |
| Beginner           | Formik + Yup      |
| High Performance   | React Hook Form   |
| TypeScript Project | Zod               |
| Small Form         | Custom Validation |

---

# Most Used Combination in Industry

## Old Projects

* Formik + Yup

## Modern Projects

* React Hook Form + Zod


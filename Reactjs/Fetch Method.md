# Fetch API in JavaScript

# What is Fetch API?

`fetch()` is a modern JavaScript method used to make:
- API calls
- HTTP requests
- network requests

It is used to communicate with servers and get/send data.

---

# Why Fetch API is Used?

Fetch API is used because:
- asynchronous request handling
- cleaner than XMLHttpRequest
- Promise-based
- easy error handling
- modern syntax

---

# Where Fetch API is Used?

## Common Use Cases
- Fetching API data
- Login systems
- Sending form data
- Loading products/users/posts
- CRUD operations
- Authentication

---

# Syntax

```js
fetch(url, options)
```

---

# Basic GET Request

```js
fetch("https://api.example.com/users")
    .then((response) => {
        return response.json();
    })
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log(error);
    });
```

---

# How Fetch Works Internally?

## Step 1
Request sent to server.

---

## Step 2
Server sends response.

---

## Step 3
Fetch returns Promise.

---

## Step 4
`.then()` handles success.

---

## Step 5
`.catch()` handles errors.

---

# Important Point

Fetch does NOT directly return actual data.

It returns:
```js
Promise
```

So we use:
```js
.then()
```
or
```js
async/await
```

---

# Response Object

Fetch returns a Response object.

Example:

```js
fetch(url)
.then((response)=>{
    console.log(response);
})
```

---

# Common Response Properties

| Property | Meaning |
|---|---|
| response.ok | true/false |
| response.status | HTTP status code |
| response.statusText | Status message |
| response.headers | Response headers |

---

# response.json()

Used to convert JSON data into JavaScript object.

```js
response.json()
```

---

# Why response.json() Needed?

Server mostly sends data in JSON format.

`response.json()` converts it into usable JavaScript object.

---

# Example

```js
fetch("https://jsonplaceholder.typicode.com/users")

.then((response)=>{
    return response.json();
})

.then((data)=>{
    console.log(data);
});
```

---

# Fetch with async/await

## Why Use async/await?

Cleaner and readable syntax.

---

# Example

```js
async function getUsers(){

    try{

        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

        const data = await response.json();

        console.log(data);

    }catch(error){

        console.log(error);

    }

}

getUsers();
```

---

# HTTP Methods in Fetch API

| Method | Purpose |
|---|---|
| GET | Get data |
| POST | Send data |
| PUT | Update complete data |
| PATCH | Update partial data |
| DELETE | Delete data |

---

# 1. GET Request

## Purpose
Used to fetch data from server.

```js
fetch("https://api.com/users")
```

---

# 2. POST Request

## Purpose
Used to send data to server.

---

# Example

```js
fetch("https://api.com/users", {

    method: "POST",

    headers: {
        "Content-Type": "application/json"
    },

    body: JSON.stringify({
        name: "Krupa",
        age: 22
    })

})
.then((response)=> response.json())
.then((data)=> console.log(data));
```

---

# Why JSON.stringify() Used?

`body` must be string format.

`JSON.stringify()` converts object → JSON string.

---

# 3. PUT Request

## Purpose
Completely update existing data.

---

# Example

```js
fetch("https://api.com/users/1", {

    method: "PUT",

    headers: {
        "Content-Type": "application/json"
    },

    body: JSON.stringify({
        name: "New Name"
    })

});
```

---

# 4. PATCH Request

## Purpose
Partially update data.

---

# Example

```js
fetch("https://api.com/users/1", {

    method: "PATCH",

    headers: {
        "Content-Type": "application/json"
    },

    body: JSON.stringify({
        name: "Updated"
    })

});
```

---

# Difference Between PUT and PATCH

| PUT | PATCH |
|---|---|
| Full update | Partial update |
| Replaces entire data | Updates specific field |

---

# 5. DELETE Request

## Purpose
Delete data from server.

---

# Example

```js
fetch("https://api.com/users/1", {

    method: "DELETE"

});
```

---

# headers in Fetch API

Headers provide extra information to server.

---

# Common Header

```js
headers: {
   "Content-Type": "application/json"
}
```

---

# Why Content-Type Used?

Tells server:
```js
data is JSON format
```

---

# Error Handling in Fetch API

---

# Important Interview Point

Fetch only rejects Promise when:
- network error occurs

Fetch DOES NOT reject for:
- 404
- 500

So manual checking needed.

---

# Proper Error Handling Example

```js
fetch("https://api.com/users")

.then((response)=>{

    if(!response.ok){
        throw new Error("API Failed");
    }

    return response.json();

})

.then((data)=>{
    console.log(data);
})

.catch((error)=>{
    console.log(error);
});
```

---

# response.ok

| Value | Meaning |
|---|---|
| true | Success |
| false | Failed |

---

# Status Codes

| Code | Meaning |
|---|---|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 404 | Not Found |
| 500 | Server Error |

---

# Fetch vs Axios

| Fetch API | Axios |
|---|---|
| Built into browser | External library |
| Need manual JSON conversion | Auto JSON conversion |
| Manual error handling | Better error handling |
| Promise-based | Promise-based |

---

# Advantages of Fetch API

- Modern syntax
- Promise-based
- Cleaner code
- Easy async handling
- Supported in modern browsers

---

# Limitations of Fetch API

- No automatic JSON parsing
- Manual error handling needed
- No request timeout by default

---

# Fetch API Real-world Example

```js
async function getProducts(){

    try{

        const response = await fetch(
            "https://fakestoreapi.com/products"
        );

        if(!response.ok){
            throw new Error("Failed");
        }

        const data = await response.json();

        console.log(data);

    }catch(error){

        console.log(error);

    }

}

getProducts();
```

---

# Interview Questions

# Q1. What is Fetch API?

Fetch API is a modern JavaScript method used to make HTTP requests.

---

# Q2. Is Fetch synchronous or asynchronous?

Asynchronous.

---

# Q3. What does fetch return?

It returns a Promise.

---

# Q4. Why response.json() used?

To convert JSON data into JavaScript object.

---

# Q5. Difference between PUT and PATCH?

| PUT | PATCH |
|---|---|
| Full update | Partial update |

---

# Q6. Does fetch reject on 404?

No.

Only network failure rejects Promise.

---

# Q7. Why use async/await with fetch?

Cleaner and more readable asynchronous code.

---

# Q8. Difference between Fetch and XMLHttpRequest?

Fetch is:
- modern
- Promise-based
- cleaner syntax

XMLHttpRequest is older callback-based approach.

---

# Q9. Why headers are used?

To send extra information to server.

---

# Q10. Why JSON.stringify() used in body?

Because request body should be string format.

---

# Quick Revision

## fetch()
Used for API calls.

---

## response.json()
Converts JSON → JavaScript object.

---

## response.ok
Checks request success.

---

## async/await
Cleaner async handling.

---

## GET
Fetch data.

---

## POST
Send data.

---

## PUT
Full update.

---

## PATCH
Partial update.

---

## DELETE
Delete data.
## 1. What is HTML and why is it used?

### Answer:

HTML stands for **HyperText Markup Language**.
It is the standard language used to create webpages and web applications.

HTML is used to:

* Structure web pages
* Display text, images, videos, tables, forms, etc.
* Create links between pages
* Define webpage content for browsers

### Example:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page</title>
</head>
<body>
  <h1>Hello World</h1>
</body>
</html>
```

---

# 2. What is the difference between HTML and XHTML?

| HTML                                | XHTML                            |
| ----------------------------------- | -------------------------------- |
| Less strict                         | Very strict                      |
| Tags can remain unclosed            | All tags must be closed          |
| Attribute values may not use quotes | Attribute values must use quotes |
| Case insensitive                    | Case sensitive                   |
| Easier to write                     | Follows XML rules                |

### Example:

### HTML

```html
<input type=text>
```

### XHTML

```html
<input type="text" />
```

---

# 3. What are the different versions of HTML?

### Answer:

Different versions of HTML are:

| Version   | Description                      |
| --------- | -------------------------------- |
| HTML 1.0  | First basic version              |
| HTML 2.0  | Introduced forms                 |
| HTML 3.2  | Added tables and styling         |
| HTML 4.01 | Improved structure and scripting |
| XHTML     | HTML with XML rules              |
| HTML5     | Latest modern version            |

---

# 4. What is the difference between HTML4 and HTML5?

| HTML4                   | HTML5                     |
| ----------------------- | ------------------------- |
| No semantic tags        | Semantic tags added       |
| No audio/video support  | Audio/video support added |
| Uses plugins like Flash | Native multimedia support |
| Limited form controls   | New input types added     |
| No local storage        | Local storage available   |

### HTML5 Semantic Tags:

```html
<header>
<nav>
<section>
<article>
<footer>
```

---

# 5. What is the purpose of `<!DOCTYPE html>`?

### Answer:

`<!DOCTYPE html>` tells the browser that the document is written in HTML5.

It helps the browser:

* Render the page correctly
* Avoid compatibility issues
* Use standard mode

### Example:

```html
<!DOCTYPE html>
```

---

# 6. What is the role of `<head>` tag in HTML?

### Answer:

The `<head>` tag contains metadata and information about the webpage.

It includes:

* Page title
* CSS links
* JavaScript files
* Meta tags
* SEO information

### Example:

```html
<head>
  <title>My Website</title>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="style.css">
</head>
```

---

# 7. What is the difference between `<head>` and `<body>`?

| `<head>`                 | `<body>`                       |
| ------------------------ | ------------------------------ |
| Contains metadata        | Contains visible content       |
| Not displayed on webpage | Displayed on webpage           |
| Includes title, CSS, JS  | Includes text, images, buttons |

### Example:

```html
<head>
  <title>Page Title</title>
</head>

<body>
  <h1>Hello</h1>
</body>
```

---

# 8. What are HTML elements and attributes?

## HTML Element

An HTML element consists of:

* Opening tag
* Content
* Closing tag

### Example:

```html
<p>Hello</p>
```

## HTML Attribute

Attributes provide extra information about elements.

### Example:

```html
<img src="image.jpg" alt="Image">
```

Here:

* `src`
* `alt`

are attributes.

---

# 9. What is the difference between tag and element?

| Tag                          | Element                 |
| ---------------------------- | ----------------------- |
| Only opening or closing part | Complete structure      |
| Example: `<p>`               | Example: `<p>Hello</p>` |

### Example:

```html
<p>Hello</p>
```

* `<p>` → Tag
* `<p>Hello</p>` → Element

---

# 10. What are empty elements in HTML?

### Answer:

Empty elements are HTML elements that do not have closing tags and content.

They are also called self-closing tags.

### Examples:

```html
<br>
<hr>
<img>
<input>
```

### Example:

```html
<input type="text">
<br>
<hr>
```

---

# Quick Interview Revision

| Question             | Short Answer                                     |
| -------------------- | ------------------------------------------------ |
| What is HTML?        | Language used to create webpages                 |
| HTML vs XHTML        | XHTML is stricter                                |
| Latest HTML version  | HTML5                                            |
| Purpose of DOCTYPE   | Tells browser to use HTML5                       |
| `<head>` use         | Metadata and links                               |
| `<body>` use         | Visible webpage content                          |
| Element vs Attribute | Element = full structure, Attribute = extra info |
| Empty elements       | Tags without closing tags                        |


# 2. Block vs Inline Elements (Very Common)

---

# 1. What is the difference between block-level and inline elements?

| Block-Level Elements                | Inline Elements                          |
| ----------------------------------- | ---------------------------------------- |
| Takes full width available          | Takes only required width                |
| Starts from new line                | Does not start from new line             |
| Can contain block & inline elements | Usually contains text or inline elements |
| Height & width can be applied       | Height & width usually not applied       |

### Example:

```html id="ij5j0l"
<div>This is block element</div>
<span>This is inline element</span>
```

---

# 2. Give examples of block-level elements.

### Common Block Elements:

```html id="bhzjlwm"
<div>
<p>
<h1> to <h6>
<section>
<article>
<header>
<footer>
<nav>
<ul>
<li>
form
```

### Example:

```html id="wz3qyt"
<div>Hello</div>
<p>Paragraph</p>
<section>Section</section>
```

---

# 3. Give examples of inline elements.

### Common Inline Elements:

```html id="vgsvm4"
<span>
<a>
<img>
<strong>
<em>
<label>
<input>
```

### Example:

```html id="w75t7m"
<span>Hello</span>
<a href="#">Link</a>
<strong>Bold Text</strong>
```

---

# 4. What is the difference between `<div>` and `<span>`?

| `<div>`                         | `<span>`                    |
| ------------------------------- | --------------------------- |
| Block-level element             | Inline element              |
| Takes full width                | Takes only content width    |
| Used for larger layout sections | Used for small text styling |
| Starts on new line              | Stays in same line          |

### Example:

```html id="iqvwur"
<div>
  This is div
</div>

<span>
  This is span
</span>
```

### Interview Point:

* `<div>` → Layout/Container
* `<span>` → Styling small text/content

---

# 3. Semantic HTML (MNC Focus)

---

# 1. What is Semantic HTML?

### Answer:

Semantic HTML uses meaningful tags that clearly describe the purpose of the content.

These tags make code:

* Easy to read
* Easy to maintain
* Better for SEO
* Better for accessibility

### Examples of Semantic Tags:

```html id="jv7h1r"
<header>
<footer>
<section>
<article>
<nav>
<aside>
```

---

# 2. Why should we use semantic tags?

### Answer:

Semantic tags are used because they:

* Improve code readability
* Improve SEO
* Help screen readers
* Make maintenance easier
* Clearly define webpage structure

### Interview Line:

> Semantic tags describe the meaning of content instead of just presentation.

---

# 3. Explain `<header>`, `<footer>`, `<section>`, `<article>`, `<aside>`.

---

## `<header>`

Used for:

* Logo
* Navigation
* Title
* Intro content

### Example:

```html id="lxce6r"
<header>
  <h1>My Website</h1>
</header>
```

---

## `<footer>`

Used for:

* Copyright
* Contact info
* Footer links

### Example:

```html id="4r9nnn"
<footer>
  Copyright 2026
</footer>
```

---

## `<section>`

Represents a thematic group of content.

### Example:

```html id="0zx65e"
<section>
  <h2>About Us</h2>
  <p>Company details...</p>
</section>
```

---

## `<article>`

Represents independent content.

Examples:

* Blog post
* News article
* Product card

### Example:

```html id="d7os4x"
<article>
  <h2>React Interview</h2>
  <p>Important questions...</p>
</article>
```

---

## `<aside>`

Used for side content.

Examples:

* Sidebar
* Ads
* Related links

### Example:

```html id="7lmb6e"
<aside>
  Related Posts
</aside>
```

---

# 4. What is the difference between `<section>` and `<div>`?

| `<section>`                | `<div>`                        |
| -------------------------- | ------------------------------ |
| Semantic tag               | Non-semantic tag               |
| Defines meaningful section | Generic container              |
| Better for SEO             | No SEO meaning                 |
| Used for grouped content   | Used mainly for styling/layout |

### Example:

```html id="zwcqdp"
<section>
  <h2>Services</h2>
</section>

<div class="container">
  Content
</div>
```

---

# 5. What are the benefits of semantic HTML for SEO?

### Answer:

Semantic HTML improves SEO because search engines understand webpage structure better.

### Benefits:

* Better search ranking
* Easier indexing
* Improved accessibility
* Better user experience
* Helps search engines identify important content

### Important Semantic Tags for SEO:

```html id="2xdmxk"
<header>
<nav>
<main>
<section>
<article>
<footer>
```

---

# Quick Interview Revision

| Question                 | Short Answer             |
| ------------------------ | ------------------------ |
| Block element            | Takes full width         |
| Inline element           | Takes only content width |
| `<div>`                  | Block-level container    |
| `<span>`                 | Inline container         |
| Semantic HTML            | Meaningful HTML tags     |
| Benefit of semantic tags | SEO + readability        |
| `<article>`              | Independent content      |
| `<aside>`                | Sidebar/related content  |
| `<section>`              | Thematic section         |
| `<div>` vs `<section>`   | Generic vs semantic      |


# 4. HTML Forms (Very Important)

---

# 1. What are the different form elements in HTML?

### Answer:

HTML forms are used to collect user input.

### Common Form Elements:

| Element      | Purpose             |
| ------------ | ------------------- |
| `<form>`     | Creates form        |
| `<input>`    | Input field         |
| `<textarea>` | Multi-line text     |
| `<label>`    | Label for input     |
| `<select>`   | Dropdown            |
| `<option>`   | Dropdown option     |
| `<button>`   | Button              |
| `<fieldset>` | Group form elements |
| `<legend>`   | Title for fieldset  |

### Example:

```html id="m6d2z0"
<form>
  <label>Name</label>
  <input type="text">

  <textarea></textarea>

  <select>
    <option>India</option>
  </select>

  <button>Submit</button>
</form>
```

---

# 2. Explain the difference between GET and POST methods.

| GET                    | POST                      |
| ---------------------- | ------------------------- |
| Data sent in URL       | Data sent in request body |
| Less secure            | More secure               |
| Limited data size      | Large data can be sent    |
| Used for fetching data | Used for submitting data  |
| Data visible in URL    | Data not visible in URL   |

### Example of GET:

```html id="9r0dfr"
<form method="GET">
```

### Example of POST:

```html id="9z75k4"
<form method="POST">
```

### Interview Line:

* GET → Retrieve data
* POST → Send sensitive/form data

---

# 3. What is the use of `action` and `method` in forms?

---

## `action`

Specifies where form data should be sent.

### Example:

```html id="llj0v0"
<form action="/submit">
```

---

## `method`

Specifies how data will be sent.

### Example:

```html id="3xup0k"
<form method="POST">
```

---

## Full Example:

```html id="dpc2n7"
<form action="/submit" method="POST">
  <input type="text">
</form>
```

---

# 4. What is the difference between `<input>` and `<textarea>`?

| `<input>`           | `<textarea>`               |
| ------------------- | -------------------------- |
| Single-line input   | Multi-line input           |
| Used for small text | Used for long text         |
| Self-closing tag    | Has opening & closing tags |

### Example:

```html id="dz6m5m"
<input type="text">

<textarea></textarea>
```

---

# 5. What are different input types in HTML5?

### Common Input Types:

```html id="u1v6vd"
text
password
email
number
date
time
checkbox
radio
file
url
tel
search
range
color
submit
```

### Example:

```html id="1w30ko"
<input type="email">
<input type="date">
<input type="number">
```

---

# 6. What is the use of `required`, `readonly`, `disabled` attributes?

| Attribute  | Purpose                   |
| ---------- | ------------------------- |
| `required` | Field must be filled      |
| `readonly` | Cannot edit value         |
| `disabled` | Field disabled completely |

---

## `required`

```html id="7n5g0s"
<input type="text" required>
```

User must enter value before submit.

---

## `readonly`

```html id="xuh7s7"
<input type="text" value="Admin" readonly>
```

User can see but cannot edit.

---

## `disabled`

```html id="1cm92w"
<input type="text" disabled>
```

Field becomes inactive.

---

# 7. What is form validation in HTML5?

### Answer:

Form validation checks whether user input is correct before submitting the form.

HTML5 provides built-in validation without JavaScript.

### Validation Examples:

```html id="2yc97x"
<input type="email" required>
<input type="number" min="1" max="10">
```

### Benefits:

* Reduces invalid data
* Improves user experience
* Saves development time

---

# 8. Explain `pattern` attribute.

### Answer:

The `pattern` attribute is used to validate input using regular expressions.

### Example:

```html id="3f91t5"
<input type="text" pattern="[A-Za-z]{3}">
```

### Meaning:

* Only 3 alphabets allowed

### Mobile Number Example:

```html id="46tvwb"
<input type="text" pattern="[0-9]{10}">
```

### Interview Line:

> Pattern attribute is used for custom validation using regex.

---

# 9. What is the purpose of `autocomplete`?

### Answer:

`autocomplete` helps browsers automatically fill form fields using previously entered data.

### Example:

```html id="l2sny0"
<input type="email" autocomplete="on">
```

### Values:

| Value | Meaning             |
| ----- | ------------------- |
| `on`  | Enable suggestions  |
| `off` | Disable suggestions |

### Benefits:

* Faster form filling
* Better user experience

---

# Complete Form Example

```html id="01n7t0"
<form action="/submit" method="POST">

  <label>Name</label>
  <input type="text" required>

  <label>Email</label>
  <input type="email" autocomplete="on">

  <label>Password</label>
  <input type="password">

  <label>Message</label>
  <textarea></textarea>

  <button type="submit">Submit</button>

</form>
```

---

# Quick Interview Revision

| Question       | Short Answer         |
| -------------- | -------------------- |
| `<form>` use   | Collect user input   |
| GET method     | Data in URL          |
| POST method    | Data in request body |
| `action`       | Where data goes      |
| `method`       | How data is sent     |
| `<input>`      | Single-line field    |
| `<textarea>`   | Multi-line field     |
| `required`     | Mandatory field      |
| `readonly`     | Cannot edit          |
| `disabled`     | Completely disabled  |
| `pattern`      | Regex validation     |
| `autocomplete` | Auto-fill form data  |

# 5. HTML5 New Features (Mostly Asked)

---

# 1. What are the new features introduced in HTML5?

### Answer:

HTML5 introduced many new features for modern web development.

### Major Features of HTML5:

* Semantic tags
* Audio & Video support
* Canvas
* SVG
* Local Storage
* New form input types
* Geolocation API
* Drag & Drop
* Web Workers

### Semantic Tags:

```html id="wjlwm7"
<header>
<footer>
<section>
<article>
<nav>
```

### Interview Line:

> HTML5 provides multimedia support, semantic structure, and better APIs without plugins.

---

# 2. What are `<audio>` and `<video>` tags?

### Answer:

These tags are used to play media files directly in the browser without plugins.

---

## `<audio>` Tag

### Example:

```html id="tcf58l"
<audio controls>
  <source src="song.mp3" type="audio/mp3">
</audio>
```

### Common Attributes:

| Attribute  | Purpose            |
| ---------- | ------------------ |
| `controls` | Show controls      |
| `autoplay` | Play automatically |
| `loop`     | Repeat audio       |

---

## `<video>` Tag

### Example:

```html id="gm99iy"
<video width="400" controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

### Interview Line:

> HTML5 audio and video tags remove the need for Flash plugins.

---

# 3. What is the difference between cookies and localStorage?

| Cookies                      | localStorage                   |
| ---------------------------- | ------------------------------ |
| Small storage size           | Larger storage size            |
| Sent to server automatically | Not sent to server             |
| Has expiry time              | Stays until manually removed   |
| Less secure                  | More secure for client storage |

### Interview Line:

* Cookies → Server communication
* localStorage → Browser storage

---

# 4. What is the purpose of `data-*` attributes?

### Answer:

`data-*` attributes are used to store custom data inside HTML elements.

### Example:

```html id="o8vvvh"
<div data-id="101">
  Product
</div>
```

### JavaScript Access:

```javascript id="rldhtq"
element.dataset.id
```

### Benefits:

* Store extra custom information
* Easy access using JavaScript

---

# 5. What is the `<canvas>` element?

### Answer:

`<canvas>` is used to draw graphics using JavaScript.

Used for:

* Games
* Charts
* Animations
* Drawing

### Example:

```html id="7z30uj"
<canvas id="myCanvas"></canvas>
```

### Interview Line:

> Canvas provides bitmap-based graphics rendering.

---

# 6. What is SVG in HTML?

### Answer:

SVG stands for **Scalable Vector Graphics**.

It is used to create vector-based graphics.

### Features:

* Scalable without losing quality
* Better for icons and logos
* XML-based

### Example:

```html id="p1b2n5"
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" />
</svg>
```

### Difference Between Canvas and SVG

| Canvas                  | SVG                    |
| ----------------------- | ---------------------- |
| Pixel-based             | Vector-based           |
| Better for games        | Better for icons/logos |
| Uses JavaScript drawing | XML-based elements     |

---

# 6. SEO & Accessibility (MNC Level)

---

# 1. What is accessibility in HTML?

### Answer:

Accessibility means making websites usable for everyone, including people with disabilities.

### Accessibility helps:

* Screen reader users
* Keyboard navigation users
* Visually impaired users

### Techniques:

* Semantic HTML
* Alt text
* ARIA attributes
* Proper headings

### Interview Line:

> Accessibility improves usability for all users.

---

# 2. What is the purpose of `alt` attribute in images?

### Answer:

The `alt` attribute provides alternative text for images.

### Used for:

* Screen readers
* SEO
* When image fails to load

### Example:

```html id="n3qg9o"
<img src="logo.png" alt="Company Logo">
```

### Interview Line:

> Alt text improves accessibility and SEO.

---

# 3. What are ARIA attributes?

### Answer:

ARIA stands for **Accessible Rich Internet Applications**.

ARIA attributes help screen readers understand UI components.

### Common ARIA Attributes:

| Attribute       | Purpose                  |
| --------------- | ------------------------ |
| `aria-label`    | Label element            |
| `aria-hidden`   | Hide from screen readers |
| `aria-expanded` | Expanded/collapsed state |

### Example:

```html id="0e2lzc"
<button aria-label="Close Menu">
  X
</button>
```

---

# 4. What is the use of `role` attribute?

### Answer:

The `role` attribute defines the purpose of an element for accessibility tools.

### Example:

```html id="9h73c9"
<div role="navigation">
```

### Common Roles:

| Role         | Meaning            |
| ------------ | ------------------ |
| `navigation` | Navigation section |
| `button`     | Button             |
| `dialog`     | Popup dialog       |

### Interview Line:

> Role attribute helps assistive technologies identify element behavior.

---

# 5. What is the difference between `id` and `class`?

| `id`               | `class`            |
| ------------------ | ------------------ |
| Unique             | Reusable           |
| One element only   | Multiple elements  |
| Accessed using `#` | Accessed using `.` |

### Example:

```html id="0v9zxl"
<div id="header"></div>

<div class="card"></div>
<div class="card"></div>
```

### CSS Example:

```css id="25u4e1"
#header{
  color:red;
}

.card{
  color:blue;
}
```

---

# 6. Why is heading hierarchy important (`h1` to `h6`)?

### Answer:

Heading hierarchy creates proper document structure.

### Benefits:

* Better SEO
* Better readability
* Better accessibility
* Helps screen readers

### Correct Structure:

```html id="0w74yx"
<h1>Main Title</h1>
<h2>Section</h2>
<h3>Subsection</h3>
```

### Important Rule:

* Use only one `<h1>` for main page title
* Follow proper order (`h1 → h2 → h3`)

### Interview Line:

> Proper heading hierarchy improves SEO and accessibility.

---

# Quick Interview Revision

| Question          | Short Answer                    |
| ----------------- | ------------------------------- |
| HTML5 features    | Semantic tags, multimedia, APIs |
| `<audio>`         | Play audio                      |
| `<video>`         | Play video                      |
| localStorage      | Browser storage                 |
| Cookies           | Server communication            |
| `data-*`          | Custom data storage             |
| `<canvas>`        | Draw graphics                   |
| SVG               | Vector graphics                 |
| Accessibility     | Website usable for everyone     |
| `alt` attribute   | Alternative image text          |
| ARIA              | Accessibility attributes        |
| `role` attribute  | Defines element purpose         |
| `id`              | Unique                          |
| `class`           | Reusable                        |
| Heading hierarchy | SEO + structure                 |

# 7. Tables & Lists (Small Company Focus)

---

# 1. How do you create tables in HTML?

### Answer:

HTML tables are created using:

* `<table>`
* `<tr>` → Table row
* `<th>` → Table heading
* `<td>` → Table data

### Example:

```html id="u0s4l0"
<table border="1">

  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>

  <tr>
    <td>Krupa</td>
    <td>25</td>
  </tr>

</table>
```

---

# 2. What is the difference between `<thead>`, `<tbody>`, `<tfoot>`?

| Tag       | Purpose              |
| --------- | -------------------- |
| `<thead>` | Table header section |
| `<tbody>` | Main table body      |
| `<tfoot>` | Table footer section |

### Example:

```html id="kfh6qw"
<table border="1">

  <thead>
    <tr>
      <th>Name</th>
      <th>Salary</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>John</td>
      <td>50000</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Total</td>
      <td>50000</td>
    </tr>
  </tfoot>

</table>
```

### Benefits:

* Better structure
* Easier styling
* Better readability

---

# 3. What is `colspan` and `rowspan`?

---

## `colspan`

Used to merge columns.

### Example:

```html id="5h6jlwm"
<td colspan="2">Merged Column</td>
```

---

## `rowspan`

Used to merge rows.

### Example:

```html id="hl53m9"
<td rowspan="2">Merged Row</td>
```

---

## Full Example:

```html id="0l9ygu"
<table border="1">

  <tr>
    <td colspan="2">Header</td>
  </tr>

  <tr>
    <td rowspan="2">Name</td>
    <td>Krupa</td>
  </tr>

  <tr>
    <td>Modi</td>
  </tr>

</table>
```

---

# 4. Difference between ordered and unordered list.

| Ordered List | Unordered List |
| ------------ | -------------- |
| Uses numbers | Uses bullets   |
| `<ol>` tag   | `<ul>` tag     |

---

## Ordered List Example:

```html id="jlwmwq"
<ol>
  <li>HTML</li>
  <li>CSS</li>
</ol>
```

### Output:

1. HTML
2. CSS

---

## Unordered List Example:

```html id="om04uc"
<ul>
  <li>HTML</li>
  <li>CSS</li>
</ul>
```

### Output:

* HTML
* CSS

---

# 5. What is a definition list?

### Answer:

A definition list is used to display terms and their descriptions.

### Tags Used:

| Tag    | Purpose                |
| ------ | ---------------------- |
| `<dl>` | Definition list        |
| `<dt>` | Definition term        |
| `<dd>` | Definition description |

### Example:

```html id="3h24hc"
<dl>

  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>

  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>

</dl>
```

---

# 8. Media & Performance Questions

---

# 1. How do you optimize images in HTML?

### Answer:

Image optimization improves website performance and loading speed.

### Techniques:

* Use compressed images
* Use modern formats like WebP
* Use proper image size
* Use lazy loading
* Use responsive images

### Example:

```html id="y4fihn"
<img src="image.webp" width="300" loading="lazy">
```

### Interview Line:

> Optimized images improve page speed and SEO.

---

# 2. What is lazy loading in HTML?

### Answer:

Lazy loading delays image loading until the image becomes visible on screen.

This improves:

* Performance
* Page speed
* Initial loading time

### Example:

```html id="ys3zt2"
<img src="image.jpg" loading="lazy">
```

### Interview Line:

> Lazy loading loads images only when needed.

---

# 3. What is `<picture>` tag used for?

### Answer:

`<picture>` is used for responsive images.

It allows different images for:

* Different screen sizes
* Different resolutions

### Example:

```html id="wiyv6k"
<picture>

  <source media="(max-width:600px)" srcset="mobile.jpg">

  <source media="(max-width:1000px)" srcset="tablet.jpg">

  <img src="desktop.jpg" alt="Image">

</picture>
```

### Benefits:

* Better responsiveness
* Better performance
* Device-specific images

---

# 4. Difference between relative and absolute paths.

| Relative Path            | Absolute Path               |
| ------------------------ | --------------------------- |
| Relative to current file | Full URL/path               |
| Shorter                  | Complete address            |
| Used inside project      | Used for external resources |

---

## Relative Path Example:

```html id="qvjlwm"
<img src="images/logo.png">
```

---

## Absolute Path Example:

```html id="9kx8iu"
<img src="https://example.com/logo.png">
```

### Interview Line:

* Relative → Internal project files
* Absolute → External resources

---

# Quick Interview Revision

| Question      | Short Answer            |
| ------------- | ----------------------- |
| `<table>`     | Create table            |
| `<tr>`        | Table row               |
| `<th>`        | Table heading           |
| `<td>`        | Table data              |
| `<thead>`     | Header section          |
| `<tbody>`     | Main content            |
| `<tfoot>`     | Footer section          |
| `colspan`     | Merge columns           |
| `rowspan`     | Merge rows              |
| `<ol>`        | Ordered list            |
| `<ul>`        | Unordered list          |
| `<dl>`        | Definition list         |
| Lazy loading  | Load images when needed |
| `<picture>`   | Responsive images       |
| Relative path | Internal path           |
| Absolute path | Full URL                |


# 9. Interview Practical Scenarios (2–4 Years)

---

# 1. How do you create a responsive navbar using HTML?

### Answer:

A responsive navbar is created using:

* Semantic tags
* Flexbox/CSS
* Media queries

### Basic HTML Structure:

```html id="zfrjtz"
<nav>

  <div class="logo">
    MyLogo
  </div>

  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>

</nav>
```

### Important Points:

* Use `<nav>` semantic tag
* Use media queries for mobile responsiveness
* Use Flexbox for alignment

### Interview Line:

> Responsive navbar adjusts layout based on screen size.

---

# 2. How do you structure a landing page using semantic tags?

### Answer:

A landing page should use semantic HTML for better SEO and readability.

### Example Structure:

```html id="0fe5x4"
<header>
  Header Content
</header>

<nav>
  Navigation
</nav>

<section>
  Hero Section
</section>

<article>
  Features
</article>

<aside>
  Sidebar
</aside>

<footer>
  Footer
</footer>
```

### Benefits:

* Better SEO
* Better accessibility
* Easy maintenance

---

# 3. How do you create a login form with validations?

### Example:

```html id="mjlwm5"
<form>

  <label>Email</label>
  <input 
    type="email"
    required
  >

  <label>Password</label>
  <input 
    type="password"
    minlength="6"
    required
  >

  <button type="submit">
    Login
  </button>

</form>
```

### Validation Used:

| Validation     | Purpose            |
| -------------- | ------------------ |
| `required`     | Mandatory field    |
| `type="email"` | Email validation   |
| `minlength`    | Minimum characters |

### Interview Line:

> HTML5 provides built-in form validations without JavaScript.

---

# 4. How do you embed a YouTube video?

### Answer:

YouTube videos are embedded using `<iframe>`.

### Example:

```html id="mq2cw4"
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/video-id"
  allowfullscreen>
</iframe>
```

### Interview Point:

* `allowfullscreen` enables fullscreen mode

---

# 5. How do you make a downloadable file link?

### Answer:

Use the `download` attribute.

### Example:

```html id="u8fjlwm"
<a href="resume.pdf" download>
  Download Resume
</a>
```

### Interview Line:

> Download attribute forces browser to download the file.

---

# 6. How do you open a link in a new tab securely?

### Answer:

Use:

* `target="_blank"`
* `rel="noopener noreferrer"`

### Example:

```html id="6jx0nk"
<a 
  href="https://google.com"
  target="_blank"
  rel="noopener noreferrer"
>
  Open Google
</a>
```

### Why `rel="noopener noreferrer"`?

* Improves security
* Prevents tab hijacking

### Interview Line:

> Always use `noopener noreferrer` with `_blank` for security.

---

# 10. Advanced HTML Questions (4 Years + MNC)

---

# 1. What is the Shadow DOM?

### Answer:

Shadow DOM is a browser technology used to create isolated DOM trees.

It helps:

* Encapsulate styles
* Avoid CSS conflicts
* Build reusable components

### Example:

```javascript id="rj8ncb"
element.attachShadow({ mode: "open" })
```

### Interview Line:

> Shadow DOM provides style and structure encapsulation.

---

# 2. What is Web Components in HTML?

### Answer:

Web Components are reusable custom HTML elements.

### Main Technologies:

| Technology      | Purpose            |
| --------------- | ------------------ |
| Custom Elements | Create custom tags |
| Shadow DOM      | Encapsulation      |
| HTML Templates  | Reusable templates |

### Example:

```html id="jlwmh5"
<my-card></my-card>
```

### Benefits:

* Reusable UI
* Framework independent
* Encapsulation

---

# 3. What is the difference between `<iframe>` and `<embed>`?

| `<iframe>`             | `<embed>`                     |
| ---------------------- | ----------------------------- |
| Embeds another webpage | Embeds external content/media |
| Can load HTML pages    | Used for PDFs/media           |
| More commonly used     | Less flexible                 |

---

## `<iframe>` Example:

```html id="jlwmyn"
<iframe src="page.html"></iframe>
```

---

## `<embed>` Example:

```html id="5l1m7v"
<embed src="file.pdf">
```

---

# 4. How does browser render HTML?

### Answer:

Browser rendering process:

1. Browser reads HTML
2. Creates DOM tree
3. Loads CSS
4. Creates CSSOM
5. Combines DOM + CSSOM
6. Creates Render Tree
7. Paints content on screen

### Flow:

```text
HTML → DOM → CSSOM → Render Tree → Layout → Paint
```

### Interview Line:

> Browser converts HTML into DOM and renders UI step-by-step.

---

# 5. What happens when HTML has invalid nesting?

### Answer:

Invalid nesting means placing elements incorrectly.

### Example:

```html id="yc7m4u"
<p>
  <div>Hello</div>
</p>
```

### Problem:

* Browser auto-corrects structure
* Unexpected UI issues can happen
* Layout bugs may occur

### Correct Example:

```html id="7r4r83"
<div>
  <p>Hello</p>
</div>
```

### Interview Line:

> Invalid nesting can cause unpredictable browser behavior.

---

# Quick Interview Revision

| Question              | Short Answer                   |
| --------------------- | ------------------------------ |
| Responsive navbar     | Uses Flexbox + media queries   |
| Semantic landing page | Uses semantic tags             |
| Login validation      | HTML5 validations              |
| YouTube embed         | `<iframe>`                     |
| Download file         | `download` attribute           |
| Open secure new tab   | `_blank + noopener noreferrer` |
| Shadow DOM            | Encapsulated DOM               |
| Web Components        | Reusable custom elements       |
| `<iframe>`            | Embed webpage                  |
| `<embed>`             | Embed media/files              |
| Browser rendering     | DOM → CSSOM → Render           |
| Invalid nesting       | Causes rendering issues        |


# Most Asked HTML Interview Questions (Quick Revision)

---

# 1. Difference between block and inline elements

| Block Elements                      | Inline Elements           |
| ----------------------------------- | ------------------------- |
| Takes full width                    | Takes only required width |
| Starts on new line                  | Stays in same line        |
| Can contain block & inline elements | Usually contains text     |

### Block Element Examples:

```html id="jlwm52"
<div>
<p>
<section>
<h1>
```

### Inline Element Examples:

```html id="jlwmr0"
<span>
<a>
<strong>
<img>
```

### Example:

```html id="jlwmg8"
<div>Hello</div>
<span>Hello</span>
```

### Interview Line:

> Block elements take full width while inline elements take only content width.

---

# 2. Semantic HTML

### Answer:

Semantic HTML uses meaningful tags that describe content properly.

### Examples:

```html id="jlwm0q"
<header>
<footer>
<section>
<article>
<nav>
```

### Benefits:

* Better SEO
* Better accessibility
* Easy maintenance
* Better readability

### Interview Line:

> Semantic tags define the meaning of content clearly.

---

# 3. HTML5 Features

### Major HTML5 Features:

* Semantic tags
* Audio & Video support
* Canvas
* SVG
* LocalStorage
* New form input types
* Geolocation API

### Example:

```html id="jlwm3p"
<audio>
<video>
<canvas>
```

### Interview Line:

> HTML5 introduced multimedia support and semantic structure.

---

# 4. Forms Validation

### Answer:

HTML5 form validation checks user input before form submission.

### Example:

```html id="jlwmho"
<input 
  type="email"
  required
>
```

### Common Validation Attributes:

| Attribute      | Purpose            |
| -------------- | ------------------ |
| `required`     | Mandatory field    |
| `minlength`    | Minimum characters |
| `pattern`      | Regex validation   |
| `type="email"` | Email validation   |

### Interview Line:

> HTML5 provides built-in validation without JavaScript.

---

# 5. LocalStorage vs SessionStorage

| LocalStorage                     | SessionStorage               |
| -------------------------------- | ---------------------------- |
| Permanent storage                | Temporary storage            |
| Data remains after browser close | Data removed after tab close |
| Larger storage                   | Smaller storage              |

### Example:

```javascript id="jlwmz9"
localStorage.setItem("name", "Krupa")

sessionStorage.setItem("name", "Krupa")
```

### Interview Line:

* LocalStorage → Long-term storage
* SessionStorage → Session-based storage

---

# 6. Accessibility + ARIA

## Accessibility

Accessibility means making websites usable for everyone.

### Benefits:

* Screen reader support
* Better usability
* Better SEO

---

## ARIA

ARIA stands for:

```text id="jlwm3x"
Accessible Rich Internet Applications
```

### ARIA Example:

```html id="jlwm2n"
<button aria-label="Close">
  X
</button>
```

### Common ARIA Attributes:

| Attribute       | Purpose                  |
| --------------- | ------------------------ |
| `aria-label`    | Label element            |
| `aria-hidden`   | Hide from screen readers |
| `aria-expanded` | Expanded state           |

### Interview Line:

> ARIA improves accessibility for assistive technologies.

---

# 7. `<div>` vs `<section>`

| `<div>`            | `<section>`                |
| ------------------ | -------------------------- |
| Non-semantic       | Semantic                   |
| Generic container  | Meaningful content section |
| Mainly for styling | Better for SEO             |

### Example:

```html id="jlwm7u"
<div class="container">
</div>

<section>
  About Us
</section>
```

### Interview Line:

> `<section>` provides meaning while `<div>` is just a container.

---

# 8. GET vs POST

| GET               | POST                |
| ----------------- | ------------------- |
| Data sent in URL  | Data sent in body   |
| Less secure       | More secure         |
| Limited data      | Large data          |
| Used for fetching | Used for submitting |

### Example:

```html id="jlwm5d"
<form method="GET">
<form method="POST">
```

### Interview Line:

* GET → Retrieve data
* POST → Send secure/sensitive data

---

# 9. `id` vs `class`

| `id`               | `class`             |
| ------------------ | ------------------- |
| Unique             | Reusable            |
| Used once          | Used multiple times |
| Accessed using `#` | Accessed using `.`  |

### Example:

```html id="jlwmcf"
<div id="header"></div>

<div class="card"></div>
```

### CSS:

```css id="jlwmw1"
#header{
  color:red;
}

.card{
  color:blue;
}
```

### Interview Line:

> `id` is unique while `class` is reusable.

---

# 10. SEO Importance of Semantic Tags

### Answer:

Semantic tags help search engines understand webpage structure.

### Important Semantic Tags:

```html id="jlwmq7"
<header>
<nav>
<main>
<section>
<article>
<footer>
```

### SEO Benefits:

* Better indexing
* Better ranking
* Improved accessibility
* Better readability

### Interview Line:

> Semantic HTML improves SEO and accessibility.

---

# One-Line Quick Revision

| Topic           | One-Line Answer           |
| --------------- | ------------------------- |
| Block element   | Takes full width          |
| Inline element  | Takes required width      |
| Semantic HTML   | Meaningful HTML tags      |
| HTML5           | Modern HTML version       |
| Form validation | Validates user input      |
| LocalStorage    | Permanent browser storage |
| SessionStorage  | Temporary browser storage |
| ARIA            | Accessibility attributes  |
| `<div>`         | Generic container         |
| `<section>`     | Semantic section          |
| GET             | Data in URL               |
| POST            | Data in request body      |
| `id`            | Unique                    |
| `class`         | Reusable                  |
| Semantic SEO    | Better search ranking     |


Haan, Jarvis ke hisaab se jo tumne abhi cover kiya hai wo **strong HTML interview preparation** hai — especially 2–4 years React/frontend developer interviews ke liye.
Lekin MNCs aur product-based companies kabhi-kabhi kuch extra practical aur advanced HTML topics bhi puchte hain.

Ye important topics abhi add karne chahiye:

---

# 1. Meta Tags

## Questions:

* What are meta tags?
* Why are meta tags important?
* What is viewport meta tag?

### Example:

```html id="xv9o6s"
<meta charset="UTF-8">

<meta 
  name="viewport"
  content="width=device-width, initial-scale=1.0"
>
```

### Interview Point:

Viewport tag helps make websites responsive.

---

# 2. Difference Between Cookies, LocalStorage & SessionStorage

Ye bahot puchte hai comparison form mein.

| Feature       | Cookies    | LocalStorage | SessionStorage |
| ------------- | ---------- | ------------ | -------------- |
| Storage Size  | Small      | Large        | Large          |
| Expiry        | Has expiry | Permanent    | Tab close      |
| Server Access | Yes        | No           | No             |

---

# 3. iframe Security Issues

## Questions:

* What are iframe security risks?
* What is sandbox attribute?

### Example:

```html id="rjlwm5"
<iframe 
  src="page.html"
  sandbox>
</iframe>
```

### Interview Point:

Sandbox restricts iframe permissions.

---

# 4. preload, defer, async

Very common in MNC interviews.

| Attribute | Behavior                    |
| --------- | --------------------------- |
| async     | Loads JS parallel           |
| defer     | Loads JS after HTML parsing |

### Example:

```html id="jlwm5u"
<script src="app.js" defer></script>

<script src="app.js" async></script>
```

### Interview Line:

* async → Executes immediately after loading
* defer → Executes after DOM creation

---

# 5. Difference Between Semantic and Non-Semantic Tags

| Semantic    | Non-Semantic |
| ----------- | ------------ |
| Meaningful  | Generic      |
| `<section>` | `<div>`      |
| `<article>` | `<span>`     |

---

# 6. DOM (Very Important)

## Questions:

* What is DOM?
* What is DOM tree?
* Difference between HTML and DOM?

### Interview Line:

> DOM is the browser representation of HTML document.

---

# 7. Critical Rendering Path

Product-based companies puch sakti hai.

### Flow:

```text id="jlwm38"
HTML → DOM → CSSOM → Render Tree → Paint
```

### Interview Point:

Browser converts HTML + CSS into visible UI.

---

# 8. Progressive Enhancement vs Graceful Degradation

### Progressive Enhancement

Basic functionality first.

### Graceful Degradation

Full functionality first.

---

# 9. SEO Advanced Questions

## Questions:

* Why only one h1?
* Difference between robots.txt and sitemap?
* What is canonical tag?

### Canonical Example:

```html id="jlwmim"
<link 
  rel="canonical"
  href="https://example.com"
>
```

---

# 10. Accessibility Advanced

## Questions:

* Keyboard navigation?
* tabindex?
* Screen readers?

### Example:

```html id="jlwm06"
<button tabindex="0">
  Submit
</button>
```

---

# 11. Responsive Design Basics

## Questions:

* What is responsive design?
* What is viewport?
* Mobile-first approach?

### Example:

```css id="jlwm6k"
@media(max-width:768px){
}
```

---

# 12. preload / prefetch / preconnect

Performance optimization questions.

### Example:

```html id="jlwm0c"
<link rel="preload" href="style.css">

<link rel="preconnect" href="https://fonts.googleapis.com">
```

---

# 13. Difference Between SVG and Canvas

Very common frontend question.

| SVG              | Canvas           |
| ---------------- | ---------------- |
| Vector           | Pixel            |
| Better for icons | Better for games |


## Focus: Semantic HTML, Data Attributes, Accessibility

---

# 1. Browser HTML ko kaise parse karta hai?

### Answer:

Browser HTML ko line-by-line read karta hai aur DOM (Document Object Model) tree banata hai.

### Steps:

```text id="n8ocf1"
HTML → DOM → CSSOM → Render Tree → Layout → Paint
```

### Process:

1. HTML parse hota hai
2. DOM tree create hota hai
3. CSS parse hoti hai
4. Render tree banta hai
5. Browser UI draw karta hai

### Interview Line:

> Browser HTML ko parse karke DOM tree banata hai jisse webpage render hota hai.

---

# 2. Meta tags ka real-world use kya hai?

### Answer:

Meta tags webpage ki metadata information provide karte hain.

### Uses:

* SEO
* Responsive design
* Character encoding
* Social sharing preview

### Example:

```html id="jlwm0k"
<meta charset="UTF-8">

<meta 
  name="viewport"
  content="width=device-width, initial-scale=1.0"
>

<meta 
  name="description"
  content="Frontend Developer Portfolio"
>
```

---

# 3. `section` vs `article` kab use karte ho?

| section               | article                     |
| --------------------- | --------------------------- |
| Related content group | Independent content         |
| Part of webpage       | Standalone reusable content |

### Example:

```html id="jlwm3n"
<section>
  <h2>Services</h2>
</section>

<article>
  <h2>Blog Post</h2>
</article>
```

### Interview Line:

> Article independent hota hai, section grouped content hota hai.

---

# 4. Kya `header` aur `footer` multiple times use ho sakte hain?

### Answer:

Haan.

`header` aur `footer` multiple times use ho sakte hain:

* Page level
* Article level
* Section level

### Example:

```html id="jlwm7m"
<header>Main Header</header>

<article>
  <header>Article Header</header>
</article>
```

---

# 5. `aside` tag ka real use-case batao

### Answer:

`aside` side content ke liye use hota hai.

### Real-world Examples:

* Sidebar
* Ads
* Related articles
* Author info

### Example:

```html id="jlwm5a"
<aside>
  Related Posts
</aside>
```

---

# 6. `article` ke andar `section` allowed hai? Kyun?

### Answer:

Haan allowed hai.

Kyunki:

* Article independent content hota hai
* Uske andar multiple logical sections ho sakte hain

### Example:

```html id="jlwm6y"
<article>

  <section>
    Introduction
  </section>

  <section>
    Conclusion
  </section>

</article>
```

---

# 7. `section` ke andar `article` allowed hai?

### Answer:

Haan.

### Example:

```html id="jlwmha"
<section>

  <article>
    Blog 1
  </article>

  <article>
    Blog 2
  </article>

</section>
```

### Interview Line:

> Section grouped content hota hai jisme multiple articles ho sakte hain.

---

# 8. Kya `div` completely avoid kar dena chahiye?

### Answer:

Nahi.

`div` abhi bhi useful hai:

* Layout
* Styling
* Wrapper container

### Rule:

* Semantic tag available ho → semantic use karo
* Generic container chahiye → div use karo

### Interview Line:

> Semantic first approach follow karni chahiye, but div still important hai.

---

# 9. Semantic tags ka CSS ya JS pe koi effect hota hai?

### Answer:

Direct functional effect nahi hota.

But:

* Better readability
* Better maintainability
* Better accessibility
* Better SEO

### CSS Example:

```css id="jlwmux"
section{
  padding:20px;
}
```

---

# 10. Screen reader semantic tags ko kaise use karta hai?

### Answer:

Screen readers semantic tags ko landmarks ki tarah treat karte hain.

### Example:

* `nav` → Navigation
* `main` → Main content
* `aside` → Sidebar

Isse visually impaired users easily navigate kar paate hain.

---

# 11. `main` tag ek page me kitni baar hona chahiye?

### Answer:

Sirf ek baar.

### Reason:

Main content unique hona chahiye.

### Example:

```html id="jlwmf4"
<main>
  Main Content
</main>
```

---

# 12. Kya `nav` ke andar `nav` ho sakta hai?

### Answer:

Technically possible hai but generally avoid karte hain.

### Use-case:

Agar separate navigation groups ho.

### Example:

```html id="jlwm89"
<nav>
  Main Menu

  <nav>
    Footer Links
  </nav>

</nav>
```

---

# 13. `figure` aur `figcaption` ka use kya hai?

### Answer:

Media content + caption dikhane ke liye use hota hai.

### Example:

```html id="jlwm18"
<figure>

  <img src="chart.png">

  <figcaption>
    Sales Chart 2026
  </figcaption>

</figure>
```

### Benefits:

* Better semantics
* Better accessibility

---

# 14. `time` tag ka real-world use?

### Answer:

Date/time represent karne ke liye.

### Example:

```html id="jlwm6x"
<time datetime="2026-05-21">
  May 21, 2026
</time>
```

### Benefits:

* SEO
* Machine-readable dates

---

# 15. `address` tag ka correct use kya hai?

### Answer:

Author/company contact information ke liye.

### Example:

```html id="jlwm4t"
<address>
  Pune, Maharashtra
</address>
```

### Wrong Use:

❌ Random location styling ke liye use nahi karna.

---

# 16. `data-id` vs `id` me difference?

| data-id                       | id                        |
| ----------------------------- | ------------------------- |
| Custom data storage           | Unique element identifier |
| Multiple same values possible | Unique होना चाहिए         |
| JS communication              | CSS/JS targeting          |

### Example:

```html id="jlwm8s"
<div 
  id="card"
  data-id="101">
</div>
```

---

# 17. Kya data attributes SEO friendly hote hain?

### Answer:

Direct SEO impact nahi hota.

But:

* JS integrations
* Analytics
* Dynamic UI handling

ke liye useful hote hain.

---

# 18. Data attributes ko JavaScript me kaise access karte ho?

### Example:

```html id="jlwmn7"
<button data-user-id="101">
  Click
</button>
```

### JavaScript:

```javascript id="jlwm7r"
const btn = document.querySelector("button")

console.log(btn.dataset.userId)
```

---

# 19. Kya data attributes CSS me use ho sakte hain?

### Answer:

Haan.

### Example:

```css id="jlwmu2"
[data-theme="dark"]{
  background:black;
}
```

---

# 20. Data attributes ka misuse kya ho sakta hai?

### Answer:

❌ Sensitive data store karna
❌ Business logic store karna
❌ Excessive data storage

### Wrong Example:

```html id="jlwmh2"
<div data-password="12345">
```

---

# 21. `data-*` attributes aur custom attributes me difference?

| data-*                 | Custom Attribute        |
| ---------------------- | ----------------------- |
| Valid HTML5            | Invalid/non-standard    |
| Recommended            | Avoid                   |
| Accessible via dataset | Direct attribute access |

### Correct:

```html id="jlwm8r"
<div data-id="1"></div>
```

### Wrong:

```html id="jlwm3e"
<div custom-id="1"></div>
```

---

# 22. Kya data attributes DOM ka part hote hain?

### Answer:

Haan.

Data attributes DOM attributes ka hi part hote hain.

### Access:

```javascript id="jlwmh8"
element.dataset
```

---

# 23. Event delegation me data attributes kaise help karte hain?

### Answer:

Different buttons/actions identify karne me help karte hain.

### Example:

```html id="jlwmxt"
<button data-action="delete">
```

### JavaScript:

```javascript id="jlwm9l"
if(e.target.dataset.action === "delete"){
}
```

---

# 24. `dataset` kya hota hai?

### Answer:

`dataset` object data attributes ko access karne ke liye use hota hai.

### Example:

```javascript id="jlwmjl"
element.dataset.userId
```

---

# 25. `dataset` camelCase me kyun convert hota hai?

### Example:

```html id="jlwm4v"
data-user-name
```

JavaScript me:

```javascript id="jlwmbo"
element.dataset.userName
```

### Reason:

JavaScript camelCase convention follow karta hai.

---

# 26. Kya data attributes dynamically change kar sakte hain?

### Answer:

Haan.

### Example:

```javascript id="jlwm5s"
element.dataset.status = "active"
```

---

# 27. Performance pe data attributes ka koi impact hota hai?

### Answer:

Normally negligible impact hota hai.

But:

* Excessive attributes
* Huge data storage

performance affect kar sakte hain.

---

# 28. Analytics tracking me data attributes ka role?

### Answer:

Tracking identifiers store karne ke liye.

### Example:

```html id="jlwm0n"
<button data-track="signup-btn">
```

---

# 29. A/B testing me data attributes ka use?

### Example:

```html id="jlwm1i"
<div data-variant="A">
```

Different UI variants identify karne ke liye.

---

# 30. `aria-*` vs semantic tags difference?

| Semantic Tags          | ARIA                      |
| ---------------------- | ------------------------- |
| Native meaning         | Extra accessibility info  |
| Built-in accessibility | Accessibility enhancement |

### Interview Line:

> Semantic first, ARIA second.

---

# 31. Kab `aria-label` use karna chahiye?

### Answer:

Jab visible label available na ho.

### Example:

```html id="jlwmmt"
<button aria-label="Close">
  X
</button>
```

---

# 32. Kya aria attributes semantic tags ko replace kar sakte hain?

### Answer:

Nahi.

Semantic HTML pehle prefer karna chahiye.

ARIA sirf enhancement ke liye use hota hai.

---

# 33. Poor semantic HTML ke kya drawbacks hain?

### Drawbacks:

* Bad SEO
* Poor accessibility
* Difficult maintenance
* Bad readability

---

# 34. Legacy project me semantic HTML kaise improve karoge?

### Steps:

1. Audit existing HTML
2. Replace unnecessary divs
3. Add semantic structure
4. Improve headings
5. Add ARIA where needed

---

# 35. SEO issue aa raha hai — HTML level pe kya check karoge?

### Checklist:

✅ Proper headings
✅ Semantic tags
✅ Meta tags
✅ Alt attributes
✅ Page title
✅ Structured content
✅ Mobile responsiveness

---

# Rapid-Fire Answers

| Question           | One-Line Answer                |
| ------------------ | ------------------------------ |
| Semantic HTML      | Meaningful HTML structure      |
| Data attribute     | Custom HTML data storage       |
| `article` vs `div` | Semantic vs generic            |
| Accessibility      | Making web usable for everyone |
| `main` tag         | Main unique content            |
| `dataset`          | JS object for data attributes  |
| `time` tag         | Machine-readable dates         |
| `figure`           | Media container with caption   |


Haan, ye question maine upar cover kiya hai — but short form me tha.
Ye raha proper interview-ready answer:

---

# Data attributes kya hote hain?

### Answer:

Data attributes custom attributes hote hain jo HTML elements me extra information store karne ke liye use hote hain.

Ye always `data-` prefix se start hote hain.

### Syntax:

```html id="mbc3ny"
data-*
```

### Example:

```html id="qk3w5g"
<button data-user-id="101">
  Delete User
</button>
```

Yaha:

```html id="q5ksbn"
data-user-id="101"
```

ek custom data attribute hai.

---

# Data Attributes ka Purpose

Data attributes mainly use hote hain:

* JavaScript communication
* Analytics tracking
* Dynamic UI handling
* Event delegation
* Testing

---

# JavaScript me Access

### Example:

```javascript id="f8prrz"
const btn = document.querySelector("button")

console.log(btn.dataset.userId)
```

### Output:

```text id="i79d1q"
101
```

---

# Important Points

| Point               | Explanation           |
| ------------------- | --------------------- |
| Starts with `data-` | HTML5 standard        |
| Stores custom data  | Extra information     |
| Accessible via JS   | Using `dataset`       |
| SEO impact          | No direct SEO benefit |

---

# Interview Line

> Data attributes HTML aur JavaScript ke beech clean communication provide karte hain without affecting UI structure.


# Accessibility (WCAG) - Interview Notes

# What is Accessibility?

Accessibility means making websites usable for everyone including:

- Disabled users
- Screen reader users
- Keyboard users

---

# What is WCAG?

WCAG stands for:

# Web Content Accessibility Guidelines

These are rules for making websites accessible.

---

# Why Accessibility is Important?

- Better user experience
- Helps disabled users
- Improves SEO
- Important in real projects

---

# 1. aria-label

Used to give readable label for screen readers.

Useful when button/icon has no visible text.

---

# Example

```html
<button aria-label="Close Menu">X</button>
````

Screen reader reads:

```text id="7g2w5m"
Close Menu
```

---

# 2. alt Attribute

Used inside image tag.

Describes image for screen readers.

---

# Example

```html
<img src="logo.png" alt="Company Logo" />
```

If image does not load or user uses screen reader,
`alt` text is used.

---

# 3. Keyboard Navigation

Website should work using keyboard only.

Users should navigate using:

* Tab
* Enter
* Arrow keys

---

# Example

```html
<button>Submit</button>
<a href="/home">Home</a>
```

Buttons and links are keyboard accessible by default.

---

# Bad Example

```html
<div onclick="handleClick()">Click</div>
```

`div` is not keyboard accessible ❌

---

# Good Example

```html
<button>Click</button>
```

Accessible ✅

---

# Important Interview Points

| Feature             | Purpose                   |
| ------------------- | ------------------------- |
| aria-label          | Label for screen readers  |
| alt                 | Image description         |
| Keyboard navigation | Use website without mouse |
| Semantic HTML       | Better accessibility      |

---

# Short Interview Answer

```text id="p6j1qs"
Accessibility means making websites usable for all users including disabled users. 
WCAG provides guidelines for accessibility. 
Important practices include using aria-label, alt attributes, semantic HTML and keyboard navigation.
```

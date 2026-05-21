# Core CSS Fundamentals – Interview Notes

## 1. What is the Difference Between CSS2 and CSS3?

| CSS2                 | CSS3                                          |
| -------------------- | --------------------------------------------- |
| Older version of CSS | Latest advanced version                       |
| Large single file    | Divided into modules                          |
| No animations        | Supports animations and transitions           |
| Limited selectors    | Advanced selectors available                  |
| No Flexbox/Grid      | Supports Flexbox and Grid                     |
| No media queries     | Supports responsive design with media queries |

### Example Features in CSS3

* Flexbox
* Grid
* Animation
* Transition
* Media Queries
* Border Radius
* Box Shadow

---

# 2. Different Ways to Apply CSS

## A) Inline CSS

CSS written directly inside HTML tag using `style` attribute.

### Example

```html
<p style="color:red;">Hello</p>
```

### Advantages

* Quick styling

### Disadvantages

* Not reusable
* Difficult to maintain

---

## B) Internal CSS

CSS written inside `<style>` tag in same HTML file.

### Example

```html
<head>
  <style>
    p{
      color: blue;
    }
  </style>
</head>
```

### Advantages

* Good for single page styling

### Disadvantages

* Not reusable across multiple pages

---

## C) External CSS

CSS written in separate `.css` file.

### Example

### HTML

```html
<link rel="stylesheet" href="style.css">
```

### CSS

```css
p{
  color: green;
}
```

### Advantages

* Reusable
* Clean code
* Easy maintenance

### Disadvantages

* Extra file request

---

# 3. Difference Between Class Selector and ID Selector

| Class Selector             | ID Selector     |
| -------------------------- | --------------- |
| Uses `.`                   | Uses `#`        |
| Can be used multiple times | Used only once  |
| Reusable                   | Unique          |
| Lower priority             | Higher priority |

### Class Example

```css
.box{
  color:red;
}
```

```html
<div class="box"></div>
```

---

### ID Example

```css
#header{
  color:blue;
}
```

```html
<div id="header"></div>
```

---

# 4. Difference Between Margin and Padding

| Margin                            | Padding                      |
| --------------------------------- | ---------------------------- |
| Space outside border              | Space inside border          |
| Creates distance between elements | Creates space inside element |
| Transparent                       | Takes background color       |

### Example

```css
div{
  margin:20px;
  padding:20px;
}
```

### Visual

```text
Margin -> Outside Space
Border
Padding -> Inside Space
Content
```

---

# 5. Difference Between Block, Inline, and Inline-Block Elements

| Block                | Inline                           | Inline-Block                          |
| -------------------- | -------------------------------- | ------------------------------------- |
| Takes full width     | Takes only content width         | Content width but allows height/width |
| Starts new line      | Does not start new line          | Does not start new line               |
| Can set width/height | Cannot set width/height properly | Can set width/height                  |

---

## Block Example

```html
<div>Hello</div>
```

### Common Block Elements

* div
* p
* h1-h6

---

## Inline Example

```html
<span>Hello</span>
```

### Common Inline Elements

* span
* a
* strong

---

## Inline-Block Example

```css
span{
  display:inline-block;
  width:100px;
}
```

---

# 6. Difference Between Relative, Absolute, Fixed, Sticky Positioning

---

## A) Relative Position

Element moves relative to its original position.

### Example

```css
.box{
  position: relative;
  top:20px;
  left:20px;
}
```

### Important

* Original space remains occupied.

---

## B) Absolute Position

Element moves relative to nearest positioned parent.

### Example

```css
.box{
  position:absolute;
  top:0;
  right:0;
}
```

### Important

* Removed from normal document flow.

---

## C) Fixed Position

Element stays fixed on screen even during scrolling.

### Example

```css
.navbar{
  position:fixed;
  top:0;
}
```

### Use Case

* Sticky navbar
* Floating buttons

---

## D) Sticky Position

Element behaves like relative until scroll point is reached, then becomes fixed.

### Example

```css
.header{
  position:sticky;
  top:0;
}
```

### Use Case

* Sticky headers

---

# 7. What is the Default Position Value in CSS?

Default value is:

```css
position: static;
```

### Features

* Normal document flow
* `top`, `left`, `right`, `bottom` do not work

---

# 8. Difference Between `visibility: hidden` and `display: none`

| visibility: hidden   | display: none                 |
| -------------------- | ----------------------------- |
| Element hidden       | Element removed completely    |
| Space remains        | Space removed                 |
| Element still exists | Element not visible in layout |

---

## visibility:hidden Example

```css
.box{
  visibility:hidden;
}
```

### Result

* Element hidden
* Space still occupied

---

## display:none Example

```css
.box{
  display:none;
}
```

### Result

* Element hidden
* Space also removed

---

# Interview Quick Revision

## CSS Position Types

* static → default
* relative → relative to itself
* absolute → relative to parent
* fixed → fixed on screen
* sticky → sticky after scroll

---

## Margin vs Padding

* Margin = outside space
* Padding = inside space

---

## Display Types

* Block → full width
* Inline → content width
* Inline-block → inline + width/height support

---

# Most Asked Interview One-Line Answers

### What is CSS?

CSS is used to style and design HTML elements.

---

### Which CSS is best for large projects?

External CSS because it is reusable and maintainable.

---

### Which selector has higher priority?

ID selector has higher priority than class selector.

---

### What is default position in CSS?

`position: static`

---

### Which property removes element completely?

`display: none`

---

### Which property hides element but keeps space?

`visibility: hidden`


# CSS Box Model & CSS Specificity – Interview Notes

# 2. CSS Box Model (Very Important)

# What is CSS Box Model?

Every HTML element in CSS is treated like a box.

The CSS Box Model contains:

```text id="y55fzh"
-------------------------
|        Margin         |
|  -------------------  |
|  |     Border      |  |
|  |  -------------  |  |
|  |  |  Padding   | |  |
|  |  |  Content   | |  |
|  |  -------------  |  |
|  -------------------  |
-------------------------
```

---

# Parts of Box Model

| Property | Description               |
| -------- | ------------------------- |
| Content  | Actual text/image         |
| Padding  | Space inside border       |
| Border   | Surrounds padding/content |
| Margin   | Space outside border      |

---

# Example

```css id="bhqvow"
div{
  width:200px;
  padding:20px;
  border:5px solid black;
  margin:10px;
}
```

---

# Actual Width Calculation

```text id="r2klr5"
Total Width =
Width + Left Padding + Right Padding +
Left Border + Right Border +
Left Margin + Right Margin
```

### Example

```text id="jl86o5"
200 + 20 + 20 + 5 + 5 + 10 + 10
= 270px
```

---

# What does `box-sizing: border-box` do?

Normally width only applies to content.

But with:

```css id="3sj7cq"
box-sizing:border-box;
```

Padding and border are included inside width.

---

# Without border-box

```css id="tq4nbv"
div{
  width:200px;
  padding:20px;
  border:5px solid black;
}
```

### Actual width becomes:

```text id="5n9h4x"
250px
```

---

# With border-box

```css id="4m9d5c"
div{
  width:200px;
  padding:20px;
  border:5px solid black;
  box-sizing:border-box;
}
```

### Actual width remains:

```text id="yhmll9"
200px
```

---

# Why `border-box` is Important?

### Advantages

* Easy layout management
* Width does not increase unexpectedly
* Mostly used in modern projects

---

# Global Usage

```css id="ajxk7u"
*{
  box-sizing:border-box;
}
```

---

# How to Center a Div Horizontally and Vertically?

# Method 1: Using Flexbox (Most Common)

```css id="6wspru"
.parent{
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
}
```

### Explanation

| Property               | Purpose           |
| ---------------------- | ----------------- |
| justify-content:center | Horizontal center |
| align-items:center     | Vertical center   |

---

# HTML

```html id="i8gzkz"
<div class="parent">
  <div class="child">Hello</div>
</div>
```

---

# Method 2: Using Margin Auto (Horizontal Only)

```css id="tznxja"
div{
  width:200px;
  margin:auto;
}
```

### Important

Works only for horizontal centering.

---

# Method 3: Using Position + Transform

```css id="lj7h7z"
.child{
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
}
```

---

# Why Margin Collapse Happens?

Margin collapse happens when vertical margins of two elements combine into one margin.

---

# Example

```css id="a7ygrh"
.box1{
  margin-bottom:20px;
}

.box2{
  margin-top:30px;
}
```

### Final margin becomes:

```text id="q5t7bf"
30px
```

NOT:

```text id="4kivzx"
50px
```

---

# Why?

CSS combines overlapping vertical margins into single larger margin.

---

# Important Points

✅ Happens only in vertical margins
✅ Horizontal margins never collapse
✅ Larger margin value wins

---

# How to Prevent Margin Collapse?

### Use:

* padding
* border
* overflow:hidden
* display:flex

---

# Example

```css id="kewm7m"
.parent{
  overflow:hidden;
}
```

---

# 3. CSS Specificity & Priority

# What is CSS Specificity?

Specificity decides which CSS rule will apply when multiple rules target same element.

More specific selector gets higher priority.

---

# CSS Priority Order

| Selector                         | Priority |
| -------------------------------- | -------- |
| Inline Style                     | Highest  |
| ID Selector                      | High     |
| Class / Attribute / Pseudo-class | Medium   |
| Element Selector                 | Low      |

---

# Example

```css id="9g9piu"
p{
  color:blue;
}

.text{
  color:green;
}

#title{
  color:red;
}
```

```html id="0a2k3f"
<p id="title" class="text">Hello</p>
```

### Output

```text id="t0dbm3"
Red
```

Because ID selector has higher priority.

---

# Specificity Value

| Selector | Value |
| -------- | ----- |
| Inline   | 1000  |
| ID       | 100   |
| Class    | 10    |
| Element  | 1     |

---

# Example

```css id="vc91gd"
#box{
  color:red;
}
```

Specificity:

```text id="l1gqoz"
100
```

---

# What is the Use of `!important`?

`!important` gives highest priority to a CSS property.

---

# Example

```css id="lmljvu"
p{
  color:red !important;
}
```

Even if another selector has higher specificity, this style will apply.

---

# Important Notes

✅ Overrides normal specificity
✅ Should be avoided in large projects
✅ Makes debugging difficult

---

# How to Override Styles in CSS?

# Method 1: Higher Specificity

```css id="1c2r0w"
#title{
  color:blue;
}
```

Overrides:

```css id="6v5d5u"
p{
  color:red;
}
```

---

# Method 2: Use `!important`

```css id="4zj02l"
p{
  color:green !important;
}
```

---

# Method 3: Write CSS Later

Later CSS overrides earlier CSS if specificity is same.

---

# Example

```css id="3m8b6k"
p{
  color:red;
}

p{
  color:blue;
}
```

### Output

```text id="5i8nm9"
Blue
```

Because last rule wins.

---

# Interview Quick Revision

# Box Model

* Content
* Padding
* Border
* Margin

---

# box-sizing:border-box

Includes padding and border inside width.

---

# Center Div

Best method:

```css id="qv4rnp"
display:flex;
justify-content:center;
align-items:center;
```

---

# Margin Collapse

* Only vertical margins collapse
* Larger margin wins

---

# CSS Specificity Priority

```text id="pjlwm5"
Inline > ID > Class > Element
```

---

# !important

Gives highest priority.

---

# Most Asked Interview One-Line Answers

### What is CSS Box Model?

CSS Box Model defines spacing and structure of HTML elements.

---

### Why use `box-sizing:border-box`?

To include padding and border inside total width.

---

### Best way to center a div?

Using Flexbox.

---

### What is specificity?

Specificity decides which CSS rule applies.

---

### Which selector has highest priority?

Inline CSS.

---

### Why avoid `!important`?

Because it makes CSS difficult to manage and debug.


# Flexbox & CSS Grid – Interview Notes

# 4. Flexbox Interview Questions (Most Asked)

# What is Flexbox?

Flexbox is a one-dimensional layout system in CSS used to align and distribute items efficiently.

It works in:

* Row direction
* Column direction

---

# Why Flexbox is Used?

✅ Easy alignment
✅ Responsive layouts
✅ Space distribution
✅ Centering elements easily

---

# Enable Flexbox

```css id="2t8vhs"
.container{
  display:flex;
}
```

---

# Main Axis & Cross Axis

```text id="l2m1r9"
flex-direction: row

Main Axis  -> Horizontal
Cross Axis -> Vertical
```

---

# Difference Between `justify-content` and `align-items`

| justify-content           | align-items             |
| ------------------------- | ----------------------- |
| Aligns items horizontally | Aligns items vertically |
| Works on main axis        | Works on cross axis     |

---

# Example

```css id="36h9v4"
.container{
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
}
```

---

# `justify-content` Values

```css id="y0p7l7"
justify-content:
flex-start;
center;
flex-end;
space-between;
space-around;
space-evenly;
```

---

# `align-items` Values

```css id="8fr7xq"
align-items:
stretch;
flex-start;
center;
flex-end;
```

---

# What is `flex-direction`?

Defines direction of flex items.

---

# Values of `flex-direction`

| Value          | Meaning            |
| -------------- | ------------------ |
| row            | Horizontal         |
| column         | Vertical           |
| row-reverse    | Reverse horizontal |
| column-reverse | Reverse vertical   |

---

# Example

```css id="7n7j33"
.container{
  display:flex;
  flex-direction:column;
}
```

---

# What is `flex-wrap`?

Controls whether items should wrap into next line.

---

# Without Wrap

```css id="tq5rfx"
.container{
  display:flex;
  flex-wrap:nowrap;
}
```

Items may overflow.

---

# With Wrap

```css id="8s44g5"
.container{
  display:flex;
  flex-wrap:wrap;
}
```

Items move to next line automatically.

---

# Values of `flex-wrap`

| Value        | Meaning               |
| ------------ | --------------------- |
| nowrap       | Default               |
| wrap         | Moves items next line |
| wrap-reverse | Reverse wrapping      |

---

# How to Create Equal Height Columns Using Flexbox?

Flexbox automatically creates equal height columns.

---

# Example

```css id="6v1md6"
.container{
  display:flex;
}

.box{
  flex:1;
}
```

---

# HTML

```html id="8o2x8l"
<div class="container">
  <div class="box">One</div>
  <div class="box">Two</div>
  <div class="box">Three</div>
</div>
```

---

# Difference Between `align-content` and `align-items`

| align-items              | align-content         |
| ------------------------ | --------------------- |
| Aligns single line items | Aligns multiple lines |
| Works on items           | Works on flex lines   |
| Used most frequently     | Used less often       |

---

# Example

```css id="mcotvu"
.container{
  display:flex;
  flex-wrap:wrap;
  align-content:center;
}
```

---

# What is `flex:1`?

`flex:1` means item takes equal available space.

---

# Example

```css id="mk7zt4"
.box{
  flex:1;
}
```

---

# Equivalent To

```css id="3g7wwh"
flex-grow:1;
flex-shrink:1;
flex-basis:0;
```

---

# Example

```css id="ah9h22"
.container{
  display:flex;
}

.box{
  flex:1;
}
```

All boxes become equal width.

---

# Interview Quick Revision (Flexbox)

| Property        | Purpose              |
| --------------- | -------------------- |
| display:flex    | Enable flexbox       |
| justify-content | Horizontal alignment |
| align-items     | Vertical alignment   |
| flex-direction  | Direction            |
| flex-wrap       | Wrapping             |
| flex:1          | Equal space          |

---

# Most Asked One-Line Answers

### What is Flexbox?

Flexbox is a one-dimensional layout system.

---

### Difference between justify-content and align-items?

justify-content works horizontally, align-items works vertically.

---

### What is flex-wrap?

Allows items to move to next line.

---

### What is flex:1?

Makes elements take equal available space.

---

# 5. CSS Grid Interview Questions (MNC Focus)

# Difference Between Flexbox and Grid

| Flexbox                  | Grid                       |
| ------------------------ | -------------------------- |
| One-dimensional          | Two-dimensional            |
| Works in row OR column   | Works in rows AND columns  |
| Better for small layouts | Better for complex layouts |

---

# When to Use?

### Use Flexbox For:

* Navbar
* Buttons
* Small alignment

### Use Grid For:

* Full page layouts
* Dashboard
* Complex responsive design

---

# Enable Grid

```css id="4m1tq8"
.container{
  display:grid;
}
```

---

# What is `grid-template-columns`?

Defines number and size of columns.

---

# Example

```css id="e3n6k5"
.container{
  display:grid;
  grid-template-columns:200px 200px 200px;
}
```

Creates 3 columns.

---

# Using Repeat

```css id="u1d2yo"
grid-template-columns:repeat(3,1fr);
```

---

# What is `fr` Unit in Grid?

`fr` means fraction of available space.

---

# Example

```css id="pnxzyb"
grid-template-columns:1fr 1fr 1fr;
```

Creates 3 equal columns.

---

# Example 2

```css id="pr3shn"
grid-template-columns:1fr 2fr;
```

Second column gets double space.

---

# Explain `grid-area`

Used to define or place grid items in specific area.

---

# Example

```css id="wbp7g5"
.item{
  grid-area:1 / 1 / 3 / 3;
}
```

---

# Meaning

```text id="3r2x3q"
grid-area:
row-start /
column-start /
row-end /
column-end
```

---

# Example Layout

```css id="8zc1yl"
.container{
  display:grid;
  grid-template-columns:repeat(3,1fr);
}
```

---

# How to Create Responsive Layouts Using CSS Grid?

# Method 1: Using `repeat()`

```css id="vs5r7w"
grid-template-columns:repeat(3,1fr);
```

---

# Method 2: Using `auto-fit`

```css id="5j8vcc"
grid-template-columns:
repeat(auto-fit,minmax(200px,1fr));
```

---

# Why This is Powerful?

✅ Automatically responsive
✅ Adjusts columns based on screen size
✅ No media query needed sometimes

---

# Complete Responsive Example

```css id="p8z6nq"
.container{
  display:grid;
  grid-template-columns:
  repeat(auto-fit,minmax(250px,1fr));

  gap:20px;
}
```

---

# Interview Quick Revision (Grid)

| Property              | Purpose           |
| --------------------- | ----------------- |
| display:grid          | Enable grid       |
| grid-template-columns | Create columns    |
| fr                    | Fraction unit     |
| grid-area             | Position items    |
| auto-fit              | Responsive layout |

---

# Flexbox vs Grid Quick Trick

```text id="m9lbxq"
Flexbox = 1D
Grid = 2D
```

---

# Most Asked One-Line Answers

### What is Grid?

Grid is a two-dimensional layout system.

---

### What is fr unit?

Fraction of available space.

---

### Difference between Grid and Flexbox?

Grid works in rows and columns, Flexbox works in one direction.

---

### Best property for responsive grid?

```css id="pdzpd5"
repeat(auto-fit,minmax())
```

---

### What is grid-area?

Used to position grid items inside grid layout.

# Responsive Design & Advanced CSS – Interview Notes

# 6. Responsive Design Questions

# What is Responsive Design?

Responsive design means a website automatically adjusts according to different screen sizes.

Website should work properly on:

* Mobile
* Tablet
* Laptop
* Desktop

---

# Why Responsive Design is Important?

✅ Better user experience
✅ Mobile-friendly website
✅ Important for SEO
✅ Works on all devices

---

# Example

```css id="4x8m9p"
.container{
  width:100%;
}
```

---

# What are Media Queries?

Media queries are used to apply different CSS styles for different screen sizes.

---

# Syntax

```css id="r8m2wq"
@media (max-width:768px){

}
```

---

# Example

```css id="r95t3y"
body{
  background:white;
}

@media (max-width:768px){
  body{
    background:lightblue;
  }
}
```

---

# Meaning

```text id="v3w8ny"
If screen width is 768px or less,
apply these styles.
```

---

# Common Breakpoints Used in Projects

| Device  | Breakpoint |
| ------- | ---------- |
| Mobile  | 480px      |
| Tablet  | 768px      |
| Laptop  | 1024px     |
| Desktop | 1200px+    |

---

# Example

```css id="a3c3xt"
@media (max-width:480px){
}

@media (max-width:768px){
}

@media (max-width:1024px){
}
```

---

# Difference Between em, rem, %, vh, vw

| Unit | Meaning                          |
| ---- | -------------------------------- |
| em   | Relative to parent font size     |
| rem  | Relative to root(html) font size |
| %    | Relative percentage              |
| vh   | Viewport height                  |
| vw   | Viewport width                   |

---

# Example of em

```css id="dd7zqx"
.parent{
  font-size:20px;
}

.child{
  font-size:2em;
}
```

### Result

```text id="8sm0yz"
40px
```

---

# Example of rem

```css id="hskjhh"
html{
  font-size:16px;
}

h1{
  font-size:2rem;
}
```

### Result

```text id="8u5qxu"
32px
```

---

# Example of %

```css id="nbj1w9"
div{
  width:50%;
}
```

Element takes 50% width of parent.

---

# Example of vh & vw

```css id="0k8a9j"
div{
  width:100vw;
  height:100vh;
}
```

---

# Meaning

| Unit  | Meaning            |
| ----- | ------------------ |
| 100vw | Full screen width  |
| 100vh | Full screen height |

---

# Mobile-First vs Desktop-First Approach

| Mobile-First               | Desktop-First              |
| -------------------------- | -------------------------- |
| Design starts from mobile  | Design starts from desktop |
| Uses min-width             | Uses max-width             |
| Better for responsive apps | Traditional approach       |

---

# Mobile-First Example

```css id="p0m71d"
.box{
  width:100%;
}

@media (min-width:768px){
  .box{
    width:50%;
  }
}
```

---

# Desktop-First Example

```css id="8r8rhy"
.box{
  width:50%;
}

@media (max-width:768px){
  .box{
    width:100%;
  }
}
```

---

# Which is Better?

✅ Mobile-first is preferred in modern development.

---

# How to Make an Image Responsive?

# Method 1 (Most Common)

```css id="m3bhw8"
img{
  max-width:100%;
  height:auto;
}
```

---

# Why?

✅ Image never overflows
✅ Adjusts according to screen size

---

# Example

```html id="c6r6mo"
<img src="image.jpg">
```

---

# Interview Quick Revision (Responsive Design)

| Topic             | Key Point                    |
| ----------------- | ---------------------------- |
| Responsive Design | Adjusts to all screens       |
| Media Query       | Different styles for devices |
| rem               | Relative to root             |
| vh/vw             | Viewport units               |
| Mobile-first      | Preferred approach           |

---

# Most Asked One-Line Answers

### What is responsive design?

Design that adapts to different screen sizes.

---

### What are media queries?

Used to apply CSS for specific screen sizes.

---

### Difference between em and rem?

em depends on parent, rem depends on root.

---

### Best way to make image responsive?

```css id="2i8czd"
max-width:100%;
height:auto;
```

---

### Which approach is preferred?

Mobile-first approach.

---

# 7. Advanced CSS Questions

# What are Pseudo-Classes and Pseudo-Elements?

| Pseudo-Class          | Pseudo-Element          |
| --------------------- | ----------------------- |
| Targets element state | Targets part of element |
| Uses `:`              | Uses `::`               |

---

# Examples of Pseudo-Classes

* `:hover`
* `:focus`
* `:nth-child()`

---

# Examples of Pseudo-Elements

* `::before`
* `::after`
* `::first-letter`

---

# `:hover`

Applies style when mouse moves over element.

---

# Example

```css id="0wtxnu"
button:hover{
  background:red;
}
```

---

# `:nth-child()`

Targets specific child element.

---

# Example

```css id="r5x6pd"
li:nth-child(2){
  color:red;
}
```

Targets second list item.

---

# `::before`

Adds content before element.

---

# Example

```css id="gzltwf"
p::before{
  content:"Hello ";
}
```

---

# `::after`

Adds content after element.

---

# Example

```css id="4wq8l8"
p::after{
  content:" 😊";
}
```

---

# What is `z-index`?

`z-index` controls stacking order of elements.

Higher `z-index` appears on top.

---

# Example

```css id="i3mjlwm"
.box1{
  z-index:1;
}

.box2{
  z-index:10;
}
```

`.box2` appears above `.box1`.

---

# When `z-index` Does Not Work?

`z-index` works only when element has:

```css id="u8v5wr"
position:
relative;
absolute;
fixed;
sticky;
```

---

# Example

```css id="lf4x4r"
.box{
  position:relative;
  z-index:10;
}
```

---

# What is Stacking Context?

Stacking context decides how elements stack on top of each other.

Created by:

* z-index
* opacity
* transform
* position

---

# Simple Meaning

```text id="7c5f0h"
Like layers in Photoshop.
```

---

# Example

```css id="m7z0yb"
.parent{
  position:relative;
  z-index:1;
}
```

Creates new stacking context.

---

# What is CSS Inheritance?

Inheritance means child elements inherit some CSS properties from parent.

---

# Common Inherited Properties

* color
* font-size
* font-family
* text-align

---

# Example

```css id="w4rltu"
body{
  color:red;
}
```

All child text becomes red.

---

# Non-Inherited Properties

* margin
* padding
* border

---

# Force Inheritance

```css id="3cokx8"
color:inherit;
```

---

# Interview Quick Revision (Advanced CSS)

| Topic            | Key Point                |
| ---------------- | ------------------------ |
| :hover           | Mouse over state         |
| ::before         | Add content before       |
| z-index          | Layer order              |
| Stacking Context | Controls layering        |
| Inheritance      | Child gets parent styles |

---

# Most Asked One-Line Answers

### What is pseudo-class?

Used to style special state of element.

---

### Difference between pseudo-class and pseudo-element?

Pseudo-class targets state, pseudo-element targets part of element.

---

### What is z-index?

Controls element stacking order.

---

### Why z-index may not work?

Because position property is missing.

---

### What is inheritance?

Child elements inherit styles from parent.

# 8. Real-Time Scenario Based Questions

# How Will You Fix UI Breaking in Different Screen Sizes?

# Common Solutions

✅ Use responsive design
✅ Use Flexbox/Grid
✅ Use media queries
✅ Avoid fixed widths
✅ Use relative units (`%`, `rem`, `vh`, `vw`)
✅ Make images responsive

---

# Example

```css id="d8qlg8"
.container{
  display:flex;
  flex-wrap:wrap;
}
```

---

# Responsive Media Query

```css id="dnlrfx"
@media (max-width:768px){
  .container{
    flex-direction:column;
  }
}
```

---

# Important Tips

❌ Avoid:

```css id="g2m9ho"
width:1200px;
```

✅ Use:

```css id="e4q4j8"
width:100%;
max-width:1200px;
```

---

# How to Make a Sticky Navbar?

Using:

```css id="2hr5u7"
position:sticky;
top:0;
```

---

# Example

```css id="1r7vqs"
.navbar{
  position:sticky;
  top:0;
  background:white;
  z-index:1000;
}
```

---

# Alternative Method

```css id="8w3nlg"
position:fixed;
top:0;
width:100%;
```

---

# Difference

| Sticky                    | Fixed             |
| ------------------------- | ----------------- |
| Sticks after scroll point | Always fixed      |
| Better for sections       | Better for navbar |

---

# How to Create a Dropdown Menu Using Only CSS?

# HTML

```html id="q4xjmt"
<div class="dropdown">
  <button>Menu</button>

  <div class="content">
    <a href="#">Home</a>
    <a href="#">About</a>
  </div>
</div>
```

---

# CSS

```css id="7z7juh"
.content{
  display:none;
}

.dropdown:hover .content{
  display:block;
}
```

---

# Logic

```text id="r1x6y2"
On hover, dropdown becomes visible.
```

---

# How to Create a Modal Popup with CSS?

# HTML

```html id="79e8qb"
<div class="modal">
  Modal Content
</div>
```

---

# CSS

```css id="dk8u38"
.modal{
  position:fixed;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);

  background:white;
  padding:20px;
}
```

---

# Overlay Example

```css id="m3bgxt"
.overlay{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.5);
}
```

---

# How to Create a Loader/Spinner?

# HTML

```html id="11m58j"
<div class="loader"></div>
```

---

# CSS

```css id="fw7h8m"
.loader{
  width:50px;
  height:50px;
  border:5px solid lightgray;
  border-top:5px solid blue;
  border-radius:50%;

  animation:spin 1s linear infinite;
}

@keyframes spin{
  100%{
    transform:rotate(360deg);
  }
}
```

---

# How to Prevent Overflow Issues in Layout?

# Common Solutions

✅ Use:

```css id="p1bpqx"
box-sizing:border-box;
```

---

✅ Avoid fixed widths

---

✅ Use:

```css id="04e0m0"
max-width:100%;
```

---

✅ Add:

```css id="7rk9ul"
overflow:hidden;
```

OR

```css id="p2ru9f"
overflow:auto;
```

---

# Example

```css id="rzmw0k"
img{
  max-width:100%;
}
```

---

# How to Handle Long Text in UI?

# Using Ellipsis

```css id="4tiz8u"
.text{
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}
```

---

# Result

```text id="qnlaj4"
This is very long te...
```

---

# Using `word-break`

```css id="9xldjp"
.text{
  word-break:break-word;
}
```

---

# Why?

Long words automatically break instead of overflowing.

---

# Interview Quick Revision (Scenario Based)

| Problem       | Solution                  |
| ------------- | ------------------------- |
| UI Breaking   | Media queries + Flex/Grid |
| Sticky Navbar | position:sticky           |
| Dropdown      | :hover                    |
| Loader        | animation                 |
| Overflow      | max-width + overflow      |
| Long Text     | ellipsis                  |

---

# Most Asked One-Line Answers

### Best way to fix responsive issues?

Use Flexbox/Grid with media queries.

---

### How to make navbar sticky?

```css id="h96f1j"
position:sticky;
top:0;
```

---

### How to handle long text?

Use `text-overflow:ellipsis`.

---

### How to prevent overflow?

Use `max-width:100%`.

---

# 9. CSS Performance & Best Practices

# Best Practices for Writing CSS in Large Projects

# Common Best Practices

✅ Use external CSS
✅ Follow naming convention
✅ Reuse classes
✅ Avoid inline CSS
✅ Keep CSS modular
✅ Use variables
✅ Write responsive CSS
✅ Avoid deep nesting

---

# Folder Structure Example

```text id="lzb8uo"
css/
 ├── main.css
 ├── layout.css
 ├── components.css
 ├── responsive.css
```

---

# How to Avoid Duplicated CSS?

# Bad Example

```css id="zwg9g7"
.button1{
  padding:10px;
}

.button2{
  padding:10px;
}
```

---

# Good Example

```css id="x9m0p6"
.btn{
  padding:10px;
}
```

Reuse same class.

---

# Use Variables

```css id="3g9dvu"
:root{
  --primary-color:blue;
}
```

---

# What is BEM Naming Convention?

BEM =

```text id="f0mjlwm"
Block__Element--Modifier
```

---

# Example

```css id="2x7c8i"
.card__title--active{
  color:red;
}
```

---

# Meaning

| Part     | Meaning               |
| -------- | --------------------- |
| Block    | Main component        |
| Element  | Child element         |
| Modifier | Different state/style |

---

# Example

```html id="zjlwmm"
<div class="card">
  <h2 class="card__title"></h2>
</div>
```

---

# Advantages of BEM

✅ Clean CSS
✅ Reusable
✅ Easy maintenance
✅ Avoids conflicts

---

# Difference Between SCSS and CSS

| CSS                     | SCSS               |
| ----------------------- | ------------------ |
| Normal styling language | CSS preprocessor   |
| No variables            | Supports variables |
| No nesting              | Supports nesting   |
| No mixins               | Supports mixins    |

---

# SCSS Example

```scss id="2g1j6d"
$primary:red;

.button{
  color:$primary;

  &:hover{
    color:blue;
  }
}
```

---

# CSS Output

```css id="5bgxhf"
.button{
  color:red;
}

.button:hover{
  color:blue;
}
```

---

# How to Optimize CSS for Performance?

# Best Practices

✅ Minify CSS
✅ Remove unused CSS
✅ Avoid heavy selectors
✅ Use reusable classes
✅ Avoid too much nesting
✅ Use efficient selectors

---

# Bad Selector

```css id="5z6k0q"
div ul li a span{
}
```

---

# Better Selector

```css id="b0qahv"
.menu-text{
}
```

---

# Interview Quick Revision (Performance)

| Topic        | Key Point           |
| ------------ | ------------------- |
| BEM          | Naming convention   |
| SCSS         | Advanced CSS        |
| Reusable CSS | Avoid duplication   |
| Minify CSS   | Improve performance |

---

# Most Asked One-Line Answers

### What is BEM?

A CSS naming convention.

---

### Difference between SCSS and CSS?

SCSS supports variables, nesting, mixins.

---

### How to optimize CSS?

Minify and remove unused CSS.

---

# 10. Modern CSS Features

# What are CSS Variables?

CSS variables store reusable values.

---

# Syntax

```css id="xjlwm9"
:root{
  --primary-color:blue;
}
```

---

# Usage

```css id="1j2h8x"
button{
  background:var(--primary-color);
}
```

---

# Advantages

✅ Reusable
✅ Easy theme changes
✅ Cleaner code

---

# What is `calc()` Function?

`calc()` performs calculations in CSS.

---

# Example

```css id="zhhktl"
width:calc(100% - 100px);
```

---

# Meaning

```text id="3yjjlwm"
Full width minus 100px
```

---

# Another Example

```css id="e1yb8i"
height:calc(100vh - 60px);
```

---

# What is `clamp()` Used For?

`clamp()` sets responsive values with:

* minimum
* preferred
* maximum

---

# Syntax

```css id="1t1tkw"
font-size:clamp(16px,5vw,40px);
```

---

# Meaning

```text id="6kgqvl"
Minimum = 16px
Preferred = 5vw
Maximum = 40px
```

---

# Why `clamp()` is Powerful?

✅ Responsive typography
✅ Reduces media queries
✅ Better responsive design

---

# Difference Between `min-width` and `max-width`

| min-width             | max-width             |
| --------------------- | --------------------- |
| Minimum allowed width | Maximum allowed width |
| Used in mobile-first  | Used in desktop-first |

---

# Example

```css id="q0f55n"
@media (min-width:768px){
}
```

Means:

```text id="3l7rze"
768px and above
```

---

# Example

```css id="tx1yo9"
@media (max-width:768px){
}
```

Means:

```text id="w5w2g8"
768px and below
```

---

# What are CSS Custom Properties?

CSS custom properties are another name for CSS variables.

---

# Example

```css id="5rjlwm"
:root{
  --font-size:20px;
}
```

---

# Usage

```css id="a8wsc9"
h1{
  font-size:var(--font-size);
}
```

---

# Interview Quick Revision (Modern CSS)

| Feature   | Purpose           |
| --------- | ----------------- |
| Variables | Reusable values   |
| calc()    | CSS calculations  |
| clamp()   | Responsive values |
| min-width | Mobile-first      |
| max-width | Desktop-first     |

---

# Most Asked One-Line Answers

### What are CSS variables?

Reusable values stored in variables.

---

### What does calc() do?

Performs calculations in CSS.

---

### Why use clamp()?

For responsive sizing.

---

### Difference between min-width and max-width?

min-width = above size, max-width = below size.

---

### What are CSS custom properties?

Another name for CSS variables.

# 11. Common MNC Level Questions

# Difference Between Absolute and Fixed Positioning

| Absolute                                         | Fixed                                 |
| ------------------------------------------------ | ------------------------------------- |
| Positioned relative to nearest positioned parent | Positioned relative to browser window |
| Moves during scrolling                           | Stays fixed during scrolling          |
| Removed from normal flow                         | Removed from normal flow              |

---

# Absolute Example

```css id="blsqcn"
.box{
  position:absolute;
  top:20px;
  left:20px;
}
```

---

# Fixed Example

```css id="ywr7nl"
.navbar{
  position:fixed;
  top:0;
  width:100%;
}
```

---

# Simple Trick

```text id="svu65p"
Absolute = Parent based
Fixed = Screen based
```

---

# How Does Browser Render CSS?

# Rendering Process

```text id="pn6a91"
1. Browser reads HTML
2. Creates DOM
3. Reads CSS
4. Creates CSSOM
5. Combines DOM + CSSOM
6. Creates Render Tree
7. Layout Calculation
8. Painting
9. Display on screen
```

---

# Important Terms

| Term        | Meaning                 |
| ----------- | ----------------------- |
| DOM         | HTML structure          |
| CSSOM       | CSS structure           |
| Render Tree | Final visible structure |

---

# Simple Flow

```text id="hn8ikm"
HTML → DOM
CSS → CSSOM
DOM + CSSOM → Render Tree
```

---

# What is Critical CSS?

Critical CSS is the minimum CSS required to render visible content quickly.

---

# Why Important?

✅ Faster page loading
✅ Better performance
✅ Better user experience

---

# Example

Above-the-fold CSS loads first.

---

# Non-Critical CSS

Loaded later using:

```html id="mjlwmn"
<link rel="preload">
```

OR async techniques.

---

# How to Support Old Browsers in CSS?

# Common Methods

✅ Use vendor prefixes
✅ Avoid unsupported properties
✅ Use fallbacks
✅ Use autoprefixer
✅ Check browser compatibility

---

# Vendor Prefix Example

```css id="w9t9rk"
.box{
  -webkit-transform:rotate(45deg);
  transform:rotate(45deg);
}
```

---

# Fallback Example

```css id="ecazig"
background:#000;
background:rgba(0,0,0,0.5);
```

---

# Browser Compatibility Website

Commonly used:

```text id="4jlwm8"
Can I Use
```

---

# How to Debug CSS Issues?

# Common Debugging Steps

✅ Use browser DevTools
✅ Inspect element
✅ Check specificity
✅ Check overflow
✅ Verify media queries
✅ Check positioning
✅ Use temporary borders

---

# Temporary Border Trick

```css id="plrd6w"
*{
  border:1px solid red;
}
```

Helps identify layout issues.

---

# Important DevTools Tabs

| Tool     | Purpose              |
| -------- | -------------------- |
| Elements | Inspect HTML/CSS     |
| Computed | Final applied styles |
| Console  | Errors               |
| Network  | CSS loading          |

---

# Common CSS Problems

| Problem                 | Reason            |
| ----------------------- | ----------------- |
| z-index not working     | Missing position  |
| Overflow issue          | Fixed width       |
| Media query not working | Wrong breakpoint  |
| CSS not applying        | Specificity issue |

---

# Interview Quick Revision (MNC Questions)

| Topic               | Key Point             |
| ------------------- | --------------------- |
| Absolute            | Parent based          |
| Fixed               | Screen based          |
| Critical CSS        | Important visible CSS |
| Old Browser Support | Prefixes + fallbacks  |
| Debugging           | DevTools              |

---

# Most Asked One-Line Answers

### Difference between absolute and fixed?

Absolute is parent-based, fixed is screen-based.

---

### What is Critical CSS?

Minimum CSS needed for visible content.

---

### Best way to debug CSS?

Using browser DevTools.

---

### How to support old browsers?

Use prefixes and fallbacks.

---

# 12. Practical Coding Questions Asked in Interviews

# Q1: Center a Div

# Using Flexbox (Most Common)

```css id="2w2d8n"
.container{
  display:flex;
  justify-content:center;
  align-items:center;
}
```

---

# Explanation

| Property               | Purpose           |
| ---------------------- | ----------------- |
| display:flex           | Enable flexbox    |
| justify-content:center | Horizontal center |
| align-items:center     | Vertical center   |

---

# Full Height Center

```css id="9yfq1e"
.container{
  height:100vh;
}
```

---

# Q2: Responsive Grid Layout

# Code

```css id="uxsvs4"
.grid{
  display:grid;

  grid-template-columns:
  repeat(auto-fit,minmax(200px,1fr));

  gap:20px;
}
```

---

# Explanation

| Property     | Purpose                |
| ------------ | ---------------------- |
| display:grid | Enable grid            |
| auto-fit     | Responsive columns     |
| minmax()     | Minimum & maximum size |
| 1fr          | Equal space            |

---

# Why Important?

✅ Automatically responsive
✅ No extra media query sometimes
✅ Common MNC question

---

# Q3: Text Ellipsis

# Code

```css id="ljlwm0"
.text{
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}
```

---

# Result

```text id="5fjlwm"
This is a very long te...
```

---

# Why Use?

✅ Prevents UI breaking
✅ Common in cards/tables
✅ Handles long text properly

---

# Important Properties

| Property               | Purpose            |
| ---------------------- | ------------------ |
| white-space:nowrap     | Single line        |
| overflow:hidden        | Hide extra content |
| text-overflow:ellipsis | Add ...            |

---

# Bonus: Most Asked CSS Topics for 2–4 Years Experience

# 1. Flexbox

Must Know:

* justify-content
* align-items
* flex-wrap
* flex:1
* flex-direction

---

# 2. Grid

Must Know:

* grid-template-columns
* auto-fit
* minmax()
* grid-area

---

# 3. Responsive UI

Must Know:

* Media queries
* Mobile-first
* rem/vh/vw
* Responsive images

---

# 4. Specificity

Must Know:

* Inline > ID > Class > Element
* !important
* CSS overriding

---

# 5. Positioning

Must Know:

* relative
* absolute
* fixed
* sticky

---

# 6. Real-Time Debugging

Must Know:

* DevTools
* Overflow fixing
* z-index issue
* Responsive debugging

---

# 7. SCSS

Must Know:

* Variables
* Nesting
* Mixins

---

# 8. Component-Based CSS

Mostly used in:

* React
* Angular
* Vue

---

# Common Approaches

* CSS Modules
* Styled Components
* Tailwind CSS
* SCSS

---

# Interview Quick Final Revision

```text id="rxz5y0"
Flexbox = 1D Layout
Grid = 2D Layout
```

---

```text id="wlr86f"
Specificity:
Inline > ID > Class > Element
```

---

```text id="w1cjlwm"
Responsive Image:
max-width:100%;
height:auto;
```

---

```text id="ekjlwm"
Sticky Navbar:
position:sticky;
top:0;
```

---

```text id="ukjlwm"
Ellipsis:
white-space:nowrap;
overflow:hidden;
text-overflow:ellipsis;
```

---

# Final Most Asked Interview Questions

### Difference between Grid and Flexbox?

Grid is 2D, Flexbox is 1D.

---

### Why z-index not working?

Position property missing.

---

### Best layout system today?

Flexbox + Grid together.

---

### Best debugging tool for CSS?

Browser DevTools.

---

### Best responsive approach?

Mobile-first design.

# Complete CSS Position, Selectors & Pseudo Classes Notes (Interview Notes)

# 1. CSS Position Properties (Complete)

# What is Position in CSS?

`position` property controls how an element is placed in webpage.

---

# Types of Position

| Position | Meaning                    |
| -------- | -------------------------- |
| static   | Default position           |
| relative | Relative to itself         |
| absolute | Relative to parent         |
| fixed    | Relative to browser window |
| sticky   | Sticky during scroll       |

---

# A) position: static

Default position of every element.

---

# Features

✅ Normal document flow
❌ top/left/right/bottom do not work

---

# Example

```css id="v9a2pq"
.box{
  position:static;
}
```

---

# B) position: relative

Moves element relative to its original position.

---

# Features

✅ Original space remains
✅ Can use top/left/right/bottom

---

# Example

```css id="gh9fx0"
.box{
  position:relative;
  top:20px;
  left:20px;
}
```

---

# C) position: absolute

Moves element relative to nearest positioned parent.

---

# Features

✅ Removed from normal flow
✅ Searches nearest parent having:

* relative
* absolute
* fixed
* sticky

---

# Example

```css id="jlwm2m"
.parent{
  position:relative;
}

.child{
  position:absolute;
  top:0;
  right:0;
}
```

---

# D) position: fixed

Element stays fixed on screen.

---

# Features

✅ Does not move on scroll
✅ Mostly used for navbar/chat button

---

# Example

```css id="93xrm8"
.navbar{
  position:fixed;
  top:0;
  width:100%;
}
```

---

# E) position: sticky

Behaves like relative until scroll point reached.

---

# Example

```css id="w7wl4m"
.header{
  position:sticky;
  top:0;
}
```

---

# Difference Between Relative & Absolute

| Relative             | Absolute               |
| -------------------- | ---------------------- |
| Keeps original space | Removes original space |
| Relative to itself   | Relative to parent     |

---

# Difference Between Absolute & Fixed

| Absolute          | Fixed           |
| ----------------- | --------------- |
| Parent based      | Screen based    |
| Scrolls with page | Does not scroll |

---

# Difference Between Fixed & Sticky

| Fixed              | Sticky                    |
| ------------------ | ------------------------- |
| Always fixed       | Fixed after scroll point  |
| Relative to screen | Relative + fixed behavior |

---

# Important Position Properties

| Property | Purpose       |
| -------- | ------------- |
| top      | Move downward |
| left     | Move right    |
| right    | Move left     |
| bottom   | Move upward   |
| z-index  | Layer order   |

---

# Example

```css id="jlwm2z"
.box{
  position:absolute;
  top:10px;
  left:20px;
}
```

---

# 2. CSS Selectors (Complete)

# What is Selector?

Selector targets HTML elements for styling.

---

# Types of Selectors

| Selector         | Symbol |
| ---------------- | ------ |
| Universal        | *      |
| Element          | p, h1  |
| Class            | .      |
| ID               | #      |
| Group            | ,      |
| Descendant       | space  |
| Child            | >      |
| Adjacent Sibling | +      |
| General Sibling  | ~      |
| Attribute        | []     |

---

# A) Universal Selector

Targets all elements.

```css id="jlwm8a"
*{
  margin:0;
}
```

---

# B) Element Selector

Targets specific tag.

```css id="jlwm4h"
p{
  color:red;
}
```

---

# C) Class Selector

Reusable selector.

```css id="jlwm5n"
.box{
  color:blue;
}
```

---

# HTML

```html id="jlwm1c"
<div class="box"></div>
```

---

# D) ID Selector

Unique selector.

```css id="jlwm5t"
#header{
  color:green;
}
```

---

# HTML

```html id="jlwm9p"
<div id="header"></div>
```

---

# Difference Between Class & ID

| Class          | ID              |
| -------------- | --------------- |
| Reusable       | Unique          |
| Uses .         | Uses #          |
| Lower priority | Higher priority |

---

# E) Group Selector

Apply same style to multiple elements.

```css id="jlwm1y"
h1,p,div{
  color:red;
}
```

---

# F) Descendant Selector

Targets child inside parent.

```css id="jlwm0v"
div p{
  color:red;
}
```

---

# G) Child Selector (>)

Targets direct child only.

```css id="jlwm2u"
div > p{
  color:blue;
}
```

---

# H) Adjacent Sibling Selector (+)

Targets immediate next sibling.

```css id="jlwm8q"
h1 + p{
  color:red;
}
```

---

# I) General Sibling Selector (~)

Targets all next siblings.

```css id="jlwm3r"
h1 ~ p{
  color:green;
}
```

---

# J) Attribute Selector

Targets element based on attribute.

```css id="jlwm9x"
input[type="text"]{
  border:1px solid black;
}
```

---

# 3. Pseudo Classes (Very Important)

# What is Pseudo Class?

Pseudo-class styles special state of element.

Uses:

```css id="jlwm0k"
:
```

---

# Common Pseudo Classes

| Pseudo Class | Purpose          |
| ------------ | ---------------- |
| :hover       | Mouse over       |
| :focus       | Input focus      |
| :active      | Click state      |
| :visited     | Visited link     |
| :first-child | First child      |
| :last-child  | Last child       |
| :nth-child() | Specific child   |
| :not()       | Exclude element  |
| :checked     | Checked checkbox |
| :disabled    | Disabled element |
| :empty       | Empty element    |

---

# A) :hover

```css id="jlwm4m"
button:hover{
  background:red;
}
```

---

# B) :focus

```css id="jlwm8v"
input:focus{
  border:2px solid blue;
}
```

---

# C) :active

```css id="jlwm6e"
button:active{
  transform:scale(0.9);
}
```

---

# D) :visited

```css id="jlwm4d"
a:visited{
  color:purple;
}
```

---

# E) :first-child

```css id="jlwm7w"
li:first-child{
  color:red;
}
```

---

# F) :last-child

```css id="jlwm3j"
li:last-child{
  color:blue;
}
```

---

# G) :nth-child()

```css id="jlwm5g"
li:nth-child(2){
  color:green;
}
```

---

# Even/Odd Example

```css id="jlwm9l"
li:nth-child(even){
  background:gray;
}
```

---

# H) :not()

```css id="jlwm0r"
p:not(.active){
  color:red;
}
```

---

# I) :checked

```css id="jlwm7t"
input:checked{
  accent-color:red;
}
```

---

# J) :disabled

```css id="jlwm6y"
button:disabled{
  opacity:0.5;
}
```

---

# K) :empty

```css id="jlwm8s"
div:empty{
  display:none;
}
```

---

# 4. Pseudo Elements

# What is Pseudo Element?

Targets part of element.

Uses:

```css id="jlwm3a"
::
```

---

# Common Pseudo Elements

| Pseudo Element | Purpose            |
| -------------- | ------------------ |
| ::before       | Add content before |
| ::after        | Add content after  |
| ::first-letter | First letter       |
| ::first-line   | First line         |
| ::selection    | Selected text      |
| ::placeholder  | Placeholder text   |

---

# A) ::before

```css id="jlwm5q"
p::before{
  content:"🔥 ";
}
```

---

# B) ::after

```css id="jlwm2l"
p::after{
  content:" 😊";
}
```

---

# C) ::first-letter

```css id="jlwm7h"
p::first-letter{
  font-size:40px;
}
```

---

# D) ::first-line

```css id="jlwm1m"
p::first-line{
  color:red;
}
```

---

# E) ::selection

```css id="jlwm0z"
::selection{
  background:yellow;
}
```

---

# F) ::placeholder

```css id="jlwm6n"
input::placeholder{
  color:gray;
}
```

---

# 5. CSS Specificity (Important)

# Priority Order

```text id="jlwm4u"
Inline > ID > Class > Element
```

---

# Specificity Values

| Selector | Value |
| -------- | ----- |
| Inline   | 1000  |
| ID       | 100   |
| Class    | 10    |
| Element  | 1     |

---

# Example

```css id="jlwm3f"
#title{
  color:red;
}
```

Wins over:

```css id="jlwm8i"
p{
  color:blue;
}
```

---

# 6. z-index

# What is z-index?

Controls layer order.

Higher value appears above.

---

# Example

```css id="jlwm9v"
.box{
  position:relative;
  z-index:10;
}
```

---

# Why z-index Not Working?

Because:
❌ position missing

Must use:

* relative
* absolute
* fixed
* sticky

---

# 7. Overflow Properties

| Property | Meaning          |
| -------- | ---------------- |
| hidden   | Hide overflow    |
| auto     | Scroll if needed |
| scroll   | Always scroll    |
| visible  | Default          |

---

# Example

```css id="jlwm7p"
.box{
  overflow:auto;
}
```

---

# 8. Display Properties

| Display      | Meaning               |
| ------------ | --------------------- |
| block        | Full width            |
| inline       | Content width         |
| inline-block | Inline + width/height |
| none         | Hide element          |
| flex         | Flexbox               |
| grid         | Grid layout           |

---

# 9. Visibility vs Display None

| visibility:hidden       | display:none       |
| ----------------------- | ------------------ |
| Hidden but space exists | Completely removed |

---

# 10. Important Interview Quick Notes

# Flexbox Center

```css id="jlwm2b"
display:flex;
justify-content:center;
align-items:center;
```

---

# Responsive Image

```css id="jlwm5v"
img{
  max-width:100%;
  height:auto;
}
```

---

# Text Ellipsis

```css id="jlwm8b"
.text{
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}
```

---

# Sticky Navbar

```css id="jlwm4p"
.navbar{
  position:sticky;
  top:0;
}
```

---

# Global Box Sizing

```css id="jlwm9n"
*{
  box-sizing:border-box;
}
```

---

# CSS Variables

```css id="jlwm6w"
:root{
  --primary-color:blue;
}
```

---

# Use Variable

```css id="jlwm1q"
button{
  color:var(--primary-color);
}
```

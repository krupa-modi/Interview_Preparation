# How does addEventListener Work?

## Answer

`addEventListener()` is a JavaScript method used to attach an event handler to an HTML element. It allows the browser to listen for specific events such as clicks, key presses, mouse movements, or form submissions.

### Syntax

```javascript
element.addEventListener(event, callback);
```

### Example

```javascript
const button = document.getElementById("btn");

button.addEventListener("click", () => {
  console.log("Button clicked");
});
```

When the button is clicked, the callback function executes.

### Common Events

```javascript
click
submit
change
keydown
keyup
mouseover
mouseout
```

### Advantages over onclick

```javascript
button.addEventListener("click", firstFunction);
button.addEventListener("click", secondFunction);
```

Multiple event listeners can be attached to the same element, whereas `onclick` can only hold one function at a time.

### Event Object

```javascript
button.addEventListener("click", (event) => {
  console.log(event.target);
});
```

The event object provides information about the event, such as the target element, mouse position, and keyboard key pressed.

### Event Bubbling

```javascript
child.addEventListener("click", () => {
  console.log("Child clicked");
});

parent.addEventListener("click", () => {
  console.log("Parent clicked");
});
```

Clicking the child element triggers both child and parent listeners because events bubble up through the DOM.

### Interview Summary

"`addEventListener()` is used to attach event handlers to DOM elements. It listens for specific events such as clicks or key presses and executes a callback function when the event occurs. It supports multiple listeners, event bubbling, and access to the event object."


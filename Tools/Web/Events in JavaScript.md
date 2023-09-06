Event listener:
```html
<button id ="btn">Click me</button>
```
```javascript
const btn = document.querySelector('#btn');
btn.addEventListener('click', () => {
	alert("Hello world");
}); //anonymous function can be changed for named function
```
Listeners are attached to [[Document Object Model]] nodes.

Listener for group of buttons:

```html
<div id="container">
    <button id="1">Click Me</button>
    <button id="2">Click Me</button>
    <button id="3">Click Me</button>
</div>
```
```javascript
// buttons is a node list. It looks and acts much like an array.
const buttons = document.querySelectorAll('button');

// we use the .forEach method to iterate through each button
buttons.forEach((button) => {

  // and for each one we add a 'click' listener
  button.addEventListener('click', () => {
    alert(button.id);
  });
});
```

More events:
https://www.w3schools.com/jsref/dom_obj_event.asp

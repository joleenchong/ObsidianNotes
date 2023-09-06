A tree-like representation of the webpage's contents. Think of a binary tree, where each element is a child of another node.
```html
<div id="container">
  <div class="display"></div>
  <div class="controls"></div>
</div>
```
`display` and `controls` are children of `container`.

Query selectors for targeting DOM elements:
```javascript
element.querySelector(selector); //returns a reference to the first match of selector

element.querySelectorAll(selectors); //returns nodelist of references to all matches of selectors

const container = document.querySelector('#container');
// selects the #container div

console.dir(container.firstElementChild);                      
// selects the first child of #container => .display

const controls = document.querySelector('.controls');   
// selects the .controls div

console.dir(controls.previousElementSibling);                  
// selects the prior sibling => .display
```

Element creation:
```javascript
//document.createElement(tagName, [optional parameters])
const div = document.createElement('div');
```
- does not put the new element into the DOM -> manipulate the element before placing on the page

Append element to DOM:
```javascript
parentNode.appendChild(childNode);
//appends child node as last child of parentNode

parentNode.insertBefore(newNode, referenceNode);
//inserts new node into parentNode before referenceNode

```

Remove element from DOM:
```javascript
parentNode.removeChild(child); 
//returns reference to child after removing it
```

Altering elements:
```javascript
div.style.color = 'blue';
div.style.cssText = 'color: blue; background: white;'
div.setAttribute('style', 'color: blue; background: white;')
```

Editing attributes:
```javascript
div.setAttribute('id', 'theDiv');
//if id exists, update it to theDiv, else create an id with value theDiv

div.getAttribute('id');
//returns value of specified attribute

div.removeAttribute('id');
```

Working with classes:
```javascript
div.classList.add('new');
div.classList.remove('new');
div.classList.toggle('active');
//if div doesn't have active, add it, otherwise remove it
```

Adding text content:
```javascript
div.textContent = 'Hello World' //creates text node and inserts it into div
```

Adding HTML content:
```javascript
div.innerHTML = '<span>Hello World</span>'; //renders HTML inside div
```
Note: can lead to [[Cross-site scripting attack (XSS)]]. Use `textContent` instead.

This only changes the DOM, not the HTML. The DOM is what's being rendered by the HTML.


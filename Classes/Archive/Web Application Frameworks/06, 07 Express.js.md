A runtime environment for executing JavaScript code. Used for the backend.

Applications:
- Real-time client side web apps

Uses [[REST API]].

Installation:
- install LTS of Node.js from website
- create project folder and use `npm init -yes` to init `package.json` to store project metadata
- install express using `npm i express`
- optional: install nodemon with `npm i -g nodemon` to automatically restart app when files changes

Building web server:
```javascript
//loads express module, require() returns a function named 'express'
const express = require('express');
//express() returns an object of type express
const app = express();

//args - path, callback function / route parameters
//'/' is path, (request, resource) is callback function
app.get('/', (request, resource) => {
	resource.send(req.params.someField)); 
});

app.listen(3000, () => console.log('Listening to port 3000'));
```
To run:
```bash
node app.js
nodemon app.js
```
- visit localhost:{port number} to see

Route parameters:
- named URL segments to capture values specified at URL position
	- e.g. in `https://domain/posts/1`, `/posts/:postID` is the route path
	- values are rendered in `req.params` object in key-pair
		- `req.params`: {"postID":"1"}

Views are defined in a HTML file using:
```html
<h1>Thing<h1>
<input type="text" id="" name="thingName" placeHolder="Enter thing">
<button type="submit">Button text</button>
```
```javascript
app.get('/', (request, resource) => {
	resource.sendFile(_dirname + '/thing.html');
})
```

Middleware functions:
- have access to request object, response object, & next middleware function in app's req-res cycle
- can do:
	- execute any code
	- make changes to req & res objects
	- end req-res cycle
	- call next middleware function to stack
- called sequentially, with last function sending response back to browser
- useful mid functions to consider:
```javascript
// helmet - secures express apps by setting various HTTP headers
const helmet = require('helmet');
app.use(helmet());

// morgan - logs HTTP req in terminal
const morgan = require('morgan');
app.use(morgan('tiny'))

// coonect-timeout - sets a timeout period for HTTP req processing
const timeout = require('connect-timeout')
```

Template engines:
- allows using static template files in app
- replaces variables in a template file with actual values at runtime
- in pug, defined with YAML

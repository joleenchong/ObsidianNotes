Alert:
```html
<div class="alert alert-primary" role="alert"> Primary alert </div>

<div class="alert alert-secondary" role="alert"> Secondary alert </div>

<div class="alert alert-success" role="alert"> Success alert </div>

<div class="alert alert-danger" role="alert"> Danger alert </div>

<div class="alert alert-warning" role="alert"> Warning alert </div>
```
- Dismissable alerts with links
```html
<div class="alert alert-warning alert-dismissible fade show" role="alert">
Primary alert - click <a href="#" class="alert-link">here</a> for more information
	<button type="button" class="close" data-dismiss="alert" aria-label="Close">
		<span aria-hidden="true">&times;</span>
	</button>
</div>
```

Breadcrumb:
```html
<nav aria-label="breadcrumb">
	<ol class="breadcrumb">
		<li class="breadcrumb-item"><a href="#">Home</a></li>
		<li class="breadcrumb-item"><a href="#">Blog</a></li>
		<li class="breadcrumb-item active">Frameworks</li>
	</ol>
</nav>
```

Buttons:
```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-info">Info</button>
```
- to control sizing:
```html
<button type="button" class="btn btn-primary btn-lg">Large button</button>
<button type="button" class="btn btn-primary btn-sm">Small button</button>
<button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button>
```
- states:
```html
<a href="#" class="btn btn-primary btn-lg active" role="button" aria-pressed="true">Pressed Button</a>

<button type="button" class="btn btn-lg btn-primary" disabled>Primary button</button>
<a href="#" class="btn btn-primary btn-lg disabled" tabindex="-1" role="button" aria-disabled="true">Primary link</a>
<!-- tabindex='-1' prevents <a> elements from receiving keyboard focus -->
```
- groups:
```html
<div class="btn-group" role="group">
	<button type="button" class="btn btn-secondary">Left</button>
	<button type="button" class="btn btn-secondary">Middle</button>
	<button type="button" class="btn btn-secondary">Right</button>
</div>
<!-- Using with other attributes -->
<div class="btn-group btn-group-lg" role="group">...</div>
<div class="btn-group" role="group">...</div>
<div class="btn-group btn-group-sm" role="group">...</div>
<!-- Making button groups appear vertically -->
<div class="btn-group-vertical">
...
</div>
```

Collapsible areas:
```html
<p>
	<a class="btn btn-primary" data-bs-toggle="collapse" href="#collapseExample"
role="button" aria-expanded="false">Link with href</a>
</p>

<div class="collapse" id="collapseExample">
	<div class="card card-body">
	Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
	</div>
</div>
```

Forms:
```html
<input type="value">
<!-- Common types: email, password, number, date -->
<form>
	<div class="form-group">
		<label for="">Text area</label>
```
- honestly might need its own page


Bootstrap is a framework for building responsive website interfaces.

To use:
- include stylesheet in `<head>` block:
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```
- include JavaScript lib in `<body>` block:
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
```

Components:
- Layout - organising components and data on page
- Contents - presenting data
- Forms - styling and structure for forms to receive user input
- Components - blocks that provide integral part of page & functionality
- Helpers and utilities

Bootstrap uses a grid system to store containers, rows, and columns for layouts. Containers are used to centre and horizontally pad website's content. Rows are wrappers for columns -> content is placed inside columns and only columns may be immediate children of rows.
- Breakpoints for viewport width:
	- xs - <576px
	- s - =>576px
	- m - =>768px
	- l - =>992px
	- xl - =>1200px
- 15px of padding is applied to each side of column by default
- each row is 12 units in width

[[Bootstrap UI components]]

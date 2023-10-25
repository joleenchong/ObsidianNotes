REST (REpresentational State Transfer) - an architecture where clients connect to Web servers using Resources.

Resource - any object a server can provide info about
- each one has unique identifier

When a RESTful API is called, the server will transfer a representation of the state of the requested resource to the client.

Requests:
- HTTP GET - retrieves resource representation / info only
	- when resource found, return HTTP response code 200 (OK) along with response body (XML/JSON)
	- when not found, return HTTP response code 404 (NOT FOUND)
- HTTP POST - creates new resource into resource collection
```HTTP
POST /student HTTP/1.1
Host: curtin.edu.au Accept: application/json
Content-Type: application/json
Content-Length: 81
{
	"Id": 20920942
	"Name": "Honker Bonkers",
	"Address": "Perth",
}
```
- HTTP PUT - update existing resource (if doesn't exist, API can either make new resource or not)
- HTTP DELETE - deletes resources
- HTTP PATCH - updates specific item in resource (does not create new resource if resource don't exist)

Documentation:
https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
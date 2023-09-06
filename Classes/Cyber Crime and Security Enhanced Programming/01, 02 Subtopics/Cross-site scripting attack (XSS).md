The victim visits a web page / app that executes malicious code. This is done through a script (e.g. JavaScript, Groovy, GML).

![[Pasted image 20230811120247.png]]

Types:
- stored / persistent - code is injected into website's database and served to user visiting affected page -> results in execution in browser
- reflected - script is embedded into URL and reflected off a web server to victim's browser when they click on link
- DOM-based - client-side script manipulates [[Document Object Model]] and injects code directly into user's browser
- blind - script is sent to server and server's response containing the script is served to the victim browser

Mitigation:
- prohibit HTML code in inputs
- validate inputs
- secure cookies
- sanitize data
- use web application firewall (WAF)

Forces end-user to execute unwanted actions on web app they're currently authenticated. The attacker tricks the users into executing attacks through social engineering.

![[Pasted image 20230811121848.png]]

[[Cross-site scripting attack (XSS)|XSS]] vs XSRF:

| Aspect               | XSS            | XSRF                          |
| -------------------- | -------------- | ----------------------------- |
| Attack Target        | user's browser | user's authenticated sessions |
| Attack Mechanism     | injects malicious scripts into web page | tricks users into doing unintended actions |
| Victim's involvement | unknowingly viewing compromised page | unknowingly performing action on another site |
| Purpose              | stealing data, performing actions, malware | performing unauthorised actions |
| Exploits trust in    | user's trust in website's content | user's authenticated session in app |
| Examples             | stored XSS, reflected XSS, DOM-based XSS | unauthorised email change, form submissions |
| Impact               | data theft, defacement, distribution of malware | unauthorised actions on user's behalf |
| Prevention           | input validation, output encoding, content security policies (CSP) | Anti-CSRF tokens, same-site cookie attributes |


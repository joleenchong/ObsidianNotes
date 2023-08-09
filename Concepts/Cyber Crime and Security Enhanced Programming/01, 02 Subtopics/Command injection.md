An attack where the goal is to execute some commands on the host OS through a vulnerable app.
- commands are executed with privilege of vulnerable app -> so execute with least privilege

Mitigation:
- don't run system commands with user-supplied input
- least privilege
- strong input validation for input passed into commands
- only use secure APIs


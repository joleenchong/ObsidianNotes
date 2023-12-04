Serialisation - converting Object into series of bytes to save object in easily transmittable form
- Needed for caching, replication, communication, persistence, cross-machine synchronisation

Vulnerabilities:
- untrusted data - object fields inaccessible to users
- custom deserialisation functions / code
- object type serialisations - unexpected objects
- function trampolines / gadgets - chain multiple object types

Gadgets:
- short code (usually assembly or machine code instructions) within target app that perform specific tasks
- gadget chains - one or more gadgets working in sequence

How attack:
- identify software vulnerability (e.g. buffer overflows, code injections)
- attacker identifies and chains gadgets -> creates instruction sequence to use all the vulnerabilities to achieve something

Prevention:
- use non-native formats - XML & JSON
- use runtime application self-protection (RASP)
- implement checks for data integrity
- only deserialise simple objects
- run deserialisation code in low privilege environments
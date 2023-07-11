An event-driven, serverless compute option that doesn't need maintaining [[Azure Virtual Machines]] or [[Azure Containers]]. An event wakes the function, alleviating the need to keep resources provisioned where there are no events. They're considered a [[Platform as a Service (PaaS)]] leaning towards the SaaS spectrum as they aren't pre-made software, but compute options that the user creates & configures without worrying abt infrastructure.

Benefits:
- no need to worry about platform or infrastructure
- scalability
- only charges for CPU time used when function runs - runs code when it's triggered and automatically deallocates resources when function is finished

Functions can be stateless or stateful:
- stateless (default) - behave as if restarted every time they respond to an event
- stateful (AKA durable functions) - context is passed through function to track prior activity
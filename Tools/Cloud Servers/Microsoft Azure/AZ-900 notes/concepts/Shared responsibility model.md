Responsibilities are shared between the cloud provider and consumer. Server upkeep is handled by the provider while the consumer is responsible for the security of the stored information. Responsibility is balanced between the provider and consumer based on cloud service type: [[Infrastructure as a Service (IaaS)]] places most responsibility on the consumer, [[Software as a Service (SaaS)]] places most responsibility on the provider, while [[Platform as a Service (PaaS)]] evenly distributes responsibility between them.

The consumer is always responsible for:
- info & data stored in cloud
- allowed devices to connect to cloud (PCs, mobiles, etc.)
- accounts & identities of people, services & devices within organisation

The provider is always responsible for:
- physical datacenter
- physical network
- physical hosts

| Responsibility                      | SaaS     | PaaS   | IaaS     |
| ----------------------------------- | -------- | ------ | -------- |
| Identity & directory infrastructure | Shared   | Shared | Consumer |
| Applications                        | Provider | Shared | Consumer |
| Network controls                    | Provider | Shared | Consumer |
| Operating system | Provider | Provider | Consumer |


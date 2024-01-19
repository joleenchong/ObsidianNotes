
Pod - an abstraction over container:
- smallest k8s unit
- does abstraction to avoid having to interact with the docker directly
- usually 1 app per pod
- each pod gets own IP address
	- when pod dies and revives, it gets new IP address

Service - a permanent IP address:
- types:
	- internal - doesn't expose service to public
	- external - does expose service to public
- also a load balancer - forwards request to less busy pods

Ingress - forwards requests to services:
- used if you want to use a more productiony URL

ConfigMap - an external configuration of an app:
- contains configs like database URL
- connect it to pod so pod gets data
- when changing configurations, just change in configMap
- only store non-confidential data

Secret - ConfigMap for secret data:
- doesn't make it automatically secure

Volume - long term storage
- attaches physical storage on pod
- can be local or remote

Deployment - blueprints for pods:
- main thing you would work with
- for replicating application pods

StatefulSet - deployments for saving state:
- used for databases
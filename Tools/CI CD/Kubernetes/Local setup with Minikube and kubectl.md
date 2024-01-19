A minikube is a one node cluster where master processes and worker processes run on one node. It comes with pre-installed Docker to run containers + pods.

Kubectl is a command line tool to interact with k8s clusters by interacting with the API server.

Process
- start Minikube using `minikube start`
- create yaml configuration file for deployments
- apply yaml config using `kubetctl apply -f filename.yml`
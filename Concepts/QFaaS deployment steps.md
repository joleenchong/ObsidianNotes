Carried out on Google Cloud with Google Kubernetes Engine.
Domain name: qfaas.live

1. Create Dockerfile to build qfaas-core with dependencies
	- qfaas-core exposed on TCP:5000
	- Optional: create a deployment yaml to apply with kubectl?
	- Runs `python3 main.py`
	- Might need to install qfaas pip library, but there were some issues with installing this
2. Create 2 clusters, one for Gitlab Server, one for Main
	- likely may merge these clusters so they can connect with each other. Gitlab Server only needs one node anyways
	- put in same fleet
3. Deploy OpenFaaS on Main cluster using arkade
4. Deploy Gitlab Server on Gitlab cluster
5. Next - try to access Gitlab Server using gitlab.qfaas.live
	- configure Cloud DNS Wildcard entry to point to Gitlab Server external IP address with qfaas.live
	- Firewall?
6. Create Dockerfiles for qfaas-fn and qfaas-ui to deploy to server
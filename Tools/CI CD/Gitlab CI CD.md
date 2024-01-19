A pipeline of actions that execute when committing to a git repo to deliver changes to the end user. These can be tests, building and packaging, artifact repository, and deployment.

Architecture:
- instance / server - hosts app code and pipeline config
- runner - separate machines connected to the main server to run CI/CD jobs

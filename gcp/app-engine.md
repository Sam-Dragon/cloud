# App Engine

- It is PAAS service
- It is serverless
- Less responsibility & flexibility
- It is the simplest way to deploy & scale applications in GCP
- It provides end-to-end application deployment
- It supports all runtimes such as Java, Go, Ruby, Python etc..

> Features
- Auto Scaling & automatic Load balancing
- Managed platform updates & app health monitoring
- Automatic versioning
- Traffic splitting

> Environments
- Standard
  - Applications run in specific runtime sandboxes
  - v1: older one which supports runtimes such java, python, php,go
    - Has language restrictions on python and php
    - limited network acess 
  - v2: new one which supports runtimes such java, python, php,go
    - full network access & no language restrictions
- Flexible
  - Applications instances runs with **docker containers** 
  - Makes use of compute engine VM's
  - Supports any runtime
  - Provides access to local disks and background process

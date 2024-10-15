# App Engine

- It is PAAS service
- It is serverless
- Less responsibility & flexibility
- It is the simplest way to deploy & scale applications in GCP
- It provides end-to-end application deployment
- It supports all runtimes such as Java, Go, Ruby, Python etc..
- One app engine per region

> Features
- Auto Scaling & automatic Load balancing
- Managed platform updates & app health monitoring
- Automatic versioning
- Traffic splitting

> Environments
- Standard [REcommended]
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

**Note**: App comparision to pick environment in video.88

> Application Component Hierarchy
- Application
  - One application per project
- Service
  - Create micro services or app components
  - Each service can have different settings
- Version
  - Each version associate with code and configuration
  - Each version can run in one or more instances
  - Multiple versions can co-exist
  - Options to rollback and split traffic
 
> Scaling Instances
- Automatic: Recommended for continuously running workloads
- Basic: Recommended for Adhoc workloads
- Manual: User control

> Request Routing
- Routing by URL
- Syntax
  - https://PROJECT_ID.REGION_ID.r.appspot.com (default service)
  - https://SERVICE-dot-PROJECT_ID.REGION_ID.r.appspot.com (specific service)
  - https://VERSION-dot-SERVICE-dot-PROJECT_ID.REGION_ID.r.appspot.com (specific version of service)

- Routing with Dispatch File
  - Configure dispatch.yml with routes

- Routing with Cloud Load Balancing
  - Configure routes with load balancer 

> Deploy new version without downtime
- Deploy the new version & shift traffic to new version using [--promote]
- Deploy the only new version but dont traffic [--no-promote]
- Deploy the new version but shift only small traffic using canary style [--splits=v2=.9,v1=.1]
- Deploy the new version but shift gradually [--migrate]

> Splitting Traffic ways
- It is used in conjuntion with set-traffic with '**--split-by**' flag

- IP Splitting [Less Recommended]
  - Based on IP address

- Cooking Splitting [Highly Recommended]
  - Based on Cookie [GOOGAPPUUID]

- Random [Highly Recommended]
  - Does it randomly 

> Jobs
- 

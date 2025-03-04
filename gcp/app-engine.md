# App Engine

- It is PAAS service
- It is serverless
- Less responsibility & flexibility
- It is the simplest way to deploy & scale applications in GCP
- It provides end-to-end application deployment
- It supports all runtimes such as Java, Go, Ruby, Python etc..
- It is regional based [Cannot be changed once created]
- It is one per project
- Cannot migrate region based app to another region
- Scale downs to zero for standard-v2 version but not for flexible type
- Use dynamic instances for cost sensitive

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
  - It supports scaling type such as Automatic, Manual, Basic
  - It can scale down to zero
  - Starts up in seconds
  - Supports Rapid scaling
  - Max request timeout is between 1 to 10 minutes
  - Local disk writes to /tmp folder
  - ssh for debugging is not allowed
  - charged based on instance hours

- Flexible
  - Applications instances runs with **docker containers** 
  - Makes use of compute engine VM's
  - Supports any runtime
  - Provides access to local disks and background process
  - It supports scaling type such as Automatic, Manual
  - It cannot scale down to zero. It needs minimum one instance
  - Starts up in minutes
  - Doesnt Support Rapid scaling
  - Max request timeout is upto 60 minutes
  - Local disk writes to new disk if created on startup
  - ssh for debugging is allowed
  - charged based on persistence disks, vcpu's, memory

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
- Schedule jobs on pre-defined interval
- Configure cron.yml for jobs

> Queue
- Manages the task queues
- Configure queue.yml for tasks

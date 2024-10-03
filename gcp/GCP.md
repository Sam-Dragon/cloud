# Cloud
- On demand resource provisioning [Think like Contractor job]
- No maintainance
- Globalization

# GCP
- It has 200+ services
- It is Iaas service unlike amazon which is Paas service

> Regions & Zones
- region is large area with common features. 
- geographical location to host resources
- Region contains 'zones'
<br> Ex. monsoon region, mountanious region <br>

> Advantages
- prevents slow access to other users in the world. low latency
- prevents data center crash. High availablity
- global footprint
- Adhere govt regulations

> Zone
- It is small area that differs from its surroundings in some way [special area]. 
- each zone has data centers
Ex. war zone, no-parking zone

# Compute Engine
- Provision and manage Virtual machines (VM's) [Virtual machines - virtual servers in GCP]
- Create & manage lifecycle of VM's
- Load balancing & auto scaling for multiple VM's
- Attach Storage [& network storage] to VM's
- Manage Network connectivity & configuration of VM's

> IP's
- Internal - addresses which are internal to particular network
- External - addresses which are internet accessible
- VM instance must have internal ip. external ip is present if internet accessible but if vm instance stops we lose external ip

Problem - External ip keeps changing on vm restart ? How to avoid <br>
Solution - one way we can use is 'static ip' or use load balancers

> Static IP Address [VPC Network]
- It is re-assignable
- It needs to be removed
Note: They are billable even if you dont use it 

> Machine Types
- Basically contains the configuations of the hardware [CPU, Memory, GPU]
- There are predefined machine types are provided but we can still customize it
- Custom machine types are restricted to machine types such as N2. E1 etc..

> Availability policy
- It is mainly for migration activities or short lived activities
- Migration is On by default
- Short lived activites needs to be configured 

> GPU
- High performance for math intensive & graph intensive workloads
- High cost
- Use images for GPU libraries

  > Restrictions
  - Limited to specific machine types
  - Cannot be used for maintainance
  - Allow restart always

> Affinity
- To make sure specific types or group of pods runs in the server, we provide affinity rules
- It can be configured under 'Sole Tenancy' of VM configuration

# Simplifying vm instance setup
> Startup scripts
  - On load, we can provide all plugins to install

> **Instance template** [Recommended]
  - Used to create vm instances or create instance groups
  - We cannot update the template created. Copy and modify it
  - Image family can be specified
  
> **Custom Image**
  - In order to prevent installation of os patches and software on launch of vm instances increase the boot time
  we create image out of instance
  - It is sharable
  - Deprecate old images
  - Security

# Preemptible VM
- Short-lived cheaper compute instances [spot instances like AWS]
- It lives upto 24hrs

> Usage
- If application in fault tolerant
- If it is cost sensesitive
- Workload is not immediate
<br>Ex: Non-immediate batch processing jobs

> Restrictions
- Not always available
- No SLA & cannot be migrated to regular VM's
- No automatic restarts
- No discounts

# Spot VM
- Latest version of Preemptible VM
- No restriction on time
- Similar restrictions to Preemptible VM

# Migration of VM
- Migration is enabled by default in 'Availability policy'
- It can be migrated to another host in same zone
- Support for instances of Local SSD's
- No support for GPU and preemptible instances
- **It is configured in Availability policy [Maintainance Or Restart]**

# Best Practices
- Ensure VM configuration is based on project, cost & api's enablement
- Node affinity can be configured on server
- OS patch for large number of VM's can be done via VM Manager
- Install software can be done via SSH
- Prevent exposing VM to Internet can be done by prevent external address allocation via Firewall rules

# GCloud
- It is command line interface to interact with google cloud resources [CRUD]
- Most services can be managed with gcloud cli. i.e. VM, instance groups, database etc..

# Instance Groups
- Group of vm instances managed as a single entity

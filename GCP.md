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

- zone is small area that differs from its surroundings in some way [special area]. 
- each zone has data centers
Ex. war zone, no-parking zone


# Compute Engine
- provision and manage Virtual machines (VM's) [Virtual machines - virtual servers in GCP]
- create & manage lifecycle of VM's
- Load balancing & auto scaling for multiple VM's
- Attach Storage [& network storage] to VM's
- Manage Network connectivity & configuration of VM's

> IP's
- Internal - addresses which are internal to particular network
- External - addresses which are internet accessible
- VM instance must have internal ip. external ip is present if internet accessible but if vm instance stops we lose external ip

Problem - External ip keeps changing on vm restart ? How to avoid
Solution - one way we can use is 'static ip' or use load balancers

> Static IP Address [VPC Network]
- It is re-assignable
- It needs to be removed
Note: They are billable even if you dont use it 

# Simplifying vm instance setup
- Startup scripts
  - on load, we can provide all plugins to install

- Instance template [Recommended]
  - used to create vm instances or create instance groups
  - we cannot update the template created. Copy and modify it
  - Image family can be specified
  
- custom image
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
- similar restrictions to Preemptible VM

# Migration of VM
- Migration is enabled by default in 'Availability policy '
- It can be migrated to another host in same zone
- support for instances of Local SSD's
- No support for GPU and preemptible instances
- **It is configured in Availability policy [Maintainance Or Restart]**

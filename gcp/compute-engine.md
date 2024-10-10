# Cloud
- On demand resource provisioning [Think like Contractor job]
- No maintainance
- Globalization

# GCP
- It has 200+ services
- It is Iaas service unlike amazon which is Paas service

> Regions & Zones
- It is large area with common features. 
- Geographical location to host resources
- Region contains 'zones'
<br> Ex. monsoon region, mountanious region <br>

> Advantages
- Prevents slow access to other users in the world. low latency
- Prevents data center crash. High availablity
- Global footprint
- Adhere govt regulations

> Zone
- It is small area that differs from its surroundings in some way [special area]. 
- Each zone has data centers
Ex. war zone, no-parking zone

# Compute Engine
- It is IAAS
- It gives more flexibility & responsibility
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
- Manage group of similar VM's having similar lifecycle as One Unit
- It mandatorily requires **instance template**
- It can be created as stateless & stateful [database + rest api] as well

> Types
- Managed - MIG [Recommended]
  - Identical VM's created using templates
  - Manages the certain number of instances
  - Features:
    - Auto scaling: scale based on the load
    - Auto Healing: detection of failures and recovering from it
    - Add load balancer to distribute the load
    - Create instances in multiple zones
    - Release new application without any downtime [Rolling updates or canary deployment]
      - Option: update VMS [Rolling update + Canary Testing] or Restart/Replace VMS [Restart/Replace with new VMS]

- UnManaged [Not Recommended]
  - Different configuration of VM in same group
  - It doesn't offer Auto scaling, Auto Healing & Manage releases

> Use cases
- MIG for survive zonal failures
- Preserve VM state [Database Data]
- High availability
- Self healing
- Frequent Scale up & Scale down

# Cloud Loadbalancing
- Distributes the traffic accross the application instances in single region or multiple zones
- Fully distributed, software defined managed service
- Features
    - Health Checks - Route to healthy instances [Recover from failures]
    - Auto Scaling
    - Global load balancing with single anycast ip [supports internal load balancing]
- It provides 'High availability'
- It enables 'Auto Scaling'
- It provides 'Resiliency'

> Protocols
- It is standard of distributing of data over the network
- Network Layer[L3]: It transfer bits and bytes [0, 1]. It is Unreliable
    - IP  
- Transport Layer[L4]: It ensures the bits and bytes are transferred properly\
    - TCP [Transmission Control]: Transfer bytes in order. Reliability > Perfromance
    - TLS [Transport Layer Security]: Secured TCP
    - UDP [User Datagram Protocol]: Alternate to TCP. Performance > Reliability 
- Application Layer[L7]: We host our applications
    - HTTP[Hyper Text Transfer Protocol]: Stateless Request/Response Cycle
    - HTTPS[Hyper Text Transfer Protocol Secured]: Secure HTTP with certificates
    - SMTP[Simple Mail Transfer Protocol]: For mailing purposes
    - FTP [File Transfer Protocol]: For files 

> Creation
- They are of two types
  - Client-side: Client manges the traffic & load balancer is deployed on client side.
    - It carries list of server names
  - Server-side[Recommended]: Server manges the traffic & load balancer is deployed in front of server instances
    - It is a middle component between server & application instances

- They are of two types
  - Internal: load balancers which communicate between VM's internal to network
    - They can be used for TCP, UDP or HTTP(s) traffic
    - For TCP/UDP, we will use Internal TCP/UDP Load Balancer
    - For HTTP(S), we will use Internal HTTP(S) Load Balancer
      
  - External: load balancers which communicate between Internet & VM
    - For HTTP(S), we will used External HTTP(S) Load Balancer (Global or Regional)
    - For TCP, if SSL offload, we will use SSL Proxy Load Balancer else TCP Proxy LB if not External Network LB
    - For UDP/ESP or ICMP, if SSL offload, we will use External Network LB

    Note: All balancer types uses Proxy way only external tcp/udp uses pass-though way
    
> Components

  > backend
  - group of endpoints recieves the traffice from google cloud load balancer [Ex. Instance Groups]

  > frontend
  - It serves the client requests.It specifies 'ip address, port & protocol'
  - For ssl, certificate must be assigned 

  > Host & Path Rules
  - Defines rules to redirect the traffic to different backends
  - It can either redirect request to path or host or by headers

> Load balancing - SSL/TLS Termination/offloading
- Client to Load Balancer Over Internet: **HTTPS/TLS** required
- Load Balancer to VM Servers : **HTTP/HTTPS/TCP** required

> Scenarios
- healthy instances to recieve traffic
- high availability
- route request to mutiple mircoservices
- external HTTPS traffic
- ssl termination for NON-HTTPS

# Managed Services

- Basic Terminologies
  - IAAS (Infrastructure As A Service)
    - Only infra [vitualiztion + hardware + networking] will be given, rest all needs to be configured
    - Example: Google Compute Engine [GCE]
  - PAAS (Platform As A Service)
    - Only platform [OS + Application Runtime + vitualiztion + hardware + networking] will be given, rest all needs to be configured
    - Example: Google App Engine
    - Varieties  
      - FAAS (Function As A Service): Functions needs to be defined. thats it
        - Google Cloud Functions [GCF]  
      - CAAS (Container As A Service): Containers needs to be specified. thats it
        - Google Kubernetes Engine [GKE], Google App Engine, Cloud Run
      - Databases [SQL + NoSQL]: Google Cloud SQL, Amazon RDS, Azure SQL  etc..
  - Serverless
    - Worry about application, forget about infra, scaling, healing 
    - Pay for requests not for servers
    - Example: lamdas in AWS, azure functions in azure and google functions in google cloud, Google App Engine, Cloud Run 

# Compute Engine
- It is Iaas
- Virtual Machine: Basic server configuration sits here [Charagable]
- Instance Templates: Template configuration for creating VM [Not Charagable]
- Image: It is created from boot persistent disk
- Machine Image: Similar to instance template but additionally save multiple boot disks data, permissions [Charagable]
- Instance Groups: It is like replicate set which will use instance templates & creates VM's
- Load Balancer: It uses instance groups for managing traffic across VM's
- Preemptible VM: short-lived cheaper compute instances [Max 24 hrs]
- Spot VM: short-lived cheaper compute instances with any time limit
- Filestore: used for sharing files 

> Instance Template vs Custom Images vs Persistent disks snapshots vs Machine Images
- Instance template mainly used for cloning, replication and contains vm configuration but no backup
- where as custom images used for cloning and replication and single disk backup but no configuration
- where as persistent disks snaphots used only for disks backup but no configuration nor cloning and replication
- finally machine images manages everything backups, cloning and replication, configuration

# App Engine
- It is PaaS
- It is always one app per project
- change of region is not possible once configured
- Application: It is based on region & can be specified with version
- Service: The instance of application & it can have applications with different versions 
- Version: Each deployment of application is treated as new version

# Databases
- Relational OLTP databases: Cloud SQL [Small scale], Cloud Spanner [Large scale - Mission Critical]
- Relational OLAP databases: BigQuery [Datawarehousing & BigData workloads]
- NoSQL databases: Cloud Firestore (Datastore++) [serverless, medium scale - mobile & web apps], Cloud BigTable [No Serverless, large scale - IOT, analytical & operational workloads, time-series data]
- In-memory databases: Cloud Memorystore

# Cloud Functions
- It is FAAS or serverless
- It is short lived process which is event driven
- It can be used for batch process, data upload
- No server management

> **Gen 2**
- It uses '**cloud run**' internally for multiple revisons & traffic splitting
- Longer Request Timeout: upto 60 mins [1st gen has only 9mins]
- Large Instances Size: upto 16GB ram and 4vCPU [1st has max 8GB ram & 2 vCPU]
- Concurrency: upto 1000 concurrent requests per function instance [v1: only 1 request per instance]
- Multiple Function Revisions and Traffic Splitting supported [v1 not supported]
- Support 90+ event types - enabled by Eventarc [v1 has only 7 event types]

# Cloud Run
- It is CAAS or serverless
- No server management
- funlly managed serverless platform for containerized applications

# Cloud KMS [Key Management Service]
- It is responsible to manage cryptographic keys
- It can be used for both software and hardware
- Integrates with most of gcp services by encypting data in multiple ways
  - Google Managed Key: No configuration
  - Custom Managed Key: Key managed by KMS
  - Customer Supplied Key: User defined key
- Encryption ways
  - Symmetric Key Encryption: Same key for both encyption and decryption
  - ASymmetric Key Encryption: public key for encryption but private key for decryption. uses public key cryptography such as RSA

# IAM
- Basic Roles (or Primitive Roles) - Viewer/Editor/Owner [**NOT** RECOMMNED FOR PRODUCTION]
  - Viewer: Read Only
  - Editor: Viewer + Edit Actions
  - Owner: Editor + Manage Roles & Permissions + Billing

- Predefined Roles - Fine grained roles predefined & managed by google [RECOMMNED FOR PRODUCTION]
  - Different roles for different purposes
    
# Scenarios
- Compute Engine [IaaS] - VM management 
- Google Kubernetes Engine [CaaS] - containerized apps with cluster
- App Engine [PaaS (CaaS, Serverless)] - Application code management
- Cloud Functions [Faas] - Event driven apps
- Cloud Run [CAAS (Serverless)] - containerized apps without cluster

# GCloud Commands
- Cloud Storage - gsutil
- Cloud BigQuery - bq
- Cloud Bigtable - cbt
- Kubernetes - kubectl

- Configurations [Account, Project, Region, Zone Info] - gcloud config
- Compute Engine [Regions, Zones Info, VM, machine types, Instance Templates, Instance Groups, local and persistent disks, Images, ] - gcloud compute
- App Engine [deploy, services, instances, versions, browse] - gcloud app
- Cloud Run [deploy, service, revision] - gcloud run
- Cloud Functions [deploy, service, revision] - gcloud functions
- Pub/Sub [topics, subscriptions] - gcloud pubsub

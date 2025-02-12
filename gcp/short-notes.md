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
- fully managed serverless platform for containerized applications
- **It fully managed and deploys serverless applications** 

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
  - Storage Admin: Manages buckets and all the objects in the bucket
  - Storage Object Admin: Manages all the objects within a bucket [cannot create new buckets]
  - Storage Object Viewer: Reads all the objects within a bucket [No editing]
  - Storage Object Creator: Creates objects in an a bucket
 
- Custom Roles: if not defined in predefined roles 

# Service Accounts
- Mainly used for machine level access
- It is associated to email address [No creds]
- Uses Private/public keys
- Types
  - Default, User Defined & Google managed

# ACL [Access Control List]  
- We can provide customized permissions

# Cloud Storage - **Signed URL**
- It is mainly used with service accounts
- A URL that gives permission for limited time to perform specific actions

# Cloud Storage - **Static Websites**
- Bucket Name same as domain name
- Copy all files to bucket
- Give access to all users by providing permissions

# Databases
- RPO [Recovery Point Objective] - Maximum acceptable period of data loss
- RTO [Recovery Time Objective] - Maximum acceptable downtime
- OLTP [Online Transaction Processing] - Tranasctions based
- OLAP [Online Analytics Processing] - analytics based

# Relational Database
- fixed set of schema & strong transactional capabilities used for OLAP & OLTP usecases
- OLTP
  - **Row storage** supporting large number of transactions
  - Popular databases : MySql, Postgres SQL, Oracle SQL etc..
  - Google Managed Service:
    - **Cloud SQL**:
      - fully managed relational database service 
      - supports MySQL, PostgresSQL & SQL Server for **regional** databases [upto few **TB's**]
      - Automatic encryption, maintanance, updates, backups, storage increase & binary logging
      - supports **migration but with downtime**
      - data export from UI or gcloud
      - High availability uses primary & standby instance. It cannot be used as a Read replica. At a time only single instance is connected
      - High availabiliy setup cannot be used as Read Replica
    - **Cloud Spanner**:
      - Fully managed, '**Mission critical**' database [global database]
      - supports large transactions for global applications upto few **PB's**
      - Higher availability, Strong transactional consistency, horizontal scaling
      - data export can be done via cloud console or dataflow but 'gcloud export' is not supported
  - Use cases - ERP, CRM, E-Commerce, Banking Apps
- OLAP
  - Mainly used for analytics 
  - **Columnar storage** supporting very large number of transactions
  - Google Managed Service:
    - **Big Query**: uses petabytes of data
  - Use Cases: Reporting Systems, Data warehouses, Business Intelligence

# Non Relational Database
- flexible schema, horizontal scaling, scalability & high performance
- Google Managed Service
  - **Cloud Firestore** [or Datastore++]:
    - managed serverless no-sql **document** database
    - strong consistency, mobile & web client libraries
    - recommended for small to medium databases
    - Exports the data from cloud bigtable to cloud storage not from cloud console
    - Use cases: user profile, product catalogs
  - **Cloud BigTable**:
    - managed, scalable NoSQL **wide columnar** database but **not serverless**
    - scale horizontally with multiple nodes **[No downtime for cluster resizing]**
    - Recommended for operational & analytical workloads Not for transactional workloads [supports single row transactions]
    - Export: cannot export using cloud console nor gcloud but can be done using java app or hbase commands
    - Use cases: IOT Streams, Graph and real time analytics [timeseries data, stock prices, financial data]

# In-Memory Database
- Retriving persistent data from memory
- Use Cases: Caching, Session Management, Leader Board etc.
- Google Managed Service:
  - **Memory Store**
    - Fully managed service
    - Reduce access times
    - Supports **Redis & Memcache**
      - Memcache: Caching, Session store
      - Redis: Leader Board, Player Profiles etc.  

# Scenarios
- Compute Engine [IaaS] - VM management 
- Google Kubernetes Engine [CaaS] - containerized apps with cluster
- App Engine [PaaS (CaaS, Serverless)] - Application code management
- Cloud Functions [Faas] - Event driven apps
- Cloud Run [CAAS (Serverless)] - containerized apps without cluster
- [Internal] VM to Cloud Storage/Pubsub - [Uses Google Managed Keys]
- [External] On Premises to Cloud Storage - [Internal required Service Account User Managed Keys]
- [External] On Premises to Google Cloud API's - [OAuth2, OpenIDConnect, JWT]
- very small RTO [data loss - 1 mins] and RPO [downtime - 5 mins] - Hot Standby 
- very critical data RTO [data loss - 1 mins] and RPO [downtime - 15 mins] - Warm Standby
- very critical RTO [data loss - 1 mins] and High RPO [downtime - few hours] - Snapshots & Transaction Logs

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
- IAM [roles] - gcloud iam

# Additional
- Cloud Build: CICD platform for deployment process. It primary task is to build, test and deploy apps
- Cloud Composer: Fully mananged workflow orchastration service built on Apache Airflow 

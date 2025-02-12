# Database

> Problems
- If database crashes, data is lost
- If datacenter crashes, database will be down

> Prime Factors
- Availability
  - Multiple standby's available or distribute the database [either on multiple regions or multiple zones]
- Durability
  - Multiple copies of data (standbys, transaction logs & replicas) [either on multiple regions or multiple zones]
- Consistency
  - Update data consistently over multiple replicas 
 
> Terminologies
- RPO [Recovery Point Objective] - Maximum acceptable period of data loss
- RTO [Recovery Time Objective] - Maximum acceptable downtime

> Reporting & Analytics Applications 
- Performance Problem
- It can be solved using vertical scaling, read replicas or creating a database cluster

> Consistency Types
- Strong Consistency
  - synchronous replicas to all replicas
  - Example: Banking Transactions
- Eventual Consistency 
  - asynchronous replicas to all replicas
  - Example: social media posts, facebook message posts, twitter tweets etc..
- Read After Write Consistency
  - Inserts are available immediately, however updates uses eventual consistency

> Categories
- Relational [OLTP & OLAP], Document, Graph, Key Value, In-Memory etc..
- Key Factors
  - Based on Schema or Schemaless
  - Based on transaction properties [Atomicity & Consistency]
  - Based on latency [seconds, milliseconds or microseconds]
  - Based on No. of transactions per second [hundred or million or trillion]
  - Based on data size [MBs or GBs or PBs]     

# Relational Database
- Predefined schema with tables & relationships
- Strong transactional capabilities
- Used for OLTP [Online Transaction Processing] usecases
- Used for OLAP [Online Analytics Processing] usecases

> Relational Database - OLTP
- Large number of users making large number of transactions
- It uses row storage
- Use cases - ERP, CRM, E-Commerce, Banking Apps
- Popular Databases:
  - MySql, PostgresSql, Oracle sql etc.
- Google Managed Service:
  - Cloud SQL: Supports MySQL, PostgresSQL & SQL Server for regional database [upto few TB's]
  - Cloud Spanner: Unlimited scale [multiple PB's] availibility to global applications with horizonal scaling

> Relational Database - OLAP
- Used to analyze petabytes of data
- It uses columnar storage
- It uses high-compression, distribute data, single query across nodes
- Use Cases: Reporting Systems, Data warehouses, Business Intelligence
- Google Managed Service:
  - BigQuery: uses petabytes of data  

> Cloud SQL
- Fully managed relational database service
- supports MySQL, PostgresSQL & SQL Server
- It is regional service not global
- Use HHD's or SSD's
- Upto 416GB of RAM & 30TB of data storage
- Automatic encryption, maintanance, updates, backups & binary logging
- Automatic storage increase without downtime
- Point in time recovery
- Supports Migration but with downtime
- Export data from UI or gcloud
- High availability uses primary & standby instance. It cannot be used as a Read replica. At a time only single instance is connected
- Read replicas for newer version possible in cross zone, cross region & external

> Cloud Spanner:
- Fully managed, 'Mission critical' database
- Huge volumes of relational data
- Infinite 'scaling' of growing application
- Need 'global' database
- Higher availability
- It is very expensive 
- Strong transactional consistency
- Scale to PB's of data with automatic sharding
- Horizontal scaling
- Export can be done via cloud console or dataflow but 'gcloud export' is not supported

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
  - Use Cases: Reporting Systems, Data warehouses, Business Intelligence 
  - Google Managed Service:
    - BigQuery: uses petabytes of data  

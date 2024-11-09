# Database

> Problems
- If database crashes, data is lost
- If datacenter crashes, data will be down

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

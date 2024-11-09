# Non Relational Databases
- flexible schema
- horizontal scaling
- scalability & high performance
- Google Managed Service
  - Cloud Firestore [or Datastore++]: managed serverless no-sql document database
  - Cloud BigTable: managed, scalable NoSQL wide column database
 
> Cloud Firestore
- Provides acid ike transactions, sql queries, indexes
- Strong consistency, mobile & web client libraries
- Used for small & medium databases

> Cloud BigTable
- Not Serverless [Requires VM instances]
- Recommended data size > 10 TB to PB's
- Recommended for operational & analytical workloads
- Not recommended for transactional workloads [supports single row transactions] 

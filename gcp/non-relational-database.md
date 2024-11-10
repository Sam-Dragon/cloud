# Non Relational Databases
- flexible schema
- horizontal scaling
- scalability & high performance
- Google Managed Service
  - Cloud Firestore [or Datastore++]: managed serverless no-sql document database
  - Cloud BigTable: managed, scalable NoSQL wide column database

> Cloud Datastore
- Highly scalable no-sql document database
- Reommended for few TB's of data
- Supports transactions, indexes & SQL like queries [GQL]
- Used for flexible schema with transactions
- Structure: Kind > Entity [use namespaces to group entities]
- Export only from gcloud [Not from cloud console]
 
> Cloud Firestore
- Provides acid ike transactions, sql queries, indexes
- Strong consistency, mobile & web client libraries
- Used for small & medium databases
- offers datastore & native modes

> Cloud BigTable
- Not Serverless [Requires VM instances]
- Recommended data size > 10TB to PB's
- Recommended for operational & analytical workloads
- Not recommended for transactional workloads [supports single row transactions] 

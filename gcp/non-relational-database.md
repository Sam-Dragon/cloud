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
- Exports the data from cloud bigquery to cloud storage
 
> Cloud Firestore
- Provides acid ike transactions, sql queries, indexes
- Strong consistency, mobile & web client libraries
- Used for small & medium databases
- offers datastore & native modes
- Exports the data from cloud bigquery to cloud storage

> Cloud BigTable
- Not Serverless [Requires VM instances]
- Recommended data size > 10TB to PB's
- Recommended for operational & analytical workloads
- Not recommended for transactional workloads [supports single row transactions] 
- Petabyte scale, wide column NoSQL db (HBase Compatible)
- supports single row transactions
- Not Serverless: Instance is mandatory
- Export: cannot export using cloud console or gcloud but can be done using java app or hbase commands
- use 'cbt' command line tool (NOT gcloud)
- Use cases: IOT Streams, Graph and real time analytics [timeseries data, stock prices, financial data]

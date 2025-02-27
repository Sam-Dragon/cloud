# Cloud Storage

- It is called object storage. no partial updates allowed
- It provides rest-service endpoints
- It store all kind of files - text, binary, backup & archives
- We can have any number of objects
- It is responsible to store the data in case of backup & recovery

> Bucket
- Container to store all the objects in cloud. It must be globally unique 
- It can store the data in zonal or regional or multi-regional
- It is flexible, popular & inexpensive storage device

> Storage Class
- **Standard**: Best for **short term storage** and frequently access data
- **Nearline**: Best for **backups** and data access less than a **month**
- **Coldline**: Best for **disaster recovery** and data access less than a **quarter**
- **Archive**:  Best for **disaster recovery for long-term digital preservation** of data and data access less than a **year**

> Objects
- They are stored in buckets
- It has limit of max size of 5TB
- Object Versioning: Prevents accidental deletion and provides history
- Object Lifecycle Management: delete an object to set storage class to next version

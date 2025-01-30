# Block and File Storage

# Block Storage
- store the data in blocks
- one block storage device can be attached to one VM
- Exception: we can connect multiple block storage device to VM which are read only
- It can used as DAS [Direct Attach Storage] similar to harddisk (OR) [Storage Area Network] network connecting pool of devices[databases]. 
Ex: Hard disk

# File Storage
- media workflows like video editing
- share files to multiple file servers

# GCP Block Storage
- It is part of compute engine
- Types
  - Persistent Disks: Network Block Storage
    - zonal: data replicated to single zone
    - regional: data replicated to multiple zone
  - LocalSSDs: Local Block Storage

# GCP File Storage
- It is not part of compute engine
- Filestore: High performance file storage. 

# LocalSSDs
- physically attached to host of VM instance
- stores temporary data [ephemeral storage]
- automatically encrypted [google managed] - cannot configure custom keys
- lifecycle tied to vm instance
- only some machine types supports local ssds 
- supports SCSI and NVMe interface

> Advantages
- Very fast I/O [high thorughput & low latency]
- High IOP's while storing temporary information
Ex: caches, temporary data, scratch files

> Disadvantages
- Ephemeral storage
- Cannot detach and attach it to another VM instance

# Persistent Disks
- It will stored in the network
- More durable
- lifecycle is not tied to vm instance
- Increase size when needed
- They are regional and zonal
- It provides snapshots
Ex: Run custom database


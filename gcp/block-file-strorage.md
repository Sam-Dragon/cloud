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

# GCP 
> Block Storage
- Persistent Disks: Network Block Storage
  - zonal: data replicated to single zone
  - regional: data replicated to multiple zone
- LocalSSDs: Local Block Storage

> File Storage
- Filestore: High performance file storage

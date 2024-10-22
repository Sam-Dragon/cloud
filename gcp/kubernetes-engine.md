# Kubernetes Engine [GKE]

- Managed kubernetes services
- Minimizes operation for auto-repair & auto-upgrade
- It provides pod & **cluster autoscaling**
- Enables cloud logging and cloud monitoring with simple configuration
- Uses Container-Optimized OS, a hardend OS buit by google
- Provides support persistent disks & Local SSD

> Modes
- Standard: Responsible to manage the complete cluster  
- Autopilot: New mode, which manages complete cluster

> Advantages of Autopilot 
- reduce the operational cluster
- hadsoff-experience

> Cluster Types
- Zonal Cluster:
  - Single Zonal Cluster: single control plane. Nodes running in same zone
  - Multi Zonal Cluster: single control plane. Nodes running in multiple zones
- Regional Cluster: Replicas of control plane runs in multiple zones of given region. Nodes runs in same place where control                     plane runs
- Private Cluster: VPC native cluster. Nodes only have internal ip address
- Alpha Cluster: Cluster with alpha api, new k8s features can be tested here

# Best Practices
- Number of pods must be equal to number of nodes
- Use 'Auto scaling' to manual adjust number of pods vs nodes
- Replicate master nodes accross multiple zones for high availability
- some cpu is reserved by control plane so use multiple vcpu
- Stateful deployments for kafka, redis, zookeeper
- deamonset on each node for log collection or monitoring
- 
- 

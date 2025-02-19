# VPC [Virtual Private Cloud]
- Corporate network the provides internal secure network protecting resources, data & communication from external users
- Own isolated network in gcp cloud
- It is a **global** resource. i.e. It is not tied to any zone or region
- It contains subnets in one or more region
- Every project has default VPC
- Make sure to configure firewall rules for accessing
- It is specified when creating a VM

> Types
- Auto-mode VPC network: Default, subnets are created automatically
- custom-mode VPC network: manually created, subents are controlled. recommended for production

# Subnets
- It is associated to region 
- It helps you to seperate private resources [Internet NON accessible] from public resources [Internet accessible]
- It distributes resources across multiple regions for high availability
- IP's are ranged using CIDR blocks
- It manges the VM internal ip address range
- default subnets can talk to each other where as it cannot talk to custom subnet 

> Options
- **Private Google Access**: Allows VM to connect to google api's using private IP's
- **Flow Logs**: VPC related network issues

# CIDR [Classless Inter-Domain Routing] blocks
- It contains the starting IP address & range [/28]
- Range [/28] - indicates the first 28bits are fixed and last 4 bits can vary [i.e 2 ^ 4 = 16],
  that means total 16 IP addresses will be there

# Firewall Rules
- controls the traffic going in and out of network
- It is stateful
- each rule has priority assigned [0 [high] - 65535 [low - Default]]
- All egress is allowed but ingress is not [It must be overridden]
- It allows egress, ssh, rdc, ipcl

# Shared VPC
- **Organization has multiple projects and you want projects to communicate with each other**
- It can be achieved by creating share VPC at organization or folder level [Access Role: **Shared VPC Admin**]
- Network admins responsible for Host projects & resource users use service project
- It is centralized approach

# VPC Peering
- Connects VPC networks accross **different organizations**
- Networks in same project, different project & accross project in different organizations
- All communications are internal IP address. [Not accessible via internet]
- It is decentralized approach

# Hybrid Cloud
> Cloud VPN
- connect on-premise network to gcp network
- Implemented using IPSEC vpn tunnel
- Types: HA VPN [Dynamic Routing], Classic VPN [Static Routing]
- Useful in low bandwidth needs

> Cloud Interconnect
- High speed physical connection between on-premise and vpc network
- Types: Dedicate Interconnect [Recommended], Partner interconnect
- Data exchanges happens through a private network
- supports google api's and services can be privately accessed from on-premise
- Useful in high bandwidth needs

> Direct Peering
- connect customer network to google network
- It is not gcp service
- It is not recommended

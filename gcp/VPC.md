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
- It is associated to region or zone
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
- [/28] - indicates the first 28bits are fixed and last 4 bits can vary [i.e 2 ^ 4 = 16],
  that means total 16 IP addresses will be there

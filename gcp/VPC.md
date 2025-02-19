# VPC [Virtual Private Cloud]
- Corporate network the provides internal secure network protecting resources, data & communication from external users
- Own isolated network in gcp cloud
- It is a **global** resource. i.e. It is not tied to any zone or region
- It contains subnets in one or more region
- Every project has default VPC

# Subnets
- It is associated to region or zone
- It helps you to seperate private resources [Internet NON accessible] from public resources [Internet accessible]
- It distributes resources across multiple regions for high availability

> Types
- Auto-mode VPC network: Default, subnets are created automatically
- custom-mode VPC network: manually created, subents are controlled. recommended for production

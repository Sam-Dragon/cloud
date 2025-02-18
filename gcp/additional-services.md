# Services

# Google Cloud Deployment Manager
- Automatic provisioning of infrastructure
- All configurations is defined in simple text file - YAML
- Managed dependencies, Automatic rollbacks, version control, Automate deployment, avoid configuration drift<br>
Example: Creating mutliple enviroments with similar configuration

> Terminologies
- **Configuration File**: YAML file with resource definition in single deployment
- **Templates**: Reusable resource definitions that can be used for multiple configurations files
  - It can be developed in python or jinja 
- **Deployment**: Collection of resources that are deployed and managed together
- **Manifests**: Read only object containing original deployment configuration

# Cloud Market Place
- Install custom software with multiple resources
- Central repo for easily deployable apps & datasets [Playstore]
- One place to bring the software required for installation and manage

# Cloud DNS
- It is global Domain Name System
- It is service for setting up an website with a domain name
- It supports 2 zones: Public & Private

# Cloud DataFlow
- It is data-processing tool not migration
- It is serverless
- It is service which streams the data between platforms
- Migrate data, compress data, convert formats
- Example: Fraud Detection, Sensor Data Processing, Batch Processing
- It is based on Apache Beam

# Cloud DataProc
- Managed Spark & Hadoop Service
- It is mainly used for AI/ML
- It uses VM internally
- Modes: Single/Standard/High Availability [3 replicas]
- It is data analysis platform
- Alternative: BigQuery

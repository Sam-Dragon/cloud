# Commands

> Version
- gcloud --version

> Initialize
- gcloud init

# Base Configuration
- Group = config

# Sample 
> List with attribute
- gcloud config list [ATTRIBUTE]

> Set
- gcloud config set compute/region [REGION]

> UnSet
- gcloud config unset compute/region [REGION]

# Operations
> List
- gcloud GROUP SUB-GROUP ACTION ..

> ACTIONS = create, activate, delete, describe, list

# Sample
> List
- gcloud configs configurations list

> List with filter
- gcloud configs configurations list --filter [Field]:[Value]

> List with sorting
- gcloud configs configurations list --sort-by [Field]
    
> Create
- gcloud configs configurations create my-first-configs

> Describe
- gcloud configs configurations describe my-first-configs

> Delete
- gcloud configs configurations delete my-first-configs

> Activate
- gcloud configs configurations activate my-first-configs

# Module Configurations
  - GROUP = configs
  - SUB-GROUP = configurations

# VM Instances, Zones, Regions, Machine Types, Instance Templates
- Make sure project, region, zone is associated
- GROUP = compute
- SUB-GROUP = instances, zones, regions, machine-types, instance-templates

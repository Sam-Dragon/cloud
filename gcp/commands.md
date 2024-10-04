# Commands

> Version
- gcloud --version

> Initialize
- gcloud init

# Operations
> List
- gcloud GROUP SUB-GROUP ACTION ..

> ACTIONS = create, activate, delete, describe, list

# Base Configuration
- Group = config

# Sample 
> List with attribute
- gcloud config list [ATTRIBUTE]

> Set
- gcloud config set compute/region [REGION]

> UnSet
- gcloud config unset compute/region [REGION]

# Common
> List
- gcloud config configurations list

> List with filter
- gcloud config configurations list --filter [Field]:[Value]

> List with sorting
- gcloud config configurations list --sort-by [Field]
    
> Create
- gcloud config configurations create [VALUE]

> Describe
- gcloud config configurations describe [VALUE]

> Delete
- gcloud config configurations delete [VALUE]

> Activate
- gcloud config configurations activate [VALUE]

> Rename
- gcloud config configurations rename [OLD_VALUE] [NEW_VALUE]

# Module Configurations
  - GROUP = configs
  - SUB-GROUP = configurations

# VM Instances, Zones, Regions, Machine Types, Instance Templates
- Make sure project, region, zone is associated
- GROUP = compute
- SUB-GROUP = instances, zones, regions, machine-types, instance-templates

# VM Instances
- GROUP = compute
- SUB-GROUP = instances

> Create
- gcloud config configurations create [VALUE]

  > Flags
  - --machine-type
  - --custom-cpu --custom-memory --custom-vm-type
  - --image or --image-family or --source-snapshot or --source-instance-template or --source-machine-image
  - --service-account or --no-service-account
  - --zone
  - --tags
  - --preemptible
  - --restart-on-failure or --no-restart-on-failure or migrate-policy
  - --boot-disk-size --boot-disk-type --boot-disk-auto-delete  --np-boot-disk-auto-delete
  - --deletion-protection --no-deletion-protection
  - --metadata/metadata-from-startup-script/startup-script-url
  - --shutdown-script
  - --network --subnet --network-tier
  - --accelerator --metadata
 
  > regions & zones
  - Centralized configuration - default configuration for regions & zones
  - It can be found under compute-engine > Settings > Settings
      - gcloud compute project-info add-metadata --metadata = [REGION | ZONE]
  - Local configuration - set region/zone for local project
      - gcloud config set compute region/zone
  - command specific - directly provide while creation
      - gcloud config configurations create [VALUE] --zone --region

# Instances

> Get
- gcloud compute instance-groups managed list

> Resize
- gcloud compute instance-groups managed resize managed-instance-group --size=1 --zone=us-central1-a

> Recreate
- gcloud compute instance-groups managed recreate-instances managed-instance-group --instances=managed-instance-group-85fb --zone us-central1-a

> Delete
- gcloud compute instance-groups managed delete managed-instance-group --zone=us-central1-a
- gcloud compute instance-groups managed delete managed-instance-group

> Create
- gcloud compute instance-groups managed create managed-instance-group --zone=us-central1-a  --template=projects/<PROJECT_ID>/regions/<REGION>/instanceTemplates/<INSTACE_TEMPLATE> --size=1

  > Flags
  - --health-check
  - --initial-delay  

> Scaling
- gcloud compute instance-groups managed set-autoscaling managed-instance-group --max-num-replicas=2 --zone us-central1-a
- gcloud compute instance-groups managed stop-autoscaling managed-instance-group --zone us-central1-a

      > Flags
      - --cool-down-period(60s(default))
      - --scale-based-on-cpu --target-cpu-utilization scale-based-on-load-balancing --target-load-balancing-utilization
      - --min-num-replicas(on(default)/off/only-scale-out)

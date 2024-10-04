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
- gcloud compute instances create my-test-vm --source-instance-template=my-instance-template-with-custom-image
- gcloud compute instance-groups managed list
- gcloud compute instance-groups managed delete my-managed-instance-group
- gcloud compute instance-groups managed create managed-instance-group --zone=us-central1-a  --template=projects/academic-being-436605-q7/regions/us-central1/instanceTemplates/simple-instance-template-with-startup-scripts --size=1
- gcloud compute instance-groups managed set-autoscaling my-mig --max-num-replicas=2 --zone us-central1-a
- gcloud compute instance-groups managed stop-autoscaling my-mig --zone us-central1-a
- gcloud compute instance-groups managed resize my-mig --size=1 --zone=us-central1-a
- gcloud compute instance-groups managed recreate-instances my-mig --instances=my-mig-85fb --zone us-central1-a
- gcloud compute instance-groups managed delete my-managed-instance-group --region=us-central1

> Create instance with project & region
- gcloud compute instances create my-test-vm --source-instance-template=https://compute.googleapis.com/compute/v1/projects/<<PROJECT_ID>>/regions/<<REGION>>/instanceTemplates/<<INSTANCE_TEMPLATE_NAME>>

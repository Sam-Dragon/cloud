# Commands

> Version
- gcloud --version

> Initialize
- gcloud init

# Configuration
> List
- gcloud config list

> List & find specific attribute
- gcloud config list [Attribute]

# Module configurations
> List
- gcloud config configurations list

> Create & set
- gcloud config configurations create my-default-configuration

> Describe
- gcloud config configurations describe my-default-configuration

> Delete
- gcloud config configurations delete my-default-configuration

> Set
- gcloud config configurations activate my-default-configuration

# Instances

- gcloud compute instances list
- gcloud compute instances create
- gcloud compute instances create my-first-instance-from-- gcloud
- gcloud compute instances describe my-first-instance-from-- gcloud
- gcloud compute instances delete my-first-instance-from-- gcloud
- gcloud compute zones list
- gcloud compute regions list
- gcloud compute machine-types list
 
- gcloud compute machine-types list --filter zone:asia-southeast2-b
- gcloud compute machine-types list --filter "zone:(asia-southeast2-b asia-southeast2-c)"
- gcloud compute zones list --filter=region:us-west2
- gcloud compute zones list --sort-by=region
- gcloud compute zones list --sort-by=~region
- gcloud compute zones list --uri
- gcloud compute regions describe us-west4
 
- gcloud compute instance-templates list
- gcloud compute instance-templates create instance-template-from-command-line
- gcloud compute instance-templates delete instance-template-from-command-line
- gcloud compute instance-templates describe my-instance-template-with-custom-image

> Set / unset the project
- gcloud config set project <PROJECT>
- gcloud config unset project <PROJECT>


> Manage multiple configurations
- 

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

> Create
- gcloud compute instance-groups managed create managed-instance-group --zone=us-central1-a  --template=projects/<PROJECT_ID>/regions/<REGION>/instanceTemplates/<INSTACE_TEMPLATE> --size=1

  > Flags
  - --health-check
  - --initial-delay  

> Update
- gcloud compute instance-groups managed update managed-instance-group

  > Flags
  - --health-check
  - --initial-delay  
  
> Delete
- gcloud compute instance-groups managed delete managed-instance-group --zone=us-central1-a
- gcloud compute instance-groups managed delete managed-instance-group

> Resize
- gcloud compute instance-groups managed resize managed-instance-group --size=1 --zone=us-central1-a

> Scaling
- gcloud compute instance-groups managed set-autoscaling managed-instance-group --max-num-replicas=2 --zone us-central1-a
- gcloud compute instance-groups managed stop-autoscaling managed-instance-group --zone us-central1-a

  > Flags
  - --cool-down-period(60s(default))
  - --scale-based-on-cpu --target-cpu-utilization scale-based-on-load-balancing --target-load-balancing-utilization
  - --min-num-replicas(on(default)/off/only-scale-out)

> Instances

> Recreate
- gcloud compute instance-groups managed recreate-instances managed-instance-group --instances=managed-instance-group-85fb --zone us-central1-a

> Update
- gcloud compute instance-groups managed update-instances managed-instance-group --instances=managed-instance-group-85fb --zone us-central1-a

  > Flags
  - --minimal-action=none(default)/refresh/restart/replace
  - --most-disruptive-allowed-action=none(default)/refresh/restart/replace

> Instance-Template

> Update
- gcloud compute instance-groups managed set-instance-template managed-instance-group --template=instance-template
  
> Rolling Actions (Deployment)
- gcloud compute instance-groups managed rolling-action

    > Restart
    - gcloud compute instance-groups managed rolling-action restart managed-instance-group
    - --max-surge=5 or 10%
 
    > Replace (Delete & Create)
    - gcloud compute instance-groups managed rolling-action replace managed-instance-group
    - --max-surge=5 or 10%
    - --max-unavailable=5 or 10%
    - --replacement-method=recreate/substitute(default)

    > Update Instances
    
        > Basic Version
        gcloud compute instance-groups managed rolling-action start-update managed-instance-group --version=template=v1-template
          
        > Canary Version
        gcloud compute instance-groups managed rolling-action start-update managed-instance-group --version=template=v1-template --canary-version=template=v2-template, target-size=10%

# App Engine
> Create app engine
- gcloud app create --region=[REGION]

> Deploy the python application after importing 
- gcloud app deploy --version [VERSION] (OR) gcloud app deploy --version=[VERSION] --promote
- gcloud app deploy (OR) gcloud app deploy **dispatch.yml**
- gcloud app deploy --image-url=[DOCKER-IMAGE]
- gcloud app deploy --stop-previous-version

> To deploy with version & decide to navigate traffic
- gcloud app deploy --version=[VERSION] **--no-promote**

> List the services, versions & instnaces
- gcloud app services list
- gcloud app versions list --hide-no-traffic
- gcloud app instances list
- gcloud app regions list
- gcloud app zones list

> View the data based on versions 
- gcloud app browse
- gcloud app browse --version=[VERSION]
- gcloud app browse --service=[SERVICE]

> Split traffic between version [Canary Deployment]
- gcloud app services set-traffic --splits=v3=.5,v2=.5 --split-by=random
- gcloud app services set-traffic split=v3=.5,v2=.5
- gcloud app services set-traffic splits=v3=.5,v2=.5
- watch curl https://melodic-furnace-304906.uc.r.appspot.com/

> Display url to console  
- gcloud app open-console --version=v2

> Debugging
- gcloud app open-console --logs
- gcloud app logs --tail

> Instances
- gcloud app instances list
- gcloud app instances describe INSTANCE --service=[SERVICE-NAME] --version=[VERSION-NAME]
- gcloud app instances delete INSTANCE --service=[SERVICE-NAME] --version=[VERSION-NAME]
- gcloud app instances scp INSTANCE --service=[SERVICE-NAME] --version=[VERSION-NAME] --recurse local_dir INSTANCE:remote_dir
- gcloud app instances ssh INSTANCE --service=[SERVICE-NAME] --version=[VERSION-NAME]

> Services
- gcloud app services list
- gcloud app services browse SERVICE-NAME --version=[VERSION]
- gcloud app services describe SERVICE-NAME
- gcloud app services delete SERVICE-NAME
- gcloud app services set-traffic SERVICE-NAME --splits=[VERSION_NUMBER=PERCENTAGE, VERSION_NUMBER=PERCENTAGE] --split-by=[IP/COOKIE,RANDOM]

> Versions
- gcloud app versions list
  - --hide-no-traffic 
- gcloud app versions browse --service=SERVICE-NAME --version=[VERSION]
- gcloud app versions describe --service=SERVICE-NAME
- gcloud app versions delete --service=SERVICE-NAME
- gcloud app versions migrate VERSION-NAME --service=SERVICE-NAME
- gcloud app version start/stop [VERSION] --service=SERVICE-NAME

> Jobs
- gcloud app deploy cron.yml

> Queue
- gcloud app deploy queue.yml

# Cloud Run
- gcloud run deploy SERVICE_NAME --image [IMAGE URL] --revision-suffix=[VERSION]
- gcloud run services update-traffic SERVICE_NAME --to-revisions=[VERSION_NUMBER=PERCENTAGE, VERSION_NUMBER=PERCENTAGE] 
- gcloud run revisions list

# Cloud Functions
- gcloud function list
- gcloud function deploy [NAME]
  - --docker-registry: registry to store functions docker images [-container-registry[DEFAULT] or -artifact-registry]
  - --docker-repository: repository to store functions docker images 
  - --gen2 (use 2nd gen, if not mentioned it will use 1st gen)
  - --runtime (nodejs, java, python etc..)
  - --service-account (Service Account to use)
    - 1st Gen [Default]: App Engine default service account. PROJECT_ID@appspot.gsserviceaccount.com
    - 2nd Gen: Default compute service account. PROJECT_NO-compute@developer.gsserviceaccount.com
  - --timeout
  - --max-instances / -min-instances
  - --source
    - zip file from google cloud storage
    - source repository [repository url]
    - local file system
  - --trigger-bucket (OR) --trigger-bucket (OR) --trigger-topic (OR) --trigger-event-filters [gen2] 

# Pub/sub
- gcloud config set project glowing-furnace-304608

> Topics
- gcloud pubsub topics create topic-from-gcloud
- gcloud pubsub topics list
- gcloud pubsub topics delete topic-from-gcloud

> Create Subscriptions
- gcloud pubsub subscriptions create subscription-gcloud-1 --topic=topic-from-gcloud
- gcloud pubsub subscriptions create subscription-gcloud-2 --topic=topic-from-gcloud

> Read messages from subscribers
- gcloud pubsub subscriptions pull subscription-gcloud-2
- gcloud pubsub subscriptions pull subscription-gcloud-1

> Publish Message to Topic by Publisher
- gcloud pubsub topics publish topic-from-gcloud --message="My First Message"
- gcloud pubsub topics publish topic-from-gcloud --message="My Second Message"
- gcloud pubsub topics publish topic-from-gcloud --message="My Third Message"

> Read message & acknowledge
- gcloud pubsub subscriptions pull subscription-gcloud-1 --auto-ack
- gcloud pubsub subscriptions pull subscription-gcloud-2 --auto-ack

> Read all subscribers of topic
- gcloud pubsub topics list-subscriptions topic-from-gcloud

# Kubernetes Engine

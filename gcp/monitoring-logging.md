# Monitoring
- Tools to monitor the infrastructure
- Gather metrics
- Create Visualizations
- Configure Alerts - Based on condition, documentation, notifications - multiple channels

> Workspace
- They are used to organize monitoring information for projects
- We can add GCP projects or AWS accounts

> Monitoring for VM
- Default - CPU, Disk Traffic, Network Traffic, Uptime information
- '**Cloud Agent**' fetches additional metrics disk, CPU, Network, Process Metrics of VM & sends to cloud monitoring

# Logging
- Real time log management and analysis tool
- It can perform operations such as sorting, searching, filtering, analyzing, alerting etc..
- exabyte scale, fully managed service [No server provisioning, patching etc.]
- Ingest log data from any source

> Features  
- Logs Explorer: search, sort & analyze logs using flexible queries
- Logs Dashboard: rich visualizations
- Logs Metrics: capture metrics from logs (Using queries/matching strings)
- **Logs Router**: Route different entries to different destinations

> Log Data Collection
- Automatically happens from App Engine, GKS, GCE
- Ingest logs for GCE VM's
  - Install & Run '**Logging Agent**' on all the VM's
- Ingest logs for on-premises
  - Install BindPlane tool from Blue Medora
  - Use cloud logging api   

> Audit & Security Logs
- Access Transparency Logs: captures action performed by GCP team on content [Only for organizations above gold level]
- Cloud Audit Logs:
  - Admin Activity Logs
  - Data Access Logs
  - System Event Audit Logs
  - Policy Denied Audit Logs  

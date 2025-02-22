# Hierarchy
- Organization -> Folder -> Projects -> Resources
- [Organization + Folder] not applicable in free tier account
- One project per application per enviroment [Example: Dev, Prod, Stage]


> Permission Hierarchy
- ACL: lowest level to provide specific permissions for resource
- IAM Policies: role based permissions for resource
- Organization Policies: Global configuration for permissions for resource

# IAM [Identity & Access Management]
- To control the acess to the system based on authentication & Authorization
- It gives fine grain control to users in order to access the resource based on role assigned
- IAM is applicable to user(s), service accounts, unauthenticated users 

> Terminologies
- **Users**: gcp user
- **Roles**: It all about permissions
- **Policy**: Assign roles to users 

> Roles
- Basic Roles (or Primitive Roles) - Viewer/Editor/Owner [**NOT** RECOMMNED FOR PRODUCTION]
  - Viewer: Read Only
  - Editor: Viewer + Edit Actions
  - Owner: Editor + Manage Roles & Permissions + Billing
 
- Predefined Roles - Fine grained roles predefined & managed by google [RECOMMNED FOR PRODUCTION]
  - Different roles for different purposes

- Custom Roles
  - Create your own role  

> IAM Policy
- It is policy applicable to any resource [organization, folder, project, resource]
- Policy object - It has list of bindings, binding binds roles to list of members
- Member type is identified by **prefix**
  - user, serviceaccount, group or domain
- Members to roles is many-to-many relationship
- Binding users to the role

> IAM Members/Identities
- Google Account: Represents a person [email]
- Service Account: Represents an application account [Not Person]
- Google Group: Collection - Google & Service Accounts
- Google Workspace Domain: google workspace or gsuite to managed all google services
- Cloud Identity Domain: identity as service to centrally manage users & groups
  
> **Policy Troubleshooter**
- It helps to troubleshoot permission for the user

> Service Account
- machine to machine communication 
- Identified by email address [id-compute@developer.gserviceaccount.com]
- Machine level interaction [No User Intervention]
- It doesnt have any password
  - It use RSA Private/Public Key
  - Cannot login via browser or cookies
Ex: VM needs access to cloud storage

> Service Account Types
- Default Service Account [NOT RECOMMENDED]: Automatically created when services are used
- User Managed[RECOMMENDED]: Created by user for fine grain access control
- Google Managed Service Accounts: Created & Managed by Google
  - Used by GCP to perform operations on user's behalf
  - Dont worry about them
 
> SA Use Cases
- [Internal] VM to Cloud Storage/Pubsub - [Uses Google Managed Keys]
- [External] On Premises to Cloud Storage - [Internal required Service Account User Managed Keys]
- [External] On Premises to Google Cloud API's - [OAuth2, OpenIDConnect, JWT]

> ACL [Access Control Lists]
- defines the level of access for a resource
- Access can be fetched either by IAM or ACL
- IAM must be used for defining common permissions to all objects in a bucket
- ACL must be used for customize access to individual objects
- Access Controls: Uniform [IAM] & Fine Grained [IAM + ACL]

> Cloud Storage - **Signed URL**
- A URL that gives permission for limited time to perform specific actions

> Cloud Storage - **Static Websites**
- Bucket Name same as domain name
- Copy all files to bucket
- Give access to all users by providing permissions

> IAM Best Practices
- Principal of Least Privilege
- Seperation of duties
- Constant monitoring
- Use groups whenever possible

> User Identity Management
- Google Workspace [GSuite]
- Corporate Directory Federation : federate cloud identity or google workspace with external identity provider such as Active Directory or Azure Active Directory

> Organization Policy Service
- It is global constraints [centralized constraints on the resources]
- Example: Deny Service Account Creation,
- Organization Policy Administrator role
- organization policy overrides all the constraints specified by IAM (OR) ACL 

# Billing Account
- It can be associated with one or more projects
- organization can have multiple billing accounts
- Types: Self Served [Credit Card, Bank Account] or Invoiced [Large organizations]
- billing data can be exported to BigQuery [Visualization] (OR) Cloud Storage[History/Archiving]
- billing exports type - BigQuery Export (OR) File Export to Cloud Storage

# Scenario
- App Engine Deployer -> Deploy the apps but cant shift traffic
- App Engine Service Admin -> It can shift traffic but cant deploy
- IAM Group -> In case of providing access to operations team for production access
- IAM Role -> In case of providing access to specific team member for production access
- Viewer -> Auditor role to read  but no edit access for all resources
- Cloud Storage Viewer -> project A wants to access cloud storage of project B
- Organization Administrator -> defines resource hierarchy, access management policies, manage roles and policies
- Billing Account Creator -> create billing accounts
- Billing Account Administrator -> Manages the billing accounts but cannot create billing account
- Billing Account User -> Associate project with billing accounts [Project Owner]
- Billing Account Viewer -> only view the billing account details 
- Compute Engine Admin -> complete control of compute stuff. everything of compute stuff
- Compute Instance Admin -> complete control of compute instance and disks
- Compute Engine Network Admin -> complete access to networking resources and read only access to firewall rules and certs
- Compute Engine Security Admin -> complete access to firewall rules and ssl certs
- Compute Storage Admin -> complete access to disks, images & snapshots
- Compute Engine Viewer -> read only access to everything to compute
- Compute OS Admin Login -> log into compute engine instance as admin user
- Compute OS Login -> log into compute engine instance as standard user
- App Engine Creator -> create/delete applications
- App Engine Admin -> read/update applications, CRUD operations for services/instances/version/operations
- App Engine Viewer -> read all the application resources
- **App Engine Code Viewer** -> read the code of the application
- App Engine Deployer -> version(CRD), applications/services/versions
- App Engine Service Admin -> versions (RUD), applications (R), services/instances (CRUD) operations. split or migrate traffic, start & stop version
**Note**: App engine doesnt allow you to view or download logs, view monitoring charts, enable/disable billing, access config or data stored in services

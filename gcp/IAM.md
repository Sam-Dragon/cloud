# Hierarchy
- Organization -> Folder -> Projects -> Resources
- One project per application per enviroment

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
- Binding users to the role
- Policy object - It has list of bindings, binding binds roles to list of members
- Member type is identified by **prefix**
  - user, serviceaccount, group or domain
- Members to roles is many-to-many relationship

> Policy Troubleshooter
- It helps to troubleshoot permission for the user

> Service Account
- VM needs access to cloud storage
- Identified by email address [id-compute@developer.gserviceaccount.com]
- Machine level interaction [No User Intervention]
- It doesnt have any password
  - It use RSA Private/Public Key
  - Cannot login via browser or cookies

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

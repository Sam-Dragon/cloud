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

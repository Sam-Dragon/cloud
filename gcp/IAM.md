# IAM [Identity & Access Management]
- To control the acess to the system based on authentication & Authorization
- It gives fine grain control to users in order to access the resource based on role assigned

> Terminologies
- **Users**: gcp user
- **Roles**: It all about permissions
- **Policy**: Assign roles to users 

> Roles
- Basic Roles (or Primitive Roles) - Viewer/Editor/Owner [NOT RECOMMNED FOR PRODUCTION]
  - Viewer: Read Only
  - Editor: Viewer + Edit Actions
  - Owner: Editor + Manage Roles & Permissions + Billing
 
- Predefined Roles - Fine grained roles predefined & managed by google [RECOMMNED FOR PRODUCTION]
  - Different roles for different purposes

- Custom Roles
  - create your own role  

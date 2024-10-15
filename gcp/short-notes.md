# Compute Engine
- Virtual Machine: Basic server configuration sits here [Charagable]
- Instance Templates: Template configuration for creating VM [Not Charagable]
- Instance Groups: It is like replicate set which will use instance templates & creates VM's
- Load Balancer: It uses instance groups for managing traffic across VM's

# App Engine
- Application: It is based on region & can be specified with version
- Service: The instance of application & it can have applications with different versions 
- Version: Each deployment of application is treated as new version

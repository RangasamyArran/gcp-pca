# VPC Network Concepts
## VPC networks
* Created within projects, which means there is no cross-project communication 
by default. 
* Global resources, for example: VM in US can communicate with a VM in APAC
* Private RFC 1918 IP range
* Can be non RFC 1918 IP range
### Subnets
* Are part of a VPC network
* Regional objects
* VMs which are zonal resources are allocated with an IP from a subnet in the same region
* Do not provide network boundaries. VMs can communicate across subnets.
* However, default firewall rules deny traffic between VMs regardless of subnets

#### Subnet creation modes
|Default| Auto Mode| Custom Mode|
|-------|----------|------------|
|One subnet per region|Default network|Full control of subnets and IP ranges|
|Default firewall rules|Default /20 subnet per region|No default firewall rules|
|Experimentation Not good for production|Expandable up to /16|Default firewall rules |Expandable|
|Org policy to skip|Isolated use cases (testing, PoCs)|Good for production

<img width="481" alt="image" src="https://github.com/user-attachments/assets/3034ef7f-50b5-42ef-bc4b-96fdcb76aff9">

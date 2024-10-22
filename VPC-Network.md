# [VPC Network Concepts](https://cloud.google.com/vpc/docs/overview)
## VPC networks

* Provides connectivity for your Compute Engine virtual machine (VM) instances, including Google  Kubernetes Engine (GKE) clusters, serverless workloads, and other Google Cloud products built on Compute Engine VMs.
* Offers built-in internal passthrough Network Load Balancers and proxy systems for internal Application Load Balancers.
* Connects to on-premises networks by using Cloud VPN tunnels and VLAN attachments for Cloud Interconnect.
* Distributes traffic from Google Cloud external load balancers to backends.

## Firewall rules
Firewall rules let you control which packets are allowed to travel to which destinations. Every VPC network has two implied firewall rules that block all incoming connections and allow all outgoing connections.

The default network has additional firewall rules, including the default-allow-internal rule, which permit communication among instances in the network.

## Routes
* Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside of Google Cloud.
* Each VPC network comes with some system-generated routes to route traffic among its subnets and send traffic from eligible instances to the internet

## Forwarding rules
* While routes govern traffic leaving an instance, forwarding rules direct traffic to a Google Cloud resource in a VPC network based on IP address, protocol, and port.


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

#### IP Allocation in VPC
VMs must have internal IP and can have external IP addresses
* Internal IP:
  * Allocated from subnet range to VMs by DHCP
  * Alternatively, can reserve (static) internal IP address
* External IP:
  * Assigned from pool (ephemeral)
  * Alternatively, can reserve (static) external IP address
  * Bring Your Own IP address (BYOIP)
A subnet can contain a secondary range of internal IP addresses
* Useful when multiple services are running on a VM and each needs its own IP address
* Also applies to GKE pods

Subnet:
* Primary CIDR range 10.1.0.0/16 
* Secondary CIDR range 10.2.0.0/20

### Routes
* Managed at the VPC level
* Applies to traffic egressing a VM
* Enables VMs on same network (VPC) to communicate via private IP
  * Only if it is allowed by a firewall rule
* Automatically created when a subnet is created
* Can manually create static/custom routes
  * Next hop can be: Instance IP or name, Cloud VPN, Internal TCP/UDP load balancer, default 
internet gateway
* Routes can be selectively applied to
  * All instances, instances with specific network tags, instances with specific service accounts
* Internet access is enabled by a default route (priority=1000)
  * Applies to VMs with external IPs
  * No gateway or public component needed
    
<b>There are 3 kinds of routes</b>

<ins>Subnet routes</ins>
* System-generated. Added for each subnet.
* Allows routing between subnets.
* Non Removable and non overridable.
* Exchanged with VPC Peering, and by default through Cloud Router. More on 
that in a later slide.
* The narrowest possible IP range, which means it cannot be overridden.

<ins>Static routes</ins>
* Considered a custom route
* Manually added by users
* Next hop can be: Instance IP or name, Cloud VPN, Internal TCP/UDP load balancer, default internet gateway

<ins>Dynamic routes</ins>
* Considered a custom route
* Added by Cloud Router through a BGP session
* Next hop is alway the BGP peer

<b><ins>Notes</ins></b>
Unlike other cloud providers, internet access is enabled by a default route (priority=1000). No gateway or public component is needed.
* It doesn’t mean all VM’s have internet access. an external IP on VM’s is 
needed for public Internet access.
* Removable with caveats
  * A public internet route to destination of Google API’s is needed for Private Google Access
  * Cloud CDN requires the default internet rout




<img width="481" alt="image" src="https://github.com/user-attachments/assets/3034ef7f-50b5-42ef-bc4b-96fdcb76aff9">

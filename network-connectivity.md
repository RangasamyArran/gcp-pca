# Network connectivity:
  Network Connectivity is Google's suite of products that provide enterprise connectivity from your on-premises network or from another cloud provider to your Virtual Private Cloud (VPC) network. 

  When connecting to Google Cloud, you can choose among the following Google Cloud networking products. 
  - Cloud VPN
  - Cloud Interconnect

## Cloud VPN
   * Provide network connectivity with Google Cloud between your on-premises network and Google Cloud, or from Google Cloud to another cloud provider.
   * If you need a lower cost solution, have lower bandwidth needs, or you are experimenting with migrating your workloads to Google Cloud, you can choose Cloud VPN

Google Cloud offers two types of Cloud VPN gateways: 
  - HA VPN 
  - Classic VPN.

### HA VPN

* Securely connect your on-premises network to your VPC network through an IPsec VPN connection
* When you create an HA VPN gateway, Google Cloud automatically chooses two external IP addresses, one for each of its interfaces. 
* Each IP address is automatically chosen from a unique address pool to support high availability. Each of the HA VPN gateway interfaces supports multiple tunnels. You can also create multiple HA VPN gateways. When you delete the HA VPN gateway, Google Cloud releases the IP addresses for reuse

### Classic VPN

* All Cloud VPN gateways created before the introduction of HA VPN are considered Classic VPN gateways
* Classic VPN gateways have a single interface, a single external IP address, and support tunnels that use static routing 

## Cloud Interconnect
Cloud Interconnect offers three options for connecting to Google Cloud: 
- Dedicated Interconnect
- Partner Interconnect
- Cross-Cloud Interconnect.

**Dedicated Interconnect** and **Partner Interconnect**
Extending your on-premises network to your VPC networks in Google Cloud,  You can create a dedicated connection (Dedicated Interconnect) or use a service provider (Partner Interconnect) to connect to VPC networks.

|  | Dedicated Interconnect | Partner Interconnect |
|--| ---------------------- | ---------------------|
| Features | A direct connection to Google | More points of connectivity through one of our supported service providers |
|  | Traffic flows directly between networks, not through the public internet | Traffic flows between networks through a service provider, not through the public internet |
|  | 10-Gbps or 100-Gbps circuits with flexible VLAN attachment capacities from 50 Mbps to 50 Gbps | Flexible capacities from 50 Mbps to 50 Gbps |
| Supported bandwidth |  Scale to meet the most demanding data needs. Connection capacity is delivered over one or more 10-Gbps or 100-Gbps Ethernet circuits, with a maximum of 8 x 10-Gbps (80 Gbps) circuits, or 2 x 100-Gbps (200 Gbps) circuits for each Dedicated Interconnect connection.   If your traffic doesn't require a 10-Gbps or 100-Gbps circuit, consider Cloud VPN or Partner Interconnect |  Pay only for the capacity you need, with options of 50 Mbps to 50 Gbps for each VLAN attachment. Increases in the number of VLAN attachments or increasing the capacity of an existing VLAN attachment depends on your service provider's available capacity.

## Peering 
If you need access to only Google Workspace or supported Google APIs, you have the following options:
- Direct Peering
  - Directly connect (peer) with Google Cloud at a Google edge location.
- Carrier Peering
  - To peer with Google by connecting through a support provider, which in turn peers with Google

  

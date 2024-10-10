# Cloud Load Balancing

Google's Cloud Load Balancing is built on reliable, high-performing technologies such as Maglev, Andromeda, Google Front Ends, and Envoy—the same technologies that power Google's own products

## Types of load balancers

* Cloud Load Balancing offers two types of load balancers:
  - Application Load Balancers
    - Layer 7 load balancer for your applications with HTTP(S) traffic
  - Network Load Balancers
    - Layer 4 load balancer that supports TLS offloading (with a proxy load balancer) or you need support for IP protocols such as UDP, ESP, and ICMP (with a passthrough load balancer).
   
### Application Load Balancers
 Proxy-based Layer 7 load balancers that enable you to run and scale your services behind an anycast IP address. The Application Load Balancer distributes HTTP and HTTPS traffic to backends hosted on a variety of Google Cloud platforms—such as Compute Engine and Google Kubernetes Engine (GKE)—as well as external backends outside Google Cloud.
 
 - External Application Load Balancers
   - implemented as managed services either on Google Front Ends (GFEs) or Envoy proxies. Clients can connect to these load balancers from anywhere on the internet

 - Internal Application Load Balancers
   - Built on the Andromeda network virtualization stack and the open source Envoy proxy. This load balancer provides internal proxy-based load balancing of Layer 7 application data. The load balancer uses an internal IP address that is accessible only to clients in the same VPC network or clients connected to your VPC network

### Network Load Balancers
  Network Load Balancers are Layer 4 load balancers that can handle TCP, UDP, or other IP protocol traffic. These load balancers are available as either 
  - Proxy load balancers
    - Advanced traffic controls and backends on-premises and in other cloud environments
    - Layer 4 reverse proxy load balancers that distribute TCP traffic to virtual machine (VM) instances in your Google Cloud VPC network
      * External proxy Network Load Balancers
        -  internet to backends in your Google Cloud VPC network, on-premises, or in other cloud environments
      * Internal proxy Network Load Balancers
        - Envoy proxy-based regional Layer 4 load balancers that enable you to run and scale your TCP service traffic behind an internal IP address that is accessible only to clients in the same VPC network or clients connected to your VPC network.
       
          ![image](https://github.com/user-attachments/assets/2f79e327-7f88-4ae6-a68e-644d237687b2)

  - Passthrough load balancers
    -  if you want to preserve the source IP address of the client packets
    -  Load-balanced packets are received by backend VMs with the packet's source and destination IP addresses, protocol, and, if the protocol is port-based, the source and destination ports unchanged.
    -  Load-balanced connections are terminated at the backends. Responses from the backend VMs go directly to the clients, not back through the load balancer. The industry term for this is **direct server return(DSR)**

      - External passthrough Network Load Balancers
      - Internal passthrough Network Load Balancers
   
    ![image](https://github.com/user-attachments/assets/74937cde-6991-40b2-ba01-1d28655a00fd)

# How to choose Load Balancer:
![lb-product-tree](https://github.com/user-attachments/assets/9d6b780d-7a59-4525-87a4-202fdeef5197)

![image](https://github.com/user-attachments/assets/985f820e-9e91-475c-9045-8e53bba43af7)




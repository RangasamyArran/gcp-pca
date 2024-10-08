Before jumping into **GKE** lets understand what is **Kubernetes**

## Kubernetes
  Kubernetes is an open-source platform that helps you orchestrate and manage your
container infrastructure on-premises or in the cloud. It’s a container-centric management environment. Google originated it and donated it to the open-source community. Now it’s a project of the vendor-neutral Cloud Native Computing Foundation.

It automates the deployment, scaling, load balancing, logging, monitoring, and other
management features of containerized applications.
Supports 
  * Declarative configurations
  * Imperative configuration(recommeded to use only for quick temporary fixes)

To understand how Kubernetes works, there are two related concepts you need to
understand. 
  * The first is the Kubernetes object model. Each thing Kubernetes
manages is represented by an object, and you can view and change these objects’
attributes and state.
  * The second is the principle of declarative management. Kubernetes expects you to tell it what you want the state of the objects under its management to be; it will work to bring that state into being and keep it there

    ![image](https://github.com/user-attachments/assets/47933898-ba0d-4ca9-8687-ebcaea8f111d)

#### Control plane and nodes:
  The job of the nodes is to run Pods(smallest kubernetes deployment object). The job of the control plane is to coordinate the entire cluster. 
  Several critical Kubernetes components run on the control plane. The single
component that you interact with directly is the **kube-apiserver**. This component’s job is to accept commands(from **kubectl**) that view or change the state of the cluster, including launching Pods

#### Cooperating processes make a Kubernetes cluster work
![image](https://github.com/user-attachments/assets/76128bc8-298a-4192-925b-7a0a1b2b1555)

##### Control Panel:
**kubectl**

  This command’s job is to connect to kube-apiserver and communicate with it using the Kubernetes API

**kube-apiserver**

  Authenticates incoming requests, determines whether they are authorized and valid, and manages admission control. Any query or change to the cluster’s state must be
addressed to the kube-apiserver

**etcd**

  The cluster’s database. Its job is to reliably store the state of the cluster. This
includes all the cluster configuration data; and more dynamic information such as
what nodes are part of the cluster, what Pods should be running, and where they
should be running. You never interact directly with etcd; instead, kube-apiserver
interacts with the database on behalf of the rest of the system.

**kube-scheduler**

  Responsible for scheduling Pods onto the nodes. It evaluates the requirements of each individual Pod and selects which node is most suitable.

**kube-controller-manager**

  It continuously monitors the state of a cluster through Kube-APIserver. Whenever the current state of the cluster doesn’t match the desired state, kube-controller-manager will attempt to make changes to achieve the desired state. It’s called the “controller manager” because many Kubernetes objects are maintained by loops of code called controllers. These loops of code handle the process of remediation.

**kube-cloud-manager**

  It manages controllers that interact with underlying cloud providers. If you manually launched a Kubernetes cluster on Google Compute Engine, kube-cloud-manager would be responsible for bringing in Google Cloud features like load balancers and storage volumes when you needed them.    

##### Nodes:

**kubelet**

  Each node runs a kubelet. You can think of kubelet as Kubernetes’s agent on each node. When the kube-apiserver wants to start a Pod on a node, it connects to that node’s kubelet. Kubelet uses the container runtime to start the Pod and monitors its lifecycle, including readiness and liveness probes, and reports back to Kube-APIserver.
  
**kube-proxy**

  It maintains network connectivity among the Pods in a cluster. In open-source Kubernetes, it does so using the firewalling capabilities of iptables, which
are built into the Linux kernel.
  
## GKE
  GKE is a Google-managed implementation of the Kubernetes open source container orchestration platform. Kubernetes was developed by Google, use to deploy and operate containerized applications at scale using Google's infrastructure. GKE provides the operational power of Kubernetes while managing many of the underlying components, such as the control plane and nodes, for you

### GKE cluster architecture 

  A GKE cluster consists of a **control plane** and worker machines called **nodes**. The control plane and nodes make up the Kubernetes cluster orchestration system. 
    <img width="514" alt="image" src="https://github.com/user-attachments/assets/7fc78c09-7d27-4c4d-ae7a-bc71852e0d68">

A comparison of the two GKE offerings

| Autopilot mode  | Standard mode |
| --------------- | --------------|
| Optimized Managed Kubernetes with hands-off experience  |  Managed Kubernetes with configuration flexibility  |
| Less management overhead but less configuration abilities  | Less management overhead but less configuration abilities  |
| Only pay for what you use (Pod pricing) | Pay for all provisioned infrastructure, regardless of utilization |

**Common for Autopilot and Standard:**
- Kubernetes control plane
- Container runtime
- Container-optimized OS
- Virtualization, Network
- Hardware

Standard mode has all of the same functionality as Autopilot but you are responsible for the configuration, management, and optimization of the cluster to your requirements.

![image](https://github.com/user-attachments/assets/fc605528-d96b-4e46-9ea9-31bb2ec6270e)

![image](https://github.com/user-attachments/assets/1135dc0c-2315-448b-a075-ba92864ad527)

#### Pods and Controller Objects
  A **pod** is the smallest deployable unit in Kubernetes, which is a group of one or more containers that share storage and network resources. They're designed to run a single instance of an application or a microservice. Think of them as the basic building blocks.

In GKE: When you deploy an application, it's encapsulated within a pod. If your app needs to scale, more pods are created.

This is based on the **IP-per-pod** model of Kubernetes. With this model, each Pod is assigned a single IP address, and the containers within a Pod share the same network namespace, including that IP address.

![image](https://github.com/user-attachments/assets/6f6addf3-dd46-4ec6-b8e1-42bce644deef)


**Controllers** are the brains behind the operation. They manage the lifecycle of pods, ensuring that the desired state of your system matches the current state.

Key controllers include:

**Deployment:** Ensures a specified number of pods are running. Handles updates and rollbacks.

**ReplicaSet:** Maintains a stable set of replica pods running at any given time.

**StatefulSet:** Manages stateful applications, where each pod has a unique identity and stable, persistent storage.

**DaemonSet:** Ensures that all (or some) nodes run a copy of a pod, usually for background tasks like logging.

**Job and CronJob:** Manages batch tasks, ensuring they complete successfully.

In GKE: These controllers are responsible for the health, scaling, and management of your application's pods. For instance, a Deployment controller ensures that the desired number of replicas for your application are always running. If a pod crashes, the controller creates a new one to replace it.

![image](https://github.com/user-attachments/assets/d9cfa2dc-5b01-40e0-a005-46094a9ac0ad)

**A Deployment maintains the desired state**

Ex: 
![image](https://github.com/user-attachments/assets/d0b14ecd-c690-4303-9a3c-524728d323c6)

Explanation:

when Kube-scheduler schedules Pods for a Deployment, it notifies the Kube-APIserver. These changes are constantly monitored by controllers—especially by the Deployment controller. 

The Deployment controller creates a child object, a ReplicaSet, to launch the desired Pods. If one of these Pods fails, the ReplicaSet controller will recognize the difference between the current state and the desired state and will try to fix it by launching a new Pod

**Deployments ensure that sets of Pods are running**
~~~
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
~~~

**how do Pods talk to other Pods?**

Each Pod has a unique IP address, just like a host on the network. On a node, the Pods are connected to each other through the node's root network namespace, which ensures that Pods can find and reach each other on that VM.

This allows the two Pods to communicate on the same node. The root network namespace is connected to the Node's primary NIC. Using the node’s VM NIC, the root network namespace is able to forward traffic out of the node. This means that the IP addresses on the Pods must be routable on the network that the node is connected to.

**Pod to Pod within the same node**:

![image](https://github.com/user-attachments/assets/142c486e-26ab-46d3-a816-dfcd63a39bc6)

> [!Note]
> In GKE, the nodes will get the Pod IP addresses from address ranges assigned to your Virtual private Cloud(VPC).

Each node maintains a separate IP address space for its Pods, the nodes don’t need to perform Network Address Translation on the Pod IP addresses. That means that the Pods can directly connect to each other using their native IP addresses. Pod IP addresses are natively routable within the cluster's VPC network and other VPC networks connected to it by VPC Network Peering.

#### Services
A Kubernetes Service is an object that creates a dynamic collection of IP addresses, called endpoints, that belong to Pods matching the Service’s label selector.

When you create a Service, that Service is issued a static Virtual IP address from the
pool of IP addresses that the cluster reserves for Services.

The Virtual IP is durable. It is published to all nodes in the cluster. It doesn't change,
even if all of the pods behind it change.

In GKE, this range is automatically managed for you, and by default contains over
4,000 addresses per cluster.

**There are several ways to find a Service in GKE**
- Environment Variables
  - This is enabled by default but it is not the most robust mechanism for discovery.
  - If changes are made to a Service after Pods have been started those changes will not be visible to Pods that are already running.
  - Pods will only see the changes that were made up to the point where they are started because the environment variables are defined inside the Pods when the Pods are started.
- Kubernetes DNS
  - DNS names are more discoverable than environment variables. And DNS changes can be visible to Pods during their lifetimes.
  - The Kubernetes DNS server watches the API server for the creation of new Services. When a new Service is created, kube-dns automatically creates a set of DNS records for it.
 
**Service discovery through Kubernetes DNS:**

![image](https://github.com/user-attachments/assets/84de2613-57e1-4c7c-be5e-1d2c57d8f14e)
  
  Kube-dns maintains the DNS records of Pods and Services. To maintain high performance for Service discovery, GKE autoscales kube-dns based on the number of nodes in the cluster.

  Every Service defined in the cluster is assigned a DNS A record. In this example, there is a Service named “lab” in the **demo** namespace. The name of the namespace and the label **SVC** are added to the DNS name, resulting in a fully qualified domain name of lab.demo.svc.cluster.local as below. Services are assigned one A (Address) record and one SRV (Service) record.

- A(Address) Record

  ![image](https://github.com/user-attachments/assets/ac06efad-1c5e-4c69-aaf8-30cbf183929c)

- SRV(service) Record
  
  ![image](https://github.com/user-attachments/assets/decb7c2f-39bd-4627-8545-e0eb974e6a9f)

> [!Note]
> Headless Kubernetes Services, those that are defined without a ClusterIP, also have DNS A and and SRV records defined but those resolve to the set of IP addresses of the pods selected by the Service.

#### Service Types and Load Balancers
  
  There are three principal types of Services: ClusterIP, NodePort, and LoadBalancer. These Services build conceptually on one another, adding functionality with each step.

**ClusterIP Service**

It has a static IP address and operates as a traffic distributor within the cluster, but ClusterIP Services aren’t accessible by resources outside the cluster. Other Pods will use this ClusterIP as their destination IP address when communicating with the Service.

  ![image](https://github.com/user-attachments/assets/7d2b038b-7d4a-4483-94e7-86c7f29d35e2)

- How it works
  
![image](https://github.com/user-attachments/assets/e6e508c9-c90b-48aa-a408-262b38019059)

  In this example, you have frontend Pods that must be able to locate the backend Pods. When you create the Service, the cluster control plane assigns a virtual IP address—also known as ClusterIP—from a reserved pool of Alias IP addresses in the cluster’s VPC. This IP address won’t change throughout the lifespan of the Service.
  
  The cluster control plane selects Pods to include in the Service’s endpoints based on
the label selector on the Service and the labels on the Pods. The ip-addresses of these backend pods are mapped to the target port, TCP port 6000 in this example, to create the endpoint resources that the service forwards requests to.

  The ClusterIP Service will answer requests, on TCP port 3306 in this example, and forward the requests to the backend pods using their ip-addresses and target port as the endpoint resources

**NodePort Service**

  In addition to the setup of the internal ClusterIP Service, a specific port is exposed for external traffic on every node. This port—also known as nodePort —is automatically allocated from the range 30,000 to 32767.

  ![image](https://github.com/user-attachments/assets/70502480-952b-4abe-bea6-e49cb74dccda)

 **LoadBalancer Service**

   When you create a LoadBalancer Service, GKE automatically provisions a Google Cloud network load balancer for inbound access to the Services from outside the cluster. 
   
   Client traffic will be directed to the external IP address of the Google Cloud network load balancer, and the load balancer will forward the traffic on to the nodes for this Service. The nodes will forward that traffic to the internal LoadBalancer Service, and the LoadBalancer Service will then forward the request to one of the Pods.
![image](https://github.com/user-attachments/assets/b7777b26-e66f-4469-b782-ca1c7a6d7311)

**summary:**
![image](https://github.com/user-attachments/assets/617d9d8c-6b91-40d9-a622-f745cf4e95f4)

- **ClusterIP** Services can be used within the cluster to provide a stable endpoint that allows Pods to connect to other Pods without the risk of the IP address changing.
- **NodePort** Services extend the ClusterIP Services concept to expose and then bind a port number on each of the nodes in the cluster to the Service. This allows you to access resources within the cluster from external resources such as Google Cloud compute instances.
- **LoadBalancer** Service type implementation in GKE improved on the NodePort Service by using the cloud provider API to create a Google Cloud network load balancer for traffic distribution across the nodes.







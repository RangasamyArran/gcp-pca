# What is computing?
GCP offers a range of compute services that go from giving users full control (i.e., Compute Engine) to highly-abstracted (i.e., Firebase and Cloud Functions), letting Google take care of more and more of the management and operations along the way.

[Reference](https://cloud.google.com/blog/products/compute/choosing-the-right-compute-option-in-gcp-a-decision-tree?m=1) 

![image](https://github.com/user-attachments/assets/3cb62034-abed-409c-a111-e08402664b1b)

![image](https://github.com/user-attachments/assets/632ed0a9-e50e-474b-9c0d-a9c389f1bc8a)

[Respective usecase](https://cloud.google.com/hosting-options)

## Choosing a Google Cloud compute option

**Compute Engine** - Virtual machines. You reserve a configuration of CPU, memory, disk, and GPUs, and decide what OS and additional software to run.
  * If you need more control over the underlying infrastructure (for example, the operating system, disk images, CPU, RAM, and disk) then it makes sense to use Compute Engine. This is a typical path for legacy application migrations and existing systems that require a specific OS.


**Kubernetes Engine** - Managed Kubernetes clusters. Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications. You create a cluster and configure which containers to run; Kubernetes keeps them running and manages scaling, updates and connectivity.

**Cloud Run** - A fully managed serverless platform that runs individual containers. You give code or a container to Cloud Run, and it hosts and auto scales as needed to respond to web and other events.

**App Engine** - A fully managed serverless platform for complete web applications. App Engine handles the networking, application scaling, and database scaling. You write a web application in one of the supported languages, deploy to App Engine, and it handles scaling, updating versions, and so on. 

**Cloud Functions** - Event-driven serverless functions. You write individual function code and Cloud Functions calls your function when events happen (for example, HTTP, Pub/Sub, and Cloud Storage changes, among others). 

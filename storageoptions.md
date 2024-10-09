# Storage Options:
Google Cloud offers storage services for all the key storage formats: block, file, and object.

## Block Storage:
  The data that you store in block storage is divided into chunks, each stored as a separate block with a unique address
* **Persistent Disk**
  * Dedicated hard-disk drives (HDD) and solid-state drives (SSD) for enterprise and database applications deployed to Compute Engine VMs and Google Kubernetes Engine (GKE) clusters.
  * You can use Persistent Disk as a boot disk for a virtual machine (VM) instance, or as a data disk that you attach to a VM.
* **Google Cloud Hyperdisk**
  * Fast and redundant network storage for Compute Engine VMs
* **Local SSD**
  * Ephemeral, locally attached block storage for high-performance applications.
 
## File Storage:
Data is organized and represented in a hierarchy of files that are stored in folders, similar to on-premises network-attached storage (NAS). File systems can be mounted on clients using protocols such as NFS and Server Message Block (SMB)

* Cloud FileStore:
  * NFS file servers for Compute Engine VMs and Google Kubernetes Engine clusters.
* Cloud NetApp Volumes
  * File-based storage using NFS or SMB.

## Object storage
Data is stored as objects in a flat hierarchy of buckets. Each object is assigned a globally unique ID
* Cloud Storage
  * low-cost, highly durable, no-limit object storage for diverse data types.
  * The data you store in Cloud Storage can be accessed from anywhere, within and outside Google Cloud


# Storage advisor

![storage-advisor](https://github.com/user-attachments/assets/19380668-9a27-4eae-ad98-e32c497cb577)

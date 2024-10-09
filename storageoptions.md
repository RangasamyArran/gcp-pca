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


### More on Cloud Storage:
- Cloud Storage is a service for storing your objects in Google Cloud.
- An object is an immutable piece of data consisting of a file of any format.
- Store objects in containers called buckets.
- Buckets can also contain managed folders, which you use to provide expanded access to groups of objects with a shared name prefix
  Ex:
  ~~~
    exampleinc.org (org)
      imageprocessing(project)
        photos(bucket)
          animals(managed folder)
            puppy.png
        videos(bucket)
          animalsvideo(managed folder)
            cat.vd
  
  ~~~

 - Storage class is a piece of metadata that is used by every object.
 - The storage class set for an object affects the object's availability and pricing model
 - If you don't specify a default storage class when you create a bucket, that bucket's default storage class is set to Standard storage.
 - You can change the storage class of an existing object either by rewriting the object or by using Object Lifecycle Management
 - You can enable the Autoclass feature on a bucket to let Cloud Storage manage storage class transitions for you automatically.
 
| Storage Class| Name for APIs and CLIs | Minimum storage duration | Retrieval fees | Typical monthly availability | 
| --- | --- | --- | --- | --- |
| Standard storage | STANDARD |	None |	None | >99.99% in multi-regions and dual-regions, 99.99% in regions |
| Nearline storage | NEARLINE | 30 days | Yes | 99.95% in multi-regions and dual-regions, 99.9% in regions |
| Coldline storage | COLDLINE |	90 days	| Yes | 99.95% in multi-regions and dual-regions, 99.9% in regions |
| Archive storage  | ARCHIVE  |	365 days | 	Yes | 99.95% in multi-regions and dual-regions, 99.9% in regions |


### Object Lifecycle Management
- It contains a set of rules which apply to current and future objects in the bucket.
- When an object meets the criteria of one of the rules, Cloud Storage automatically performs a specified action on the object

  Each rule contains one action and one or more conditions.
  
- An object has to match all of the conditions specified in a rule for the action in the rule to be taken.
- If you specify multiple rules that contain the same action, the action is taken on an object when that object matches the conditions in any of the rules.
- If multiple rules have their conditions satisfied simultaneously for a single object, Cloud Storage performs the action associated with only one of the rules, based on the following considerations:
  - The Delete action takes precedence over any SetStorageClass action.
  - The SetStorageClass action that switches the object to the storage class with the **lowest at-rest storage pricing takes precedence**.

    For example, if you have one rule that changes the object's class to Nearline storage and another rule that changes the object's class to Coldline storage, but both rules use the exact same condition, the object's class always changes to Coldline storage when the condition is met.
- Changes to a bucket's lifecycle configuration can take up to 24 hours to go into effect


    
# Storage advisor

![storage-advisor](https://github.com/user-attachments/assets/19380668-9a27-4eae-ad98-e32c497cb577)

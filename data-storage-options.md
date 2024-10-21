# What is cloud storage?
* Each VM has a boot persistent disk (PD) that contains the operating system
  * Not best practice to place non-system data on the boot disk
* When apps require additional storage space add one or more additional storage options
  * Cloud Storage buckets: Affordable object storage
  * Additional persistent disk(s): Efficient, reliable block storage.
  * Local SSD: High performance, transient, local block storage.
  * Filestore: High performance file storage for Google Cloud users.

## Considerations include
* Product choice
  * (e.g., Cloud SQL, BigQuery, Firestore, Spanner, Bigtable) 
* Choosing storage options 
  * (e.g., Zonal persistent disk, Regional balanced persistent disk, standard, Nearline, Coldline, Archive)

## Comparing storage options: use cases
|# |Firestore| Bigtable| Cloud Storage| Cloud SQL| Cloud Spanner| BigQuery|
|--|---------|---------|--------------|----------|--------------|---------|
|Type| No SQL Document|No SQL Wide Column|Blob Store|Relational SQL for OTLP|Relational SQL for OTLP|Relational SQL for OTAP|
|Best for| Storing, syncing and querying data| “Flat” data, Heavy read/write, events, analytical data| Structured and unstructured binary or object data| Web frameworks,existing applications | Large-scale database applications (> ~2 TB)|Interactive querying, offline analytics|
|Use cases|Mobile, web, and server development|AdTech, Financial and IoT data|Images, large media files, backups|User credentials, customer orders|Whenever high I/O, global consistency is needed|Data warehousing|

## Decide which storage option fits your use case
![image](https://github.com/user-attachments/assets/a96c1e0b-a01a-4ab1-9c29-df7b70cf7a23)

## Transfer data sets to GCP
![image](https://github.com/user-attachments/assets/de7907f6-fcba-42ab-bf85-e5c44fdb0f81)

## Choosing a Cloud Storage class 
![image](https://github.com/user-attachments/assets/c850aea9-9c1d-4d68-b527-3d971b7ffdd4)

## Data processing - Cloud Dataflow versus Cloud Dataproc
![image](https://github.com/user-attachments/assets/8f61092e-e4de-47ad-beb5-6ea152f32605)








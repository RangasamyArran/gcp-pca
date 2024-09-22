Considerations include
* Product choice
  * (e.g., Cloud SQL, BigQuery, Firestore, Spanner, Bigtable) 
* Choosing storage options 
  * (e.g., Zonal persistent disk, Regional balanced persistent disk, standard, Nearline, Coldline, Archive)

Comparing storage options: use cases
|# |Firestore| Bigtable| Cloud Storage| Cloud SQL| Cloud Spanner| BigQuery|
|--|---------|---------|--------------|----------|--------------|---------|
|Type| No SQL Document|No SQL Wide Column|Blob Store|Relational SQL for OTLP|Relational SQL for OTLP|Relational SQL for OTAP|
|Best for| Storing, syncing and querying data| “Flat” data, Heavy read/write, events, analytical data| Structured and unstructured binary or object data| Web frameworks,existing applications | Large-scale database applications (> ~2 TB)|Interactive querying, offline analytics|
|Use cases|Mobile, web, and server development|AdTech, Financial and IoT data|Images, large media files, backups|User credentials, customer orders|Whenever high I/O, global consistency is needed|Data warehousing|



